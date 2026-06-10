# jekcms — Changelog

All notable changes to jekcms. This file is generated from a single
source of truth and mirrors the public changelog at https://jekcms.com/changelog

_Do not edit by hand — edit `marketing-includes/changelog-data.php`, then run_
_`php tools/gen-changelog-md.php` and commit._

---

## [2.16.23] - 2026-06-10  ·  _Patch_
**Category Archive Filter Fix**

### Fixed
- Category pages now show only their own posts — on themes that query archives by category ID, the post list ignored the category filter and showed every published post. The core query layer now accepts both category ID and slug, so every category archive lists exactly the posts that belong to it.

---

## [2.16.22] - 2026-06-10  ·  _Minor_
**Invoicing, Customer Portal Language & Support System**

### Added
- Real PDF invoices — admins can now generate an invoice for any order and email it to the customer, and customers can download a proper PDF from their portal. Invoices render with full Turkish characters and work on any shared host (no server extensions required).
- Turkish-law VAT handling — domestic sales carry 20% VAT (KDV); sales to customers outside Turkey are treated as a VAT-exempt service export and the exemption note is printed on the invoice automatically.
- Company billing settings — a new admin screen for your seller details (company title, tax office, tax number, address, IBAN) that appear on every generated invoice.
- Billing profile for customers — buyers can now enter their tax number, address and country so their invoices are complete and the correct VAT rule is applied.

### Improved
- Customer portal fully bilingual — every page of the customer portal (orders, licenses, invoices, support, profile, sign-in/up) now follows the selected language, so Turkish users no longer see stray English labels.

### Fixed
- Support tickets hardened — fixed an issue where a second ticket from a customer could fail, added missing attachment storage, corrected priority handling, and customers now get an email when staff reply (and staff get one on new tickets).
- Portal pages that referenced old data fields now load correctly — order detail, new-ticket and invoice pages were updated to the live data model.
- Two admin tools gained CSRF protection and several blog/theme pages had social-share image and metadata issues corrected for better SEO.

---

## [2.16.21] - 2026-06-09  ·  _Minor_
**Automatic Internal Links on Publish**

### Added
- New posts get internal links automatically when published — the moment a post goes live (manual publish, scheduled date, or content queue), 3-5 contextual links to your existing published posts are added inside it, so you no longer have to run the linker site by site. Only published posts are used as link targets; queued or scheduled items are never linked.

---

## [2.16.20] - 2026-06-06  ·  _Minor_
**Security Hardening Pass: Payment, CSRF, Uploads, SSRF, API**

### Fixed
- Marketing homepage hardening guard aligned — the direct-access guard in the constants file only accepted one context flag, while the marketing site and update-server bootstrap use different ones; the guard now matches the loader so the public site renders normally
- Payment webhook is now fail-closed — the iyzico webhook accepted an event when no signature header was present; it now rejects any unsigned or invalid-signature webhook (matching the Stripe gateway), closing an unauthenticated path to marking orders paid
- One-click (GET) CSRF on admin actions closed — central CSRF enforcement now also covers authenticated GET action handlers (delete/toggle/activate), so a forged link or image tag can no longer trigger destructive admin actions
- API input is column-whitelisted — the categories/tags update endpoints now accept only known fields, removing an identifier-injection vector from attacker-controlled JSON keys
- SVG uploads disabled — SVG is no longer an allowed upload type (it can carry scripts and was served inline), eliminating a stored-XSS vector; standard image formats are unaffected
- SSRF guards added to server-side fetchers — bulk-import and remote content-image fetching now validate the URL against private/loopback/metadata ranges and no longer follow redirects
- Customer portal forms fixed — the CSRF token field referenced a non-existent method (so it rendered empty); corrected to the proper token, and a reflected status parameter in pagination links is now URL-encoded
- Removed a temporary password-reset utility from the web root that was reachable without authentication

---

## [2.16.19] - 2026-06-06  ·  _Patch_
**In-Article Images Now Match on Items That Already Have a Pinterest Slot**

### Fixed
- Image matching no longer skips the in-article photos when an item only had a Pinterest slot — after a re-import added a Pinterest slot to an item that had no content image plan, the matcher mistook that lone Pinterest slot for a full plan and never built one from the article's headings, so the cover and pin matched but the in-article images (img02, img03…) stayed in temp. The matcher now ignores the Pinterest slot when deciding whether a content plan exists, builds the heading-based plan when needed, and preserves the existing Pinterest slot

---

## [2.16.18] - 2026-06-06  ·  _Minor_
**Re-Importing JSON Now Updates Existing Queue Items (Pinterest + Prompts)**

### Improved
- Re-importing a JSON now enriches items already in the queue instead of skipping them — previously a duplicate (same source id) was skipped entirely, so content imported before a feature existed could never gain it. Now a re-import fills in any empty image prompts from the new file and adds the Pinterest brief (hook, title, description, tags, image prompt) and pin slot — while preserving already-matched image URLs, the schedule, and any manual edits. The import result reports how many items were updated

---

## [2.16.17] - 2026-06-06  ·  _Patch_
**Content Queue Image Column Now Counts the Matched Cover**

### Fixed
- The image-status column no longer shows “—” when the cover is actually matched — items imported without a full image plan store their cover in the `featured_image` column rather than the plan, so the queue list read “no images” even though the cover thumbnail was clearly set (and the image dialog said “1/1 matched”). The column now counts a column-matched cover too, so the list and the dialog agree

---

## [2.16.16] - 2026-06-06  ·  _Minor_
**End-to-End Pinterest Pins: Custom Copy, Per-Category Boards, and Baked Designs**

### Added
- Per-article Pinterest copy now publishes — a pin's title and description come from the imported brief (`_pinterest_title` / `_pinterest_description`) instead of the generic post title and template, so each pin reads the way it was written
- Pins route to the matching board automatically — a pin is posted to the board whose name matches the article's category (with the connected account's default board as fallback), so a multi-topic site keeps its Pinterest boards organized with no manual selection
- Designed-in-full pins are supported — when the image already bakes in its own headline and domain bar, the CMS skips its own stamp (`stamp:false`), so there is never a double bar

### Improved
- The AI content wizard now writes premium pin briefs — when Pinterest is enabled, it produces an editorial brief (short hook, ≤100-char title, ≤500-char keyword-rich caption, tags, the `<slug>-pinterest` filename, and a full split-layout image prompt with the site domain baked in) ready for image generation

---

## [2.16.15] - 2026-06-05  ·  _Minor_
**Hands-Off Pinterest Pins and Bulk Image Matching in the Content Queue**

### Added
- Pinterest pins now match automatically — drop a `<slug>-pinterest.jpg` into the uploads `temp` folder alongside your article images and the queue picks it up on the next “Match Images” run, stamps your site’s domain bar onto it, and attaches it to the post. No more uploading pins one at a time
- Pinterest captions travel with the content — the import schema now carries a pin hook (the headline on the image), a meta description (the caption shown under the pin) and tags, and writes them to the published post so a Pinterest publisher can fill those fields without guesswork
- An image-status column in the queue list — every row shows how many article images are matched (e.g. 2/3) and whether a Pinterest pin is present and matched, at a glance

### Improved
- The content queue list was redesigned — the action buttons (view, images, publish, delete) are now a compact, single-row icon group instead of a stack that overflowed the column, and the new image-status chips are monochrome and uncluttered
- Image matching now shows a real progress bar — a clean progress window reports matched count, percentage and a live log as it processes the temp folder in batches, instead of a number ticking in a button
- Content Studio is now the calm starting point for publishing — the dashboard gathers the publishing calendar, queue health, next action and entry points for AI draft, planned batches and content packs into one compact two-language screen
- Imports are more forgiving — image entries that use `role`/`prompt` instead of `slot`/`image_prompt` are now understood, so content generated by different tools imports correctly without hand-editing the JSON

---

## [2.16.14] - 2026-06-04  ·  _Patch_
**Admin Sessions No Longer Drop After a Few Hours Idle**

### Fixed
- You stay signed in until you actually sign out — even with the session cookie and garbage-collection lifetimes already raised to 30 days, an inactivity check was still destroying the session after ~2 hours of no activity (its threshold constant was undefined, so it fell back to a 2-hour default). The idle limit now matches the 30-day session lifetime, so leaving the dashboard open and coming back hours later keeps you logged in

---

## [2.16.13] - 2026-06-04  ·  _Patch_
**Admin Language Consistency — Plugin Text Now Follows TR/EN**

### Fixed
- The newer plugins no longer leak the wrong language in the admin — Google Console, Traffic & Distribution, and parts of Social Publishing hardcoded their interface text in a single language (mostly Turkish), so it showed Turkish in the English admin (and vice-versa). All of these are now bilingual and follow the admin language setting
- Google Console’s plugin-list description is now bilingual — it was missing from the localized description map and fell back to the Turkish manifest text
- The Two-Factor Authentication card in Settings → Security is now bilingual — its labels, steps, badges and buttons were Turkish-only
- Social Publishing platform help/how-to, cost and warning texts are now bilingual for all platforms — these registry strings rendered in a single language regardless of admin locale

---

## [2.16.12] - 2026-06-04  ·  _Patch_
**Performance (N+1) and Security/SEO/Plugin Hardening**

### Improved
- List pages issue far fewer database queries — loading a post list with relations ran 6 queries per post (author, categories, tags, meta, SEO, comments); a 12-post page hit ~72 queries. It now batches all of them into 6 total via IN() lookups
- Image dimension lookups no longer scan the media table on every render — the per-image width/height query used a leading-wildcard LIKE (full-table scan per image); it now uses exact-path matching plus a per-request cache
- Saving a post no longer wipes the entire object cache — cache invalidation is now targeted to the affected namespaces instead of a global flush
- Faster LCP on article pages — the hero/featured image on travel and health single-post templates now carries fetchpriority="high"

