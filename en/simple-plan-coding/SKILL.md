---
name: simple-plan-coding
description: Use when making a plan for a programming task.
---

## Steps

The word "approach" below can also be understood as "plan" or "proposal"; they mean roughly the same thing here.

1. Think through whether the user's proposed approach has any hidden risks, and whether there is a better option. Nothing is more inefficient than efficiently doing something that should not have been done in the first place.

2. Present one or more initial approaches. Describe each in a short paragraph, then ask the user which initial approach they agree with.

3. For the approach the user agrees with, give one more level of detail for (1) the implementation approach and (2) the testing approach. Note that this means one more level of detail, not a very detailed implementation plan. Create a new file to store this approach.
   - **Requirement 1: write the approach top-down.** Think about how human engineers plan: what abstractions are needed to satisfy the request, then roughly how those abstractions should be implemented.
   - **Requirement 2: the plan should preferably not exceed one-tenth of the number of changed lines after implementation starts.** If something can be explained clearly in 50 lines, do not use 100. If the same idea has already been written earlier in the plan document, do not repeat it later.
   - As long as these two requirements are met, you may choose any format that works, such as ASCII or Mermaid diagrams, pseudocode, or natural-language design notes.

4. After the user agrees to start implementation, start working. You can only write no more than about 100 lines of code at a time, then wait for the user's confirmation. After the user confirms the code is fine, commit once as a backup. The commit message should start with `"partial-feat/refactor/fix..."`. Before committing, only check `git status`; do not use `git diff`.

## Notes

- Stop and ask when you hit a key question. If a reasonable assumption can be made, keep going and state that assumption clearly in the plan.
  - "Key question" includes, but is not limited to, issues that would make the plan non-executable or create major divergence in technical direction, or issues where no reasonable assumption can be made.
- Until the user explicitly says to start implementation, you are still in the planning phase. During that time, do not modify any existing code files.
- If the design changes during implementation, update the original plan too.
- If the existing code has flaws that will interfere with the work, such as oversized files, blurry boundaries, or confused responsibilities, the design should include targeted improvements for those issues.
