# micropowers

[中文版本](README_zh.md)

This project is **not** designed for producing code quickly. It is designed for code quality. Reality has taught me again and again that AI-written code must be reviewed carefully.

This project is designed specifically for GPT-5.4 (GPT-5.5 is dumb and expensive). I have not tested it with other models.

~~`plan-coding`: more usable than Codex's built-in planning mode.~~ In theory this skill has the best taste, but for some reason after February 2026 GPT started writing poor plans when following it. I wrote a new `simple-plan-coding` skill instead: first let the AI write a simple plan that can usually be reviewed in about a minute, then tell it to write no more than 100 lines of code at a time while I watch and correct as it goes.

`incremental-coding`: for tasks simple enough that they do not even need a plan.

`en/AGENTS.md`: copy whichever instructions you like into `~/.codex/AGENTS.md`. The end of the document contains a memory-related instruction that should be used together with `summary-memory-instruction.md`.

`en/summary-memory-instruction.md`: copy this into `~/.codex`. Read it first so the workflow below makes sense. When the AI outputs `REQUEST_RESET_CONTEXT`, start a new conversation and tell it: `You previously summarized your context into AGENTS.md (the codex harness has already loaded it for you, so do not read it again). Then you reset the context. Now let's continue working.` This is a good fit for a custom prompt, but the Codex team removed that feature, so I use `espanso` for it now.

Codex already has a memory mechanism, so why use this one? I have looked at the memory under `~/.codex`, and I am not very satisfied with it. Its global memory even contains memory from other projects. If I am working on project A, why should memory from project B be mixed in too?

Why not put this into `~/.codex/AGENTS.md`? GPT-5.4 is not especially trained around memory behavior. If you put this there, after finishing a task it still probably will not remember to write a summary. It may just waste the attention.

This cannot be turned into a stop hook. Earlier instructions already tell it to stop after writing about 100 lines of code, and that also counts as a stop. If this triggered there too, it would happen far too often. So this can only be sent manually after a task is finished.

To decide whether to reset context, tell the AI: `If more than 50% of the current context is just useless intermediate process, go read ~/.codex/summary-memory-instruction.md, follow its instructions, then output REQUEST_RESET_CONTEXT.` Likewise, putting this instruction directly into `~/.codex/AGENTS.md` is not very useful.

It is better to first write the rough project architecture yourself in the project-level `AGENTS.md`. Do not be lazy about that part. Let the AI help fill in the rest afterward.

Then add this text at the beginning of the root-level `AGENTS.md`:
```This document is a summary of the codebase intended to help the Agent build an understanding of it, rather than a replacement for the code files. So the Agent must not rely on this document alone when answering user questions or making plans. If the Agent breaks this rule, it will be penalized.```

## Acknowledgements

Parts of this project were inspired by:
- [superpowers](https://github.com/obra/superpowers)
- OpenAI's create-plan skill (that was before Codex introduced planning mode; it now seems to have been removed)
- [gstack](https://github.com/garrytan/gstack)

## Other Notes

Toward the end of 2025, setting GPT's reasoning level to `high` worked fairly well. Around March and April 2026, I found that `medium` worked better because it reduced over-engineering and failures to follow instructions.

Can anyone reach Codex lead tibo and ask him to bring GPT-5.2 back? My guess is that my X account has too little weight for him to notice my replies. I filed an [issue](https://github.com/openai/codex/issues/25816#issuecomment-4604452829), but it got closed.
