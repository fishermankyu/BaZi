# Day Master Strength Scoring Formula

A weighted approach to quantify 身强/身弱 (Day Master strength/weakness) instead of just eyeballing counts. **Caveat to always give the user**: exact numeric weights vary by school/book — this is *a* reasonable, internally consistent convention, not a universally fixed standard.

## Formula

```
Score(item) = BaseScore(position type) × PositionalWeight(pillar) × SeasonalMultiplier(vs. month branch)
```

**Exception — month branch's own main qi**: if `item` *is* the month branch's main qi (i.e. item's element = month branch's own element, which is definitionally always true for that one item), SeasonalMultiplier is fixed at **×1.0** instead of being looked up in the table below. Rationale: "being in command of the season" (当令) is already fully expressed by PositionalWeight = ×1.5 for that item. Running it through the 旺相休囚死 table on top of the positional weight double-counts the same fact (month governs the chart) twice, which structurally inflates every chart's month-branch-main-qi term to the ceiling regardless of the rest of the chart. Every other item — month stem, month branch's middle/residual qi, and all items in the other three pillars — still uses the full three-factor multiplication, because for them the seasonal comparison is genuine independent information, not a restatement of their own position.

## 1. Base score by position type (using branch main-qi = 1 as the reference unit)

| Position type | Base score |
|---|---|
| Earthly Branch main qi (本气) | 1.0 |
| Heavenly Stem (透干) | 0.7 |
| Branch middle qi (中气) | 0.4 |
| Branch residual qi (余气) | 0.2 |

Rationale: branch main qi is treated as the deepest, most stable root ("根深"); a stem floating alone in the sky is more exposed to being directly clashed/combined away ("苗"), hence slightly lower than main qi despite being fully "visible." Middle/residual qi are progressively weaker, partial presences.

## 2. Positional weight (which pillar the item sits in)

| Pillar position | Weight |
|---|---|
| Month stem/branch (月柱) | ×1.5 |
| Day branch (日支) | ×1.2 |
| Year stem/branch, Hour stem/branch | ×1.0 |

Month pillar gets the highest weight because the month branch (月令) sets the seasonal backdrop for the whole chart — it's the single most influential position.

## 3. Seasonal multiplier — relationship of the item's element to the month-branch's element (旺相休囚死)

| State | Multiplier | Condition |
|---|---|---|
| 旺 Wang (thriving) | ×2.0 | item's element = month branch's element |
| 相 Xiang (supported) | ×1.5 | month branch's element generates item's element |
| 休 Xiu (resting) | ×1.0 | item's element generates month branch's element |
| 囚 Qiu (imprisoned) | ×0.6 | item's element controls month branch's element |
| 死 Si (dead) | ×0.3 | month branch's element controls item's element |

Remember the exception above: skip this table (use ×1.0 instead) for the one item that *is* the month branch's own main qi.

## 4. Branch relationship modifiers (刑沖合會害破)

Before finalizing each branch's score, check all pillar-pair combinations for 合/會/沖/刑/害/破 (see `references/xingchonghehui.md` for full definitions and coefficients). Damage-type relationships (沖/刑/害/破) discount the affected branch's main-qi score; combination-type relationships (六合/三合/三會/半合) discount the main-qi score *and* add a separate resonance bonus credited to the combined element. Apply these modifiers to the base×positional×seasonal score from steps 1–3 above, then carry the adjusted numbers into the final support/drain tally.

## 5. Normalization

Raw support/drain totals aren't comparable across charts (a chart with more hidden-stem occurrences naturally produces bigger raw numbers). Convert to a percentage before classifying:

```
Score% = SupportTotal / (SupportTotal + DrainTotal) × 100
```

- SupportTotal = sum of all 比劫 (same element as Day Master) + 印 (generates Day Master) items
- DrainTotal = sum of all 食伤 (Day Master generates) + 财 (Day Master controls) + 官杀 (controls Day Master) items
- 50% = perfectly balanced; higher = stronger Day Master, lower = weaker.

### Classification thresholds (provisional — flag as **待校准**, not settled convention)

| Score% | Classification |
|---|---|
| > 80% | 极强 (extremely strong) — check whether 从強格 applies |
| 65–80% | 身强 (strong) |
| 35–65% | 平衡 (balanced) |
| 20–35% | 身弱 (weak) |
| < 20% | 极弱 (extremely weak) — check whether 從弱格 applies |

The 80%/20% extremes are exactly where the 格局 (structure) module should double-check whether the ordinary support-vs-drain reading even applies, since 從強/從弱 charts are explicit exceptions to this formula.

## Worked example 1 — clearly/extremely weak

Chart: 己卯 丙寅 庚午 癸未 — Day Master 庚 (Yang Metal), month branch 寅 (Wood).

| Item | Position | Base | Pos. weight | Seasonal | Score |
|---|---|---|---|---|---|
| 己 (year stem) | stem | 0.7 | ×1.0 | Wood controls Earth → 死 ×0.3 | 0.21 |
| 卯 main qi 乙 | year branch | 1.0 | ×1.0 | same element → 旺 ×2.0 | 2.0 |
| 丙 (month stem) | stem | 0.7 | ×1.5 | Wood generates Fire → 相 ×1.5 | 1.575 |
| 寅 main qi 甲 | month branch | 1.0 | ×1.5 | **is month branch's own main qi → fixed ×1.0** | 1.5 |
| 寅 middle qi 丙 | month branch | 0.4 | ×1.5 | 相 ×1.5 | 0.9 |
| 寅 residual 戊 | month branch | 0.2 | ×1.5 | 死 ×0.3 | 0.09 |
| 午 main qi 丁 | day branch | 1.0 | ×1.2 | 相 ×1.5 | 1.8 |
| 午 middle qi 己 | day branch | 0.4 | ×1.2 | 死 ×0.3 | 0.144 |
| 癸 (hour stem) | stem | 0.7 | ×1.0 | Water generates Wood → 休 ×1.0 | 0.7 |
| 未 main qi 己 | hour branch | 1.0 | ×1.0 | 死 ×0.3 | 0.3 |
| 未 middle qi 丁 | hour branch | 0.4 | ×1.0 | 相 ×1.5 | 0.6 |
| 未 residual 乙 | hour branch | 0.2 | ×1.0 | 旺 ×2.0 | 0.4 |

