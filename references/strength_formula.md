# Day Master Strength Scoring Formula

A weighted approach to quantify 身强/身弱 (Day Master strength/weakness) instead of just eyeballing counts. **Caveat to always give the user**: exact numeric weights vary by school/book — this is *a* reasonable, internally consistent convention, not a universally fixed standard.

## Formula

```
Score(item) = BaseScore(position type) × PositionalWeight(pillar) × SeasonalMultiplier(vs. month branch)
```

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

## Worked example

Chart: 己卯 丙寅 庚午 癸未 — Day Master 庚 (Yang Metal), month branch 寅 (Wood).

| Item | Position | Base | Pos. weight | Seasonal | Score |
|---|---|---|---|---|---|
| 己 (year stem) | stem | 0.7 | ×1.0 | Wood controls Earth → 死 ×0.3 | 0.21 |
| 卯 main qi 乙 | year branch | 1.0 | ×1.0 | same element → 旺 ×2.0 | 2.0 |
| 丙 (month stem) | stem | 0.7 | ×1.5 | Wood generates Fire → 相 ×1.5 | 1.575 |
| 寅 main qi 甲 | month branch | 1.0 | ×1.5 | same element → 旺 ×2.0 | 3.0 |
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
- Wood (财, drains) = 5.4
- Fire (官杀, drains) = 4.875
- Water (食伤, drains) = 0.7

**帮身 (support) total ≈ 0.744 vs 耗身 (drain) total ≈ 10.975** → roughly 1:15, a clearly and heavily 身弱 (weak Day Master) chart. When support is this thin (no 比劫 at all, only a modest, seasonally-dead 印), and multiple drain categories (财/官杀/食伤) are all present and several are seasonally reinforced, that's a strong signal of 极弱 (very weak), not just mild imbalance.

## Using the result

- Classify: support-total vs drain-total ratio → clearly strong / balanced / clearly weak / extremely weak.
- If asked for 喜用神 (favorable elements): weak Day Master generally favors elements that support it (印, 比劫 — here Earth/Metal); strong Day Master generally favors elements that drain/balance it (官杀/财/食伤). Always caveat this is the standard heuristic, not a fixed rule — some configurations (e.g. 从弱格/从强格 "following" structures) invert this, and a full determination should look at the whole chart, not just the ratio.