### Fixed
- Client IP detection can no longer be spoofed to evade blocks — forwarded headers are now accepted only when they carry a public IP, so an attacker cannot inject an internal/loopback address to bypass IP blocking or frame another IP
- Redirect Manager blocks dangerous redirect schemes — javascript:/data:/vbscript: targets are refused at emit time
- Admin error messages no longer leak internals — Security Center and Redirect Manager now show a generic message and log the detail
- Cross-domain Sitemap line removed from the shipped robots.txt fallback — robots is served dynamically with the site’s own domain; the static fallback no longer carries a hardcoded foreign domain
- Google Console snippets can no longer double-inject — the head injector is guarded against firing on both head hooks
- Removed the misleading dead Pinterest-template dropdown in Social Publishing settings (it was never read)

---

## [2.16.11] - 2026-06-04  ·  _Patch_
**Deep Audit Fixes — CSRF Enforcement, Cache, SEO & Systems**

### Fixed
- CSRF protection is now actually enforced across the admin — the validation helper returned a boolean that nearly every admin/AJAX endpoint discarded, so forged cross-site requests were silently accepted. Validation now blocks state-changing authenticated requests centrally (clean 419, JSON for AJAX) without affecting public forms or page rendering
- "Clear Cache" buttons work again — they called a method that did not exist and fataled (purging nothing). Added the missing prefix-delete method and hardened the handler
- Sitemap index no longer miscounts pages as posts — the posts-sitemap presence/lastmod now filter on post type, fixing false "empty posts sitemap" and wrong freshness signals
- Update manifest hash guard is no longer a no-op — the signed update manifest now exposes the core package hash under the field the client checks
- Social Publishing "Hold for approval" no longer silently stops publishing — held items now appear in the queue with one-click Approve / Approve-All / Cancel actions
- Traffic & Distribution now verifies TLS — IndexNow/WebSub/Web-Push calls had certificate verification disabled; enabled to prevent MITM

---

## [2.16.9] - 2026-06-04  ·  _Patch_
**Security Center Now Matches the Admin Design System**

### Fixed
- The Security Center looked disconnected from the rest of the admin — it shipped its own stylesheet with hardcoded light-mode colors (white cards, grey borders) instead of the admin’s shared design tokens, so it ignored dark mode and its tabs/cards/tables didn’t match the other panels. Every color now uses the admin theme variables, so it adapts to dark/light and looks like one consistent product. Status indicators keep a subtle tinted badge instead of solid blocks, and the brand wordmark was corrected to lowercase

---

## [2.16.8] - 2026-06-04  ·  _Patch_
**Strip Byte-Order Marks From Core Files — Fixes Admin Layout & AJAX**

### Fixed
- Admin pages no longer render with broken styling — several core PHP files (bootstrap, constants, helpers, theme functions) carried an invisible UTF-8 byte-order mark (BOM) before their opening tag. That BOM was emitted before the document’s doctype, which forced browsers into "quirks mode" and broke list/table layouts across the admin. The BOM has been stripped from every PHP file fleet-wide
- AJAX actions no longer fail with a JSON parse error — the same BOM was prepended to JSON responses (e.g. "Match Images"), so the browser threw `Unexpected token … is not valid JSON`. With the BOM removed, responses are clean JSON again

---

## [2.16.7] - 2026-06-04  ·  _Patch_
**Match Images — Build Article Image Plans From Your Generated Files**

### Fixed
- Bulk image matching now actually imports your files — the media importer used PHP’s upload-only move function, which always fails for files already on the server (e.g. images you place in the uploads/temp folder). A server-side "sideload" path now imports those files correctly, and a valid uploader id is always supplied so the database insert no longer fails outside a browser session
- "Match Images" understands multi-image articles — drop files named `{slug}-img01..04` in the temp folder and the matcher attaches them as the article’s image plan: image 01 becomes the featured image and the rest are placed in the body after the article’s headings. When the article already has a plan, empty slots are filled in order
- Admin thumbnails resolve relative image paths — queue list and calendar previews now prefix the uploads URL for plan images stored as relative paths, so the thumbnail shows instead of a broken image

---

## [2.16.6] - 2026-06-04  ·  _Patch_
**Match Images — In-Memory Matching, Seconds Instead of Minutes**

### Fixed
- "Match Images" now finishes in seconds on large queues — the previous version ran two full-table `LIKE '%slug%'` scans per item and re-normalized every media filename for every item, which on a queue of hundreds against thousands of media files took minutes and hit a server gateway timeout (the generic "server error"). The media library is now normalized once and all items are matched in memory — no per-item database queries, no repeated work

---

## [2.16.5] - 2026-06-04  ·  _Patch_
**Match Images No Longer Times Out on Large Queues**

### Fixed
- "Match Images" no longer fails with a generic server error on large queues — with hundreds of queued items and thousands of media files, the slug-to-media scan could exceed PHP’s execution limit and return a raw 500. It now skips items that already have an image attached through the image-matching flow (so nothing is re-scanned needlessly), and the time limit is raised for the bulk pass
- Queue actions now always return a readable error — any failure in a content-queue action is converted to a proper JSON message instead of a raw 500 page, so the browser shows the real reason rather than a generic "server error"

---

## [2.16.4] - 2026-06-04  ·  _Patch_
**Reliable Manual Publishing — No More "Spinning then Failed"**

### Fixed
- Publishing no longer crashes when a session cannot start — if output had already begun (e.g. a slow image URL emitting a warning), the session layer threw a fatal "headers already sent" error that aborted the publish even though the post itself was fine. The session now degrades gracefully (logs and continues, fail-closed) instead of crashing background work
- A dead or slow featured-image URL can’t freeze the publish anymore — image download now has an 8-second connect and 25-second total cap (was 60s with no connect timeout), the single biggest cause of the publish button spinning for up to a minute. A failed download simply falls back to publishing without that image
- Already-published posts are no longer mislabeled "failed" — if a post was created but a later side-step (cache, session, search-engine ping) errored, the queue now finds the post by slug as well as title and correctly marks it completed
- The optional in-content image localization can no longer abort a publish — the whole step is now isolated; any error there is skipped and the post still goes live

---

## [2.16.3] - 2026-06-04  ·  _Patch_
**Content Queue — Recover Stuck Posts & Fix Missing Thumbnails**

### Fixed
- Scheduled posts can no longer vanish silently — if publishing was interrupted by a fatal error mid-run, the item used to stay frozen in a "processing" state that appeared in no queue tab and was never retried. Publishing now catches every failure type and the auto-publisher reclaims any item stuck longer than 15 minutes, so the backlog clears on the next visit
- Failed and stuck items are now visible and recoverable — a new "Failed" tab surfaces every problem item (failed or processing) with a one-click retry, instead of leaving them invisible while still showing on the calendar
- Featured thumbnails show in the admin again — completed posts whose image was attached through the image-matching flow stored the picture in the rich payload, not the legacy column, so the queue list and calendar showed an empty box even though the live post had the image. The admin now reads the matched image as a fallback
- Calendar hover preview image fixed — the tooltip was building the image path the wrong way around (a local path treated as an external URL and vice-versa), so the preview was always broken. It now uses the same single image resolver as the rest of the queue

---

## [2.16.2] - 2026-06-02  ·  _Patch_
**Security Hardening — Per-Install Unique Keys**

### Improved
- Every installation now generates its own unique security keys — authentication, session and JWT secrets are created with cryptographic randomness on first run and stored outside the distributed package. No two installs share secrets, so a token issued on one site is meaningless on another
- Install-time integrity manifest — the wizard now signs the tamper-detection manifest with the install’s own key at the end of setup, so a fresh installation never shows a false "integrity" warning

---

## [2.16.1] - 2026-06-02  ·  _Patch_
**Migration Polish — Author Links Show Everywhere, Bulletproof .htaccess**

### Improved
- The installer now guarantees jekcms’ own .htaccess is used — on most WordPress sites the .htaccess is stuffed with SEO/sitemap-plugin rewrite rules that can break clean URLs. The installer detects whether jekcms’ signature is present; if not, it backs the old file up to `.htaccess.wp-backup` and writes the canonical jekcms .htaccess (read straight from the package, so no drift). Routing is correct even if the host locked the file or the archive lacked it

### Fixed
- Migrated author social links now actually appear — several themes (Personal, Trends, Lifestyle, Pets, Finance) were reading the old column names and silently showed nothing. They now read the real `social_x / social_facebook / social_instagram / social_linkedin / website` fields, so the profiles imported in 2.16.0 are visible on author and article pages

---

## [2.16.0] - 2026-06-02  ·  _Minor_
**WordPress Migration — Richer, Safer, Cleaner Imports**

### Added
- Author profiles now come over in full — biography, website, social links (X, Facebook, Instagram, YouTube, Pinterest, LinkedIn) and a Gravatar-based avatar, instead of just the name. Existing authors are enriched only where fields are empty (never overwritten)

### Improved
- Re-running a migration no longer creates duplicates — posts already imported (matched by their original slug) are skipped, so an interrupted migration can be safely resumed
- Empty categories are cleaned up — WordPress’ default "Uncategorized" and any category with no posts are removed after import, so your category list stays meaningful
- A clear warning before deleting old files — if you migrated without downloading images (so your content still points at the old site), the cleanup step now warns that deleting the old files would break those images

---

## [2.15.1] - 2026-06-01  ·  _Patch_
**Installer Renamed to jekcms-install.php (avoids WordPress clash)**

### Improved
- The setup file is now `jekcms-install.php` instead of the generic `install.php`. A leftover WordPress `install.php` on the server can no longer be confused with — or shadow — the jekcms installer. All "not installed yet" redirects and robots rules were updated to match

---

## [2.15.0] - 2026-06-01  ·  _Minor_
**Setup Wizard — Clean WordPress Switchover (Safe Cleanup + Logo)**

