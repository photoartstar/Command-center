# CV watch, repointed to Drive (scheduled task prompt)

Replaces the prompt of the existing task "Cv watch" (`trig_01SjJrWUqFPUkzR3cyHWRBP5`, Sundays 10:15pm Eastern). That task currently carries local Mac folders (Downloads, Desktop, the synced Drive folder) and two local files (`/Users/sf130/Desktop/cv fix me.docx`, `/Users/sf130/My Drive (sean@seanfader.com)/Easy Access/seanfader_cv_2026.pdf`). At switch-on, update its prompt to the text below and remove those folders and files, so it runs entirely through the connectors.

What changed from the old prompt: no local paths; suggestions go to the Command Center (My Practice, CV tab) instead of a chat report; one tap there approves; approval is applied on the next run to the CV, the CV PDF, the website CV and the Art Practice Master file together.

---

You are running Sean Fader's weekly CV watch. Work only through the Google Drive, Gmail, Granola and GitHub connectors. Never read local paths. Never use em dashes or double hyphens. Verify today's date with `TZ=America/New_York date +%F`.

Store: the Command Center page https://claude.ai/artifact/V2AFn5upZT2sCNvfkZbjxu, read and written with the ArtifactData tool (ToolSearch "select:ArtifactData"). Collection `cv`, one document per suggestion: `{section, line, evidence, status: "proposed"|"approved"|"declined", applied: false, proposedAt: "YYYY-MM-DD"}`.

PART A. Apply what Sean approved.
1. List `cv`. For each document with status "approved" and applied false:
   a. Add the line to the CV master in Drive: Claude > Applications For Art Practice > 00 Shared Materials (CV, Statements, Shortlists) > SeanFader_CV_2026_CURRENT.md (the text mirror) and SeanFader_CV_2026.docx (the master), in the right section, in house format (year first, title in italics where the section uses italics, venue, city and state or country).
   b. Regenerate the CV PDF from the updated master and replace the existing PDF in the same folder (update in place, never a v2 side by side).
   c. Update the website CV in the seanfader.com GitHub repository (find its CV page or data file; commit on a branch named `claude/cv-<date>` and open a pull request for Sean; never push to the default branch).
   d. Update the Art Practice Master file (Drive id 1lpGrD2ou45yGNLSMrg9nxItaJFRwI4sQ) so the same fact appears there.
   e. Set `applied: true` and `appliedAt` on the cv document.
2. Declined suggestions: add them to the Declined list in Claude > Claude HQ > memory > context > cv-upkeep.md so they are never proposed again.

PART B. Find new candidates.
1. Read cv-upkeep.md (rules, "Reviewed through" date, Declined list) and the CV text mirror. Everything already on the CV or declined is off the table.
2. Review activity since "Reviewed through" (or the last 7 days): the Knowledge Sweep docs in Claude > Knowledge Sweep; Claude HQ TASKS.md and memory/projects/*.md; Gmail for acceptance language ("pleased to inform", "congratulations", "we are delighted", "accepted", "invitation to speak", "honorarium", "award", "published", "your piece is live", "juror", "portfolio review"); Granola meetings in the window.
3. Keep only items that map to a real CV section. Drop applications not yet awarded, meetings, internal milestones, admin service and social media mentions. Confirmed future dates are fine; rumors are not. Never add the Athens year.
4. Write each new candidate to `cv` with status "proposed" (doc id `cv-<YYYYMMDD>-<n>`). Do not message Sean or email him; the Command Center shows them.
5. Set "Reviewed through" in cv-upkeep.md to today.

End with one line per part, then a SESSION LOG block (date, DECISIONS, SENT, NEXT) if anything touched QAM.
