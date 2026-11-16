# How the new Command Center works

Live page (private to Sean): https://claude.ai/artifact/V2AFn5upZT2sCNvfkZbjxu
Source: `app/command-center.html`. Republish from this file (same path in the session that published it, or pass the URL from any other session after an `Artifact read`).

The old Command Center (https://claude.ai/artifact/XfLznGMXYLP4jjL4FoknxM, pinned) keeps running until switch-on. Do not edit or delete it as part of this rebuild.

## Three pieces

1. **The page** renders everything and records what Sean does. It holds no copy of shared QAM data.
2. **The page's store** (the artifact `db` capability) holds the scanned items, Sean's check-offs, snoozes and dismissals, the undo log, the QAM timeline, practice goals, CV suggestions and briefings. Scheduled scans read and write it with the `ArtifactData` tool. Rules: only the owner (admin and up) can read or write anything.
3. **Airtable** ("QAM Team Tracker (trial)", base `appPeWDhXHErd70GJ`) is the source of truth for shared QAM work. The page reads Contacts, Funding and Social Posts live through the Airtable connector and writes approvals back. Sam and Maureen work there.

Refresh button: starts the scan scheduled task through the Claude Code Remote connector (`fire_trigger`), using `meta/config.scanTriggerId`, and re-reads Airtable. While `meta/config.live` is false it only re-reads.

## Store layout

| Path | What | Written by |
|---|---|---|
| `items/<id>` | One thing that may need Sean | scans |
| `state/<itemId>` | Sean's decision on that item | page (and undo) |
| `undo/<auto>` | Newest-first log for the Undo button, last 30 kept | page |
| `timeline/<id>` | QAM milestones for the top strip | scans, Claude sessions |
| `goals/<id>` | My Practice Big Goals | practice pass |
| `cv/<id>` | CV watch suggestions | CV watch (proposes), page (decides) |
| `briefs/<id>` | Night-before meeting briefings | scan |
| `meta/config` | `{live, scanTriggerId, refreshTriggerId}`, the on switch (Refresh fires `refreshTriggerId`, the fast scan) | Claude at switch-on |
| `meta/status` | `{lastScan, failed: [...], sources: {gmail|nyu|calendar|zoho|airtable|drive|meta: {ts, ok, err}}}` drives the connection health strip | every scan |
| `thursday/<id>` | For Thursday items `{meeting, text, done, inAgenda}` | page, morning scan |
| `opps/<slug>` | Practice and job opportunities from the funding feed | morning scan |
| `pipeline/<slug>` | Sean's stage and pin per opportunity | page only |
| `waiting/<threadId>` | Waiting on people `{who, what, sent, url, area, kind}` | fast scan |
| `interfolio/<id>` | Interfolio log suggestions | morning scan proposes, page decides |
| `classes/<id>`, `attendance/<date>-<class>` | Rosters, absences, drafted emails | scan, page |
| `reimb/<transactionId>` | Reimbursable charge `{title, amount, date, payer, customer_id, expense_id, status: open|claimed|paid|cancelled, invoice_id, invoice_number, receipt, receiptMissing, forWhat}` | page (Reimburse), morning pass (receipts, paid) |
| `meta/nyu`, `meta/teaching` | NYU terms and dates, next class, `week` (this week's plan per class) | morning scan |
| `sort/<transactionId>` | What Sean did with a Zoho charge `{mode: biz|qam|brigitte|refund|invoice|personal, cat, note, vendorKey}` or `{parked}`; teaches the guesses | page |
| `charges/<transactionId>` | Claude's look-up for a charge `{items, suggest, why, question, url, none, reimb, area}` | morning scan |
| `automatch/<transactionId>` | Money in recorded against an invoice automatically `{title, amount, date, invoice_number, customer, account_id, ts, undone?}` | morning scan (Undo on the page) |
| `expected/<slug>` | Money owed but not invoiced `{client, what, amount, src, status}` | morning scan, page |
| `claims/<invoiceId>` | NYFA claim packet `{invoice_number, total, items, status: queued|building|blocked|ready|sent, missing, driveUrl, note, goWithout}` | page queues, morning pass builds |
| `meta/cards` | `{cards: [{name, statementBalance, due, paid}]}` for On track | morning pass |
| `invpay/<invoiceId>` | Manual Mark paid, incl. partial `{amount, total, ts}` | page |
| `meta/memorials` | Memorials class: week, guests, projects, readings | morning pass, Claude |
| `meta/lock` | `{by, ts, until}`: one scan or Refresh at a time | scans |
| `followups/<invoiceId>` | Drafted 30-day invoice follow-up `{to, subject, body}` | morning scan |

Version 3 of the page (Nov 15) also reads Zoho Books live (bank and card balances, unpaid invoices, items) and can create a customer plus a DRAFT invoice. "Tell Claude" uses the page's `sample` capability to file a typed or dictated note; when that is unavailable it saves the note with `needsFiling: true` for the next scan.

### `items/<id>`

```json
{
  "area": "qam | practice | teaching | money | personal",
  "kind": "request | email | event | deadline | grant | application | bill | followup | circleback | renewal | nudge | task | sign | social | briefing",
  "title": "Short, under 70 characters",
  "who": "Person or org (optional)",
  "note": "One short line (optional)",
  "due": "YYYY-MM-DD or null",
  "surface": "YYYY-MM-DD: the day it goes On Deck, or null",
  "src": {"type": "gmail | calendar | kevin | zoho | airtable | granola", "url": "https://...", "label": "Gmail"},
  "updated": "YYYY-MM-DD"
}
```

IDs must be stable across scans so a dismissal sticks: `gm-<gmail thread id>`, `cal-<event id>`, `kev-<sheet>-<row number>`, `zoho-<bill or invoice id>`, `at-<airtable record id>`, `gr-<granola meeting id>`, `cb-<slug>` for circle-back notes. Allowed characters: letters, digits and `_ - . ~ : @ +`.

### `state/<itemId>`

`{s: "done" | "snoozed" | "wrong", until: "YYYY-MM-DD" | null, ts, title, area, kind}`

- `done` and `wrong` hide the item for good. A scan must never re-create or re-surface an item whose id has one of these.
- `snoozed` hides it until `until`, then it returns On Deck.
- `wrong` ("doesn't belong here") is also a training signal: scans should read recent `wrong` titles and stop producing that kind of item.

### On Deck rule (page side)

An item is On Deck when it is not hidden by state and any of these hold: `due` is today, tomorrow or past; `surface` has arrived; or a snooze just ended. The scan does the judgement and sets `surface`:

| Case | `surface` |
|---|---|
| Request with a deadline | the day before the deadline (due in 7 days waits about 6) |
| Request with no deadline | 4 days after it arrived with no reply from Sean |
| "Circle back in early December" | the first working day of that window |
| Big grant or deadline | 10 days before the deadline |
| Bill | 3 days before the due date or late fee |
| Anything due within a day | today (or just set `due`) |

## Airtable fields added for this build (Nov 15 2026)

Contacts (`tblQeHggYxmEK7OEY`): Introduced by (self link) with its reverse Introduced, Summary, Last conversation, Next step date, Keywords, Email, Granola notes, Email threads.
Funding (`tbl6SYnqI4FSrW3LR`): Received (date the money came in; drives the 9-month renewal bar).
New table Social Posts (`tblIE99nz7g8OI68i`): Post, Planned date, Status, Format, Caption, Why this post, Image folder, Follow, Tag, Collaborators, Maureen OK, Maureen notes, Sean approved on, Memorial, Task. Status flow: Idea, Claude draft, Sean approved, Maureen approved, With Tasneem, Scheduled, Posted (also Needs changes, Dropped).

Field IDs used by the page are listed at the top of the page's script.