**Totals by element** (excluding the Day Master's own element, Metal, which had no other occurrence here):
- Earth (印, supports) = 0.744
- Wood (财, drains) = 1.5 + 0.9 + 0.09 + 0.4 = 2.89
- Fire (官杀, drains) = 1.575 + 1.8 + 0.144 = 3.519
- Water (食伤, drains) = 0.7

SupportTotal = 0.744. DrainTotal = 2.89 + 3.519 + 0.7 = 7.109. (Previously, before this fix, DrainTotal was 10.975 — the month branch's main qi term alone dropped from 3.0 to 1.5, a 1.5-point reduction on the drain side.)

**Score% = 0.744 / (0.744 + 7.109) × 100 ≈ 9.5%** → 极弱 (extremely weak). Still clearly and heavily weak, same conclusion as before the fix, but the number is now less inflated and comparable across charts. With support this thin (no 比劫 at all, only a modest, seasonally-dead 印) and drains spread across three categories (财/官杀/食伤), the chart is a strong candidate for checking 從弱格 (following-weak structure) rather than assuming the ordinary formula applies at face value.

## Worked example 2 — textbook "strongest" case

Chart: 甲丁甲乙 / 寅卯寅亥 — Day Master 甲 (Yang Wood), month branch 卯 (Wood). This chart is commonly cited as a maximal-strength textbook example: 得令 (month branch shares Day Master's element) + 得地 (rooted in year and day branches) + 得势 (multiple Wood/Water stems and branches supporting).

| Item | Position | Base | Pos. weight | Seasonal | Score |
|---|---|---|---|---|---|
| 甲 (year stem) | stem | 0.7 | ×1.0 | same element → 旺 ×2.0 | 1.4 |
| 寅 main qi 甲 | year branch | 1.0 | ×1.0 | 旺 ×2.0 | 2.0 |
| 寅 middle qi 丙 | year branch | 0.4 | ×1.0 | Wood generates Fire → 相 ×1.5 | 0.6 |
| 寅 residual 戊 | year branch | 0.2 | ×1.0 | Wood controls Earth → 死 ×0.3 | 0.06 |
| 丁 (month stem) | stem | 0.7 | ×1.5 | 相 ×1.5 | 1.575 |
| 卯 main qi 乙 | month branch | 1.0 | ×1.5 | **is month branch's own main qi → fixed ×1.0** | 1.5 |
| 寅 main qi 甲 (day branch) | day branch | 1.0 | ×1.2 | 旺 ×2.0 | 2.4 |
| 寅 middle qi 丙 (day branch) | day branch | 0.4 | ×1.2 | 相 ×1.5 | 0.72 |
| 寅 residual 戊 (day branch) | day branch | 0.2 | ×1.2 | 死 ×0.3 | 0.072 |
| 乙 (hour stem) | stem | 0.7 | ×1.0 | 旺 ×2.0 | 1.4 |
| 亥 main qi 壬 | hour branch | 1.0 | ×1.0 | Water generates Wood → 休 ×1.0 | 1.0 |
| 亥 middle qi 甲 | hour branch | 0.4 | ×1.0 | 旺 ×2.0 | 0.8 |

**Totals by element** (Day Master's own element is Wood — here Wood occurs elsewhere too, via 比劫, so it's tallied as support, not excluded):
- Wood (比劫, supports) = 1.4 + 2.0 + 1.5 + 2.4 + 1.4 = 8.7
- Water (印, supports) = 1.0 + 0.8 = 1.8
- Fire (食伤, drains) = 0.6 + 1.575 + 0.72 = 2.895
- Earth (财, drains) = 0.06 + 0.072 = 0.132
- (no Metal/官杀 present)

SupportTotal = 8.7 + 1.8 = 10.5. DrainTotal = 2.895 + 0.132 = 3.027.

**Score% = 10.5 / (10.5 + 3.027) × 100 ≈ 77.6%** → 身强 (strong), consistent with the source material's "strongest" label. (Before the fix, the month branch's main qi term alone contributed 3.0 instead of 1.5 to the support side — the single largest term in the whole table, larger even than the day branch's own main qi at 2.4 — which was the clearest sign the old formula was over-weighting that one item.)

## Using the result

- Compute Score% and classify using the thresholds table above.
- If asked for 喜用神 (favorable elements): weak Day Master generally favors elements that support it (印, 比劫); strong Day Master generally favors elements that drain/balance it (官杀/财/食伤). Always caveat this is the standard heuristic, not a fixed rule — some configurations (e.g. 从弱格/从强格 "following" structures, typically flagged when Score% is past the 80%/20% extremes) invert this, and a full determination should look at the whole chart, not just the ratio.
- Treat the specific thresholds (65/35, 80/20) as a provisional convention pending more calibration examples, not an authoritative standard — say so if the user asks where the numbers come from.