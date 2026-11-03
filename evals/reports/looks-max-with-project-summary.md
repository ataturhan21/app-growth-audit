# Looks Max with its project folder: summary

Eval case `looks-max-with-project`, run (b) of the release test, 2026-11-03. The app's source is private, so this is a short public summary. The full report, with `file:line` evidence, stays with the owner. The run was hand-checked: every code quote was re-opened and matched, and the scores and ranking were recomputed. The project folder was read only: its `git status` was clean after every run.

## What a project folder adds

The store-link-only run ([report](looks-max-store-only.md)) could assess 9 of 26 checks. With the source code, 24 of 26 were assessed. Only the two copy checks stayed Not assessed, because the app has no written reviews yet.

| Area | Store link only | With project folder |
|---|---|---|
| Store listing | 24 (9 of 9 checks) | 24 (9 of 9) |
| Onboarding | — (0 of 6) | 25 (6 of 6) |
| Paywall | — (0 of 9) | 48 (9 of 9) |
| Copy | — (0 of 2) | — (0 of 2) |
| **Overall** | 24 (9 of 26) | 34 (24 of 26) |

## Verdict and top 5 fixes

**Verdict:** remove the unsourced "92% feel more confident after 3 weeks" claim from the paywall and onboarding. It is shown at the moment of purchase and on listing screenshot #4, and users can't check its source, which makes it a possible review risk (A-RG 2.3.1(a)). The structural blockers come next: 0 ratings, no rating prompt, and a hard paywall before any real result.

| Rank | Fix | Area · check | Priority |
|---|---|---|---|
| 1 | Remove or source the "92%" claim on the paywall and in onboarding | Paywall · P-PROOF | 5×3÷1 = 15.0 |
| 2 | Name the job in the subtitle ("face rating"), not "Your Daily Looks Maxxing Coach" | Listing · L-TITLE | 4×3÷1 = 12.0 |
| 3 | Make the store's trial setup match the paywall, which hides any plan that has a free trial (**Owner decision** whether to offer a trial) | Paywall · P-TRIAL | 4×2÷1 = 8.0 |
| 4 | Remove or source the "92%" badge on screenshot #4 and "science-backed" in the description | Listing · L-HONEST | 5×3÷2 = 7.5 |
| 5 | Compute the "potential" shown before the paywall from the user's answers only, since part of it comes from a per-install value | Paywall · P-PROOF | 5×3÷2 = 7.5 |

Ranks 6 to 10 cover asking for a rating after the first score reveal, a description that matches the screenshots, release notes, a visible way out of the paywall (**Owner decision**), and the German listing.

## What the code showed that the listing couldn't

- **The paywall comes before any real result.** The onboarding "scan" is an animation, and the real analysis runs after payment and sign-up.
- **The paywall has no close or back control.** It's a hard paywall, which is the owner's choice; on Play it's a possible review risk.
- **Notification permission** is requested on the first dashboard visit, with no explanation screen first.
- **These parts pass:** plan clarity (the billed price is the largest), an honest savings badge computed from real prices, Restore Purchases, the Terms and Privacy links, and the auto-renew disclosure.

## How the eval improved the skill

This case went through three rounds:
- **Round 1** passed the notification-permission check after finding one legitimate call site. It missed a dashboard hook that asks on first visit. The skill now traces every caller of a permission request.
- **Round 2** gave the same unsourced claim impact 5 on the listing but 3 on the paywall. It also missed that the "potential" number is partly derived from a per-install value. The skill now pins any possible review risk to impact 5 and traces every personal number shown before the paywall to its formula.
- **Round 3** caught both.
