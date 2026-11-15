# Switch-on checklist

Do not switch the new Command Center on until Sean's Mac is back from the shop and every task below has been checked. "Switch on" means: create the scan task, write its id into the page's `meta/config`, and set `live: true`.

## 1. Tasks that feed or compete with the Command Center (inventory Nov 15 2026)

| Task | Id | Today | Needs before switch-on |
|---|---|---|---|
| Cv watch | trig_01SjJrWUqFPUkzR3cyHWRBP5 | Enabled, Sun 10:15pm. Reads local Desktop, Downloads and synced Drive paths | Replace prompt with `scans/cv-watch.md`; remove local folders and files |
| Qam daily scan (NYU mail, calendar, PSLF, CRM) | trig_01MpPHFTyfcKY3ogFC9KPfKe | Disabled, device_absent. Local QAM_DIR, Chrome for NYU mail, session_info, local QAM_Tracker.html | Retire: the Command Center scan and Airtable replace it. Keep disabled; PSLF check moves to the Money page design |
| Qam weekly advisor | trig_011F26U4X7iF6J49dms5LEfK | Enabled, Mon 7am, but reads local files and finishes in about 3 seconds. Bound to the Mac (TS00808-02LP-MC) | KEEP (Sean, Nov 15). Apply the prompt in `scans/qam-weekly-advisor.md`. A new prompt needs Sean's approval in a conversation linked to the Mac, so do this once it is back |
| QAM morning scan, QAM Items Feed | trig_016PpC6QJoMXcsaV6QKhuZGa | Enabled, 4am, cloud only, reads Kevin's tracker | Keep running for the old Command Center until switch-on, then retire (the new scan reads Kevin's tracker itself) |
| QAM midday catch-up | trig_01AA342cQCrHfZ5r1EQnzzr5 | Enabled, 11am, cloud only | Retire at switch-on (replaced by the 3x daily scan) |
| Funding scan, QAM Funding Feed | trig_016nNYubYJPUNEJGFzTGEofs | Enabled, 4:40am, cloud only | Keep. The new scan reads its feed for practice applications. Never rename "QAM Funding Feed" |
| Weekly funding scan fader qam | trig_014tJ262dAzwLSE14hM1PzqC | Enabled, Mon 4am, writes the same feed | Check it does not collide with the daily funding scan (two writers of one feed) |
| Daily social scan | trig_01ADtcMWy62ESTUFps1U73We | Disabled, device_absent, local folders | QAM half replaced by `scans/qam-social.md`; @photoartstar half goes to the practice scan |
| Nightly knowledge sweep | trig_011ARnNCY79ntmEy9Vi5WTrp | Disabled, device_absent, needs local sessions | Mac-only by design. Re-enable when the Mac is back |
| Morning brief | trig_01PhcBQTiPuhig1V66Hu684R | PAUSED Nov 15 at Sean's request; On Deck replaces it | Leave paused. Delete only if Sean asks |
| NYU mail pass (new) | not created yet | NYU mail is read in the browser, so it needs the Mac | Create from the "NYU mail pass" section of `scans/command-center-scan.md`, bound to the Mac |
| Zoho Books Monday pass, Zoho weekly digest | trig_018YuDF9QNLtPa3icnF8Xv95, trig_01VnjQJgQfTPdwurVtJBTyom | Enabled, cloud only | Keep. Money page design will decide where the digest shows |
| NYC DCLA reminder | trig_015g2115t5mUg8yjJmGeQDo7 | One-shot Jan 15 2027, email notification on | Turn its email notification off (brief: nothing new in his inbox) |
| ANEF attestation watch | trig_01VUGgcPDoMJ4NXa9w3VYXUr | Disabled | Leave off |
| Apple card monthly import, Weekly DMARC scan, Monthly memory consolidation | (see list_triggers) | Enabled | No change |

Three tasks (Morning brief, Funding scan, QAM morning scan) fired recently but have no run record. Check their last session transcripts before relying on them.

## 2. Answers from Sean (Nov 15) and what is still open

Answered:
- Second Gmail account is the NYU account. It is read through the web interface, so a separate NYU mail pass runs on the Mac (see `scans/command-center-scan.md`). Sean is open to a better option later; a sender-filtered forward is the cloud-only alternative.
- Council member: Carl Wilson, Nov 24 10am, 224 West 30th Street, Suite 1206, with Sam and Maureen. Timeline updated.
- San Francisco talk is the St. Joseph's event, Jan 23. Timeline marked confirmed.
- AR launch: fully finalized by Dec 1, likely sooner. Timeline shows Dec 1 as a target (dashed).
- Morning brief: dropped (paused); On Deck is the replacement. Weekly advisor: keep, repointed.

Round 2 (later Nov 15): see `docs/instructions-round-2.md`. Blockers found while building it:
- **Running agenda doc** (`1lqzyGEjkrBqdE6-4OO6KpLR2JECcHQiM2VhIeAt6x6c`, Sam's): the connectors get "permission denied". Sam needs to give sean@seanfader.com edit access (or Sean opens it once from that account) before For Thursday items can be written into it.
- **Absence email templates:** location unknown; the attendance step needs them.
- **Kevin's tracker vs Sean's records** disagree on Heritage Alliance (Kevin: declined; Sean: submitted), Ford Good Neighbor (Kevin: awarded; Sean: 2028 prospect) and Knight (Kevin: "closed, not a fit"; Sean: warm, stalled). Possible duplicates: NYU Arts and Humanities Exploration vs Sean's NYU records; two NYC Cultural Affairs records. A second Couch gift (Sep 3 2026, donor-advised fund, amount unknown).
- **Fast vs morning scans:** create two tasks; write the fast one's id into `meta/config.refreshTriggerId`.
- **Maureen's Sunday review email** is the one email any task sends. Confirm with Sean before creating that task.

Still open:
- **Big Goals moves.** The first practice pass fills the places and introducers from the Art Practice Master and his contacts. Sean should review them once.
- **Cv watch** probably has the same Mac binding as the advisor (it carries local folders). Its new prompt may also need approval from a conversation linked to the Mac.

## 3. Switch-on steps (in a cloud session)

1. Re-check every row in section 1 and apply the changes Sean approved.
2. Run the people wiki backfill (`scans/people-wiki.md`, part A) in a supervised session.
3. Create the scan task from `scans/command-center-scan.md` (fresh session per fire, connectors listed at the top of that file). Fire it once by hand and read its output.
4. Open the page, confirm items appear, then write `meta/config` = `{live: true, scanTriggerId: "<new trig id>"}` with ArtifactData.
5. Create the CV watch, QAM social and monthly wiki backup tasks (or update the existing CV watch task).
6. Retire the tasks marked "retire" above, and unpin the old Command Center only when Sean says so.
