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

**Judging whether a 六合 "transforms" (化)**: default to "combines but doesn't transform" (×0.8, tied down but no element change). Only upgrade to "transforms" (×0.5 + bonus) if the transformed element is dominant in the month branch, or has strong roots elsewhere in the chart.

## 2a. Stacking rule (revised: marginal decay, not flat multiplication)

Multiplying every applicable discount straight together over-punishes a branch that's caught in several relationships at once — the punishments aren't independent probabilistic events, and traditional treatments don't compound them that way. Use this instead:

**Step 1 — check for root (透干/坐根) before anything else.** Look up the branch's main-qi element. If that same element appears as a Heavenly Stem anywhere in the four pillars (透干) — including sharing a pillar with it (自坐, e.g. a stem sitting directly above its own branch) — the branch has real backing and resists being knocked around. If there's no such stem anywhere in the chart, the branch is "rootless" for this purpose.
- Rooted branch: halve the "damage" (see Step 2) from every damage-type relationship (沖/刑/害/破) affecting it.
- Rootless branch: damage-type relationships apply at full strength.
- This root check does not apply to combination-type (合/會/半合) relationships — those aren't about resisting damage, they're about a resonance bond forming.

**Step 2 — convert each relationship's discount to a "damage" amount, then decay.** Damage = 1 − discount (e.g. 六沖's ×0.5 discount = 0.5 damage; 六害's ×0.9 discount = 0.1 damage). Rank the branch's relationships by the strength ordering (三會 > 三合 > 六沖 ≈ 三刑 > 六合 > 半合 > 六害 > 六破) and sum with each successive one weighted at half the last:

```
Total damage = damage₁×1.0 + damage₂×0.5 + damage₃×0.25 + damage₄×0.125 ...
Final multiplier = 1 − Total damage  (apply the root halving from Step 1 to each damageᵢ first, if rooted)
```

**Step 3 — check for 合解冲 (combination shields a clash) before finalizing.** If a branch is simultaneously in a 六合/半合/三合 with one neighbor and a 六沖 with another, check whether the *combination partner* is itself intact (not itself heavily damaged by other relationships). If the partner is intact, the combination meaningfully shields the clash — halve the clash's damage contribution again (on top of Step 2's decay weighting). If the partner is itself under heavy attack from other relationships ("can't help, in trouble itself"), the shield doesn't hold — the clash applies at its normal decayed weight.

Middle/residual hidden-stem qi (中气/余气) are still not discounted by default — only main qi is affected.

**Caveat**: this decay model, the root-check, and the 合解冲 priority rule are one reasonable way to avoid the over-punishment that flat multiplication causes — not a settled standard. Different schools resolve simultaneous relationships differently; treat this as *a* defensible convention for comparing charts consistently, not *the* authoritative resolution.

## 3. Worked Example

Kevin's full chart: **己卯 戊辰 壬子 己酉**, Day Master 壬 (Yang Water), month branch 辰 (Earth — so per seasonal table: Earth=旺, Metal=相, Fire=休, Wood=囚, Water=死)

Original scores (from `strength_formula.md`'s base × positional × seasonal), before any branch-relationship modifier:
- 卯 main qi 乙 (year branch, Wood): 0.6
- 辰 main qi 戊 (month branch, Earth): 3.0 | middle 乙 (Wood): 0.36 | residual 癸 (Water): 0.09
- 子 main qi 癸 (day branch, Water): 0.36
- 酉 main qi 辛 (hour branch, Metal): 1.5
- Stems (unaffected by branch relationships): 己(year)=1.4, 戊(month)=2.1, 己(hour)=1.4

All six branch-pairs have a relationship here (卯辰害, 卯子刑, 卯酉沖, 辰子半合水[缺申], 辰酉合金[未化], 子酉破) — a dense, all-relationships-triggered case, which makes it a good stress-test for the decay model vs. flat multiplication.

**Root check (透干/坐根) first:**
- 辰 (main 戊, Earth): 戊 also sits as the month **stem**, directly above it → **rooted**
- 子 (main 癸, Water): shares its pillar with 壬 (the Day Master, same element) → **rooted**
- 卯 (main 乙, Wood): no Wood stem anywhere in the chart → **rootless**
- 酉 (main 辛, Metal): no Metal stem anywhere in the chart → **rootless**

**Per-branch decay calculation** (tier order: 沖≈刑 > 合 > 半合 > 害 > 破; root halves only damage-type terms 沖/刑/害/破, not 合/半合):

| 支 | 关系（按强弱排序） | 阻尼后 damage | 加权 Total damage | 最终系数 |
|---|---|---|---|---|
| 卯 (rootless) | 沖0.5(w1.0), 刑0.15(w0.5), 害0.1(w0.25) | 0.5, 0.15, 0.1 | 0.5+0.075+0.025=0.6 | **0.4** |
| 辰 (rooted) | 合0.2(w1.0), 半合0.3(w0.5), 害0.1→0.05(w0.25, root-halved) | 0.2, 0.3, 0.05 | 0.2+0.15+0.0125=0.3625 | **0.6375** |
| 子 (rooted) | 刑0.15→0.075(w1.0, root-halved), 半合0.3(w0.5), 破0.03→0.015(w0.25, root-halved) | 0.075, 0.3, 0.015 | 0.075+0.15+0.00375=0.22875 | **0.77125** |
| 酉 (rootless) | 沖0.5(w1.0, **shield-checked**), 合0.2(w0.5), 破0.03(w0.25) | see below | 0.25+0.1+0.0075=0.3575 | **0.6425** |

**合解冲 check on 酉**: 酉 is clashed by 卯 (沖) but combined with 辰 (合). Is 辰 intact? 辰's own final multiplier is 0.6375 — it kept more than half its strength — so the shield holds: 卯酉沖's damage contribution is halved again, from 0.5 → 0.25, before weighting.

Half-combo (子辰半合) Water bonus, unchanged — uses original scores per the bonus rule: (0.36 + 3.0) × 0.4 = **+1.344**

**Adjusted main-qi scores:**
- 卯 main: 0.6 × 0.4 = **0.24**
- 辰 main: 3.0 × 0.6375 = **1.9125**
- 子 main: 0.36 × 0.77125 = **0.27765**
- 酉 main: 1.5 × 0.6425 = **0.96375**

**Totals by element:**
- Earth (官殺, drain) = 己1.4 + 戊2.1 + 己1.4 + 辰main1.9125 ≈ **6.81**
- Wood (食傷, drain) = 卯main0.24 + 辰middle0.36 ≈ **0.60**
- Water (比劫, support) = 辰residual0.09 + 子main0.278 + half-combo bonus1.344 ≈ **1.71**
- Metal (印, support) = 酉main0.964 ≈ **0.96**

Support 2.68 : Drain 7.41 ≈ **1:2.77** — still clearly 身弱, Earth (官殺) still the dominant drain by a wide margin, but notably less extreme than the flat-multiplication result on this same chart (**1:3.15**) and far less extreme than not discounting at all (**1:4.54**). The gap between the two methods is entirely due to 辰 and 酉 retaining more of their original strength once root and the 合解冲 shield are accounted for, rather than every relationship blindly compounding.

This is the intended behavior of the revised model: it still flags this chart as weak with Earth as the clear pressure point, but it no longer lets a branch caught in three simultaneous relationships get crushed to a fraction of its value just because the math multiplies everything together.
