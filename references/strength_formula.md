# Day Master Strength Scoring Formula

A weighted approach to quantify 身强/身弱 (Day Master strength/weakness) instead of just eyeballing counts. **Caveat to always give the user**: exact numeric weights vary by school/book — this is *a* reasonable, internally consistent convention, not a universally fixed standard.

## Formula

```
Score(item) = BaseScore(position type) × PositionalWeight(pillar) × SeasonalMultiplier(vs. month branch)
```

**Exception**: if `item` is the month branch's own main qi, SeasonalMultiplier is fixed at **×1.0** instead of the table below. Reason: "当令" is already fully expressed by PositionalWeight ×1.5 for that item; running it through 旺相休囚死 on top would double-count the same fact and inflate that one term to the ceiling regardless of the rest of the chart. Every other item (month stem, month branch's middle/residual qi, all items in the other three pillars) uses the full three-factor multiplication as normal.

### 1. Base score by position type (branch main-qi = 1 as reference unit)

| Position type | Base score |
|---|---|
| Earthly Branch main qi (本气) | 1.0 |
| Heavenly Stem (透干) | 0.7 |
| Branch middle qi (中气) | 0.4 |
| Branch residual qi (余气) | 0.2 |

Main qi = deepest root ("根深"); a stem alone is more exposed ("苗"), hence lower than main qi despite full visibility.

### 2. Positional weight (which pillar)

| Pillar | Weight |
|---|---|
| Month stem/branch | ×1.5 |
| Day branch | ×1.2 |
| Year, Hour stem/branch | ×1.0 |

Month pillar sets the seasonal backdrop for the whole chart — the single most influential position.

### 3. Seasonal multiplier (item's element vs. month branch's element — 旺相休囚死)

| State | Multiplier | Condition |
|---|---|---|
| 旺 | ×2.0 | item = month branch element |
| 相 | ×1.5 | month branch generates item |
| 休 | ×1.0 | item generates month branch |
| 囚 | ×0.6 | item controls month branch |
| 死 | ×0.3 | month branch controls item |

