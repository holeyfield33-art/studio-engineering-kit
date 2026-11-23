# SDLC for vibe coders — practical engineering, not paperwork

A software development lifecycle (SDLC) is the way an application moves from an idea through design, implementation, verification, release and maintenance. Its useful purpose is **not** to make every project produce a giant report. It is to keep important decisions and responsibilities from disappearing between prompts.

## Why it matters

An AI tool can produce a working interface quickly while leaving unclear requirements, data ownership, authorization, error states, deployment assumptions or maintenance instructions. **The right question is not “did we complete every lifecycle phase?” but “what can still make this product fail in its actual context?”**

For example, a SaaS app with login may still lack server-side checks that prevent one user from reading another's records. A meaningful acceptance check is an unauthorized access attempt that is denied. An offline command-line tool might instead need reliable malformed-input handling and stable output, not web-session controls.

## Start with four document roles

| Role | Typical location | What it answers |
| --- | --- | --- |
| Purpose and usage | `README.md` | What is this, who uses it, and how can it run? |
| Agent guidance | `AGENTS.md` or existing platform rules | What should this agent respect, and what changes are prohibited? |
| Current truth | `docs/STATUS.md` **if necessary** | What's actually working, blocked, verified and next? |
| Engineering decisions | Existing `docs/SDLC.md`, `docs/ENGINEERING.md` or equivalent **if necessary** | What product-specific boundaries, tests, architecture and release rules matter? |

Add a `docs/PRODUCT.md` only when user journeys, requirements or non-goals need durable detail; a `CHANGELOG.md` for user-visible release history; a dated evidence/decision record for consequential decisions. **Do not create empty files or duplicates.** Existing names are valid. One current status authority is enough.

## A five-minute engineering loop

1. **Understand:** Read the actual repository and user goal. Identify one observed user problem, plus what must stay unchanged.
2. **Notice:** Identify the one or two high-leverage missing considerations, such as auth vs authorization, data ownership, input failures, accessibility or migration, *only when relevant*.
3. **Specify:** Write an observable success condition and, where relevant, a negative/failure condition.
4. **Change:** Apply the smallest coherent fix using existing conventions and normal authorized tools.
5. **Verify and hand off:** Run focused checks, preserve evidence, and say what wasn't run. Update the one current status source when the state materially changed.

### Example: an appointment form

User request: “Add a form so customers can request appointments.”

- Positive behavior: valid requests produce the intended confirmation and persisted record.
- Negative behavior: missing or malformed required fields are rejected without side effects.
- If there are authenticated customers: verify server-side data ownership, not just login UI.
- If a notification or calendar service is involved: consider failure/retry and duplicate submissions.
- If there is no real deployment: do **not** invent production monitoring, incident procedures or pentest certification.

## Get the actual starter templates

The **$9.99 Launch Edition** includes a practical maintained-repository starter with an optional STATUS template, SDLC/engineering contract template, PRODUCT template, installation prompt and platform setup guide. The public core instructions remain free. A purchase link will be added **only after checkout and file delivery have been verified**.

This guide distills the Software Research Studio product intent and adaptive repository knowledge layout (2026-11-01). It is contextual engineering guidance, not proven automated engineering or an OWASP certification.
