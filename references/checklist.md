# Checklist

Each check has an **ID**, a **weight** (3 core · 2 important · 1 polish, see `scoring.md`), what to look for, why it matters, how to verify it, and a **source** ID from `sources.md` (`practice` = no primary source; never attach a number to it).

Result per check: **Pass**, **Fail** or **Not assessed**. Pass and Fail always carry evidence: a quote, a screenshot (file or listing position, e.g. `listing screenshot #2`), a `path:line`, or a URL. When the evidence needed isn't available, the result is **Not assessed** with the input that would unlock it. Never guess.

Thresholds in the Verify lines (e.g. "fewer than 5 screenshots") are this checklist's own pass/fail rules, not industry benchmarks; a report may quote them as rules, never as statistics.

Contents: [Store listing](#store-listing-l) · [Onboarding](#onboarding-o) · [Paywall](#paywall-p) · [Copy](#copy-c)

---

## Store listing (L)

Evidence: the store lookup/listing data and the screenshot images. Applies to every audit.

### L-TITLE · weight 3 · Title and subtitle say what the app does
- **Look for**: the name + subtitle (iOS) or title + short description (Play) name the job the app does in words a searcher would type (e.g. "face rating", "workout planner"), not only a brand or a slogan. Within limits: iOS name and subtitle 30 characters each; Play title 30.
- **Why**: these fields are what search results show and what search indexes; a slogan-only subtitle spends the space on words nobody searches.
- **Verify**: quote both fields with their character counts. Fail if neither field contains a plain description of the core job, or if a field is over its limit, or if it uses ranking/price terms ("#1", "free") (possible review risk on Play).
- **Source**: A-PP, G-META, A-RG 2.3.7

### L-SHOTS3 · weight 3 · The first 3 screenshots tell the value
- **Look for**: screenshots 1–3, read in order with only their captions, tell a stranger what the app does and why it's worth it; each shows the app in use; captions are short and readable at thumbnail size.
- **Why**: Apple: the first one to three images appear in search results when there's no preview, "so make sure these highlight the essence of your app".
- **Verify**: view the images (see SKILL.md §2 on how). Quote each caption with its position. Fail if any of the three is a splash/logo/login screen, has no caption that names a benefit, or the three together don't state the core job.
- **Source**: A-PP, A-RG 2.3.3

### L-SHOTSALL · weight 1 · All screenshot slots used, each one distinct
- **Look for**: the listing uses most of its slots (iOS up to 10) and every screenshot shows a different feature or benefit.
- **Verify**: count screenshots from the lookup (`screenshotUrls`). Fail if fewer than 5, or two screenshots repeat the same message.
- **Source**: A-PP

### L-VIDEO · weight 1 · Preview video
- **Look for**: an app preview (iOS) or promo video (Play) whose first seconds show the core action.
- **Why**: Apple: previews autoplay muted, "so make sure the first few seconds of your video are visually compelling".
- **Verify**: the lookup API does not expose previews. Pass/Fail only if you actually see the listing's media strip (a play control on the first media item) or the owner supplies the video. Otherwise **Not assessed** — unlock: a screenshot of the listing page or the video file.
- **Source**: A-PP, G-LISTING

### L-RATING · weight 2 · Rating and recent reviews
- **Look for**: an average rating and count are shown; recent reviews aren't dominated by one repeated complaint; the app asks for ratings at a moment of success.
- **Why**: "Ratings and reviews influence how your app ranks in search".
- **Verify**: quote `averageUserRating` and `userRatingCount` from the lookup; read the most recent reviews (A-RSS). Fail if there are too few ratings for the store to show a summary, or if most of the recent reviews repeat one complaint (quote 2–3). With a project folder, also check where the review prompt fires (`SKStoreReviewController`, `requestReview`, `expo-store-review`, `ReviewManager`): Fail if it never fires or fires on first launch/onboarding.
- **Source**: A-PP, A-HIG-RR

### L-DESC1 · weight 2 · The first lines of the description sell the app
- **Look for**: the first sentence states what the app does and for whom; it isn't a disclaimer, award list or keyword dump; brand names are consistent.
- **Why**: "The first sentence of your description is the most important — this is what users can read without having to tap to read more."
- **Verify**: quote the first sentence. Fail if it doesn't name the core job, or the description contradicts the listing (a different app name, features shown in screenshots but missing from the text).
- **Source**: A-PP

### L-LOCAL · weight 1 · Localization fits the audience
- **Look for**: listing languages (`languageCodesISO2A`) and in-app locales cover the markets the app targets; screenshots with text are localized for each listed language.
- **Verify**: quote the language list. Fail if the app lists a language whose listing text or screenshots are only in English (check the other storefront's lookup, e.g. `country=de`), or, with a project folder, if app locales and listing languages differ. With no market information, Pass on language list alone and say so.
- **Source**: G-LISTING

### L-FRESH · weight 1 · Updates are recent and the notes say something
- **Look for**: the current version is recent and its release notes name what changed for the user.
- **Verify**: quote `currentVersionReleaseDate` and `releaseNotes`. Fail if the last update is over a year before the audit date, or the notes are only boilerplate ("Bug fixes and performance improvements").
- **Source**: practice

### L-HONEST · weight 3 · Listing claims are honest
- **Look for**: every statistic, award, user count or "science-backed"/"clinically proven" claim in the listing or screenshots has a visible basis; screenshots show features the app really has.
- **Why**: misleading marketing "is grounds for removal" — flag as **possible review risk**, not legal advice.
- **Verify**: quote each claim with its location. Fail if a number or award has no visible basis (e.g. a percentage on a screenshot with no source), or a feature appears in screenshots but nowhere in the app (only checkable with a project folder). Sample data shown *inside* the app UI (an example user's score or percentile in a device frame) is a demo of the product, not a claim; a statistic in a caption, badge or the description, stated as a fact about users or the app ("92% feel more confident"), is a claim.
- **Source**: A-RG 2.3.1(a), A-RG 1.1.6

---

## Onboarding (O)

Evidence: user-provided screenshots or a screen recording of the first run, or the project's source (screens, routes, string files). Without either, every O check is **Not assessed** — unlock: onboarding screenshots or the app's project folder.

### O-TTV · weight 3 · Time to first value is short
- **Look for**: the number of screens from first launch to the first moment the user gets the thing they came for (e.g. their score, their first workout).
- **Why**: Apple: onboarding should be "fast, fun, and optional"; "if you try to teach too much, people can feel overwhelmed".
- **Verify**: list the screens in order with their headline (from screenshots or the navigation/route code) and count them. Fail if two or more screens that only explain (no input, no value) come back to back before the first value, or if questions whose answers aren't used yet come before the first value. State the count; don't compare it with an outside benchmark.
- **Source**: A-HIG-ONB

### O-PERSONAL · weight 2 · Personalization questions feed the result
- **Look for**: questions asked during onboarding (goal, level, preferences) and whether their answers visibly change what the user gets (plan, result, paywall copy).
- **Verify**: list the questions; find where each answer is used. Fail if a question's answer is never used later (ask fewer questions), or there are no questions while the paywall promises a "personalized" plan.
- **Source**: A-HIG-ONB ("Postpone nonessential setup flows")

### O-PERM · weight 2 · Permissions are primed and asked in context
- **Look for**: each system permission (camera, photos, notifications, tracking) is requested when the feature needs it, after a screen that explains why.
- **Why**: "wait to request permission until people actually use an app feature that requires access"; "Avoid requesting permission at launch".
- **Verify**: for each permission, cite where it's requested and the screen before it. Fail if any is requested at launch or with no explanation before it.
- **Source**: A-HIG-PRIV, A-HIG-ONB

### O-ACT · weight 3 · A clear activation moment
- **Look for**: one named moment where the user first gets the core value (score revealed, first workout logged), designed as a highlight and reached by most users.
- **Verify**: name the screen and quote its headline. Fail if no single screen delivers the core value, or if it's reachable only after payment *and* account creation with no preview of the value.
- **Source**: practice

### O-SKIP · weight 1 · Optional steps can be skipped
- **Look for**: tutorials and non-essential questions (name, preferences) have a skip; the user isn't forced to create an account before seeing value.
- **Verify**: cite skip controls. Fail if sign-up or a tutorial is required before first value with no skip.
- **Source**: A-HIG-ONB

### O-SHORT · weight 1 · Not too short either
- **Look for**: the onboarding collects what the result and the paywall depend on (goal, level), so the paywall can speak to the user's goal.
- **Verify**: Fail if the paywall or result claims personalization that onboarding never collected input for.
- **Source**: practice

---

## Paywall (P)

Evidence: paywall screenshots, or the project's paywall code and string files (prices usually come from the store at runtime: then quote the code that formats them). Without either, every P check is **Not assessed** — unlock: a paywall screenshot or the project folder. Never make a purchase or start a trial to see the paywall.

### P-PLACE · weight 3 · Placed after value is shown or previewed
- **Look for**: where the paywall appears (before onboarding, after onboarding, before or after the first result, at feature gates) and whether the user has seen or previewed the value first.
- **Verify**: cite the route/trigger. Fail if the paywall appears before the user has seen any part of the core value (not even a blurred or partial preview). Hard vs soft paywall is the owner's choice: report it, don't fail it alone.
- **Source**: practice, A-RG 3.1.2(c)

### P-PLANS · weight 3 · Plans are clear
- **Look for**: each plan's name, billing period and full price are visible together; the amount billed is the most prominent price; per-week/per-month breakdowns are smaller.
- **Why**: Apple: "the amount that will be billed must be the most prominent pricing element"; Play lists annual plans shown mainly as a monthly cost as a violation.
- **Verify**: quote each plan's displayed text or the format string. Fail if a breakdown price is larger or more prominent than the billed amount, or a plan's billing period isn't stated. Possible review risk.
- **Source**: A-SUB, G-SUB, A-RG 3.1.2(c)

### P-TRIAL · weight 3 · Trial terms stated plainly
- **Look for**: if there's a trial: its length, the price after it, and that it renews automatically, next to the button. If there's no trial: the button doesn't imply one.
- **Verify**: quote the trial text. Fail if trial length or after-trial price is missing or only in fine print. If the store config and the app disagree (e.g. docs promise a trial the code filters out), Fail and quote both. Possible review risk.
- **Source**: A-SUB, G-SUB

### P-DEFAULT · weight 1 · Default plan is a deliberate, honest choice
- **Look for**: which plan is pre-selected, and that the pre-selection is visible (not a hidden checkbox).
- **Verify**: cite the default. Fail only if the pre-selected plan isn't visibly selected or the button text doesn't match it.
- **Source**: practice

### P-SAVE · weight 2 · Annual savings framed honestly
- **Look for**: "Save X%" computed from the real prices shown, against a named plan, displayed smaller than the annual price.
- **Verify**: quote the badge and how X is computed (code or arithmetic from shown prices). Fail if the percentage is hard-coded, compared against an unnamed or unshown plan, or more prominent than the billed price.
- **Source**: A-SUB, G-SUB

### P-PROOF · weight 2 · Social proof is honest
- **Look for**: ratings, user counts, testimonials and statistics on the paywall, and whether each matches a verifiable source (store rating, a cited study).
- **Verify**: quote each item. Fail if a number has no source the user can see (e.g. a hard-coded percentage), or a rating/count doesn't match the store lookup. With a project folder, also trace every personal number shown on or just before the paywall (a score, a "potential", a percentile) to the code that computes it: Fail if any part of it comes from something other than the user's own data (a random value, a device or install ID, a fixed constant) while the screen presents it as their result. Possible review risk.
- **Source**: A-RG 2.3.1(a), A-RG section 3 intro

### P-CLOSE · weight 3 · A visible way out
- **Look for**: a close/dismiss control visible on arrival (not delayed, not tiny or faded), or another clear way to continue without paying.
- **Why**: Play's policy flags a "Dismiss button is missing or not clearly visible"; Apple requires clearly describing what the user gets before asking them to subscribe.
- **Verify**: cite the control (or quote the code comment that removes it). Fail if there's no visible way out on a paywall the user didn't ask to open. A hard paywall at the end of onboarding is the owner's choice, but say it's a **possible review risk** on Play and name the trade-off.
- **Source**: G-SUB, A-RG 3.1.2(c)

### P-RESTORE · weight 2 · Restore purchases
- **Look for**: a "Restore Purchases" control on the paywall (and in settings).
- **Verify**: quote the label and cite where it's rendered. Fail if missing. Possible review risk.
- **Source**: A-RG 3.1.1, A-SUB

### P-LEGAL · weight 2 · Terms, privacy and auto-renew disclosure
- **Look for**: links to Terms of Use and Privacy Policy on the paywall, plus text saying the subscription renews automatically and how to cancel.
- **Verify**: quote the links and disclosure text. Fail if any is missing. Possible review risk.
- **Source**: A-RG 5.1.1(i), A-SUB, G-SUB

---

## Copy (C)

Evidence: the listing text, paywall/onboarding copy, and recent reviews (A-RSS). Needs written reviews: with none, both checks are **Not assessed** — unlock: reviews from another storefront, support emails or survey answers.

### C-VOC · weight 2 · Listing and paywall use the users' words
- **Look for**: the words reviewers use for the app's benefit and their problem (quote 3–5 reviews), and whether the subtitle, first screenshots and paywall headline use the same words.
- **Verify**: put review phrases next to the listing/paywall phrases. Fail if the users' main words appear nowhere in the listing or paywall.
- **Source**: practice

### C-OBJECT · weight 2 · Recurring objections are answered
- **Look for**: complaints that repeat in recent reviews (price surprise, "can't use without paying", cancel trouble, crashes) and whether the listing or paywall answers them truthfully.
- **Verify**: count how many of the recent reviews raise the objection and quote 2–3. Fail if an objection raised by several reviews is not answered anywhere (e.g. the description doesn't say a subscription is required while reviews complain about it).
- **Source**: A-RG 3.1.2(c), practice
