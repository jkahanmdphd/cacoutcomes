# Cardiac arrest outcomes: icon arrays

A single-page web app that draws icon-array figures (1 icon = 1 person out of 100 or 1,000) for survival and functional outcomes after cardiac arrest, using the raw counts published by randomized trial cohorts.

Everything is in `index.html`: no build step, no dependencies, no network requests.

## Hosting on GitHub Pages

1. Create a repository (for example `arrest-icons`) and add `index.html` and this README to the `main` branch.
2. In the repository, open **Settings → Pages**, set **Source** to "Deploy from a branch", branch `main`, folder `/ (root)`, and save.
3. After a minute the app is live at `https://<your-username>.github.io/arrest-icons/`.

## Features

- Choose cohort, outcome (survival or functional), and group: pooled, a single arm, or both arms side by side.
- Choose which side of the outcome to count (e.g. "died" or "alive").
- 100 or 1,000 icons; grouped or scattered; person, dot or square icons.
- Exact counts with 95% Wilson confidence intervals under each array.
- Download PNG (3x) or SVG; the figure carries its own title, legend and source.
- The URL hash stores the current settings, so any figure can be linked directly.

## Cohorts included

TTM2 (2021), TAME (2023), TTM (2013), BOX blood-pressure and oxygen comparisons (2022), CAPITAL CHILL (2021), HYPERION (2019), TOMAHAWK (2021, with 1-year follow-up), COACT (2019), HACA-IHCA (2022), PARAMEDIC2 (2018), PARAMEDIC-3 (2024).

Two observational cohorts from settings with little or no withdrawal of life-sustaining therapy are also included: KORHN-PRO (South Korea, registry of 1,354) and ProNeCA (Italy, prognostication cohort of 346).

STEPCARE is not included: its main results had not been published when this was built.

## Adding or correcting data

All data live in the `TRIALS` array near the top of the `<script>` block. Each outcome lists `[events, denominator]` per arm exactly as published, plus plain-language labels for the event and its complement. Add an object and it appears in the menus and the data table automatically.

Some counts are derived rather than quoted and are flagged `derived: true`: CAPITAL CHILL 180-day mortality and HACA-IHCA CPC 1–2 (back-calculated from percentages); KORHN-PRO CPC 3–4 (survivors minus those with CPC 1–2); ProNeCA deaths (poor outcomes minus those alive in an unresponsive state).

## Caveats

Trial participants are selected, and outcome scales differ between trials (mRS, CPC, GOS-E, Disability Rating Scale). The figures describe cohort averages and are not individual prognoses.
