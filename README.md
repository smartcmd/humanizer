# humanizer

给 AI 写的东西去去味，中文英文都能用。

里面有 22 条规则，专门改那些看着眼熟、读着费劲的写法：开头来一句“值得注意的是”，动不动“不是……而是……”，注释里堆满“边界”“契约”“语义”，说完还要再总结一遍。每条规则命中一次就改，具体写在 [SKILL.md](SKILL.md) 里。

## 安装

Codex：

```bash
git clone https://github.com/smartcmd/humanizer.git ~/.agents/skills/humanizer
```

Claude Code：

```bash
git clone https://github.com/smartcmd/humanizer.git ~/.claude/skills/humanizer
```

装过同名技能的话，先把旧文件夹移出去备份，再运行上面的命令。

其他安装方式可以看 [Codex 文档](https://learn.chatgpt.com/docs/build-skills)和 [Claude Code 文档](https://code.claude.com/docs/en/skills)。

## 使用

在 Codex 里用 `$humanizer`，在 Claude Code 里用 `/humanizer`。把要改的文字一起发过去就行：

```text
用 humanizer 改一下这段话：

[粘贴原文]
```

想让它平时写代码也遵守这些规则，可以在项目的 `AGENTS.md` 或 `CLAUDE.md` 里加一句：

```text
写注释、文档、界面文案和提交信息时，使用 humanizer，写完按技能里的规则检查一遍。
```

## 举个例子

原文：

> 值得注意的是，这个函数读取本地缓存，未命中时返回空字符串。这样的设计为上层逻辑提供了强大而灵活的支持。

改写后：

> 这个函数读取本地缓存，未命中时返回空字符串。

英文也一样：

> It is important to note that the service boasts a robust caching layer, ensuring seamless access to previously fetched results.

改写后：

> The service caches results so later requests can reuse them.
