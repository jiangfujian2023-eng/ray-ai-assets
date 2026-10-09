# 内容素材卡九节模板（Content Material Card Template）

> 把一条原始素材变成可回读、可核验的标准卡片。
> 适用于短视频转写、图文笔记、播客、网页文章、课程录音等任何来源素材的首轮归档。

**包版本**：v0.1.2
**模板规格**：`template_version V2.2`
**资产编号**：RAY-004
**许可**：**MIT License** — Copyright (c) 2026 锐泽 Ray（全文见 [`LICENSE`](./LICENSE)）

你可以自由使用、复制、修改、合并、发布、分发、再分发、出售本包，
**唯一条件是在副本或实质性部分中保留上面的版权声明与许可声明。**

> MIT 覆盖的是**本包的公开导出文件**。本包的上游原料、第三方作品各有各的权利归属，
> **不因本包采用 MIT 而获得许可**。

---

## 一页说明

### 这个包解决什么

素材只存原文，下次谁都无法判断它可信不可信、用在哪里。**素材卡**把一条素材固定成九节：原始素材信息、标题与标签、内容总结、金句、关键点、资源位、正文全文、疑似错误对照表、来源说明。

核心原则：**原文可回溯。** 纠错只写进对照表，不在正文里改——任何时候都能核对「我说的」和「原作者说的」差在哪。

### 适合谁

- 做素材归档、竞品拆解、内容蒸馏的人
- 需要区分「官方可回读」与「博主口述」的调研者
- 团队里希望素材有统一格式、避免重复劳动的人

### 输入 / 输出

| | 内容 |
|---|---|
| **输入** | 一条素材（链接／已下载的媒体／已转写的文本／你粘贴的正文） |
| **输出** | 一份填好的 `content-material-card-<素材ID>.md`，含九节＋frontmatter |
| **不做** | 不做蒸馏判断、不做分发决策——那些是模板下游的事 |

### 怎么用

1. 复制 `templates/content-material-card-template-V2.2.md` 到你的素材目录
2. 改名为 `content-material-card-<素材ID>.md`
3. 填 frontmatter（平台、作者、时间、URL、采集日期）
4. 逐节填写，按下面三种情况区别处理，**不要编**：

   | 情况 | 写什么 |
   |---|---|
   | 确认**没有发生**、或该项**不适用** | `无` |
   | **缺失、无法取得、不确定** | `待补` |
   | 确实有内容 | 如实写 |

   ⚠️ **不要用「无」掩盖「不知道」。** 没查到 ≠ 不存在。
   **也不要留空**——留空无法区分「忘了填」和「没有」。
5. 对照下方「验收清单」逐条自查

### 触发条件

- 采集到一条新素材，需要归档
- 需要把已转写稿变成可检索、可分发的结构化卡片
- 发现旧卡片缺字段，需要按统一规格补齐

### 依赖与费用

| 项 | 情况 |
|---|---|
| 运行环境 | 任意 Markdown 编辑器，无需插件 |
| 软件依赖 | **无**（纯文本模板） |
| 费用 | **零** |
| 可选转写 | 视频素材需先转写，**转写工具与模型费用另计**，不属于本包 |

---

## 可选字段的处理（重要）

模板 frontmatter 里有**三个可选字段**来自我方内部约定。**你可以直接用，也可以替换或整行省略**——它们不影响模板的其他部分。

> **关于「留空」的范围**：上述可选字段**允许省略或留空值**，因为它们不是你业务的一部分。
> 但「没有整段留空」这条纪律针对的是**九节正文与必填身份字段**——那些省略了就是缺信息。
> 两者不冲突：可选字段按你的需要处理，九节正文按纪律逐项交代。

| 字段 | 是什么 | 你可以怎么处理 |
|---|---|---|
| `maturity`（G0–G5） | 成熟度刻度 | 保留字段与刻度，**判定标准由你自己定**。例如：G0=刚采集、G1=已核对、G2=已复用过。删掉整行也可以。 |
| `赋能` | 我方的业务分区字段 | **改成你自己的分类**（如 市场／产品／运营／研究），或整行留空。 |
| `source_class`（来源性质） | 来源分类，如官方／个人观点／营销推广 | 采用或换成你自己的分类标准（它与 `evidence` 是两个不同字段）。 |

### O/E 证据分级（完整定义）

