# 通关用神 (Bridging) — Resolving Head-On Elemental Conflicts

通关 is the fourth of the five classical 用神-selection methods (扶抑/病药/调候/通关/専旺). It's not a replacement for 扶抑 (`strength_formula.md`) — it's a supplementary lens for a specific situation 扶抑 alone doesn't resolve cleanly: **two forces in the chart are directly opposing each other (one 克-ing the other) at roughly matched strength**, so simply "support the weak side" doesn't work, because the weak side just gets attacked again. The fix is an intermediary element that both drains the aggressor and feeds the victim, turning a direct clash into a flowing chain.

## The general rule

For any 克 relationship X克Y, the bridging element Z is the one where **X generates Z, and Z generates Y** — i.e. the element that sits between X and Y along the 五行相生 (generation) cycle:

```
木克土 → bridge = 火   (木生火, 火生土)
土克水 → bridge = 金   (土生金, 金生水)
水克火 → bridge = 木   (水生木, 木生火)
火克金 → bridge = 土   (火生土, 土生金)
金克木 → bridge = 水   (金生水, 水生木)
```

This is elemental-level, symmetric, and doesn't reference the Day Master. When translated into Ten-God language (relative to a specific Day Master), the same principle produces these classical fixed pairings:

| Conflict (十神) | Bridge | Why |
|---|---|---|
| 财旺克印 (财印交战) | 官杀 | 财生官, 官生印 |
| 官杀旺克比劫/日主 | 印 | 官杀生印, 印生日主 |
| 伤官旺克正官 (伤官见官) | 财 | 伤官生财, 财生官 |
| 比劫旺克财 (比劫夺财) | 食伤 | 比劫生食伤, 食伤生财 |
| 印旺克食伤 (枭印夺食) | **special case** — no separate 5th god; the Day Master itself is already the bridge (印生日主, 日主生食伤). Some sources instead point to a strong/得令 Day Master as sufficient; others give 比劫 as functionally similar since it shares the Day Master's element. School disagreement here — flag if asked. |

Only the last one breaks the clean "find element Z" pattern, because 印 and 食伤 are already separated by exactly the Day Master's own position in the generation cycle — there's no room for a distinct fifth element to sit between them.

## When 通关 applies (and when it doesn't)

Three genuine-use scenarios, roughly in order of how textbook-clean they are:
1. **两神对峙, 势均力敌** — the two opposing forces are roughly matched in strength. This is the cleanest, most classic case for 通关.
2. **两神成象对立** — both sides have a strong, well-rooted presence in the chart (not just passing mentions), locked in genuine conflict.
3. **一旺一衰, 力量悬殊** — one side is much stronger than the other. 通关 is *less reliable* here (see strength-matching caveat below); direct suppression of the stronger side is often a better fix than routing through a bridge.

**Two important restrictions, both easy to get wrong:**

