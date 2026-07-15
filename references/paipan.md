# 排盘 (Computing the Four Pillars from a Birth Date/Time)

Use this file whenever the person gives a **raw birth date/time** (solar/Gregorian calendar) instead of an already-computed chart, and asks for the 八字 to be worked out. If they paste four ready-made stem-branch pairs, skip straight to `SKILL.md`'s workflow step 1 — this file is only for the conversion step.

## Primary method: use a library, not manual arithmetic

**Don't hand-calculate the pillars from memory as the default method.** Manual calculation (memorized epoch anchors, approximate 节气 dates, counting days across decades by hand) is genuinely error-prone — there's real risk of an off-by-one on the day-count, or an approximate 节气 date being wrong by the day or two that actually matters for someone born near a boundary. A proper library computes 节气 astronomically (to the exact date and time, using actual solar-position calculation, not a precomputed lookup table of dates) and eliminates manual day-counting entirely.

**Library choice matters — these aren't interchangeable, and none of them are "brute-force enumeration" for the core calculation, but they differ in how much unrelated baggage they carry:**

- **`sxtwl` (primary recommendation)**: computes everything from Julian Day / J2000-epoch solar-position astronomy — genuinely algorithmic, not a lookup table of pre-computed dates. Small, self-contained (~4MB, almost entirely the compiled astronomical calculation itself), no unrelated bundled data. Use this as the default.
- **`lunar-python`**: also astronomically-driven for the core 排盘 calculation, and has the most convenient one-line API (`getEightChar()` returns all four pillars directly). But the package also bundles a large, unrelated embedded dataset for traditional 老黄历 宜忌 (daily auspicious/inauspicious activity lookups) that has nothing to do with computing pillars — inflates the package without adding relevant capability. Fine to use for its convenient API, just be aware of what else it's carrying.
- **`cnlunar`**: smallest footprint (~260KB), also algorithmic. Good as a third independent cross-check.

```bash
pip install sxtwl --break-system-packages
```

```python
import sxtwl
Gan = ["甲","乙","丙","丁","戊","己","庚","辛","壬","癸"]
Zhi = ["子","丑","寅","卯","辰","巳","午","未","申","酉","戌","亥"]
day = sxtwl.fromSolar(YEAR, MONTH, DAY)
year_gz = Gan[day.getYearGZ().tg] + Zhi[day.getYearGZ().dz]
month_gz = Gan[day.getMonthGZ().tg] + Zhi[day.getMonthGZ().dz]
day_gz = Gan[day.getDayGZ().tg] + Zhi[day.getDayGZ().dz]
hour_gz_obj = day.getHourGZ(HOUR)  # HOUR = the true-solar-time-corrected hour, see below
hour_gz = Gan[hour_gz_obj.tg] + Zhi[hour_gz_obj.dz]
```

**Cross-validate** by also running `lunar-python` and/or `cnlunar` (same installer pattern) and confirming they agree before reporting the chart — these are independent implementations, so agreement across 2–3 of them is meaningful confirmation, not redundant effort. If they disagree, that's a signal to investigate rather than pick one arbitrarily (check the birth time is right at a 节气 or 时辰 boundary, where legitimate implementation differences in rounding can surface).

**True solar time still needs manual pre-processing**: these libraries convert *clock* time to ganzhi — they don't know the birth location, so they don't apply the longitude correction described in §4 below. If the birth location is known, apply that correction to the input time *before* passing it to the library, especially when the birth time is within ~15–20 minutes of a 时辰 boundary (2-hour block) where the correction could flip the hour branch.

**When to fall back to the manual method in §1–4 below**: if `bash_tool` isn't available in the current context, if the person wants to see the derivation (teaching mode, per `SKILL.md`'s Tone notes), or as a sanity check alongside the library output. The manual algorithm is also useful for explaining *why* a chart came out the way it did (e.g. "you're within 2 days of the 清明 boundary, here's why the month pillar is what it is") even when the library did the actual computation.

## Manual method (fallback / explanation of mechanics)

**Standing caveat for this section**: BaZi pillars are computed from true solar-calendar dates using precise 节气 (solar term) boundaries, which shift by up to a day or two from year to year — they are astronomically determined, not fixed calendar dates. The dates below are approximate; don't rely on them alone when precision matters (birth near a boundary) — use `web_search` to verify the exact date/time of the relevant 节 for that specific year, or better, use the library method above.

### §1 年柱 (Year Pillar)

