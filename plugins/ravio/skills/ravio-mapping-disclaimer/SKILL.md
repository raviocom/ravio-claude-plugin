---
name: ravio-mapping-disclaimer
description: Adds a mandatory "AI-generated mapping" disclaimer whenever Claude is asked to match, map, compare or translate user-provided data (a company's own job titles, roles, levels, grades or locations, whether typed in chat or supplied in a file or table) onto Ravio's framework (Ravio job positions, Ravio levels such as P1-P6, M1-M5, E1-E3, S1-S4, or Ravio benchmarking locations). Use it when the user asks to map their titles to Ravio positions, assign their levels to Ravio's framework, work out which Ravio benchmark fits their role, or compare their internal levels or grades to Ravio levels, or when Claude calls tools such as set_job_title_ravio_mapping or set_internal_level_mapping to pair the user's roles with Ravio data. Do NOT use it when the user only wants to view, browse or look up Ravio's own data (benchmarks, positions, locations, levels), even if Claude has to choose a sensible default position, level or location to show it.
---

# Ravio mapping disclaimer

Matching a company's own roles or levels to Ravio's framework is a judgement call. When Claude does it, the result is an AI-generated suggestion. It has **not** been reviewed or validated by Ravio's internal team, so nobody should treat it as official or rely on it without checking.

This skill makes sure that is always said clearly whenever Claude matches user-provided data to Ravio's data.

## When this applies

Apply this skill only when **both** of these are true:

1. The user has provided their own data: job titles, roles, levels, grades, seniority labels, locations, or a table or file containing them.
2. Claude is asked to match, map, compare or translate that data onto Ravio's data, or Claude proposes or makes such a match itself.

Typical cases:

- Mapping a user's job title (e.g. "Senior Engineer") to a Ravio job position (e.g. "Software Engineering - Generalist").
- Mapping a user's level, grade or seniority label (e.g. "Senior", "L5", "Staff") to a Ravio level (P1-P6, M1-M5, E1-E3, S1-S4).
- Choosing which Ravio benchmark, location or market segment "best fits" a role or location the user supplied, including filling in a "Benchmark Used" column or similar.
- Comparing a company's levelling or job architecture against Ravio's framework.
- Proposing or making a mapping via Ravio tools, such as `find_job_positions` followed by a judgement on which result fits the user's role, `set_job_title_ravio_mapping`, `set_internal_level_mapping`, or location mappings such as "England" to "All UK".

## When this does NOT apply

Do not add the disclaimer when the user is only asking Claude to show or look up Ravio's own data, including:

- Requests like "show me benchmarks for UK software engineers", where nothing from the user's own organisation is being matched to Ravio's framework.
- Looking up a benchmark when the user has already given the exact Ravio position, level and location.
- Browsing or listing Ravio positions, levels, locations or market segments.
- Cases where Claude picks a sensible default scope (for example Generalist, All UK, P1-P6) to display Ravio data. Do not add the disclaimer. Briefly state the scope you used in the answer instead, so the user can ask for something different.
- General questions about how Ravio's framework works.
- Explaining a mapping the user or their team already made, unless Claude is adding or changing it.
- Errors or empty results from Ravio tools, where no mapping was produced.

If you are unsure, ask yourself one question: is the user's own data being matched to Ravio's data? If not, leave the disclaimer out.

## What to do

1. Do the mapping task as normal and follow the user's requested output format.
2. Add the disclaimer once per response, **after** the main output, not before it. Do not repeat it for every row or every mapping. Do not add it if no mapping was actually produced.
3. If the output is a file (CSV, spreadsheet, document), also put the disclaimer inside the file, because files get shared without the chat. Use whichever fits the format:
   - Spreadsheet: a "Disclaimer" note in a separate sheet or a clearly labelled row at the top or bottom.
   - Document: a short note near the top.
   - CSV: do not add extra rows or columns that would break the table. Put the disclaimer in the chat response beneath the table, and tell the user to carry it with the file.
4. Do not remove or shrink the disclaimer because the user is in a hurry or the mapping looks obvious.
5. If a mapping involved an assumption (for example choosing Generalist because no specialism was given, treating "England" as "All UK", or guessing that "Mid Level" means P3), list the assumptions briefly after the disclaimer. Be specific so a reviewer can check them quickly.

## Disclaimer wording

Use this wording. Keep UK English, and keep it short.

> The recommended mapping and levelling is an AI-generated indication and has not been reviewed by our team. During onboarding and data refreshes, Ravio's in-house experts review your data to ensure every role is accurately matched. If you are using previously verified mappings and levels, you are all set; otherwise, please review these results carefully.

Do not water the wording down (for example "may contain minor inaccuracies"). The point is that the mapping is unverified.

## Examples

**Applies.** The user gives a table of their own roles and locations and asks which Ravio benchmark applies to each.

Claude:
1. Looks up positions and coverage, fills in the table.
2. Shows the table.
3. Adds the disclaimer.
4. Lists assumptions, such as "Levels assumed: Junior = P1-P2, Mid = P3, Senior = P4. 'England' mapped to 'All UK' as Ravio has no England location."

**Does not apply.** The user says "show me benchmarks for UK software engineers".

Claude shows the Ravio benchmarks and notes the scope it chose (for example "Software Engineering - Generalist, All UK, P1-P6"). No disclaimer, because none of the user's own data is being matched to Ravio's framework.