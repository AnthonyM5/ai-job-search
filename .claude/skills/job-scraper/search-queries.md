# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Search Sites

The built-in `.agents/skills/` job-portal CLI tools (Jobindex, Jobbank, Jobdanmark, Jobnet) are Danish-market-specific and do not apply here - Anthony is based in New York, NY. Use LinkedIn and Google `site:` searches instead. Consider running `/add-portal` to build a local search skill for a US-specific board (e.g. Indeed, Wellfound, Dice) if a recurring need shows up.

Primary (US job market):

- **linkedin.com/jobs** - primary source, filter by location (New York, NY / Remote)
- **ATS boards** (Ashby, Greenhouse, Lever, Workday, et al.) - see `ats-boards.md` in this directory. Most reqs are posted here and never syndicated to LinkedIn or aggregators; this is the highest-yield source for postings other candidates never see.
- **builtin.com / builtinnyc.com** - NYC-heavy aggregator, reliably fetchable
- Company career pages via Google `site:` searches for known target companies

## Query Categories

Queries are grouped by priority. Each query should be combined with location terms ("New York, NY" or "Remote") where the site supports it.

### Priority 1: Frontend / Product Engineer

Strongest and most desired career direction - Angular/React/TypeScript-heavy roles with growth into architecture.

```
site:linkedin.com/jobs "Frontend Engineer" OR "Product Engineer" "New York" OR "Remote"
site:linkedin.com/jobs "Senior Frontend Engineer" React TypeScript
"Frontend Engineer" React Angular TypeScript "New York, NY"
```

### Priority 2: Full Stack (Node/Ruby)

Domain expertise expansion - roles offering backend/architecture ownership alongside frontend work.

```
site:linkedin.com/jobs "Full Stack Engineer" Node.js React "New York" OR "Remote"
site:linkedin.com/jobs "Full Stack Engineer" Ruby on Rails
"Full Stack Software Engineer" TypeScript Node.js "New York, NY"
```

### Priority 3: Adjacent Roles

Roles Anthony could pivot into given his BFF/architecture/testing-leadership experience.

```
site:linkedin.com/jobs "UI Engineer" OR "Web Engineer" TypeScript "New York" OR "Remote"
site:linkedin.com/jobs "Software Engineer II" OR "Software Engineer III" React Angular
site:linkedin.com/jobs "Frontend Architect" OR "Staff Frontend Engineer"
```

### Priority 4: Broader Technical

Wider net for general technical roles.

```
site:linkedin.com/jobs "Software Engineer" React TypeScript "New York" OR "Remote"
site:linkedin.com/jobs "JavaScript Developer" OR "TypeScript Developer" "Remote"
```

## Location Filter

When evaluating results, verify the job location matches Anthony's constraints:

- **Ideal:** Fully remote (US-based)
- **Acceptable:** Hybrid roles based in New York, NY (any borough or reasonable commute distance)
- **Borderline:** Hybrid roles requiring frequent travel outside NYC metro - flag and discuss
- **Too far:** On-site-only roles outside the NYC metro area, or any role requiring relocation

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:

- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
