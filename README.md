# micropowers

This skill collection is **NOT** designed for producing code quickly. It is designed for code quality. Reality has taught me that AI-generated code must be reviewed carefully.

- ~~plan-coding: more usable than Codex's built-in planning mode.~~ I feel shorter plans fit human nature better: once a plan exceeds ~100 lines, people stop reading carefully. I wrote a new simple-plan-coding skill: first ask the AI for a simple plan (reviewable in ~1 minute), then constrain it to write no more than 100 lines at a time while you supervise and correct as needed.
- incremental-coding: in most cases you should use simple-plan-coding instead of this. It enforces writing no more than 100 lines at a time, with a brief explanation before coding. This fits human nature better; if AI outputs 400-500 lines at once, humans usually will not want to review it carefully.
- AGENTS.md (placed under ~/.codex): contains the memory mechanism. Codex already has a memory mechanism, so why use this one? I have looked at the memory under the .codex directory, and I am not very satisfied with it. You must read this document before using it, because it is still semi-manual for now.
    - You should maintain project memory in the root-level `AGENTS.md`, such as the rough architecture of the project. Do not skip this. Write down the architecture yourself first, then let AI help fill in the rest.
    - Then add the following text at the beginning of the root-level `AGENTS.md`:
    - ```This document is a summary of the codebase intended to help the agent build an understanding of it. It does not mean the agent can skip reading the actual code files referenced by the summary, because an agent may not know what it does not know. For example, when implementing a feature, it may add a fallback without realizing the existing codebase already has one, simply because it did not read enough of the code, leading to duplicated logic.```
    - GPT-5.5 is relatively good at memory: it tends to remember to write summaries and reset context. But it writes code poorly. GPT-5.2 writes better code, but often forgets to summarize/reset, so you need to remind it.
## Acknowledgements

Parts of this project were inspired by:
- [superpowers](https://github.com/obra/superpowers)
- OpenAI's create-plan skill (that was before Codex introduced planning mode; it now seems to have been removed)
- [gstack](https://github.com/garrytan/gstack)

## Other Notes

Toward the end of 2025, setting GPT reasoning to high worked fairly well. Around March to April 2026, I found that medium worked better because it reduced over-engineering and instruction-following issues.
