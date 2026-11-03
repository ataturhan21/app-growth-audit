# Sources

Every check in `checklist.md` cites one of these by ID, and **every number a report states must appear here with its source**. A number that isn't on this page (a conversion lift, a benchmark, an "industry average") stays out of the report. Quotes are short excerpts, checked on 2026-11-03; re-open the link when a report depends on one, because store rules change.

## Apple

| ID | Source | What it supports (short quote or fact) |
|---|---|---|
| A-PP | [App Store product page](https://developer.apple.com/app-store/product-page/) | App name **30** characters; subtitle **30** characters; keywords **100** characters; promotional text **170** characters; up to **10** screenshots; up to **3** app previews, each up to **30** seconds. "the first one to three images will appear in search results when no app preview is available, so make sure these highlight the essence of your app." "The first sentence of your description is the most important". "Ratings and reviews influence how your app ranks in search". Ratings can be requested up to **3** times in a **365**-day period. |
| A-SUB | [Auto-renewable subscriptions](https://developer.apple.com/app-store/subscriptions/) | Sign-up screen must include "Full renewal price, shown clearly and prominently" and "A way for current subscribers to sign in or restore purchases"; "the amount that will be billed must be the most prominent pricing element in the layout"; "clearly indicate how long the free trial lasts and the price billed once the free trial is over"; savings or per-period breakdowns "should be displayed in a subordinate position and size to the annual price"; "always make it easy for people to access the system-provided management UI where they can cancel". |
| A-RG | [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/) | 2.3.3 "Screenshots should show the app in use"; 2.3.7 don't pack metadata with "trademarked terms, popular app names, pricing information, or other irrelevant phrases"; 2.3.1(a) misleading marketing "is grounds for removal"; 3.1.1 "make sure you have a restore mechanism"; 3.1.2(a) subscription period "must last at least seven days"; 3.1.2(c) "Before asking a customer to subscribe, you should clearly describe what the user will get for the price"; 5.1.1(i) privacy policy link "within the app in an easily accessible manner"; section 3 intro: manipulating reviews with "incentivized, filtered, or fake feedback" may lead to removal from the developer program. |
| A-HIG-ONB | [HIG: Onboarding](https://developer.apple.com/design/human-interface-guidelines/onboarding) | "design a flow that's fast, fun, and optional"; "Teach through interactivity"; "if you try to teach too much, people can feel overwhelmed"; "Postpone nonessential setup flows or customization steps"; permission requests in onboarding give "the opportunity to show people why your app or game needs their permission". |
| A-HIG-PRIV | [HIG: Privacy](https://developer.apple.com/design/human-interface-guidelines/privacy) | "Request permission only when your app clearly needs access"; "Ideally, wait to request permission until people actually use an app feature that requires access"; "Avoid requesting permission at launch unless the data or resource is required for your app to function." |
| A-HIG-RR | [HIG: Ratings and reviews](https://developer.apple.com/design/human-interface-guidelines/ratings-and-reviews) | "Ask for a rating only after people have demonstrated engagement"; "Avoid asking for a rating on first launch or during onboarding"; the system limits the prompt to **three** occurrences per app within a **365**-day period. |
| A-LOOKUP | `https://itunes.apple.com/lookup?id=<id>&country=<cc>` (Apple's public lookup endpoint; fields as observed in its JSON) | Returns name, description, screenshot URLs, rating, rating count, version, release date, release notes, languages and price. It does not return the subtitle, in-app purchase prices or preview videos. |
| A-RSS | `https://itunes.apple.com/<cc>/rss/customerreviews/page=1/id=<id>/sortby=mostrecent/json` | Public feed of the most recent written reviews (up to **50** per page) with rating, date, title and text. |

## Google

| ID | Source | What it supports |
|---|---|---|
| G-META | [Play metadata policy](https://support.google.com/googleplay/android-developer/answer/9898842) | "Your app title must be 30 characters or less."; don't use text in the title, icon or developer name "that indicate store performance or ranking" (e.g. "#1"), or price and promotional terms (e.g. "free for limited time only"). |
| G-LISTING | [Play store listing best practices](https://support.google.com/googleplay/android-developer/answer/13393723) | Short description up to **80** characters; full description up to **4,000** characters. |
| G-SUB | [Play subscriptions policy](https://support.google.com/googleplay/android-developer/answer/9900533) | "clearly and explicitly disclosing your offer terms, the cost of your subscription, the frequency of your billing cycle"; violations include "Annual subscriptions that most prominently display their pricing in terms of monthly cost", offers "that do not clearly explain how long the free trial or introductory pricing will last", and an example flagged because the "Dismiss button is missing or not clearly visible"; "include in your app access to an easy-to-use, online method to cancel". |

## Context, not evidence

| ID | Source | Use |
|---|---|---|
| RC-AGA | RevenueCat, App Growth Annual 2026 talks "Why your app's marketing stalls, and what to fix first" and "The big app roast: paywall and lifecycle teardowns" | Inspiration for the checklist's scope (listing → onboarding → paywall → lifecycle). Not cited for any number or rule. |

## Checklist items without a primary source

These checks are judgment calls drawn from common practice. A report may include them, but marks the source as `practice` and never attaches a number to them:

- L-FRESH (recent updates with meaningful release notes)
- O-ACT (a single, named activation moment)
- O-SHORT (onboarding so short it skips the setup the paywall depends on)
- P-PLACE (paywall placed after the user has seen value; Apple's 3.1.2(c) only requires describing what the user gets)
- P-DEFAULT (which plan is pre-selected)
- C-VOC (listing and paywall words match review words)
- C-OBJECT (recurring review objections answered; partly backed by 3.1.2(c))
