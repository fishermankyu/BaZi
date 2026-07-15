---
name: bazi-analysis
description: >
  Use this skill whenever the user gives a BaZi (四柱/八字, Four Pillars of Destiny) chart —
  four stem-branch pairs like "丁丑 壬子 甲戌 辛未" — or asks to analyze one, or asks about any
  traditional BaZi concept. Covers: identifying the Day Master and Five Elements/Yin-Yang;
  hidden stems (藏干); Ten Gods (十神); regular pattern / structure (格局, 八正格 or 建禄/月刃);
  branch relationships (刑沖合會害破); Day Master strength/weakness (身强身弱) via a calibrated
  weighted formula; following structures for extreme charts (従格, incl. 従财/従杀/従儿/従旺/従強/
  専旺); seasonal adjustment (调候); bridging conflicting Ten Gods (通关); synthesizing all of the
  above into one 喜用神/忌神 verdict; Major Luck Cycles and Annual Fortune (大运流年); and common
  Special Stars and the Void (神煞, 空亡 — 桃花/驿马/华盖/魁罡/天乙贵人/etc.). Trigger this for
  requests like "算一下这个八字", "十神怎么算", "身强身弱", "喜用神", "什么格局", "从格吗",
  "调候用神", "大运流年怎么看", "有没有桃花", "空亡在哪", or any BaZi/Four Pillars chart or
  concept the user raises, even without using the word "skill." This is an intellectual/analytical
  framework, not fortune-telling advice — always frame conclusions as traditional-system outputs,
  not deterministic predictions.
---

# BaZi (Four Pillars) Analysis

A structured method for reading a four-pillar (八字) chart: from raw stems/branches through hidden stems, Ten Gods, and a quantified strength score. This mirrors a from-scratch tutoring conversation, so keep the same teach-by-derivation tone unless the user just wants a fast answer.

## Triage first — how much depth does this request actually need?

Before running the workflow, judge whether the person wants a quick answer or a full walkthrough — this is a **depth** decision, separate from **topic** (see below). Signals for **quick**: a narrow question ("我是身强还是身弱", "这个月对我好不好"), no request to see the derivation, casual phrasing. Signals for **full**: they paste a chart cold and ask to "算一下"/analyze it, ask to be walked through the logic, or are visibly in learning mode (see Tone notes below).

- **Quick answer**: give the specific thing asked (e.g. just the 身强/身弱 classification, or just 喜用神, or just the 格局 name) in a sentence or two. Run 格局/従格/调候/通关 checks silently in the background only insofar as they change the headline answer (e.g. don't say "身弱" if it's actually a confirmed 従格 that inverts the reading) — but don't narrate the check itself or walk through gejv.md/congge.md/diaohou.md/tongguan.md's reasoning unless asked. One line answer, not a report.
- **Full walkthrough**: run steps 1–11 below in full, showing derivation at each stage per the Tone notes.
- If genuinely ambiguous, default toward the shorter answer and offer to go deeper — don't pre-emptively dump the full derivation on someone who didn't ask for it.

**Topic** is independent of depth: steps 12 (大运流年) and 13 (神煞/空亡) only run when the person actually asks about timing/a specific year, or about a named 神煞/空亡 — regardless of whether the rest of the answer is quick or a full walkthrough. Don't run them just because it's a "full walkthrough" of the static chart, and don't skip them in a "quick answer" if that's specifically what was asked.

## Workflow (for full walkthroughs)