模板用两个字母区分信息来源的可核实程度：

| 标记 | 含义 | 判定标准 | 在卡片里怎么用 |
|---|---|---|---|
| **O** | **官方可回读** | 来源是**发布方自己**的正式渠道：官方文档、平台公告、官方规则页、公司公告、原始数据表。**判定看「是谁说的」，不是「能不能打开」。** | 可引用，注明 URL |
| **E** | 经验、观点或转述 | 博主／从业者的个人观点、个人经历、经验总结、二手转述。**即使原文一字不差、能逐字回读，仍标 E。** | 引用时必须写明「E，这是他人说法」 |

**两条硬规则：**

1. **O 与 E 不得混标**。一条内容里既有官方数据又有博主判断时，拆成两条分别标，不要标成一个混合等级。
2. **`confidence` 与 `evidence` 是两件事**。`evidence` 说来源性质（官方／个人说法），`confidence` 说你对这条记录的把握程度（low／medium／high）。**没有一手数据时不得标 high** —— 这是两个独立字段，不要用其中一个代替另一个。

**能不能回读，和观点是否为真，是两件事。**

能打开原文只说明**你看得到他说了什么**，不说明**他说的是真的**。同理，可回读也不自动授予引用或再分发的许可——**那是版权问题，由素材原作者的许可决定，不由可回读性决定。**

### 两个对照例

| 内容 | 判定 | 理由 |
|---|---|---|
| 某平台官方公告：「本政策自2026 年 10 月 1 日起生效」 | **O** | 来源是平台自己的正式公告，是发布方的第一手声明 |
| 某博主视频：「我做这行五年，月入五万」 | **E** | 即使视频能逐字回读，主张是**他个人的经历陈述**，不是官方可核事实 |

**关键差别**：前者是「发布方自己宣告的规则」，后者是「个人对客观世界的陈述」。个人陈述即使为真，也不属于官方可回读来源。

### `source_class`（来源性质）

可选值：`官方／亲历分享／个人观点／营销推广／二手转述／AI生成／其他`

这是**分类标签，不是可信度评级**。**营销推广不等于不可信**，但它决定了你要不要去核实数字。

---

## 六条硬纪律（模板内已固化）

1. **不许省略整段** —— 没有就写「无」
2. **纠错不改原文** —— 只列对照表，正文保留转写原样
3. **不猜** —— 低置信标「需回看」；抓不到写「待补」
4. **数字必须带出处** —— 没出处的数字标「未核实」，不得用于对外产出
5. **绝对化话术打 ⚠️** —— 不得进入任何对外内容
6. **`sources` 必填** —— 无来源的结论不写进知识库

---

## 验收清单

填完卡片后逐条自查：

- [ ] frontmatter 身份字段填全（平台／作者／时间／时长／URL／素材ID／采集日／源文件）
- [ ] 互动数据未公开的写「未公开」，**没有猜数字**
- [ ] 平台自带标注（如「个人观点」）已抄录
- [ ] 关键点表每行有「类型」（方法／判断／数据／案例）
- [ ] 金句里的绝对化话术已加 ⚠️
- [ ] **第六节正文全文是原文／原转写**，没有润色改写（**第二节「内容总结」允许概括，这是它的用途**）
- [ ] 疑似错误只出现在对照表，未动正文
- [ ] 无出处的数字标「未核实」
- [ ] `sources` 非空
- [ ] 九节正文与必填身份字段**没有整段留空**
- [ ] 区分清楚了「无」与「待补」——没查到的没有写成「无」
- [ ] 可选字段（`maturity`／`赋能`／`source_class`）按需处理，不强制填

---

## 已知限制

- 本模板**不含**转写／下载能力。视频素材需先自行转写，费用另计。
- `maturity`／`赋能`／`source_class` 三个字段来自我方内部约定，**外部使用需自行定义等价标准**（上文已给可公开的定义与替换方式）。
- O/E 分级**不是行业标准**，是我方约定。别人可能用别的体系。
- 模板提供的是**格式**，不保证你填的内容正确。判断仍需自己负责。

---

## 真实验证范围（请按这个理解本包）

**已发生的**：模板在我方内部资产台账登记为「2026-09-30 四次填实」——即有四条真实素材用它填过卡。

**未发生的**：
- 本次导出**没有重新实跑**那四次任务
- **没有**在任何外部环境做过独立试用
- **没有**验证过不同编辑器／不同平台的兼容性

