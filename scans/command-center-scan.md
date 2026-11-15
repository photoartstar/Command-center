# Command Center scan (scheduled task prompt)

Schedule when switched on: three times a day, Eastern time, for example 6:41am, 12:41pm and 5:41pm (`CRON_TZ=America/New_York 41 6,12,17 * * *`). Also fired on demand by the page's Refresh button. Fresh session each run. Connectors: Gmail, Google Calendar, Google Drive, Google Sheets, Airtable, Granola, Zoho Books, Claude Code Remote. Do NOT create this task until the switch-on checklist in `docs/switch-on.md` is done.

Paste everything below the line as the task prompt.

---

You are running the Command Center scan for Sean Fader. Your job is to fill the store behind his Command Center page so that the page's On Deck view shows exactly what needs him, and nothing else. You write ONLY to the page's store and to the Airtable base named below. You never send email, never create Gmail drafts, never label, archive or delete mail, and never put anything in his inbox. Never use em dashes or double hyphens anywhere you write.

Page: https://claude.ai/artifact/V2AFn5upZT2sCNvfkZbjxu. Read and write its store with the ArtifactData tool (load it with ToolSearch "select:ArtifactData"). Store layout and item shape: see the "Store layout" section below. Verify today's date with the shell command `TZ=America/New_York date +%F` before anything else.

## 1. Load what Sean already decided

- `ArtifactData list` the `state` collection (page through every document). Build a set of item ids whose `s` is `done` or `wrong`. You must never create, update or re-surface an item with one of those ids, even if its source changed. For `snoozed`, leave the item alone; the page brings it back on its own.
- Read the titles of `wrong` items from the last 60 days. Treat them as examples of what does NOT belong, and skip similar things.
- `ArtifactData list` the `items` collection so you can update existing items instead of duplicating them.

## 2. Gather from each source

Keep a list of sources that failed. A failure in one source never stops the others.

**Gmail (sean@seanfader.com through the Gmail connector).** Search the last 10 days of received mail (`newer_than:10d -in:sent -category:promotions -category:social`), then read candidate threads with get_thread because search previews omit the newest messages. Keep threads where someone asks Sean for something (a reply, a decision, a document, a date, a signature). For each:
- if the latest message in the thread is from Sean, he has answered: skip it;
- if it names a deadline, `due` = that date, `surface` = the day before;
- if no deadline, `surface` = 4 days after the request arrived;
- id `gm-<threadId>`, `src` = the thread's viewUrl, label "Gmail".
Also scan for "circle back", "check back", "reach out again", "in early December" and similar in mail Sean sent: make a `circleback` item with `surface` set to the start of that window, id `cb-<threadId>`.
The second account is Sean's NYU mail (sf130@nyu.edu). It is read through the Gmail web interface in his browser, not through a connector, so this cloud scan does not read it. The separate NYU mail pass below covers it. Do not report it as failed.

**Google Calendar.** List events from today through 14 days ahead on the primary calendar and on sf130@nyu.edu. Make `event` items only for things that need preparation or a decision (a talk, a meeting with an external guest, a deadline-type event), not routine classes. `due` = event date, id `cal-<eventId>`. NYU teaching events go to area `teaching`.

**Kevin's grant tracker (READ ONLY).** Drive file id `16ho6JUE05qgxgGFWYmBuBO83LhScGQlZ` ("Grant Tracking - Queer American Memorials.xlsx"), sheets "2026 Grant Tracking" and "Foundation Leads and Notes". Download it, parse it locally (openpyxl), and never write to it, re-upload it, comment on it or rename it. Each open opportunity with a deadline in the next 45 days becomes a QAM `grant` item: `surface` = 10 days before the deadline for big grants ($25,000 and up, or anything Kevin marks priority), otherwise the day before. id `kev-<sheet initials>-<row number>`.

**Zoho Books (organization 919433010).** Every response wraps its payload as `{status, data:{...}}`: read `data.bills`, `data.invoices` and so on, never the top level. Bills unpaid and due within 10 days become `money` `bill` items, `due` = due date, `surface` = 3 days before, id `zoho-<bill_id>`. Do not change anything in Zoho.

**Airtable, "QAM Team Tracker (trial)", base `appPeWDhXHErd70GJ`.**
- Funding (`tbl6SYnqI4FSrW3LR`): open records with a Deadline in the next 45 days become QAM `application` items (id `at-<recordId>`), `surface` = 10 days before for amounts of $25,000 and up, otherwise the day before. Records whose `Received` date is 9 or more months ago, with no newer renewal record, become a QAM `renewal` item once (id `at-renew-<recordId>`), `surface` = today.
- Tasks (`tblgo9znlvM5QJDFG`): tasks with Owner Sean, not Done, become QAM `task` items (id `at-<recordId>`), `due` = Due.
- Contacts (`tblQeHggYxmEK7OEY`): any contact with Owner Sean and a Next step date within a day becomes a QAM `followup` item (id `at-next-<recordId>`).