### Added
- The wizard now finishes a WordPress migration cleanly — after importing your content, a Cleanup step lists exactly which old WordPress files will be removed and asks you to confirm (with a clear "this cannot be undone" warning). It then deletes them with a live progress bar, and optionally drops the old WordPress database too
- Safe by design — only genuine WordPress files are removed (a strict allow-list: `wp-admin`, `wp-includes`, `wp-content`, `wp-*.php`, `xmlrpc.php`…). jekcms’ own files are never touched — even where names overlap (e.g. license/readme). The wizard also refuses to drop jekcms’ own database
- Logo support — your site logo is pulled automatically from WordPress when migrating, or you can upload one (PNG/SVG/JPG/WebP). For a fresh install, just upload your logo. It’s saved to your site settings

---

## [2.14.3] - 2026-06-01  ·  _Patch_
**Setup Wizard — English & Turkish, English by Default**

### Added
- The setup wizard now speaks English and Turkish, defaulting to English. A language toggle (EN/TR) sits next to the theme switch in the top bar, and your choice is remembered. Every label, hint, button, alert and progress message is fully translated

---

## [2.14.2] - 2026-06-01  ·  _Patch_
**Setup Wizard — A Polished, Modern First Impression**

### Improved
- The setup wizard was redesigned from the ground up — a glassy, animated interface with a numbered progress tracker, the jekcms wordmark logo, soft animated background auras, smooth card transitions and a live progress bar. It now supports both dark and light themes with a one-tap toggle (your choice is remembered)
- The database step is much clearer — it now explicitly states that this is a new, empty database for jekcms, with a prominent note for WordPress users that it is not their existing WordPress database (that comes in the next step). No more mixing them up

---

## [2.14.1] - 2026-06-01  ·  _Patch_
**Setup Wizard — WordPress Migration Verified End-to-End**

### Fixed
- The WordPress import step now connects to the correct database. Three real-world bugs found during a live migration test (a 114-post WordPress site) were fixed: the framework is loaded in global scope so the site's configuration is read correctly, database seeding no longer collides with open result cursors, and AJAX responses are now always clean JSON (no stray warnings)

---

## [2.14.0] - 2026-06-01  ·  _Minor_
**New Setup Wizard — Install Fresh or Migrate From WordPress in Minutes**

### Added
- A modern, guided installer (install.php) — drop it next to the jekcms archive in your site root, open it in a browser, and it walks you through everything: a system requirements check, database connection (with step-by-step phpMyAdmin guidance and auto-create if the database is missing), site details, theme choice and admin account. It then unpacks the files, builds the database, applies your settings automatically, and cleans itself up afterwards
- WordPress migration built into the wizard — choose "Migrate from WordPress", enter your WordPress database details, and the installer previews how many posts, pages, categories and comments it found, pre-fills your site name and tagline from WordPress, then imports content, downloads & converts images to AVIF, and brings over approved comments. At the end it checks for leftover WordPress files and warns you to remove them to avoid conflicts
- Finishes with clear next steps — two cards to open the Admin Panel or view your site, with your details already filled in

---

## [2.13.9] - 2026-05-31  ·  _Patch_
**Account & License Security Hardening**

### Fixed
- License site-limit race condition closed — registering domains for a license is now serialized (row-locked), so two simultaneous requests can no longer slip past your plan's site limit
- Logout now fully ends the session — the session is destroyed and its cookie cleared (previously only the user id was removed), removing a session-fixation surface

---

## [2.13.8] - 2026-05-31  ·  _Patch_
**Reliability Audit — Newsletter Cron, Scheduled-Posts Link & Contact Inbox Fixed**

### Improved
- Trimmed remaining developer-oriented notes across the admin (technical jargon, internal details) down to plain, end-user labels

### Fixed
- Newsletter sending cron was broken across all sites (a comment line accidentally ended early and broke the file). Scheduled campaigns now send again
- Scheduled-posts link in the top bar led nowhere — it now opens the scheduled posts list correctly
- Contact-form inbox could load the wrong site's configuration (a hard-coded path) — now resolved per-site

---

## [2.13.7] - 2026-05-31  ·  _Patch_
**Google Console — One Clear "Scan" Button**

### Improved
- Index Coverage now has a single Scan button (auto-completes the whole site; becomes Re-scan when done) instead of three overlapping controls. Each card carries one short line explaining what it does

---

## [2.13.6] - 2026-05-31  ·  _Patch_
**Google Console — Cleaner, Less Cluttered Copy**

### Improved
- Trimmed long explanatory notes in the Google Console panel down to short, action-focused labels — less clutter, faster to scan

---

## [2.13.5] - 2026-05-31  ·  _Minor_
**Google Console — Cleaner Search Console Flow + Responsible Bulk Indexing**

### Added
- Bulk "Submit to Index" — notify Google about your not-indexed pages in one click. Built responsibly: a daily cap (well under quota), the same URL is never re-sent within 14 days, and only genuinely not-indexed pages qualify (404 / noindex / redirects are skipped). A clear notice explains that Google officially supports the Indexing API only for job-posting / livestream pages

