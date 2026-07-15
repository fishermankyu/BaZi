# 正格 (Regular Pattern / 八格) — What Kind of Chart This Is

格局 answers a different question than anything covered so far. 身强身弱 (`strength_formula.md`) is a scalar — how much support vs. drain. 従格 (`congge.md`) is an extreme-case override. 格局 is neither of those — it's a **qualitative classification of the chart's overall structure**, built around which Ten God the month branch puts in charge. Two charts can have similar Score% and still be structurally different "kinds" of chart (a 正官格 chart and a 食神格 chart can both be mildly 身弱, but they're different structures with different things they need protected).

**Relationship to the rest of the workflow**: 格局 is normally determined right after Ten Gods (step 4), before the strength-scoring machinery. Once 格局 is identified, 身强身弱 tells you whether the chart can "carry" that structure or needs help — 格局 is the noun, 扶抑 is how healthy that noun is. 従格 is what happens when the Day Master is so extreme that the normal 格局 framework doesn't meaningfully apply at all (see integration note at the end).

## How to determine 格局 (取格规则)

Priority order, stop at the first that applies:

1. **月支本气透干**: if the month branch's main qi (本气) appears on any heavenly stem in the chart (year/month/hour — day stem is the Day Master itself and doesn't count), take the Ten God that stem represents as the 格. This is the default, most common case.
2. **月支中气或余气透干** (if main qi didn't transparent): if the month branch's middle or residual qi transparents on a stem instead, take that Ten God as the 格.
3. **月支所有藏干都未透干**: take the Ten God corresponding to the month branch's main qi anyway (格局 by qi alone, not requiring transparency) — this is a weaker, less "rooted" version of the same 格.
4. **Fallback**: if none of the above gives a usable candidate (e.g. the month branch's qi is 比肩/劫财 — see below), look at which Ten God has the strongest, best-rooted presence elsewhere in the chart and use that instead.

**比肩/劫财 cannot be a 格** — they share the Day Master's own element and have no 生克 relationship *to* the Day Master (you can't be in a structural relationship with yourself). If the month branch's main qi is the Day Master's own element, the chart instead falls into two special adjacent categories:
- **建禄格**: month branch is the Day Master's 禄 position (the branch matching the Day Master's own element, e.g. 甲日生于寅月).
- **月刃格 (阳刃格)**: month branch is the Day Master's 帝旺/羊刃 position — only applies to yang Day Masters (e.g. 丙日生于午月).

Some schools count these two as part of a ten-pattern set; others treat them as adjacent-but-separate from the eight Ten-God-named 正格. Either way, when 建禄/月刃 applies, look at the next-strongest transparent stem elsewhere in the chart to find a secondary usable 格 for practical purposes, since 建禄/月刃 alone describes the *root strength* more than a structural relationship to lean on.

**If two candidates transparent simultaneously** (e.g. both a 食神 and a 七杀 stem present): prefer whichever is more directly tied to the month branch itself (当令者优先), then whichever sits closer to the month pillar in the four pillars.

## 八正格: 成格条件、喜、忌

| 格 | 成格条件 | 喜 (supports the structure) | 忌 (breaks the structure) |
|---|---|---|---|
| **正官格** | 月令正官透干,不被刑冲克破 | 财生官, 印护官(化伤官) | 伤官克官 ("伤官见官,为祸百端"), 七杀混官 (官杀混杂) |
| **七杀格 (偏官格)** | 月令七杀透干,有制或有化 | 食神制杀, 或印化杀(转化七杀为助力) | 无制无化 (七杀失控,凶性显); 财生杀太过 |
| **正财格** | 月令正财透干,不被劫夺 | 食伤生财, 官星护财(挡住比劫) | 比劫夺财, 印星制食伤(断了财的生源) |
| **偏财格** | 月令偏财透干 | 日主强旺能掌控财 | 官杀混杂(财杀纠缠), 财多身弱(扛不动) |
| **食神格** | 月令食神透干,不被枭神(偏印)克制 | 身强, 财星(食神生财,顺畅出秀) | 枭神夺食(偏印克食神), 比劫过重(分薄食神的力量) |
| **伤官格** | 月令伤官透干 | 印护伤官(化伤官锋芒), 或配合七杀(伤官驾杀) | 无制无通关(容易恃才傲物,运势起伏大); 伤官见官 |
| **正印格** | 月令正印透干,不被财破 | 官杀生印(印有源头), 身弱喜印生扶 | 财坏印(财克印), 印过重身弱反被拖累(印重身轻) |
| **偏印格** | 月令偏印透干 | 食神制枭得当(不要枭神反夺食神), 官杀生印 | 偏印夺食(克制食神过度), 印重无制 |

