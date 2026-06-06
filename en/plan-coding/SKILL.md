---
name: plan-coding
description: Use only when the user explicitly asks to use this skill.
---

## Steps

1. Think through whether the user's proposed approach has any hidden risks, and whether there is a better option. Nothing is more inefficient than efficiently doing something that should not have been done in the first place.

2. Present one or more initial approaches. Describe each in a short paragraph, then ask the user which initial approach they agree with.

3. Create a formal implementation and testing plan, and store it in a new file.
  - **Requirement 1: plan top-down.** Think about how human engineers make plans: what abstractions are needed to satisfy the user's request -> roughly how those abstractions should be implemented.
  - **Requirement 2: the plan must not be too abbreviated.** Otherwise it leaves room for ambiguity, so different people reading the same plan will interpret it differently, which leads to very different implementations.
    - One way to think about it: if the plan does not mention a given interface, data model, and so on, then the final implementation should not introduce those things either.
    - "Not too abbreviated" does not mean writing fluff. If something can be explained clearly in 100 lines, do not use 200. Do not repeat earlier points later using different wording.
  - **Requirement 3: the plan must not be too detailed.** Otherwise it becomes indistinguishable from writing the code directly. A good reference is that the line count should not exceed one-fifth of the number of lines in the actual code change. If requirements 2 and 3 are hard to satisfy at the same time, prioritize requirement 3, because reading a very long plan file is tiring.
  - As long as these three requirements are met, you may choose any format that works, such as ASCII or Mermaid diagrams, pseudocode, or natural-language design notes.

4. After the user agrees to start implementation, read the `incremental-coding` skill and follow its requirements when writing code, unless the task is small or the user explicitly says not to use that skill this time.

## Notes
- Stop and ask when you hit a key question. If a reasonable assumption can be made, keep going and state that assumption clearly in the plan.
  - "Key question" includes, but is not limited to, issues that would make the plan non-executable or create major divergence in technical direction, or issues where no reasonable assumption can be made.
- Until the user explicitly says to start implementation, you are still in the planning phase. During that time, do not modify any existing code files.
- Do not repeat in chat what you have already written in the plan.
- The plan file should be referenced from the project's root `AGENTS.md`, because it acts as a summary of the code and is useful for future fast onboarding.
- If the design changes during implementation, update the original plan too, because the final plan file will be referenced by `AGENTS.md`.
- If the existing code has flaws that will interfere with the work, such as oversized files, blurry boundaries, or confused responsibilities, the design should include targeted improvements for those issues.

---

To repeat the goal of the plan: it should be made top-down, and different people reading the same plan should arrive at the same understanding of it, which means the code they write from that plan should also be roughly the same.