The 60-cycle repeats on a known anchor: **1984 = 甲子 year**. For any year Y: `offset = (Y - 1984) mod 60` (use Python-style modulo that stays non-negative for years before 1984 too). Stem index = `offset mod 10`, Branch index = `offset mod 12`, read off:
- Stems (index 0–9): 甲乙丙丁戊己庚辛壬癸
- Branches (index 0–11): 子丑寅卯辰巳午未申酉戌亥

**Critical boundary rule**: the BaZi year does **not** start on Jan 1 or on Lunar New Year — it starts at **立春** (roughly Feb 3–5, varies by year). If the birth date falls before that year's 立春, use the *previous* year's stem-branch for the year pillar. Verify the exact 立春 date/time for the specific year via `web_search` if the birth date is in January or early-to-mid February.

### §2 月柱 (Month Pillar)

**Step 1 — find the month branch** via which pair of 节 (solar terms, not the 气 in between) the birth date falls between. The twelve 节 boundaries and their branches:

| 节 (approx. date) | Branch |
|---|---|
| 立春 (~Feb 4) → 惊蛰 | 寅 |
| 惊蛰 (~Mar 6) → 清明 | 卯 |
| 清明 (~Apr 5) → 立夏 | 辰 |
| 立夏 (~May 6) → 芒种 | 巳 |
| 芒种 (~Jun 6) → 小暑 | 午 |
| 小暑 (~Jul 7) → 立秋 | 未 |
| 立秋 (~Aug 8) → 白露 | 申 |
| 白露 (~Sep 8) → 寒露 | 酉 |
| 寒露 (~Oct 8) → 立冬 | 戌 |
| 立冬 (~Nov 7) → 大雪 | 亥 |
| 大雪 (~Dec 7) → 小寒 | 子 |
| 小寒 (~Jan 6) → 立春 | 丑 |

The approximate dates drift by about ±1 day year to year — if the birth date is within ~2 days of one of these boundaries, verify the exact 节 date/time for that specific year via `web_search` rather than assuming the approximate date holds.

**Step 2 — find the month stem** via 五虎遁 (determined by the *year* stem, then cycling forward from 寅):

| Year stem | 寅月 starts at | Then cycle forward: 卯, 辰, 巳, 午, 未, 申, 酉, 戌, 亥, 子, 丑 |
|---|---|---|
| 甲 or 己 | 丙寅 | 丁卯 戊辰 己巳 庚午 辛未 壬申 癸酉 甲戌 乙亥 丙子 丁丑 |
| 乙 or 庚 | 戊寅 | 己卯 庚辰 辛巳 壬午 癸未 甲申 乙酉 丙戌 丁亥 戊子 己丑 |
| 丙 or 辛 | 庚寅 | 辛卯 壬辰 癸巳 甲午 乙未 丙申 丁酉 戊戌 己亥 庚子 辛丑 |
| 丁 or 壬 | 壬寅 | 癸卯 甲辰 乙巳 丙午 丁未 戊申 己酉 庚戌 辛亥 壬子 癸丑 |
| 戊 or 癸 | 甲寅 | 乙卯 丙辰 丁巳 戊午 己未 庚申 辛酉 壬戌 癸亥 甲子 乙丑 |

Mnemonic: 甲己之年丙作首, 乙庚之年戊为头, 丙辛之年庚寅上, 丁壬壬寅顺水流, 戊癸甲寅好追求.

### §3 日柱 (Day Pillar)

This is the step most prone to drift/error if reconstructed from memory each time — **always compute it, don't guess**. Method: day-count from a known anchor date, mod 60.

**Reliable anchor**: **1949-10-01 = 甲子 day** (cross-validated against the also-commonly-cited **2000-01-01 = 戊午 day**; these two agree, which is a useful sanity check when computing by hand).

Procedure: count the exact number of days between the anchor and the birth date (careful with leap years — Feb 29 in any year divisible by 4, except century years not divisible by 400, though this exception is irrelevant for any birth date between 1900–2099). Take `days mod 60` to get an offset from 甲子 (offset 0). Stem index = `offset mod 10`, Branch index = `offset mod 12`, read off the same stem/branch lists as §1.

**When precision matters** (this calculation is easy to get off-by-one on with manual counting), cross-check by computing the offset two different ways (e.g. count forward from the anchor and also backward from a second known reference date) and confirm they agree before reporting the day pillar with confidence.

### §4 时柱 (Hour Pillar)

