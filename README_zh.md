# micropowers

本项目**并非**为了快速产出代码而设计，而是为了代码质量而设计，现实一次次教育我 AI 写的代码必须被认真审查。本项目还包含了一个比 codex 自带的更好的记忆指令。

本项目专为 GPT-5.4 设计（GPT-5.5又笨又贵），没有为其他模型测试过。

~~`plan-coding`: 比codex自带的计划模式更好用。~~ 理论上这个skill是品味最好的，但不知道怎么回事，26年2月份后 GPT 按照这个 skill 写出来的计划就很糟糕。我新写了一个 `simple-plan-coding`，先让AI写个简单的计划（基本一分钟就能看完），然后告诉它一次只写100行以内的代码，我在旁边盯着，一边写一边纠正（反正这些代码你迟早都是要读的）。

`incremental-coding`: 适用于连计划都不需要做的任务，比如简单的小功能。

`agentsmd-to-be-copied.md`: 选择你喜欢的那些指令，复制到 ~/.codex/AGENTS.md 中。文档末尾有个记忆相关的指令，需要配合`memory-instruction.md`使用

`memory-instruction.md`: 把这个复制到 ~/.codex 目录下。你得先读一下这个文档的内容才能理解我后面说的话。当 AI 输出 `REQUEST_RESET_CONTEXT` 时，你要新开个对话，然后跟 AI 说`之前你把你的上下文摘要到 AGENTS.md 中了（codex harness已经为你加载好了，你不要再去读一遍），然后重置了上下文，现在我们继续工作吧`（这个挺适合做成custom prompt的，但是codex团队把这个功能删了，我尝试说服他们加回这个功能，但是失败了，我现在在用 espanso 来做这个）

codex有记忆机制，为什么用我这个？我看过~/.codex目录里面的记忆，我对其不太满意，它的总体记忆居然有其他项目的记忆，我在搞项目A，为啥要把项目B的记忆也一块搞进去？

为啥不把这个放进 ~/.codex/AGENTS.md 里面？GPT-5.4在记忆上并没有受过什么训练，你把这个放进里面，它在完成任务后也大概率是不会记得要去做摘要的，只会浪费注意力。

这个没法做成stop hook，因为我们前面的指令让它一次只写100行左右的代码，这也算一个stop，如果这也要触发的话，就太频繁了。只能在任务完成后手动发送。

建议先在项目目录下的 AGENTS.md 中先亲自写一下大致架构是怎样的，先不要偷懒，剩下的再让 AI 去补全。

然后在其开头加上：
```本文档是对代码库的一种摘要，目的是为了帮助 Agent 建立对代码库的理解，而不是作为代码文件的替代，所以 Agent 不能光靠本文档就去回答用户的问题、制定计划，如果 Agent 违反了这个规则，会被惩罚扣分。```

## 致谢

本项目的部分内容受到了以下项目的启发：
- [superpowers](https://github.com/obra/superpowers)
- OpenAI 的 create-plan skill （那是在 codex 推出计划模式之前的，现在似乎已经被删掉了）
- [gstack](https://github.com/garrytan/gstack)

## 其他

在25年底，把 GPT 的推理程度调成high还是不错的，2026年3、4月左右，我发现 medium 会更好，有效减少了过度设计和不遵守指令的问题。

有没有人能联系上codex的负责人tibo，让他把GPT-5.2重新上线一下？好像是因为我的X账号权重比较低，导致他看不到我的留言。发过 [issue](https://github.com/openai/codex/issues/25816#issuecomment-4604452829) ，结果被关了。

