# Contributing

欢迎你把自己的实践经验带回来，让这个项目变得更好。

## 可以贡献的

- **方法论细节**：PLAN.md、SKILL.md 里的措辞、节奏、硬约束的修正
- **新增 skill**：有没有值得单独抽出来的练习（如 Values Discovery、Life Wheel 等）
- **工具适配实测**：你在 Codex / Cursor / ChatGPT Projects / Gemini 等工具里真的跑过后，写成 Issue 或补充 README 的方式 B
- **bug / typo**：任何错别字、死链接、不一致术语
- **翻译**：本项目原生中文，欢迎英文版 / 其他语言分支

## 不要提交的（非常重要）

- **`PROGRESS.md`**：已 gitignore，这是你的私人进度
- **`compass/` `dashboard/` `journal/` `odyssey/` `prototypes/` `failure-log/` `reviews/`**：你的个人人生设计答案，永远不提交
- **`CLAUDE.local.md` `.claude/private/` `.claude/**/*.local.*`**：本地临时指令 / 草稿
- **任何含真人姓名、联系方式、公司名的示例**：SKILL.md 里的示范数据请匿名化

## PR 规范

### 改流程时同步三处

如果你修改了某个练习的流程，**必须同时更新**：

1. 该 skill 的 `.claude/skills/life-design-coach-XXX/SKILL.md`
2. `PLAN.md` 对应的 "Phase X.X 练习" 节
3. 如有对应的铁律调整，还要改 `CLAUDE.md`

单点修改会让三个来源失去一致性。

### Skill 命名 / 描述规范

- 所有 skill 必须以 `life-design-coach-` 为前缀（避免和其他插件重名）
- `SKILL.md` 的 frontmatter `name:` 必须和目录名**完全一致**
- `description:` 必须包含清晰的**触发条件**（用户说什么话会调用它），用中文列 3-5 个触发词
- body 必须有：前置条件 / 流程 / 硬约束 / 产出 / 收尾 五个小节

### Commit message

使用 Conventional Commits：

```
feat: 新增 XXX skill
fix: 修复 YYYY 的前置条件判断
docs: 补充方式 B 的 ChatGPT 实测
refactor: 调整 aeiou 流程 step 顺序
```

## 提 Issue

Bug / 疑问 / 工具适配反馈都到 GitHub Issues。

**不要在 Issue 里贴你的练习答案**。如果需要举例，请脱敏。

## 行为约定

- 不评判别人的人生设计选择
- 不推销"正确的人生观"
- 尊重这套方法论的核心信念：**人生不是有最优解的选择题**
