CS3 — Where I left off (pushed June 13)
Done: Section 1 (Cap & Floor Pressure) is complete. Spotrac 2026 payrolls loaded from CSV, cleaned, and split into over_cap (6 teams) and under_floor (15 teams). Diverging bar chart built and rendering. Proxy-data limitation documented in markdown (2026 figures vs. 2027 proposal).
The headline finding to build on: the pressure is lopsided ~3:1. Floor teams need to add ~$863M collectively across 15 teams; cap teams need to shed ~$289M across 6. MIA and CLE essentially have to double payroll. That's the asymmetry thesis — and the bridge to CS2: teams forced to add ~$90M overnight can't do it through pre-arb talent, so they're pushed toward expensive free agents, which torches the surplus-value efficiency I found last study.
Pick up here — Section 2 (World Series History): pull 20 years of champions' payrolls. This is where the second data source comes in (Baseball Reference via pybaseball, or another Spotrac pull) — multi-source work is a deliberate portfolio signal. Question to answer: do champions cluster in a payroll band, and where does that band sit relative to the proposed cap/floor?
Small cleanups when I'm fresh: (1) tighten the "three teams over $40M" wording in the Section 1 takeaway to match the actual table; (2) optional chart polish — vertical annotation marking the cap/floor thresholds, drop the redundant color note from the title.
First action back: git pull origin main before touching anything (I may be on the PC), confirm the baseball-analytics kernel is selected, run all cells top-to-bottom to confirm Section 1 still executes clean, then start Section 2.

CS3.2 — Where I left off (pushed June 29)
Done: Built the Section 2 scatter — World Series champions and contenders, 2005–2025, opening-day payroll, with the proposed 2027 cap/floor as reference lines. Legend split into two scatter calls so champion/contender colors are labeled. Finding: almost no team clears the cap; many (champions included) fall below the floor — the same asymmetry as Section 1, but shown through outcomes.

Next — Strategy B (within-season ranking): nominal dollars can't separate "spent little" from "2005 dollars were small." Fix = rank each champion's payroll among that year's 30 teams (or express as a ratio to that season's league average). Tests my own hypothesis — were champions usually top-N spenders for their era? Watch for exceptions (2005 CHW, 2015 KCR, 2021 ATL won cheap) — the exceptions are the story.

Data still needed: each season's full 30-team payrolls, OR each year's league-average payroll, 2005–2025. Source from thebaseballcube (same as the champion pull). Note: cap/floor lines DROP OUT of the ranking chart — a rank has no dollar value, so the lines can't be placed. Ranking is a separate exhibit, not an edit to this one.


CS3.2 Strategy B — data done, one fix pending:
Ratio math confirmed correct (2005 CHW = 1.03, 2009 NYY = 2.28, 2025 LAD = 1.96).
BUG: contender rows show NaN — 'league-total-payroll' wasn't included in the contenders column selection. Fix: add it to that [[...]] list, re-run, confirm contender ratios populate, THEN commit/push.
After that: build the Strategy B chart (payroll_ratio on y, no cap/floor lines — they don't exist in ratio space).


CASE STUDY AS A WHOLE:
1. In S2, we graph the teams over the proposed cap and under the floor but there is no takeaways/summary of why it matters and the findings.
2. Review S3s original arrays for "Champion" and "Contender," they might be outdated. 