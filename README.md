# micropowers

This project is **not** designed for producing code quickly. It is designed for code quality. Reality has taught me again and again that AI-written code must be reviewed carefully.

This project is designed specifically for GPT-5.4 (GPT-5.5 is dump and expensive). I have not tested it with other models.

- ~~plan-coding: more usable than Codex's built-in planning mode.~~ I feel shorter plans fit human nature better. Once a plan exceeds 100 lines, people stop wanting to read it carefully. I wrote a new `simple-plan-coding` skill: first let the AI write a simple plan that can usually be reviewed in about a minute, then tell it to write no more than 100 lines of code at a time while I watch and correct as it goes.

- `incremental-coding`: an more simpler planning style.

- `summary-memory-instruction.md`: instructions for writing memory summaries. You can copy one into your home directory then let AI read it.

Codex already has a memory mechanism, so why use this one? I have looked at the memory under `~/.codex`, and I am not very satisfied with it. Its global memory even contains memory from other projects. If I am working on project A, why should memory from project B be mixed in too?

Why not put this into `~/.codex/AGENTS.md`? GPT-5.4 is not especially trained around memory behavior. If you put this there, after finishing a task it still probably will not remember to write a summary. It may just waste the attention.

This cannot be turned into a stop hook. Our Skill have already tell it to stop after writing about 100 lines of code, and that also counts as a stop. If this triggered there too, it would happen far too often. So this can only be sent manually after a task is finished.

To decide whether to reset context, tell the AI: `Is more than 50% of the current context just useless intermediate process? If yes, go read ~/summary-memory-instruction.md, follow its instructions, then output `RESET_CONTEXT`. After I see that, I will reset the context, and the codex cli will load AGENTS.md again.` Similarly, putting this instruction into `~/.codex/AGENTS.md` is not very useful either.

It is better to first write the rough project architecture yourself in the project-level `AGENTS.md`. Do not be lazy about that part. Let the AI help fill in the rest afterward.

Then add this text at the beginning of the root-level `AGENTS.md`:
```This document is a summary of the codebase intended to help the Agent build an understanding of it, but this document is not guaranteed to stay consistent with the codebase. So the Agent must not rely on this document alone to answer user questions or execute tasks. It must read the actual code files. If the Agent breaks this rule, it will be penalized.```

## Acknowledgements

Parts of this project were inspired by:
- [superpowers](https://github.com/obra/superpowers)
- OpenAI's create-plan skill (that was before Codex introduced planning mode; it now seems to have been removed)
- [gstack](https://github.com/garrytan/gstack)

## Other Notes

Toward the end of 2025, setting GPT's reasoning level to `high` worked fairly well. Around March and April 2026, I found that `medium` worked better because it reduced over-engineering and failures to follow instructions.
