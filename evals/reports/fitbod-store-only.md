> Release test run for app-growth-audit v1.0.0 (eval case `fitbod-store-only`, first round), hand-checked on 2026-11-03: quotes traced to the saved review feed and listing, scores and ranking recomputed. The `data/` files it cites were working files and are not included. A snapshot of a public listing; it will change.

# App growth audit: Fitbod: Gym & Fitness Planner (App Store, us) — 2026-11-03

**Inputs:** https://apps.apple.com/us/app/fitbod-gym-fitness-planner/id1041517543 · screenshots: none · project: none · competitors: none · focus: all · top 10. Defaults taken: storefront `us` (from the URL); focus `all`; no onboarding/paywall evidence, so every Onboarding and Paywall check is Not assessed. **Only 6 checks failed, so this report ranks 6 fixes, not 10.** Padding the list with unverified advice would break the audit's evidence rule. The other 4 slots need onboarding and paywall evidence (see Not assessed).

**Note on screenshots:** the live listing page shows 6 screenshots (`ASO-1…6-LG.png`). Apple's lookup API returns a different set of 10 older-looking ones (`Page_1_5_SIZE`, `Slice_1…8`). Screenshot checks below are judged on the **live page set**, because that's what visitors see. The lookup set is recorded in `data/screenshot-captions.md`. The owner should confirm in App Store Connect which set is live on each device size, or whether a product-page test is running.

## Verdict
Put the app's clearest differentiator in the first three screenshots: the third slot is "CUSTOMIZE YOUR EQUIPMENT", a setup step, while the line that says what Fitbod does for a lifter ("KNOW HOW MUCH TO LIFT") sits at `listing screenshot #4`. Search results only show the first one to three images (A-PP).

## Scorecard
| Area | Score | How it was computed |
|---|---|---|
| Store listing | 59 | 100 × 10 ÷ 17 (9 of 9 checks assessed) |
| Onboarding | — | 0 of 6 checks assessed |
| Paywall | — | 0 of 9 checks assessed |
| Copy | 50 | 100 × 2 ÷ 4 (2 of 2 checks assessed) |
| **Overall** | 57 | 100 × 12 ÷ 21 (11 of 26 checks assessed) |