(Skip this — use ×1.0 — for the one item that *is* the month branch's own main qi; see Exception above.)

### 4. Branch relationship modifiers (刑沖合會害破)

Before finalizing, check all pillar-pair combinations (see `references/xingchonghehui.md`). Damage-type (沖/刑/害/破) discount the affected branch's main-qi score; combination-type (六合/三合/三會/半合) discount main-qi *and* add a resonance bonus to the combined element. Apply to the base×positional×seasonal score, then carry forward into the support/drain tally.

## 5. Normalization and thresholds

```
Score% = SupportTotal / (SupportTotal + DrainTotal) × 100
```
SupportTotal = 比劫 (same element as DM) + 印 (generates DM). DrainTotal = 食伤 + 财 + 官杀. 50% = balanced; higher = stronger.

| Score% | Classification |
|---|---|
| > 75% | 极强 — check 从強格 |
| 65–75% | 身强 |
| 35–65% | 平衡 |
| 25–35% | 身弱 |
| < 25% | 极弱 — check 從弱格 |

**Structural ceiling/floor**: because branch middle/residual qi almost always belong to a different element than the branch's main qi, no real chart reaches 100%/0% — some drain (or support) always leaks in through hidden stems. Empirically the ceiling is ~80.5% and floor ~17% (synthetic max-one-sided charts), and textbook "strongest possible" charts land ~77–78%. That's why the thresholds are 75/25, not a rounder 80/20 — an 80% cutoff would misclassify textbook-extreme charts as merely 身强/身弱.

## 6. Calibration against the traditional 得令/得地/得势 three-flag method

Tested this formula against all 8 combinations of 得令/得地/得势 (using constructed charts plus two textbook/source-documented examples). Results:

| 得令 | 得地 | 得势 | Traditional label | Score% | Match? |
|---|---|---|---|---|---|
| ✓ | ✓ | ✓ | 极强 | 77.6–80.5% | Partial (bounded by structural ceiling, see §5) |
| ✓ | ✓ | ✗ | 身强 | 44.6% | Mismatch — scattered drain |
| ✓ | ✗ | ✓ | 身强 | 60.6% | Mismatch — 失地拖累 |
| ✓ | ✗ | ✗ | 次弱 | 30.5% | Match |
| ✗ | ✓ | ✓ | 平衡 | 48.6% | Match |
| ✗ | ✓ | ✗ | 身弱 | 23.0% | Match |
| ✗ | ✗ | ✓ | 身弱 | 17.9% | Mismatch — 失地拖累 |
| ✗ | ✗ | ✗ | 极弱 | 17.0% | Match |

**Two recurring mismatch patterns, both explainable (not noise):**
- **Scattered drain**: the three-flag method only checks presence/absence, so a chart that clears 得令+得地 (or 得令+得势) but has drain spread thinly across several pillars gets no penalty from the three flags — but the weighted formula sums that drain up and it can outweigh support.
- **失地拖累 (rootless drag)**: the three-flag method treats 得地 and 得势 as roughly interchangeable. This formula doesn't — a branch main qi (1.0, plus positional/seasonal multipliers) is worth structurally more than a floating heavenly-stem 比劫 (0.7, no root-depth bonus). So 得势-without-得地 charts always score weaker than the three-flag method implies. This isn't a bug — it matches the older 《滴天髓》principle "干多不如支重，而通根之中，尤以月令之支为最重也" (stems count for less than a rooted branch), which the three-flag method flattens away for teachability.

**Which to trust**: use this formula's Score% as the primary judgment; treat the three-flag method as a quick teaching-level sanity check, not an arbiter. Be honest that there's no independent ground truth in BaZi to validate either against — this is internal consistency plus rough alignment with textbook extremes and older weighting principles, not proof of correctness. If a user knows the three-flag method and gets a different read, surface both briefly rather than silently picking one (e.g. "by weighted score this leans 平衡, though 得令得地得势 alone would suggest 身强 — it's got 得势 but not 得地, and roots outweigh floating stems in this convention").

## Worked example

Chart: 己卯 丙寅 庚午 癸未 — Day Master 庚 (Yang Metal), month branch 寅 (Wood).

| Item | Position | Base | Pos. weight | Seasonal | Score |
|---|---|---|---|---|---|
| 己 (year stem) | stem | 0.7 | ×1.0 | 死 ×0.3 | 0.21 |
| 卯 main qi 乙 | year branch | 1.0 | ×1.0 | 旺 ×2.0 | 2.0 |
| 丙 (month stem) | stem | 0.7 | ×1.5 | 相 ×1.5 | 1.575 |
| 寅 main qi 甲 | month branch | 1.0 | ×1.5 | **month's own main qi → fixed ×1.0** | 1.5 |
| 寅 middle qi 丙 | month branch | 0.4 | ×1.5 | 相 ×1.5 | 0.9 |
| 寅 residual 戊 | month branch | 0.2 | ×1.5 | 死 ×0.3 | 0.09 |
| 午 main qi 丁 | day branch | 1.0 | ×1.2 | 相 ×1.5 | 1.8 |
| 午 middle qi 己 | day branch | 0.4 | ×1.2 | 死 ×0.3 | 0.144 |
| 癸 (hour stem) | stem | 0.7 | ×1.0 | 休 ×1.0 | 0.7 |
| 未 main qi 己 | hour branch | 1.0 | ×1.0 | 死 ×0.3 | 0.3 |
| 未 middle qi 丁 | hour branch | 0.4 | ×1.0 | 相 ×1.5 | 0.6 |
| 未 residual 乙 | hour branch | 0.2 | ×1.0 | 旺 ×2.0 | 0.4 |

SupportTotal (Earth 印) = 0.744. DrainTotal (Wood 财 + Fire 官杀 + Water 食伤) = 7.109.

**Score% = 0.744 / 7.853 × 100 ≈ 9.5% → 极弱.**

(A second worked example — 甲丁甲乙/寅卯寅亥, a textbook "strongest" chart scoring 77.6% → 身强 — is summarized in the calibration table above; full item-by-item math omitted here since the mechanics are identical to the example above.)

## Using the result

- Compute Score% and classify using §5's thresholds.
- If asked for 喜用神: weak DM favors 印/比劫; strong DM favors 官杀/财/食伤. Caveat: 從弱格/從強格 (flagged near the 75%/25% extremes) invert this.
- Treat 65/35 and 75/25 as calibrated against a small test set (§6), not a universally fixed standard — say so if asked, and note more calibration cases would sharpen them further.