### Improved
- Search Console tab decluttered — the redundant single-URL inspector was removed (Index Coverage already shows every URL's status). One clear flow: coverage summary → problem list → indexing actions
- Auto-scan reliability fixed — coverage now scans in short, fast batches with automatic retry, so it no longer trips the "connection error" on stricter hosts

---

## [2.13.4] - 2026-05-31  ·  _Patch_
**Google Console — One-Click Auto Scan for Index Coverage**

### Improved
- Index Coverage now scans automatically — one "Auto scan" click runs the whole site in the background, batch by batch, with a live X/Y checked… progress counter, instead of clicking "Next batch" a dozen times. Google's URL Inspection API is rate-limited and ~one URL takes a few seconds, so the panel paces itself and resumes until every URL is checked
- Resilient & cached — each batch is time-guarded so it never hangs the page, results are cached 24h, and a single-batch manual button plus Reset remain for fine control

---

## [2.13.3] - 2026-05-31  ·  _Patch_
**Google Console — Pick Your Analytics Property From a List (No More ID Typing)**

### Improved
- GA4 is now a dropdown, not a number to copy — Settings → Auto-discovery lists the Analytics accounts and properties your Google account can access, so you just pick yours instead of hunting for the numeric Property ID. Matches the existing one-click selection for Search Console site and AdSense account. Manual entry stays as a fallback
- Index Coverage is clearer before scanning — instead of a confusing row of zeros, the card now shows a clear "ready to scan" prompt, and explains that its totals won't exactly match Search Console's "Page indexing" numbers (Google also counts category/tag/system and old URLs; the panel checks your published content)

---

## [2.13.2] - 2026-05-31  ·  _Minor_
**Google Console — See Which Pages Google Isn't Indexing**

### Added
- Index Coverage in the Search Console tab — a new card scans your site's URLs and groups them by Google's indexing status: Indexed, Not indexed (crawled/discovered but not added, unknown to Google) and Error (404, server error, blocked by robots). You finally see your indexing problems in one list instead of checking URLs one by one
- Quota-friendly, incremental scan — built on Google's URL Inspection API (the only API that exposes per-URL index status). Each click inspects ~10 URLs, results are cached 24h, and a wall-clock guard keeps it responsive — large sites finish in a few clicks. Problem URLs link straight to Submit to Index

---

## [2.13.1] - 2026-05-31  ·  _Patch_
**Google Console UI — Now Fully Native to Your Admin Theme**

### Improved
- The Google Console panel was rebuilt on the admin design system — it now follows your dark/light theme, uses the same cards, pill buttons, segmented date controls and typography as the rest of the admin instead of a separate light-only look. A more professional, cohesive dashboard
- Cleaner data presentation — connection status shown as a clear pill badge, neutral monochrome trend charts (no decorative color noise), refined KPI cards, tables and diagnostics that read at a glance

---

## [2.13.0] - 2026-05-31  ·  _Minor_
**Google Console Now Ships With Every Theme**

### Added
- The Google Console plugin is now bundled with every jekcms theme — Search Console performance, GA4 traffic, AdSense earnings and frontend GA4/GTM/AdSense snippet injection in one panel, behind a single Google sign-in. Previously available on one theme, now on all of them
- One-click connect, encrypted tokens — OAuth refresh/access tokens are stored encrypted; the connection survives even if your admin session drops mid-flow (server-side one-time state, 10-min window)

---

## [2.12.0] - 2026-05-31  ·  _Minor_
**One Universal Key, Multiple Sites — Manage Domains From Your Dashboard**

### Added
- Site management in your account — one license = one key + N site slots. Register each site's domain (e.g. `siteadi.com`) under My Licenses, up to your plan's limit. Adding a site beyond the limit is blocked
- Strict activation — a site only activates if its domain is pre-registered for that license; an unregistered domain is rejected with a clear message. You control exactly which sites use your license
- Upgrade path — move to a higher plan for more sites; your key stays the same

---

## [2.11.0] - 2026-05-30  ·  _Minor_
**Simpler Pricing — Same Everything, Only Site Count Differs**

### Improved
- Every plan now includes the exact same features and support — all 14+ themes, all SEO & automation tools, priority support, lifetime updates. The only difference between plans is how many sites you can run
- Clear tiers: Personal $29 / 1 site · Standard $79 / 3 · Professional $149 / 10 · Unlimited $349 / ∞. The confusing dual "Agency $299 / Enterprise $599" tiers were replaced by one Unlimited plan

### Fixed
- Pricing data was inconsistent across the site, checkout and license server (Agency was 50 domains in one place, unlimited in another, $299 vs $599). Now a single consistent model end-to-end

---

## [2.10.0] - 2026-05-29  ·  _Minor_
**New Plugin: Google Console (Analytics + Search Console + AdSense)**

### Added
- Google Console plugin — Search Console (clicks/impressions/queries, URL Inspection, one-click index submit), Analytics GA4 (traffic, channels) and AdSense (earnings) in one dashboard, via a single Google OAuth connection
- Snippet injection — GA4, Tag Manager and AdSense tags injected on the frontend, managed from the admin (no code editing)
- Robust by design — encrypted tokens, response caching for quotas, per-API diagnostics, and clear "reconnect" handling

---

## [2.9.0] - 2026-05-29  ·  _Minor_
**Infrastructure Hardening — Security, Performance & SEO**

### Improved
- Faster page loads — plugin scan cached per request, composite DB indexes, and N+1 query batching on list pages. SEO: correct archive titles, paginated-page noindex, dynamic html lang

### Fixed
- Analytics plugin (ZeroTrack) and Smart Backup now create their database tables on first use, fixing a 404/500 on fresh installs

### Security
- Payment webhooks now fail closed (Stripe + iyzico): an unsigned/forged webhook can no longer mark an order paid, and the paid amount is verified against the order total
- Admin payment/customer/order pages now require admin role; unauthenticated maintenance scripts locked to CLI; session cookie set to `SameSite=Lax` (fixes being logged out when returning from external links)

---

## [2.8.3] - 2026-05-28  ·  _Patch_
**Hero Trimmed to a Hook + Features Grid Expanded**

### Improved
- Hero copy trimmed to a hook — the 8-vendor laundry list ("Analytics (Plausible). SEO schema (Rank Math)...") was too long. Replaced with a sharp hook: "Not plugins. Core." + a single subtitle quantifying the savings (20+ features, ~$624/yr). Same message, half the words, double the impact
- Features grid expanded from 14 to 20 cards — added 6 cards for built-in capabilities that were previously hidden: Social Publisher (Buffer/Hootsuite — 18+ networks auto-publish), Instant Indexer (IndexMeNow — IndexNow + WebSub + Web Push), Newsletter (Mailchimp — campaigns + subscribers + digest), AI Image Generator (Canva — Gemini-driven post covers), AI Bulk Publisher (ContentBot — n8n + bulk queue), and they collectively replace another ~$390/yr in subscriptions

---

## [2.8.2] - 2026-05-28  ·  _Patch_
**Hero Copy Forced from Code — DB Override Bypass**

### Fixed
- Hero subtitle was empty on production — load_marketing_translations() pulls hero_subtitle from the marketing_translations table when present, which still held a stale pre-v2.8.1 entry on production (the 8-vendor copy never displayed). Fix: after merging defaults+DB layers, header.php now force-overrides hero_title and hero_subtitle from the code defaults. Marketing-investment copy is a release-time concern, not a CMS admin concern

---

## [2.8.1] - 2026-05-28  ·  _Patch_
**Homepage Hero — The $624+/yr Built-In Story**

### Improved
- Hero subtitle rewritten — instead of the abstract "built-in SEO, internal linking, AVIF media" laundry list, the hero now names the 8 specific WordPress plugins jekcms replaces (Plausible, Rank Math, UpdraftPlus, Wordfence, WP 2FA, Redirection, Smush, WP Rocket) and quantifies the savings (~$624/yr in subscriptions). Concrete vendor-named replacements convert better than generic feature lists
- EN + TR copy aligned — both languages use the same 8 vendor names + dollar figure for consistent messaging across markets

---

## [2.8.0] - 2026-05-28  ·  _Minor_
**Performance Suite — Redirect Manager + Image Studio + Critical CSS, Built-In**

### Added
- Redirect Manager (NEW) — admin/redirects.php with full CRUD UI for 301/302/307/308/410 redirects. Bootstrap-level lookup runs BEFORE the router so redirects are zero-latency. Hit counter + last-hit timestamp expose which URLs people actually follow. Replaces Yoast Premium Redirect ($99/yr)
- 404 logger + Orphan 404s tab — every 404 hit is logged with referrer + UA. The admin sees URLs with 3+ hits in the last 30 days and can create a 301 with one click + a target URL field. Solving SEO recovery becomes a feed scroll
- RedirectManager class — lookup(), logNotFound(), stats(). Self-heals not_found_log table on first use. Admin/api/zt-track paths bypass (no false-positives on dev requests)
- Image Studio branding — existing admin/media-optimize.php now positioned as a Smush Pro alternative. Bulk batch convert (Media::batchConvert), responsive srcset auto-gen (320-1920px), Pinterest tall-image generator, domain-watermark stamper — all existing in Media.php
- Critical CSS Studio branding — existing Performance class (Performance::inlineCriticalCss, addCriticalCss, deferJavaScript, addPreloadHints, getCoreWebVitalsHints) positioned as a WP Rocket alternative. No new code, just visibility
- features.php +3 cards (Redirect Manager / Image Studio / Critical CSS Studio) — total grid now 14 cards covering ~$406+/yr in WP plugin subscriptions

---

## [2.7.1] - 2026-05-28  ·  _Patch_
**TOTP 2FA — Surfaced + Coverage Tracker in Security Center**

### Added
- Security Center → 2FA Status tab — lists all admin/editor/author users, their 2FA enabled state (ENABLED / NOT ENABLED pill), role, last-login timestamp. "Enable Now" button for the current user (jumps to Settings). For other users: instruction that they must enable from their own profile (TOTP is a personal credential)
- 5th KPI card: 2FA Coverage — percentage of admin/editor/author users with TOTP enabled. Color codes: green ≥80%, neutral 40-80%, red <40%. Sub-label shows raw count (e.g. "3 / 5 users")
- About TOTP card — documents the setup flow (Settings → Two-Factor Authentication → Initialize → scan QR → confirm), login flow, recovery path (DB-level unlock if authenticator is lost). Explicitly positions jekcms's TOTP as a replacement for WP 2FA + Wordfence Login Security (~$50/yr combined)
- features.php 11th card: TOTP 2FA — RFC 6238, Google Authenticator/Authy/1Password compatible

---

## [2.7.0] - 2026-05-28  ·  _Minor_
**Security Center — WAF Dashboard + File Integrity Monitor, Built-In**

### Added
- Security Center admin page — a single tabbed dashboard for WAF/login attempts, security events, and file integrity. Surfaces what was already running silently (Security::detectAttacks, login_attempts log, IntegrityGuard::maybeVerify) so you can actually see attacks happen. Replaces Wordfence Premium ($119/yr)
- WAF tab — recent login attempts (last 30), top attackers by failed-login count (last 7d), blocked IPs table with manual block/unblock, one-click "Block this attacker" from the top-attackers list. KPIs at the top: failed logins (24h), unique IPs (7d), blocked count, FIM status
- Security Events tab — parses `logs/security.log` (where Security::detectAttacks writes SQLi / XSS / path-traversal hits), displays timeline with IP, message and context. Up to 30 most recent events
- File Integrity tab — install fingerprint display, VERIFIED/DRIFT status pill, last tamper report (formatted JSON), one-click "Scan Now" button that triggers IntegrityGuard::verifyManifest(). Includes a response-playbook card for what to do if drift is detected
- Self-healing blocked_ips table — created automatically on first visit to the page. Idempotent: ON DUPLICATE KEY UPDATE preserves existing blocks. CSRF-protected admin operations throughout
- Sidebar link — new "Security Center" entry directly below Backups in the admin nav. Shield icon. Standard active-state highlighting

---

## [2.6.0] - 2026-05-28  ·  _Minor_
**Smart Backup — Scheduled Daily Backups, Built-In**

### Added
- Smart Backup scheduled cron — turn on daily auto-backups in the admin (Backups → Smart Backup Schedule card). Pick the hour (default 03:00, low-traffic window). Cron runs `BackupManager::scheduledRun()` which is idempotent (one backup per day, even if cron fires multiple times). Replaces UpdraftPlus Premium ($70/yr)
- Retention policy — configurable 7-365 days. Auto-backups older than the cutoff are deleted automatically after the daily run. Manual backups are never auto-deleted. Storage stays bounded
- Pure-PHP backups — no `mysqldump` dependency (Hostinger and shared hosts often disable it). Streaming row-by-row dump handles large post tables without exhausting memory. Output is a single ZIP with `db.sql` + `uploads/` + `manifest.json`
- External sync hint — the schedule card documents the recommended `rclone` pattern for syncing the `backups/` folder to S3, Google Drive, or Dropbox. Native cloud SDK support is on the v2.6.x roadmap

---

## [2.5.0] - 2026-05-28  ·  _Minor_
**Schema Studio — 13 Schema.org Types, Built-In**

### Added
- Schema Studio plugin family — 13 Schema.org types, all driven from the post editor with form-based UI. The full set: Article, BlogPosting, NewsArticle, TechArticle, ScholarlyArticle, Report, FAQPage, HowTo, Product, Event, Review, Course, Recipe (new), and LocalBusiness (new). Replaces Rank Math Pro's schema-builder module ($59/yr) — no subscription, no add-ons
- Recipe schema — food bloggers can now ship Google Rich Recipe cards: prep/cook/total time (ISO 8601), yield, category, cuisine, calories, ingredient list, step-by-step instructions, aggregate rating. Drives 30-40% CTR uplift on recipe-intent queries
- LocalBusiness schema — drives Google Maps + local-pack ranking. 18 business subtypes (Restaurant, Store, MedicalBusiness, Dentist, BeautySalon, TravelAgency, …). Full PostalAddress + GeoCoordinates + opening hours + price range + aggregate rating
- CSV-style data entry — ingredients, instructions and opening-hours all accept one item per line in a textarea. No fragile JavaScript arrays, no clicking +/- buttons; copy-paste works directly from your notes
- Schema preview + Google Rich Results Test link — the editor shows the live JSON-LD payload AND a one-click handoff to Google's validator. Zero guesswork

---

## [2.4.0] - 2026-05-28  ·  _Minor_
**ZeroTrack Analytics — Privacy-First, Cookie-Free, Built-In**

### Added
- ZeroTrack Analytics plugin — a built-in, privacy-first replacement for Google Analytics, Plausible and Matomo. Zero cookies. Visitor data never leaves your server. KVKK/GDPR-compliant by design: IP addresses are SHA-256 hashed with a daily-rotated salt, making cross-day correlation mathematically impossible. Auto-activated on install
- Privacy dashboard in admin → ZeroTrack: page views, unique visitors, sessions, bounce rate, daily trend chart, top pages, referrers, countries, devices, UTM sources. Date range selector (today / 7d / 30d / 90d)
- Smart filtering out of the box — respects browsers' Do-Not-Track header; excludes logged-in admins; filters Googlebot, GPTBot, ClaudeBot, headless Chrome and 20+ other automation user-agents; configurable IP and path exclusions
- Reverse-proxy aware — picks up the real visitor IP behind Cloudflare and LiteSpeed (no double-counting your CDN). Country detection via Cloudflare CF-IPCountry header — no third-party GeoIP database needed
- Self-cleaning — raw pageview rows are deleted after a configurable retention window (default 90 days). Daily aggregates are kept forever for long-term trend analysis with tiny storage footprint

---

## [2.3.18] - 2026-05-19  ·  _Patch_
**Sharper Homepage Hero — A Concrete Hook**

### Improved
- The hero now says what jekcms actually is — the vague "Smart Next-Gen CMS" line was replaced with a concrete, provable hook: everything you would normally add to WordPress (SEO, internal linking, AVIF media, bulk import, AI publishing) is already in the core, self-hosted, with no plugin stack to buy or maintain. One clear message instead of a buzzword

---

## [2.3.17] - 2026-05-19  ·  _Patch_
**Newsletter Email: Branded Dark Header**

### Improved
- Email design now has a real branded identity — the previous version rendered too plain in clients that strip CSS backgrounds. The header is now a solid dark band with the brand wordmark and an accent eyebrow, plus a thin accent rule under it, a card frame, and a tinted footer band. Backgrounds use both inline CSS and `bgcolor` attributes so the design survives in Gmail/Outlook. Auto-applied to system templates via a schema bump

---

## [2.3.16] - 2026-05-19  ·  _Patch_
**Redesigned Newsletter Email Templates**

### Improved
- Professional, brand-consistent email templates — the newsletter emails (confirmation, welcome, campaign, unsubscribe, new-post) were replaced with a polished, English, email-safe design: a clean white card on a soft background, branded header with an accent eyebrow, strong typographic hierarchy, a proper rounded brand CTA button, and a complete footer (unsubscribe, website, copyright). Table-based + inline CSS for reliable rendering across email clients; all placeholders preserved
- Auto-applied across all installs via a plugin schema-version bump — system templates refresh automatically on the next load, while any template you customized is left untouched

---

## [2.3.15] - 2026-05-19  ·  _Patch_
**Blog Editor: Featured Post & Empty-Content Fix**

### Fixed
- Blog post editor opened empty for the featured post — the editor treated `?id=0` (the featured post, which carries id 0) as "new post" because of a `id > 0` check, so it never loaded it. It now loads any post when an id is present (0 included); a truly new post is one with no id parameter. Additionally, if a row's body is empty (legacy posts whose content lived only in the static blog data file), the editor pre-fills the form from that source by slug/id for review — saving persists it into the database (display-only, non-destructive, never overwrites existing edits)

---

## [2.3.14] - 2026-05-19  ·  _Patch_
**Plugin System Restored on the Main Install (Newsletter Now Lists)**

### Fixed
- Newsletter (and all plugins) now appear in the plugin manager — the main install's bootstrap (cloned long ago from an older codebase) was entirely missing the plugin-loader block, so the plugin registrar never ran and no plugin could register itself. The block was restored, identical to the canonical source; the registrar now runs (with the self-healing plugin-table schema), so Newsletter registers automatically and is listed/activatable

---

## [2.3.13] - 2026-05-19  ·  _Patch_
**Marketing Blog Editor Now Reachable in Admin**

### Fixed
- Blog posts are editable again — the bilingual marketing blog (the EN/TR posts shown on jekcms.com/blog) has its own admin editor that reads the same table the public blog uses, but it had no link in the admin menu, so it looked like the posts weren't manageable (the CMS Posts page only lists the separate site-content table). A "Blog Posts (jekcms.com)" entry was added to the admin sidebar — the existing posts are now listed and editable

---

## [2.3.12] - 2026-05-19  ·  _Patch_
**Wizard Network Error, Profiles & Plugin Registration Fixed**

### Fixed
- "Network error" on Generate fixed — the JSON wizard endpoint (`admin/ajax/assistant-json.php`) existed only on two installs; it now exists on every site, so Generate works everywhere, not just compass
- Plugins now register on cloned installs — on installs cloned from an older database the `plugins` table could be missing newer columns, which made plugin registration fail silently — so the Newsletter plugin never appeared in the plugin manager. The scanner now self-heals the table schema, so Newsletter (and any new plugin) registers and is visible/activatable

---

## [2.3.11] - 2026-05-19  ·  _Patch_
**Root Admin Fixes — Content Fixer, Newsletter Link, Wizard Keys**

### Fixed
- Content Fixer 404 fixed — the SEO Optimizer's Content/Heading Fixer page existed in the canonical source but was missing from the main install's admin, returning 404. It is now present
- Newsletter admin link corrected — the Newsletter plugin manifest pointed its admin page to a non-existent path; corrected fleet-wide so the dashboard opens from the plugin manager (the sidebar entry still requires the plugin to be activated)
- Wizard keys fixed on the main site too — the previous translation-key parity fix covered demo sites but missed the main install; `cq_assistant_*` keys are now mirrored there as well, so the JSON Generation Wizard no longer shows raw keys

---

## [2.3.10] - 2026-05-19  ·  _Patch_
**Content Queue Wizard — Raw Keys Fixed on All Sites**

### Fixed
- JSON Generation Wizard now reads properly on every site — the content-queue assistant translation keys (`cq_assistant_*`) existed only on a couple of sites, so other sites showed raw keys like "cq_assistant_title" instead of labels. All sites now carry the full key set, mirrored byte-for-byte from the canonical source

---

## [2.3.9] - 2026-05-19  ·  _Patch_
**Newsletter Signup Live on the Marketing Site**

### Fixed
- Newsletter subscription now works on jekcms.com — the footer "Subscribe" form was built but silently failed when the subscriber table did not exist. The handler now self-creates the table (idempotent, identical schema to the Newsletter plugin, so the plugin admin reads the same subscribers). Homepage stat figures also unified site-wide

---

## [2.3.8] - 2026-05-19  ·  _Patch_
**Sub-Page SEO Audit — Documentation Title Fixed**

### Improved
- Documentation title is now descriptive & branded — the docs was a bare "Documentation"; it is now "jekcms Documentation | Setup, Admin Guide, REST API & Automation" (and category/page docs titles now carry the brand). Stronger, unique titles for search
- Full sub-page meta/SEO audit: every marketing sub-page verified to have a unique, bilingual (EN/TR) meta title and description, valid canonical + hreflang (en/tr/x-default) + Open Graph; no missing, empty or duplicate meta found

---

## [2.3.7] - 2026-05-19  ·  _Patch_
**Accurate WordPress-Alternative Page (Verified Features Only)**

### Improved
- Stronger, honest "why jekcms vs WordPress" page — now built strictly from verified features: it maps the paid WordPress plugins jekcms replaces in its core (SEO/Yoast, internal linking/LinkWhisper, broken-link detection, AVIF media/ShortPixel, security/Wordfence, payments/WooCommerce), plus jekcms-only JSON bulk import and n8n+Gemini AI automation. Modern, readable, theme-consistent table; long-tail keyword focused; FAQ with FAQPage structured data

### Fixed
- Removed an inaccurate capability claim — a "multi-site / fleet management" line was wrongly added to the comparison page, structured data and llms.txt. jekcms has no such product feature; it has been removed everywhere and replaced with verified, real capabilities only

---

## [2.3.6] - 2026-05-19  ·  _Patch_
**No Orphan Pages — Full Internal Linking**

### Fixed
- No orphan pages — every public marketing page is now reachable via the footer + sitemap + clean URL with EN/TR variants. The "Report Piracy" page was orphaned (no link anywhere) and is now footer-linked and crawlable; the WordPress-alternative page was already footer-linked (verified)

---

## [2.3.5] - 2026-05-19  ·  _Patch_
**AI-Search Visibility & WordPress-Alternative Positioning**

### Added
- WordPress Alternative comparison page — a new, honest `/wordpress-alternative` (TR: `/tr/wordpress-alternatifi`) page with a factual jekcms-vs-WordPress table and FAQ (FAQPage structured data), sitemap + hreflang + footer-linked
- llms.txt — a machine-readable summary at `/llms.txt` so AI assistants can accurately describe jekcms as a self-hosted CMS / WordPress alternative

### Improved
- Discoverable in AI search — AI answer/search engines (ChatGPT, Perplexity, Gemini, Claude, Copilot) are now explicitly allowed (server-level block removed for them; named robots groups added). Low-value SEO-scraper bots stay blocked
- Clearer entity for search & AI — structured data now classifies jekcms as a Content Management System with a precise CMS / WordPress-alternative description and feature list; site meta sharpened to say "self-hosted CMS / WordPress alternative" (factual, no keyword stuffing)

---

## [2.3.4] - 2026-05-19  ·  _Patch_
**Marketing-Site SEO Hardening**

### Improved
- No duplicate page URLs — direct `.php` hits (e.g. `/features.php`) now 301-redirect to the clean URL (`/features`), so each page has a single indexable address and a single canonical
- Single redirect hop — `http://www` now goes straight to `https://` non-www in one 301 instead of two chained redirects (faster, stronger SEO signal)
- Audited & confirmed correct: error pages return real 404 (no soft-404, noindex), dynamic robots.txt with environment-aware sitemap, bilingual sitemap with hreflang, self-referencing canonical + en/tr/x-default hreflang, `?lang=tr` → `/tr/…` 301

---

## [2.3.3] - 2026-05-19  ·  _Patch_
**Article Rendering & Internal-Link Integrity Fixes**

### Fixed
- Broken internal links repaired at the source — The auto internal linker could run over raw Markdown and inject a link inside a Markdown link, which the renderer then turned into corrupted, half-visible anchor markup. Markdown links/images are now protected, so internal linking can never mangle content again. The link cleaner was also hardened to fully remove any pre-existing corrupted/leaked link debris — re-running the internal-link scan on an affected site now self-heals old content
- Checklists render properly — Markdown task lists (`- [ ]` / `- [x]`) now show real checkbox glyphs instead of literal "[ ]" text
- Tables are styled — Markdown tables in articles now render with borders, padding and header styling instead of columns running together
- No more double bullets — list items showed both a default bullet and a custom marker; the duplicate is gone
- Related posts fixed — the related section rendered twice, once as full-width stacked images; the broken duplicate was removed, leaving the clean card grid
- Featured image aspect ratio — single-post cover images now use a proper 16:9 frame instead of a cropped near-square
- Table of contents shows accented characters correctly — the on-page contents list double-escaped HTML entities, showing things like "G&uuml;ncel" instead of "Güncel"; titles are now decoded before display (anchors stay in sync)
- Front-end fixes now go live immediately — deploys purge the page cache, so a fix is no longer masked by up-to-5-minutes of stale cached HTML

---

## [2.3.2] - 2026-05-19  ·  _Patch_
**JSON Wizard Rename & Calendar Visibility Fix**

### Improved
- "Content Assistant" renamed to "JSON Generation Wizard" — name now reflects what it actually does: builds a ready-to-import JSON + prompt
- "Continue below" marker is now built-in — typing `{devam}` in a post renders a centred "content continues below" button that smooth-scrolls to the next section. It now lives in the core renderer (theme-independent), so theme resets can no longer wipe it
- Checklist fix also covers articles already stored as HTML, not just Markdown

### Fixed
- Content calendar fixed — schedule is visible again — On some installs the whole calendar silently came back empty: the underlying query referenced a column that older content-queue tables never had, so it failed and showed nothing. The query is now schema-independent and self-healing, and the month view also shows every scheduled item regardless of its state (draft / approved / in-progress / done), colour-coded by status
- Calendar hover preview used the wrong image field in one branch — corrected

---

## [2.3.1] - 2026-05-19  ·  _Patch_
**Cleaner Content Queue Import Screen**

### Improved
- Content Queue → Import — Clearer visual separation between the AI Content Assistant and the import options (JSON / Google Sheets / CSV), so the two no longer run together on the page
- Removed the redundant static JSON and Google Sheets format reference blocks — the Assistant already generates a ready-to-use example, so the extra boilerplate only added clutter. Applied fleet-wide

---

## [2.3.0] - 2026-05-18  ·  _Minor_
**Reliability, Security & Always-On Delivery**

### Added
- Two-Factor Authentication (TOTP) — Modern QR setup card in every site's Security settings. Scan with Google Authenticator / Authy / 1Password; self-hosted QR (no third party), with a manual key fallback. Login enforcement is fail-open by design — a 2FA glitch can never lock you out
- Zero-downtime auto-deploy — Updates now ship to the whole fleet automatically within minutes of a change, over HTTPS, with a post-deploy health check. No manual uploads, no SSH, no lockouts

### Improved
- Faster pages — documentation/screenshot assets ~73% lighter, zero-layout-shift images
- Cleaner SEO — bilingual default meta description & footer fields, consistent schema name source

### Fixed
- Site name in Google results — A long-standing settings storage issue made search engines fall back to the bare domain. Now every site shows its real configured name in titles, social cards and structured data — fleet-verified
- Stay signed in — Admin sessions no longer drop unexpectedly; they persist until you explicitly sign out (root cause: server session garbage-collection wasn't aligned with the configured lifetime)
- Footer & branding — Footer renders reliably and is driven from a single source in General Settings (slogan / footer text), bilingual (TR/EN) where applicable; placeholder/demo remnants removed

---

## [2.2.0] - 2026-05-18  ·  _Minor_
**Two-Factor Auth, Smart Newsletter & Customer Update Channel**

### Added
- Admin two-factor authentication (TOTP) — Optional time-based 2FA with QR enrollment, enabled/disabled per account from Security settings; compatible with any authenticator app
- Smart newsletter digests — The subscription plugin can now send an automated weekly or monthly roundup of new posts (frequency off/weekly/monthly + day-of-month), reliably driven server-side via cron with per-period de-duplication
- Customer self-update channel — End-to-end signed update delivery: the update manifest is verified with an embedded public key so verification works on every install, SHA-256 is mandatory, and a one-command release packager builds a clean core package with a key-pair safety gate that refuses a mis-signed release

### Fixed
- Critical SEO: archive pages no longer soft-404 — On the Tech & Minimalist themes every category/author archive returned a hard 404 (the template read a routing key that was never set); these pages now resolve correctly and author archives are fully supported
- API write authorization — An authenticated low-privilege token can no longer create/modify/delete content or touch another author's posts; role + ownership are enforced from the product's own capability model
- Sitemap/robots resilience — Security user-agent heuristics could return 403 to Googlebot/Search Console for `sitemap*.xml`/`robots.txt`; these endpoints now bypass every blocking rule so indexing is never accidentally lost
- Footer social links — The marketing footer now renders only the accounts configured in General Settings → Social Media (placeholder/demo links removed)

### Technical
- Schema.org WebSite/Organization/SoftwareApplication name is now a single i18n source instead of three hardcoded strings
- Centrally (rsync) managed installs carry a marker that blocks self-update, preventing version drift from the operator's next sync; customer-shipped packages omit the marker so external self-update is unaffected

---

## [2.1.3] - 2026-05-18  ·  _Patch_
**Security Hardening & Update Integrity**

### Fixed
- Critical: SSRF blocked — Server-side image fetch (media-from-URL) now allows only http/https public hosts; private/loopback/link-local and cloud-metadata addresses are rejected, redirects disabled, size-capped
- High: Markdown XSS blocked — Link/image URLs in content are scheme-allowlisted; `javascript:`, `data:`, `vbscript:` and protocol-relative URLs can no longer reach `href`/`src`
- High: Cross-site request hardening — State-changing requests now also enforce same-origin (Origin/Referer) on top of the CSRF token, covering all admin action pages at once
- SVG upload XSS blocked — Uploaded SVGs containing scripts, event handlers, foreignObject, external refs or XML entities (XXE) are rejected; static SVGs still allowed
- Update integrity mandatory — Updates without a verified SHA-256 are refused; manual ZIP apply is off by default unless the official hash is provided; developer-license localhost detection now requires a real loopback connection (Host-header spoof closed)

---

## [2.1.2] - 2026-05-18  ·  _Patch_
**Core Web Vitals: Responsive Images, LCP & Caching**

### Improved
- Site-wide Image Optimization — Every front-end image now ships with intrinsic `width`/`height` (zero layout shift / CLS), `decoding="async"` and lazy-loading, applied through a single global output filter that covers all themes. The hero/LCP image keeps `fetchpriority="high"` and is never lazy-loaded
- Automatic Responsive Variants — Existing images are progressively back-filled with optimized AVIF/WebP size variants (thumbnail/medium/…), so cards and thumbnails download a small image instead of the full-resolution original — done gently in the background with no extra server load
- Faster First Paint — Instant-search CSS no longer blocks rendering (async with no-JS fallback); themes can ship a `critical.css` for inlined above-the-fold styles
- Browser Caching Restored — Front-end pages are cacheable again (back/forward cache works); only admin and API stay no-store

---

## [2.1.1] - 2026-05-17  ·  _Patch_
**Clean Content Rendering: Markdown, Code Blocks & Encoding**

### Improved
- Newsletter Band Restyled — The pre-footer subscribe band dropped its generic blue gradient and now uses the site's own monochrome design tokens with pill controls — consistent in both light and dark themes

### Fixed
- Critical: Raw Markdown Headings — When a post mixed HTML with Markdown (the normal output of AI/automation), `##` / `###` headings, fenced code blocks and lists were printed literally instead of being rendered. The Markdown engine was rewritten so block elements are converted even alongside HTML
- Critical: Shell Commands Became Headings — Code (fenced ``` / ~~~, inline, and existing `<pre>`) is now protected before any heading parsing, so `#` shell comments and `#!/bin/bash` lines are never mistaken for titles
- Legacy Linux Articles Repaired — WordPress-imported command blocks that had broken apart (`<pre>…</p><p>…</pre>`) were rejoined into clean multi-line code blocks
- Critical: Turkish Text Corruption (Mojibake) — Some automated content arrived double-encoded (Turkish letters shown as CJK glyphs, e.g. "Çikolata" → "脟ikolata"). The API now repairs every inbound write path automatically (self-validating, no false positives), and a fleet tool cleans existing content across all sites

---

## [2.1.0] - 2026-05-16  ·  _Major_
**Reliable Theme Switching, 17 Auto-Publish Networks & Full-Width Admin**

### Added
- Regional & Fediverse Auto-Publish — Eight new networks join the social automation engine: Pixelfed, Misskey/Sharkey, WriteFreely, Micro.blog and Lemmy (token/instance), VK (OAuth2), plus Hatena Bookmark and Plurk (OAuth1). Every connected account receives new posts automatically with per-platform pacing and back-off
- Honest Capability Notes — Networks without a safe, official publishing API (Xing, Naver, Nostr) are now clearly labelled with the reason instead of silently failing — no fake connectors

### Improved
- Full-Width Connections Page — The social connections grid no longer caps at a narrow column; cards now use the full screen width on large displays instead of leaving the right third blank

### Fixed
- Critical: Theme Switching Failed — Because `settings.key` is uniquely indexed, the old "UPDATE then INSERT-if-zero-rows" path threw a duplicate-key error whenever the value was unchanged (re-activating a theme, or the automatic previous-theme snapshot on every switch). The activation aborted with a database error and the theme never changed. Theme writes are now a single-row upsert (delete + insert) that also self-heals any pre-existing duplicate/stray rows. Active-theme reads are deterministic (canonical group, newest row) so the front-end always reflects the chosen theme

---

## [2.0.1] - 2026-04-16  ·  _Major_
**Smart Next-Gen CMS — Admin UI Overhaul, Bulletproof Slugs & Autosave**

### Added
- New Admin Design Language — Unified badge system (5 pill variants: success/danger/warning/info/neutral), stat-card-v2 with colored backgrounds + decorative SVG, quick-action outline buttons, state-block for empty/error states
- Language Toggle — TR/EN switcher in admin header with session-based override (`$_SESSION[admin_lang_override]`), persists across navigation
- Draft Autosave — Post editor saves every 30s + localStorage offline fallback. Status pill bottom-right: "Saving…" / "Saved · 15:42" / "Offline". Restore prompt on reopen if unsaved changes found
- Anonymous Preview — `preview.php?token=XXX` with 48-hex-char secret tokens stored in `post_meta`. Click "Preview Link" button, URL auto-copied to clipboard. Orange banner indicates preview mode
- Revision Diff — Click any revision → modal with word-level diff (jsdiff via CDN). Green additions / red strike-through deletions. "Restore this revision" with automatic snapshot
- Word Count Distribution — Dashboard shows stacked bar of post word counts (0-500, 500-1K, 1K-1.5K, 1.5K+) with hover tooltip
- Date Range Filter — Post listing has native date pickers for `date_from`/`date_to`
- Media Grid/List Toggle — Library view switches between grid and vertical list, preference saved to localStorage
- Slug Rebuild Tool — `admin/tools/rebuild-slugs.php` — dry-run preview + conflict handling + CLI mode for batch operations

### Fixed
- Critical: Turkish Slug Bug — `mb_strtolower()` was converting `İ` (U+0130) into composite sequences, breaking the transliteration map and leaving orphan bytes as hyphens. New `slugify()` runs `strtr` BEFORE lowercasing with comprehensive map (Turkish + Latin extended). Fixed 866 bad slugs across all sites
- Sidebar Border Bug — `.sidebar-brand` was 56px but `--header-height: 60px`, creating a 4px misalignment visible as a horizontal line. Now uses `var(--header-height)`
- profile.php 90s Button — `.avatar-actions .btn-sm` had `border-radius: 50%` rendering buttons as blobs. Plus "Active" was hardcoded English in Turkish admin. Both fixed
- Settings Thumbnail Inputs — Pixel inputs had no styling (native browser default — 90s). Now proper padding, focus ring, contained background
- Logo Regression — `logo-yatay.svg` was an obsolete test logo. Replaced with `logo-dikey.svg` + inline SVG in sidebar (matches admin login)
- License Page Branding — Fake blue `[J]` SVG monogram replaced with real `logo-dikey.svg`. Hardcoded `#28a745` colors migrated to CSS variables
- Updates Page UX — License inactive / update failed / up-to-date states use unified pill-badge format. Raw English errors removed from Turkish UI

---

## [1.5.3] - 2026-03-14  ·  _Minor_
**Auto-Seed Settings, Core Web Vitals, Update System & SEO Hardening**

### Added
- Settings Auto-Seed — `ensure_default_settings()` automatically seeds `site_name` and `site_alternate_name` into the database on first page load. Cache-file based, zero performance impact after initial run. No more manual SQL for new sites
- Migration System — `migrations/5_seo_settings_seed.php` created across all sites. Update system can now distribute database changes automatically
- LCP Eager Loading — First post card image on page 1 gets `loading="eager" fetchpriority="high"` across all theme architectures. Expected ~200-500ms LCP improvement
- CLS Prevention — `width` and `height` attributes added to all post card images. Eliminates layout shift completely
- CSS Cache Busting — `?v=THEME_VERSION` parameter added to stylesheet links in starter theme headers
- Update Server Connected — `api/updates/check.php` now uses real `UpdateManager` with database queries instead of static stub response. Graceful fallback on connection errors
- jekcms Backlinks — All footer files across active sites, admin panels, and bundled themes now link to `jekcms.com` with "jekcms" anchor text and `rel="noopener noreferrer"`
- Marketing SEO — Real favicon URL (SVG), `application-name` meta tag, `theme-color`, WebSite schema `alternateName` added. Decorative text moved to CSS to prevent Google sitelink pollution

### Fixed
- Sitemap pagination URLs removed — `?page=2`, `?page=3` etc. no longer appear in homepage, category, tag, and author sitemaps. These thin pages wasted crawl budget
- Thin tag pages now `noindex` — Tag pages with fewer than 3 posts get `noindex, follow` via `output_robots_meta()` to prevent thin content indexing
- Markdown `# Heading` now renders as `<h2>` instead of `<h1>` — prevents double H1 on post pages where title is already H1
- SQL migration file `sql/v1.5.1-seo-site-names.sql` deleted — replaced by automatic `ensure_default_settings()` mechanism
- Marketing site favicon was data URI — Google requires real URL for SERP favicon display. Replaced with proper `/favicon.svg`
- Marketing site showed "Dashboard Posts Media Settings" as Google sitelinks — decorative text moved from HTML to CSS `content: attr(data-label)`

---

## [1.5.2] - 2026-02-27  ·  _Patch_
**Deep SEO Audit — Schema, OG Image, Core Web Vitals & Accessibility**

### Fixed
- BlogPosting `author` schema missing `url` property — Google requires author URL since 2023. Added `author.url` pointing to `/author/{slug}` across all sites
- BreadcrumbList last item missing `item` (URL) property — Google Rich Results test was reporting errors. Fixed both category and non-category code paths across all sites
- `og:image:width` and `og:image:height` meta tags missing in bundled theme functions.php files — Facebook/LinkedIn image previews could render incorrectly. Added 1200×630 dimensions
- Featured/hero image missing `fetchpriority="high"` in active theme single.php files — LCP (Largest Contentful Paint) performance impact. Also added `width`/`height` where missing
- Author avatar `<img>` tags had empty `alt=""` in active theme files — accessibility and image SEO issue. Replaced with author name
- Hardcoded `<html lang="tr">` in affected themes — replaced with dynamic `get_setting()` for correct language declaration

---

## [1.5.1] - 2026-02-27  ·  _Patch_
**SEO Audit — Pagination, Sitemap Language, Tag Cleanup & OG Locale**

### Fixed
- Pagination URL double query string bug — `?page=3?page=4` caused by `get_canonical_url()` returning `?page=N`. Now strips page param from baseUrl before rebuilding
- Schema `$currentUrl` missing `?page=N` on paginated pages — canonical and schema URLs now consistent
- `?page=1` duplicate content — 301 redirect to clean URL added in all site .htaccess files
- News sitemap hardcoded `<news:language>en</news:language>` — now uses `get_setting('general', 'site_language')` dynamically across all sites
- Tag URLs returning 301 to homepage — changed to proper 410 Gone response with minimal HTML page across all sites
- BlogPosting schema missing `inLanguage` property — added dynamic language detection across all sites
- `og:locale` hardcoded to `en_US` on Turkish sites — now dynamically set to `tr_TR` or `en_US` based on site language setting
- AVIF → WebP schema image fallback missing `file_exists()` check — WebP URL was emitted even when file didn't exist

---

## [1.5.0] - 2026-02-25  ·  _Minor_
**Duplicate Prevention, Smart Thumbnails & Admin Tools**

### Added
- `Post::checkDuplicate()` method — detects duplicate posts by title or slug before creation
- Duplicate check integrated into all API webhooks: `webhookPublish`, `webhookSchedule`, `webhookDraft`, `webhookBulkPublish`, `webhookContentGenerate`
- HTTP 409 response with full existing post details (id, title, slug, status, url) when duplicate detected
- `force_duplicate: true` request parameter to bypass duplicate check when intentional duplicates are needed
- Bulk publish silently skips duplicates with `skipped` counter instead of blocking
- Admin "Duplicates" button on Posts page — opens modal with full duplicate analysis
- Slug pattern detection engine: finds posts ending with `-N` (N=1-10) where the base slug also exists as another post
- Single-click and bulk "Trash All Duplicates" actions with real-time UI updates
- Image proxy fallback in `get_featured_image()` — when pre-generated thumbnail files are missing, dynamically resizes via `image-proxy.php`
- Size dimension map: thumbnail (400×400), card (480×300), medium (800×500), large (1600×1000)
- AVIF → WebP → original format cascade when looking up sized variants
- Content Queue sidebar badge now counts `queued` status alongside `draft` and `ready`

---

## [1.4.5] - 2026-02-17  ·  _Patch_
**Production Hardening — SEO Fixes, License Enforcement & Session Security**

### Added
- `output_robots_meta()` function — per-page robot directives (noindex for 404, search pages; post-level override)
- License enforcement in `init.php` and `login.php` — redirects to `license.php` when no active license key is configured
- Cross-site session hijacking prevention: cookie path scoped to site-specific URL path via `parse_url(SITE_URL, PHP_URL_PATH)`
- Session `_site_hash` verification in `Auth::loadUser()` — prevents authenticated sessions from bleeding across co-hosted sites
- Site-specific `remember_token` cookie path — remember-me tokens no longer shared between sites on same domain
- Footer branding standardized across all installations

### Fixed
- API upload path double `uploads/uploads/` prefix — `uploadFromUrl()` and `uploadFromBase64()` now strip redundant prefix before saving to database
- Duplicate `<link rel="canonical">` tags removed from affected site headers where both inline and `output_seo_head()` emitted canonicals
- FAQ schema output: enforced minimum 3 items with 50+ character answers, maximum 10 items, deduplicated across helpers
- Sidebar category post counts removed per design rules — "(5)" count display no longer appears in category listings
- Author name links converted from non-clickable `<span>` to proper `<a href>` anchor tags in single.php files
- SITE_NAME config spacing corrected — compound names like "FinanceSubject" updated to properly spaced "Finance Subject"
- Schema.org URLs stripped of tracking parameters (`utm_source`, `fbclid`, etc.) via `parse_url()`
- Post card images missing `width`/`height` attributes — CLS prevention applied across affected sites

---

## [1.4.0] - 2026-02-10  ·  _Minor_
**SEO Overhaul, Content Optimizer, Breadcrumbs & Table of Contents**

### Added
- Complete SEO overhaul across all active sites — meta tags, Open Graph, Twitter Cards, Schema.org structured data reviewed and standardized
- Breadcrumb navigation with Schema.org `BreadcrumbList` markup added to every site
- Table of Contents (TOC) — automatically generated from `<h2>`/`<h3>` headings, renders as sidebar widget or inline block depending on theme
- Content Optimizer with dictionary-based synonym refresh — replaces removed AI API (Gemini/Groq) approach that broke Turkish morphology
- Turkish synonym dictionary (~200 modern word pairs) and English synonym dictionary (~180 pairs) with archaic terms removed
- Auto language detection via `get_setting('general', 'ai_content_language')` for optimizer dictionary selection
- Google SERP site name fix: `??` operator replaced with `?:` to catch empty strings in `og:site_name` and WebSite schema
- `<meta name="application-name">` tag added to all theme headers for Google site name signal
- Pinterest Compose API endpoint for Livecub — Gemini generates photo, PHP GD adds text overlay, 5 layout templates, 1000×1500 output
- SosyalMedya cover image engine replaced: PHP GD gradients → Gemini Image API professional photographs (1080×1920, AVIF, 5 styles)
- Turkish slug generation fix: `generateSlug()` now properly transliterates ç, ğ, ı, ö, ş, ü across all sites
- `fix-slugs.php` utility script for repairing existing corrupted Turkish slugs in production databases

### Fixed
- robots.txt files had unresolved `{{SITE_DOMAIN}}` placeholders in affected sites
- hobirehber schema function was named `output_hobbyrig_schema()` instead of `output_hobirehber_schema()`
- CSP header in production was blocking Google Analytics, AdSense, and Facebook Pixel domains
- MinimalistRig posts had full URLs in `featured_image` column instead of relative paths
- Livecub favicon was showing jekcms [J] icon instead of Livecub L+Heart brand icon

---

## [1.3.1] - 2026-01-24  ·  _Patch_
**Critical SEO Fix, Multi-Site Template & Documentation**

### Added
- `_template/` directory established as the canonical base for creating new jekcms sites — includes all required files, folder structure, and placeholder variables
- Dual-environment configuration: `.env` (local development) and `.env-production` (live server) with automatic detection based on hostname
- Placeholder system for rapid site cloning: `{{SITE_NAME}}`, `{{SITE_SLUG}}`, `{{SITE_DOMAIN}}`
- Standard error pages: 400, 401, 403, 404, 500, 502, 503 with consistent branding
- Maintenance mode page (`maintenance.php`) with countdown timer
- Standardized `.htaccess` with GZIP compression, browser caching (1 year for static assets), security headers, and URL rewriting
- Complete deployment documentation: architecture guide, SEO checklist, responsive images reference, upgrade instructions

### Fixed
- Critical: Removed `X-Robots-Tag: noindex` HTTP header that was accidentally blocking all Google indexing across production sites
- Admin content queue retry: `attempts` counter now resets to 0 when a failed task is re-queued
- Removed obsolete Pinterest sharing code from post editor panel
- Removed e-commerce menus (Sales, Customers) from blog-only site admin panels — these belong to the main marketing site only
- Synchronized missing AJAX endpoints (comment, newsletter, comment-like) across all sites
- Added missing `SpamFilter.php` class to kriptogetiri

---

## [1.3.0] - 2026-01-21  ·  _Minor_
**E-Commerce, Customer Portal, License System & Multi-Language Engine**

### Added
- Complete e-commerce system with iyzico payment gateway integration — credit card processing, 3D Secure, installment support
- Order management lifecycle: create → payment → confirmation → processing → completed, with cancellation and refund flows
- PDF invoice generation with automatic numbering, tax calculation, and downloadable customer receipts
- Customer portal at `/customer/` — dashboard with order history, active licenses, downloadable invoices, and profile management
- Support ticket system with threaded messages, priority levels, and admin response tracking
- Multi-language engine with database-driven translations — Turkish and English supported out of the box, extensible to any language
- `Translator` class with lazy-loading approach: strings parsed on demand, not upfront — significant memory reduction on multi-locale installations
- jekcms license system with 6 tiers: DEV (free), PER (personal), STD (standard), PRO (professional), AGC (agency), ENT (enterprise)
- License activation, validation, and deactivation API at `/api/license/`
- Update server with check, download, and report endpoints at `/api/updates/`
- Image proxy with SSRF protection — blocks private IP ranges (10.x, 172.16-31.x, 192.168.x, 127.x) and automatic garbage collection (7-day TTL)
- Cache management system: page cache, query cache, object cache, sitemap cache, feed cache, image cache with admin AJAX clear controls
- Rate limiting with IP-based tracking and configurable thresholds
- IP blocking list for persistent abusers
- SEO pagination: `rel="next"`/`rel="prev"` tags, canonical URL query string exclusion, robots.txt `Allow: /*?page=`
- Responsive image `srcset` generation with automatic `width`/`height` attributes for CLS prevention
- Gravatar 2x rendering for HiDPI/Retina displays

---

## [1.2.1] - 2026-01-15  ·  _Patch_
**Admin Panel English Translation & UI Polish**

### Added
- Complete English translation of all admin panel interface elements — menus, labels, buttons, tooltips, error messages, and success notifications
- Unified terminology across admin: consistent use of "Posts", "Pages", "Media", "Settings" throughout all modules
- Post voting system activated — thumbs up/down with per-IP deduplication
- Post view counter with bot-filtered tracking
- Newsletter module wired into admin sidebar under PLUGINS section
- AI content queue foundation — infrastructure for automated content generation pipeline

### Fixed
- Admin sidebar spacing reduced for cleaner navigation appearance
- CSS improvements across admin panel — consistent padding, border alignment, and responsive behavior on smaller screens

---

## [1.2.0] - 2026-01-14  ·  _Minor_
**Plugin Architecture, Newsletter System & Advertising Module**

### Added
- Plugin enable/disable system with database-driven management — plugins can be activated, deactivated, and configured without code changes
- Newsletter module with subscriber management, campaign creation, and delivery tracking — moved from core to PLUGINS menu for optional activation
- Advertising system for banner and inline ad placements with impression and click tracking
- Contact form with spam protection, email notifications, and admin message management
- Email delivery logging with status tracking (sent, failed, bounced)
- Spam protection logging for audit and pattern analysis
- Admin sidebar reorganized: PLUGINS section separated from core navigation
- API endpoint enhancements for external integrations

---

## [1.1.0] - 2026-01-08  ·  _Minor_
**Environment System, SEO Tools & Performance Foundation**

### Added
- Environment configuration system — automatic local/production detection based on hostname with separate database credentials and URL settings
- SEO Optimizer admin tool with on-page analysis, keyword density checker, and readability scoring
- Extended sitemap system: `sitemap.xml` index with separate `sitemap-posts.xml`, `sitemap-pages.xml`, and `sitemap-categories.xml`
- Schema.org auto-detection: `Article`, `BlogPosting`, `WebPage`, and `WebSite` structured data injected per page type
- Post view tracking with `post_views` table — bot-filtered, deduplicated by IP, used for "Popular Posts" widgets
- Post voting system infrastructure with `post_votes` table — per-IP rate limiting, thumbs up/down
- Performance baseline: output buffering, query logging in development mode, execution time tracking
- Advanced `robots` meta controls: per-page `noindex`/`nofollow` settings in post editor

---

## [1.0.0] - 2026-01-02  ·  _Major_
**Initial Release — Blog CMS Foundation**

### Added
- Core blog CMS with post and page management — WYSIWYG editor, draft/published/scheduled status workflow, revision history
- User authentication with role-based access control: admin, editor, author, subscriber — each role has granular permission boundaries
- Hierarchical category system with unlimited nesting depth and SEO-friendly URL slugs
- Tag management with auto-suggest, bulk operations, and tag cloud generation
- Media library with drag-and-drop upload, AVIF/WebP automatic conversion, and gallery management
- Theme system supporting 14+ premium themes — each theme is a self-contained directory with templates, partials, assets, and configuration
- Responsive design with mobile-first approach — all themes pass Google Mobile-Friendly test out of the box
- Comment system with nested replies, Gravatar integration, and admin moderation queue
- Basic SEO: `<title>` tags, `<meta description>`, canonical URLs, and XML sitemap generation
- RSS feed at `/feed.xml` with full-content and excerpt modes
- Search functionality with relevance scoring across titles, content, and excerpts
- Admin dashboard with post statistics, recent activity feed, and quick-action buttons
- API token system for external integrations — key generation, revocation, and usage logging
- Clean URL routing via `.htaccess` rewrite rules — `/post-slug`, `/category/name`, `/tag/name`, `/author/name`

---
