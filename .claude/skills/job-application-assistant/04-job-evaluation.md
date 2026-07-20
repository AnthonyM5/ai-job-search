# Job Evaluation Framework

<!-- SETUP: Skill match areas and career goals are personalized by running /setup -->

## Scoring Dimensions

Evaluate each job posting against these five dimensions:

### 1. Technical Skills Match (0-100)
How well do the required/preferred skills align with the candidate's capabilities?

| Score | Meaning |
|-------|---------|
| 80-100 | Core requirements are primary skills |
| 60-79 | Most requirements match, 1-2 gaps that are learnable |
| 40-59 | Partial match, significant upskilling needed |
| 0-39 | Fundamental mismatch |

**Strong match areas:** JavaScript/TypeScript, React, Angular, Redux, NgRx, RxJS, CSS, Cypress, frontend architecture (BFF, RBAC, multi-step workflows)
**Moderate match areas:** Node.js, Ruby on Rails, AWS (Lambda, CloudFormation), PostgreSQL, Redis, CI/CD, observability (Splunk/New Relic/CloudWatch)
**Weak match areas:** Backend-heavy/infrastructure-first roles, roles requiring deep systems/architecture ownership (growth area, not yet demonstrated at senior/staff level)

### 2. Experience Match (0-100)
Does work history align with what they're looking for?

| Score | Meaning |
|-------|---------|
| 80-100 | Direct experience in the same domain and role type |
| 60-79 | Related experience, transferable skills clear |
| 40-59 | Adjacent experience, would need to make the case |
| 0-39 | Unrelated experience |

**Strong:** Frontend/Product Engineer roles (Angular, React, TypeScript) in B2B/enterprise SaaS or financial services
**Moderate:** Full-stack roles (Node.js/Ruby backend + frontend), roles with a BFF/API layer component
**Entry-level:** Backend-only or infrastructure/platform engineering roles

### 3. Behavioral/Culture Fit (0-100)
Does the role and company culture match the behavioral profile?

| Score | Meaning |
|-------|---------|
| 80-100 | Culture strongly matches behavioral preferences |
| 60-79 | Mixed signals but mostly compatible |
| 40-59 | Some friction areas |
| 0-39 | Significant culture mismatch |

**Red flags to research:** Department disorganization, work dominated by maintenance over development, poor chemistry with leadership, culture mismatches. Check reviews, media coverage, LinkedIn connections, and network contacts for insider perspective.

### 4. Location & Logistics (Pass/Fail + Notes)
- Within commute range: PASS
- Remote with occasional office: PASS
- Requires relocation: FAIL (deal-breaker)
- Frequent international travel: FLAG (discuss with user)

### 5. Career Alignment & Motivation (0-100)
Does this role advance career goals and contain tasks that energize?

| Score | Meaning |
|-------|---------|
| 80-100 | Strongly aligned with career direction, clear growth path |
| 60-79 | Good role but only partially aligned with long-term goals |
| 40-59 | Decent job but doesn't build toward career goals |
| 0-39 | Dead end or backwards step |

**Career goals:**
- Grow from feature-delivery ownership toward architecture/infrastructure-level decision-making
- Move into Frontend/Product Engineer or Full Stack (Node/Ruby) roles with more system design scope
- Build toward senior/staff-level technical leadership

**Motivation filter:** Evaluate not just whether you *can* do the tasks, but whether the tasks will *energize* you. Consider:
- Tasks that energize: architecture and infrastructure-level decisions, cross-functional collaboration with Product/Design, mentoring, complex frontend systems (workflows, BFF, RBAC)
- Tasks that drain: repetitive maintenance work, excessive meetings/process overhead, unclear ownership boundaries
- Non-task factors: leadership style, department culture, company values, degree of autonomy

**Life situation alignment:** Consider personal constraints:
- **Security**: Currently employed full-time at Accenture Song; not under urgent pressure to leave, evaluate opportunistically
- **Flexibility**: Prefers remote or hybrid (NYC-based); baseline salary target ~$140k
- **Professional development**: Prioritizes roles offering growth into architecture/infrastructure-level engineering, not just lateral frontend moves

### 6. Salary Benchmark (Optional)

