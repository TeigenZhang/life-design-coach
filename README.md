# life-design-coach

> 把任意 AI 变成你的**人生设计教练**。
> 基于斯坦福《人生设计课》（*Designing Your Life* by Bill Burnett & Dave Evans）方法论，配套 8 周实践节奏和可直接用的教练指令。

---

## 这是什么

一套**方法论模板 + AI 教练人格设定**。放到 Claude Code（或任何支持长上下文指令的 AI）里，它就会：

- 用**苏格拉底式提问**带你做练习，不直接给建议
- 一次只问一个问题，等你回答再继续
- 检测到**"重力问题"**（沉没成本、外部环境依赖）时温和打断你
- 挑战你的**功能失调信念**（"我应该已经知道自己要什么了" / "选错了就完了" 等）
- 每次对话结束前**必须产出下周能做的最小行动**

它遵守寻路思维（*Wayfinding*）而非导航思维（*Navigation*）—— 不问"你的目标是什么"，而是帮你从数据里发现"**什么让你活过来**"。

## 这**不是**什么

- **不是一个 App 或 SaaS** —— 就是几个 markdown 文件 + 你的 AI
- **不是书的替代品** —— 强烈建议配合原书使用，本项目是实践脚手架，不是书本内容
- **不是让 AI 帮你决定人生** —— AI 只负责追问、结构化、防你掉进思维陷阱；答案永远是你自己的
- **不是填表应用** —— 每一个练习都是为了引导一个真实的对话和一次真实的行动

## 谁适合用

- 在职业或生活岔路口，觉得"什么都行，但不知道该做什么"
- 愿意**连续 3 周记录**日常活动的人（Good Time Journal 是整个体系的命根）
- 接受"人生不是有最优解的选择题，而是需要不断原型测试的设计项目"

---

## 如何开始

### 方式 A：Claude Code（推荐）

