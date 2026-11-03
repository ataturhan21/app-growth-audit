# app-growth-audit

A [Claude Code](https://claude.com/claude-code) skill that audits a mobile subscription app the way a stranger meets it — **store listing → screenshots → onboarding → paywall** — and returns the 10 fixes worth doing first.

Every finding cites evidence you can open (a quote, a screenshot, a `file:line` or a URL), and every number comes from a listed source. When the evidence isn't there, the check says **Not assessed** and names the input that would unlock it, instead of guessing.

## What it does

1. **Gathers evidence** from public sources and what you give it:
   - App Store: Apple's public lookup endpoint (title, description, screenshots, rating, release notes), the listing page (subtitle, live screenshots) and the public review feed.
   - Google Play: the public listing page.
   - The screenshot images themselves.
   - Onboarding and paywall: your screenshots or screen-recording frames, or your app's source code (read-only).
2. **Checks it** against [`references/checklist.md`](references/checklist.md): 26 checks across the store listing, onboarding, paywall and copy. Each check lists what to look for, why it matters, how to verify it, and a source from [`references/sources.md`](references/sources.md) (Apple's and Google's own guidelines, quoted).
3. **Scores and ranks** with [`references/scoring.md`](references/scoring.md): each area gets a 0–100 score (weighted share of assessed checks passed), and each fix gets a priority of impact (1–5) × confidence (1–3) ÷ effort (1–3), with the arithmetic shown.
4. **Writes a Markdown report**: verdict, scorecard, ranked fixes, check results, what wasn't assessed, and sources.

It is read-only: no logins, purchases, trials or account creation, and it never edits your project.

## Install

**Option A: copy the folder** (simplest; update by copying again)

```bash
git clone https://github.com/ataturhan21/app-growth-audit ~/.claude/skills/app-growth-audit
```

**Option B: install as a plugin** (update with `/plugin marketplace update app-growth-audit`)

```
/plugin marketplace add ataturhan21/app-growth-audit
/plugin install app-growth-audit@app-growth-audit
```

Pick one; installing both gives you two copies of the skill.

For claude.ai or the Skills API, remove the `argument-hint` line from `SKILL.md` first. That field is specific to Claude Code.

## Use

Just ask; the skill triggers on requests like these:

- `audit my app's store listing https://apps.apple.com/us/app/…/id123456789`
- `review my paywall, screenshots are in ~/Desktop/paywall`
- `why isn't my app growing? store link …, the code is in ./mobile-app`
- `roast this app's store page and compare it with https://apps.apple.com/…`

Or call it directly:

```
/app-growth-audit <store URL | app name> [screenshots=<folder>] [project=<folder>] [vs <competitor URLs>] [listing|onboarding|paywall|all] [top=<N>]
```

Defaults are `all`, top 10 and the `us` storefront (or the one in the URL). Every default it takes is stated in the report.

| You give it | It can assess |
|---|---|
| A store link only | Listing and copy. Onboarding and paywall are **Not assessed**. |
| + onboarding/paywall screenshots | + onboarding and paywall, from the images |
| + the app's project folder | + onboarding and paywall from the code, with a "File to change" for each fix |

## Example report

Excerpt from a store-link-only audit of [Fitbod](https://apps.apple.com/us/app/fitbod-gym-fitness-planner/id1041517543), 2026-11-03 (full report in [`evals/reports/fitbod-store-only.md`](evals/reports/fitbod-store-only.md)):

> **Verdict:** Put the app's clearest differentiator in the first three screenshots: the third slot is "CUSTOMIZE YOUR EQUIPMENT", a setup step, while the line that says what Fitbod does for a lifter ("KNOW HOW MUCH TO LIFT") sits at `listing screenshot #4`. Search results only show the first one to three images (A-PP).

| Area | Score | How it was computed |
|---|---|---|
| Store listing | 59 | 100 × 10 ÷ 17 (9 of 9 checks assessed) |
| Onboarding | — | 0 of 6 checks assessed |
| Paywall | — | 0 of 9 checks assessed |
| Copy | 50 | 100 × 2 ÷ 4 (2 of 2 checks assessed) |

| Rank | Fix | Area | Priority |
|---|---|---|---|
| 1 | Move "KNOW HOW MUCH TO LIFT" (now #4) into slot 2 or 3 | Listing · L-SHOTS3 | 4×3÷1 = 12.0 |
| 2 | Lead the description with what the app does, not "*Apple Editor's Choice Award Winner*" | Listing · L-DESC1 | 4×3÷1 = 12.0 |
| 3 | Say plainly that a subscription is needed after the trial, and how to cancel (7 of the 50 most recent reviews raise this) | Copy · C-OBJECT | 4×2÷1 = 8.0 |

## Evals

[`evals/`](evals/) holds the test cases, each a folder in the layout `claude plugin eval` reads (`prompt.md`, `case.yaml`, `graders/`), plus the reports from the runs used to test this release:

| Case | App | Result |
|---|---|---|
| `looks-max-store-only` | [Looks Max](https://apps.apple.com/us/app/looks-max-look-your-best/id6778990308), store link only | [report](evals/reports/looks-max-store-only.md) |
| `looks-max-with-project` | Looks Max with its source code (owner-only: the project is private) | [summary](evals/reports/looks-max-with-project-summary.md) |
| `umax-store-only` | [Umax](https://apps.apple.com/us/app/umax-become-hot/id6471026798) (face rating) | [report](evals/reports/umax-store-only.md) |
| `fitbod-store-only` | [Fitbod](https://apps.apple.com/us/app/fitbod-gym-fitness-planner/id1041517543) (fitness) | [report](evals/reports/fitbod-store-only.md) |

Each report was checked by hand before release: every quote was found in the saved review feed or listing, every number traced to `sources.md` or the evidence, and every ranking recomputed. [`evals/trigger-queries.json`](evals/trigger-queries.json) holds 16 queries for testing when the skill should and shouldn't trigger.

Reports are snapshots of public listings on 2026-11-03; the listings will change.

## Limits

- **It can't see what isn't public or given.** Without onboarding/paywall screenshots or source code, those areas are Not assessed. It never starts a purchase or trial to see a paywall.
- **Apple's lookup endpoint doesn't return the subtitle, in-app purchase prices or preview videos**, and its screenshot list can differ from what the live page shows. The skill reads the listing page for these. When it can't render the page, the affected checks are Not assessed or say what they relied on.
- **Screenshot images may need a browser.** Some networks reset non-browser downloads from Apple's image CDN. The skill then opens the images in a browser tool, and without one marks the screenshot checks Not assessed.
- **Review checks need written reviews.** A new app with none gets Not assessed for copy checks.
- **Scores are not predictions.** Area scores and priorities rank what to fix. They don't forecast conversion, revenue or ranking, and the skill never quotes a lift or benchmark that isn't in `sources.md`.
- **Several checks are judgment calls** (marked `practice` in the checklist, listed in `sources.md`): there's no primary source behind them, so they never carry a number.
- **Not legal advice.** Store-guideline issues are flagged as a "possible review risk" with the guideline cited.

## Credits

The checklist's scope (listing → onboarding → paywall → lifecycle) was inspired by two talks at RevenueCat's App Growth Annual 2026: "Why your app's marketing stalls, and what to fix first" and "The big app roast: paywall and lifecycle teardowns". The rules themselves are sourced from Apple's and Google's published guidelines.

## License

[MIT](LICENSE)
