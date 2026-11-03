> Release test run (a) for app-growth-audit v1.0.0: eval case `looks-max-store-only`, second round after skill fixes, hand-checked on 2026-11-03. Store link only, so onboarding and paywall are Not assessed by design. The `data/` files it cites were working files and are not included. A snapshot of a public listing; it will change.

# App growth audit: Looks Max - Look Your Best (App Store, us) — 2026-11-03

**Inputs:** https://apps.apple.com/us/app/looks-max-look-your-best/id6778990308 · screenshots: none · project: none · competitors: none · focus: all · top 10. Defaults taken: focus `all` (none named), top 10, storefront `us` (from the URL's `/us/` segment); no screenshots or project folder, so onboarding and paywall are Not assessed. Only 8 checks failed, so 8 fixes are ranked.

## Verdict
Remove or source the unverifiable claims first: the description's first sentence promises "objective, science-backed insights" and listing screenshot #4 shows a "92% feel more confident after 3 weeks*" badge whose only basis is "*Looks Max user survey"; a user can't check either, and under A-RG 2.3.1(a) misleading marketing "is grounds for removal" (possible review risk, not legal advice).

## Scorecard
| Area | Score | How it was computed |
|---|---|---|
| Store listing | 24 | 100 × 4 ÷ 17 = 23.5 → 24 (9 of 9 checks assessed; Pass: L-SHOTS3 3 + L-SHOTSALL 1) |
| Onboarding | — | 0 of 6 checks assessed |
| Paywall | — | 0 of 9 checks assessed |
| Copy | — | 0 of 2 checks assessed (no written reviews in the us, de or gb feeds) |
| **Overall** | 24 | 100 × 4 ÷ 17 = 23.5 → 24 (9 of 26 checks assessed) |

