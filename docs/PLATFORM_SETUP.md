# Install the Studio Engineering Kit in your coding agent

**Checked against official platform documentation: 2026-11-23.** These are setup routes, not guarantees the model follows every instruction. Always inspect the target project's existing policy and project-specific requirements.

The reusable core is [AGENTS.md](../AGENTS.md). Read [PRACTICES.md](../PRACTICES.md) only for relevant issues and [BOUNDARIES.md](../BOUNDARIES.md) for evidence limitations.

## General installation safety

1. **Inspect first.** Check whether the target already has root or nested `AGENTS.md`, `CLAUDE.md`, `.cursor/rules/` or project instructions. Do not overwrite or bypass existing instructions.
2. **Add only compatible guidance.** Paste the Studio content into an appropriate project instructions field, or merge it into the existing agent entrypoint after the project's owner approves. If you cannot modify project instructions, paste the guidance at the start of a specific chat and make no claim about persistence.
3. **Test loading before coding.** Ask the agent which instructions it actually sees and to summarize the minimal-change and negative-test rules. This verifies only that the instructions are accessible, not the correctness of generated code.
4. **Request one narrow change.** Confirm the actual diff, relevant commands, negative/failure check and unrun checks. The kit does not grant permission to deploy or run live security tests.

## Lovable

Open **Project settings → Instructions** and add the Studio core instructions under the existing project-specific context; do not erase that context. Lovable documents a 10,000-character limit for project instructions. It also reads a top-level `AGENTS.md` or `CLAUDE.md` in the project repository; scoped files apply while it works in those folders. Check the file remains compatible with your current project.

Source: https://docs.lovable.dev/features/knowledge

## Bolt

Open your project settings, select **Knowledge**, append the Studio guidance under **Project instructions**, then save. Bolt includes this knowledge with future prompts. On mobile, open project name → Project settings → Knowledge.

Source: https://support.bolt.new/settings/project-settings

## Cursor

For a simple repository-wide setup, place/merge `AGENTS.md` at the **target project's root**. For more targeted rules, use Cursor's structured `.cursor/rules` functionality, following the platform format. Existing local instructions take precedence; do not clobber them.

Source: https://cursor.com/docs/rules

## Claude Code

Claude Code supports `AGENTS.md` project instructions in versions **2.1.277 and later**, provided the project-instruction setting permits them. By default, `CLAUDE.md` or `CLAUDE.local.md` in the same path chain takes precedence and may prevent direct `AGENTS.md` loading. A safe compatible route is to append `@AGENTS.md` to the existing `CLAUDE.md` after review, or enable reading both kinds of files in Claude Code's settings. Check `/config` and `/context all` against the specific version you use.

Source: https://code.claude.com/docs/en/memory

## What successful installation means

- The agent can restate the working instructions.
- The next task's change remains narrowly scoped.
- The agent identifies applicable omissions and tests **without inventing work or evidence**.
- A missing test result is `NOT_RUN`, never `PASS`.

This is a usability check, not independent proof that the kit improves model performance.
