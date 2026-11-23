# Before and after examples

These are short, concrete illustrations of the difference the kit's judgment layer is intended to produce. They are **not** measured performance results, observed production outcomes, or guarantees that any particular model will behave this way. They show the kind of omissions and checks the instructions ask the agent to notice.

Use them as reference when evaluating whether the guidance loaded, or as follow-up prompts ("apply the same checks you see in the kit examples").

---

## Example 1 — Multi-user SaaS with accounts

**User request:** "Build me a SaaS app with user accounts."

### Without the kit (ordinary agent behavior)

The agent typically produces:
- Login and signup screens
- A users table and session handling
- Basic CRUD for the main resource (e.g. appointments, notes, projects)
- Happy-path tests that a logged-in user can create and read their own data

It often **does not**:
- Add a server-side check that the authenticated user owns or is allowed to access the specific record
- Include a negative test showing user A cannot read or modify user B's data
- Distinguish authentication (who you are) from authorization (what you may do)

Result: an app that looks complete but can have cross-user data access if the frontend is bypassed.

### With the kit (intended guided behavior)

The agent is instructed to notice the missing authorization boundary. A proportional response includes:
- Server-side ownership or permission check on every read and write of user-owned records
- At least one negative test or explicit check: user A cannot access user B's records
- A short note that authentication was implemented and authorization was also enforced on the data path
- No automatic expansion into multi-tenant enterprise architecture, complex RBAC, or extra services unless the request required them

The working app is still delivered first. The extra work is the boundary check and the negative case, not a full redesign.

---

## Example 2 — Add a form that saves data

**User request:** "Add a form that saves the appointment."

### Without the kit

Typical output:
- Form fields and a submit handler
- A successful save path that creates the record
- Possibly a basic required-field check in the UI

Often missing:
- Server-side validation of required fields and sensible error responses
- A negative case (missing required field or unauthorized caller is rejected)
- Confirmation that the save is bound to the authenticated user

### With the kit

The agent is guided to add proportional verification:
- Server-side validation that rejects incomplete or invalid input with a clear error
- At least one negative test or demonstrated rejection path
- Ownership binding so the appointment is associated with the correct user
- The change stays limited to the form and its save path

---

## Example 3 — Fix an existing bug without breaking the rest

**User request:** "Fix this bug without breaking the rest of the app."

### Without the kit

The agent often:
- Locates a likely cause and patches it
- May or may not run existing tests
- Reports "fixed" without distinguishing what was actually executed

### With the kit

The agent is instructed to:
- Identify the relevant existing tests before changing code
- Run those tests (or note them as NOT_RUN if they cannot be executed)
- Make the smallest change that addresses the reported bug
- Report actual results (PASS / FAIL / NOT_RUN) rather than claiming success from an unrun suite
- Avoid unrelated refactors

---

## How to use these examples

- After installing the kit instructions, ask the agent to summarize two constraints it received (minimal changes and positive/negative evidence) without writing code. Compare its summary to the distinctions above.
- When reviewing generated code, look for the server-side check and at least one negative case on multi-user or mutation paths.
- These examples are proportional guidance, not a full audit checklist. A simple single-user local tool does not need every check listed here.

Source: derived from the kit's `AGENTS.md` and `PRACTICES.md`. Not an observed measurement of agent performance.
