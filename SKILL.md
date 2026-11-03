---
name: app-growth-audit
description: "Audit a mobile subscription app's App Store or Google Play listing, screenshots, onboarding and paywall against an evidence-based checklist, then return the top 10 fixes ranked by impact × confidence ÷ effort, each citing its evidence (a quote, screenshot, file:line or URL). Use whenever the user wants their app's store listing, screenshots, ASO, onboarding, paywall, trial or subscription conversion reviewed, asks 'why isn't my app growing', 'review my paywall', 'audit my app's store listing', 'roast my app', or pastes an apps.apple.com or play.google.com link and asks what to fix — even if they don't say 'audit'. Accepts a store URL or app name, folders of screenshots, an optional local app project (read-only) and competitor URLs. Read-only: never logs in, buys, or edits the app."
argument-hint: "<store URL | app name> [screenshots=<folder>] [project=<folder>] [vs <competitor URLs>] [listing|onboarding|paywall|all] [top=<N>]"
---

# App growth audit: find the fixes worth doing first

Audit a subscription app the way a stranger meets it — **store listing → screenshots → onboarding → paywall** — and return a short, ranked list of fixes. The value of this audit is that every finding can be checked: each one cites evidence the reader can open, and each number comes from a listed source. An audit full of plausible-sounding advice nobody can verify is worse than a short one that's right, so when evidence is missing the answer is **Not assessed**, never a guess.

**Arguments** (from `ARGUMENTS: …` or the user's message; parse what's there, default the rest, never stop to ask):

| Input | How to recognize it | Default |
|---|---|---|
| App | an `apps.apple.com/…/id<digits>` or `play.google.com/store/apps/details?id=<package>` URL, or an app name | required; with only a name, resolve it (below) |
| Screenshots | a local folder of images or screen-recording frames (`screenshots=`, or a folder path the user calls screenshots/recording) | none |
| Project | a local app source folder (`project=`, or a folder path containing `package.json`, `*.xcodeproj`, `build.gradle`, `pubspec.yaml`) | none |
| Competitors | further store URLs (`vs …`, `compare with …`) | none |
| Focus | `listing`, `onboarding`, `paywall`, `all` | `all` |
| Count | `top=N` or a standalone integer 1–30 | 10 |
| Storefront | a 2-letter country (`country=de`) or the URL's `/us/` segment | `us` |

State every default you took in the report's **Inputs** line, so the reader knows what was and wasn't looked at.

## Ground rules (they still apply after context is summarized)

- **Evidence or Not assessed.** Every Pass and Fail cites a quote, a screenshot (file name, or listing position like `listing screenshot #2`), a `path:line`, or a URL. If you can't see it, it's Not assessed with the input that would unlock it.
- **No invented numbers.** A number (limit, length, benchmark, statistic, lift) appears only if it's in [references/sources.md](references/sources.md) with its source, or is a fact read from the evidence (a rating, a price, a screen count). This includes numbers inside a suggested fix: write "up to 30 seconds" (sourced), not a range you remember ("15–30 s"). Never estimate conversion lifts or revenue.
- **Public pages only.** No logins, purchases, trials, account creation, or scraping beyond the public listing, lookup and review feeds. Don't start the app's payment flow to see a paywall.
- **Project folders are read-only.** Read code and string files; never edit, commit, install, build, or run scripts in them. Quote at most a short line from internal files; never copy secrets, keys, tokens or config values into the report (name them only).
- **Not legal advice.** Store-guideline problems are labelled **possible review risk**, citing the guideline, never "illegal" or "will be rejected".
- **Owner decisions stay proposals.** Changes to pricing, the offer, positioning, or adding a feature are ranked but labelled **Owner decision**.
- **Honest growth.** Never recommend dark patterns: fake urgency, hidden close buttons, invented social proof, confirmshaming, pre-checked upsells.

## 1. Resolve the app

- **App Store URL** → take the digits after `id`. **App name only** → `https://itunes.apple.com/search?term=<name>&entity=software&country=<cc>&limit=5`; pick the exact name match (else the top result) and say which in Inputs.
- **Google Play URL** → the `id=` package name. **Name on Play** → search isn't public as an API; ask nothing, use the App Store if the app exists there, otherwise say the Play listing needs a URL.

## 2. Gather evidence

Save everything under the session scratchpad (`<scratchpad>/app-growth-audit/<app-slug>/`), never in the user's project. On Windows, keep that path short and use absolute paths rather than `cd` into deep folders: paths past 260 characters break `git`, Python and the shell itself.

**App Store**
1. `curl -s "https://itunes.apple.com/lookup?id=<id>&country=<cc>"` → `trackName`, `description`, `screenshotUrls`, `averageUserRating`, `userRatingCount`, `version`, `currentVersionReleaseDate`, `releaseNotes`, `languageCodesISO2A`, `formattedPrice`, `primaryGenreName`, `sellerName`. (On Windows, run Python with `PYTHONIOENCODING=utf-8` when printing this text.)
2. Recent reviews: `curl -s "https://itunes.apple.com/<cc>/rss/customerreviews/page=1/id=<id>/sortby=mostrecent/json"` → up to 50 reviews (`feed.entry`; absent when there are none). Tally ratings and recurring complaints.
3. The **subtitle** and the in-app purchase flag aren't in the lookup: read them from the listing page (`apps.apple.com/<cc>/app/id<id>`) with a browser tool's page-text reader or `WebFetch`. If both fail, L-TITLE is judged on the name alone and says so.
4. **Screenshots — look at the images; don't infer them from file names.** The lookup's `screenshotUrls` can be a different or older set than what the live listing shows (often another device size), so when you can render the listing page, judge the screenshot checks on the **live page's media strip** (its `<img>`/`<source>` URLs, in order) and note the lookup set if it differs. Try in order: (a) download each URL (replace the trailing `<w>x<h>bb.jpg` with `392x696bb.jpg`) with `curl` into the scratchpad and `Read` it; (b) if downloads fail (some networks reset non-browser connections to the image CDN), open each image URL in a browser tool and screenshot it, using your own tab if other agents may share the browser; (c) if neither works, L-SHOTS3/L-SHOTSALL/L-HONEST are Not assessed — unlock: save the screenshots into a folder and pass `screenshots=`. Record each caption verbatim with its position.

