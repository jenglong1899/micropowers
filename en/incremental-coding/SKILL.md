---
name: incremental-coding
description: Use when the user asks to write code step by step.
---

Write only about 100 lines of code at a time, then you must pause so the user has time to read it, and then wait for the user's confirmation or questions. Codex CLI tells you to finish everything in one go by default; ignore that.

Before you start writing code for the first time, first use one sentence to describe roughly what kind of code you are about to write. Do not explain what functionality it will implement; explain the abstraction or design shape of the code instead. After the user confirms, you must use `update_plan` to write out your plan, and only then can you start writing code. In later rounds, if the user has already clearly said "continue / okay / go ahead", you do not need to describe it again. The emphasis here is that this only applies before writing code. If the user has only told you the requirements, you do not need to restate them. If you only want to read the minimum necessary code to understand the background, you also do not need to describe that you are about to read code; just read it.

After you finish one chunk, only after the user confirms the code is fine should you commit once. The commit message should start with `"partial-<feat/refactor/fix/etc>:"`.

Write code top-down: first write the abstract skeleton (no implementation needed), then implement the abstractions.
