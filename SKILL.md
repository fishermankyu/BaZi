---
name: bazi-analysis
description: >
  Use this skill whenever the user gives a BaZi (四柱/八字, Four Pillars of Destiny) chart —
  four stem-branch pairs like "丁丑 壬子 甲戌 辛未" — or asks to analyze one. Covers identifying
  the Day Master, listing Heavenly Stems/Earthly Branches with Yin-Yang and Five Elements,
  finding hidden stems (藏干, i.e. main/middle/residual qi) for each branch, computing the
  Ten Gods (十神) relative to the Day Master, and scoring day-master strength/weakness
  (身强身弱) using a weighted formula that accounts for stem vs. branch, hidden-qi depth,
  position, and seasonal (month-branch) power. Trigger this for requests like "算一下这个八字",
  "十神怎么算", "身强身弱", "喜用神", or any BaZi/Four Pillars chart the user pastes in, even
  without using the word "skill." This is an intellectual/analytical framework, not
  fortune-telling advice — always frame conclusions as traditional-system outputs, not
  deterministic predictions.
---

# BaZi (Four Pillars) Analysis

A structured method for reading a four-pillar (八字) chart: from raw stems/branches through hidden stems, Ten Gods, and a quantified strength score. This mirrors a from-scratch tutoring conversation, so keep the same teach-by-derivation tone unless the user just wants a fast answer.

## Workflow

1. **Parse the chart** — four pillars, each a Stem+Branch pair: Year, Month, Day, Hour. The Day Stem (日干) is the **Day Master** — everything else is read relative to it.
2. **List Five Elements + Yin-Yang** for every stem and every branch (see `references/stems_branches.md`).
3. **Expand hidden stems (藏干)** for each branch — main qi / middle qi / residual qi (see `references/hidden_stems.md`).
4. **Compute Ten Gods (十神)** for every stem and every hidden stem relative to the Day Master (see `references/ten_gods.md`).
5. **Check branch relationships (刑沖合會害破)** across all pillar pairs — combinations, clashes, punishments, harms, breaks (see `references/xingchonghehui.md`). Apply the relationship modifiers there to adjust branch scores before finalizing strength.
6. **Score Day Master strength** using the weighted formula (see `references/strength_formula.md`), folding in the branch-relationship modifiers from step 5, then classify 身强/身弱 and note likely 喜用神 (favorable elements) at a high level if asked.
7. **If Score% falls past 75% (极强) or below 25% (极弱)**, check whether a 従格 (following structure) applies before finalizing the strength reading — see `references/congge.md`. A 従格, if confirmed, inverts or replaces the standard 喜用神 heuristic for that chart, so this check must happen before giving 喜用神 guidance on an extreme chart. Most extreme charts will still fail one of 従格's structural gates (purity, root-clearing, 得用) and should be read as ordinary 极强/极弱 — don't default to 従格 just because the percentage is extreme.
8. **Check 调候 (seasonal adjustment)** — see `references/diaohou.md`. This is independent of 身强身弱/従格: look up the Day Master + month branch in the 十干喜用提要 table, and check whether the called-for stem is present and functioning in the chart. If the seasonal need (especially in 亥子丑巳午未) is unmet, flag it — 调候 takes practical priority ("先解冻，后论生克") over 扶抑 when the two genuinely conflict. If already met by something in the chart, just note it's satisfied.
9. **Check 通关 (bridging)** — see `references/tongguan.md`. Only relevant when two Ten-God categories are in direct, roughly-matched 克 conflict. Verify the bridging element is actually present and rooted (don't recommend a bridge that isn't on the chart — say so if missing instead), and check the conflict isn't actually the chart's own 扶抑-prescribed cure before suggesting a bridge (e.g. don't bridge away 官杀 attacking a Day Master that `strength_formula.md` already flagged as wanting exactly that). 通关 is supplementary to 扶抑, not a replacement for it.
10. Only go into interpretive meaning (career, relationships, health) if the user asks — default to the structural mechanics first.

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
- `references/xingchonghehui.md` — 六合/三合/三會/六沖/三刑/自刑/六害/六破 definitions, plus the modifier coefficients (discount for damage-type relationships, discount + bonus for combination-type relationships) that fold into the strength formula, with a worked example.
- `references/strength_formula.md` — the weighted scoring formula (base score by stem/main/middle/residual qi × positional weight × seasonal 旺相休囚死 multiplier), with normalization to Score%, calibrated classification thresholds, and worked examples.
- `references/congge.md` — 従格 (following structure) rules: 従财/従杀/従儿 (従弱系) and 従旺/従強/専旺 (従強系), their成立 conditions, favor/avoid lists, and the decision workflow for when Score% is past 75%/25%.
- `references/diaohou.md` — 调候 (seasonal adjustment) rules: the full 十干喜用提要 table (10 Day Masters × 12 months, primary/secondary favorable stems per combination), plus the priority logic for when 调候 conflicts with 扶抑/従格 ("先解冻，后论生克").
- `references/tongguan.md` — 通关 (bridging) rules: the general X克Y→bridge-element-Z rule, the four Ten-God fixed pairings (财印/官比劫/伤官见官/比劫夺财), strength-matching and "don't bridge away a needed cure" restrictions, and calibration tests.

## Example interaction shape

User pastes: `己卯 丙寅 庚午 癸未`
→ Identify Day Master (庚, Yang Metal), walk through Five Elements/Yin-Yang per pillar, expand hidden stems per branch, derive Ten Gods per stem/hidden-stem, then (if asked) run the strength formula and classify 身强/身弱, noting the month branch (月令) is the dominant weighting factor.