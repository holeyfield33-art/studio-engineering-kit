# Short verification examples

See also the concrete before-and-after illustrations in [before-after.md](before-after.md).

## Multi-user data

Request: "Build a SaaS app with user accounts."

Kit-guided agent should consider:
- Server-side check that the authenticated user owns or is allowed to access the record being read or modified.
- At least one negative test: user A cannot read or write user B's data.

## Form / API mutation

Request: "Add a form that saves the appointment."

Kit-guided agent should consider:
- Validation of required fields and sensible error responses.
- Negative case: missing required field or unauthorized caller is rejected.

## Existing project change

Request: "Fix this bug without breaking the rest."

Kit-guided agent should:
- Identify the relevant existing tests.
- Run them before and after the change.
- Note any NOT_RUN checks instead of claiming a pass.

These are proportional checks, not a full audit. For fuller before/after illustrations of ordinary vs kit-guided behavior, see [before-after.md](before-after.md).


## A documented Studio pilot (observed, not a before/after agent comparison)

In [STUDIO-PILOT-002](https://github.com/holeyfield33-art/software-research-studio/blob/main/experiments/agent_b_scanplan/trials/STUDIO-PILOT-002/README.md), an offline CLI failed on an escaped unpaired Unicode surrogate. The report records a red test phase with 1 failure and 4 errors across 23 tests, then a narrowly scoped validation fix followed by **23/23 local tests passing**. A positive control preserved international/emoji inputs and unchanged demo output.

**Limits:** This verifies a particular local code repair and regression check. The independent comparison arm was `NOT_RUN`, canonical host acceptance was `NOT_RUN`, and release remained `HOLD`. It **does not** show that buyers' coding agents improve after installing this kit. The [comparison protocol](https://github.com/holeyfield33-art/software-research-studio/blob/main/experiments/agent_b_scanplan/trials/STUDIO-PILOT-002/COMPARISON_PROTOCOL.md) remains unexecuted.
