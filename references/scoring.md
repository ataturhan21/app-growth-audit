# Scoring

Two numbers come out of an audit: a **score per area** (how healthy it is) and a **priority per fix** (what to do first). Both are computed the same way every time so two audits of the same app can be compared, and so a reader can recompute any number in the report.

## Area score (0–100)

Each check has a weight in `checklist.md`: **3** (core: it decides whether a stranger understands, tries or pays), **2** (important), **1** (polish).

```
area score = round(100 × Σ weight of Pass checks ÷ Σ weight of assessed checks)
```

- Only **Pass** and **Fail** are assessed. **Not assessed** checks are left out of both sums, and the scorecard shows how many were left out, so a score built on 2 of 9 checks is visibly thin.
- An area with no assessed checks shows `—`, never 0 or 100.
- **Partial** does not exist: a check that is half met is a Fail with the missing half in its evidence.
- The overall score is the same formula over every assessed check in every area audited.

Write the computation next to the score, e.g. `62 = 100 × 13 ÷ 21 (7 of 9 checks assessed)`.

## Fix priority

Every Fail becomes a candidate fix. Score each one:

```
priority = impact × confidence ÷ effort      (range 0.33–15)
```

### Impact (1–5): how much of the funnel it touches

| Impact | Meaning | Typical examples |
|---|---|---|
| 5 | Blocks or misleads most visitors at the first step they meet, or is a possible review risk that could pull the app | first screenshots don't say what the app does; trial terms hidden; no way to dismiss a hard paywall that blocks the first value |
| 4 | Hurts every visitor at one funnel step | value buried in description's first sentence; paywall before any value; no restore purchases |
| 3 | Hurts a large share of visitors or one important segment | no localization for a market the app ships in; permission asked with no priming |
| 2 | A visible weakness that lowers trust or clarity | generic release notes; social proof without a source |
| 1 | Polish | minor wording, ordering of later screenshots |

### Confidence (1–3): how sure the evidence makes us

| Confidence | Meaning |
|---|---|
| 3 | Seen directly: the store listing, a screenshot, or the line of code that renders it, quoted in the report |
| 2 | Inferred from strong evidence: code paths whose runtime order isn't certain, a pattern across several reviews |
| 1 | Plausible from indirect evidence: a single review, a config file that may not ship |

Confidence rates whether the **problem exists as described**, not how big its effect will be (that's impact). A subtitle quoted from the live listing is confidence 3 even though its effect on search is uncertain.

### Effort (1–3): what it costs the owner

| Effort | Meaning |
|---|---|
| 1 | Text or metadata change in the store console or a string file; no new build or one string change |
| 2 | A new asset (screenshot set, video) or a contained change to one screen |
| 3 | A flow change across several screens, new backend work, or a pricing/offer change that needs the owner's decision |

### Ranking rules

1. Sort by priority, highest first.
2. Ties: higher impact first, then lower effort, then the check's order in `checklist.md`.
3. Return the top N (default 10). Keep every other Fail in a short "Also failing" list so nothing is lost.
4. A fix that changes positioning, pricing, the offer, or adds a feature is still ranked, but is labelled **Owner decision** in the Fix column: the skill proposes it and never presents it as a done deal.
5. Show the arithmetic in the table (e.g. `5×3÷1 = 15.0`), so a reader can check the order.

## What the scores are not

They are not predictions of conversion, revenue or ranking. The report never converts a priority into an expected lift, and never quotes a benchmark that isn't in `sources.md`.
