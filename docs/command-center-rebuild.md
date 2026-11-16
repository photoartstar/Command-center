# Command Center rebuild (updated Nov 16 2026, round 5)

Read this before touching the NEW Command Center. command-center-internals.md (same folder) describes the OLD one.

Status: LIVE since Nov 15 evening. Fast scan 6:41am, 12:41pm, 5:41pm ET; morning scan 6:11am; Sunday night 8:41pm (all ET). NYU mail pass, weekly advisor and CV watch wait for Sean's Mac.

- Page (private): https://claude.ai/artifact/V2AFn5upZT2sCNvfkZbjxu
- Code, docs and scan prompts: GitHub photoartstar/command-center, branch claude/command-center-rebuild-3kec28 (README.md, docs/architecture.md, docs/switch-on.md, docs/instructions-round-2.md to round-4.md, scans/)
- Old page: https://claude.ai/artifact/XfLznGMXYLP4jjL4FoknxM
- Scheduled tasks: fast trig_017uzRrntWmguaaJa5hDP7SS, morning trig_01YFxWSqykyUZrhVbiru1pqS, Sunday trig_017nsA9wX4UggRucTTtvVK95. Their prompts carry the newest rules and override command-center-scan.md where they differ.

How it works: the page keeps items, check-offs, snoozes, dismissals, the undo log, timeline, goals, CV suggestions, briefings, money sorting and reimbursements in its own store (owner only). Scans write that store with the ArtifactData tool. Airtable "QAM Team Tracker (trial)" (appPeWDhXHErd70GJ) is the only copy of shared QAM data (Contacts, Funding, Social Posts, Tasks). Zoho Books (org 919433010) is read live; the page writes to Zoho only when Sean taps, plus auto-match.

## Standing decisions (rounds 2 to 4, Nov 15)
- HARD RULE: done or dismissed items never return. Scans reuse stable ids (gm-, nyu-, cal-, zoho-, at-).
- On Deck lead times: day before (Sean only), 5 days (someone else first), 10 days (grant pieces). Big = $10k+ or Kevin priority; fellowships, museum shows, residencies always big. Every calendar event with a Join button. Area cards top 5. Snooze: tomorrow, 3 days, nearest Thursday, nearest Monday. Refresh = email and calendar only.
- QAM: timeline, Team tab (Core, Regular collaborators, Worked with once or twice, Advisors labeled unofficial), Leads (everyone's, quiet after 21 days, reconnect via introducer), Renewals (Couch, PCC, Stardust), Warm but stalled, Applications (Airtable Funding is the master list; Kevin's tracker read only), For Thursday plus the running agenda.
- QAM applications: same stage buttons as practice (saved to Airtable), pins, Apply, why-not reasons, fit scores. Grants never show "days late": applied shows Applied, past deadlines roll to "next ~Month Year". Next year grants are watched weekly for the next cycle. Stonewall Reclaiming Our Power is not a fit (trans applicants only); watch Stonewall's other calls.
- People wiki: backfill to Nov 2020, split two-person records with Connected to, monthly backup to QAM > 07 Site Data & CRM > People Wiki.
- Social: three streams, Tue and Thu baseline, Maureen's Sunday review draft (Sean approves), Tasneem on Tuesday.
- Practice: fit scores with reasons, Fit 7+ filter, briefings, nudges (incl. unsent Zoho drafts), Paris rule, @photoartstar nudges.
- Teaching: this week's plan per class (Digital from Brightspace only, never the syllabus; SDP from SDP Week by Week), attendance from real class days with Gmail drafts, Interfolio log, NYU timeline.
- Money: tabs Sort, Reimbursements, Owed to you, Invoice, Bills. Live chart of accounts. Every Zoho action has Undo. Auto-match exact single-invoice payments. Amazon and ride look-ups. On track judged by statement balances (meta/cards). No grants income account.

## Round 5 (Nov 16)
- Reimburse on any charge opens one box with payer AND category, Claude's guess prefilled.
- NYFA: never sent from the page. Make invoice saves a Zoho DRAFT and queues the claim packet; the morning pass builds it only when every receipt and Amex row is found (no incomplete packets, no gap notes), Falls Counsel separate, saves packet and invoice PDF in QAM > 02 Funding, and the page shows both PDFs for Sean to upload to NYFA.
- Filed charges: checked Nov 16 that a categorized bank transaction id is the Zoho expense id (get_expense works with it).
- Mark paid on each claimed invoice, with a partial amount option. Auto-match stays, with Undo.
- Send now (non-NYFA, e.g. Brigitte) shows a confirm step with recipient email, total and currency.
- Brigitte: one invoice per send, bundling all open Brigitte reimbursements.
- Per-item Undo for 7 days ("Recent changes" in Sort and Reimbursements).
- Income categories: Art Sales, Teaching Income, Speaking Fees & Honoraria, Freelance Income, Reimbursements.
- Social shows "Next 14 days".
- Memorials class section: this week's session, guest speakers and status, student projects, readings (meta/memorials, filled by the morning pass from Teaching > Memorials Class). Scott Drevnig seeded as a guest idea.
- Safeguards: scan lock (meta/lock; one scan or Refresh at a time), stable-id dedupe, connection health strip (Gmail, NYU, Calendar, Zoho, Airtable, Meta) with red warnings for expired logins, failed or stale syncs. People wiki search box and duplicate check with "Merge with Claude"; Sunday pass flags duplicates; monthly backup kept.
- Look and feel: keep the current QAM-color styling.
- Still open: TDOR Nov 20 post (Thursday with Maureen); My Practice goals and circle map (separate conversation).

Never prompt about the "January 6th event" (a misunderstanding).