1. **Parse the chart** — four pillars, each a Stem+Branch pair: Year, Month, Day, Hour. The Day Stem (日干) is the **Day Master** — everything else is read relative to it.
2. **List Five Elements + Yin-Yang** for every stem and every branch (see `references/stems_branches.md`).
3. **Expand hidden stems (藏干)** for each branch — main qi / middle qi / residual qi (see `references/hidden_stems.md`).
4. **Compute Ten Gods (十神)** for every stem and every hidden stem relative to the Day Master (see `references/ten_gods.md`).
5. **Determine 格局 (regular pattern)** — see `references/gejv.md`. Look up whether the month branch's main qi (or, failing that, secondary qi) transparents on a heavenly stem; the corresponding Ten God is the chart's structural pattern (one of the eight 正格, or 建禄/月刃 if the month branch's qi is 比劫). This identifies *what kind* of chart it is, distinct from the strength scoring that follows — determine it now, since later steps build on top of it.
6. **Check branch relationships (刑沖合會害破)** across all pillar pairs — combinations, clashes, punishments, harms, breaks (see `references/xingchonghehui.md`). Apply the relationship modifiers there to adjust branch scores before finalizing strength.
7. **Score Day Master strength** using the weighted formula (see `references/strength_formula.md`), folding in the branch-relationship modifiers from step 6, then classify 身强/身弱 and note likely 喜用神 (favorable elements) at a high level if asked.
8. **If Score% falls past the extreme thresholds defined in `strength_formula.md` §5 (currently 75% 极强 / 25% 极弱)**, check whether a 従格 (following structure) applies before finalizing the strength reading — see `references/congge.md`. A 従格, if confirmed, **replaces the 格局 from step 5 entirely** — a chart is read as either an ordinary 格局 (with 扶抑/调候/通关 as needed) or as a 従格, not both at once; say so explicitly rather than reporting them as compatible parallel conclusions. Most extreme charts will still fail one of 従格's structural gates (purity, root-clearing, 得用) and should be read as ordinary 极强/极弱 within the step-5 格局 — don't default to 従格 just because the percentage is extreme.
9. **Check 调候 (seasonal adjustment)** — see `references/diaohou.md`. This is independent of 身强身弱/従格: look up the Day Master + month branch in the 十干喜用提要 table, and check whether the called-for stem is present and functioning in the chart. If the seasonal need (especially in 亥子丑巳午未) is unmet, flag it — 调候 takes practical priority ("先解冻，后论生克") over 扶抑 when the two genuinely conflict. If already met by something in the chart, just note it's satisfied.
10. **Check 通关 (bridging)** — see `references/tongguan.md`. Only relevant when two Ten-God categories are in direct, roughly-matched 克 conflict. Verify the bridging element is actually present and rooted (don't recommend a bridge that isn't on the chart — say so if missing instead), and check the conflict isn't actually the chart's own 扶抑-prescribed cure before suggesting a bridge (e.g. don't bridge away 官杀 attacking a Day Master that `strength_formula.md` already flagged as wanting exactly that). 通关 is supplementary to 扶抑, not a replacement for it.
11. **Synthesize into one verdict** — see `references/zonghecaijue.md`. Don't report steps 5/7/8/9/10 as five separate paragraphs; merge them via the arbitration hierarchy there (従格 overrides all > 格局's own 喜忌 as default frame > 调候 overrides only on genuine unmet extreme-month need > 通关 narrowest/supplementary > 扶抑 Score% as continuous cross-check, not a sixth vote) and close with the one-line-identity + 喜用神 + 忌神 (+ optional tension note) template given there.
12. **If asked about a specific age/year, or about 运势/大运/流年** — see `references/dayunliunian.md`. Determine 顺/逆 排 (year stem yin-yang × gender), list the 大运 sequence from the month pillar with 起运年龄, compute the relevant 流年 pillar, and check both against step 11's 喜用神/忌神 conclusion — layering in 天克地冲/冲提纲/岁运并临/合 as applicable. This is a distinct, opt-in step: don't run it unless the person asked about timing, a specific year, or "运势" — it doesn't apply to a pure structural reading of the original chart.
13. **If asked about a specific 神煞 (桃花/驿马/华盖/etc.) or about 空亡** — see `references/shenshakongwang.md`. Look up the relevant marker(s) using the fixed lookup rules there, and read the result relative to whether it lands on a 喜用神 or 忌神 per step 11's conclusion. Also opt-in — supplementary color, not part of the core structural read, and never overrides steps 5–11's conclusions.
14. Only go into interpretive meaning (career, relationships, health) if the user asks — default to the structural mechanics first.

## Tone and pacing notes (from the source conversation)

- The user is learning this system interactively — prefers being **quizzed and correcting their own attempts** over just being told answers. If they attempt a calculation, check it step by step and correct only the specific error, don't just hand over the final table.
- Explain *why*, not just *what* — e.g. why 亥's main qi is 壬 (yang) despite 亥 itself being a yin branch (two separate systems: the branch's own yin-yang label vs. its hidden stem's yin-yang, from 十二长生 theory).
- Keep phrasing in Chinese for terminology (天干地支, 十神, 藏干, etc.) since the user thinks in these terms; explanations can mix Chinese terms with plain-language analogies (e.g. "根 vs 苗", "扛麻袋上楼" for 财 vs 食伤).
- Always caveat: different schools (流派) give slightly different numeric weights — present the formula as *a* reasonable convention, not *the* definitive one. Never claim deterministic/fortune-telling authority; frame as a traditional analytical framework the user is engaging with intellectually.

## Quick reference tables

Full tables are in `references/`. Load only what's needed:
- `references/stems_branches.md` — 10 stems + 12 branches, Five Element + Yin-Yang for each, plus the 12-month calendar mapping.
- `references/hidden_stems.md` — full 藏干 table (main/middle/residual per branch) with the seasonal-transition logic (四正/四长生/四库 categories) and the twelve-stage (十二长生) long-life cycle table used to explain exceptions like 亥/午.
- `references/ten_gods.md` — the Ten Gods derivation rule (生克关系 + 阴阳同异) and full 10x10 lookup table for any Day Master.
- `references/gejv.md` — 正格 (regular pattern / 八格) rules: the 取格 priority ladder (月支本气/次气透干, fallback to strongest rooted stem), why 比劫 can't be a 格 (建禄/月刃 instead), 成格/败格 conditions for all eight 正格, and calibration tests.
- `references/xingchonghehui.md` — 六合/三合/三會/六沖/三刑/自刑/六害/六破 definitions, plus the modifier coefficients (discount for damage-type relationships, discount + bonus for combination-type relationships) that fold into the strength formula, with a worked example.
- `references/strength_formula.md` — the weighted scoring formula (base score by stem/main/middle/residual qi × positional weight × seasonal 旺相休囚死 multiplier), with normalization to Score%, calibrated classification thresholds, and worked examples.
- `references/congge.md` — 従格 (following structure) rules: 従财/従杀/従儿 (従弱系) and 従旺/従強/専旺 (従強系), their成立 conditions, favor/avoid lists, and the decision workflow for when Score% is past the extreme thresholds (canonical values live in `strength_formula.md` §5).
- `references/diaohou.md` — 调候 (seasonal adjustment) rules: the full 十干喜用提要 table (10 Day Masters × 12 months, primary/secondary favorable stems per combination), plus the priority logic for when 调候 conflicts with 扶抑/従格 ("先解冻，后论生克").
- `references/tongguan.md` — 通关 (bridging) rules: the general X克Y→bridge-element-Z rule, the four Ten-God fixed pairings (财印/官比劫/伤官见官/比劫夺财), strength-matching and "don't bridge away a needed cure" restrictions, and calibration tests.
- `references/zonghecaijue.md` — synthesis rules: the arbitration hierarchy for merging 格局/扶抑/従格/调候/通关 into one verdict, plus the output template (one-line identity + 喜用神 + 忌神 + optional tension note) for both quick and full-walkthrough answers.
- `references/dayunliunian.md` — 大运流年 (Major Luck Cycles & Annual Fortune) rules: 排大运 calculation (顺逆排, 起运年龄), 排流年, the 命局>大运>流年 nesting priority, and how to read a 大运/流年 pillar against the chart (Ten God check, 天克地冲, 冲提纲, palace-to-life-domain mapping, 岁运并临, combinations). Opt-in — only relevant when asked about timing/a specific year.
- `references/shenshakongwang.md` — 神煞与空亡 (Special Stars & Void) rules: fixed lookup tables for 9 common 神煞 (天乙贵人/文昌/桃花/驿马/华盖/将星/魁罡/羊刃/天德月德), the 六旬空亡 lookup and its modifiers (冲/合/填实), and how both read relative to 喜用神/忌神. Opt-in, supplementary color only.

## Example interaction shape

User pastes: `己卯 丙寅 庚午 癸未`
→ Identify Day Master (庚, Yang Metal), walk through Five Elements/Yin-Yang per pillar, expand hidden stems per branch, derive Ten Gods per stem/hidden-stem, then (if asked) run the strength formula and classify 身强/身弱, noting the month branch (月令) is the dominant weighting factor.

## Maintenance: cross-file dependencies

These references cite numbers or conclusions defined canonically in *other* files, rather than owning that value themselves. **If you edit a canonical value, check every listed consumer** — none of this is auto-validated, since skills are plain markdown with no build step.

| Canonical value | Owned by | Consumed by (must stay in sync) |
|---|---|---|
| 极强/极弱 thresholds (currently 75%/25%) | `strength_formula.md` §5 | `congge.md` (trigger condition, 3 mentions), `gejv.md` (従格 override note), `SKILL.md` step 8 |
| Base/positional/seasonal score tables | `strength_formula.md` §1–3 | `xingchonghehui.md` (modifiers apply on top of these scores) |
| 従格 favor/avoid lists per subtype | `congge.md` | `zonghecaijue.md` (arbitration hierarchy step 1) |
| 格局 喜/忌 table per pattern | `gejv.md` | `zonghecaijue.md` (arbitration hierarchy step 2), `tongguan.md` (checks before naming a bridge) |
| 调候's "先解冻，后论生克" priority rule | `diaohou.md` | `zonghecaijue.md` (arbitration hierarchy step 3), `SKILL.md` step 9 |
| "Don't bridge away a needed cure" restriction | `tongguan.md` | `zonghecaijue.md` (arbitration hierarchy step 4) |
| Final 喜用神/忌神 synthesis (per chart) | `zonghecaijue.md` (output of the full arbitration hierarchy) | `dayunliunian.md` (step 12, checks 大运/流年 Ten Gods against this), `shenshakongwang.md` (step 13, reads 神煞/空亡 relative to this) |

**When adding a new reference file**: if it restates a number or rule owned elsewhere, phrase it as a pointer ("see X §Y") rather than duplicating the literal value, and add a row to this table. This keeps the number of places any single fact needs updating close to one.