**Google Play** — fetch `https://play.google.com/store/apps/details?id=<pkg>&hl=en&gl=<cc>` (page text) for title, short description, description, rating, review count, "Updated on", and screenshot images (view them as above). Written reviews visible on the page count as recent reviews.

**Screenshots folder** — `Read` every image in name order. Sort them into listing / onboarding / paywall by what they show; cite them by file name.

**Project folder** (read-only) — find, by searching names and strings (`onboarding`, `paywall`, `subscribe`, `trial`, `restore`, `requestPermission`, `requestReview`, `Purchases`, `StoreKit`, `BillingClient`):
- the navigation order from first launch to the first result (route files, a flow/step registry) — list screens with their headline string and `path:line`;
- string/locale files for onboarding and paywall copy (quote from the source of truth, not a test);
- paywall: when it's shown, plans and how prices are rendered (store-provided vs hard-coded), default plan, trial handling, savings badge logic, social proof strings, close control, restore, terms/privacy links, auto-renew text;
- permission requests and what screen precedes each; the review-prompt call site;
- the in-app locales.
Prefer what ships: if docs and code disagree, the code wins, and the disagreement is itself evidence (quote both). Skip dev-only code (`__DEV__`, debug flags) and never describe unreleased features in a report meant to be shared.

**Competitors** — run the listing checks (§2 App Store/Play steps 1–4) on each; use them only for side-by-side contrast in fixes ("Competitor X's subtitle names the job: '…'"), never as benchmarks.

## 3. Check

Read [references/checklist.md](references/checklist.md) and run every check in the focus areas. For each: **Pass / Fail / Not assessed**, the evidence, and for Fail the concrete fix. Rules that matter most:
- Onboarding (O-) and paywall (P-) checks need onboarding/paywall screenshots or a project folder. With neither, **every** O and P check is Not assessed — don't fill them from the listing's marketing screenshots, which show the product, not the flow.
- Copy checks (C-) need written reviews; quote the reviewers' own words.
- A screenshot claim (a percentage, "science-backed", an award) with no visible basis fails L-HONEST; when a project folder shows the same claim's internal source, say whether that source is something a user could verify.

## 4. Score and rank

Follow [references/scoring.md](references/scoring.md) exactly: area score = weighted share of assessed checks passed; fix priority = impact (1–5) × confidence (1–3) ÷ effort (1–3), ties by impact, then lower effort. Show the arithmetic so the reader can recompute it. Keep the top N; list the remaining Fails in one line each under "Also failing".

## 5. Write the report

Write the report to `<scratchpad>/app-growth-audit/<app-slug>-<yyyymmdd>.md` (or the path the user named) and show it in chat. Use this structure exactly:

```markdown
# App growth audit: <app name> (<store>, <storefront>) — <yyyy-mm-dd>

**Inputs:** <store URL> · screenshots: <folder | none> · project: <folder | none> · competitors: <list | none> · focus: <focus> · top <N>. Defaults taken: <list>.

## Verdict
<One line: the single most important fix and why, with its evidence.>

## Scorecard
| Area | Score | How it was computed |
|---|---|---|
| Store listing | 62 | 100 × 13 ÷ 21 (8 of 9 checks assessed) |
| Onboarding | — | 0 of 6 checks assessed |
| Paywall | … | … |
| Copy | … | … |
| **Overall** | … | … |

## Ranked fixes
| Rank | Fix | Area | Evidence | Impact | Effort | Priority | How to check it worked |
|---|---|---|---|---|---|---|---|
| 1 | <specific change; "Owner decision:" prefix if it changes price/offer/positioning/features> | Listing · L-SHOTS3 | <quote / screenshot #n / path:line / URL> | 5 | 1 | 5×3÷1 = 15.0 | <observable check: what to look at after the change, e.g. "subtitle reads …", "paywall shows X on arrival", a store-console metric to watch — no predicted numbers> |

(With a project folder, add a **File to change** column with the `path:line` to edit.)

**Also failing:** <ID — one line each>

## Check results
<Per area, a compact table: ID | Result | Evidence.>

## Not assessed
| Check(s) | Missing | Input that unlocks it |
|---|---|---|

## Sources
<Every URL fetched and every file read, plus the sources.md IDs cited.>
```

Then reply in chat with the Verdict line, the top 3 fixes (one line each), the scorecard, and the report path.

## Examples

- "audit my app's store listing https://apps.apple.com/us/app/…/id123" → listing + copy checks from public data; onboarding and paywall Not assessed, with "pass `project=` or onboarding/paywall screenshots" as the unlock.
- "review my paywall, screenshots are in ~/Desktop/paywall" → focus `paywall`, P checks from the images, listing skipped (state it).
- "why isn't my app growing? repo is ./ios-app, store link …" → focus `all`, project read-only, fixes include a File to change column.
