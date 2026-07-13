# Branch Relationships: 合會刑沖害破 + Strength Formula Modifiers

Supplements `strength_formula.md`: how Earthly Branches interact with each other (combine, clash, punish, harm, break), and how to quantify these relationships as modifiers feeding into the Day Master strength score. **Same caveat as elsewhere**: exact coefficients vary by school — this is an internally consistent teaching convention, not a universal standard.

## 1. Relationship Definitions

### Combinations (合) — resonance-type

**Six Combinations (六合)** — branch pairs: 子丑合 (Earth), 寅亥合 (Wood), 卯戌合 (Fire), 辰酉合 (Metal), 巳申合 (Water), 午未合 (no transformation / Sun-Moon combination)

**Three Harmonies (三合局)** — three branches forming a full elemental bureau (strongest); missing one branch = 半合/拱合 "half combination" (half strength):
```
申子辰 → Water bureau   亥卯未 → Wood bureau
寅午戌 → Fire bureau    巳酉丑 → Metal bureau
```

**Three Meetings (三會)** — branches grouped by seasonal direction, must be all three present, strongest of the combination types:
```
寅卯辰 → East, Wood     巳午未 → South, Fire
申酉戌 → West, Metal    亥子丑 → North, Water
```

### Clash (沖) — damage-type

**Six Clashes (六沖)** — branches six positions apart: 子午, 丑未, 寅申, 卯酉, 辰戌, 巳亥. A clash on the month branch (月令) affects the whole chart most heavily.

### Punishment (刑) — damage-type

```
Ungrateful Punishment (無恩之刑): 寅巳申 (mutual)
Relying-on-Power Punishment (恃勢之刑): 丑戌未 (mutual)
Rudeness Punishment (無禮之刑): 子卯 (pair, no third branch needed)
Self-Punishment (自刑): 辰辰 午午 酉酉 亥亥
```

### Harm (害) / Break (破) — damage-type, decreasing strength

**Six Harms (六害)**: 子未, 丑午, 寅巳, 卯辰, 申亥, 酉戌 (logic: one branch's combination partner gets clashed away, so the branch itself is collaterally harmed)

**Six Breaks (六破)**: 子酉, 午卯, 巳申, 寅亥, 辰丑, 戌未 (weakest, many schools ignore entirely)

### Relative strength ordering
```
三會 > 三合 (full) > 六沖 ≈ 三刑 > 六合 > 半合/拱合 > 六害 > 六破
```

## 2. Modifier Coefficients (feed into strength_formula.md scores)

Damage-type (沖/刑/害/破): only discount the affected branch's **main qi (本气)** score, no new score added.
Combination-type (合/會/半合): discount the main qi score **and** add a separate resonance bonus credited to the combined element.

| Relationship | Affected item | Discount | Bonus |
|---|---|---|---|
| 三會 (all 3 present) | each branch's main qi | ×0.3 | + (sum of the 3 branches' original main-qi scores) × 0.8, credited to the meeting's element |
| 三合 (all 3 present) | each branch's main qi | ×0.4 | + (sum of original scores) × 0.6, credited to the bureau's element |
| 半合/拱合 (2 branches) | each branch's main qi | ×0.7 | + (sum of original scores) × 0.4, credited to the bureau's element |
| 六合 (no transformation, default) | both branches' main qi | ×0.8 | none |
| 六合 (transforms/化, requires the transformed element to be seasonally dominant or rooted elsewhere) | both branches' main qi | ×0.5 | + (sum of original scores) × 0.5, credited to the transformed element |
| 六沖 | both branches' main qi | ×0.5 | none |
| 三刑 (all 3 present) | each branch's main qi | ×0.75 | none |
| Two-branch punishment (e.g. 子卯) | both branches' main qi | ×0.85 | none |
| 自刑 | that branch's main qi | ×0.9 | none |
| 六害 | both branches' main qi | ×0.9 | none |
| 六破 | both branches' main qi | ×0.97 (many schools treat as ×1.0, i.e. ignore) | none |

**Stacking rule**: if one branch is involved in multiple relationships, multiply the discount factors together. Middle/residual hidden-stem qi (中气/余气) are not discounted by default — only main qi is affected — unless a more granular school-specific treatment is wanted.

**Judging whether a 六合 "transforms" (化)**: default to "combines but doesn't transform" (×0.8, tied down but no element change). Only upgrade to "transforms" (×0.5 + bonus) if the transformed element is dominant in the month branch, or has strong roots elsewhere in the chart.

## 3. Worked Example

Kevin's three pillars (no hour pillar): **己卯 戊辰 壬子**, Day Master 壬 (Yang Water), month branch 辰 (Earth — so per seasonal table: Earth=旺, Metal=相, Fire=休, Wood=囚, Water=死)

Original scores (from `strength_formula.md`'s base × positional × seasonal):
- 卯 main qi 乙 (year branch, Wood): 0.6
- 辰 main qi 戊 (month branch, Earth): 3.0
- 辰 middle qi 乙 (Wood, no discount): 0.36
- 辰 residual qi 癸 (Water, no discount): 0.09
- 子 main qi 癸 (day branch, Water): 0.36

Three relationships present: 卯辰害 (harm), 子辰半合水 (half-combination toward Water, missing 申), 子卯相刑 (Rudeness Punishment)

After discounts:
- 卯 main qi: 0.6 × (harm 0.9 × punishment 0.85) = 0.6 × 0.765 = **0.459**
- 辰 main qi: 3.0 × (harm 0.9 × half-combo 0.7) = 3.0 × 0.63 = **1.89**
- 子 main qi: 0.36 × (half-combo 0.7 × punishment 0.85) = 0.36 × 0.595 = **0.214**

Water resonance bonus from 子辰半合: (0.36 + 3.0) × 0.4 = **+1.344** (credited to Water)

Totals by element (Day Master is Water, so Water/Metal support 帮身, Wood/Fire/Earth drain 耗身; no Metal or Fire present here):
- Earth (官殺, drain) = 己1.4 + 戊2.1 + 辰main1.89 ≈ **5.39**
- Wood (食傷, drain) = 卯main0.459 + 辰middle0.36 ≈ **0.819**
- Water (比劫, support) = 辰residual0.09 + 子main0.214 + half-combo bonus1.344 ≈ **1.648**

Support 1.648 : Drain 6.209 ≈ **1:3.77** — leaning weak (身弱), Earth (官殺) is the heaviest drain. This example is missing the hour pillar, so the reading is incomplete; it's only meant to validate the formula mechanics.
