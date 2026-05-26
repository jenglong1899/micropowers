# micropowers

[中文版本](./README_zh.md)

This skill collection is not designed for producing code quickly. It is designed for code quality. Reality has taught me that AI-generated code must be reviewed carefully.

- `AGENTS.md` (placed under `~/.codex`): contains the memory mechanism. Codex already has a memory mechanism, so why use this one? I have looked at the memory under the `.codex` directory, and I am not very satisfied with it. You must read this document before using it, because it is still semi-manual for now.
  - You should maintain project memory in the root-level `AGENTS.md`, such as the rough architecture of the project. Do not skip this. Write down the architecture yourself first, then let AI help fill in the rest.
  - Then add the following text at the beginning of the root-level `AGENTS.md`:
  - ```This document is a summary of the codebase intended to help the agent build an understanding of it. It does not mean the agent can skip reading the actual code files referenced by the summary, because an agent may not know what it does not know. For example, when implementing a feature, it may add a fallback without realizing the existing codebase already has one, simply because it did not read enough of the code, leading to duplicated logic.```
- `incremental-coding`: write no more than 100 lines of code at a time. This fits human nature better; if AI outputs 400-500 lines at once, humans usually will not want to review it carefully.
- ~~`plan-coding`: more usable than Codex's built-in planning mode.~~ I do not know what happened with GPT-5, but it feels dumber: it spent time making a plan, then later implemented something different. I wrote a new `simple-plan-coding` skill: first let AI write a simple plan that can basically be reviewed in one minute, then use `incremental-coding` afterward and correct it while coding.

## Acknowledgements

Parts of this project were inspired by:

- [superpowers](https://github.com/obra/superpowers)
- OpenAI's `create-plan` skill (that was before Codex introduced planning mode; it now seems to have been removed)
- [gstack](https://github.com/garrytan/gstack)

## Other Notes

Q: Why not merge `incremental-coding` directly into `plan-coding`?  
A: Because that would split the AI's attention.

Toward the end of 2025, setting GPT reasoning to `high` worked fairly well. Around March to April 2026, I found that `medium` worked better because it reduced over-engineering and instruction-following issues.

May 2026 update: I do not know what happened with GPT-5.5 — it became much worse. Switching to GPT-5.2 worked a lot better.


Todo: I previously asked AI about this. I vaguely remember Linux may have something like a hook that can run automatically after you finish reading a file. I will look into it when I have time and see whether it can be used for automatic updates, so agents do not need to update things manually every time.