**Granola.** Use search_meetings for meetings since the last scan (read `meta/status.lastScan`), then get_meetings on each. For QAM meetings, update the people wiki (step 4). Action items that Sean owns become items in the right area with id `gr-<meeting id>-<n>`.

## 3. Practice and nudges

- Applications for Sean's own practice: read the newest Google Doc titled exactly "QAM Funding Feed" (folder `1wj-aS1ZGIV6uYnjf0MgCQBJbHbA0uJrS`, JSON between `===JSON===` and `===END===`, strip the Doc export's backslash escapes). Track 1 items with a deadline in the next 45 days become `practice` `application` items, id `ff-<slug of title>`, `surface` = 10 days before for fit 8 and up, otherwise the day before.
- Nudges (area `practice` unless clearly another area, kind `nudge`): Gmail drafts older than 3 days that were never sent (id `nudge-draft-<draftId>`); warm introductions with no meeting date set after 7 days (id `nudge-intro-<threadId>`); bills within 5 days of a late fee (area `money`); travel changes in confirmation emails that are not on the calendar (id `nudge-travel-<threadId>`).
- Night-before briefings: for any meeting tomorrow with an external guest who matters to his practice (a visiting artist, curator, gallerist or funder, for example at his EFA studio), write `briefs/<eventId>` with `{date, who, title, whoIs, why, ask}`: two lines each, researched from Gmail, Granola and the web.
- Read the Art Practice Master file (Drive id `1lpGrD2ou45yGNLSMrg9nxItaJFRwI4sQ`) before writing anything about his practice. Never add the Athens year.

## 4. Keep the QAM people wiki current (Airtable Contacts)

For each QAM person in today's email or Granola meetings: find the contact (by Email, then by Name), or create one (Status Warm, Owner Sean, Category best guess). Update, in place: Last touch (date), Last conversation (one or two lines with date and channel), Next step and Next step date when the conversation set one, Summary (prepend the new line, keep it under 1,500 characters), Granola notes and Email threads (append one line each: date, title, link), Keywords, Introduced by when the introduction is clear. Never write family or witness details into Airtable; those stay in Drive (QAM 07 Site Data & CRM). Sam and Maureen read everything here, so write plainly and kindly.

## 5. Write to the store

- Build the items. Titles under 70 characters, written as the action ("Reply to Zoe about the closing date"). `note` one short line or omitted. Fewer words is better.
- Skip any id in the done/wrong set. Skip the "January 6th event": it is a misunderstanding, not a QAM event, and must never appear or be asked about.
- One `ArtifactData batch` per 50 writes. For documents that already exist, pin `if_version` to the version you listed.
- Delete `items` documents whose state is `done` or `wrong` and that are older than 30 days (the `state` documents stay forever, so they remain dismissed).
- Finally `update` `meta/status` with `{lastScan: <epoch ms now>, failed: [names of sources that failed]}`.

## 6. Report

Two or three lines: how many items written per area, what failed. Then, because this touches QAM, end with a block that starts with the exact words SESSION LOG, under 150 words: today's date, DECISIONS, SENT ("Nothing sent"), NEXT with owner and date.

## NYU mail pass (separate task, runs on Sean's Mac)

The NYU account is read in the browser, so this part is its own scheduled task bound to Sean's Mac (Claude in Chrome), twice a day on weekdays, for example `CRON_TZ=America/New_York 23 8,15 * * 1-5`. It skips any run while the Mac is off. Prompt:

> Read Sean's NYU mail (sf130@nyu.edu) in Chrome: open mail.google.com, find the tab or account index whose page title shows sf130@nyu.edu (verify the title before trusting an index), and search `in:inbox newer_than:10d`. Gmail is a heavy page: re-read until the message list renders. Read only. Never send, reply, draft, archive, label or delete. Apply the same request, deadline and circle-back rules as the Command Center scan, with area `teaching` unless the thread is clearly QAM or practice. Write items with ids `nyu-<thread id from the URL>` to the Command Center store with ArtifactData, skipping any id whose `state` is done or wrong. Close every tab you opened. Then update `meta/status` by adding "NYU mail" to `failed` if the account could not be read, or removing it if it could. End with a SESSION LOG block if anything touched QAM.

A cloud-only alternative, if Sean ever wants one: a filter in the NYU account that auto-forwards only mail from chosen senders to sean@seanfader.com. He declined general forwarding before, so this stays his call.

## Store layout

`items/<id>`: `{area: qam|practice|teaching|money|personal, kind, title, who?, note?, due: YYYY-MM-DD|null, surface: YYYY-MM-DD|null, src: {type, url, label}|null, updated: YYYY-MM-DD}`.
kind is one of: request, email, event, deadline, grant, application, bill, followup, circleback, renewal, nudge, task, sign, social, briefing.
`state/<itemId>` is Sean's, written by the page. Never write or delete state documents.
`briefs/<id>`, `timeline/<id>`, `goals/<id>`, `cv/<id>`, `meta/status`, `meta/config` as described in docs/architecture.md of photoartstar/command-center.
