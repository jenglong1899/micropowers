Now summarize the current context and record it in the project's root `AGENTS.md` or in other documents. **The summary must let you continue working seamlessly after the context is cleared and later reloaded.** When you are unsure whether something should be recorded, judge it against that goal.

Usually:
- Summarizing means throwing away intermediate process and keeping only the final result.
- You should remember mistakes you made, so you do not repeat them later.
- You should remember roughly what each file is about.
- You should not record irrelevant details such as "I ran `ls` an hour ago".

You must maintain the structure of the memory documents. Messy memory hurts both future work and future maintenance.

As you do more work, the memory gets longer. **Make sure `AGENTS.md` stores only memories that matter in 80%+ of future situations**, such as user preferences. Put less frequently needed memory into other documents, then leave a rough description(reference) from `AGENTS.md`. This does not mean every other memory document must be refered directly from `AGENTS.md`. Indirect references are fine too. For example, if 20 documents are all about one topic, you can keep them in one folder and describe that folder in `AGENTS.md`.

Again, **the goal of the summary is that after the context is cleared and your summary is loaded again, you can continue working as if nothing had happened**.

After finishing the summary, output `Summary complete, please start a new conversation to reset the context`.
