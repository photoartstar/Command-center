# QAM people wiki: one-time backfill and monthly backup

Both run against the Contacts table of "QAM Team Tracker (trial)" (base `appPeWDhXHErd70GJ`, table `tblQeHggYxmEK7OEY`). Airtable is the only copy; the Command Center keeps none.

## A. One-time backfill (run once, in a supervised session, after switch-on is approved)

Paste as a session prompt:

---

Build the QAM people wiki in Airtable. Never use em dashes or double hyphens. Never write family, witness or next-of-kin details into Airtable (those stay in QAM 07 Site Data & CRM in Drive). Sam and Maureen read everything you write.

1. Sources: the existing Outreach CRM (`QAM_Outreach_CRM.xlsx` in Drive; search by title), every Granola meeting about QAM (search_meetings with keywords "QAM", "Queer American Memorials", "memorial", plus each existing contact's name), and Gmail history about QAM (sean@seanfader.com; search by contact names, organizations and "Queer American Memorials").
2. Split combined records into one person per record (for example "Andy Cushman and Katrina Stewart" becomes two contacts with the same Organization), keeping the original record for the first person so its links survive.
3. For every person: Name, Organization, Role, Category, Email, Status, Owner, Last touch, Last conversation, Next step, Next step date, Summary (who they are, how we met, what was discussed, what is next), Keywords, Memorials (link), Introduced by (link), Granola notes and Email threads (one line each: date, title, link).
4. Work in batches of 10 records; after each batch list what you changed in two lines.
5. Finish with a count of people added, updated and split, plus any introductions you could not resolve, then a SESSION LOG block.

---

## B. Monthly backup to Drive (scheduled task)

Schedule: the 1st of each month at 8:23pm Eastern, `CRON_TZ=America/New_York 23 20 1 * *`. Fresh session. Connectors: Airtable, Google Drive.

Prompt:

---

Back up the QAM people wiki from Airtable to Google Drive as a small linked wiki. Never use em dashes or double hyphens.

1. Read every record in Contacts (base appPeWDhXHErd70GJ, table tblQeHggYxmEK7OEY), all fields.
2. Target folder: QAM > 06 Team & Updates (id 1bi-XIbxUg8BxCM7KlzVhvtDt_L08kS37) > "People Wiki". Create that subfolder once if it is missing (ask nothing; it is inside QAM 06, not a new top-level folder).
3. Write one Markdown file per person, named `<Name>.md` (disableConversionToGoogleType true), each with: organization and role, status and owner, summary, last conversation, next step and date, keywords, memorials, "Introduced by" and "Introduced" as relative links to the other people's files (`[Name](Name.md)`), and the Granola and email links. Plus `index.md` listing everyone by category with links.
4. Update files in place when they exist (never "v2" copies). Move pages of people deleted from Airtable into QAM Archive (superseded) (id 1UKPqWXqu5PmkLJzaF0PcQYZ5-mQsKTuH). Never delete anything.
5. Report the count in one line and end with a SESSION LOG block.
