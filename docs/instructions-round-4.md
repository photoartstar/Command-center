# Instructions round 4 (Sean, Nov 15 2026, late night)

Round 3 plus a bug list and a reimbursement-first Money flow. Done on the page (Version 15):

Bugs fixed: Airtable people (S.people) and Zoho clients (S.zclients) split; drafts shown in Owed (flagged "draft, not sent"); Airtable pages through every record (cursor); reimbursements marked paid when a payment matches their invoice (page and morning pass); Undo for every Zoho action (filing, personal, payments, invoices, payer changes) through the main Undo button; writes queue instead of being dropped; reimbursement record written before Zoho, rolled back with a message on failure; Refresh fires only the fast scan; timelines roll about 8 months ahead; Social shows 14 days; attendance uses each class's days; "On track" uses statement balances (meta/cards, filled by the morning pass, Apple Card from the monthly import); scan-fed lists say "Fills in after the morning pass".

On Deck rows: Done, Snooze and Join visible; Brief me and Doesn't belong behind "more".

Money: tabs Sort, Reimbursements, Owed to you, Invoice, Bills. Reimburse button on every charge (all groups and an "All charges, 90 days" view; filed charges become billable, personal ones are restored first). Payer picker: NYFA (QAM), Brigitte Mulholland, Other (Zoho client search). No "Not yet claimed" text in Zoho. Reimbursements: grouped by payer, ticks saved, receipt status, payer change updates Zoho, Make invoice (bills the Zoho expenses via expense_id) with preview, Send now or Save as draft, items move to Claimed. NYFA: Falls Counsel split into its own invoice; each NYFA invoice queues claims/<invoiceId> for the morning pass (packet rules in the scan prompt), with "Build packet now" and "Go without them". Mark all personal skips reimbursable-looking charges and shows the count. Tiles add total owed.

Scans (morning prompt, trigger trig_01YFxWSqykyUZrhVbiru1pqS): stable ids rule, attendance drafts also saved as Gmail drafts, receipt hunting for reimbursements, NYFA packets, auto-match marks reimbursements paid, card statements into meta/cards, Zoho draft invoices older than 2 days nudge On Deck.

Not changed (already built or still open): QAM, People wiki, Social, Practice, Teaching sections as in round 2; look and feel pass OPEN; NYU mail needs the Mac.