## 格局清浊成败 (三条件)

Beyond just "does the pattern technically exist," judge how *clean* it is — this maps onto the traditional language of 清/浊/成/败/有情/无情/有力/无力:

1. **透干有根**: the defining stem isn't just floating — it should have real root in the branches (main/middle/residual qi backing it up), not merely visible on a stem with nothing supporting it underneath.
2. **清纯不杂**: the pattern isn't muddied by competing/conflicting Ten Gods crowding the chart (e.g. a clean 正官格 with a stray 七杀 also present becomes "官杀混杂," a recognized flaw — mixed authority, not a clean single structure).
3. **有护有制**: whatever would naturally threaten this pattern (per the 忌 column above) is either absent, or present but controlled/protected against.

Missing any of the three doesn't necessarily destroy the pattern outright, but each miss is a real flaw ("破格" in the more severe cases) worth naming rather than glossing over — a chart can technically "have" a 正官格 and still be a fairly compromised, low-quality version of one.

## Integrating with the rest of the workflow

Revised placement: 格局 slots in **right after Ten Gods (step 4), before or alongside branch relationships (step 5)** — determine it early, since 扶抑 and later modules build on top of it rather than the reverse.

- If 従格 (`congge.md`) is later confirmed for this chart (Score% past the extreme thresholds in `strength_formula.md` §5, and passing 従格's structural gates), **the 従格 reading takes over and the ordinary 正格 framework no longer meaningfully applies** — say so explicitly rather than reporting both as if they're compatible parallel conclusions. A chart is read as either an ordinary 正格 (with 扶抑/调候/通关 as needed) or as a 従格, not both at once.
- Otherwise (ordinary strength range, no 従格), the 正格 identified here is the backdrop that 扶抑, 调候, and 通关 all operate within — e.g. a 正官格 chart's 喜用神 conversation should specifically flag whether 伤官 or 官杀混杂 are present (格局-specific concerns), not just the generic 扶抑 support/drain read.
- Only surface the full 成格/败格 nuance (清浊成败 breakdown) in a full walkthrough (per the Triage step) — for a quick answer, just name the 格 and whether it's clean or compromised in a sentence.

## Calibration tests run against 取格规则

| # | Chart | Day Master | Designed to test | Result | Expected? |
|---|---|---|---|---|---|
| 1 | 己卯 戊辰 壬子 己酉 | 壬 (Water) | Main rule — 月支本气透干 | 月支辰本气戊, transparent on the month stem itself (自坐, strong root) → **七杀格**, clean transparent-and-rooted case | ✓ |
| 2 | 辛丑 丁未 甲子 丙寅 | 甲 (Wood) | Fallback rule 2 — 本气未透,退求中气 | 月支未: 本气己(财)未见于any stem; 中气丁(伤官) transparent on month stem → **伤官格** (taken from 中气, not 本气, correctly skipping the untransparented main qi) | ✓ |
| 3 | 甲寅 甲午 丙午 戊子 | 丙 (Fire) | 比劫卡月支 → must not be taken as a 格; falls to 建禄/月刃 + fallback search | 月支午本气丁 = 劫财(same element, can't be a 格) → correctly excluded; chart classified as **月刃格** (yang Day Master sitting on 帝旺/羊刃), with 甲(印) — doubly present and rooted — surfaced as the practical secondary reference per the fallback rule | ✓ |

All three branches of the 取格 priority ladder (main-qi hit, main-qi miss falling to secondary qi, 比劫 exclusion triggering the 建禄/月刃 special case) behaved as expected — no case defaulted to reporting a 比劫 as a 格, and the fallback correctly distinguished "untransparented main qi, try secondary qi" from "main qi is fundamentally ineligible (比劫), skip to the special case" rather than conflating the two.