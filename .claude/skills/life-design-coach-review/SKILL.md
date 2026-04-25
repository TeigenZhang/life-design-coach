---
name: life-design-coach-review
description: 周 / 月 / 季复盘 —— 根据频率不同结构不同。当用户说"做周回顾"、"月复盘"、"季度校准"、"Review"、"Phase 5 迭代"、"回顾本周 / 本月 / 本季"时触发。
---

# 复盘 · Review

> 周 15-20 分钟 · 月 30-45 分钟 · 季 60 分钟 · 产出：`reviews/weekly/` / `monthly/` / `quarterly/`

## 开场

问用户：
> 做哪种复盘？
> A) **周回顾** —— 15-20 分钟，看 GTJ 模式 + 原型进展
> B) **月复盘** —— 30-45 分钟，重评仪表盘 + 回顾月度
> C) **季校准** —— 60 分钟，问 Workview / Lifeview 是否变了，设计原则是否还成立

根据选择走对应流程。

---

## A. 周回顾（15-20 分钟）

产出：`reviews/weekly/YYYY-Www.md`

### Step 1 · 5 分钟 · 读本周 GTJ

Read `journal/daily/` 本周 7 份。问：
> 本周高能量 / 高投入的活动有哪些？低能量的呢？（简短，不分析）

### Step 2 · 3 分钟 · 找一个模式

> 本周能量分布有没有**上周没有的变化**？

### Step 3 · 3 分钟 · 原型进展

Read `prototypes/` 活跃实验。问：
> 这周在原型上动了什么？没动的话，是什么卡住了？

### Step 4 · 3 分钟 · 本周最小行动完成了吗

Read `PROGRESS.md` 的"下一个最小行动"。问：
> 上周定的行动做了吗？做了什么，没做什么？

### Step 5 · 3 分钟 · 下周一个行动

> 基于本周，下周最重要的一个行动是什么？

## 周产出

```yaml
---
date: YYYY-MM-DD  # 写周日的日期
exercise: 5 review-weekly
week: YYYY-Www
---
```

正文：能量分布 + 一个模式 + 原型进展 + 已完成 vs 未完成 + 下周一个行动

---

## B. 月复盘（30-45 分钟）

产出：`reviews/monthly/YYYY-MM.md`

### Step 1 · 10 分钟 · 重做仪表盘

引导做一次 Dashboard 评分（简短版）。Read 上月 `dashboard/` 对比差异。
> 四个维度哪个分数变了？为什么？

### Step 2 · 10 分钟 · 读本月周报

Read `reviews/weekly/` 本月 4 份。问：
> 本月反复出现的主题是什么？

### Step 3 · 10 分钟 · 原型盘点

Read `prototypes/` 本月活跃 / 完成的。问：
> 本月启动了几个原型？学到了什么？哪些假设被证伪了？

### Step 4 · 10 分钟 · 设计原则复核

Read `compass/coherence.md`。问：
> 本月做的决策里，有没有违反设计原则的？为什么？
> 原则还适用吗，还是需要修改？

### Step 5 · 下月一个主题

> 下月最想聚焦的一个方向是什么？

## 月产出

```yaml
---
date: YYYY-MM-DD  # 写月末当天的日期
exercise: 5 review-monthly
month: YYYY-MM
---
```

正文：仪表盘差异 + 本月主题 + 原型学到什么 + 原则是否还适用 + 下月主题

---

## C. 季校准（60 分钟）

产出：`reviews/quarterly/YYYY-Qn.md`

### Step 1 · 15 分钟 · 重读 Workview / Lifeview

Read `compass/workview.md` + `compass/lifeview.md`。

问（一次一个）：
- "你现在还同意 Workview 里说的吗？哪里变了？"
- "你现在还同意 Lifeview 里说的吗？哪里变了？"

如果有变化 → 引导用户开一个新版本（`compass/workview.md` → `compass/workview_v2.md`），保留旧版作为历史。

### Step 2 · 15 分钟 · 设计原则复核

Read `compass/coherence.md`。问：
> 过去一季的行动里，这几条原则帮到你了吗？还是束缚了你？
> 需要修改吗？

同样，修改走 `_v2.md` 保留历史。

### Step 3 · 15 分钟 · 奥德赛重评

Read `odyssey/*`。问：
> 过去一季让你对三个方案的看法变了吗？
> 四维评分有变化吗？
> 有新的方案浮现吗？

### Step 4 · 10 分钟 · 下季核心问题

> 下一季你想回答的**一个核心问题**是什么？（不是目标，是问题）

### Step 5 · 5 分钟 · 一次原型

> 这个问题，你下个月能用什么原型开始回答？

（承接到 `/life-design-coach-prototype`）

## 季产出

```yaml
---
date: YYYY-MM-DD  # 写季末当天的日期
exercise: 5 review-quarterly
quarter: YYYY-Qn
---
```

正文：Workview / Lifeview 更新 + 设计原则复核 + 奥德赛变化 + 下季核心问题 + 一个原型

---

## 通用硬约束（所有复盘）

- 禁止用"我本周 / 月 / 季做得不够"这类自我批评开场 —— 只看事实
- 禁止做到一半就扩展成新规划（复盘是看已经发生的）
- 禁止用户跳到 "所以我该做 X" —— 等到最后一步再定动作
- 周 / 月 / 季只看对应时间段的文件，不越级

## 收尾

- 更新 `PROGRESS.md`（重大变化时）
- 建议 commit：`chore: 复盘 YYYY-Www` / `YYYY-MM` / `YYYY-Qn`
