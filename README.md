# chat-to-wechat-article（对话转公众号文章）

一个 Agent Skill：把你与 AI 围绕某个问题的**多轮对话记录**，重构为一篇可直接发布到**微信公众号**的 Markdown 文章。

适用人群：运营公众号想持续输出内容的创作者、想把 AI 讨论沉淀为科研笔记/学习日志的研究者和工程师。

## 为什么做这个

GitHub 上已有不少相关工具，但方向不同：

- [geekjourneyx/md2wechat-skill](https://github.com/geekjourneyx/md2wechat-skill)：把**已有的 Markdown** 转成公众号排版 HTML 并推送草稿箱；
- [jackwener/wechat-article-to-markdown](https://github.com/jackwener/wechat-article-to-markdown)：把**公众号文章**抓取转换为 Markdown（反方向）；

而"**对话记录 → 公众号文章**"这一环缺少现成方案。本 Skill 填补的正是这个空白，并与上述工具互补：

```
与 AI 的对话 ──(本 Skill)──> 公众号 Markdown ──(md2wechat 等)──> 排版 HTML / 草稿箱
```

## 功能特性

- 🧠 **重构而非堆砌**：按"读者理解成本"重排内容逻辑，而不是按对话轮次流水账；
- ✍️ **三种标题候选**：悬念式 / 干货式 / 问题式，附 120 字公众号摘要；
- 🕳️ **保留踩坑记录**：对话中的错误假设和被纠正的理解改写为"踩过的坑"小节——往往是读者最有共鸣的部分；
- 🧹 **去 AI 痕迹**：内置排查清单（排比堆砌、"希望对你有帮助"、滥用粗体破折号等）；
- 🔒 **事实纪律**：只包含对话中真实出现的事实与结论，不为完整性虚构数据和引用；
- 📦 **直接兼容** md2wechat / mdnice / 墨滴等排版工具。

## 安装

### Claude Code / 兼容 skills 的 Agent

```bash
npx skills add ytu2023/chat-to-wechat-article --skill chat-to-wechat-article
```

或手动安装：

```bash
git clone https://github.com/ytu2023/chat-to-wechat-article
mkdir -p ~/.claude/skills
cp -r chat-to-wechat-article/chat-to-wechat-article ~/.claude/skills/
```

## 使用方法

安装后，对 Agent 直接说：

> "把我和你的这轮讨论整理成一篇公众号文章"

或粘贴/上传对话记录：

> "附件是我和 AI 讨论 XXX 的记录，帮我转成可发布的公众号 Markdown"

产出内容：

1. 3 个候选标题 + 公众号摘要（digest）；
2. 结构化正文（引言 → 核心讨论 → 踩坑记录 → 结论收获）；
3. 封面图建议（可选生成）；
4. 标准 `.md` 文件，可直接粘贴进排版工具。

## 目录结构

```
chat-to-wechat-article/
├── SKILL.md                        # Skill 主入口与工作流程
├── templates/
│   └── article-template.md         # 公众号文章结构模板
└── references/
    └── style-guide.md              # 公众号写作风格 + 去 AI 痕迹清单
```

## 推荐工作流（公众号涨粉 + 科研记录双目标）

1. 与 AI 深入讨论一个具体问题（保留完整上下文）；
2. 用本 Skill 转成 Markdown 文章；
3. 用 [md2wechat](https://github.com/geekjourneyx/md2wechat-skill) 或 mdnice 排版；
4. 原稿 Markdown 同时提交到自己的 GitHub 笔记仓库（成长记录）；
5. 发布到公众号（涨粉输出）。

## License

MIT
