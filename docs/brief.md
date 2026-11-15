# Command Center Rebuild Brief

Decided with Sean on a voice call, Nov 15 2026. Areas still to design: Teaching and NYU, Money, Personal.

## Setup and build approach

- Build in Claude Code on the web (cloud). Sean's Mac is in the shop; do not switch the new Command Center on until his Mac is back and every task feeding it has been checked.
- Everything Sean uses is in Google Drive. Point every task at Drive through the connector, never at the local synced Drive folder, Desktop or Downloads (CV watch currently reads local paths and must be repointed).
- Website (seanfader.com) source files live on GitHub, so Claude Code can update it from the cloud.
- Works on both phone and laptop.
- Refreshes a few times a day, plus a Refresh button.
- Undo button at the top, next to Refresh, that reverses the last dismiss or check-off.
- Every item can be checked off, snoozed, or marked "doesn't belong here". Dismissed items stay gone and never reappear from a later scan.
- Fewer words, more visuals throughout. The old version was too text-heavy and overwhelming.
- Nothing new goes to his inbox. Everything appears on the Command Center only.

## Front page: On Deck

- Five areas: QAM, My Practice, Teaching and NYU, Money, Personal. Each shows a few items.
- "On Deck" (not "urgent") always shows everything that qualifies, however many items there are:
  - anything due within a day;
  - requests with a deadline, surfaced by that deadline (due in 7 days can wait about 6);
  - requests with no deadline, after 4 days of no reply;
  - "circle back in early December" type notes, only when that time arrives;
  - big grants or deadlines within 10 days.
- Sources: both Gmail accounts, the personal Google Calendar, the NYU calendar (sf130@nyu.edu, already visible through the connector), Kevin's grant tracker (read only), and Zoho.
- Checking an item off just clears it. Sean archives his own email. Never edit Kevin's tracker.
- Each area has its own detailed page built for that work.

## QAM page

- Top: a cute horizontal timeline from now to spring, with an icon per milestone (lambda for launches, microphone for talks, pen for signatures). Tap for details.
- Current milestones: councilman meeting on the 24th; AR launch; San Francisco talk in late January (to confirm, possibly the St. Joseph's event Jan 23); talk to Santa Clara County queer organizations via Sera Fernando, around the following Monday; ICA San Jose closing Feb 21 2027; Trans Day of Visibility launch for Alina at the Billy DeFrank Center, Mar 31 (needs install planning); New York progress on Amanda Milan; nudge Maureen to sign the LLC operating agreement; Ogunquit Museum project.
- NOT a QAM event: the "January 6th event" (a misunderstanding). Never prompt to confirm it.
- Main job: leads and follow-ups. Each person shows name, last conversation, and next step with a date, updated from Granola meeting notes and email.
- Grant renewal reminders about 9 months after a gift (e.g. Couch Family Foundation), showing when it came in and how long it's been.
- Applications tab: the full list of QAM applications due.
- Social media tab for QAM (see below).
- Money owed or incoming is not on this page. Bills due surface through On Deck.

## QAM people wiki (Airtable)

- Lives in the Contacts table of the Airtable base "QAM Team Tracker (trial)". Airtable is the single source of truth for shared QAM work. The Command Center reads from and writes back to it and keeps no separate copy.
- Sean doesn't work in Airtable himself. Claude updates it from his Command Center and assigns tasks there. Sam and Maureen see everything, including full notes.
- Every person ever emailed or met about QAM, built from the existing Outreach CRM plus a fresh pull of email and Granola history.
- Each person: an "introduced by" link to another person, keywords, connected memorials, links to Granola notes and email threads, and a running summary (who they are, how they met, what was discussed, what's next).
- Claude uses this to answer questions like "who introduced us to Stonewall?" and to suggest going back through the introducer when a lead goes quiet. Claude can also search Sean's email and Granola directly for anything not summarized.
- Monthly backup to Drive as a small wiki: one page per person, with working links between people and out to Granola and email.

## QAM social media (separate from Sean's own)

- Shows the next week of planned posts and the strategy.
- Claude drafts captions and picks images for now, learning Maureen's standards over time.
- Flow: Claude drafts, Sean approves on the Command Center, Maureen approves (in Airtable), then the task goes to Tasneem with an image folder in QAM 04 Comms & Marketing (one folder per post) and an instruction card (who to follow, tag, invite as collaborator).
- Add a social posts table to the Airtable base for this flow.
- Ideas: an Instagram post for Trans Day of Remembrance (Nov 20), and posting the vertical cut of the website video.

## My Practice page

- Big Goals, each with concrete moves (which places fit, who in his circle can introduce, next step): a New York gallery, a museum show, a major fellowship.
- His personal-practice applications and deadlines live here.
- His own social media lives here.
- Key relationships and follow-ups, plus a map of his circle and how people could help.
- Night-before briefing for any important meeting (e.g. a visiting artist or curator at his EFA studio): who they are and why they could be helpful.
- Automatic nudges for what tends to slip: unsent drafts, warm intros with no date set, bills sliding toward late fees, travel changes nobody else heard about.
- CV watch suggestions appear here with one-tap approval. Approval updates the CV, the CV PDF and the website CV.
- The Art Practice Master file, CV and website update together whenever a practice fact changes.
- Leave off: the Athens year (only a hope, about 18 months away).
- Open: check whether the Guggenheim 2027 reference letters were all received (Sean doesn't usually have many letters).

## Still to design

- Teaching and NYU page
- Money page (Zoho, reimbursements)
- Personal page