**前提**：已安装并登录 [Claude Code](https://docs.claude.com/en/docs/claude-code/overview)（Node 18+，`claude --version` 能跑通）。

```bash
git clone https://github.com/TeigenZhang/life-design-coach.git
cd life-design-coach
cp -n PROGRESS.template.md PROGRESS.md   # 你的私人进度文件（已存在则跳过，不会覆盖）
claude
```

然后对 Claude 说：

> 我准备好了，开始做仪表盘。

Claude Code 启动时会自动加载 `CLAUDE.md`（教练人格 + 工作流），再按工作流提示读取 `PROGRESS.md` 和对应阶段的 `SKILL.md`，带你走完整个流程。

<a id="other-ai"></a>

### 方式 B：其他任何 AI

**核心思路**：本项目把"教练能力"全部封装在几个 markdown 文件里。把任意 AI 变成你的人生设计教练，本质上就是把下面三件东西交给它：

| 喂什么 | 来自 | 作用 |
|--------|------|------|
| **教练人格** | `CLAUDE.md` | 让 AI 守住 7 条铁律、苏格拉底式提问 |
| **当前练习 playbook** | 对应阶段的 `.claude/skills/life-design-coach-*/SKILL.md`（13 选 1） | 让 AI 知道这个练习具体怎么带 |
| **你的上下文** | `PROGRESS.md` + 已有产出（`compass/`、`journal/` 等） | 让 AI 知道你做到哪一步、之前写过什么 |

> 💡 `PLAN.md`（8 周方法论全文）是**加分项** —— 上下文宽裕的 AI 建议一并喂上去，能多一层大局观；最低可用集就是上面这三件。
>
> 💡 怎么拿到对应的 `SKILL.md`？在 GitHub 仓库的 `.claude/skills/life-design-coach-<练习名>/SKILL.md` 找到对应文件，点右上角 `Raw` 复制全文即可。13 个练习名见下方 [Slash Commands](#slash-commandsclaude-code) 表。

方式 A 之所以"零配置"，是因为 Claude Code 启动时自动加载 `CLAUDE.md`（教练人格 + 工作流），再按 slash command / 工作流提示去读对应的 `SKILL.md`、`PROGRESS.md` 和你的已有产出。换其他任何 AI（ChatGPT / DeepSeek / Kimi / Gemini / 豆包 / 通义 / Cursor / Codex …）都行 —— 只是这"喂进去"的步骤需要你手动做。

> ⚠️ **隐私提示**：把这些文件喂给第三方 AI，等于把你的工作观 / 人生答案交出去，可能被用于训练。**敏感信息建议先匿名化**（抹掉真名、公司名、可识别细节），尤其上传到不完全信任的 AI 时。如果用的是 Project / Knowledge 这种**长期保存**机制，练完一个阶段后建议手动删除或撤回已上传的文件。
>
> ⚠️ **实测范围**：本项目目前**只在 Claude Code 里实测过**。下面几种"塞法"是基于机制推断"应该能用"，试过的同学欢迎开 Issue / PR 补充实战体验。

#### 怎么塞 —— 按你用的 AI 支持什么，选最省事的方式

| 你的 AI 支持… | 推荐塞法 |
|--------------|---------|
| **本地仓库 + rules 文件**<br>（Codex CLI / Cursor / GitHub Copilot / Cline / Aider 等编码 Agent） | `git clone` 仓库后，把 `CLAUDE.md` 复制 / 重命名为它认的 rules 文件名（`AGENTS.md` / `.cursorrules` / `.github/copilot-instructions.md` / `.clinerules` / `CONVENTIONS.md`）；其他文件 AI 按需读取 |
| **Project / Knowledge / Gem 持久化**<br>（跨会话保存 —— Claude.ai Projects · ChatGPT Projects · Gemini Gems · Kimi 智能体 · 智谱 GLM · 腾讯元器 · 通义智能体 等） | 创建一个 Project / Gem / 智能体，把 `CLAUDE.md` 和当前阶段的 `SKILL.md` 上传到 Knowledge |
| **单次会话**<br>（不跨会话保留 —— DeepSeek · Kimi · 豆包 · 通义 · 文心 · 混元 · 腾讯元宝 · 讯飞星火 · 免费版 ChatGPT / Gemini 等 —— 多数支持当次会话上传文件，但下次会话不保留） | 每次新会话开始时，把 `CLAUDE.md`（支持上传就上传，不支持就整段粘）+ 当前阶段 `SKILL.md` + 当前 `PROGRESS.md` 和已有产出 一起喂给它 |

**首次启动话术**（任何 AI 通用 —— 在已经把上面三件东西塞给 AI 之后）：

> 你的角色和行为铁律由我提供的 `CLAUDE.md` 定义。我准备好了，开始做仪表盘。

**会话持续性（很重要）**：

大模型不会自动记得上一次对话。**每次新会话开始前**：

- 如果你用的是"单次会话 AI"（上面第三行），把固定的 `CLAUDE.md` + 当前阶段 `SKILL.md` 也要重新喂一遍 —— 不像 Project / Knowledge 能一直留着
- 不管哪种 AI 都要带上**动态上下文**：最新的 `PROGRESS.md`（当前阶段、上次的下一步）、本阶段已有产出（如 `compass/workview.md`、本周 `journal/daily/` 等）

否则 AI 没法判断前置条件是否满足，可能越级进入后面的 skill。

练习产出自己保存为本地 markdown（AI 给你提问和结构，你把它粘回本地对应目录）。目录结构参考 `PLAN.md` 最后一节。

### 方式 C：只想读方法论 / 自助做练习

直接读 `PLAN.md` 和 `.claude/skills/*/SKILL.md`。**这些 SKILL.md 是为 Claude 写的指令，但对人类读者也是完整的练习 playbook** —— 一个人对着 SKILL.md 也能把练习做完，AI 只是让流程变成对话而已。

---

## 核心铁律（教练模式）

这些约束写在 `CLAUDE.md` 里，AI 在对话中会自动遵守：

1. **用问题回应陈述** —— 永远不要直接给建议
2. **一次只问一个问题** —— 等用户回答后再继续，禁止一口气抛出列表
3. **检测重力问题** —— 出现"要是当初…就好了""如果环境…就好了""等我…之后"时温和提示
4. **挑战功能失调信念** —— 见 PLAN.md 的信念表
5. **对话收尾必出行动** —— 每次会话以"下周能做的最小行动"结束
6. **分析瘫痪转原型** —— 用户在脑内打转超过 3 轮，强制转向原型实验
7. **寻路而非导航** —— 不问"目标是什么"，问"什么让你活过来"

---

## 8 周推进节奏

```
仪表盘 → Workview → Lifeview → 罗盘校准
  → GTJ (连记 3 周) → AEIOU → 能量地图
  → Mindmap → Odyssey → 原型实验
```

**不跳步**。没有 GTJ 数据不做 Odyssey。详细节奏见 `PLAN.md`。

---

## Slash Commands（Claude Code）

每个练习都有对应的 skill，在 Claude Code 里直接用 `/` 触发，或用自然语言让 Claude 主动调用。所有 skill 带 `life-design-coach-` 前缀。

| 命令 | 做什么 |
|------|--------|
| `/life-design-coach-dashboard` | Phase 1.1 · 人生仪表盘（四维评分） |
| `/life-design-coach-workview` | Phase 1.2 · 工作观 |
| `/life-design-coach-lifeview` | Phase 1.3 · 人生观 |
| `/life-design-coach-coherence` | Phase 1.4 · 罗盘校准 + 设计原则 |
| `/life-design-coach-journal` | Phase 2.1 · Good Time Journal 每日 check-in |
| `/life-design-coach-aeiou` | Phase 2.2 · AEIOU 深度反思 |
| `/life-design-coach-energy-map` | Phase 2.3 · 能量地图四象限 |
| `/life-design-coach-mindmap` | Phase 3.1 · 思维导图发散 |
| `/life-design-coach-odyssey` | Phase 3.2 · 3 个 5 年奥德赛方案 |
| `/life-design-coach-prototype` | Phase 4.1 · 原型对话 / 原型体验 |
| `/life-design-coach-failure` | Phase 4.2 · 失败事件冷处理 |
| `/life-design-coach-reset` | 紧急 · 20 分钟重置 |
| `/life-design-coach-review` | 周 / 月 / 季复盘 |

每个 skill 的完整流程在 `.claude/skills/life-design-coach-*/SKILL.md`。

非 Claude Code 工具没有 slash command 机制，但按 [方式 B](#other-ai) 把 `CLAUDE.md` + 当前阶段 `SKILL.md` + `PROGRESS.md` 和已有产出喂给 AI（`PLAN.md` 是加分项），它就能按同样节奏工作 —— 你说"开始做仪表盘"，它会按对应 `SKILL.md` 的流程推进。

---

## 项目结构

```
life-design-coach/
├── CLAUDE.md                         # 教练人格设定 + 铁律（AI 会自动加载）
├── PLAN.md                           # 8 周方法论全文 + 练习清单
├── PROGRESS.template.md              # 进度导航仪的模板（tracked）
├── PROGRESS.md                       # 你 cp 出的私人进度（gitignored，不会提交）
├── README.md                         # 本文件
├── LICENSE                           # MIT
└── .claude/
    └── skills/                       # 13 个练习对应的 Claude Code skills
        ├── life-design-coach-dashboard/SKILL.md
        ├── life-design-coach-workview/SKILL.md
        ├── life-design-coach-lifeview/SKILL.md
        ├── life-design-coach-coherence/SKILL.md
        ├── life-design-coach-journal/SKILL.md
        ├── life-design-coach-aeiou/SKILL.md
        ├── life-design-coach-energy-map/SKILL.md
        ├── life-design-coach-mindmap/SKILL.md
        ├── life-design-coach-odyssey/SKILL.md
        ├── life-design-coach-prototype/SKILL.md
        ├── life-design-coach-failure/SKILL.md
        ├── life-design-coach-reset/SKILL.md
        └── life-design-coach-review/SKILL.md
```

练习过程中会按需创建以下目录（不预建空目录）：

```
compass/         # 罗盘：Workview + Lifeview + 设计原则
dashboard/       # 人生仪表盘历史
journal/         # Good Time Journal
odyssey/         # 奥德赛计划
prototypes/      # 原型实验
failure-log/     # 失败免疫日志
reviews/         # 周/月/季复盘
```

这些目录包含你的**私人答案**，已在 `.gitignore` 中排除 —— 不要 commit 或公开。

---

## 反馈与贡献

方法论改进、铁律补充、新的练习模板都欢迎 PR。个人练习数据**不要**提交。

## 致谢

- Bill Burnett & Dave Evans —— 《Designing Your Life》原作者，斯坦福设计学院
- Anthropic Claude —— 本项目的默认教练载体

## License

MIT
