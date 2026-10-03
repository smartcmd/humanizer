# humanizer

适用于 Codex、Claude Code 等 Agent 的中英文写作技能。写文章、邮件、文案、技术文档和代码注释时，逐句检查 AI 腔。

按作者的使用体验，这套规则对 GPT 的效果特别好。它重点处理 GPT 常见的否定式对比、抽象措辞和模板句，Claude Code 也可以使用。

这份技能从 TokenRouter 仓库的 humanizer 改进版整理而来，保留了 22 条写作规则。它集中处理否定式对比、空泛表态、写给审查者看的注释、架构黑话、模板句和聊天残留。每条规则单独生效，命中一次就改。

## 安装

Codex 用户级安装：

```bash
git clone https://github.com/smartcmd/humanizer.git ~/.agents/skills/humanizer
```

Claude Code 用户级安装：

```bash
git clone https://github.com/smartcmd/humanizer.git ~/.claude/skills/humanizer
```

目录里已有同名技能时，先把旧目录移到技能目录之外备份，再安装本版本。其他客户端按其技能目录约定放置本仓库。技能入口是 [SKILL.md](SKILL.md)，规则使用中文编写，适用于中英文文字。

目录约定见 [Codex 官方技能文档](https://learn.chatgpt.com/docs/build-skills)和 [Claude Code 官方技能文档](https://code.claude.com/docs/en/skills)。

## 使用

在 Codex 中用 `$humanizer`，在 Claude Code 中用 `/humanizer` 调用。也可以在任务里直接要求使用 humanizer：

```text
使用 humanizer 改写下面这段文字，保留事实和作者立场：

[粘贴原文]
```

也可以在写作任务里直接指定：

```text
使用 humanizer，根据这些要点写一封项目进展邮件。
```

在代码仓库里使用时，可以在 Agent 指令中要求：

```text
编写或修改注释、文档、界面文案和提交信息时，使用 humanizer 技能。
交付前按技能的 22 条规则检查本次新增和修改的文字。
```

客户端通过 `SKILL.md` 加载规则。`agents/openai.yaml` 提供技能名称、简介和调用提示。

## 改写示例

原文：

> 值得注意的是，这个函数读取本地缓存，未命中时返回空字符串。这样的设计为上层逻辑提供了强大而灵活的支持。

改写后：

> 这个函数读取本地缓存，未命中时返回空字符串。

改写保留了缓存未命中时的返回值。事实中的限制、风险和不确定性都需要准确表达。

原文：

> It is important to note that the service boasts a robust caching layer, ensuring seamless access to previously fetched results.

改写后：

> The service caches results so later requests can reuse them.

## 规则的用法

先保留材料中的事实，再按要点重写整句。代码标识符、命令、路径、协议字段和引用原文照原样书写。用户指定的语言、文体、篇幅和交付格式决定本次任务的写法。

交付前逐条检查全部规则。Git 仓库中的文本可以先用技能提供的命令筛选，随后通读全文。

## 来源与许可

上游是 [blader/humanizer](https://github.com/blader/humanizer) 3.0.0，规则参考了 Wikipedia 的 “Signs of AI writing”。[TokenRouter](https://github.com/TokenFlux/TokenRouter) 的改进版补充了中文句式、代码注释和提交信息的规则，humanizer 在此基础上整理为通用技能。

采用 [MIT 许可](LICENSE)，保留上游版权声明。