## Ranked fixes
| Rank | Fix | Area | Evidence | Impact | Effort | Priority | How to check it worked |
|---|---|---|---|---|---|---|---|
| 1 | Reorder the screenshot set so "KNOW HOW MUCH TO LIFT" (now #4) sits in slot 2 or 3, and move "CUSTOMIZE YOUR EQUIPMENT" (now #3) later. On the next asset refresh, make slot 1 name the job, strength or lifting workouts that plan sets, reps and weights, instead of the generic "Smart workouts built for you". | Listing · L-SHOTS3 | Live `listing screenshot #1` "SMART WORKOUTS BUILT FOR YOU"; `#2` "Took the guesswork out of making progress"; `#3` "CUSTOMIZE YOUR EQUIPMENT"; `#4` "KNOW HOW MUCH TO LIFT". None of the first three names strength or weight training, or says the app sets your weights. | 4 | 1 | 4×3÷1 = 12.0 | An App Store search for "fitbod" or "workout planner" shows the "how much to lift" screenshot in the first three. In App Store Connect, watch product page conversion rate before and after the change. |
| 2 | Start the description with the sentence that says what the app does ("Build muscle, gain strength and lose weight with a customized workout plan just for you."). Move "*Apple Editor's Choice Award Winner*" lower: the award already shows in the page's Awards badge. | Listing · L-DESC1 | The description's first line is "*Apple Editor's Choice Award Winner*", an award line in the one spot readers see without tapping "more" (A-PP: "The first sentence of your description is the most important"). | 4 | 1 | 4×3÷1 = 12.0 | The first visible line of the listing description names the job. |
| 3 | Answer the paywall and billing objection in the listing. Say plainly that Fitbod needs a subscription after the free trial (give the real trial length and plan prices, which the owner must fill in; they aren't public in the lookup), and how to cancel (iPhone Settings → Apple ID → Subscriptions). Also clean up the terms block: drop the duplicate, contradictory renewal bullets ("within 24 hours of the end" vs "within 24 hours before the end") and the outdated "iTunes Account". | Copy · C-OBJECT | 7 of the 50 most recent reviews (A-RSS) are about being required to pay, being charged, or not being able to cancel. Examples: "it made me purchase subscription and I had no way of continuing without it" (1★, 2026-10-28); "Even though I immediately canceled free trial, they charged my card" (1★, 2026-10-25); "it's not showing up in my subscription so I'm not able to cancel it" (1★, 2026-10-31). The description says only "After your free trial has ended, this app includes an auto-renewing subscription, which unlocks all premium workouts and features". "Premium" hints at a free tier, and the text gives no trial length and no cancel path. | 4 | 1 | 4×2÷1 = 8.0 | The description says up front that a subscription is needed and how to cancel. Over the next few weeks, check whether "had to pay / can't cancel" reviews come up less often in the RSS feed. |
| 4 | Write release notes that name what changed for the user, for example which Apple Watch or Beta Coach problems a version fixes, instead of "- Bug fixes and improvements". | Listing · L-FRESH | Version 8.38.0 (2026-10-27): "Release Notes for 8.38.0 - Bug fixes and improvements". Several current reviews name specific bugs that the notes could answer. | 2 | 1 | 2×3÷1 = 6.0 | The next version's notes name at least one user-visible change. |
| 5 | Address the Apple Watch reliability complaints where the listing promotes the Watch. Use the 170-character promotional text or the release notes to say truthfully what has been fixed. Don't claim a fix that hasn't shipped. | Copy · C-OBJECT (second objection) | 3 of 50 recent reviews: "Fitbod is no longer working with my Apple Watch!" (3★, 2026-10-23); "the UI struggles communicating between the app and Apple Watch. Constantly desync" (4★, 2026-10-26); "Overwrites Apple Watch workouts" (3★, 2026-11-02). Meanwhile the description says "Hit your next session with Strava, Fitbit, and Apple Watch integration", and `listing screenshot #4` shows the Watch. | 2 | 1 | 2×2÷1 = 4.0 | The promotional text or release notes mention the Watch fix. Check whether Watch complaints keep appearing in the RSS feed. |
| 6 | Add an app preview video (up to 3, each up to 30 s, per A-PP) whose first seconds show a generated workout and the weight it suggests. | Listing · L-VIDEO | The live page's media strip starts with a screenshot. There's no play control and the page has 0 `<video>` elements. | 2 | 2 | 2×2÷2 = 2.0 | The listing's first media item is a preview with a play control. |

**Also failing:** none. All 6 Fails are ranked above.

## Check results

**Store listing**
| ID | Result | Evidence |
|---|---|---|
| L-TITLE | Pass | Name "Fitbod: Gym & Fitness Planner" (29/30) and subtitle "AI Personal Trainer & Workouts" (30/30), read from the listing page. Both name the job ("fitness planner", "personal trainer", "workouts"); no ranking or price terms. |
| L-SHOTS3 | Fail | Live #1 "SMART WORKOUTS BUILT FOR YOU", #2 "Took the guesswork out of making progress", #3 "CUSTOMIZE YOUR EQUIPMENT". #3 is a setup feature, not a benefit, and the three together never say strength or weight training, or that the app picks your weights (that's #4). |
| L-SHOTSALL | Pass | Live page: 6 screenshots, each a different feature (plan, recovery map, equipment, weight logging, strength record, weekly targets). That's ≥5, but 4 of the 10 slots (A-PP) are unused. The lookup set (10 images) repeats the same "Target muscles" screen in #1 and #5. |
| L-VIDEO | Fail | Media strip seen: first item is a screenshot, no play control, 0 `<video>` elements. |
| L-RATING | Pass | `averageUserRating` 4.80672 and `userRatingCount` 288,915 (page: "289K Ratings"). Recent 50 reviews: 22×5★, 7×4★, 8×3★, 3×2★, 10×1★. No single complaint dominates (billing is the largest, at 7). Two reviews complain about repeated rating requests ("hate getting asked for a rating after each workout", 1★, 2026-10-30). Where the prompt fires can only be checked with a project folder (A-HIG-RR). |
| L-DESC1 | Fail | First line "*Apple Editor's Choice Award Winner*" is an award line. The job sentence comes second. |
| L-LOCAL | Pass | `languageCodesISO2A` EN, PT, ES. The br storefront has a localized name ("Fitbod: Treinos e Fitness"), description and screenshots (`ASO-1-Portuguese.jpg`); mx/es have "Fitbod: Rutinas Personalizadas" and `ASO-1-Spanish.jpg`. Judged on the language list alone, since there's no market info. |
| L-FRESH | Fail | Updated 2026-10-27 (recent), but the notes say only "Bug fixes and improvements". |
| L-HONEST | Pass | Claims: "Editor's Choice" is backed by the page's Awards badge, and "274,000+ Reviews" (live #1) is at or below the store's 289K ratings. Polish: the store counts *ratings*, not written reviews, so "Ratings" is the accurate word, and the five-star quote on #2 has no attribution. The lookup set's "250,000 Reviews" with five full stars sits beside a 4.8 average. Feature claims (for example "Pro fitness trainers available via email") can't be checked without the app. |

**Onboarding:** all 6 checks Not assessed.  **Paywall:** all 9 checks Not assessed.

**Copy**
| ID | Result | Evidence |
|---|---|---|
| C-VOC | Pass | Reviewers say "guides you through what you need to be doing", "it automatically increases weight as I become stronger. There's no thinking", "I don't have to plan my workout", "progressive overload thing", and "Great alternative to expensive personal trainer" (featured review). The listing uses the same ideas: subtitle "AI Personal Trainer", #2 "Took the guesswork out of making progress", #4 "KNOW HOW MUCH TO LIFT". |
| C-OBJECT | Fail | Paywall and billing (7 of 50) and Apple Watch sync (3 of 50) objections recur and aren't answered in the listing. See fixes 3 and 5. Smaller themes: Beta Coach quality (2–3 reviews), price (2), rating prompts (2). |

## Not assessed
| Check(s) | Missing | Input that unlocks it |
|---|---|---|
| O-TTV, O-PERSONAL, O-PERM, O-ACT, O-SKIP, O-SHORT | First-run flow (marketing screenshots show the product, not the flow) | Onboarding screenshots or a screen recording (`screenshots=`), or the app's project folder (`project=`) |
| P-PLACE, P-PLANS, P-TRIAL, P-DEFAULT, P-SAVE, P-PROOF, P-CLOSE, P-RESTORE, P-LEGAL | The paywall itself (the audit never starts a purchase or trial) | Paywall screenshots or the project folder. These matter here: reviews like "Has u do a bunch of stuff then at the end makes u subscribe" point at P-PLACE/P-CLOSE/P-TRIAL. |
| Review-prompt timing (part of L-RATING) | Where `requestReview` fires | Project folder |

## Sources
- https://itunes.apple.com/lookup?id=1041517543&country=us (A-LOOKUP), saved as `data/lookup.json`; also `country=de|br|mx|es` (`data/lookup_*.json`)
- https://itunes.apple.com/us/rss/customerreviews/page=1/id=1041517543/sortby=mostrecent/json (A-RSS), saved as `data/reviews.json` (50 reviews, 2026-10-19 → 2026-11-02)
- https://apps.apple.com/us/app/fitbod-gym-fitness-planner/id1041517543: page text (subtitle, "Free · In-App Purchases", awards, ratings) and media strip, viewed in a browser
- Screenshot images on is1-ssl.mzstatic.com (live `ASO-1…6-LG.png`; lookup `Page_1_5_SIZE`, `Page_2_5_SIZE`, `Slice_1…8`), viewed in a browser. Captions in `data/screenshot-captions.md`
- sources.md IDs cited: A-PP, A-RG 2.3.1(a), A-RG 2.3.3, A-RG 2.3.7, A-RG 3.1.2(c), A-HIG-RR, A-LOOKUP, A-RSS, G-LISTING; `practice` for L-FRESH, C-VOC, C-OBJECT
