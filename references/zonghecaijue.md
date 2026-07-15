# 综合裁决 (Synthesis) — Merging 格局/扶抑/従格/调候/通关 into One Verdict

By the time all five layers have been checked (格局 `gejv.md`, 扶抑 `strength_formula.md`, 従格 `congge.md`, 调候 `diaohou.md`, 通关 `tongguan.md`), don't report five separate paragraphs and leave the person to reconcile them. This file is the arbitration hierarchy and output template for turning five layers into one coherent 喜用神 conclusion.

## The arbitration hierarchy

**Not a flat vote across five equal layers.** Each layer has a different scope, and the scopes nest:

```
従格 (if confirmed)  →  overrides everything below entirely
        ↓ (if not confirmed)
格局's own 喜/忌 table  →  primary frame (already strength-sensitive by design)
        ↓
调候  →  overrides 格局/扶抑 ONLY when a genuine unmet need exists in an extreme month (亥子丑巳午未)
        ↓
通关  →  narrowest, supplementary; never overrides a cure 格局/扶抑 actually wants kept
        ↓
扶抑 Score%  →  runs throughout as a continuous cross-check, not a separate vote
```

### 1. 従格 first — if confirmed, it replaces everything

If `congge.md`'s workflow confirms a 従格, its own favor/avoid list becomes the *entire* basis for 喜用神. The step-5 格局 and the ordinary 扶抑 印比/官杀财食伤 heuristic are both set aside — don't average a 従财格's "喜财食伤" with what the abandoned ordinary 正格 would have wanted. 调候 and 通关 still get checked, but filtered through the 従格's own logic: a 通关 bridge or 调候 stem that would undermine the 従格's direction (e.g. reintroducing 比劫 into a 従财格) should be flagged as a conflict with the 従格 itself, not applied blindly.

### 2. 格局's own 喜/忌 — the default frame, not a competitor to 扶抑

If no 従格 applies, `gejv.md`'s per-pattern 喜/忌 table (e.g. 食神格喜身强、财星,忌枭神夺食、比劫过重) is the starting point — notice these conditions already reference 身强/身弱 internally. This means most of the time, **格局 and 扶抑 aren't actually in tension** — the 格局 system was built with strength-sensitivity baked in, not as a separate axis to arbitrate against.

**When they do appear to conflict** (格局's 喜 list wants something the raw Score% says the Day Master can't afford — e.g. a 食神格 wanting more 财 to flow toward, but Score% shows the Day Master already thin on support): treat this as a sign the 格局 may be **败格 / not cleanly formed** rather than a 50-50 tossup to arbitrate. Lean toward protecting the Day Master (the 扶抑 direction) in this case — an unsustainable 格局 isn't "clean" per its own 清浊成败 conditions (`gejv.md` §3), so raw Score% acts as the tie-breaker specifically for this scenario, not as a routine override.

### 3. 调候 — overrides, but only for genuine unmet extreme-month needs

Per `diaohou.md`: if the month is genuinely one of the six urgent ones (亥子丑巳午未, plus early 寅) and the classically-called-for stem is entirely absent from the chart, 调候 takes practical priority over whatever 格局/扶抑 concluded — "先解冻，后论生克." If the seasonal need is already satisfied by something already in the chart, there's no override to apply — just note it's met and move on. Don't invent tension where the need is already covered.

### 4. 通关 — narrowest scope, never undoes a needed cure

Per `tongguan.md`: only relevant when two Ten-God groups are in a genuine, roughly-matched head-on 克. Before naming a bridge, check it against **both** 格局's 喜/忌 (`gejv.md`) and 扶抑's conclusion (`strength_formula.md`) — if the "conflict" is actually something the chart wants kept (e.g. 七杀格's own 食神制杀 relationship, or 官杀 attacking a genuinely strong Day Master that 扶抑 already flagged as wanting exactly that), don't bridge it away. 通关 fixes standoffs the other layers didn't already resolve — it doesn't get a vote on relationships those layers have already blessed.

### 扶抑 Score% — the continuous cross-check, not a fifth vote

Score% doesn't get its own turn in the hierarchy above — it's already threaded through 従格's trigger condition (step 1), 格局's own 喜忌 (step 2), and the tie-breaker role when 格局 and raw strength disagree (step 2's caveat). Don't additionally present it as a sixth, independent opinion at the end; it's infrastructure the other layers already consumed.

## Output template

**For a full walkthrough** (per SKILL.md's Triage step), close with a synthesis section shaped like this — adapt wording, don't paste this verbatim:

1. **One-line identity**: [Day Master] + [格局 or 従格 name] + [身强/身弱 or 従格 direction] — e.g. "壬水七杀格,身弱(26.5%)".
2. **喜用神** (2–3 items max, ranked): state each with its source layer in one clause, not a separate paragraph per layer — e.g. "庚金(印,扶抑与调候皆需要)、丙火(调候,原局全无,需运补)".
3. **忌神** (1–2 items): what actively works against the chart, per whichever layer(s) flagged it.
4. **Notable tension, if any** (optional, one sentence): only include if step 2/3/4 of the hierarchy above produced a real override worth flagging (e.g. "甲木在调候上有用,但对日主是食伤耗身方向,两者方向不完全一致,不算硬冲突"). Skip this line entirely if the layers all agreed — don't manufacture tension for completeness.

**For a quick answer** (per Triage): just the one-line identity plus the top 1–2 喜用神 items, no source attribution, no tension caveat unless directly asked.

## Worked example (using the chart already run earlier: 己卯 戊辰 壬子 己酉)

1. **一句话**: 壬水七杀格,身弱(26.5%,接近但未跨过极弱门槛)
2. **喜用神**: 庚辛金(印,扶抑要印比,调候也要庚金发水源,两层重叠,是最推荐的一项)、壬癸水(比劫,扶抑方向)
3. **忌神**: 戊己土(官杀,已经是压倒性耗身主力,不宜再加)
4. **一点张力**: 调候还想要甲木疏土,但甲木对壬水是食伤耗身,跟身弱要补不要耗的方向不完全一致——不过辰月不是调候最紧急的六个月之一,这条张力不算硬冲突,可以提一句但不必强求解决。

This mirrors the conclusion reached earlier in conversation — the arbitration hierarchy above is what makes that same conclusion reproducible by rule rather than by ad hoc reasoning each time.