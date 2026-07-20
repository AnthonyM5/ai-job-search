# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

<!-- These are populated by /setup from your actual experience. Below are templates showing the format. -->

### 1. RBAC data-source disagreement under SLA pressure (disagreeing well, cross-team problem-solving)

**S:** On a project with a tight SLA, the initial plan called for the frontend team to implement RBAC logic that required standing up a new backend data source built to existing standards — a significant lift given the timeline.
**T:** I disagreed with that approach: I raised with my tech lead that the data-source buildout would push the feature past the SLA, and needed to find a way to meet the deadline without compromising the RBAC logic's data integrity.
**A:** I worked directly with the backend teams to determine whether the attributes RBAC needed already existed somewhere in current datasets. Once we confirmed they did and scoped the exact fields required, we agreed a new dataset wasn't necessary for this feature, and implemented the logic by blending the existing datasets in our Backend-for-Frontend layer, resolving to a simple boolean gate on the frontend.
**R:** The feature shipped on time, meeting the SLA, with no compromise to data integrity. Worth noting honestly: this didn't become a new standing pattern — blending was viable specifically because the needed data already existed elsewhere; a genuinely new data source would still be the right call in cases where it doesn't. The value was in recognizing which situation this was before committing to the heavier build.
**Use for:** "disagreeing with a technical decision," "tough feedback," "working under deadline pressure," "cross-team collaboration"

### 2. [PROJECT_NAME] ([SKILL_DEMONSTRATED])

**S:** [CONTEXT]
**T:** [YOUR RESPONSIBILITY]
**A:** [WHAT YOU DID]
**R:** [OUTCOME]
**Use for:** "[QUESTION_TYPE_1]", "[QUESTION_TYPE_2]"

### 3. [PROJECT_NAME] ([SKILL_DEMONSTRATED])

**S:** [CONTEXT]
**T:** [YOUR RESPONSIBILITY]
**A:** [WHAT YOU DID]
**R:** [OUTCOME]
**Use for:** "[QUESTION_TYPE_1]", "[QUESTION_TYPE_2]"

## STAR Candidates (Complete Manually)

### jQuery to React/TypeScript migration

**Source:** CV - Accenture Song
**What happened:** Led the migration of legacy jQuery-based interfaces to modern React and TypeScript architectures, reducing UI-related defects by ~30%.
**Why it matters:** Answers technical leadership, legacy modernization, and measurable-impact questions.
**S/T/A/R stub:**

- Situation: Codebase with old legacy JS and HTML web pages, primarily using jQuery for DOM manipulation needed an overhaul, and existing contractors needed to be up-skilled in TypeScript/React.
- Task: Simultaneously develop new features and integrate 3rd party vendors using net-new components built in TypeScript, Higher Order Components and other React patterns and up-skill contractors to adhere to new standards.
- Action:

- Result:

### Role-based access control (RBAC) feature work

**Source:** CV - Accenture Song
**What happened:** Owned end-to-end feature work (design, planning, and production support) that implemented RBAC gating across a high-traffic internal Angular application, spanning both associate-role and customer-eligibility privilege logic. Built the supporting Backend-for-Frontend layer (legacy API and dataset integration) that simplified this complex, multi-source business logic down to something the Angular frontend could gate on cleanly.
**Why it matters:** Answers system design, security/entitlement, and complexity-handling questions. Important framing note: this was E2E ownership of feature work that relied on and implemented RBAC gating, not sole ownership of an RBAC system as a standalone platform — keep that distinction precise under follow-up questions.
**S/T/A/R stub:**

- Situation: Building out features to enable associates to assist customers with their debit cards which relied on RBAC for associates, customer eligibility and an emphasis on both accuracy and reliability.
- Task: Design and expand existing debit card service features for customers replacing cards on different networks and at different stages of card-activation - allow specially trained associates to easily service cohorts of customers.
- Action: Worked with the data teams to identify a single source of truth for customer cohorts, implement the proper RBAC gating for UI/UX and weave together disparate datasets, APIs into one central BFF endpoint that simplified business logic for the web app and delivered a clean/clear UX for the associate.
- Result: Enabled debit card servicing features for replacing, re-issuing and reporting lost/stolen across different payment networks and provided E2E testing, on-call production support and triage for incidents.

