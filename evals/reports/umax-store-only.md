> Release test run for app-growth-audit v1.0.0 (eval case `umax-store-only`, second round after skill fixes), hand-checked on 2026-11-03: quotes traced to the saved review feed and listing, scores and ranking recomputed. The `data/` files it cites were working files and are not included. A snapshot of a public listing; it will change.

# App growth audit: Umax - Become Hot (App Store, us) — 2026-11-03

**Inputs:** https://apps.apple.com/us/app/umax-become-hot/id6471026798 · screenshots: none · project: none · competitors: none · focus: all · top 10. Defaults taken: focus `all`, top 10, storefront `us` (from the URL's `/us/` segment); screenshots judged on the live page's media strip (4 images), which differs from the lookup's older 5-image set.

## Verdict
Say what costs money before people download: the listing reads "Free" and its screenshots show finished scores, while 21 of the 50 most recent reviews complain they had to pay or invite 3 friends before seeing anything ("Have to buy pro or recommend three friends to even see anything", review #26), and the only disclosure is a footnote near the end of the description ("*analysis results require subscription. Additional scans require additional purchase."); the invite-3-friends route is never mentioned.

The roast in one breath: 4.6 stars from 52K ratings, but 47 of the last 50 reviews are 1–2 stars; the subtitle "Get your ratings" doesn't say ratings *of what*; the description opens with "1) Download the app"; and there's been no update since June 2024 while 22 recent reviewers say the scan broke or the app crashed after they paid.

## Scorecard
| Area | Score | How it was computed |
|---|---|---|
| Store listing | 41 | 100 × 7 ÷ 17 (9 of 9 checks assessed) |
| Onboarding | — | 0 of 6 checks assessed |
| Paywall | — | 0 of 9 checks assessed |
| Copy | 0 | 100 × 0 ÷ 4 (2 of 2 checks assessed) |
| **Overall** | 33 | 100 × 7 ÷ 21 (11 of 26 checks assessed) |

## Ranked fixes
| Rank | Fix | Area | Evidence | Impact | Effort | Priority | How to check it worked |
|---|---|---|---|---|---|---|---|
| 1 | Put the cost up front, truthfully: open the description and the promotional text (limit 170 characters, A-PP) with one plain line on what is free and what isn't — taking the scan is free; seeing results needs the subscription or 3 friend invites; extra scans and "10/10" images are separate purchases (owner fills in the exact current terms). This states the offer; it doesn't change it. | Copy · C-OBJECT | 21/50 recent reviews hit the pay/invite gate (data/review_coding.json): #7 "You can only use it if you pay for it or if 3 of your friends download it"; #45 "you actually have to pay for this even though it's advertised as free"; #49 "There's no glimpse or trial of what you're paying for". Listing: "Free · In‑App Purchases"; disclosure only as a late footnote; invite route not mentioned anywhere | 5 | 1 | 5×3÷1 = 15.0 | The lines visible without tapping "more" state the cost; in the review feed, new reviews about "have to pay" / "invite 3 friends" |
| 2 | Rewrite the subtitle to name the job in searchers' words, e.g. "AI Face Rating & Looksmax" (25 of 30 characters). Renaming the app itself ("Become Hot") is optional and an **Owner decision** (positioning). | Listing · L-TITLE | Name "Umax - Become Hot" (17 chars), subtitle "Get your ratings" (16 chars): neither says *face* or *looks*. Apps under "You Might Also Like" on the same page use "AI Face Attractiveness Test" and "Looks Rater, Symmetry Analyzer" | 4 | 1 | 4×3÷1 = 12.0 | Live listing shows the new subtitle; App Store Connect search impressions for face-rating terms |
| 3 | Replace the description's opening "HOW TO USE UMAX: 1) Download the app…" with one sentence saying what it does and for whom (e.g. "Umax rates your face from a selfie — overall, jawline, skin, cheekbones — and builds a glow-up routine to improve it."), then the cost line from fix 1. Drop the unsupported "faster than anybody else". | Listing · L-DESC1 | First sentence: "HOW TO USE UMAX: 1) Download the app 2) Take a selfie 3) Get your analysis*"; "facial attractiveness" first appears in the 4th paragraph | 4 | 1 | 4×3÷1 = 12.0 | The text above the "more" fold names face rating and the routine |
| 4 | Use the reviewers' own words — "face scan", "face rating", "glow-up advice/routine" — in subtitle, screenshot captions and promotional text (overlaps fixes 2–3) | Copy · C-VOC | Reviewers: "AI face ratings" (featured review by TheFredAccount), "face scan" (#19), "gives good glow-up advice" (featured review by Imogyouparasite). Captions: "Get your ratings", "Custom routine", "You as a 10/10", "Overall score": no "face", no "scan" | 3 | 1 | 3×2÷1 = 6.0 | Captions and subtitle contain "face" and "scan"/"rating" |
| 5 | Fill more of the 10 screenshot slots, each with a distinct message: the trait breakdown, progress picture, group scanning (the latest release's feature, absent from the strip), and one honest "how it works / what's free" frame | Listing · L-SHOTSALL | Live media strip: 4 screenshots (data/live_listing.txt); "Added new group scanning!" not shown in any screenshot | 2 | 2 | 2×3÷2 = 3.0 | Live strip shows the new screenshots, none repeating a message |
| 6 | Ship an update (see fix 7) with release notes naming what changed for the user | Listing · L-FRESH | `currentVersionReleaseDate` 2024-06-28, version 1.4.3: over two years before this audit | 2 | 2 | 2×3÷2 = 3.0 | Listing shows a 2026 version date with specific notes |
| 7 | Fix the post-purchase failures reviewers keep hitting (scan stuck at 91%, results never shown after inviting friends, crash on launch after subscribing), then reply to affected reviews with the fix and how to request a refund through Apple | Listing · L-RATING | 4.56 from 51,707 ratings, but 44 of the 50 most recent are 1★ and 3 are 2★; 22/50 say it broke after paying or inviting: #46 "got stuck at 91%… so i just wasted $4"; #31 "Just crashes every time, I've reinstalled, restarted, tried everything"; #34 "i went to redeem to see my results and it didnt work" | 4 | 3 | 4×2÷3 = 2.67 | Review feed: 1★ reviews mentioning crash / 91% / no results |
| 8 | Add an app preview whose first seconds show the selfie turning into the score | Listing · L-VIDEO | Live page: no `<video>` element and no play control in the media strip | 1 | 2 | 1×2÷2 = 1.0 | Media strip opens with a preview |

Ties: fixes 2 and 3 (12.0, impact 4, effort 1) and fixes 5 and 6 (3.0, impact 2, effort 2) are ordered by checklist order.

**Also failing:** none beyond the 8 above.

## Check results

**Store listing**
| ID | Result | Evidence |
|---|---|---|
| L-TITLE | Fail | "Umax - Become Hot" (17) + "Get your ratings" (16); no plain description of the job (face rating) in either |
| L-SHOTS3 | Pass | Live #1 "Get your ratings" (ratings screen: Overall 86, Potential 95, Masculinity, Skin Quality, Jawline, Cheekbones), #2 "Custom routine" (glow-up routine with streak), #3 "You as a 10/10" (AI portrait); all show the app in use and together state rating + improvement |
| L-SHOTSALL | Fail | 4 screenshots on the live listing (the lookup returns an older set of 5) |
| L-VIDEO | Fail | Live page DOM: no `<video>`, no play/preview control |
| L-RATING | Fail | 4.56 / 51,707 ratings; recent 50 (2026-03-26 → 2026-11-01): 44×1★, 3×2★, 1×4★, 2×5★; repeated complaints quoted in fixes 1 and 7 |
| L-DESC1 | Fail | Opens with "HOW TO USE UMAX: 1) Download the app…" |
| L-LOCAL | Pass | `languageCodesISO2A`: ["EN"]; US storefront, no other target market known (passed on the language list alone) |
| L-FRESH | Fail | 1.4.3, 2024-06-28; notes "Added new group scanning!" are specific, but the date is over a year old |
| L-HONEST | Pass | No statistic, award or user count in captions or description; in-app numbers (86, 95, bell curve) are demo UI, not claims. "faster than anybody else" is an unsupported superlative but not a number or award (removed in fix 3 anyway) |

**Copy**
| ID | Result | Evidence |
|---|---|---|
| C-VOC | Fail | Users say "face scan", "face ratings", "glow-up advice"; subtitle and captions use none of them |
| C-OBJECT | Fail | Pay/invite gate raised by 21 of 50 recent reviews; answered only by a late footnote; invite route unmentioned |

**Onboarding / Paywall:** all Not assessed (below). The marketing screenshots show the product, not the flow, so they weren't used for O/P checks.

## Not assessed
| Check(s) | Missing | Input that unlocks it |
|---|---|---|
| O-TTV, O-PERSONAL, O-PERM, O-ACT, O-SKIP, O-SHORT | First-run screens | Onboarding screenshots or a screen recording (`screenshots=`), or the app's project folder (`project=`) |
| P-PLACE, P-PLANS, P-TRIAL, P-DEFAULT, P-SAVE, P-PROOF, P-CLOSE, P-RESTORE, P-LEGAL | Paywall screens and prices (IAP prices aren't in the lookup; no purchase flow was started) | A paywall screenshot or the project folder. Reviews point at what to check first: an invite-3-friends gate instead of a preview (#7, #26), per-scan charges on top of the subscription ("$5 PER SCAN", featured review), and whether any result is previewed before paying (#49). Changing that offer would be an **Owner decision**. |

## Sources
- https://itunes.apple.com/lookup?id=6471026798&country=us → data/lookup.json (A-LOOKUP)
- https://itunes.apple.com/lookup?id=6471026798&country=de → data/lookup_de.json (fetched; not used for a check)
- https://itunes.apple.com/us/rss/customerreviews/page=1/id=6471026798/sortby=mostrecent/json → data/reviews.json (A-RSS); hand coding in data/review_coding.json (supersedes the keyword pass in data/review_tally.json)
- https://apps.apple.com/us/app/umax-become-hot/id6471026798 (page text and media strip) → data/live_listing.txt
- Live screenshots viewed in a browser (is1-ssl.mzstatic.com, 392x696bb.jpg): …_Frame_10.png, …_Frame_93045.png, …_Frame_9.png, …_Frame_93046.png; lookup set #1 …_Frame_2608148.png
- sources.md IDs cited: A-PP (30-character name/subtitle, 170-character promotional text, 10 screenshot slots, first-sentence and screenshot guidance), A-RG 2.3.1(a), 2.3.3, 2.3.7, 3.1.2(c), A-LOOKUP, A-RSS; `practice` for L-FRESH, C-VOC, C-OBJECT