So: this is a template with a **real internal usage record**, but **not a broadly validated product**. Please use it with that expectation.

---

## English

### What this is

A Markdown template that turns **one raw source** into a **traceable, verifiable** material card. Works for short/long video transcripts, image posts, podcasts, web articles, and course recordings.

**The core principle: the original stays traceable.** Corrections go in the error-comparison table — **never edited into the body text** — so you can always check where your summary diverges from what the author actually said.

### Input / Output

| | |
|---|---|
| **Input** | one source (link / downloaded media / transcript / pasted text) |
| **Output** | one filled `content-material-card-*.md` with nine sections + frontmatter |
| **Not** | distillation decisions or distribution routing — those are downstream |

### How to use

1. Copy `templates/content-material-card-template-V2.2.md`
2. Rename to `content-material-card-<source-id>.md`
3. Fill the frontmatter (platform, author, timestamp, URL, capture date)
4. Fill each section. Distinguish three cases — **never invent**:

   | Case | Write |
   |---|---|
   | Confirmed **did not happen**, or **not applicable** | `无` (none) |
   | **Missing, unobtainable, or uncertain** | `待补` (to be filled) |
   | Content genuinely exists | Write it |

   ⚠️ **Don't use "none" to hide "I don't know".** Not found ≠ does not exist.
   **Don't leave blanks either** — a blank can't distinguish "forgot to fill" from "there is none".

5. The three optional frontmatter fields (`maturity`, `赋能`, `source_class`) **may be omitted or left empty** — they aren't part of your workflow. The "no blank section" rule applies to the nine content sections and the required identity fields, not to these.
5. Self-check against the acceptance checklist above

### Optional fields

`maturity` (G0–G5), `赋能`, and `source_class` come from our internal conventions. **Keep them, replace them, or delete them** — see 「可选字段的处理」 above for the full definitions and how to substitute your own.

### Dependencies & cost

| | |
|---|---|
| Runtime | any Markdown editor, no plugins |
| Software deps | **none** (plain-text template) |
| Cost | **zero** |
| Optional | video sources must be transcribed first — **transcription tooling and model cost are separate** |

### Six hard rules (baked into the template)

1. **Never drop a whole section** — write "none" if absent
2. **Corrections never touch the body** — table only
3. **Don't guess** — mark low-confidence items "needs review"; write "待补" rather than inventing
4. **Numbers need a source** — unsourced numbers are marked "unverified" and must not reach published output
5. **Flag absolute claims** (躺赚/包赚/稳赚/100%) with ⚠️
6. **`sources` is mandatory** — no conclusion without a source

### Known limitations

- Ships **no** download/transcription capability
- `maturity` / `赋能` / `source_class` rely on **our internal conventions** — define your own equivalents
- O/E grading is **not an industry standard**, it's our convention

### Real validation status

**Done:** logged in our internal asset ledger as "filled four times on 2026-09-30" — four real sources were archived with it.

**Not done:** this export did **not** re-run those four tasks; **no** independent external trial; **no** cross-editor / cross-platform compatibility testing.

Treat it as **internally used with a real usage record**, not a broadly validated product.

---

## 文件清单

```
ray-collection-prompt-content-material-card/
├── README.md                    本文件
├── LICENSE                      MIT License
├── NOTICE.md                    权属、来源与改动说明
├── CHANGELOG.md                 版本变更
├── MANIFEST.txt                 逐文件 SHA256（可校验完整性）
└── templates/
    └── content-material-card-template-V2.2.md    九节模板（唯一必读文件）
```

**必要文件就是 `templates/` 里那一个模板。** 其余是说明与校验文件。

---

## 许可：MIT

本包采用 **MIT License**，Copyright (c) 2026 锐泽 Ray。

**你不需要额外申请，也不设付费墙、不索取注册或个人资料。** 下载即可用。

唯一义务：**分发副本或实质性使用时，保留 `LICENSE` 文件与上述版权声明。**

这不是「能看不能用」的限制性授权——复制模板、填写自己的卡片、改成你自己的版本、
用于自己的收费业务、公开发布，都允许。

**许可只覆盖本包。** 你用本模板填出来的卡片内容归你；但如果你在卡片里引用了别人的素材，
那些素材的版权仍是原作者的，与本包的 MIT 无关。