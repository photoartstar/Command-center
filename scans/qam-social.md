# QAM social flow (scheduled task prompts)

Replaces the QAM half of the old "Daily social scan" (`trig_01ADtcMWy62ESTUFps1U73We`, disabled, device_absent). Sean's @photoartstar has no approval flow: the morning scan nudges him the morning after art events. Rules from Sean, Nov 15 2026.

## The plan

Three streams:
1. **Dated calendar:** birthdays of people QAM will memorialize; Trans Day of Remembrance (Nov 20), Trans Day of Visibility (Mar 31), Pride; Matthew Shepard's birthday (Dec 1); key legislative dates (Clinton State of the Union, Jan 19 1999; Obama signing the Shepard Byrd Act, Oct 28 2009).
2. **News posts** as things happen (a new brick, an install, a launch).
3. **Baseline:** 1 to 2 posts a week, Tuesday and Thursday mornings. Check Instagram Insights monthly and adjust.

Weekly rhythm:
- Claude keeps the following week drafted in the Social Posts table (base `appPeWDhXHErd70GJ`, table `tblIE99nz7g8OI68i`).
- Sean approves on the Command Center (QAM, Social tab).
- **Sunday night:** Maureen gets a review email covering the following week's posts, and can also tick "Maureen OK" in Airtable. Both work.
- **Tuesday:** Tasneem gets the following week's approved posts (image folders and instruction cards) and schedules them all in Meta. Questions go to the Thursday meeting.

## One-time setup (supervised session)

Pull what still works from QAM_Instagram_Rollout_ICA_San_Jose_2026 (QAM 04 Comms & Marketing), move that doc to QAM Archive (superseded) (`1UKPqWXqu5PmkLJzaF0PcQYZ5-mQsKTuH`), and write a new lean long-term strategy Sean can realistically keep up with: `QAM_Instagram_Strategy` in QAM 04 Comms & Marketing (`1CjdYZ4OpeKL7FRw1AsWSXyBOitknfSPx`). Update the page's Strategy link to the new doc. Load qam-voice-and-language first.

## Daily social task (part of the morning scan)

Never post, schedule, accept a Collab, message anyone, or change any Meta setting. Never use em dashes or double hyphens. Load the qam-voice-and-language skill before writing any QAM text and design-memory before choosing images.

1. Keep the next 7 to 10 days drafted. For each Tuesday and Thursday baseline slot and each dated-calendar day without a record, create one with Status "Claude draft": Post, Planned date, Format, Caption (draft in the site register for Sean to rewrite), Why this post (one line), Follow, Tag, Collaborators (handles, one per line).
2. Image folder: one subfolder per post in QAM > 04 Comms & Marketing > Instagram Assets, named "YYYY-MM-DD Post title". Copy images in (never move originals). Save the link in Image folder.
3. Learn Maureen's standards from every Maureen notes field. Keep her rules in Claude > Claude HQ > memory > context > qam-social-standards.md (update in place) and apply them.
4. Advance the flow: "Sean approved" + Maureen OK → "Maureen approved". Maureen notes without Maureen OK → "Needs changes", redraft, back to "Claude draft".
5. Alina: never use her face or image on social until Michael Eredia says yes for social specifically (the family approved the show, not social). The backup for memorial posts is to honor people by name with no faces. Never claim a memorial is installed or an oral history recorded unless it has happened.

## Sunday night: Maureen's review email

Send ONE email from sean@seanfader.com to Maureen (mtowey@gmail.com), subject "QAM posts for the week of <date>", listing next week's posts in date order: day, title, caption, image folder link, and a line saying she can reply with changes or tick "Maureen OK" in Airtable. Plain and short. This is the only email any Command Center task sends. If nothing is planned, send nothing.

## Tuesday: Tasneem's handoff

For every post planned in the following week with Status "Maureen approved": create a Task (table `tblgo9znlvM5QJDFG`) with Owner Tasneem, Area Comms, Due that Friday, Notes holding the instruction card (image folder link, caption, who to follow, who to tag, who to invite as Collab), link it to the post, and set Status "With Tasneem". Posts approved by Sean but not Maureen by Tuesday become a For Thursday item.

## Open

Trans Day of Remembrance, Nov 20: to discuss with Maureen at the Thursday Nov 19 meeting (already on the For Thursday list). Sean is asking Michael Eredia about social use of Alina's image.
