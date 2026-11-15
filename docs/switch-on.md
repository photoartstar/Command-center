# Switch-on checklist

Do not switch the new Command Center on until Sean's Mac is back from the shop and every task below has been checked. "Switch on" means: create the scan task, write its id into the page's `meta/config`, and set `live: true`.

## 1. Tasks that feed or compete with the Command Center (inventory Nov 15 2026)

| Task | Id | Today | Needs before switch-on |
|---|---|---|---|
| Cv watch | trig_01SjJrWUqFPUkzR3cyHWRBP5 | Enabled, Sun 10:15pm. Reads local Desktop, Downloads and synced Drive paths | Replace prompt with `scans/cv-watch.md`; remove local folders and files |
| Qam daily scan (NYU mail, calendar, PSLF, CRM) | trig_01MpPHFTyfcKY3ogFC9KPfKe | Disabled, device_absent. Local QAM_DIR, Chrome for NYU mail, session_info, local QAM_Tracker.html | Retire: the Command Center scan and Airtable replace it. Keep disabled; PSLF check moves to the Money page design |
| Qam weekly advisor | trig_011F26U4X7iF6J49dms5LEfK | Enabled, Mon 7am, but reads local files and finishes in about 3 seconds | Repoint to Airtable + Drive, or pause. Sean to decide |
| QAM morning scan, QAM Items Feed | trig_016PpC6QJoMXcsaV6QKhuZGa | Enabled, 4am, cloud only, reads Kevin's tracker | Keep running for the old Command Center until switch-on, then retire (the new scan reads Kevin's tracker itself) |
| QAM midday catch-up | trig_01AA342cQCrHfZ5r1EQnzzr5 | Enabled, 11am, cloud only | Retire at switch-on (replaced by the 3x daily scan) |
| Funding scan, QAM Funding Feed | trig_016nNYubYJPUNEJGFzTGEofs | Enabled, 4:40am, cloud only | Keep. The new scan reads its feed for practice applications. Never rename "QAM Funding Feed" |
| Weekly funding scan fader qam | trig_014tJ262dAzwLSE14hM1PzqC | Enabled, Mon 4am, writes the same feed | Check it does not collide with the daily funding scan (two writers of one feed) |
| Daily social scan | trig_01ADtcMWy62ESTUFps1U73We | Disabled, device_absent, local folders | QAM half replaced by `scans/qam-social.md`; @photoartstar half goes to the practice scan |
| Nightly knowledge sweep | trig_011ARnNCY79ntmEy9Vi5WTrp | Disabled, device_absent, needs local sessions | Mac-only by design. Re-enable when the Mac is back |
| Morning brief | trig_01PhcBQTiPuhig1V66Hu684R | Enabled, weekdays 7am, new artifact every day | Retire or fold into On Deck. Sean to decide |
| Zoho Books Monday pass, Zoho weekly digest | trig_018YuDF9QNLtPa3icnF8Xv95, trig_01VnjQJgQfTPdwurVtJBTyom | Enabled, cloud only | Keep. Money page design will decide where the digest shows |
| NYC DCLA reminder | trig_015g2115t5mUg8yjJmGeQDo7 | One-shot Jan 15 2027, email notification on | Turn its email notification off (brief: nothing new in his inbox) |
| ANEF attestation watch | trig_01VUGgcPDoMJ4NXa9w3VYXUr | Disabled | Leave off |
| Apple card monthly import, Weekly DMARC scan, Monthly memory consolidation | (see list_triggers) | Enabled | No change |

Three tasks (Morning brief, Funding scan, QAM morning scan) fired recently but have no run record. Check their last session transcripts before relying on them.

## 2. Open questions for Sean

1. **Second Gmail account.** The brief says both Gmail accounts. The Gmail connector reaches only sean@seanfader.com, and a second account cannot be added to it. Options: forward the second account to sean@seanfader.com with a label (he declined this for NYU before), or accept that the scan cannot see it.
2. **AR launch date.** Not set; it shows in the timeline's "No date yet" tray.
3. **San Francisco talk.** Is it the St. Joseph's event on Jan 23? The timeline marks it as to confirm.
4. **Councilman meeting on the 24th.** Which council member? The milestone says only "Councilman meeting".
5. **Morning brief and weekly advisor.** Keep, fold into the Command Center, or retire?
6. **Big Goals moves.** First practice pass fills the places and introducers from the Art Practice Master and his contacts. Sean should review them once.

## 3. Switch-on steps (in a cloud session)

1. Re-check every row in section 1 and apply the changes Sean approved.
2. Run the people wiki backfill (`scans/people-wiki.md`, part A) in a supervised session.
3. Create the scan task from `scans/command-center-scan.md` (fresh session per fire, connectors listed at the top of that file). Fire it once by hand and read its output.
4. Open the page, confirm items appear, then write `meta/config` = `{live: true, scanTriggerId: "<new trig id>"}` with ArtifactData.
5. Create the CV watch, QAM social and monthly wiki backup tasks (or update the existing CV watch task).
6. Retire the tasks marked "retire" above, and unpin the old Command Center only when Sean says so.