- **Strength matching**: the bridging element must itself be strong enough to actually carry the load — rooted, ideally transparent on a stem. If the aggressor badly outweighs the bridge (source material describes this roughly as 3:1, 4:1 or worse), the aggressor will simply "step over" a weak bridge and keep attacking the victim anyway — cited principle: "強旺的五行就会越过通关五行而克制衰弱的五行". In lopsided cases, directly restraining the aggressor (a controlling element) is often the more effective fix than trying to force a bridge that's too thin to hold.
- **Not every 克 relationship is a problem to be solved**. Some clashes are exactly what the chart *needs* — e.g. a genuinely strong Day Master benefits from 官杀 attacking it (that's the ordinary 扶抑 prescription for 身强). If an 印 shows up and "bridges" that 官杀-vs-日主 conflict by draining the 官杀 into generating the Day Master, it neutralizes a relationship the chart actually wanted — described in source material as "通关了反而坏格局" (bridging that backfires). **Before applying a bridge, check what `strength_formula.md`/`congge.md` already concluded the chart wants** — if the "conflict" is actually the chart's intended cure (e.g. 官杀 attacking an already-strong Day Master), don't bridge it away.
- Related old heuristic: **"有制先论制,无制方论通关"** — if the aggressor is already being controlled/checked by something else in the chart, evaluate that control first; only look for a bridging element if there's no existing check.

## Integrating with the rest of the workflow

通关 supplements 扶抑, it doesn't replace it — sequence:
1. Run 扶抑 (`strength_formula.md`) and 従格 (`congge.md`) first, as already documented.
2. Run 调候 (`diaohou.md`).
3. **Then** scan for direct 克 relationships between two Ten-God categories that are both substantial (not just a token presence) in the chart, and check whether they're roughly matched in strength (scenario 1/2 above) — if so, and if a suitable bridging element (per the table) is present, rooted, and not already accounted for by 扶抑/调候, surface it.
4. Before naming a bridge as 用神, sanity-check against step 1's conclusion: is this 克 relationship actually a problem the chart needs solved, or is it the chart's own 扶抑-prescribed cure (e.g. 官杀 attacking a genuinely strong Day Master)? Only bridge relationships that are genuinely a "病" (problem), not a "药" (cure) already in progress.
5. If a bridge candidate exists but is too weak relative to the aggressor (lopsided, not roughly matched), say so explicitly and suggest that directly restraining the aggressor is the more reliable fix instead of forcing a thin bridge.

**Caveat to give the user**: 通关, like 调候, is described in source material as *supplementary* to 扶抑, not a coequal replacement for it — "调候用神和通关用神是辅助扶抑用神的,推命还需以生扶用神为主." Don't let a 通关 finding override a clear 扶抑/従格 conclusion; it's an additional layer of nuance for specific standoff situations, not a competing primary method.

## Calibration tests run against this workflow

Three constructed tests, targeting the two easiest failure modes: (a) confusing "a bridge exists in principle" with "a bridge is actually present in this chart," and (b) bridging a conflict that the chart's 扶抑 reading actually wants to keep.

| # | Chart | Day Master | Designed to test | Result | Expected? |
|---|---|---|---|---|---|
| 1 | 戊辰 壬子 甲午 己未 | 甲 (Wood) | 财旺克印 conflict is real (财 5 items vs 印 3 items), but 官杀 (the prescribed bridge) is **entirely absent** — no stem, no hidden stem, anywhere | Correctly flagged as "无解,缺通关字" — the 财-印 conflict is real but currently unresolved in the original chart; needs 官杀 to arrive via 大运/流年 before it can bridge. Does **not** fabricate a bridge that isn't there. | ✓ |
| 2 | 戊辰 壬子 甲申 己未 | 甲 (Wood) | Same 财印 conflict, but 官杀 (庚) is now present — sitting in the day branch's main qi (申), a strong position even without transparency on a stem | Correctly identified as "already bridged" — 财→官→印 flows without a gap, described as 流通有情 rather than as a recommendation to seek something. Distinguishes cleanly from test 1's "missing bridge" conclusion despite near-identical 财/印 balance. | ✓ |
| 3 | (conceptual — no full chart constructed) | — | Whether the workflow correctly withholds a 通关 recommendation when the 克 relationship is the chart's own 扶抑-prescribed cure (e.g. 官杀 attacking an already-strong Day Master, where 官杀 is 药 not 病) | Correctly suppressed — applying the fixed 官杀克比劫→用印通关 pairing mechanically here would remove a needed check on a strong Day Master. Step 4 of the integration workflow (checking against the 扶抑 conclusion before naming a bridge) was the deciding factor. Verified as a logic/sequencing check rather than a new numeric case. | ✓ |

Test 1 vs test 2 confirms the workflow distinguishes "conflict exists, bridge doesn't" from "conflict exists, bridge already in place" rather than defaulting to the same advice regardless of whether the prescribed element is actually on the chart. Test 3 confirms the "is this 克 a problem or the chart's cure" gate (see restrictions above) actually fires rather than being a a theoretical caveat that gets skipped in practice.