# CI cost policy for Marqov repositories

This is the default for new and maintained repositories. Each repository must implement it in its own workflows; this document does not change organization settings or required checks.

- Develop in draft pull requests. Skip automatic planners, builds and test matrices at the job level while a PR is draft, before allocating a runner. Include `ready_for_review` so the full applicable checks run when review begins.
- Batch related changes and run focused checks locally before one push. Do not repeatedly rerun workflows without new evidence or a corrected prerequisite.
- Cancel superseded PR checks by PR number. Preserve manual, release and publication workflows and their cancellation rules.
- Keep existing required check names and branch protection. Do not use blanket workflow-level `paths-ignore` rules that leave required checks pending.
- Classify changed files conservatively. Prose-only changes may skip executable tests; tests, fixtures, dependency locks, requirements, build configuration, workflow files and scripts embedded under docs still require their applicable checks. Check both sides of renames and fail closed on missing or truncated change lists.
- Retain existing documentation/link validation and secret scanning on prose where configured. A documentation edit can still contain credentials or broken links.
- Preserve release, tag, manual and scheduled coverage. Avoid duplicate feature-branch push and PR builds when the PR checks already cover them.
- A skipped test is not evidence that executable code passed. Any aggregate required gate must reject planner failure, unknown outputs and missing expected job results, and permit skips only for a valid draft or prose-only decision.

Review the workflow and configured required checks when adopting this policy. Repositories without workflows need no new paid runner merely to claim compliance. Changing a budget or purchasing capacity is a separate owner decision.