### Dynamic multi-step workflow (reactivation feature)

**Source:** CV - Accenture Song
**What happened:** Designed and built a multi-step form workflow from scratch in Angular with dynamic branching logic based on associate role and customer inputs.
**Why it matters:** Answers "describe a complex feature you built from scratch" and ambiguity-handling questions.
**S/T/A/R stub:**

- Situation:
- Task:
- Action:
- Result:

### Cypress testing standardization

**Source:** CV - Accenture Song
**What happened:** Standardized an existing but under-adopted Cypress end-to-end testing pattern within my team. Regression testing went from a manual effort spread across multiple sprints down to a few hours - most of the remaining time was sourcing correct mock data in each appropriate environment, not running the tests themselves. Also proposed wider adoption across the mono-repo; whether and how to adopt it was left to each client team's discretion.
**Why it matters:** Answers quality/testing culture and process-improvement questions. Framing note: the pattern already existed org-wide but wasn't widely adopted - the work was standardizing and proving it out within the team, then proposing (not mandating) broader mono-repo adoption. Keep that scope precise under follow-up: you drove team-level adoption and made the proposal, you didn't roll it out across other teams yourself.
**S/T/A/R stub:**

- **S:** An E2E testing pattern already existed in the mono-repo but wasn't widely adopted. Regression testing on our team was manual, ran across multiple sprints, and consumed a lot of time mostly hunting down correct mock data for each environment rather than actually verifying behavior.
- **T:** I wanted to cut that cycle down and make regression confidence something the team could get in hours, not sprints, using the existing pattern rather than inventing a new one.
- **A:** I standardized the existing Cypress end-to-end testing pattern within my team - consistent structure, reusable fixtures/mock-data setup per environment, and repeatable patterns other engineers could extend without re-solving the mock-data problem each time. Once it was working well, I proposed wider adoption across the mono-repo, leaving the decision of whether and how to implement it up to each client team.
- **R:** Regression testing dropped from a multi-sprint manual effort to a few hours on my team, with most of that remaining time being environment-specific mock-data sourcing rather than test execution. The mono-repo-wide proposal was a suggestion, not a mandate - adoption elsewhere was each client team's call.

### Content system reliability fix

**Source:** CV - AJ Madison
**What happened:** Maintained and optimized large-scale product content systems, reducing stale links and broken user flows by ~85%.
**Why it matters:** Answers data-integrity and early-career impact questions.
**S/T/A/R stub:**

- Situation:
- Task:
- Action:
- Result:

### Real-time multi-participant state sync (Socket.io)

**Source:** CV/LinkedIn - Accenture Song
**What happened:** Built real-time, multi-participant state synchronization using Socket.io on a React/Laravel learning platform, syncing mouse movement, input, and drag-and-drop interactions live across a shared Leaflet map session.
**Why it matters:** Answers real-time systems, WebSocket/Socket.io depth, and multi-user collaborative UI questions.
**S/T/A/R stub:**

- Situation:
- Task:
- Action:
- Result:

### Two-way messaging feature (Socket.io/NestJS)

**Source:** CV/LinkedIn - Accenture Song
**What happened:** Built a two-way messaging feature (daycare centers to parents) in an Angular/Ionic mobile app, using Socket.io and NestJS for real-time delivery.
**Why it matters:** Answers mobile/hybrid-app experience, backend-for-real-time-delivery design, and cross-functional (parent/business) product questions.
**S/T/A/R stub:**

- Situation:
- Task:
- Action:
- Result:

<!-- Add more STAR examples as needed. Aim for 4-6 covering different competencies. -->

## Common Tough Questions

### "Why did you leave [previous company]?"

> [PREPARE YOUR ANSWER - be honest, forward-looking, no negativity about former employer]

### "You don't have [specific skill/experience]."

> [PREPARE YOUR ANSWER - acknowledge the gap, bridge to adjacent experience, show willingness to learn]

### "Where do you see yourself in 5 years?"

> [PREPARE YOUR ANSWER - show ambition aligned with the role's growth path]

### "What's your biggest weakness?"

> [PREPARE YOUR ANSWER - genuine weakness with concrete mitigation strategy]

### "Why this company specifically?"

> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role

- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team

- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth

- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)

- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips

- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette

- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes

- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines

When the user asks for interview practice:

1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