## Ranked fixes
| Rank | Fix | Area | Evidence | Impact | Effort | Priority | How to check it worked |
|---|---|---|---|---|---|---|---|
| 1 | Rewrite the description's first sentence without "objective, science-backed": say what the app measures, e.g. "Looks Max uses AI to rate your face and break the score down by symmetry, skin quality, jawline and more." Keep "science-backed" only if the description links the study. | Listing · L-HONEST | Description sentence 1: "deliver objective, science-backed insights" (lookup `description`; live listing page) | 5 | 1 | 5×3÷1 = 15.0 | The live description has no "science-backed"/"objective", or names its source next to it. |
| 2 | Put the core job in the name or subtitle in the words people search, e.g. subtitle "AI Face Rating & Glow-Up Coach" (30 characters, the limit) instead of "Your Daily Looks Maxxing Coach"; "Look Your Best" in the name is a slogan. | Listing · L-TITLE | Name "Looks Max - Look Your Best" (26 characters); subtitle "Your Daily Looks Maxxing Coach" (30 characters); neither says "face rating"/"face score", though screenshot #1's caption is "AI face rating…". Similar apps on the same page name the job: "Face rating: looksmax analysis", "AI Face Rating & Glow Up", "Face Rating & Glow Up Coach". | 4 | 1 | 4×3÷1 = 12.0 | The subtitle (or name) contains "face rating" or "face score"; watch App Store Connect search impressions for that term. |
| 3 | Fix the brand slip "Only Looksmax" → "Looks Max", and add the features the screenshots sell but the text never mentions: Future Self AI projection, daily habits with XP and streaks, daily-selfie timelapse, hair and beard scoring, leaderboard, paid 1:1 coach calls. | Listing · L-DESC1 | Description paragraph 2: "Only Looksmax gives you the data-driven tools"; screenshots #3 "SEE YOUR FUTURE FACE.", #4 "BUILD THE HABITS.", #5 "WATCH IT HAPPEN.", #6 "THE CUT THAT FITS YOU." (and lookup-set #7 "CLIMB THE LEADERBOARD.", #8 "TALK TO A REAL COACH.") have no matching line under "KEY FEATURES". | 3 | 1 | 3×3÷1 = 9.0 | The description uses one app name throughout and each screenshot headline has a matching feature line. |
| 4 | Remove the "92% feel more confident after 3 weeks*" badge from screenshot #4, or replace it with a statement the user can verify (survey size, date, where it's published). Re-export it in every device-size set. | Listing · L-HONEST | Listing screenshot #4 (C04_65; also lookup set C04_69): badge outside the device frame "92% feel more confident after 3 weeks*", footnote "*Looks Max user survey"; no survey details anywhere on the listing. Possible review risk (A-RG 2.3.1(a)). | 5 | 2 | 5×3÷2 = 7.5 | Screenshot #4 on the live listing shows no unsourced percentage. |
| 5 | Ask for ratings at a success moment (after the first face score is revealed, or a streak milestone) with `SKStoreReviewController`/`requestReview`, never on first launch or during onboarding; the system allows the prompt 3 times in 365 days (A-HIG-RR). If a prompt already exists, check that it fires. | Listing · L-RATING | Lookup `averageUserRating` 0, `userRatingCount` 0; listing page: "This app hasn't received enough ratings or reviews to display an overview." Version 2.4, first released 2026-06-23. | 4 | 2 | 4×3÷2 = 6.0 | The listing shows a ratings summary instead of "hasn't received enough ratings"; `userRatingCount` in the lookup rises above 0. |
| 6 | Write release notes that name what changed for the user (which screen or feature is new or fixed). | Listing · L-FRESH | `currentVersionReleaseDate` 2026-11-02 (recent); `releaseNotes` "Bug fixes and performance improvements." | 2 | 1 | 2×3÷1 = 6.0 | The next version's "What's New" names at least one user-facing change. |
| 7 | Localize the German storefront: German description, subtitle and screenshot captions. (Owner decision only if you'd rather stop listing German.) | Listing · L-LOCAL | `languageCodesISO2A` ["EN","DE"], page "English and German"; the `country=de` lookup returns the same English description and the same English-caption screenshot URLs as `us`. | 3 | 2 | 3×3÷2 = 4.5 | `https://itunes.apple.com/lookup?id=6778990308&country=de` returns German text; the de listing's screenshots have German captions. |
| 8 | Add an app preview whose first seconds show the face scan turning into a score (screenshot #1's moment). Previews can be up to 30 seconds, up to 3 per listing (A-PP). | Listing · L-VIDEO | The live listing's media strip starts with screenshot C01_65; no `<video>` element and no play control on the page. | 2 | 2 | 2×3÷2 = 3.0 | The listing's first media item is a preview with a play control. |

Confidence is 3 for every fix (each problem is seen directly on the listing). Ranks 5 and 6 tie at 6.0; the higher impact goes first.

**Also failing:** none — all 8 Fails are ranked above.

## Check results

### Store listing
| ID | Weight | Result | Evidence |
|---|---|---|---|
| L-TITLE | 3 | Fail | Name "Looks Max - Look Your Best" (26/30), subtitle "Your Daily Looks Maxxing Coach" (30/30). No plain statement of the core job (AI face rating); no ranking or price terms. |
| L-SHOTS3 | 3 | Pass | #1 "WHAT'S YOUR FACE SCORE?" / "AI face rating with a full feature breakdown and a plan to raise it."; #2 "FIND YOUR WEAK SPOT." / "Every feature scored, so you know exactly what to fix first."; #3 "SEE YOUR FUTURE FACE." / "Future Self shows an AI projection of your glow-up after months of work." All three show the app in use and together state the job. |
| L-SHOTSALL | 1 | Pass | Live strip: 6 screenshots (C01_65–C06_65), each a different feature (score, breakdown, future face, habits, timelapse, hair). Lookup `screenshotUrls`: 8 (C01_69–C08_69), adding "CLIMB THE LEADERBOARD." and "TALK TO A REAL COACH."; the set shown on the us web listing has only the first 6, so consider adding #7–#8 there too (up to 10 allowed, A-PP). |
| L-VIDEO | 1 | Fail | Rendered listing page: no `<video>`, no play control; first media item is screenshot C01_65. |
| L-RATING | 2 | Fail | `averageUserRating` 0, `userRatingCount` 0; page: "This app hasn't received enough ratings or reviews to display an overview." Review-prompt placement not checkable without a project folder. |
| L-DESC1 | 2 | Fail | First sentence names the job ("uses advanced AI to analyze your facial features…"), but paragraph 2 says "Only Looksmax" (a different app name), and features in screenshots #3–#6 (and lookup #7–#8) are missing from the text. |
| L-LOCAL | 1 | Fail | `languageCodesISO2A` ["EN","DE"]; the de storefront lookup returns the identical English description and the same screenshot URLs (English captions). |
| L-FRESH | 1 | Fail | `currentVersionReleaseDate` 2026-11-02, version 2.4 — recent; `releaseNotes` "Bug fixes and performance improvements." — boilerplate. |
| L-HONEST | 3 | Fail | Description: "objective, science-backed insights" (no basis shown). Screenshot #4 badge: "92% feel more confident after 3 weeks*" / "*Looks Max user survey" (no details a user can check). Screenshot #3's "+2.00 PROJECTED" is labelled "AI-generated simulation. Individual results may vary." (visible basis). Sample scores inside device frames (8.43, 5.84, 8.09) are product demos, not claims. Lookup-set #8 shows in-app text "10+ years of experience" for coaches — inside the app UI, so not counted, but make sure it's true. Possible review risk (A-RG 2.3.1(a)). |

### Onboarding
| ID | Result | Evidence |
|---|---|---|
| O-TTV, O-PERSONAL, O-PERM, O-ACT, O-SKIP, O-SHORT | Not assessed | No onboarding screenshots or project folder; the listing's marketing screenshots show the product, not the first-run flow. |

### Paywall
| ID | Result | Evidence |
|---|---|---|
| P-PLACE, P-PLANS, P-TRIAL, P-DEFAULT, P-SAVE, P-PROOF, P-CLOSE, P-RESTORE, P-LEGAL | Not assessed | No paywall screenshot or project folder; the listing only says "In‑App Purchases". The paywall was not opened (no purchases or trials). |

### Copy
| ID | Result | Evidence |
|---|---|---|
| C-VOC, C-OBJECT | Not assessed | The us review feed has no entries (`feed.entry` absent); de and gb feeds are also empty; the listing shows no ratings overview. |

## Not assessed
| Check(s) | Missing | Input that unlocks it |
|---|---|---|
| O-TTV, O-PERSONAL, O-PERM, O-ACT, O-SKIP, O-SHORT | First-run flow | Onboarding screenshots or a screen recording (`screenshots=<folder>`), or the app's project folder (`project=<folder>`) |
| P-PLACE, P-PLANS, P-TRIAL, P-DEFAULT, P-SAVE, P-PROOF, P-CLOSE, P-RESTORE, P-LEGAL | Paywall screens and copy | A paywall screenshot (`screenshots=<folder>`) or the project folder |
| C-VOC, C-OBJECT | Written reviews (none in us, de, gb) | Support emails, survey answers, or reviews once the app has some |
| L-RATING (review-prompt part only) | Where the rating prompt fires | The project folder |

## Sources
- App lookup (us): https://itunes.apple.com/lookup?id=6778990308&country=us → `data/lookup.json` (A-LOOKUP)
- App lookup (de): https://itunes.apple.com/lookup?id=6778990308&country=de → `data/lookup_de.json`
- Reviews (us): https://itunes.apple.com/us/rss/customerreviews/page=1/id=6778990308/sortby=mostrecent/json → `data/reviews.json` (A-RSS; no entries)
- Reviews (de, gb): same feed with `/de/` and `/gb/` → `data/reviews_de.json`, `data/reviews_gb.json` (no entries)
- Live listing page (subtitle, "In‑App Purchases", ratings notice, languages, media strip): https://apps.apple.com/us/app/looks-max-look-your-best/id6778990308
- Screenshots viewed in a browser (the image CDN resets curl): live set C01_65–C06_65 and lookup set C01_69–C08_69 on is1-ssl.mzstatic.com; captions in `data/screenshot-captions.json`
- sources.md IDs cited: A-PP, A-RG (2.3.1(a), 2.3.3, 2.3.7), A-HIG-RR, A-LOOKUP, A-RSS, G-LISTING; `practice` for L-FRESH