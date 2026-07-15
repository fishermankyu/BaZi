# 大运流年 (Major Luck Cycles & Annual Fortune) — Adding the Time Axis

Everything so far (`gejv.md` 格局, `strength_formula.md` 扶抑, `congge.md` 従格, `diaohou.md` 调候, `tongguan.md` 通关, synthesized in `zonghecaijue.md`) describes the **static original chart (原局)** — what kind of structure this person was born with. 大运流年 adds the missing axis: **time**. 大运 (10-year Major Luck pillars) and 流年 (single-year Annual pillars) are read as temporary extra pillars layered on top of the original four, shifting the balance for that period.

**Sequencing**: run this module only after the full `zonghecaijue.md` synthesis is done — 大运/流年 are evaluated *against* that already-established 喜用神/忌神 conclusion, not derived independently. Don't re-run 扶抑/従格/格局 logic from scratch for each 大运/流年; check whether the incoming pillar's Ten God matches what synthesis already flagged as favorable or unfavorable.

## 1. 排大运 (calculating the Major Luck pillars)

**Step 1 — 顺排 or 逆排 (direction)**: determined by year stem's yin/yang crossed with gender.
- 阳年 (year stem 甲丙戊庚壬) + male, or 阴年 (乙丁己辛癸) + female → **顺排** (forward through the 60-cycle)
- 阴年 + male, or 阳年 + female → **逆排** (backward through the 60-cycle)

**Step 2 — the pillar sequence**: start from the **month pillar**, not the day or year pillar. 顺排: take the *next* ganzhi in 60-cycle order after the month pillar as the first 大运, then keep advancing. 逆排: take the *previous* ganzhi as the first 大运, then keep retreating. Each 大运 pillar governs **10 years**.

**Step 3 — 起运年龄 (age at which the first 大运 begins)**: count the days from the birth date/time to the nearest **节** (one of the twelve 节 solar terms — 立春/惊蛰/清明/立夏/芒种/小暑/立秋/白露/寒露/立冬/大雪/小寒; not the twelve 气 in between). 顺排 counts forward to the *next* 节; 逆排 counts backward to the *previous* 节. Convert the day-count to an age using: **3 days = 1 year, 1 day = 4 months, 1 时辰 (2-hour block) ≈ 10 days ≈ 4 more days' worth (roughly 1.3 months)**. Round to the nearest reasonable unit (schools differ on rounding fine remainders — flag this as a minor precision caveat, not a hard rule).

**Caveat to give the user**: 起运年龄 calculation depends on the exact solar-term timing for that specific year (which shifts by up to a day or two annually) and on precise birth time — if the birth time is uncertain or only approximate, say the 起运 age is approximate too, don't state it with false precision.

## 2. 排流年 (Annual pillars)

Far simpler: 流年 is just that calendar year's own ganzhi — the same computation used for anyone's **year pillar** (see `stems_branches.md`'s 12-month/60-cycle logic), applied to whichever year is being asked about. It doesn't depend on gender, 阴阳年, or direction — everyone's 流年 for a given year is the same ganzhi, applied differently only through each person's own chart.

## 3. Layered priority: 命局 > 大运 > 流年

Classical framing: **命局断应事,年运断应期** — the original chart tells you *what kind* of thing tends to happen (which life domain, via which Ten God); 大运 and 流年 tell you *when*. Nest the read like this:
- **命局 (static)**: the underlying structure — what `zonghecaijue.md` already concluded.
- **大运 (10-year)**: the "internal factor" / broad direction for that decade — is this decade's incoming pillar reinforcing the chart's 喜用神 or its 忌神? This sets the *decade's* overall tone.
- **流年 (1-year)**: the "external trigger" — within that decade, individual years spike or dip further depending on how that specific year's pillar interacts with both 命局 and the current 大运.

A rough combination table: 大运吉+流年吉 → strongest positive year; 大运吉+流年平 → still positive, muted; 大运凶+流年吉 → mixed, net mildly positive but friction present; 大运凶+流年凶 → weakest year in that stretch, particularly worth flagging. Don't treat any single year in isolation from its decade's 大运 backdrop.

## 4. How to read a 大运 or 流年 pillar against the chart

1. **Ten God check**: what Ten God does the incoming pillar's stem (and separately, its branch's main qi) represent relative to the Day Master? Compare against `zonghecaijue.md`'s 喜用神/忌神 conclusion — landing on a 喜用神 Ten God is the baseline "favorable," landing on 忌神 is baseline "unfavorable." This is the default read before checking any of the sharper signals below.
2. **天克地冲 (stem-clash + branch-clash together)**: if the incoming pillar's stem controls (克) a chart pillar's stem *and* its branch is in 六冲 with that same chart pillar's branch simultaneously, this is one of the most heavily-weighted disruption signals — "该运/年必多凶险" in source material. **But the direction of "bad" depends entirely on what's being clashed**: if the clashed chart pillar/element is a 忌神, the clash can be net positive (removing something unwanted); if it's a 喜用神, the clash is genuinely concerning. Never call 天克地冲 automatically bad without checking which side it's hitting.
3. **冲提纲 (clashing the month branch specifically)**: since the month branch is the chart's structural hinge (提纲), a clash here signals larger life disruption/change (job change, relocation) more than other pillars — "变动大不等于变坏," frame as significant change, not automatically misfortune.
4. **Which pillar is clashed maps to which life domain**: 冲年柱→年长者/早年环境; 冲月柱→父母/工作环境; 冲日柱→自身/婚姻; 冲时柱→子女/晚年. Use this to say *what area* a disruptive year is more likely to touch, not just that "something happens."
5. **岁运并临**: when the current 流年's ganzhi is identical to the current 大运's ganzhi, source material treats this as an amplifier, not a separate verdict — "吉凶加倍," intensifying whatever that pillar's baseline read already was (favorable pillar → especially good year; unfavorable → especially rough year). Frame it as "this year hits harder either way," not as an independent omen.
6. **合/会with the chart**: a 大运/流年 pillar combining (六合/三合/半合) with chart branches can shift an existing chart relationship — e.g. resolve a standoff, or pull an element toward transformation — evaluate using the same modifier logic as `xingchonghehui.md`, just with the incoming pillar treated as a temporary extra branch in the mix.

## Workflow summary

1. Determine 顺/逆 and list out the 大运 sequence (§1), noting 起运年龄 with its precision caveat.
2. For the specific year(s) in question, compute that year's 流年 pillar (§2).
3. Identify which 大运 that year falls within.
4. Check both the 大运 and 流年 pillars' Ten God against `zonghecaijue.md`'s 喜用神/忌神 conclusion (§4.1), then layer on 天克地冲/冲提纲/岁运并临/合 checks (§4.2–4.6) as applicable.
5. Synthesize per §3's nesting: state the decade's overall tone from 大运, then the specific year's spike/dip from 流年, and which life domain (if a clash is involved) it's more likely to touch.
6. Standard caveat: this is a traditional analytical framework describing tendencies, not a deterministic prediction — say so, especially when discussing specific years, since this is the module most likely to be heard as literal fortune-telling if not framed carefully.