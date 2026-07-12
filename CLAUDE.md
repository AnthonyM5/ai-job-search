# Job Application Assistant for Anthony Mai

<!-- SETUP: This file is populated by running /setup -->
<!-- After running /setup, all [PLACEHOLDER] tokens will be replaced with your actual information -->

## Role

This repo is a job application workspace. Claude acts as a career advisor and application assistant for Anthony Mai, helping with:

1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

<!-- This section is auto-populated by /setup. You can also fill it in manually. -->

### Identity

- **Name:** Anthony Mai
- **Location:** New York, NY (open to hybrid NYC-based roles or fully remote)
- **Languages:** English (native), Cantonese
- **Status:** Currently employed full-time at Accenture Song
- **LinkedIn headline:** "Software Engineer"

### Education

<!-- List your degrees, most recent first -->

- **Bachelor of Science in Information Science** (-2026) - City University of New York
- **Software Engineering, Full Stack Web Development** - Flatiron School (bootcamp, not a degree)

### Professional Experience

<!-- List your roles, most recent first -->

- **Software Engineer (Product)** (2021 - Present) - **Accenture Song**
  - Owned and shipped end-to-end customer-facing Angular/TypeScript features for high-traffic financial services platforms
  - Led migration of legacy jQuery interfaces to React/TypeScript, reducing UI-related defects by ~30%
  - Built role-based access control, BFF architecture on AWS Lambda, and multi-step branching workflows; standardized Cypress testing across teams
  - Mentored junior engineers and provided technical guidance on frontend architecture, testing strategy, and code quality
- **Web Content Specialist** (2019 - 2021) - **AJ Madison**
  - Frontend QA and Cypress testing; reduced stale links/broken user flows by ~85% through content system optimization

### Technical Skills

- **Primary:** JavaScript, TypeScript, React, Angular, Redux, RxJS
- **Secondary:** Node.js, Ruby on Rails, SQL, PostgreSQL, Redis
- **Domain:** B2B/enterprise workflow platforms, financial services, frontend architecture (RBAC, BFF, multi-step workflows)
- **Software:** AWS (Lambda, CloudFormation), CI/CD, Cypress, Splunk, New Relic, CloudWatch

### Certifications

<!-- List relevant certifications with dates -->

- **AWS Certified Cloud Practitioner**
- **Google IT Support Professional Certificate**
- **Google Data Analytics Professional Certificate**

### Publications

<!-- List peer-reviewed publications, if any -->

None currently.

### Awards

<!-- List relevant awards, hackathons, competitions -->

None currently.

### Behavioral Profile

<!-- Your behavioral assessment results (PI, DISC, Myers-Briggs, or self-assessment) -->

- **Collaborative** - Does best work pairing and coordinating closely with a team, thrives in fast-paced, high-ambiguity environments
- **Consensus-driven** - Prefers to align stakeholders before committing to a direction; detailed, thorough communicator
- **Mentoring** - Guides junior engineers on frontend architecture, testing strategy, and code quality; raises team-wide standards rather than only shipping individually
- **Strengths:** Comfort with ambiguity, cross-functional collaboration, ownership of complex frontend systems, mentoring and technical guidance
- **Growth areas:** Consensus-seeking style can be reframed as stakeholder-alignment strength; still building architecture/infrastructure-level ownership
- **Thrives in:** Fast-paced, collaborative teams with clear ownership boundaries and minimal process overhead

### What Excites You

<!-- What motivates you professionally -->

- Growing into architecture and infrastructure-level engineering decisions
- Complex frontend systems work: multi-step workflows, BFF layers, access control

### Target Sectors

<!-- Industries and companies you're targeting -->

- Frontend/Product Engineering: B2B and enterprise SaaS companies
- Full Stack (Node/Ruby): companies offering growth into backend/architecture ownership

### Deal-breakers

<!-- Hard constraints on job search -->

- Must be remote or hybrid (NYC-based) - no fully on-site outside NYC, no relocation
- Baseline salary target ~$140k

## Repo Structure

- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `.agents/skills/` - Job search CLI tools

## Workflow for New Job Applications

1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist

After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy

- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting

- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency

- [ ] CV follows the standard 2-page moderncv/banking format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality

- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter is addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits approximately one page

### Compiled PDF verification (MANDATORY - never skip)

Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:

- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** - not 1, not 3
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of a page with its bullets spilling to the next page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`

### ATS & keyword verification (CV)

ATS parsers read the PDF's embedded text layer, not the rendered page. Extract it with `pdftotext -layout` and verify what a parser sees. `pdftotext` (poppler) is optional - if missing, skip the parseability items with a warning and check keyword coverage from the visual PDF read instead.

- [ ] CV text layer extracts cleanly - no `(cid:*)` markers, `�` replacement characters, or text visible in the PDF but absent from the extraction
- [ ] Email and phone appear as **literal text** in the extraction (icon-glyph noise like `MOBILE-ALT`/`Envelope` is harmless, but a contact detail carried only by an icon or hyperlink is invisible to ATS)
- [ ] Reading order of the extracted text matches the visual order (single-column stock template is safe; multi-column custom templates are where this breaks)
- [ ] Posting keywords covered or honestly absent - synonym-only matches tightened to the posting's exact term where truthfully applicable, keywords the profile genuinely supports added to experience bullets, genuine gaps left visible and **never stuffed**
