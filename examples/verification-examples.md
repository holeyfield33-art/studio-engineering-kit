# Short verification examples

## Multi-user data

Request: “Build a SaaS app with user accounts.”

Kit-guided agent should consider:
- Server-side check that the authenticated user owns or is allowed to access the record being read or modified.
- At least one negative test: user A cannot read or write user B’s data.

## Form / API mutation

Request: “Add a form that saves the appointment.”

Kit-guided agent should consider:
- Validation of required fields and sensible error responses.
- Negative case: missing required field or unauthorized caller is rejected.

## Existing project change

Request: “Fix this bug without breaking the rest.”

Kit-guided agent should:
- Identify the relevant existing tests.
- Run them before and after the change.
- Note any NOT_RUN checks instead of claiming a pass.

These are proportional checks, not a full audit.