If the salary lookup tool is configured (`salary_data.json` exists), look up the company:
```
python salary_lookup.py "<Company Name>" --json
```

If a city is known from the posting, add `--city "<City>"` to narrow results.

Present findings as:
```
### Salary Benchmark
| Metric | Value |
|--------|-------|
| [Category] index | XX.X (+/-X.X% vs baseline) |
| Overall index | XX.X (+/-X.X% vs baseline) |
```

Interpret results relative to the baseline defined in the data file's metadata. For index-based data, higher typically means above-market compensation.

If the salary tool is not configured, skip this section.

## Output Format

Present the evaluation as:

```
## Job Fit Evaluation: [Role] at [Company]

| Dimension | Score | Notes |
|-----------|-------|-------|
| Technical Skills | XX/100 | [brief note] |
| Experience Match | XX/100 | [brief note] |
| Behavioral Fit | XX/100 | [brief note] |
| Location | PASS/FAIL | [brief note] |
| Career Alignment | XX/100 | [brief note] |

**Overall Score: XX/100** (weighted average of scored dimensions)

### Verdict: [Strong Fit / Good Fit / Moderate Fit / Weak Fit / Poor Fit]

### Key Strengths for This Role
- [bullet points]

### Gaps to Address
- [bullet points]

### Recommendation
[1-2 sentences: apply/skip/apply with caveats]

### Company Research Checklist
- [ ] Checked company website (mission, values, recent news)
- [ ] Checked review sites (Glassdoor, Jobindex, etc.)
- [ ] Checked LinkedIn for team size, recent hires, connections
- [ ] Checked media for restructuring, growth, or workplace issues
- [ ] Identified network contacts who may know the team/manager
```

## Weighting
- Technical Skills: 30%
- Experience Match: 25%
- Behavioral Fit: 15%
- Career Alignment: 30%

(Location is pass/fail, not weighted)

## Thresholds
- **Strong Fit** (75+): Definitely apply, tailor everything
- **Good Fit** (60-74): Apply, address gaps in cover letter
- **Moderate Fit** (45-59): Consider carefully, discuss with user
- **Weak Fit** (30-44): Probably skip unless strategic reasons
- **Poor Fit** (<30): Skip

## Calibration from Past Applications

<!-- Populated by /setup Path A from resolved (non-in_progress) outcome.md records only -->

As of 2026-07-16, 3 applications have a final outcome, all `rejected` at the resume-screen stage with no interview reached: Braze (Senior Software Engineer, Frontend Infrastructure), Spotify (Frontend Engineer - Music, triage-scored 76.8/Strong Fit on paper), and Spotify (Web Engineer - Podcast). All three share a common thread: materials were either untailored (applied directly on the company site, outside the `/apply` workflow) or predated the profile corrections made this cycle (degree name, tenure, certifications).

By contrast, none of the 5 `/apply`-drafted, `/rank`-verified applications currently `in_progress` (Virtu, Nourish, Kensho, Kin Insurance, Schonfeld) have been rejected at resume screen — Kin Insurance has already reached a live interview stage.

**Preliminary signal, not a proven trend** given the small sample and several still-pending resolutions: resume-screen rejections so far correlate with skipping the `/apply` drafter-reviewer workflow, not with underlying fit. Re-evaluate this section once more applications resolve.

## Pre-Application: Call the Employer (Best Practice)

Before writing the application, consider whether the candidate should call the contact person listed in the posting. **Only call if there are substantive questions** - never call just to "be remembered."

### When to Suggest Calling
- The posting has unclear or ambiguous requirements
- It's unclear which competencies are essential vs. nice-to-have
- The role description is vague about day-to-day tasks
- There's a named contact person who invites questions

### Good Questions to Ask
- "What are the primary challenges in this role?"
- "How is time typically divided across the listed responsibilities?"
- "Which competencies are most critical for success in this position?"
- "What does success look like in the first 6-12 months?"

### Rules for the Call
- Prepare a 30-second "elevator pitch" about your background in case they ask
- The call's purpose is **gathering information**, not delivering a pitch
- Take notes - use what you learn to tailor the application
- Reference the conversation naturally in the cover letter ("After speaking with [name], I was especially drawn to...")
