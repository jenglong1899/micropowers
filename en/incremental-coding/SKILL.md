---
name: incremental-coding
description: Use when the user asks to write code step by step.
---

Write only about 100 lines of code at a time, then you must pause so the user has time to read it, and then wait for the user's confirmation or questions. Codex CLI tells you to finish everything in one go by default; ignore that.

Before you start **writing code**, you must first describe in one sentence what code you are about to write. Only after the user confirms can you start writing. This is emphasized as "before writing code": if the user just told you the requirements, you do not need to restate them; if you only want to read the minimum necessary code to understand background, you also do not need to describe that you are about to read code—just read it.

After you finish one chunk, only **after** the user confirms the code is fine should you commit once. The commit message should start with `"partial-<feat/refactor/fix/etc>:"`.

Write code top-down: first write the abstract skeleton (no implementation needed), then implement the abstractions.
