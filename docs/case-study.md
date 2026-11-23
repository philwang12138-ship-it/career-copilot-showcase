# Product case study

## 1. Context

Career Copilot began with a practical observation: job seekers do not lack isolated AI answers; they lack continuity. A useful answer about one job description is often lost before the next application, while personal experiences are repeatedly rewritten from memory.

The product therefore starts with structured memory. AI is applied on top of records with provenance, verification status, and explicit write boundaries.

## 2. Target user

The initial user is a student or early-career candidate applying across related roles, especially AI product, operations, strategy, and business functions. They need to:

- understand what different roles actually require;
- reuse verified experience without exaggerating it;
- decide which opportunities deserve limited application time;
- learn systematically from interviews;
- keep sensitive career information private.

## 3. Product decisions

### Separate facts from interpretations

Experience records carry an evidence status. Verified facts, partially verified claims, assumptions, and future plans are not treated as interchangeable. This reduces the risk that AI-generated language becomes a false autobiographical claim.

### Preserve the original context

Job descriptions retain source and collection date. Interview questions retain the original wording, follow-ups, company, role, round, and interview session. A normalized question can link to multiple real occurrences without losing context.

### Make AI writes reversible and visible

The assistant does not directly mutate career records. It prepares a proposed change, returns a diff for review, and commits only after explicit confirmation. Idempotency and audit information reduce accidental duplicate writes.

### Optimize for a working personal tool first

The first version uses a lightweight web interface and a monolithic service. This reduces deployment and maintenance overhead while keeping the data model portable to a more complex frontend or multi-user product later.

## 4. Key user journey

1. Save a job description with source and date.
2. Ask the assistant to extract requirements and compare them with verified experience.
3. Review capability gaps and decide whether to prioritize the role.
4. Reuse relevant evidence to adapt resume or interview preparation.
5. After an interview, record the session, original questions, and follow-ups.
6. Revisit those records when preparing for a related role.

## 5. Success signals

For the personal MVP, the most meaningful signals are behavioral rather than vanity metrics:

- less repeated manual organization;
- faster retrieval of relevant experience evidence;
- clearer reasoning behind application priorities;
- more interview questions connected to real sessions;
- zero silent AI writes and zero published private records.

## 6. What I learned

- AI product quality depends heavily on information boundaries, not only model capability.
- A “memory” feature is useful only when records have provenance and can be corrected.
- Privacy is part of the product architecture, not a disclaimer added at the end.
- For a personal MVP, operational simplicity can be more valuable than a fashionable stack.

## 7. Next steps

- Add a fully synthetic interactive demo for public evaluation.
- Improve job-source synchronization while keeping collection user-authorized.
- Evaluate ranking quality against actual application and interview outcomes.
- Explore a clearer visual explanation of how evidence flows into AI recommendations.