**Step 1 — adjust to true solar time**. China Standard Time is based on 120°E longitude. If the birth location's longitude is known, correct: `correction_minutes = (local_longitude - 120) × 4`. E.g. a location at 104°E is `(104-120)×4 = -64 minutes` — the true solar time is about 64 minutes *earlier* than the clock time. (This is the simplified longitude-only correction; the further refinement — the equation of time, ±~15 min depending on time of year — is a smaller effect some schools also apply, but the longitude correction is the one that matters most and shouldn't be skipped.) If the birth location is unknown or only a country/region is given, note the correction couldn't be applied precisely and flag the resulting hour-branch as a best estimate near boundaries.

**Step 2 — find the 时辰** (2-hour block) the corrected time falls into:

| 时辰 | Clock range |
|---|---|
| 子 | 23:00–01:00 |
| 丑 | 01:00–03:00 |
| 寅 | 03:00–05:00 |
| 卯 | 05:00–07:00 |
| 辰 | 07:00–09:00 |
| 巳 | 09:00–11:00 |
| 午 | 11:00–13:00 |
| 未 | 13:00–15:00 |
| 申 | 15:00–17:00 |
| 酉 | 17:00–19:00 |
| 戌 | 19:00–21:00 |
| 亥 | 21:00–23:00 |

If the corrected time falls within ~10–15 minutes of a boundary, flag that the hour pillar (and anything downstream that depends on it, e.g. 时柱's Ten God or its role in 格局/従格 checks) is sensitive to birth-time precision, and say so rather than reporting it with false confidence.

**Step 3 — find the hour stem** via 五鼠遁 (determined by the *day* stem, then cycling forward from 子):

| Day stem | 子时 starts at | Then cycle forward: 丑, 寅, 卯, 辰, 巳, 午, 未, 申, 酉, 戌, 亥 |
|---|---|---|
| 甲 or 己 | 甲子 | 乙丑 丙寅 丁卯 戊辰 己巳 庚午 辛未 壬申 癸酉 甲戌 乙亥 |
| 乙 or 庚 | 丙子 | 丁丑 戊寅 己卯 庚辰 辛巳 壬午 癸未 甲申 乙酉 丙戌 丁亥 |
| 丙 or 辛 | 戊子 | 己丑 庚寅 辛卯 壬辰 癸巳 甲午 乙未 丙申 丁酉 戊戌 己亥 |
| 丁 or 壬 | 庚子 | 辛丑 壬寅 癸卯 甲辰 乙巳 丙午 丁未 戊申 己酉 庚戌 辛亥 |
| 戊 or 癸 | 壬子 | 癸丑 甲寅 乙卯 丙辰 丁巳 戊午 己未 庚申 辛酉 壬戌 癸亥 |

Mnemonic: 甲己还加甲, 乙庚丙作初, 丙辛从戊起, 丁壬庚子居, 戊癸何方发, 壬子是真途.

## Worked example (birth data used elsewhere in this skill)

1999-04-30, 18:06, Chengdu (≈104°E).

**Library cross-validation** (actually run for this skill): `sxtwl`, `lunar-python`, and `cnlunar` were all installed and run against this date/time and **agreed exactly**: 己卯 戊辰 壬子 己酉. `sxtwl` also confirmed the 清明 boundary fell precisely on 1999-04-05 (not just "approximately" — the library flagged that exact day as a 节 boundary), validating that the manual method's approximate date table below happened to be safely clear of the boundary for this particular birth date.

**Manual method walkthrough** (for reference/teaching — reproduces the same result):
- **年柱**: 1999 is well after 立春, offset from 1984 = 15 → stem index 5 (己), branch index 3 (卯) → **己卯**.
- **月柱**: Apr 30 falls between 清明 (~Apr 5) and 立夏 (~May 6) → branch 辰. Year stem 己 → 甲己之年丙作首 → 寅丙卯丁辰戊 → 辰月 = **戊辰**.
- **日柱**: day-count from 1949-10-01 (甲子, offset 0) to 1999-04-30 = 18108 days → `18108 mod 60 = 48` → stem index 8 (壬), branch index 0 (子) → **壬子**. (Cross-checked via the 2000-01-01=戊午 anchor — both agree.)
- **时柱**: 104°E vs 120°E → correction ≈ -64 min → 18:06 clock time → ≈17:02 true solar time, still within 酉时 (17:00–19:00) either way. Day stem 壬 → 丁壬庚子居 → 子庚丑辛寅壬…酉 (9th step from 子) → **己酉**.

Result: **己卯 戊辰 壬子 己酉** — matches across all three libraries and the manual method, and is used as the recurring worked example across several other reference files (`xingchonghehui.md`, `zonghecaijue.md`, `dayunliunian.md`, `shenshakongwang.md`).