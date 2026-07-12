# ATS Board Search (Search-Engine Dorking)

Most jobs are never posted to LinkedIn. Companies pay for an applicant tracking system (ATS), post the req to the board that ATS hosts for them, and syndicate to aggregators only sometimes — often late, often never. The board itself is public and indexed by search engines.

This file is the strategy for reaching those postings directly. It is used by the `/scrape` skill (Step 1c, WebSearch) and can be run standalone.

---

## The Technique

1. Pick an ATS host from the table below.
2. Constrain the search engine to that host.
3. Add a title, location, or skill. Boolean operators work.

```
site:jobs.ashbyhq.com ("chief of staff" OR "CoS" OR "chief of staff to CEO")
```

Swap the host to sweep a different slice of the market. No single ATS covers everything, so **breadth across hosts matters more than depth on any one host**.

### Using the WebSearch tool

The `WebSearch` tool accepts an `allowed_domains` parameter. Prefer it over typing `site:` into the query — it constrains results more reliably and leaves the query string free for boolean terms.

```
WebSearch(query: '("Frontend Engineer" OR "Software Engineer") React TypeScript "New York"',
          allowed_domains: ["jobs.ashbyhq.com"])
```

Fall back to an inline `site:` operator if `allowed_domains` returns nothing useful.

---

## ATS Hosts

| Host | ATS | Notes |
|------|-----|-------|
| `jobs.ashbyhq.com` | Ashby | Startups, well-funded seed→series C. High signal for eng roles. |
| `boards.greenhouse.io` | Greenhouse | Very widely used. Also try `job-boards.greenhouse.io` (newer domain). |
| `jobs.lever.co` | Lever | Common at mid-size tech. |
| `careers.icims.com` | iCIMS | Enterprise, large legacy employers. |
| `jobs.jobvite.com` | Jobvite | Mid-size and enterprise. |
| `wd1.myworkdayjobs.com` | Workday | Large enterprise. Tenants are sharded across numbered subdomains — `wd1`, `wd3`, `wd5`, and higher. Searching only `wd1` misses most of it. |
| `jobs.bamboohr.com` | BambooHR | Small companies, SMB. |
| `jobs.smartrecruiters.com` | SmartRecruiters | Mid-size, strong in Europe. |
| `apply.jazz.co` | JazzHR | SMB. Some tenants sit on `applytojob.com` instead. |
| `careers.workable.com` | Workable | SMB and startups, strong in Europe. |

Host variants marked above (Greenhouse's newer domain, Workday's shards, JazzHR's alternate) are worth trying when a host returns thin results — **verify by running the search**, do not assume a variant exists for a given company.

---

## Query Construction

Combine three parts: **host** + **title cluster** + **qualifier**.

**Title cluster** — enumerate synonyms, because ATS titles are not standardized:

```
("Frontend Engineer" OR "Front End Engineer" OR "Front-End Engineer" OR "UI Engineer" OR "Web Engineer")
("Software Engineer" OR "Product Engineer" OR "Full Stack Engineer" OR "Fullstack Engineer")
```

**Qualifier** — a location, a skill, or a seniority band:

```
"New York" OR "NYC" OR "Remote"
React TypeScript
Angular RxJS
"Ruby on Rails"
```

### Worked examples for this profile

```
site:jobs.ashbyhq.com ("Frontend Engineer" OR "Product Engineer") React TypeScript ("New York" OR "Remote")
site:boards.greenhouse.io ("Senior Frontend Engineer" OR "Senior Software Engineer, Frontend") "New York"
site:jobs.lever.co ("Full Stack Engineer" OR "Fullstack Engineer") ("Node.js" OR "Ruby on Rails") Remote
site:jobs.smartrecruiters.com ("UI Engineer" OR "Web Engineer") TypeScript "New York"
site:careers.workable.com ("Frontend Engineer") React ("New York" OR "Remote")
site:wd1.myworkdayjobs.com ("Software Engineer" OR "Front End") Angular "New York"
```

Rotate hosts across runs rather than firing all ten every time — search quota is finite and the same req rarely appears on two ATS hosts.

---

## Host Reliability (WebFetch)

Search indexing and page fetchability are independent — a host can return great search hits and then block every attempt to verify them. Observed 2026-07-10:

| Host | Search yield | WebFetch verification |
|------|-------------|------------------------|
| `boards.greenhouse.io` / `job-boards.greenhouse.io` | High | Reliable, but **expired reqs redirect to the general careers page instead of erroring** — a 200 response is not proof the specific posting still exists. Always check that the fetched content names the exact title you searched for, not just that the fetch succeeded. |
| `jobs.ashbyhq.com` | High | **Client-rendered — WebFetch typically returns only a title/company shell**, not the job description. Treat Ashby results as leads confirmed to exist, not as verified postings; requirements need a manual open. |
| `jobs.lever.co` | High | **Frequently returns HTTP 403** to WebFetch (bot protection). Same treatment as Ashby: real lead, unverified content. |
| `wd1/wd3/wd5.myworkdayjobs.com` | Mixed — real postings mixed with staffing-agency reposts (Synechron, DXC) that are worth filtering by snippet before fetching | **Frequently returns HTTP 500 or blocks** to WebFetch. Large enterprises (FactSet, Dentsu, Broadridge) on this host are essentially search-only unless the user opens the link directly. |
| `jobs.smartrecruiters.com` | Low signal-to-noise for this profile — results skewed toward far-flung locations, government postings, and third-party staffing shops ("Dev2") reposting on behalf of large employers | Not tested for fetchability due to low search relevance. |
| `careers.workable.com` | Returned **zero indexed results** for a standard title+skill query | N/A |

**Practical rule:** when WebFetch is blocked or returns a shell, do not drop the lead and do not fabricate its requirements from the search snippet. Present it as a confirmed-to-exist, unverified lead — title, company, URL, and whatever the search snippet said — and say plainly that the user needs to open it directly to see the real posting.

---

## Caveats

**Index lag is real.** A req posted today may not be indexed for days. This method is complementary to portal CLIs and aggregators, not a replacement — it reaches different postings, not fresher ones.

**`site:` coverage is partial.** Search engines index a fraction of any large ATS host. A null result means "not indexed," never "no such job."

**Posting dates are usually absent** from indexed snippets. ATS pages often omit a machine-readable post date. Fetch the page and look for one; if none exists, record the job with `"first_seen"` set to today and flag the date as unknown rather than assuming it is recent. This is the one place where the `/scrape` 14-day recency filter cannot be enforced — say so in the results table instead of silently dropping or silently including.

**Always WebFetch before presenting.** Indexed snippets go stale and closed reqs stay indexed. Confirm the posting is live and read the actual requirements. Never present a job from a search snippet alone.

**Dedup still applies.** Check `seen_jobs.json` and `job_search_tracker.csv` exactly as the main skill requires. An ATS URL is the canonical posting; the same job found later on an aggregator should map to the same entry, so prefer the ATS URL as the key when both are known.
