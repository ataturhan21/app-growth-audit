# Release test results (v1.0.0, 2026-11-03)

Each case was run by a fresh agent that followed only `SKILL.md` and its references. Each report was then checked by hand against its graders (`evals/<case>/graders/`) and against the evidence: quotes were matched to the saved review feed, listing and source files; numbers were traced to `references/sources.md` or the evidence; and every score and priority was recomputed.

No-skill baseline runs were not done for this release.

## Final results

| Case | Rounds | Graders passed (final round) | Verdict |
|---|---|---|---|
| `looks-max-store-only` | 2 | 6 / 6 | Remove the unverifiable "science-backed" and "92%" claims (possible review risk) |
| `looks-max-with-project` | 3 | 6 / 6 | Remove the unsourced "92%" claim from the paywall and onboarding |
| `umax-store-only` | 2 | 5 / 5 | Say what costs money before download; 21 of the 50 most recent reviews complain about the pay-or-invite gate |
| `fitbod-store-only` | 1 | 5 / 5 | Put "KNOW HOW MUCH TO LIFT" (now screenshot #4) in the first three |

## What failed, and what changed in the skill

| Round | Case | Failure found by hand-checking | Skill change |
|---|---|---|---|
| 1 | umax | A fix suggested a "15–30 s" preview; only "up to 30 seconds" is sourced | Numbers inside suggested fixes must be in sources.md too |
| 1 | umax | Failed L-HONEST on an in-app demo percentile ("better than 81% of people" inside the device frame) | L-HONEST separates in-app sample data from marketing claims |
| 1 | fitbod, umax | Apple's lookup returned a different screenshot set from the one the live page shows | Judge screenshot checks on the live page's media strip; note the lookup set |
| 1 | looks-max-with-project | Passed O-PERM after finding one in-context notification request; a dashboard hook asks on first visit | Trace every caller of each permission request |
| 1 | both Looks Max runs | A subtitle quoted directly was scored confidence 2 | scoring.md: confidence rates whether the problem exists, not its effect |
| 2 | looks-max-with-project | The same unsourced claim got impact 5 on the listing and 3 on the paywall | A possible review risk is impact 5, consistently |
| 2 | looks-max-with-project | Missed that the paywall's "potential" number is partly derived from a per-install value | P-PROOF traces every personal number shown before the paywall to its formula |
| — | runs on Windows | Paths over 260 characters broke the shell, git and Python | Keep working paths short and use absolute paths |

Judgment calls can still vary between runs. For example, Umax's first three screenshots were a Fail in round 1 and a Pass in round 2, because the captions show the app in use but don't say "face rating". The rubric constrains these calls but doesn't remove them.

## Trigger check

[`trigger-queries.json`](../trigger-queries.json): 16 queries, 8 that should trigger the skill and 8 near-misses. A separate model was given only the skill descriptions, with `top10-growth`, `top10-ux`, `top10-design`, `top10-wording`, `top10-i18n` and `qa-bug-hunt` as competing skills, and chose correctly 16 of 16 times. That includes "audit my app's store listing", "review my paywall" and "why isn't my app growing", which chose this skill. This is a proxy: `claude -p`, the real trigger runner, wasn't available on the test machine.
