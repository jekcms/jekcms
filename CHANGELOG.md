# jekcms — Changelog

All notable changes to jekcms. This file is generated from a single
source of truth and mirrors the public changelog at https://jekcms.com/changelog

_Do not edit by hand — edit `marketing-includes/changelog-data.php`, then run_
_`php tools/gen-changelog-md.php` and commit._

---

## [2.79.0] - 2026-09-01  ·  _Minor_
**Search your settings, one-click color presets, per-field reset, and typography & width controls**

### Added
- The customizer now has a search box. Type "badge", "font" or "sidebar" and jump straight to the setting — including layout section cards — with the matching field highlighted when you land on it.
- Color presets: the Colors section offers ready-made palettes generated from your theme's own brand colors — Ocean, Forest, Violet, Ember — with the hue relationships between fields preserved, so every preset stays as coherent as the original design. One click fills the fields; nothing is saved until you hit Save.
- Typography controls on every theme: body font size and line height, with a content-width slider for the site's main column. These emit nothing until you actually change them, so existing sites keep their exact look.
- Every color, slider and switch now carries a small reset arrow that returns just that field to the theme default — no more resetting the whole theme to fix one value.
- Ctrl+S (Cmd+S) saves from anywhere in the customizer, and leaving the page with unsaved changes now asks first.

---

## [2.78.0] - 2026-09-01  ·  _Minor_
**A fresh install now looks like the demo, share buttons get styles, and every section heading is yours to name**

### Added
- Share buttons on the post page now come in styles: keep the theme's own design, or switch to round chips, brand-colored circles, or minimal icons — one dropdown in Customize → Post. Available on six themes (news, minimalist, lifestyle, entertainment, trends, travel); the default stays exactly what the theme ships today.
- Renaming homepage section headings now works across every theme that prints one — "Latest Articles", "Editor's Picks", "Most Read" and friends can all carry your own wording, set from the section's gear menu.

### Improved
- What you see on a theme's demo site is now what a fresh install gives you. We compared every live demo's saved settings against the theme's factory defaults and folded the differences in: the crypto theme ships with its demo's heading font, the personal theme with its demo's palette and calmer sidebar, and the pets and finance themes with the accent colors their demos actually wear. A release-gate test now keeps demo and defaults from drifting apart again.

---

## [2.77.0] - 2026-09-01  ·  _Minor_
**Card controls on all 14 themes, and a real category picker for the homepage**

### Added
- The Cards section introduced in the previous release now covers every theme. Each theme exposes exactly the options its card design supports — from the full set (badge, excerpt and its length, author, date, reading time, view count, date style, image ratio, corner radius) down to the focused set of image-led themes like travel — so every switch you see genuinely does something. Defaults still match each theme's current look.
- Choosing which categories appear on the homepage no longer means typing slugs into a text box. The category blocks section now lists your real categories as tappable chips — tick the ones you want, in the customizer, and they are saved in the same format as before, so existing setups keep working.

---

## [2.76.0] - 2026-09-01  ·  _Minor_
**The theme customizer, rebuilt: one clear layout, a new Cards section, and renamable section titles**

### Added
- A new Cards section controls the anatomy of your post cards: show or hide the category badge (and pick its position), turn the excerpt on or off and set its length, choose which meta appears — author, date, reading time, view count — switch between relative ("3 hours ago") and full dates, and set the image ratio and corner radius with live preview. It ships on four themes first (news, minimalist, tech, lifestyle); defaults match each theme's current look, so nothing changes until you change it.
- Homepage section headings are now yours to name. Open a section's gear menu in the layout card and type your own title — "Latest Stories" can become whatever fits your site; leave it empty to keep the theme's wording.

### Improved
- The customizer now looks and works like General Settings: a vertical navigation on the left, your options in the middle, and the save/preview rail on the right. Every one of the 14 themes now presents the same order — Homepage, Post, Sidebar, Cards, Colors, Fonts, Layout, Advanced — with theme-specific extras at the end. Colors and fonts each have their own section instead of hiding inside "Branding", a dot marks sections with unsaved changes, and old deep links to the previous tabs still land in the right place.

### Fixed
- Switches that rendered inside another tab (for example a theme's disclosure or trip-details options merged into the Post tab) could not actually be changed — flipping them did nothing after save, because the form marked them under the wrong tab name. They now save correctly.

---

## [2.75.10] - 2026-08-31  ·  _Patch_
**A real author page, cleaner post cards, and a calmer "how this was made" box**

### Fixed
- The refund policy page laid its "term: explanation" points out as boxed rows, and the term column landed at a different width in every row — one wrapped over three lines, the next fitted on one. It now reads as a normal list with the term in bold, so every point lines up. The partner terms page shared those same class names but shipped no styling at all, and the styling that did exist was written for dark mode only, so on the site's default light theme the bullets and panels were invisible. All of it now lives in the site stylesheet and follows the light and dark palettes.
- The author page finally shows the author: their photo, name, bio, links and a real article count, in one card at the top of the page. Two themes (entertainment, tech) previously showed only a generic person icon, and on one of them the count was the whole site's post total rather than that author's. The header now comes from a single shared component, so every theme gets the same correct page.
- Category, tag, author and search listings no longer blow one card up to double size in the narrow column beside the sidebar — every card in a listing is the same size.
- Post cards on the entertainment theme were uneven and cluttered: cards in the same row ended at different heights, the author block sat at the bottom as a large square avatar, and the category badge could drift below the image. Cards now share one anatomy — image with the badge on its top-left corner, title, and a single meta line pinned to the bottom with a small round author avatar, the date and the counters.
- The featured card stretched its neighbour into a tall, mostly empty card. It now spans two rows as well, so two normal cards stack beside it and no card is left with a hole in it.
- The "How this content was made" box no longer draws a coloured bar down its left edge; it is now a single even outline in the theme's accent colour with the information icon carrying the emphasis.
- Posts could be unreadable in dark mode: text pasted from another page brings its own colour with it, so a paragraph saved as black stayed black on the dark background. Pasted black (and pasted white) text now follows the theme's own colour, while colours you chose on purpose are kept.

---

## [2.75.9] - 2026-08-31  ·  _Patch_
**Theme switches no longer turn themselves off; reaction cards and headline badges fixed**

### Fixed
- Post-page switches (reaction cards, star rating, share bar) could silently turn themselves off after saving the customizer: a switch that wasn't part of the submitted form was treated as "off". Saving now only changes the switches that were actually on screen, so features can no longer disappear on their own. If your emoji reaction cards vanished, they come back with this update.
- Some sites rendered two reaction bars on a post — a leftover theme bar plus the built-in one. Themes now declare their own bar so the built-in one steps aside.
- Headline cards showed generic labels ("HOT NOW", "VIRAL", "EXCLUSIVE") instead of the post's category. They now show the real category name in its own colour and link to that category.

---

## [2.75.8] - 2026-08-31  ·  _Patch_
**Homepage, card and sidebar fixes across all themes**

### Fixed
- Post cards lost their title, date and meta as soon as the post had a featured image — the image escaped its frame and pushed the text out of the card. Cards now keep a fixed 16:10 image frame whether or not there is an image.
- The homepage headline grid always had one empty slot: it reserves five cards but only four were fetched. It now fills all five, falling back to the newest posts when there aren't enough popular ones — so the grid is never patchy on a new site.
- Homepage category blocks only ever showed the alphabetically first categories, so sites with many categories saw the same two blocks no matter how much they published. Blocks (and the fallback menu on some themes) now pick categories that actually have posts, most recently updated first.
- Turning every sidebar widget off did nothing: an internal fallback switched them all back on. Your selection is now final — an empty sidebar stays empty. Fixed on six themes.
- The "How this content was made" box looked like a grey block pasted onto the page: it borrowed the theme's serif heading font and letter-spaced capitals. It now follows the theme palette with an accent bar, an icon and a readable label — on every theme.
- Share buttons under posts were washed out and hard to read; they now sit on a neutral surface with full-contrast icons and fill with the network's colour on hover.
- Very tall featured images no longer stretch the post page out of shape, and the editor now suggests the right size (1200 × 675).
- The old Twitter bird was replaced with the X logo everywhere it still appeared, including the footer builder's icon set.

---

## [2.75.7] - 2026-08-31  ·  _Patch_
**Layout saves no longer overwrite each other**

### Fixed
- Saving the customizer stores the layout of every page (homepage, post page, sidebar…) in one go — and those writes were silently overwriting each other, so homepage section changes (turning the hero or category band off) were lost and the switches snapped back on. Each save now builds on the previous one within the same request; section toggles finally stick everywhere.

---

## [2.75.6] - 2026-08-31  ·  _Patch_
**Two new layout section types**

### Added
- The layout engine's section dictionary gained two generic types that any theme (including customized forks) can adopt: "Dual Spotlight" — two wide image cards side by side — and "All Posts" — a paginated full-archive grid with a posts-per-page setting.

---

## [2.75.5] - 2026-08-31  ·  _Patch_
**Section toggles that always work, missing customizer tabs, footer icon outlines**

### Fixed
- Homepage and post-page section toggles (hero, category band, widgets…) are now real form controls: they save correctly even if a browser extension, an old browser or a script error breaks the page's JavaScript. Previously the layout travelled only through a script-filled hidden field, so a broken script made the save silently skip and toggles snapped back on.
- Themes that support layout sections but don't declare a matching customizer tab now get that tab automatically — for example the Sidebar tab appears on themes that were missing it, so widget stacks can be reordered and toggled everywhere.
- Footer Builder social icons rendered as solid blobs: a stylesheet rule filled the outline-style icon set. Icons now keep their stroke outlines in both light and dark mode.

---

## [2.75.4] - 2026-08-31  ·  _Patch_
**Media uploads with broken ICC profiles, footer social selection**

### Fixed
- PNG images exported from Photoshop or Canva with a broken ICC color profile (the classic "iCCP: known incorrect sRGB profile" warning) failed to upload to the Media Library. These images are perfectly loadable — harmless decoder warnings are now tolerated during image processing and the upload completes normally.
- In the Footer Builder, toggling social networks on or off did not stick: a script error silently swallowed checkbox changes, so the previous selection came back after saving. Selections now save exactly as chosen.

---

## [2.75.3] - 2026-08-31  ·  _Patch_
**Self-healing after updates on shared hosting**

### Fixed
- On some shared hosting stacks (notably LiteSpeed with aggressive OPcache settings) a core update could leave the server serving stale compiled code, breaking the site with a 500 error until PHP was restarted. The updater now invalidates the compiled-code cache file by file right after copying — before migrations run — and a new early watchdog detects this exact failure on any later request, clears the cache itself and auto-refreshes the visitor's page within seconds. No manual PHP restart needed anymore.

---

## [2.75.2] - 2026-08-31  ·  _Patch_
**Customizer save reliability fixes**

### Improved
- Tracking ID fields (GA4, Google Tag Manager, AdSense, Facebook Pixel) now accept a pasted full snippet: the ID is extracted automatically on save, so analytics starts working even if you paste the whole code block.

### Fixed
- Saving from Appearance → Customize no longer erases your Footer Builder configuration. The two screens stored data under the same key, so every customizer save silently reset the footer to the theme default.
- Homepage section toggles (hero, category band, etc.) now survive strict hosting firewalls: the layout payload is sent in an envelope some shared-hosting WAFs used to strip, which made the toggle snap back to "on" after saving.
- Saving the customizer or the Footer Builder now also refreshes the full-page cache, so visual changes appear on the site immediately.
- Media Library uploads now show the actual reason when a file fails, instead of a bare error mark — including server-side blocks and configuration limits.

---

## [2.75.1] - 2026-08-30  ·  _Patch_
**Paid licenses can remove the footer credit**

### Added
- "Powered by jekcms" is now optional on paid licenses: a new switch under Settings → General → Branding removes the credit line from your site footer. The copyright line and legal links stay untouched. On the free edition the switch stays locked and the credit remains — removing it is a paid-license benefit.

### Improved
- Saving settings now also refreshes the full-page cache, so site-wide changes (branding, footer, reading options) appear immediately instead of waiting for the cache to expire.

---

## [2.75.0] - 2026-08-29  ·  _Minor_
**Layout engine phase 4: live preview and per-device sections**

### Added
- Live layout preview: a new button next to every section group in the theme customizer opens your real site in a preview window and applies your unsaved changes to it as you work — reorder a section or flip a toggle and the preview refreshes by itself. Desktop, tablet and mobile width buttons are built in. Drafts live only in your admin session: visitors keep seeing the saved layout until you press Save, and the preview never enters the page cache.
- Per-device section visibility: every layout section can now be shown on all devices, desktop only, or mobile only — a heavy hero for desktop, a compact strip for phones. Hiding is pure CSS media query, so nothing shifts on the devices where the section does show, and the section cards wear a small badge so you always see which ones are device-limited.

---

## [2.74.1] - 2026-08-29  ·  _Patch_
**Audit follow-up: social queue repairs its own schema**

### Fixed
- Social auto-posting on installations carrying the old queue layout no longer loses the remote post ID and publish timestamps: when the queue table lacks the newer columns, the publisher now adds them on the spot and retries, instead of logging a database error on every publish. Posts were always delivered — what was lost was the permalink back to them; that record is now kept.

---

## [2.74.0] - 2026-08-29  ·  _Minor_
**Editorial approval flow: pending → review → approve**

### Added
- Optional editorial approval for multi-author sites: turn on "Author posts require editor approval" in Settings and authors can no longer publish or schedule directly — their save honestly lands as "Pending review", and editors or admins approve it with one click ("Approve & Publish" / "Send back to draft") right from the Posts list. Every approval records who approved and when in the post's audit trail, editing an already-live post never unpublishes it, and automated pipelines keep their own quality gate. Off by default — single-author sites notice nothing.

---

## [2.73.0] - 2026-08-29  ·  _Minor_
**Media folders: organize the library without touching URLs**

### Added
- Media library folders: create, rename and delete folders from a new folder bar above the grid, filter the library by folder (including an "Unfiled" view with live counts), move files in bulk via the bulk-actions menu or one by one from the file's detail page, and have new uploads land in whichever folder is open. Deleting a folder never deletes its files — they simply return to Unfiled — and moving files never changes their URLs, so nothing published breaks. Existing installations pick up the schema automatically; no migration step needed.

---

## [2.72.3] - 2026-08-29  ·  _Patch_
**Documentation: migrating from Ghost, Substack, Medium and Blogger**

### Added
- New documentation page "Migrating from Ghost, Substack, Medium & Blogger" (in English and Turkish): which export file each platform gives you, exactly what each importer carries across — publish states, dates, tags, paid/member visibility, image localization — and, just as importantly, what does not come across (comments, authors, subscriber lists) plus how to handle redirects afterwards. The offline documentation bundled with the installation package includes it too.

---

## [2.72.2] - 2026-08-29  ·  _Patch_
**Audit follow-up: quieter logs and a cache race fix**

### Improved
- Error logs got quieter and more trustworthy: the contact-form's schema self-repair no longer probes by triggering database errors (it now checks columns directly), and deleting an already-deleted cache entry no longer logs a warning when two requests race. Version stamps across managed copies are also kept in sync automatically.

---

## [2.72.1] - 2026-08-29  ·  _Patch_
**Audit hardening: recipe filters, reaction schema, webhook brakes**

### Improved
- Membership payment bridge (released earlier today) hardened after an adversarial pass: unverified webhook requests can no longer grow the database or log files (flood brake), the delivery log rotates itself, and Stripe checkouts completed with a free trial or a 100% discount now correctly open Premium.

### Fixed
- Recipes theme: the archive's time and difficulty filters (and the "quickest" sort) now actually work — they queried post columns that never existed, so every filtered visit logged a database error and returned nothing. Filters now read the Recipe plugin's real data.
- Post reactions: installations carrying the old reaction table layout repair themselves on first use — previously every post view on such a site logged a database error and reaction counts stayed frozen. Existing reactions are preserved during the repair.
- Recipes theme: posts without recipe data no longer show invented "15 min prep · 30 min cook · 4 servings · easy" badges — the badges now read the Recipe plugin's real values and simply stay hidden when there are none.

---

## [2.72.0] - 2026-08-29  ·  _Minor_
**Membership payment bridge: automatic Premium via Stripe / Lemon Squeezy webhooks**

### Added
- Paid memberships no longer need manual bookkeeping: connect your own Stripe or Lemon Squeezy account's webhook to your site and members are marked Premium the moment their payment completes — and downgraded automatically on full refunds and subscription expiry. Matching uses the member's registration e-mail, and the provider's customer reference is remembered so subscription-end events match even when they carry no e-mail.
- Set-up lives in Settings under the membership section: paste the signing secret, copy the ready-made webhook address, and watch the "last webhook" line confirm deliveries. Secrets are stored encrypted, never echoed back into the form, and every notification is verified against its signature — unsigned or tampered requests are rejected. Money still flows entirely through your own provider account: jekcms never sees card data.

---

## [2.71.0] - 2026-08-29  ·  _Minor_
**Migrate from Medium and Blogger + new Security & Trust pages**

### Added
- Migrate from Medium: upload the ZIP from Medium's "Download your information" as-is and your stories arrive with their full body, subtitle (kept as the excerpt), publish date and URL slug — drafts stay drafts, and re-running the import safely skips what is already there. With image localization on, Medium-hosted images are pulled into your media library and converted to AVIF/WebP.
- Migrate from Blogger: upload the XML backup from Blogger's "Back up content" (a Google Takeout ZIP works too) and posts, pages and drafts import with their labels mapped to tags, publish dates and URL slugs preserved. Settings and comment entries in the backup are recognized and left out instead of turning into broken posts.
- jekcms.com now has a Security page listing the concrete protections in the product — two-factor sign-in, Argon2id password hashing, encrypted stored secrets, signed webhooks, update integrity checks — plus a responsible-disclosure channel, and a Trust Center explaining data ownership, the perpetual license model and our honesty principles. Both pages exist in English and Turkish.

### Improved
- The API reference now documents all five outgoing webhook events — new-comment and new-member notifications had shipped earlier but were missing from the docs, so integrations could not discover them.

---

## [2.70.3] - 2026-08-28  ·  _Patch_
**SEO core: multilingual sitemap discovery + consistency fixes**

### Added
- Multilingual sites are now fully discoverable: the posts sitemap lists published posts in EVERY public language (previously only the site language, which left translated posts — and any post in another language without a pair — invisible to crawlers), and translation pairs are announced with xhtml:link hreflang alternates including x-default, the format Google recommends.

### Fixed
- Category and tag sitemap entries no longer count future-dated scheduled-style posts: that mismatch could announce an archive in the sitemap while the page itself said noindex (a "submitted but noindex" contradiction in Search Console) and could even emit a future lastmod date.
- A parent category whose posts all live in child categories is now announced in the sitemap index consistently with the category sitemap itself.
- Posts embedding YouTube via iframe embed URLs now get VideoObject structured data on the page, matching what the video sitemap already announced.
- /feed.xml and /rss.xml now 301-redirect to the canonical /feed instead of serving duplicate copies of the feed.
- The installer's sample welcome post is now marked noindex — identical text across thousands of installs should not enter search indexes, and deleting it leaves no index residue.

---

## [2.70.2] - 2026-08-28  ·  _Patch_
**First-install experience polish + plugin management fix**

### Added
- New sites start friendlier: the installer now localizes the default category to your site language (Genel/General instead of "Uncategorized") and seeds an editable welcome post with first-step tips — so the homepage is alive from minute one instead of empty. WordPress migrations remove the sample post automatically once real content arrives.
- /rss now 301-redirects to the canonical /feed, so readers and tools typing the WordPress-style address no longer hit a 404.

### Fixed
- Activating or deactivating a plugin from the admin panel works again: a token-name mismatch introduced by an earlier security hardening made every plugin toggle fail with "Invalid security token" on fresh installs. The page now validates the token explicitly, and the shared helper accepts both token field names so the same class of mismatch cannot recur.

---

## [2.70.1] - 2026-08-28  ·  _Patch_
**Ad A/B, RUM and Critical CSS: measurement accuracy and hardening**

### Fixed
- Ad A/B click counting is now much more accurate: starting a scroll gesture on an ad box no longer registers as a click on touch devices, switching tabs while hovering an ad is no longer mistaken for an ad click, and an empty ad container (ad blocker or unfilled ad) no longer counts as an impression — so CTR comparisons between variants reflect real behavior.
- The Ad A/B panel no longer shows "Test ACTIVE" when the ad slot itself is disabled (which silently produced zero data); it now shows a clear "slot disabled" warning. Variant changes also flush the full-page cache immediately, so old variants stop being served the moment you edit the test.
- RUM now records a perfect CLS score of 0 correctly. Previously only visits with some layout shift were counted, which made the CLS p75 look worse than reality; browsers without layout-shift support are recorded as "no data" instead of a fake perfect score.
- Posts whose slug merely starts with "ara", "api" or "admin" (e.g. /araba-bakimi, /api-design) are no longer misclassified in RUM page types or silently excluded from analytics collection.
- Critical CSS extraction keeps more valid selectors: :is()/:not() lists with commas, escaped class names and non-ASCII class names are no longer dropped (which could cause a brief unstyled flash), a stylesheet link inside an HTML comment can no longer confuse the transform, and a single unusually small page can no longer permanently disable critical CSS for the whole site.

---

## [2.70.0] - 2026-08-28  ·  _Minor_
**Critical CSS: inline above-the-fold styles with async theme stylesheets**

### Added
- Pages now render faster: the CSS needed for the visible part of the page is inlined into the document head, and the theme's full stylesheets load asynchronously in the background (with a no-JavaScript fallback). This removes render-blocking CSS from the critical path and improves LCP and FCP.
- The critical subset is generated automatically per theme from your site's real pages — no configuration, no theme edits, and it refreshes itself whenever the theme's CSS changes. Works on every theme.
- Built-in safety rails: if the generated subset looks too small or too large, the page is served exactly as before; original stylesheet links are kept in a noscript fallback; and the feature can be switched off from the Performance panel (the RUM p75 numbers there will show you the effect).

---

## [2.69.0] - 2026-08-27  ·  _Minor_
**Performance (RUM): real-visitor Core Web Vitals panel**

### Added
- A new Performance panel shows how fast your site really is for visitors: LCP, CLS, INP, FCP and TTFB are collected from real page views and reported as 75th-percentile values — the same method Google uses for Core Web Vitals — overall, by device, by page type, and as a "slowest pages" list that tells you exactly where optimization pays off.
- The collector is a tiny inline script (no external CDN, no cookies) that sends a single measurement as the visitor leaves the page. It respects Do Not Track, skips logged-in users and bots, and works on every theme.
- Privacy-first by design: only the page path, the metric values and a coarse device class are stored — no IP address, no session, no fingerprint. Collection can be switched off in the panel, and the switch is enforced on the server, not just in the page.
- Data is kept for 90 days and old rows are cleaned up automatically.

---

## [2.68.0] - 2026-08-27  ·  _Minor_
**Ad A/B testing: placement and size variants with impression/click measurement**

### Added
- Ad slots can now run A/B tests: define two or more code variants (different sizes, formats or layouts) for any slot under Ads → Ad A/B Testing, with per-variant traffic weights. Each visitor gets a sticky, cookieless variant assignment, so the same person always sees the same variant.
- Impressions (counted when the ad is at least half visible) and clicks are now measured per variant, with bots filtered out. The panel shows 30-day impressions, clicks and CTR per variant, plus an estimated revenue column driven by a manually entered RPM.
- The variant is chosen in the browser, so full-page caching keeps working at full speed — the cached HTML is identical for every visitor and no cache page needs to be bypassed for the test.
- A lightweight standalone beacon endpoint records the events: it accepts only same-site requests, validates that the reported variant belongs to the reported slot, rate-limits per visitor, and stores only a salted daily hash — never the raw IP address.

---

## [2.67.1] - 2026-08-27  ·  _Patch_
**Link health checker: SSRF hardening**

### Security
- The outbound link-health checker (used by SEO and affiliate link monitoring) now validates the FINAL connection address, not just the originally saved URL: if a link redirects or its DNS resolves to an internal or cloud-metadata address (localhost, 127.x, 169.254.169.254, private ranges, IPv6 loopback/ULA), the probe reports it as unverifiable instead of revealing the internal service's status. This closes a server-side request forgery (SSRF) avenue where a crafted redirect could have been used to probe internal infrastructure.
- Literal IPv6 URLs (e.g. http://[::1]/) are now correctly recognized and blocked by the safety gate.

---

## [2.67.0] - 2026-08-27  ·  _Patch_
**Affiliate + Search Console Insights: reliability hardening**

### Fixed
- Search Console Insights no longer shows misleading trends when Google's API partially fails: if any part of a scheduled fetch errors out, the previous snapshot is kept and a retry is scheduled, instead of rebuilding the panel from incomplete data (which could have made every page look like it was rising or falling).
- Insights comparison windows are now exact 28-day / previous-28-day ranges (ending yesterday, since today's data is always incomplete), so the totals and the per-page changes always agree.
- Scheduled Search Console fetches now backfill any gap since the last successful run and are protected against overlapping runs, so a slow day or a missed cron no longer leaves holes in the daily trend.
- Affiliate links keep working when a link is paused: a paused link's existing in-content links and /go/ clicks still resolve (pausing only removes it from new auto-cloaking) — previously a paused link 404'd and its [aff] shortcode vanished from the post.
- An [aff] shortcode with a slug that no longer exists now preserves your custom anchor text as plain words instead of deleting it from the sentence.
- Affiliate targets are validated harder on save: over-length URLs (which MySQL would silently truncate) and links that point back at your own /go/ cloak (a redirect loop) are now rejected with a clear error.

### Security
- Hardened the affiliate link-health monitor against SSRF: a target pointing at an internal or cloud-metadata address (localhost, 169.254.169.254, private ranges) is no longer added to server-side health probing.

---

## [2.66.99] - 2026-08-27  ·  _Patch_
**Affiliate + Search Console Insights: polish and fixes**

### Improved
- Small polish: the Search Console Insights "new" badge is now localized for English sites, the affiliate panel and schema check are lighter (one fewer query per request), and a couple of dead code paths were removed.

### Fixed
- Affiliate cloak links now use only temporary redirects (302/307): a permanent 301 could be cached indefinitely by browsers and CDNs, which would stop counting clicks and prevent you from repointing a link — the two things the feature is for. Any existing 301 link is served as 302 from now on.
- Affiliate targets containing control characters (a pasted URL with hidden line breaks) are now rejected on save instead of producing a broken, destination-less redirect.
- Auto-cloak matching now lowercases only the host, not the path — case-sensitive affiliate paths (e.g. Amazon product IDs) can no longer collide and cloak a link to the wrong destination.

---

## [2.66.98] - 2026-08-27  ·  _Minor_
**Affiliate Links: a new revenue channel**

### Added
- New "Affiliate Links" plugin to manage affiliate and outbound links in one place — a new revenue channel alongside ads. Each link gets a clean cloaked URL (yoursite.com/go/slug) that records the click server-side (bot-filtered, privacy-safe: no raw IP stored) and redirects to the target, so you can rename, disable or repoint a link without touching any post.
- Automatic SEO safety: a content filter adds rel="sponsored nofollow noopener" to affiliate links (Google requires "sponsored" for paid links, and the wrong markup can cost you rankings) and can auto-nofollow all other outbound links. It can also auto-cloak any raw link in your content whose destination you've registered — existing posts are covered without editing them.
- Drop a tracked link anywhere with [aff slug] (uses the link's name as anchor) or [aff slug]custom text[/aff]. Code blocks are left untouched.
- A dashboard shows clicks per link (human vs bot separated), a 30-day click trend, and link status. Dead affiliate targets surface in the existing SEO → Broken Links checker, so you catch expired offers before they cost you.

---

## [2.66.97] - 2026-08-27  ·  _Minor_
**Search Console Insights: data-driven SEO**

### Added
- New "Insights" tab in Google Console that turns your real Search Console history into an action list — no more guessing which post to update. It keeps a daily history (previously the panel only showed a live snapshot) and every day highlights: Declining pages (clicks dropped ≥30% — top refresh priority), Striking-distance keywords (ranking 8–20 with high impressions — a small push lands them on page one), Keyword cannibalization (multiple pages competing for the same query), and Rising pages (what's working — make more like them).
- Each page row links straight to the post editor, so you go from "this is declining" to editing it in one click.
- The history is fetched automatically once a day in the background; a "Fetch now" button pulls it on demand. Insights keep showing even if the Google connection later expires (your history stays valuable), with a clear "reconnect to keep updating" notice.
- Built entirely on the existing Google connection — no new setup, no extra permissions. Reuses the same one-click OAuth and encrypted token storage.

---

## [2.66.96] - 2026-08-26  ·  _Patch_
**Advanced SEO: second deep pass (contracts + content-torture)**

### Improved
- On installs without the Advanced SEO plugin (or with it disabled), the SEO Overview page now shows a "More SEO tools" strip linking Heading Fixer, Auto Internal Links, Featured Images, Orphan Content, Year Updater, Slug Repair and the redirect manager — previously those shipped but were unreachable.
- The auto-linker progress log is now fully bilingual for English admins.
- The two SEO score engines (editor dial vs SEO panel) now use the same title/description length thresholds, so a post no longer shows two different scores in the two places.
- Meta text truncation is multibyte-safe (an em-dash at the cut boundary can no longer produce a broken character), and the AI image generator now stores featured images as an uploads-relative path so size variants and AVIF/WebP negotiation work and no dev URL leaks into social cards or the sitemap.
- The auto-link ledger is no longer age-pruned, so posts linked months ago don't revert to "orphan" and get a duplicate link.

### Fixed
- The editor's "Canonical URL", "OG Title/Description" and "Twitter Title/Description" fields now actually take effect on the live page — they were saved and shown in the admin preview but no theme ever emitted them, so republished/syndicated posts could not point search engines at the original source and social cards ignored your custom titles.
- Auto-generated focus keywords are Turkish-correct: a title containing İ (İstanbul, İş…) no longer produces a keyword with an invisible combining character that failed the analyzer's own "keyword in title" check and silently cost score points.
- The image alt-text fixer no longer corrupts alt values containing a dollar sign (deal/price titles) and no longer stamps the wrong description onto a different image whose filename ends with the same name ("a.jpg" vs "data-a.jpg"); it also stops mistaking a "data-alt" attribute for a real alt.
- Heading Fixer and Content Optimizer now leave headings inside HTML comments and code samples untouched, so a commented-out heading can no longer skew the fix and code examples are never rewritten.
- Renaming a post's slug and then renaming it back no longer creates an infinite redirect loop that made the post unreachable (the same loop-hygiene the year tool already had is now in the core rename path and slug-repair tool).
- SEO CSV import now maps columns by their header names instead of fixed positions, so a file built from the on-screen help no longer writes values into the wrong fields; it enforces the character limits, only touches non-empty cells (an empty cell no longer erases an existing value), validates robots/schema values, recomputes the score, and reports per-row errors.
- SEO Health Check no longer hides real "missing core file" errors as "could not be measured" when the site can't reach itself, and it no longer pulls the entire post corpus into memory when scanning for numbered lists.
- Redirect targets keep their query string, and a legacy protocol-relative redirect can no longer become an open redirect on the marketing site.
- SERP Identity Check reads values containing an apostrophe correctly ("Maggie's Kitchen" no longer reports a false mismatch).

---

## [2.66.95] - 2026-08-26  ·  _Patch_
**Advanced SEO panel: deep audit of all 16 tools**

### Improved
- SEO Health Check is faster and more honest: on hosts where the site cannot reach itself it stops after one connection attempt instead of blocking for a minute, marks the affected checks as "could not be measured" instead of inventing phantom schema errors, and category/author/content-quality counts now use the same visibility rules as the real sitemap.
- SERP Identity Check never certifies "clean" when the live chain could not be measured, failing checks now show the expected-vs-actual values, and its HTML parsing tolerates attribute order and single quotes (fewer false alarms with custom themes).
- Generated image alt text is Turkish-aware (İstanbul stays İstanbul), media-library fallbacks no longer keep the file extension, and the alt fixer no longer produces a duplicate alt attribute when the image tag lists alt before src.
- The SEO tools' heavy statistics scans now run only on the tabs that display them, making the other tabs noticeably faster on large sites.

### Fixed
- Heading Fixer no longer flattens sub-headings: content starting at H3 keeps its H4/H5 structure when shifted up (previously every heading could end up as H2, which also broke theme-generated tables of contents).
- "Send All Posts to IndexNow" now submits only publicly visible, indexable posts — member-only, private and noindex posts are excluded from the batch and from the counter.
- The single-post "Fix" button on the Content SEO tab now fills only the missing meta fields, matching "Fix All" — a hand-written meta title is no longer replaced when only the description was missing.
- The inline meta editor caps titles and descriptions at the real database budget (70/160 characters), so very long entries save cleanly instead of failing with a generic error.
- "Ping Sitemap" reports the real result: the retired Google/Bing ping endpoints no longer produce a false green success — the button now submits the sitemap via IndexNow and shows what actually happened.
- Slug Repair keeps its promise: repaired slugs now create automatic 301 redirects, only genuinely broken slugs are touched by default (hand-tuned slugs stay), and a new opt-in mode regenerates everything from titles when you really want that.
- Year Updater now also updates the SEO title used in Google results (previously only the on-page heading changed while the search snippet kept the old year), and running it back and forth can no longer create redirect loops.
- Redirect manager refuses rules that would loop (A→B while B→A exists, or a redirect pointing at itself via the full site URL) — these previously took the page down with an endless redirect.
- The "fix old URLs" scanner and fixer now share one pattern list built from your own site address, so the banner count and the actual fix always agree (the fixer previously used a stale fixed list and fixed nothing on most sites).
- Batch scans (strip links, fix URLs) use cursor paging so a row the transform cannot change no longer makes the progress loop run forever.
- Auto-linker and Orphan Content now handle Turkish İ/ı correctly — titles containing İ (İstanbul, İş...) can finally receive automatic internal links — and only publicly visible posts are suggested or linked.
- Content Optimizer preserves code blocks: cleanup no longer collapses indentation inside pre/code samples, keeps intentionally empty anchor/placeholder elements, and "reset" no longer deletes the content backups that make revert possible.
- Several admin listing screens in the SEO tools now escape post titles and scan results before rendering, and a few tool endpoints that write content are now administrator-only.

---

## [2.66.94] - 2026-08-26  ·  _Patch_
**Post SEO analyzer: accuracy fixes and new checks**

### Improved
- Two new writing checks in the SEO analyzer: a transition-word check (are your sentences connected for flow?) and a long-section check (a stretch of 300+ words with no subheading is now suggested for a subheading) — both work in Turkish and English.

### Fixed
- The live SEO score now judges the title by its full rendered length (your title plus the " | Site Name" the theme adds), so a title that looked fine but gets cut off in Google is now flagged — and the SERP preview's length number matches what is actually shown.
- Internal vs external link counting is corrected: a protocol-relative link to another site ("//example.com/…") is no longer miscounted as an internal link.

---

## [2.66.93] - 2026-08-26  ·  _Patch_
**Migration/import and support module hardening**

### Improved
- The WordPress migrator plugin (for exporting a WordPress site) now writes its export into a private, per-run randomized folder and deletes the intermediate data files right after packaging, so an export can't be pulled from a predictable URL on servers where directory rules aren't enforced.

### Fixed
- Imported content from every WordPress path (CSV, package and REST) now passes through the same content-cleaning step the editor uses, so a hand-edited export or a compromised source site can no longer smuggle active markup into your published posts.
- The REST and wizard migration tools are now administrator-only (they create posts and users and fetch remote content), and the wizard's per-post import step now requires a valid security token — matching the rest of the admin panel.
- Imported posts with an unknown status now land as drafts (in the review queue) instead of going straight live.
- Support ticket attachments can be downloaded again — the download link pointed at a page that did not exist, so staff could attach files but never open them; downloads are now served admin-only through a path-checked handler.
- Support ticket status and priority updates are validated against the allowed set, and the average-resolution-time metric now uses the real resolved/closed timestamps.

---

## [2.66.92] - 2026-08-26  ·  _Patch_
**SEO plugins audit: social, distribution, Google, recipe**

### Improved
- Hardening across the SEO surface: social share links now use the canonical URL (so shared and syndicated links never point at a redirect), recipe structured-data text fields are stripped to plain text as Google expects, the browser-push subscribe endpoint is restricted to real push services (SSRF hardening) with a proper per-IP rate limit, and shipped recipe/quiz scripts and push fallback text no longer leak Turkish onto English sites.

### Fixed
- Auto-publishing to social networks no longer broadcasts private, members-only, paid or password-protected posts — only fully public posts are shared, and a gated post's social description can never fall back to its full body (which also protected the Dev.to/Hashnode full-body syndication).
- The Google panel's GA4 / Tag Manager / AdSense settings actually take effect now — they were wired to a hook the themes never call, so enabling analytics in that panel injected nothing. They now flow through the site's single, consent-aware analytics injector, so there is one tag set (no double-counting) and cookie-consent is respected.
- The IndexNow "ping on publish" switch is now a real switch — instant indexing could not actually be turned off before, and the panel's "last submit" status was always blank; it now reflects real submissions.

---

## [2.66.91] - 2026-08-26  ·  _Patch_
**Quiz plugin: premium polish and reliability**

### Improved
- Result sharing is more robust: X, WhatsApp and Facebook buttons always appear (previously the whole share row vanished on some browsers), a native share sheet is offered on mobile, and copy-link stays where the clipboard is available.
- Keyboard support: press 1–9 to pick an answer and Enter to advance — faster and more accessible play.
- The public play endpoints are now rate-limited against flooding, the instant-feedback endpoint too, and answer keys are returned only for the questions actually answered (no leaking a whole question bank).
- Completion IP addresses in the stats screen are now masked for privacy, and the standalone quiz page no longer shows its title twice.

### Fixed
- Embedded quizzes could render with no styling and never start on themes that build a table of contents (they parse the post twice) — the quiz's stylesheet and script are now emitted on every embed, so quizzes always work wherever [quiz] is placed.
- The question/answer image picker stored an absolute URL that the front-end then prefixed again, producing broken images; picked images are now stored correctly and existing broken paths are healed automatically.
- Deleting a quiz now removes its questions, answers, result bands and play records instead of leaving them orphaned, and editing a quiz no longer accumulates dead answer rows; a one-time cleanup clears any leftovers on upgrade.
- Typing a slug that already belongs to another quiz no longer errors and loses your edit — it is made unique automatically.
- Personality quizzes ignore the question-bank subset setting so every result band stays reachable and two identical answer sets always give the same result.

---

## [2.66.90] - 2026-08-26  ·  _Patch_
**Theme customizer: numeric dropdowns now save correctly**

### Fixed
- In the theme customizer, dropdown fields whose choices are numbers (for example the Recipes and Travel themes' "Grid columns" 2/3/4 selector) silently reverted to the default whenever you picked a different value — the saved value now sticks. All 14 themes' customizer fields were verified end to end (513 fields across colors, fonts, ranges, toggles, selects, code and image inputs) and theme switching, preview and one-click rollback were confirmed to keep a single clean settings row.

---

## [2.66.89] - 2026-08-26  ·  _Patch_
**Newer-plugin audit: audience, editorial, edge & forms**

### Improved
- The editorial kanban board now supports real drag & drop between stages (the card's owner, date and note are preserved), overdue due-dates are highlighted, and editors — not just administrators — can use the board; plugin shortcuts in the admin sidebar are shown only to roles that can open them.
- CRM quality-of-life: a per-contact delete button (for erasure requests), segments show how many members are actually e-mailable, the contact list says when it is truncated, and the activity timeline no longer mixes in other people's form submissions for addresses containing wildcard characters.
- A/B tests: editing, activating or deleting an experiment now clears the page cache immediately (a just-activated test could look dead for the cache lifetime), the winner trophy waits for a sufficient sample, and equal conversion rates are compared exactly.
- Digital downloads and form autoresponders now throttle outgoing e-mail per recipient/site-wide, form values have a sane length cap, and the Cloudflare panel explains that HTML is only edge-cached if you add a Cache Rule.

### Fixed
- Audience (CRM): unsubscribed and bounced newsletter contacts are no longer pulled into the audience or its CSV export, the export now carries a newsletter-consent column and streams any list size, contacts deleted at their source are removed on the next refresh, and the audience is refreshed automatically right before a segment broadcast so late subscribers are included.
- Editorial calendar: scheduled posts now actually appear on the calendar on their scheduled day (they were invisible before), a post set to pending elsewhere shows in the Review column, moving a card can no longer race a simultaneous publish, and permanently deleting a post cleans up its planning card.
- Web push: the plugin's settings no longer share storage keys with other plugins (toggling ZeroTrack could silently switch push off and vice versa — existing settings migrate automatically and VAPID keys are preserved so subscribers stay valid), the click counter only accepts clicks for real recent broadcasts with sane limits, and clearly-rejected fake subscriptions are pruned faster.
- Cloudflare: turning "I'm Under Attack" on now reports an error if the API call failed instead of a false success, edge cache purges no longer block post/settings saves (they are queued and sent once per request, also removing duplicate purge calls), scheduled posts published by a real system cron now purge the edge too, and a failed reconnect no longer leaves the panel in a half-connected demo state.
- Analytics real-IP: on sites directly behind Cloudflare, visitor IPs are now resolved from the edge header (validated against Cloudflare's official ranges), so unique-visitor counts, IP exclusions and the flood limiter work correctly instead of collapsing onto a handful of edge IPs.
- Form Builder: renaming a field's label no longer silently detaches historical submissions from their CSV/archive column (machine names are now persisted), field names can't collide with the hidden system fields, and forms embedded on cached pages no longer double-submit with a failed first attempt.

---

## [2.66.88] - 2026-08-26  ·  _Patch_
**API authorization & content hardening**

### Fixed
- The automation/REST API now enforces the same role permissions everywhere: creating or deleting posts through the webhook endpoints, and managing categories, tags or comment moderation, now require the proper role — previously any valid API token could do these regardless of the account's role.
- Automation endpoints can no longer edit or delete another author's post, reassign a post's author, or save unsanitized HTML through the bulk publish/import paths (which could inject scripts) — ownership, byline and content cleaning now apply on those paths too.
- The bulk AI analysis job (which sends every post to the AI provider) now requires an administrator, and the per-post AI analysis is rate-limited, so a lower-privileged account can't burn through the site's AI key or quota.
- Search result pages on three themes now count matches the same way the list is built, so the pagination total is accurate and no empty "phantom" pages are produced.
- The marketing newsletter sign-up rate limit is now server-side (it could previously be reset by clearing cookies), the blog RSS feed pins its URLs to the real domain, and a saved post with an unparseable status value defaults safely instead of erroring.

---

## [2.66.87] - 2026-08-25  ·  _Patch_
**Concurrency, scale & integrity deep-audit**

### Fixed
- A scheduled post is now published exactly once even if two schedulers happen to run at the same moment, so it can no longer fire duplicate auto-shares, duplicate newsletter sends or duplicate push notifications.
- Deleting a category through the API now refuses when posts are still attached (matching the admin panel), instead of silently stripping those posts of their category.
- Newsletter open and click counts are now counted atomically, so inbox pre-fetching (Gmail/Apple Mail) can no longer inflate the numbers with duplicate counts.
- Comment threads with thousands of replies now build in milliseconds instead of seconds — the threading was rebuilt to scale linearly.
- Dates that can't be parsed (e.g. a malformed or empty value from an old import) now render as blank instead of "1 January 1970", and a post scheduled with an unparseable date is held as scheduled instead of quietly going live immediately.
- Hardening & cleanup: the analytics beacon now ignores spoofed forwarded-IP headers and is flood-limited; the A/B conversion link only counts same-site clicks; saving a site-wide OG image now requires an admin; permanently deleting a post cleans up its view/reaction/rating rows; and login-link tokens plus old newsletter queue rows are now pruned so they don't grow forever.

---

## [2.66.86] - 2026-08-25  ·  _Patch_
**Search, ads, quiz & security sweep**

### Fixed
- Instant search now actually uses the fast full-text index instead of silently falling back to a slow full-table scan on every keystroke, and the endpoint is rate-limited so it can't be hammered.
- Device-targeted ads are no longer frozen across devices by the page cache: the cache now keeps a separate copy per device class, so mobile visitors get mobile ads and desktop visitors get desktop ads instead of whichever device loaded the page first.
- Members/paid posts no longer leak their in-body images and embedded videos through the image and video sitemaps — only genuinely public posts contribute body media there (the cover image still appears, as before).
- Two-factor setup now refuses to enable if the secret can't be stored encrypted, instead of quietly saving it in plain text.
- Deleting a media file that's still used in posts now warns you it was in use (so broken image links aren't a silent surprise), and the download store limits how often the same email address can be sent a link (stops link-spam to someone else's inbox).
- Contact/lead forms: the form-builder honeypot no longer uses a field name that browsers autofill, which was silently dropping some genuine submissions; the quiz block now prints its stylesheet/script once per page even with multiple quizzes.

---

## [2.66.85] - 2026-08-25  ·  _Patch_
**Editor, cache & membership audit**

### Fixed
- Autosave no longer touches a published post's live body: while you edit a post that's already online, the background save keeps your draft in the revisions list instead of pushing half-finished edits to the live page — nothing goes public until you press Update. New pages also keep their type instead of turning into blog posts.
- Members/paid recipe posts now keep the ingredient list, steps and structured recipe data behind the paywall — the card, the FAQ and the page's recipe schema are shown only to signed-in members, matching how the article body is gated.
- The page cache now refreshes correctly when you trash or restore a post or add a redirect, so removed content and new redirects take effect immediately instead of lingering for the cache lifetime. Cookie-free visitors also always get the site's default language, ending a case where the first visitor's language could stick for others.
- Editor hardening: the button block now rejects javascript:/data: links like the other blocks, content saved by non-admin authors is cleaned server-side, the SEO panel escapes check text, and restoring a revision keeps your hand-picked URL instead of regenerating it from the title.
- Importing images from another site is bounded and hardened further — a per-image size ceiling, certificate verification, and a pinned resolved address stop an oversized or tampered image from stalling the import.
- Storefront: the checkout success page now shows the license key only in a short window right after payment (it's always in your email and portal too), and the update-check endpoint is rate-limited and no longer reflects arbitrary origins.

---

## [2.66.84] - 2026-08-25  ·  _Patch_
**Full-session audit hardening**

### Fixed
- For members/paid posts, the page meta description, social share tags and RSS fallback now stay inside the free teaser, so the summary shown to search engines and shared links never draws on gated text.
- Importing images from Ghost/Substack is now SSRF-hardened: image URLs from the uploaded file are checked to be public addresses (internal/cloud-metadata hosts are refused), redirects aren't followed, and oversized images are skipped so one bad file can't stall the import.
- Outgoing webhooks are bounded so an unreachable endpoint can't slow down publishing; deliveries that don't fit the window are logged as deferred and can be re-sent, and a webhook is refused rather than created if its secret can't be stored securely.
- Editor links now reject javascript:/data: URLs like the other card blocks, the snippet endpoint always returns clean JSON, reaction counts are shown only for public posts, and fast double-clicks on a reaction no longer error.

---

## [2.66.83] - 2026-08-25  ·  _Minor_
**Webhook delivery log & one-click re-send**

### Improved
- Each outgoing webhook now shows its recent deliveries right under it — the event, the response status (success or the exact HTTP error), and when it happened. If one failed because your endpoint was momentarily down, a single "Re-send" button replays that exact payload with a fresh signature. The log keeps the last 100 deliveries per webhook and never stores your signing secret.

---

## [2.66.82] - 2026-08-25  ·  _Minor_
**Ghost/Substack import now brings your images too**

### Improved
- When you import from Ghost or Substack, the images in your posts (and each post's cover) are now pulled into your own media library and converted to AVIF/WebP, and the post is rewritten to point at the local copies. Your migrated content keeps working even after the old site goes offline — no more hotlinked images that break later. It's a single checkbox on the import screen (on by default), matching the WordPress importer.

---

## [2.66.81] - 2026-08-25  ·  _Patch_
**Multilingual archives & API stability**

### Fixed
- On multilingual sites, category, tag and author pages, related lists and widgets now show only your site-language posts again; translated posts stay reachable at their own address and are still discovered through their hreflang links.
- The REST API and magic-link sign-in now work reliably on every install, including brand-new ones, and importing from Ghost/Substack cleans up correctly even if the file has an error.

---

## [2.66.80] - 2026-08-25  ·  _Patch_
**Deep audit hardening across membership, webhooks, editor & multilingual**

### Fixed
- Content gating is now consistent everywhere: /llms-full.txt, instant search and the About/Contact/FAQ/legal/homepage page routes all apply the same members/paid/private visibility gate as the rest of the site.
- Outgoing webhook signatures are now verifiable: the HMAC was being computed with the encrypted secret instead of the plaintext (a column length also truncated it), so every signature failed on the receiver — fixed end to end.
- A webhook signing secret can no longer be used as an admin API key.
- Newsletter segment sending can no longer silently fall back to the entire subscriber list when the CRM is unavailable or errors — it sends to nobody rather than everybody.
- Reply notifications no longer fire for unapproved/spam comments, so moderation-pending replies can't spray the whole thread by email.
- The paywall teaser is now safely capped even on very short posts, and the reaction bar can now be un-clicked and switched correctly with counts always coming from the server.
- Editor hardening: the snippet library and the bookmark fetcher are now restricted to content roles (not read-only subscribers); the bookmark fetcher pins the validated IP (DNS-rebinding), enforces a hard size cap, and resolves relative images correctly; product/bookmark/gallery/embed card links reject javascript:/data: URLs; the gallery block is now clickable and the four new blocks have their edit/delete toolbar.
- Magic-link sign-in/registration is now rate-limited (anti email-bombing), tokens are single-use under concurrency, and the new-member webhook fires only after the email is verified.
- Ghost/Substack import no longer triggers per-post newsletter/push/social/ping storms, survives BOM and malformed CSV rows, only raises the memory limit, maps Ghost visibility, and skips empty lexical-only posts.
- Multilingual: the language filter no longer breaks reactions, comments, pages, comment feeds or legacy-URL rescue on translated posts — it now applies only to genuine listing surfaces (archives, sitemap, feeds, search) while every translated post stays reachable at its own URL.

---

## [2.66.79] - 2026-08-25  ·  _Minor_
**Multilingual content v1 + Ghost/Substack migration**

### Improved
- Multilingual content v1: give any post a language and link it to its translated counterpart from the editor's new Translation box. Linked pairs automatically emit hreflang alternate tags (plus x-default) so search engines serve the right language; archives, sitemap and feeds keep showing only the site language while translated posts live at their own URLs.
- A practical translation workflow ships with it: Duplicate the post, switch the copy's language, link it back by ID — done. No plugin, no separate site.
- Migrate from Ghost: upload the JSON export from Ghost admin and posts, pages, drafts, tags, publish dates and feature images come across — safe to re-run, existing slugs are skipped.
- Migrate from Substack: upload the export ZIP as-is and newsletter posts import with their full body and subtitle; "paid-only" posts automatically arrive with Premium (paid) visibility, matching the membership system one-to-one.

---

## [2.66.78] - 2026-08-25  ·  _Minor_
**Integrations & engagement: webhooks, segments, reactions**

### Improved
- Outgoing webhooks are now real: pick events (post published/updated/deleted, new comment, new member), add an HTTPS URL, and jekcms sends signed JSON (HMAC signature header) the moment they happen — Zapier/n8n/Make ready, with a one-click test button.
- Newsletter campaigns can target CRM segments: choose a saved audience filter when sending and only matching active subscribers receive it — the "coming soon" broadcast gap is closed.
- Comment conversations now notify the whole thread: everyone above a new reply is emailed once (deduped), and every notification carries a one-click, tamper-proof opt-out link.
- Emoji reactions arrived on every theme: a theme-independent reaction bar appears under posts with live counts served from the API — fully compatible with the full-page cache; themes with their own reaction UI are automatically skipped.

### Fixed
- A leftover placeholder in the cron was silently marking the social-media queue as completed without doing any work — removed; the social plugin's queue is no longer swallowed.

---

## [2.66.77] - 2026-08-25  ·  _Minor_
**Editor: monetization cards, gallery, social embeds and snippets**

### Improved
- A Product/Affiliate card joined the editor: image, price, description and a call-to-action button whose link automatically carries rel="sponsored nofollow" — Google-compliant affiliate monetization in two clicks.
- Bookmark cards turn any URL into a rich preview: paste a link, hit Fetch, and the title, description, image and site name are pulled server-side (with strict SSRF protection) into an editable card.
- Gallery grids (2-4 columns) and social embeds arrived: Twitter/X, Instagram, TikTok and Vimeo links become real embeds on the page — the editor stores a neutral placeholder and the site hydrates it, so provider scripts load once and only where used.
- Snippets make repeated content one click: select anything in the editor, save it under a name, and insert it into any future post from the snippet library.

---

## [2.66.76] - 2026-08-25  ·  _Minor_
**Premium (paid) membership tier**

### Improved
- Posts can now be marked "Paid members only": anonymous readers get a premium teaser with a join call, signed-in free members see an Upgrade card with your price and payment link, and premium members read everything.
- Selling is friction-free by design: paste any payment link (iyzico or Stripe payment page) plus an optional bank-transfer note in Settings, and when a payment arrives, one click on the Users screen upgrades the member — no gateway integration to configure.
- The member account page shows premium status and the upgrade offer; staff accounts always see full content, and paid posts stay in sitemaps and feeds as leak-proof teasers with correct paywall structured data.

---

## [2.66.75] - 2026-08-25  ·  _Minor_
**Memberships: members-only content and passwordless sign-in**

### Improved
- Ghost-style memberships arrived: mark any post "Members only" and anonymous readers see a clean teaser with a join call-to-action while signed-in members read the full piece — on every theme, with zero theme changes.
- Readers join and sign in without passwords: a one-time magic link lands in their inbox (30-minute, single-use), a minimal account page lets them manage their name and newsletter subscription, and joining doubles as newsletter double opt-in.
- Members-only posts stay fully SEO-correct: they remain in sitemaps and feeds as teasers, never leak the gated body anywhere, and carry Google's official paywalled-content structured data so gating is not mistaken for cloaking.
- One-click post duplication (content, categories, tags and metadata copied into a fresh draft) joined the post list actions.
- Your content is never locked in: a new Export panel downloads everything as WordPress WXR, Ghost JSON or jekcms JSON — categories, tags and SEO fields included.

---

## [2.66.74] - 2026-08-25  ·  _Patch_
**Full-page cache: millisecond pages for visitors**

### Improved
- A textbook full-page cache now serves the homepage, single posts, category, tag, author and date archives to anonymous visitors straight from disk — measured locally, pages dropped from 60-200ms to 4-9ms.
- Cached copies are invalidated exactly when content changes: saving a post, moderating a comment, editing categories/tags/menus/users, changing settings or the theme all clear the right copies immediately; a small share of requests still runs the full engine so scheduled tasks keep ticking.
- Comment and contact forms became cache-safe: the security token is no longer baked into the page — it is fetched the moment a visitor actually starts filling a form, so anonymous browsing stays completely cookie-free.

### Fixed
- Every single visit was silently receiving a session cookie because the user loader started a session even when there was nothing to load — this broke the lazy-session design site-wide and made pages personally-addressed for no reason.
- Two themes' view counters opened a session per article view; they now use the cookie-free central counter, and A/B-test pages, dark-mode/language-cookie visitors and search results are correctly excluded from the cache.

---

## [2.66.73] - 2026-08-25  ·  _Patch_
**Deep performance pass: queries, caching and page weight**

### Improved
- Repeated database work was eliminated across the board: prepared statements are reused, per-image lookups are memoized, sidebar aggregations are cached, empty results now cache correctly, and hot columns gained indexes.
- Theme pages got lighter: template-specific stylesheets load only on their own template, mobile-only CSS no longer blocks desktop rendering, fonts load from the page head instead of a chained CSS import, and analytics/ad hosts get an early connection.
- Saving a post now runs its category/tag/meta writes in a single transaction, and archive pages batch-load categories instead of querying once per card.

### Fixed
- Six plugins were silently re-running their entire installation schema on every single page view due to a settings-key collision — the single biggest hidden cost on every site; pages now run dramatically fewer queries and zero writes.
- The featured-image helper returned the full-size original instead of the 1600px variant, so every theme preloaded multi-megabyte camera files as the hero image; the preload also now matches exactly what the browser will render.
- Browsers were told to keep HTML pages for a full hour with no way to refresh them — edits stayed invisible to returning visitors; pages are now edge-cached and browser-validated, and category/tag edits and new posts invalidate the right caches immediately.
- Sitemaps and feeds are written atomically with a generation lock — parallel crawler hits could previously read half-written XML or trigger simultaneous full regenerations.

---

## [2.66.72] - 2026-08-24  ·  _Patch_
**Categories, archives and search: deep SEO pass**

### Improved
- Categories gained their own SEO title and SEO description fields in the admin panel, and parent categories now count and list their child categories' posts everywhere — archive pages, indexing rules and the sitemap agree.
- Site search now ranks results by relevance instead of date on every theme, search page titles are capped against keyword-injection spam, and paginated search links finally carry the query along.
- Date archives (old /archive/2026 style addresses) now get a descriptive page title, paginated archive pages carry a page number in their description, and every theme reports its real page size in structured data.
- The site description used by feeds and previews became editable in Settings — until now every installation shipped the same boilerplate sentence — and the homepage title can carry the site tagline.

### Fixed
- Address-case variants of category, tag and author pages now redirect to the single canonical address instead of serving duplicate self-canonical copies, and deleted tags leave a proper "gone" record so search engines drop them quickly.
- Two themes silently lost every category description from search snippets over a variable-name mismatch, one theme pinned paginated archives' canonical to page one, and tag pages on two themes either listed the whole site or rendered without a title.
- Tag feeds became real: following a tag's feed used to silently hand subscribers the site-wide stream; category and tag feeds also stopped claiming to be the main feed, and feed images now declare their true format.
- Homepages that paginate now return an honest not-found beyond the last page and give page two and onward their own title and canonical; the theme demo search-blocking robots rule that hid the blog search's noindex from Google was lifted.

---

## [2.66.71] - 2026-08-24  ·  _Patch_
**Single posts and author pages: deep SEO pass**

### Improved
- Author pages now carry a full social-profile card: stable identity across paginated pages, a real profile picture in link previews, richer profile structured data, and each author's own posts listed correctly on every theme.
- Article structured data now reports the approved comment count, and social share cards gained an image description, a reading-time line and the post's topic tags.
- Every theme's post page now shows the publish date in a machine-readable form, and the "Updated" stamp only appears when the content genuinely changed.

### Fixed
- Bylines no longer invent a writer: when a post has no real author profile the name is shown as plain text instead of linking to an author page that never existed.
- The table of contents on the news theme now works on markdown-written posts, previous/next links on the starter theme point at the real post address, and the pets theme no longer emits a half-finished second copy of article metadata that contradicted the main one.
- Author boxes that were silently invisible now render: one theme queried profile fields under their old names, another never received the author's biography from the page at all.

---

## [2.66.70] - 2026-08-24  ·  _Patch_
**SEO verification pass: second-round hardening**

### Fixed
- Database sessions now share the site's timezone, so a freshly published post appears in sitemaps immediately on every host instead of hours later on servers whose database clock runs in UTC.
- Sitemap index announcements now use exactly the same filters as the sitemap files themselves — no more announced-but-empty news/video maps, and trashed marketing posts finally disappear from the public blog, feed and sitemap.
- Old WordPress-style category/post addresses now hop straight to the real post, and every remaining "redirect to somewhere that 404s" chain (authors, categories, attachments, feeds, year archives) returns an honest not-found instead.
- The maintenance page now sends proper no-cache headers, uses the active theme's template, and error pages exist for every status the error route accepts.
- The theme demo gallery moved to a stable address (/demos) — its old address was shadowed on the server and had been unreachable from the navigation.
- Upload-folder protection files are written Apache-2.4-safe everywhere; on hosts without the legacy compatibility module they used to turn whole media folders into server errors. A permanent release-gate check now guards this class.

---

## [2.66.69] - 2026-08-24  ·  _Patch_
**Deep SEO audit: crawling, presentation and media layer**

### Improved
- Crawlers can now fetch core stylesheet/script assets and search pages, so pages are rendered and evaluated with their real design and noindex hints are actually readable.
- Sitemaps got stricter: entry dates no longer drift on every visit, image entries always point at working files, scheduled/future content never appears early, and news/video sitemaps respect per-post indexing choices.
- Titles across all themes now follow the configured separator, add a page number on paginated archives, and no longer repeat the site name twice; archive descriptions can come from the tag or author's own text.
- Structured data is more consistent: language, titles and image formats now match across the page's tags, FAQ/HowTo blocks can no longer be emitted twice, and the publisher logo is a raster image with its true dimensions.
- Modern-format (AVIF/WebP) image sources are only offered when the file really exists — on hosts without those formats the browser now always gets a working image instead of a blank box.
- More images carry explicit dimensions and descriptive alt text, the correct hero image gets load priority on every theme, and automatic internal links open in the same tab as expected.

### Fixed
- Addresses that do not exist now return a real "not found" status everywhere instead of silently redirecting to the homepage, so search consoles report them correctly and they drop out of indexes.
- Error responses are never cached as healthy pages anymore, and error/410 pages are proper, readable pages with charset, language and a link home.
- Duplicate-address cleanups: uppercase blog links, retired tag aliases, alternate sitemap/robots/feed addresses and www+http visits each collapse to a single canonical address in one redirect hop.
- Date archives are validated (invalid years return "not found") and marked not-to-be-indexed, closing a duplicate-content surface.

---

## [2.66.68] - 2026-08-24  ·  _Patch_
**Verification pass: admin panel fixes**

### Fixed
- Some admin confirmation and validation messages (for example the new password-policy warning when adding a user) were saved but never shown on screen; the panel now displays messages from both internal channels.
- On installations whose database was missing two optional pieces, the settings page could cut off mid-render and adding a user could fail with a server error; the missing pieces are now provisioned and both flows were verified end-to-end.

### Security
- Saved AI keys in the multi-key list are no longer written into admin page HTML; rows show a masked “saved” state and each key only changes when you type a new value — leaving a row untouched keeps the stored key.

---

## [2.66.67] - 2026-08-24  ·  _Patch_
**Security hardening: broad audit across the product and site**

### Security
- Uploaded files are kept strictly non-executable everywhere: the upload-folder protection is now stronger and self-maintaining, and the blocked-extension list covers disguised double-extension names.
- Content upload endpoints now require an explicit upload permission tied to the account's role.
- Editor/API secrets (AI provider keys, SMTP password, webhook secrets) are no longer written into admin page HTML; fields show a “saved” state and only change when you type a new value.
- Order pages are tightened: cancelling an order requires the owner and a confirmed action, and guest checkout is scoped to the buyer’s own account.
- Anti-abuse limits are now enforced server-side on the contact form, verification-email resend, comment likes, newsletter signup and article voting.
- Payment confirmation now verifies the paid amount and currency against the order before completing it.
- The one-click Google connection now only works from a licensed customer domain, and several login/authorization edge cases were closed.
- Error responses no longer include internal technical details, and internal maintenance/report files are kept out of public deployments.

---

## [2.66.66] - 2026-08-24  ·  _Patch_
**Compatibility: deep sweep for PHP 8.0 servers and lean setups**

### Fixed
- On servers running PHP 8.0 (the minimum supported version), several areas used a function that only exists in newer PHP: the site footer, the Personal theme and — most critically — the auto-update engine could crash. These now work on every supported PHP version.
- Publishing a post no longer depends on optional server pieces: the search-engine ping, encoding repair tools and the RSS import endpoint all degrade gracefully when a server component is missing, instead of stopping the whole operation.
- The installer now tells the truth about requirements: the cURL component (needed by updates, licensing and integrations) is checked as required rather than merely recommended, so problems surface at install time instead of weeks later.
- The pre-release safety check was deepened: it now also blocks any new code that would require a newer PHP than the product promises, alongside the existing optional-component guard.

---

## [2.66.65] - 2026-08-24  ·  _Patch_
**Resilience: missing server components can no longer crash any operation**

### Fixed
- Following yesterday's upload fix, the entire product was swept for the same class of failure — features assuming an optional PHP server component is present. On lean hosting setups this could crash: WebP image reading during WordPress import, migration and Pinterest image generation; AVIF/WebP saving in thumbnail regeneration and the media optimizer; image processing entirely on servers without the GD component (the upload now keeps the original file instead of failing); and update, backup and package operations if the zip component is disabled. Every path now checks first and degrades gracefully with a clear message instead of a server error.
- This protection is now permanent: an automated check runs before every release and blocks any new code that uses an optional server component without a safety check.

---

## [2.66.64] - 2026-08-24  ·  _Patch_
**Critical: image uploads were completely broken on some servers**

### Fixed
- On hosting where PHP's optional "fileinfo" extension is disabled, every image upload failed with a "mime_content_type" error — the editor's image dialog, the Pinterest image and the media library were all affected. The file type is now detected through a chain of safe fallbacks (including reading the image header directly), so uploads work on every hosting configuration. If your uploads were failing, update and try again — no other action needed.

---

## [2.66.63] - 2026-08-23  ·  _Minor_
**Google Console: weekly email digest + rising/declining queries + opportunity list + cache fix**

### Added
- Weekly performance digest by e-mail: every week the plugin compares the last 7 days of Search Console, Analytics and AdSense with the previous week and sends a compact summary (with ▲▼ trends and the week's top queries) in the site language. Enable it in Settings; runs on the server cron, retries gracefully and never double-sends.
- Rising / declining queries: the Search Console tab now compares the selected period with the previous one and lists the queries that gained and lost the most clicks — including queries that disappeared entirely.
- Opportunity queries: keywords that show often in Google (ranking 4-20) but get few clicks — the fastest wins for title/description improvements, sorted by impressions.
- Pages losing traffic: content-refresh candidates ranked by click loss versus the previous period.

### Fixed
- The API response cache effectively never worked on servers where PHP and MySQL run in different time zones: expiry times were written with the PHP clock but checked against the MySQL clock, so every cached entry was born already expired (by the zone offset) and every panel visit hit Google's APIs live — this is why the panel could feel slow or unstable. Expiry is now computed on the database clock.

---

## [2.66.62] - 2026-08-23  ·  _Minor_
**Contact Form: reply from the panel + bulk actions + CSV export + phone field**

### Added
- Reply from the inbox: write your reply under the message and send it by e-mail without leaving the panel — the visitor receives it with their original message quoted, and the message is marked "replied" with the reply stored on the record. (The "replied" status existed but nothing ever set it; the old Reply button just opened your mail app.)
- Bulk actions: select multiple messages and mark read / spam / archive / delete in one go, plus one-click CSV export of the inbox (Excel-ready, with spreadsheet-formula injection neutralized).
- Optional phone field: enable it in settings and the form shows a phone input (validated loosely for international formats); the number appears under the sender in the panel and in the notification e-mail. Themes that pass their own field list are unaffected.
- Auto-reply personalization: the {name} tag in the auto-reply subject and body is replaced with the sender's name.
- Field-level error display on the form: validation errors now appear under the exact field and the first one is focused — the styling for this existed but was never used; visitors only saw a generic "check the form".

### Fixed
- Spam-flagged messages were stored without any cap — a bot flood could grow the table indefinitely (the "no message is ever lost" design kept everything). The newest 300 spam records are now kept and older ones pruned, matching the Form Builder's protection.

---

## [2.66.61] - 2026-08-23  ·  _Minor_
**Form Builder: conditional logic + multi-step forms + smarter validation**

### Added
- Conditional logic: any field can be shown only when another field meets a condition (equals / does not equal / is empty / is not empty / contains). Hidden fields are skipped by validation and never stored — the server re-evaluates every condition itself, so hand-crafted requests can't smuggle values in.
- Multi-step forms: drop a "page break" between fields and the form turns into steps with a progress indicator and back/next buttons; each step validates before advancing, and with JavaScript off everything gracefully falls back to a single long form.
- Per-field error display: validation errors now appear under the exact field (with the wizard jumping back to the right step and focusing it) instead of a single generic message.
- Multi-checkbox groups: a checkbox field with options now renders one checkbox per option, with "at least one required" enforced in the browser and on the server. Previously the options were validated but never rendered — the form always showed a single box.
- Duplicate form action in the list, and "redirect after submit" now actually redirects in the no-page-reload (AJAX) flow too.

### Fixed
- A field saved without a width value (via the API or programmatically) crashed the save with an "Undefined array key" error; the admin form always sent a width, which masked it.
- The confirmation redirect URL is now validated when saving — non-http(s) addresses are rejected instead of being passed to the browser.

---

## [2.66.60] - 2026-08-23  ·  _Minor_
**Web Push: campaign composer + click statistics + welcome notification + background secret-decryption fix**

### Added
- Campaign composer: write and send any notification (title, message, target URL, large image) to all subscribers from the admin panel — until now the panel could only send a fixed test message.
- Broadcast history with click tracking: every send (new post, campaign, test) is logged with delivered/failed counts, clicks and CTR. Clicks are counted by a lightweight beacon from the notification itself — no third-party service, no personal data.
- Welcome notification: optionally greet each new subscriber with a one-time, customizable notification the moment they subscribe — they immediately see that notifications work.
- Configurable opt-in button: position (bottom left/right), custom label, show delay, and a dismiss (✕) that snoozes the prompt for a configurable number of days. Previously the button was fixed, undismissable and shown forever.
- Rich notifications: new-post pushes now carry the post's featured image as a large picture on supported platforms; campaigns can attach one too.
- Subscriber analytics on the panel: growth in the last 7/30 days and a browser breakdown.

### Fixed
- Background jobs (cron, deferred sending after the page is delivered) could silently fail to decrypt stored secrets: if any output had already been produced when the security layer initialised, session setup threw and decryption returned empty — for Web Push this meant the whole broadcast was silently skipped with an unusable VAPID key. Session configuration now degrades gracefully after output has started, so encrypted secrets remain readable in every background context.

---

## [2.66.59] - 2026-08-22  ·  _Minor_
**Quiz: premium engine (timer, instant feedback, question bank, weighted personality) + fixes**

### Added
- Time limit per quiz: a countdown runs while playing and the quiz auto-submits with the answers picked so far when time runs out.
- Instant feedback mode: as soon as the reader picks an answer, right/wrong (and the explanation, if enabled) is shown before moving on. Correct answers still never appear in the page source — each check is answered by the server, and the endpoint only responds for quizzes that opted in.
- Question bank: shuffle question order and/or serve a fixed number of questions from the pool on every run — each play gets a different quiz. Scoring uses the served count, not the pool size.
- Weighted personality engine: every answer can carry points and the result card is chosen by the point total — the standard model of premium personality quizzes. Trivia scoring is unchanged.
- Result sharing: copy link, X, WhatsApp and Facebook buttons on the result screen, with the score or personality result in the share text.
- Duplicate quiz action in the admin list, drag-to-reorder questions in the editor, and a working media picker for quiz, question and answer images (the old "Browse" button always fell back to "enter the URL manually").
- The standalone quiz page now emits Quiz schema (JSON-LD) — deliberately without questions or answers, so correct answers stay out of the page source.

### Fixed
- On themes that pre-parse content (e.g. to build a table of contents), the embedded quiz lost its stylesheet and script — questions never rendered. The assets now travel with every embed, and the view counter no longer double-counts on those themes.
- When editing an existing quiz, the field labels showed raw template code ("${QI18N.qText}") instead of text.
- The admin quiz screens mixed Turkish and English ("No quiz plays yet yok.", untranslated settings and buttons); the share image URL of the standalone quiz page was relative, so social preview cards came out empty.

---

## [2.66.58] - 2026-08-22  ·  _Minor_
**Recipe Cards: visual recipe editor in the post editor + premium card features**

### Added
- The post editor gained a full Recipe panel: structured ingredient rows (quantity, unit, name, note) with group headings ("For the sauce"), drag-to-reorder steps with optional step photos, minute-based time fields with automatic total, servings, difficulty, course/cuisine suggestions, nutrition facts and an FAQ builder. Until now this rich recipe data could only be produced by the AI content pipeline — writing a recipe by hand meant raw ISO-8601 duration codes in the SEO schema panel.
- Bulk paste: paste a plain ingredient list ("200 g flour") or numbered steps and the panel splits quantity, unit and name into rows automatically.
- Recipe video support: paste a YouTube, Vimeo or mp4 link — the card embeds the player and YouTube videos are added to the Recipe schema as a VideoObject (eligible for video rich results).
- Cook mode on the recipe card: one tap keeps the phone screen awake while cooking (on supported browsers; the button hides itself elsewhere).
- "Copy list" button on the card copies the ingredient list — including scaled quantities when the reader changed the serving count.
- Printing now prints only the recipe card, not the whole page; a Notes/tips box and step photos are shown on the card as well.
- The [recipe] shortcode places the card wherever you want inside the content — and works on every theme, not just the recipes theme.

### Fixed
- On a recipe post without a usable image, the plugin correctly skipped the Recipe schema node but silently dropped the FAQ schema with it — FAQ rich results were lost on exactly the posts that needed them. The FAQ schema is now emitted independently.
- Recipe difficulty was displayed in raw English data tokens ("easy") on Turkish sites; known values are now shown in the site language.
- Step photos were included in the schema but never shown to readers on the card; they now appear under their step.

---

## [2.66.57] - 2026-08-22  ·  _Patch_
**Stories audit: "Latest Posts" statistics + navigation fix**

### Improved
- The whole plugin was re-verified live: poll vote integrity, per-visitor replay windows, reaction-switch accounting, slide ownership checks and the sanity of the new virtual-story validation (unknown posts rejected, polls not accepted on the automatic story).

### Fixed
- Views, link clicks and emoji reactions on the automatic "Latest Posts" story were silently discarded by the server — visitors saw the reaction animation but nothing was ever counted, and the statistics page had no trace of the story most sites use the most. These events are now recorded (with the same replay protection as manual stories), reactions show up in the ambient emoji stream, and the statistics page gained a dedicated "Latest Posts" card breaking performance down per post.
- With "auto-advance to next story" turned off, swiping or tapping to the next story closed the viewer entirely instead of advancing. That setting now only controls what happens when a story finishes on its own — manual navigation always moves to the next story.

---

## [2.66.56] - 2026-08-22  ·  _Patch_
**Web Push audit: no subscriber misses a notification + dead-subscription cleanup**

### Improved
- When the browser rotates a push subscription, the service worker now re-subscribes automatically instead of silently going quiet. Sending got faster on large lists (the signed authorization is computed once per push service instead of per subscriber) and the delivery connection is explicitly TLS-verified with redirects refused. The whole plugin was re-verified live against a mock push service: crypto self-test, dead-endpoint pruning, budget cursor, tick lock and intake validation all confirmed.

### Fixed
- On sites with many push subscribers, publishing a post only notified as many browsers as fit into the sending time window — the rest simply never received that notification. Sending now remembers exactly where it stopped and continues in the background (server cron and page-triggered fallback, with a lock so no browser is ever notified twice) until every subscriber has been reached.
- Subscriptions that kept failing without properly expiring (persistent errors, unreachable endpoints) were retried forever on every publish, eating the sending window. After 8 consecutive failures a subscription is now cleaned up automatically.
- A subscription registered with a valid push service but corrupt encryption keys was accepted and then failed on every send; keys are now validated byte-for-byte at registration.

---

## [2.66.55] - 2026-08-22  ·  _Patch_
**AI Images audit: pin domain fixed + scaling and provider improvements**

### Improved
- The visual-concept helper now uses the same hardened network settings as image generation (strict TLS, no redirects, response size cap), and the generation log cleans up entries older than 180 days by itself. The whole plugin was re-verified live: concurrency lock, daily cap, image validation, oversized-response cut-off and redirect refusal all confirmed working.

### Fixed
- The "Pinterest / Recipes pin" style rendered a fixed website address into the bottom strip of every generated pin — regardless of which site generated it. The pin now carries the site's own domain automatically.
- The "posts with missing images" list loaded the full content of every published post into memory to count images; on a site with thousands of posts that could exhaust memory. Counting now happens inside the database and the screen stays fast at any size.
- With OpenRouter selected as provider, the settings screen still warned "no Gemini API key" and style-preview generation insisted on a Gemini key. Both now follow the selected provider.

---

## [2.66.54] - 2026-08-22  ·  _Patch_
**jekcms.com audit: contact form repaired + language redirect fixed**

### Improved
- The marketing site was audited top to bottom: 38 pages in both languages (render integrity, silent log noise, titles, canonical and hreflang tags, single H1), all 88 internal links, sitemap/robots/feeds/docs search, payment checkout links and both forms — everything else came back healthy. The "Try the admin panel live" band on the themes page now sits below the theme list, and a new automated suite guards the form pipeline against regressions.

### Fixed
- The jekcms.com contact form rejected every single submission with a "security token mismatch" error: the page stored its security token in one session while the receiving endpoint checked a different one, so the two could never match. The form now fetches a fresh token at the moment of submission — messages actually arrive and open a support ticket. The footer newsletter form carried a lighter version of the same risk and now uses the same always-fresh-token pattern.
- Opening a jekcms.com page with the ?lang=tr shortcut on a direct .php address redirected to a dead URL (for example /blog.php?lang=tr landed on a 404). The Turkish redirect target is now normalized to the clean address, and subdirectory installs no longer produce doubled paths.

---

## [2.66.53] - 2026-08-22  ·  _Patch_
**General audit: post reactions/ratings completed + silent error floods ended**

### Improved
- The whole automated test battery was run end to end — 65+ suites, 2,000+ checks, all green — covering plugins, themes, mail, licensing, installers, customer portal and admin access controls.

### Fixed
- The Entertainment theme's reaction buttons (🔥 ❤️ 😮) and star ratings were half-built: the interface was drawn and clicks were sent to the server, but the receiving endpoint never existed and the database tables were never created — counts always showed zero, reverted on reload, and every page view silently wrote errors to the log. The feature is now real end to end: one reaction and one rating per visitor (updatable), public-published posts only, rate-limited, and the tables create themselves on first use.
- The settings-change timeline (who changed which setting, with undo) had never worked: its query joined a table name that doesn't exist in the product, so the history always came back empty and every dashboard load added another silent error to the log. The audit found 1,600+ recorded changes that are now actually visible.
- Small persistent warnings cleaned up across jekcms.com: the admin invoice list read a wrong column name for due dates (overdue highlighting never fired), 404 pages warned about a missing canonical URL, the blog listing warned on every load, and two 2.65-era changelog entries had no title and rendered a warning on the public changelog page.

---

## [2.66.52] - 2026-08-22  ·  _Patch_
**Customer accounts: clear verification flow + session security**

### Improved
- One password policy across the whole customer portal (register, reset, profile, sign-up modal): at least 8 characters with a letter and a digit, and obvious passwords are rejected — "12345678" is no longer a valid password for an account that holds licenses and purchase history. Both blog-site user management and the customer portal were audited end to end on a live environment: brute-force lockouts, role whitelists, IDOR scoping on orders/tickets/invoices/licenses, OAuth account-linking protections and 2FA flows all verified working.

### Fixed
- An unverified customer account was silently bounced back to the sign-in page in an endless loop with no explanation — right after registering, after signing in with the correct password, and after changing the email address on file. Every entry point now explains what happened and links to "resend verification email"; registration no longer opens a session that gets dropped one request later, and changing your email signs you out cleanly with a clear note instead of appearing to crash.
- Profile password changes and admin-side password resets now bump the session version, so every other signed-in device is signed out immediately — only the device that changed the password stays in.

---

## [2.66.51] - 2026-08-22  ·  _Patch_
**Editor SEO assistant: score verified live + 4 new checks**

### Added
- The post editor's SEO assistant gained four new checks, shown only when the issue actually exists: a stale year in the title (e.g. "2024 guide" in 2026), heading sections with no content under them, generic link text like "click here", and long articles (1000+ words) with fewer than two images.

### Improved
- The SEO score engine was verified end to end in a real browser: a blank draft scores exactly 0, Turkish dotted-İ keyword matching and inflected-word density counting work, over-density and readability warnings fire correctly, and on every scenario the dial score matches the sum of the per-category points exactly. The computed score is also confirmed to be saved with the post and shown in the post list.

---

## [2.66.50] - 2026-08-21  ·  _Patch_
**Newsletter: campaigns now send themselves**

### Improved
- The whole subscription pipeline was audited end to end on a live site: sign-up protections (honeypot, rate limit, spam filter, mail-bomb cap, address-disclosure parity), double opt-in with token rotation, one-click unsubscribe headers, open/click counters with signed links, and bounce pre-flight all verified working.

### Fixed
- Newsletter campaigns only went out while an admin kept clicking "send next batch", or on servers with a manually configured cron job; on a typical installation a campaign larger than one batch — and every automatic new-post notification — sat in the queue forever. The queue is now processed automatically: the built-in scheduler drains it in small batches as the site gets visits, and the server cron (where present) drains it in full — with row-level locking so the two never send the same email twice, and nothing is sent while the newsletter is disabled or the plugin is deactivated.

---

## [2.66.49] - 2026-08-21  ·  _Patch_
**Visual theme audit: readability and dark-mode fixes**

### Fixed
- Every theme was rendered in a real browser in both light and dark mode and measured for text readability; unreadable spots were corrected across nine themes — badge and button text on bright brand colors, faded date/muted text, table-of-contents boxes and post cards that stayed white in dark mode, a newsletter band whose white text vanished on its yellow gradient, and an oversized content image that forced horizontal scrolling.
- When you pick a light brand color in the customizer, badge/button text on that color now switches to dark automatically (and link-style brand text is deepened just enough to stay readable) instead of staying white and disappearing.
- The travel theme's default menu no longer links to pages that don't exist on the site; "Destinations/Tips" entries appear only when a matching category exists and point straight to it.
- The shared sidebar widgets (tags, categories, recent posts) now stay readable in dark mode on every theme, even when a theme doesn't define its own dark palette for them.

---

## [2.66.48] - 2026-08-21  ·  _Patch_
**Theme audit: broken-image safety net + graceful demo-media fallback**

### Added
- A new deep theme audit exercises all 13 themes across eight page types each — checking rendering, single H1, canonical tags, encoding, leaked shortcodes, layout-section contracts and every referenced asset. All 517 checks pass on both an English and a Turkish site.

### Improved
- The travel theme's showcase images (front-page slider, about page, archive banners) now appear only when the files actually exist on the installation; sites without the demo media pack get a clean dark banner instead of broken image icons.

### Fixed
- Content written on a development machine could carry "localhost" image addresses into the live site, showing readers broken images (one live post was affected and has been repaired). Rendering now silently rewrites such development addresses to the site's real address — only inside image and link attributes, so articles that mention localhost in their text or code samples are untouched.
- The finance theme linked an apple-touch icon file that doesn't ship with the theme, producing a broken request on every page; the icon already comes from the site's central favicon pipeline, so the stray link was removed.

---

## [2.66.47] - 2026-08-21  ·  _Patch_
**Site Versions screen + lasting analytics history + cleanup**

### Added
- License server: a new "Site Versions" screen lists every licensed installation that checks in with the update server — its domain, last reported version, PHP version and last-seen time — and flags at a glance which sites are up to date, which are running behind, and which have gone silent for two weeks. Check-ins are recorded only for valid licenses actively bound to the reporting domain.

### Improved
- Analytics: the daily trend chart now also reads the permanent daily summaries, so date ranges older than the raw-data retention window (90 days by default) show real history instead of an empty chart. The summaries had been collected all along but were never displayed.
- The demo site now applies updates automatically every day and its nightly reset preserves that setting, so the public demo always showcases the current release.

### Fixed
- Eight plugins registered an admin-menu hook that the panel never fires; the dead registrations were removed (menu entries continue to come from the panel's own list, nothing visible changes).
- The internal schema check misread SQL comments and nested data blocks, hiding real columns and reporting phantom ones; with the parser fixed and three schema reference files brought up to date, the known-issues backlog dropped from twelve to zero.

---

## [2.66.46] - 2026-08-21  ·  _Patch_
**General audit: silent log flood stopped + plugin registration repair**

### Improved
- Four plugin distribution tools were missing two installations from their target lists, so future fixes for those plugins would silently skip them; the lists were completed (the same gap was fixed for the SEO panel earlier).

### Fixed
- The admin dashboard queried social and push-notification tables even on installations where those plugins were never activated; the page rendered fine, but every single dashboard visit silently appended errors to the database log (one installation had accumulated 47,000 lines). The dashboard now checks the schema first and simply shows zeros, and it also adapts to older social-queue schemas instead of failing.
- The Google Console plugin's activation script used a wrong column name when registering itself, so it logged an error on every update and could fail to register on a fresh site; the column name was corrected.
- Two internal quality checks had fallen out of date after recent changes (quiz answer response and content-filter wiring) and reported false alarms; they now verify the actual behaviour instead of exact source text, and five already-resolved records were cleaned out of the schema check's known-issues list.

---

## [2.66.45] - 2026-08-21  ·  _Patch_
**Both languages everywhere: 10 themes + admin panel fully TR/EN**

### Added
- A live bilingual audit tool now logs into the panel and crawls the critical admin screens and public pages of every site in BOTH languages, catching raw dictionary keys, Turkish text in English mode and English text in Turkish mode — 140 fleet checks and 45 deep checks all pass.

### Fixed
- Around 1,100 hard-coded interface strings across ten themes (travel, pets, finance, minimalist, recipes, crypto, tech, entertainment, health, starter) now follow the site language: comment forms, newsletter boxes, search, 404 pages, pagination, reading time, share labels and screen-reader labels all render in Turkish on Turkish sites and English on English sites.
- The admin panel now honours the admin language setting consistently: the login screen tagline, every date (month names were printed in Turkish even in the English admin), the media upload box and the license screen no longer mix languages.
- Thirteen dictionary entries that displayed their internal key instead of text (e.g. the date filters on the Posts screen) and nine English dictionary entries that contained broken Turkish text (e.g. the login subtitle) were repaired in both languages.
- A site language saved as a regional code like "en-US" was silently falling back to Turkish; regional codes are now normalised, so an English site no longer renders a Turkish interface.
- Two sites were running theme copies months behind the product (missing every rollout since the layout engine); all fleet theme copies are now byte-identical with the product and a new sync tool keeps them that way.

---

## [2.66.44] - 2026-08-21  ·  _Patch_
**SEO: AI visibility audit (llms.txt + AI crawler policy)**

### Added
- SEO Health Check gained an "AI Visibility" group: it now verifies that llms.txt and llms-full.txt (the site summaries ChatGPT, Claude and Perplexity read) are actually being served, summarises your AI crawler policy (how many of the 13 known AI bots are allowed), and confirms the live robots.txt really reflects that policy — so a stray static robots.txt file can no longer silently override your choice.

### Fixed
- Advanced SEO propagation lists were completed: the plugin's activation file joined the fleet sync list and two installations missing from the dedicated sync tool's target list were added, so future panel fixes reach every site instead of silently skipping some.

---

## [2.66.43] - 2026-08-21  ·  _Patch_
**Audience (CRM): export a segment, faster counters, tighter access**

### Added
- Each saved segment now has its own "Export CSV" button, so you can download exactly the contacts a segment covers in one click — not just the whole list.

### Improved
- The audience summary counters (total plus one per source) are now computed in a single database pass instead of five separate scans, so the Audience screen stays fast on large contact lists.

### Fixed
- The admin-only access check on the Audience screen is now unconditional, closing a theoretical gap where the contact list (personal e-mail addresses) could have been reachable by a lower-privileged user if the code were loaded differently.

---

## [2.66.42] - 2026-08-21  ·  _Patch_
**Social: non-blocking Instagram/Threads publishing + Pinterest image fix**

### Fixed
- The per-post Pinterest image field in the editor now saves. It was posting to an address that had no route, so the value was silently dropped — the pin image you set was never stored.
- Publishing a photo, story or carousel to Instagram — and a post to Threads — no longer holds a worker busy waiting for the platform to finish processing. Ready posts go out immediately; ones still processing are picked up on the next pass, the same way Reels already worked. Before, a single post could tie up a worker for up to half a minute.
- When a social post succeeds, its remote post id and publish time are now recorded on the queue entry itself (not only in the log), so the published-at time and a link back to the post are available.

---

## [2.66.41] - 2026-08-21  ·  _Minor_
**Recipe card: servings scaler, card image fix, sturdier rich results**

### Added
- Recipe cards now have a servings adjuster: readers tap − / + to change the number of servings and the ingredient amounts scale automatically. Whole numbers, decimals and fractions (½, 1½, 1/2) are all handled and shown back as neat fractions; anything that isn't a plain amount ("a pinch", "2–3") is left untouched.

### Fixed
- A recipe with only a cover image (no separate step photo) now shows that image on the card. Before, the card's image was computed but never displayed unless a separate process photo was set, so many cards appeared with no picture.
- The recipe's star-rating rich result is now emitted only when the rating is a real number within range and has at least one vote — a stray or out-of-range value could previously invalidate the whole recipe rich result in Google.
- A recipe with an unreadable publish/update date no longer stamps the structured data with a 1970 date; the field is simply left out instead.
- Prep/cook/total times written with a day component (for long-rested recipes) are now counted correctly instead of reading as zero.

---

## [2.66.40] - 2026-08-20  ·  _Patch_
**Quizzes: fairer scoring, answer explanations, cleaner personality results**

### Fixed
- A question with more than one correct answer is now scored fairly: picking any of the correct answers counts as right. Before, only one of them was accepted and a reader choosing an equally-correct answer was marked wrong.
- The "Show explanation" option now actually works — when it's on, each question's explanation appears in the results review after finishing. It had no effect before.
- The "Auto-scroll" option now works too: moving to the next question gently scrolls the quiz back into view, which helps on phones. It was also previously inactive.
- Personality quizzes no longer show a "3/10 correct" score or right/wrong marks — those don't apply to result-based quizzes, so now only the result card is shown.

---

## [2.66.39] - 2026-08-20  ·  _Patch_
**Plugin review, round four: social, forms, CRM, analytics**

### Improved
- Social & Video: YouTube uploads use a tighter per-chunk timeout so a single slow chunk can no longer tie up a worker; the upload simply resumes where it left off.
- Analytics: the tracking beacon no longer re-checks the database structure on every single page view — it only sets things up if something is actually missing.
- Audience (CRM): segment sizes are now counted directly in the database instead of loading every matching contact into memory, so the Segments screen stays fast on large lists.
- A/B tests: a winner is now declared only once every variant has reached the full sample size, matching what the screen tells you to wait for.
- Forms: spam submissions can no longer grow without bound — only the most recent are kept per form.

### Fixed
- Social: the connected app's client secret is now stored encrypted, matching how access tokens are already protected.
- Video Studio: the 90-second limit is now enforced on the server too, so an over-long video can't slip through and be rejected by Instagram — you're asked to shorten the script and re-render instead.
- Contact form: on older installs, clicking "Spam" on a message could silently lose it; the message list now repairs the underlying field first so the message is safely kept.
- Forms: dropdown / radio / checkbox answers are now validated on the server against the defined options, so a made-up value can't be slipped past the form.

---

## [2.66.38] - 2026-08-20  ·  _Patch_
**Plugin review, round three: push notifications, downloads, AdSense checker**

### Improved
- AdSense readiness checker: the scan no longer loads every post into memory at once, so it runs reliably on sites with thousands of posts.

### Fixed
- Push notifications: the list of trusted push services is now matched strictly, so a look-alike address (a domain merely ending in a trusted name) can no longer register and receive your notifications, and only secure addresses are accepted.
- Push notifications: publishing a post no longer waits for every subscriber to be notified before the save completes — the save finishes at once and notifications are sent right after, within a time budget so a large subscriber list can never stall or crash the publish.
- Downloads: a download link with a set limit can no longer be pushed past its limit by firing several downloads at the exact same moment.
- Editorial calendar & recipes: the admin permission check on these screens is now unconditional, closing a theoretical gap where it could have weakened if the code were loaded differently.

---

## [2.66.37] - 2026-08-20  ·  _Patch_
**Plugin review, round two: quizzes, Google, recipes, Cloudflare**

### Improved
- Google: the plugin no longer re-checks its database structure on every admin page load — it does so only once per version.
- Cloudflare: clearing the cache after you publish or edit a post no longer holds up the save while Cloudflare responds — the save finishes immediately and the purge runs right after.

### Fixed
- Quizzes: a page containing an embedded quiz could fail to load because the view counter had nowhere to record to. The counter now has its place, is added automatically to older sites, and can never take a page down again.
- Quizzes: a published quiz now has its own shareable page, so the "View" link in the admin opens the quiz instead of a "not found" error.
- Quizzes: the WordPress importer now refuses image and page addresses that point back into the server's own network, and verifies the remote site's certificate.
- Google: the "automatically notify Google when new content is published" checkbox now genuinely turns the feature on — before, it looked enabled but every submission was quietly refused.
- Google: the manual "submit for indexing" action now only accepts addresses on your own site.
- Recipes: a recipe with no usable image no longer publishes structured data that Google would reject — the recipe rich-result is emitted only when it will actually validate.
- Cloudflare: applying the recommended security rules can no longer wipe your own custom firewall rules if reading the current rules momentarily fails — the change is aborted instead.

---

## [2.66.36] - 2026-08-20  ·  _Patch_
**Plugin review, round one: safer AI images, newsletter and notifications**

### Improved
- Web notifications: subscriber records are handled more efficiently, without needless database work on every visit.

### Fixed
- AI images: a picture returned by the image provider is now downloaded only from a safe public address; an address that points back into the server's own private network is refused.
- AI images: when generation fails, the error message no longer risks showing your API key — the key is now hidden.
- AI images: if the daily image limit can't be read for a moment, the system now stops generating rather than continuing without a limit, so you are never billed past your cap by accident.
- Newsletter: an email template you edited by hand is no longer overwritten by an update — only templates you never touched are refreshed.
- Newsletter: the weekly digest is now sent only once even if two runs happen to start at the same moment.
- Newsletter: the sign-up form no longer reveals whether an address is already on the list — the reply is the same either way.
- Web notifications: the subscribe endpoint is now protected against being flooded with fake entries.
- Stories: reaction counts now change only from a genuine visitor tap, and a reaction sent from another site is ignored.

---

## [2.66.35] - 2026-08-20  ·  _Patch_
**Video Studio: 90-second cap so videos stay Reels-eligible**

### Improved
- Studio videos are now capped at 90 seconds. Instagram only places videos of 90 seconds or less in the Reels tab; a longer one would post as an ordinary video instead. The narration is already about a minute, so this only affects manually lengthened scripts — and when it does, both the picture and the sound are trimmed at the same point, so the file really stays within the limit. The script step notes the limit as you type.

---

## [2.66.34] - 2026-08-20  ·  _Patch_
**Video Studio: sturdier YouTube and Instagram publishing**

### Fixed
- A Reels or Shorts upload that got stuck while the platform was still processing it could keep polling for up to a day. Such a job now gives up after a reasonable window and is marked failed, so one stuck upload no longer ties up the publishing queue or the daily quota.
- A video scheduled for a future time is no longer mistakenly timed out because of the wait before its scheduled moment — the timeout window now starts from the scheduled time, not from when the job was created.
- The full multi-step publishing flow for both platforms — Instagram's create / wait / publish sequence and YouTube's resumable upload that continues after an interruption — was verified end to end, including recovery when a connection drops or a session expires.

---

## [2.66.33] - 2026-08-20  ·  _Patch_
**License security hardening**

### Fixed
- The admin license screen now shows only a masked version of the license key instead of the full value.
- License activation and deactivation now require an admin login on every install, including freshly installed sites that do not yet have an active license.
- Demo-license validation now relies on the site's configured address rather than a value taken from the request, so activation stays tied to the real domain.
- Premium features, plugins and themes now follow the installed edition: a paid package (already purchased to download) keeps everything unlocked even if its token lapses, while the free package is correctly limited.
- The update-download endpoint now rate-limits per address and only responds to expected origins.

---

## [2.66.32] - 2026-08-20  ·  _Minor_
**New: Video Studio — turn posts into narrated Shorts and Reels**

### Added
- Video Studio (in the Social plugin): pick a post and the studio writes a ~60-second narration script in your site's language, reads it aloud with a natural AI voice (30 voices, Turkish included — uses your existing Gemini key's free tier, so it costs nothing), and renders a 1080×1920 vertical video with your post's images, animated captions and your site's name — right in your browser. No server video software is needed, so it works on ordinary shared hosting; rendering requires Chrome or Edge.
- One-click publishing to YouTube Shorts and Instagram Reels through the existing social queue, with retries and rate limiting handled for you. Instagram connects with your own Meta app in development mode — publishing to your own account needs no app review. For YouTube, connect your own Google Cloud app; note Google locks videos from unverified API projects to private, so until you complete Google's verification the studio's "Download + open YouTube Studio" button is the recommended path — it saves the video, copies the title and description to your clipboard and opens YouTube Studio, making manual upload a 30-second task.
- Every text the studio produces — narration, YouTube title and description, Instagram caption, hashtags — is fully editable before anything is voiced, rendered or published. A "draft job" can be opened automatically whenever you publish a post, so fresh posts wait for you in the studio.

---

## [2.66.31] - 2026-08-20  ·  _Patch_
**Comments and the contact form: lost messages found their way back**

### Fixed
- On the Personal theme the contact form posted to an address that did not exist: every message a visitor sent ended in a 404 and was never stored anywhere. The address now reaches the protected handler, and when JavaScript is off the visitor is brought back to the page with a clear "received" or "failed" notice instead of a raw code screen.
- On the Entertainment theme comments were broken twice over: approved comments were never shown (the list pulled in a file that did not exist), and a signed-in reader's comment was always rejected asking for a name the form never collects. The list renders again and the handler now fills in the reader's name and email from their account.
- On eight of fourteen sites the spam capture log still had an old table layout, so every catch failed silently: blocked bots left no trace, the admin screen showed zero blocks, and the "repeat offender" signal never fired. The table now completes its own missing columns on first use.
- Thirteen themes' comment forms used a spam-trap field literally named "website" (one theme even added "phone"). Browsers recognise those names and auto-fill them — and a real reader whose browser did so had their comment silently thrown away. The trap fields now use a neutral name browsers ignore.
- Every comment and contact submission was counted twice against the flood limits, so the caps the admin configured were effectively halved.
- All three settings on the contact form panel were dead: the recipient address was saved but notifications kept going to the general address, the custom success message was never shown, and the auto-reply was never sent at all. All three now do what the screen says — auto-replies also carry a once-per-hour-per-address brake.
- The site-wide comments feed now includes only comments from published, public posts. It is also reachable now: the feed advertised its own address but the address had no route and bounced to the home page.
- The comment moderation screen and the panel reply endpoint now require full moderation permission, not just any signed-in account.
- A reply written from the panel did not update the post's comment counter, and the person being replied to never got the "someone replied to you" email even when that notification was switched on.
- Comment notification emails were always in Turkish, even on English sites; they now follow the site language. The contact form's success and error notices also had no colour in themes without their own styling.

---

## [2.66.30] - 2026-08-19  ·  _Patch_
**A/B tests: the numbers are now real visitors' numbers**

### Fixed
- A/B test results counted search engines and automated crawlers as if they were readers: every crawl added impressions, and a crawler following the conversion link added conversions. A test could crown the wrong winner on traffic no human ever saw. Crawlers still see the page content as before, but they no longer touch the statistics.
- On a site installed in a subfolder, a conversion goal written as a plain path ("/contact") redirected the visitor to the server's root instead of the site's own page — usually a 404. Plain paths now resolve against the site's own address.
- Behind services like Cloudflare, every visitor appeared to arrive from the same address, so which variant a visitor saw depended almost entirely on their browser make — most people got the same variant and the split was badly lopsided. The variant assignment now uses the visitor's real address when a trusted proxy provides it; sites not behind a proxy are unaffected.
- Turning a plugin off left its placement codes ("[ab id=3]", "[form id=5]"…) sitting in the middle of published posts as raw text for every reader. Leftover placement codes from an inactive plugin are now removed from the page.
- Plugin placement codes also leaked as raw text into the RSS, Atom and JSON feeds, because feeds deliberately skip the plugin rendering step. Feeds now clean them out at the source.

---

## [2.66.29] - 2026-08-19  ·  _Patch_
**Analytics: the settings on the screen now actually do something**

### Improved
- Every page of every site ran three table-creation statements and nine setting inserts before rendering, on every single request. That check now happens once and remembers the answer; the admin screens still repair themselves on demand.

### Fixed
- The analytics master switch did nothing. Turning tracking off left the counting script on every page and the receiving endpoint still wrote every visit to the database, even though the screen said no data would be collected. The endpoint that receives visits now reads the settings before it stores anything, so off means off. The excluded-IP and excluded-path lists were dead in the same way and now work too.
- The free edition collected visitor data with no way to see it and no way to stop it: the analytics screens are not part of that package, but the counting script and the receiving endpoint were. Neither runs now unless the analytics module is installed.
- Any other website could post fake visits to the receiving endpoint from a visitor's browser and skew the reports. Requests that identify themselves as coming from somewhere else are now refused.
- Every comparison figure was biased upward. "7 days" actually measured eight calendar days and compared them against a seven-day span, so the up-and-down badges on the cards flattered the current period on every range. Both windows are now the same length.
- The same page was counted several times over: an address with "?page=2" or a campaign tag on the end became its own row in the most-viewed list. Addresses are now reduced to the page itself, for existing history as well as new visits, and web-encoded characters in Turkish addresses are decoded so they read normally and match the right article.
- Daily totals were being lost for good. The receiving endpoint and the housekeeping task both rotate the daily privacy key, and whichever got there first made the other skip that day's summary — one site had summaries for only 42 of its 83 days. Summarising no longer depends on the key, and missing days are recomputed from the raw records that are still within the retention window.
- Analytics silently collected nothing on installations where the first database file the endpoint found was not the one in use — it gave up instead of trying the next one. It now uses the first connection that actually works.
- The bounce rate loaded every visit session of the selected period into memory to count them; on ninety days of a busy site that is tens of thousands of rows for a single percentage. The database does the counting now.
- A malformed address in the browser bar ("?range[]=x") crashed the analytics screen with a server error.
- Saving the analytics settings and then refreshing the page submitted the form again.

---

## [2.66.28] - 2026-08-19  ·  _Patch_
**Advanced SEO panel: tools that had quietly disappeared are back**

### Improved
- Long tool tables no longer scroll inside their own frame. The panel measures the tool it is showing and grows to fit, so the slug repair and content SEO lists — hundreds of rows — scroll with the page instead of trapping a second scrollbar inside it.

### Fixed
- The heading hierarchy screen could not be opened from anywhere in the panel. It lists every published article whose headings start at the wrong level and fixes them in one click — on a test site it had findings for two hundred articles — but when the SEO tools were gathered into a single panel, this one screen was left off the menu, and the panel hides each tool's own tabs. It is now a module of its own, under Content.
- On installations where the Advanced SEO plugin is switched off, eight tools became unreachable: the SEO overview, heading fixer, content optimiser, internal linking, featured images, slug repair, orphan content and the year updater. They were removed from the main menu when the panel took over as their single entry point, so switching the panel off left the files installed and invisible. Five sites were in exactly that state. The menu now falls back to an "SEO Tools" entry whenever the panel is unavailable.
- The panel listed every tool it knows about, whether or not that screen exists in the installation at hand. A missing screen produced an empty white frame with no explanation, because a page that is not found says nothing inside a frame. The panel now lists only the tools it can actually open.
- Fixes to the panel screen itself never reached existing sites: the update tool carried the plugin's code but not the page that draws it. It is now on the list.

---

## [2.66.27] - 2026-08-18  ·  _Patch_
**Critical: the installer failed on its final step**

### Fixed
- New installations failed at the last step of the wizard. The installer carries its own copy of a small helper for reading PHP size limits, and the core gained a function with the same name on 7 August — so the moment the wizard loaded the core to finish setting up, PHP refused the duplicate and the install stopped with a server error. The installer's copy now has its own name, which also keeps its behaviour independent of the core's version. Anyone who downloaded the package between 7 and 18 August should download it again.
- The end-to-end install test that would have caught this now runs against the packaged installer, and its error detection no longer trips over the words "server error" appearing inside a script comment — a false alarm that masked whether the page was actually broken.

---

## [2.66.26] - 2026-08-18  ·  _Minor_
**Article pages stop being dead ends, and the ad-readiness panel now sees template repetition**

### Added
- Shared sidebar modules — categories, topics and recent posts — that any theme can use without carrying its own copy. A theme that ships its own version keeps it; the shared one only fills the gap.
- Three new checks in the ad-readiness panel, covering what it could not see before: how much of the site shares one title pattern or one section skeleton, how many posts run without a single image in the body, and whether a large batch of posts was published on one day. These are the traits that make a site read as machine-produced regardless of how well each article is written.

### Fixed
- One theme had its tag list switched off in code. The line dated back to when tag pages returned “gone”, and it was never revisited after those pages started serving again — so a site whose every post carried tags published not a single tag link. The list is back.
- Three themes never printed tags at all, although most of their posts were tagged. An article that ends without a single onward link is a dead end for the reader and for a crawler alike.
- The personal theme shipped its category, tag and recent-post modules switched off, so the sidebar of an article carried three links in total. The same article rendered by the theme that did get ad approval carries thirty-nine. The modules are on by default now.
- The travel theme's article rail held only a table of contents, share buttons and a back-to-top button; the theme's own richer sidebar was never included on article pages. Category, tag and recent-post navigation now sits in the rail.

---

## [2.66.25] - 2026-08-18  ·  _Patch_
**Image dimensions everywhere, and archives now list their posts in structured data**

### Added
- Category, tag and author archives now publish the list of posts they show as structured data. The page already declared itself a collection, but never said what was in it; the list is built from the same query the theme uses, so it cannot drift from what a visitor sees.

### Fixed
- Resized image variants never received width and height. The lookup stripped the size suffix from the filename but removed the file extension along with it, so the name it searched for could never match a stored one — a comparison that could not succeed by construction. Every related-post card and listing thumbnail was therefore published without dimensions, and those are the most numerous images on a page: each one shifted the layout while it loaded. Sizes now come from the file itself, so the variant reports its own true dimensions.
- Author avatars and site logos were skipped entirely. They are not stored in the media library, so no size was ever known for them, and an avatar can appear half a dozen times on a single article. They are measured now — layout treatment for them stays unchanged, only the dimensions are added.
- The featured image went into the structured data without dimensions on sites whose images predate the media library, even though the in-content images had them. That is the one image search engines look at first.
- The single post page now declares its author and section to social networks as well. Publication and modification times were already sent; the author was only in the structured data, so shared links carried no author attribution.

---

## [2.66.24] - 2026-08-17  ·  _Patch_
**API settings: quotas now apply to content generation, and usage statistics finally count it**

### Added
- The API tab now opens with the automation entry points it is named after: a link to the REST API keys used by n8n, Zapier or your own script, and one to the ready-made n8n workflows. Both had moved to other screens with no way back from here.
- Each AI setting now states what it governs — which calls a quota covers, that the token limit applies to analysis rather than article length, and what the cache window actually caches.

### Fixed
- The daily and per-account AI quotas were only applied to SEO analysis. Article generation — the path that actually spends most of the tokens — ignored them completely, so a site set to 200 calls a day could make thousands, and on a paid provider that lands straight on the owner's bill. Both quotas now cover every AI call, and the screen shows how much is left.
- The usage statistics counted the same narrow path, so most sites saw zeros no matter how much they generated. Every generation call is now recorded with its provider, model, token count and duration.
- The temperature slider did not reach article generation either: that code carried a fixed value and the setting only affected analysis. The configured value now applies everywhere it is accepted.
- The API key test endpoints now require an administrator account, matching the screen that calls them.
- The model field accepted an empty value and stored it, which left every later request pointing at no model at all — generation failed with nothing on screen to explain why. Empty and malformed values now fall back to the saved model.
- The default provider field accepted any text. An unrecognised value made the site report "no AI key connected" while the key sat there saved.
- Choosing a provider hid the other providers' key fields, and they could not be reached again without reloading — even though keys are stored per provider and several can be filled in. Nothing is hidden now; the default provider is marked instead.
- With a provider other than Gemini selected, the panel claimed the integration was off and asked for a Gemini key although generation was working. The status now follows the provider actually in use.

---

## [2.66.23] - 2026-08-17  ·  _Patch_
**User management: lockout protection, account status and a single password rule**

### Added
- Accounts can now be deactivated instead of deleted. The account status was stored and enforced everywhere — an inactive account cannot sign in and is hidden from author pages — but there was no way to set it from the panel, so the only way to stop someone from signing in was to delete their account along with everything attached to it.
- Locked accounts can be released from the user's edit screen. After five failed sign-in attempts an account locks for fifteen minutes, and the counter only cleared on a successful sign-in — so someone who could not remember their password stayed locked out with no way for an administrator to help. The current lock state and the failed-attempt counter are now shown, with a control to clear both.
- The user list now marks inactive, banned and locked accounts, so "why can't I sign in?" has a visible answer.

### Fixed
- The last administrator could lock themselves out of their own site. Changing your own role to subscriber, deactivating your own account or deleting the only administrator was accepted without a word — and afterwards nobody could reach user management again, with no way back except editing the database by hand. All three paths are now refused while no other active administrator remains.
- The role field accepted any value that was posted. A value outside the four known roles silently emptied the role — leaving an account that could sign in but had no permissions at all — and on databases in strict mode it broke the save outright. Role and status are now checked against their allowed values.
- Usernames were stored exactly as typed, including spaces and slashes, even though the username is also the author page address. A username can no longer be set to an e-mail address either: the sign-in screen accepts both a username and an e-mail, so the two would collide.
- Changing a username left the old author page as a dead address; it now redirects to the new one, the same way category addresses already did.
- The user screen enforced no password rule at all — "123" was accepted. Both the user screen and My Profile now apply one shared rule: at least eight characters with a letter and a digit, and obvious passwords are refused.
- Changing a password now also ends that account's "remember me" session on both screens, so older browser cookies stop working immediately.
- With a role filter active, the "All" tab showed the filtered number rather than the total, and paging through search results silently dropped the search.
- Deleting a user left their avatar file behind on disk.

---

## [2.66.22] - 2026-08-17  ·  _Patch_
**Spam Protection screen rebuilt, and its settings now save reliably**

### Fixed
- The Spam Protection screen was built with a layout system the admin panel does not use, so none of its structure applied: the four summary figures stacked into four full-width bands down the page, the settings sat in a single narrow column, and the icons never appeared. The screen is rebuilt with the panel's own components and now reads as one page: summary cards across the top, settings in the main column, quick actions and blocked addresses alongside.
- A status line at the top now states plainly whether protection is on. Every threshold on the page is meaningless while the master switch is off, and nothing on the old screen said so.
- Turning protection off was never saved: the screen decided the switch's state from the presence of the field rather than its value, so the setting stayed on no matter what was chosen.
- Turning the master switch off also erased the thresholds underneath it — link limit, submit time, flood caps all fell back to factory numbers, because disabled fields are not submitted by the browser and the screen treated a missing field as a request to reset. A missing field now keeps the saved value.
- Out-of-range values were stored as typed; they are now kept within the limits the screen advertises.
- The minimum submit time was an admin setting the guard did not read: the screen could say five seconds while the server decided at three. The configured value is now the one that applies.
- Spam catches were being written to a table that some installs never had. The repair routine existed but was never called from anywhere, so on those sites every caught bot vanished without trace and the screen reported nothing. The table is now created on demand and the write is retried.
- Several English labels on this screen showed placeholder text generated from their internal names; they have been written properly. Two Turkish descriptions described the wrong thing.

---

## [2.66.21] - 2026-08-17  ·  _Patch_
**Spam protection: one shared surface for every public form**

### Added
- Public forms now share a single anti-spam surface. Comments, the contact form, the newsletter box and the form builder each had their own hand-built protection, and they had drifted apart. One component now renders the hidden protection fields and one function runs the shared checks, so a new form is protected by construction rather than by remembering to repeat the work.

### Improved
- Bot catches are now recorded. Honeypot hits, instant submissions and flood blocks were silently discarded on the comment channel, so there was no way to tell working protection from absent protection; they are logged now.

### Fixed
- The timing check that catches instant bot submissions was inactive on five themes and the newsletter box, because the field it reads was never rendered there; one theme's comment form had no honeypot at all. Every public form now carries all three protection fields.
- The newsletter box never sent its hidden fields at all: the script assembled its own payload from just the e-mail address, so the honeypot on that form could never trip. The whole form is submitted now.
- Messages flagged as spam by the contact form were stored with an invalid status, because the column had never been extended with a spam value. They appeared in no folder — including the ones caught by mistake, which is exactly what the spam folder exists to prevent. The column is repaired automatically and previously mis-stored messages are recovered.
- One theme's comment form posted to an address that does not exist, so signed-in readers' comments went nowhere.
- Comment length limits counted bytes rather than characters, so Turkish text was measured incorrectly — a long comment could be refused while a single-letter name passed. Both channels now measure the same way.
- Names and subjects accepted line breaks, which single-line fields should never carry; the value is now cleaned on the way in.

---

## [2.66.20] - 2026-08-16  ·  _Patch_
**Tags no longer lead nowhere, and images declare their size**

### Fixed
- Tag links led to a bare “410 Gone” screen. Themes show tags in several places — under the article, in the sidebar cloud, on archive and search pages — but tag pages were only served when tag archives were switched on, which they are not by default. Every tagged article therefore carried several dead internal links, and a reader who clicked one landed on an unstyled error page. Tag pages are now always served with the site's own design; the setting decides only whether search engines may index them. With it off they are shown to readers but marked noindex and left out of the sitemap, exactly as before.
- Images inside articles were rendered without their dimensions, so the page reflowed as they loaded — the layout shift that Core Web Vitals measures. Both the article's main image and images inside the text now declare their size, taken from the media library, across every theme. In-text images also load lazily while the leading image stays eager, which is what browsers need for the largest element to appear quickly.

---

## [2.66.19] - 2026-08-16  ·  _Patch_
**Legal pages: updated details now apply, duplicate date and mangled e-mail fixed**

### Fixed
- Correcting your contact e-mail, address or business name and generating the legal pages again left the pages unchanged, still showing the details from installation. The generator kept any page that was long enough, to avoid overwriting text you had written yourself — but that also protected the untouched pages that shipped with the install. The generator now recognises a page you have never edited and refreshes it with your new details, while a page you edited by hand is still kept, and now says so and points to the overwrite option.
- Legal pages showed the last-updated line twice, with two different dates: the generator wrote one into the page text while the theme printed its own. The line now comes from the theme only, and pages that were never edited have the leftover line removed automatically when the Pages screen is opened and during maintenance.
- The last-updated date always showed today, on every theme, even for a page that had not changed in months — a misleading claim on a legal page. It now reflects when the page was actually last saved.
- Turkish spelling correction in the generated text ran across the whole page, including e-mail addresses and links, so an address such as iletisim@example.com could be rewritten into an invalid one. Addresses and links are now left untouched while the surrounding text is still corrected.

---

## [2.66.18] - 2026-08-16  ·  _Patch_
**Media: half-rendered screen on an empty library, and file types**

### Fixed
- The media library stopped rendering half-way down the page whenever the library was empty — which is exactly the state of a brand-new site. The file counters are produced with SQL sums, and a sum over zero rows is empty rather than zero; feeding that empty value into the counter text raised an error that ended the response early, so the page arrived without its grid, upload button or closing markup. The counters are now normalised to zero, and the translation layer no longer lets an empty value end a page.
- Every uploaded file was recorded as an image, whatever it was: PDFs, documents, spreadsheets, archives and text files all carried the image type in the library records. The type is now derived from the file itself, and existing records are corrected once during routine maintenance.
- The Video tab listed the entire library instead of videos, because that tab had no filter of its own. Video and audio now filter correctly, the Documents tab no longer mixes media files in, and the item count matches what the tab actually shows.

---

## [2.66.17] - 2026-08-16  ·  _Patch_
**Built-in pages: stable dates instead of a false freshness signal**

### Fixed
- Pages served from a theme template rather than a stored record announced the current moment as their publish and modification date, so the structured data changed on every single request — two requests three seconds apart reported two different timestamps. Search engines were told the page had just been edited every time they fetched it. These pages now carry a stable date taken from the template that produces their text, so the date only moves when the text actually changes.
- The same pages were listed in the sitemap with today's date every day, the same "permanently fresh" signal the homepage and category listings were corrected for earlier. Their sitemap entry now uses the same stable date.

---

## [2.66.16] - 2026-08-16  ·  _Patch_
**Pages: duplicate legal URLs, sitemap gaps and SEO visibility**

### Improved
- The legal page status table now shows how each page actually appears to search engines: its canonical address, whether it is indexable, whether it is in the sitemap, and its meta description length — with a plain-language note when something needs attention.

### Fixed
- Legal pages served from the theme template — the default state of a fresh site — answered on both their Turkish and English addresses with identical content, and each address declared itself canonical. Measured: /privacy and /gizlilik returned the same page byte for byte as two indexable URLs. Every alias now collapses onto one address per document, chosen by the site language, exactly as it already did once a page existed in the CMS.
- Those same pages were missing from the sitemap: live, indexable, but never submitted, because the sitemap only listed pages stored in the database. Privacy, terms, cookie policy, disclaimer, about and contact are now listed whenever they are served, and a page stored in the CMS replaces the built-in entry instead of being listed twice.
- Legal, about and contact pages served from a theme template carried the site-wide meta description — the same sentence as the homepage — because the route never handed the page's identity to the theme. Each now carries its own description; verified across all 14 themes.
- The legal page editor screen answered with a server error on every install: it queried a table that belongs to the jekcms.com marketing site and does not exist in the CMS. The address now redirects to the page it was meant to open.
- Generated legal pages calculated reading time with a counter that splits Turkish words, inflating the estimate by roughly 40%.

### Security
- The Pages hub now requires the page-editing capability. It previously checked only that someone was signed in, which gave accounts holding lesser roles more reach over published legal text than intended.

---

## [2.66.15] - 2026-08-16  ·  _Patch_
**Menus: second menu could not be created, plus icon support**

### Added
- Menu items can carry an icon (emoji), set next to the title in the menu editor and shown in every theme's navigation.
- Menu items whose parent was removed used to vanish from the navigation; they are now shown at the top level instead of being silently dropped.

### Fixed
- Creating a second menu failed with a server error. Menus carry a unique slug, but the create/update code never wrote one: the first new menu was stored with an empty slug and every menu after it collided with it. Menus now get a unique slug derived from their name, and existing rows with an empty slug are repaired automatically. Renaming a menu keeps its slug, so nothing that points at it breaks.
- The Tech theme ignored the menu module completely — its header always printed the first five categories, so nothing configured under Menus ever appeared. It now publishes the assigned menu and falls back to categories only when no menu exists.
- A menu assigned to the "Main" location was invisible on every theme, because themes read the "Header" location. "Main" is now treated as an alias of the header location, so existing menus start working without being touched, and the location list only offers what themes actually render.
- When two menus shared one location, which of them appeared was left to chance. The site now consistently shows the older one, and the Menus screen warns that the others stay hidden.

### Security
- Menu links are now restricted to safe schemes: a `javascript:` or `data:` link saved into a menu is stored and rendered as an inert "#".

---

## [2.66.14] - 2026-08-16  ·  _Patch_
**SERP site name: save defect fixed, end-to-end identity checks**

### Added
- SERP Identity Check now verifies the whole live chain Google reads for the site name — homepage reachability and indexability, the title, og:site_name, the WebSite schema name/url/alternateName, the canonical, the favicon, and whether the www variant consolidates onto one host — so a broken link in the chain shows up without waiting for a re-crawl.
- Settings → General now flags a site name that is empty, generic, or a literal copy of the domain right next to the field, since Google falls back to showing the domain in those cases, plus a direct link to the identity check.

### Improved
- The identity check no longer reports internal state rows (plugin schema markers, heal flags, cached audit payloads) as autoload defects — they are excluded by design, so the check can now actually report a clean install and a real defect stands out.

### Fixed
- A setting could fail to save entirely when its stored row lived under a different group label: the settings table keeps `key` globally unique, but the shared save helper looked the row up by group plus key, found nothing, and then tried to insert — hitting a duplicate-key error. The value silently never applied, which for the site name meant search results kept showing the domain. The save path now resolves by key (as the read path already did) and moves the row to the requested group.
- Breadcrumbs on Turkish sites announced the root as "Home" even though the site declared itself Turkish. Google shows breadcrumbs in search results, so the trail now uses the site's own language ("Ana Sayfa").

---

## [2.66.13] - 2026-08-16  ·  _Patch_
**SEO audit: pagination signals and robots consistency**

### Improved
- rel=prev/next pagination links are now emitted centrally for every theme — including the four themes whose headers never passed pagination context.
- Page 2+ of the home/blog feed now carries the page number in its title instead of duplicating page 1's title.

### Fixed
- Out-of-range pagination URLs (?page=N beyond the last page) returned an empty archive with HTTP 200 and a self-referencing canonical — an infinite, indexable space of thin duplicate pages. Every paginated list (home feeds, category/tag archives, author pages, all 14 themes) now returns a real 404.
- The personal theme stamped paginated archive pages with an extra "noindex, follow" robots tag next to the core's "index, follow" — conflicting directives, and search engines pick the restrictive one, silently dropping page 2+ from the index. Paginated archive pages are all indexable again with a single robots tag.
- A per-post robots value saved as plain "index, follow" wiped the core defaults' max-image-preview:large directive, costing those posts large-thumbnail eligibility in Google Discover. Indexable robots values without max-* directives now get the default set appended.
- URLs of non-paginated pages (a single post, a fixed homepage) with a stray ?page=999 served identical content that declared itself canonical — the canonical now keeps ?page only on genuinely paginated templates and consolidates everything else onto the clean URL.

---

## [2.66.12] - 2026-08-16  ·  _Patch_
**AdSense readiness: aligned with current approval criteria**

### Added
- New audit check: the privacy policy is now scanned for Google's "Required content" disclosures — cookie use, the third-party (Google) advertising-cookie statement and the personalized-ads opt-out link. If you rewrote the generated legal pages and dropped these sections, the audit catches it.
- New audit group: ad-click encouragement phrases ("click the ads", "reklamlara tıklayın") are now scanned in titles, slugs and bodies — the clearest program-policy violation there is.
- New sidebar card: applicant requirements (18+ age rule, the 6-month site-ownership rule that applies in some countries, HTML source access).

### Improved
- The consent-banner check now explains the certified-CMP rule accurately: since January 2024, serving ads to EEA/UK/Switzerland visitors requires a Google-certified CMP (IAB TCF) — the built-in banner covers the GDPR baseline but does not replace it; enabling Google's own consent message under AdSense → Privacy & messaging after approval satisfies the rule. The application-day checklist gained the same step.
- The policy-scan pass message now states its honest scope: Google's prohibited-content list is broader (hate speech, misleading health/election claims, deceptive practices) than what pattern scanning can detect.

### Fixed
- Policy patterns containing the Turkish dotless "ı" (e.g. "şifre kırma", "sızma testi") were silently missed in ALL-CAPS titles because uppercase "I" lowercases to "i", not "ı". The scanner now folds both the text and the patterns to a shared canonical form, so case no longer hides a match.

---

## [2.66.11] - 2026-08-16  ·  _Patch_
**Settings audit: SVG hardening in the branding preview**

### Security
- The generated-logo and favicon SVG fields are now sanitized before they are stored and before they are rendered in the branding preview. These are hidden form fields, so a tampered value could previously carry an event handler (e.g. onload) or script into the admin branding screen; the old check only rejected literal tags and the preview printed the markup raw. Legitimate generated logos are unaffected.

---

## [2.66.10] - 2026-08-16  ·  _Patch_
**License & update audit: free-tier update channel repaired**

### Fixed
- Free-tier installations could not install core updates: the server correctly serves the free package, but the signed update manifest only listed the full package's checksum, so the client's tamper check rejected the legitimate free download as a mismatch. The manifest now carries a signed entry for the free package too, and the client accepts either signed checksum — the tamper protection itself is unchanged.
- The update manifest no longer embeds full internal catalog rows (IDs, file paths, changelog text); it now carries exactly the fields clients verify, which also makes the signed payload much smaller.

### Security
- Update availability queries without a license key are now treated as the lowest tier and only see the core release, matching the existing rule for unknown keys.
- The license heartbeat endpoint no longer includes internal error details in its 500 responses outside debug mode.
- The tripwire reporting endpoint now has an IP rate limit, closing an unbounded-log disk-fill vector.
- Expired one-time download tokens are now swept opportunistically instead of accumulating forever.

---

## [2.66.9] - 2026-08-16  ·  _Patch_
**Redirect manager overhaul: 404 suggestion engine revived, URL matching fixed**

### Improved
- Pasting a full URL of your own site as the redirect source now works — the domain is stripped and the path is stored canonically; foreign-domain sources are rejected with a clear message.
- Static-asset 404s (missing images, fonts, bot .env scans) are excluded from the suggestion log so real page URLs aren't buried in noise.
- The redirects table is now self-healing on older installations where it never existed — adding a redirect no longer fails with a generic error, and automatic 301s on slug changes work there too.

### Fixed
- The "Orphan 404s" suggestion engine never received any data: the 404 logger existed but nothing ever called it, so the tab read from a table nothing wrote to. 404s (including theme-rendered ones) are now logged centrally, so the one-click "create 301" suggestions finally appear.
- Redirects with Turkish or other non-ASCII characters in the slug never fired: the browser sends the URL percent-encoded while the redirect was stored decoded, and the two were compared as raw strings. Requests are now normalized exactly like the router normalizes them (decoding, trailing slash, subfolder base path), so /eski-yazı style redirects work.
- Redirects were completely dead on subfolder installations (e.g. example.com/blog): the incoming path carried the folder prefix while the rule was stored without it, and relative targets redirected to the domain root instead of the subfolder.
- Saving a redirect whose target equals its source is now rejected — previously it created an infinite redirect loop in the browser.
- Form resubmission on refresh is gone: actions now follow the POST→redirect→GET pattern, so pressing F5 after toggling a redirect no longer silently toggles it back.
- The "Hits (30 days)" stat actually showed the lifetime hit total of recently-hit rules; it is now split into an honest "Total hits" and "rules hit in the last 30 days".

---

## [2.66.8] - 2026-08-16  ·  _Patch_
**SEO tab: archive indexing controls and Pinterest verification**

### Added
- Archive Indexing panel in Settings → SEO: the thin-content engine that decides whether author and category archives are indexable was always running, but its knobs were hidden. You can now turn author-archive indexing on/off and tune the minimum-post thresholds for author and category archives — meta robots and the sitemap follow the same values, so Google never gets conflicting signals.
- Pinterest site verification field: the meta tag output has supported Pinterest verification all along, but the form only offered Google, Bing and Yandex. The fourth field is now there.

### Fixed
- The “AI bot access” shortcut in the SEO checklist pointed at an anchor that didn't exist on the page, so the click landed at the top instead of the AI bot panel. The anchor now exists and the link scrolls to the right place.
- Archive threshold values are clamped to a sane 1–50 range on save; previously a 0 or negative value silently fell back to a different number than the one shown in the form.

---

## [2.66.7] - 2026-08-16  ·  _Minor_
**Security hardening: 2FA replay protection, backup codes, secret handling**

### Added
- Backup recovery codes: enabling 2FA now generates ten single-use codes shown once. If you lose your authenticator device you can still sign in — no more lockout requiring server access. Codes can be regenerated with a current code.
- Mandatory 2FA policy: a new toggle can require every administrator to use two-factor authentication; admins without it are guided to set it up at login and can't disable it while the policy is on.
- The File Integrity Monitor now shows a distinct “monitoring inactive” state when no manifest has been created yet, instead of falsely reporting “clean”.

### Security
- Two-factor codes can no longer be reused: each 6-digit code is now single-use within its time window (a captured code can't be replayed on another session).
- The reCAPTCHA secret key is now encrypted at rest and is no longer written back into the settings form's HTML.
- Two-factor secrets are now stored encrypted (same protection as mail/API secrets).
- reCAPTCHA on the admin login now fails closed: if Google's verification service is unreachable, login is blocked (comment/contact forms still fail open so real visitors aren't blocked; this is configurable).
- Re-keying an already-enabled 2FA now requires the current code.

---

## [2.66.6] - 2026-08-15  ·  _Patch_
**Mail overhaul: honest delivery status, diagnostic errors, deliverability tools**

### Added
- Every core e-mail (sent or failed) is now logged, and the Mail tab shows a “Recent Sends” panel with per-message errors — failures are finally visible instead of dying silently.
- One-click Deliverability (DNS) check on the Mail tab: verifies the sender domain's MX, SPF and DMARC records — the three most common reasons mail lands in spam.
- A clear warning appears when the sender address and the SMTP account are on different domains (the classic setup that providers treat as spoofing).

### Fixed
- The core SMTP client never checked the server's replies — a rejected recipient (550) or rejected message (554) was still reported as “sent”, so failed contact-form, comment and download-delivery e-mails vanished without a trace. Every SMTP step is now verified and failures carry the server's exact response.
- The “Send test” button used a different mail engine than real notifications — a passing test could hide a broken production path. The test now exercises the same engine your notifications use (and no longer depends on the newsletter plugin being present).
- The admin's PHP mail() / SMTP method choice was ignored by core notifications; it is now honored everywhere, and authless SMTP relays (no username) work.
- Scheduled-task e-mails were sent raw with an empty From header due to a settings-lookup bug; they now go through the same configured engine.
- E-mails now include Date and Message-ID headers, a plain-text alternative part and base64 body encoding (all common spam-score factors), attachments finally work over SMTP, and connections have proper timeouts.

---

## [2.66.5] - 2026-08-15  ·  _Minor_
**Ad manager overhaul: every slot now works, new revenue placements, premium controls**

### Added
- New “End of Article” slot — the ideal spot for an AdSense Multiplex unit, monetizing readers who finish a post. Works in every theme automatically.
- Four previously dead slots now work in ALL 14 themes with zero theme edits: mobile bottom anchor (with a dismiss button), mobile top banner, sidebar top and sticky sidebar — the core injects them universally.
- Revenue Settings panel: in-content ad interval (every N paragraphs, following the 300–500 word rule) with a per-page cap, lazy loading for below-fold ads (protects Core Web Vitals), a GDPR consent gate that holds custom ad codes until the visitor accepts cookies, and an editor for extra ads.txt lines (non-Google networks/resellers).
- The Banner Manager's [banner id=N] shortcode finally renders on the site — it previously appeared as plain text because no frontend handler existed.
- Slots in the admin are now ordered and badged by earning power (in-article and above-the-fold first), and slots the active theme can't print are labeled clearly.

### Fixed
- In-article ads no longer appear in 3-paragraph posts (a counting quirk made the threshold more aggressive than documented) and never land right before the article-end ads (no stacking).
- The Pets theme printed the in-article ad at the very end of the post, stacked on top of the bottom ad — it now flows between paragraphs like every other theme.
- Ad styles were emitted up to three times per page; now exactly once.
- List ads (in-feed) filled their gaps: Travel archives, search results in five themes and homepages in seven themes now show the between-posts slot.
- Post descriptions in structured data no longer leak raw shortcodes like [banner id=3].
- Deleting a banner now uses a POST request (the CSRF token no longer travels in the URL).
- Side discovery: the spam settings save path called a function that did not exist anywhere — saving spam settings or the auto-blacklist would have crashed. Defined properly.

---

## [2.66.4] - 2026-08-15  ·  _Patch_
**Maintenance cleanup is now actually scheduled**

### Fixed
- A re-audit found that the daily maintenance cleanup (expired cache, rate counters, stale feed/sitemap files, old sessions, log trimming) lived only in a legacy cron script that nothing ever invoked — so in practice none of it ran. It is now wired into the real scheduler body that both server cron and the visitor-triggered fallback execute, with its own 24-hour interval guard. Verified end-to-end: planted stale files were swept, fresh files and still-valid caches were left untouched.

---

## [2.66.3] - 2026-08-15  ·  _Patch_
**Disk hygiene: every cache now cleans up after itself**

### Fixed
- Rate-limit counter files (one tiny file per visitor IP) could pile up indefinitely on hosts where daily maintenance never runs — a real concern on shared hosting with inode quotas. The limiter now sweeps stale counters opportunistically on a small fraction of requests (the same pattern PHP uses for session cleanup), and the daily maintenance covers both counter formats instead of one.
- The daily cleanup used to delete rate counters after just one hour, silently resetting live 24-hour limits; it now waits until a counter can no longer be active.
- Requesting a comments feed for a non-existent post ID now returns 404 without writing a cache file.
- Feeds requested with a custom ?limit are now generated fresh instead of each size writing its own cache file (up to 100 files per feed).
- Stale feed and sitemap cache files left behind by key changes were never deleted; the daily maintenance now sweeps them.
- Expired session files could linger for months on quiet sites (PHP's own cleanup is probabilistic); maintenance now removes sessions past their 30-day lifetime deterministically.

---

## [2.66.2] - 2026-08-15  ·  _Patch_
**Comments in four more themes + newsletter popup fixed to once a day**

### Added
- The Lifestyle, Minimalist and Tech themes now have a full comment section (list with replies, moderation-aware form, spam protection) designed in each theme's own visual language; the Starter theme's dormant comment code was wired up and completed. All four respect the global comments setting and the per-post comment status.

### Fixed
- The newsletter signup popup could reappear on every page: the Finance theme only remembered the popup after the visitor clicked the close button, and the plugin popup reset at midnight. Both now remember the moment the popup is shown and stay quiet for a full 24 hours; subscribers never see it again.
- The Finance popup's subscribe form pointed to a root-absolute address that broke on subdirectory installs.

---

## [2.66.1] - 2026-08-15  ·  _Patch_
**System-wide audit: privacy, SEO and reliability fixes**

### Improved
- Duplicate structured data removed: author pages in the Health theme and recipe pages no longer emit the same schema twice with conflicting IDs.
- Content boxes across six themes were restyled from the left-accent-bar look to cleaner top-accent panels.
- Recipes theme post pages now get the shared content typography (image alignment, figures, captions).
- Support API endpoints now require a domain that is actually activated on the license before showing or changing tickets, with per-IP rate limits.
- Four confirmed-dead legacy files were removed after a three-week production probe; the update tooling now automatically covers every plugin's admin pages.

### Fixed
- The RSS feed cache now keys on the requested size, so a “?limit” value on one request no longer affects the feed other readers receive.
- Feeds now use the actual publish date for ordering and timestamps, so scheduled posts appear correctly (matching the sitemap's logic).
- Sitemap family: the news sitemap's index entry now uses the same publish-date window as its content; the video sitemap now really lists posts with YouTube embeds (it was announced but empty); noindex pages are no longer announced; the homepage's last-modified date reflects real content changes instead of “today”; image entries carry the post title instead of the slug.
- Comment forms in the Recipes and Travel themes posted to a non-existent address — comments could never be submitted. They now reach the comment handler, and six themes additionally hide the form when comments are closed for that post.
- The Trends theme now runs post content through the full content pipeline — shortcodes (forms, downloads, quizzes…), FAQ/how-to boxes and the final safety filter all work there now.
- Tables of contents across seven themes no longer skip or mislink headings that already have an ID.
- The “posts per page” reading setting is now honoured by archive and search pages in eight more themes.
- Database migrations now actually record their progress, run in numeric order and log failures (previously every migration silently re-ran on each update).
- Sending a newsletter from two overlapping runs could deliver the same campaign twice to a subscriber — queue rows are now claimed atomically and the cron entry point takes a lock.
- Deactivating a plugin now really turns off its public endpoints (forms, quiz submissions, download links, A/B redirects…).
- Date archives (/archive/2026) rendered as 404 even in themes that support them.
- Percent-encoded URLs (e.g. slugs with Turkish characters typed encoded) no longer 404.

### Security
- Private posts stayed truly private everywhere: posts imported from WordPress as “private” could previously be opened at their direct URL and could appear in theme lists, related-posts blocks, search results, the llms.txt export, weekly digest emails, auto-shared social posts and the Stories bar. Every one of those paths now respects the post's visibility.
- The Atom feed no longer publishes author e-mail addresses — they were an open invitation to spam harvesters and had no SEO value.
- Locking out repeated failed logins now also works when signing in with a username instead of an e-mail address.
- AVIF uploads are now validated as real images (previously they skipped both the image check and the content scan).

---

## [2.66.0] - 2026-08-15  ·  _Minor_
**More resilient automatic updates**

### Improved
- Automatic updates are now sturdier: before installing anything, the update package's digital signature is verified against several canonical forms and the exact bytes served — so a future change in how the update server formats its release list can never silently stop updates from reaching your site. The current, working verification is always tried first, so nothing changes for you day to day; this only adds safety nets.

---

## [2.65.102] - 2026-08-14  ·  _Patch_
**Fix: image & logo uploads failing on some servers**

### Fixed
- On servers where PHP's Fileinfo extension is turned off, every image and logo upload failed with “Class finfo not found”. Upload validation now detects the file type through several fallbacks (including reading the image header directly), so uploads work regardless of that extension.

---

## [2.65.101] - 2026-08-14  ·  _Patch_
**The format menu now scrolls neatly instead of overflowing the screen**

### Fixed
- With all the new blocks, the format menu could run off the bottom of the screen; it now fits the viewport with a tidy internal scroll and closes when you scroll the page, so it never appears detached from its button.

---

## [2.65.100] - 2026-08-14  ·  _Minor_
**Cleaner block design, styled callouts on the page, plus keyboard keys and drop caps**

### Added
- Two more inline text tools other editors have: a Keyboard key style (renders a real key cap, e.g. Ctrl + S) and a Drop cap (an oversized decorative first letter to open an article).
- The Info / Warning / Error / Tip highlight boxes are now properly styled on the published page — before they only looked right inside the editor.

### Improved
- Cleaner, less templated block design: the colored left bar was removed from the Key takeaways box (and the editorial summary box), replaced by a clean titled panel; the pull quote is now a centered, magazine-style quotation. The look is more editorial and less generic.

---

## [2.65.99] - 2026-08-14  ·  _Minor_
**Beautiful content blocks, collapsible FAQ, and two new text styles**

### Added
- Two strong new text styles for richer articles: a Lead paragraph (a larger, standout intro) and a Pull quote (a decorative, oversized quotation) — both in the format menu.
- The FAQ block is now collapsible on the page: each question expands and collapses like an accordion, so one FAQ block gives you a full set of expandable questions in one place.

### Improved
- All content blocks were visually redesigned on both the editor and the live page: buttons get depth and hover, How-to steps show numbered badges, Pros & Cons use clear check/cross marks with colored headers, Key takeaways carry an icon and accent bar, and star ratings are larger — a noticeably more finished, professional look.

---

## [2.65.98] - 2026-08-14  ·  _Patch_
**Editor blocks: audited and hardened for every theme**

### Fixed
- FAQ questions no longer appear inside a theme’s table-of-contents: the question is now a styled heading that stays out of the on-page contents list while still powering the FAQ rich result.
- Verified every new block (FAQ, Pros & Cons, Key takeaways, How-to) renders correctly through the article pipeline on all themes, with the FAQ and How-to search markup produced automatically and safely (user text is always escaped).

---

## [2.65.97] - 2026-08-14  ·  _Minor_
**A pro-grade editor: SEO content blocks, fixed Button & Accordion**

### Added
- Four new content blocks for richer, search-friendly articles: an FAQ (question & answer) block that automatically adds Google FAQ rich-result markup, a Pros & Cons box, a Key takeaways box, and How-to steps that automatically add How-to rich-result markup — each inserted and edited through a professional panel.
- Video now has its own toolbar button, right next to the image button — clearer than hiding it in a menu.

### Fixed
- The Button block now inserts a clean, compact button instead of a broken empty area, and can be re-edited by double-clicking it.
- The Accordion block is now fully editable: type the title directly and write the hidden content underneath (previously it appeared as an unusable strip).
- The format menu items now line up consistently — every entry is an icon plus a label in a logical order, instead of scattered styles.

---

## [2.65.96] - 2026-08-14  ·  _Minor_
**Pro Forms, an Audience suite, a richer editor, and faster videos**

### Added
- Form Builder is now a real visual builder: a two-pane editor with a LIVE PREVIEW that updates as you type, 16 field types (text, e-mail, dropdown, checkbox, date, time, star rating, consent/GDPR, section heading, info text, hidden…), per-field width so fields can sit side by side, and drag-and-drop reordering by a handle. Plus an auto-reply e-mail to the sender that fills in their own answers, redirect-after-submit, keyword spam filter, an entry limit, and a full submissions manager (read/spam, per-entry detail, CSV export).
- Audience & Marketing — the CRM grew into a marketing hub: contacts from every source unified by e-mail, plus saved Segments (audience filters with live counts) that will become broadcast targets for e-mail and web push.
- The post editor gained rich content blocks — Button/CTA, Accordion (collapsible FAQ), Star Rating, and YouTube video — inserted through professional modals (not browser prompts). Tables now open a visual size picker (pick rows × columns) and show a floating toolbar right on the table to add/remove rows and columns without dialogs.

### Improved
- Every plugin admin screen was rebuilt to the jekcms admin design — proper cards, pill buttons, stat panels, inline how-it-works notes and rich empty states, with a left inner-sidebar where a plugin has multiple sections.
- Web Push adds a “Send test to this browser” button so you can subscribe and test notifications right from the admin.

### Fixed
- Adding a YouTube video no longer slows the page: embeds load a lightweight poster and pull in the real player only on click (privacy-friendly youtube-nocookie).
- Hardened CSV exports (Audience, SEO, Analytics, form entries) against spreadsheet formula injection.

---

## [2.65.95] - 2026-08-13  ·  _Patch_
**Critical: plugin admin pages could crash with a 500**

### Fixed
- Fixed a 500 error that could break plugin admin pages. The admin header's update check caught its exception into a variable named $e — the same name pages use for their HTML-escaping helper — so whenever that check failed (e.g. a slow update server or a stale database), the page's next output call crashed with “Object of type … is not callable”. The header and sidebar now use private catch variables, so a failed background check never takes the page down.
- Plugin admin descriptions and sidebar names for the newest modules (Forms, Downloads, Web Push, Editorial Calendar, Audience/CRM, A/B Tests) now show in Turkish on Turkish installs instead of falling back to English.

---

## [2.65.94] - 2026-08-13  ·  _Patch_
**CSV exports hardened against formula injection**

### Improved
- The admin sidebar now shows the newest modules (Forms, Downloads, Web Push, Editorial Calendar, Audience/CRM, A/B Tests) with proper localized names and their own icons, instead of an English name and a generic icon.

### Security
- CSV exports are now hardened against spreadsheet formula injection: every untrusted cell in the Audience (CRM), SEO and Analytics exports is neutralized so it opens as plain text in Excel or Google Sheets.

---

## [2.65.93] - 2026-08-13  ·  _Patch_
**A/B Tests: Even Variant Split on 32-bit PHP**

### Fixed
- A/B Tests now split traffic evenly on 32-bit PHP builds too. The visitor-bucketing hash could turn negative on 32-bit, which would have pushed almost everyone onto the first variant and skewed the results; the hash is now masked to stay non-negative on every platform. No effect on 64-bit hosting (the common case), where the split was already even.

---

## [2.65.92] - 2026-08-13  ·  _Minor_
**New Plugin: A/B Tests**

### Added
- A/B Tests — find out which headline or call-to-action actually works instead of guessing. Create an experiment with two or more variants, drop the [ab id=N] shortcode into any post or page, and each visitor is shown one variant — the same one every time they return, chosen without a cookie so it just works. A link to /ab/go?e=N records a conversion for that visitor's variant and forwards them to your goal page. The admin shows impressions, conversions and conversion rate side by side, highlights the leader with a 🏆, and warns while the sample is still too small to trust. Weights let you send more traffic to a variant, and pausing an experiment freezes the numbers while still showing the winning version to readers. Lightweight by design: cookieless bucketing and aggregate counters, so no per-click table piles up. Activate it under Plugins.

---

## [2.65.91] - 2026-08-13  ·  _Minor_
**New Plugin: Audience (CRM)**

### Added
- Audience (CRM) — a lightweight CRM that unifies the contacts you already collect into one place. It gathers your newsletter subscribers, Form Builder leads, Digital Downloads buyers and approved commenters into a single audience keyed by e-mail: someone who subscribed, filled a form and bought a download shows up as one contact with all three sources, not three scattered rows. Search by name or e-mail, filter by source or by your own tags, and open any contact to see a full activity timeline across every channel. Add tags to build segments (vip, prospect, customer…) and a private note per contact, then export the filtered list to CSV for your mail tool. One click rebuilds the audience from your live data, and it always keeps the tags and notes you added. Activate it under Plugins.

---

## [2.65.90] - 2026-08-13  ·  _Minor_
**New Plugin: Editorial Calendar**

### Added
- Editorial Calendar — plan your content pipeline with a kanban board (Idea → Draft → Review → Ready) and a month calendar. Assign posts to authors, set due dates, and add editorial notes. Moving a card to Review flips the post to “pending”; the other stages keep it a draft, and publishing still happens in the editor — so nothing goes live by accident. The calendar places published and scheduled posts on their publish date and planned drafts on their due date, giving you a clear month-at-a-glance of what’s coming. Multi-author teams get a shared view of who’s working on what and when it’s due. Activate it under Plugins.

---

## [2.65.89] - 2026-08-13  ·  _Minor_
**New Plugin: Web Push Notifications**

### Added
- Web Push Notifications — let visitors opt in to browser notifications and reach them even after they leave your site. When you publish a new post, every subscriber gets a native notification that reopens the article — bringing readers back for repeat visits. Includes a subscriber count and a one-click test broadcast. Fully self-hosted: standard VAPID authentication and RFC 8291 payload encryption in pure PHP, no third-party push service and no per-message fees. Only trusted push endpoints are accepted, dead subscriptions are pruned automatically, and the private key is encrypted at rest. Works on HTTPS sites (and localhost); the visitor grants permission in their browser. Activate it under Plugins and turn on “notify on new post”.

---

## [2.65.88] - 2026-08-13  ·  _Minor_
**New Plugin: Digital Downloads**

### Added
- Digital Downloads — sell or give away digital files (ebooks, printables, templates, courses). Embed a product anywhere with the [download id=N] shortcode. Free products act as e-mail-gated lead magnets: the visitor enters an e-mail and instantly gets a secure download link (also e-mailed). Paid products create an order you fulfil however you like — bank transfer / havale or any method — then one click marks it paid and e-mails the buyer their link. Files are stored in a web-blocked folder and served only through single-use tokenized links with a per-order download limit and expiry, so they can’t be shared or hotlinked. Uploads of executable file types are refused. Activate it under Plugins; set your payment instructions on its page.

---

## [2.65.87] - 2026-08-13  ·  _Patch_
**Smarter Search: Relevance-Ranked Results**

### Improved
- Site search now ranks results by relevance instead of just date. It uses the database full-text index (which existed but was unused) so the best matches surface first — a term in the title outranks the same term buried in the body — and partial words match too (searching “brew” finds “brewing”). Very short queries automatically fall back to the previous substring search, so nothing is lost. Turkish content and multi-word queries are handled correctly.

---

## [2.65.86] - 2026-08-12  ·  _Minor_
**New Plugin: Form Builder**

### Added
- Form Builder — build unlimited custom forms (contact, lead-gen, surveys, quote requests) with a visual field editor. Ten field types (text, email, phone, URL, number, textarea, dropdown, radio, checkbox, date), each optional or required. Embed any form anywhere with the [form id=N] shortcode, collect submissions in a built-in viewer, and get e-mail notifications on new entries. Protected out of the box with a honeypot, CSRF, rate limiting, minimum-submit-time and spam filtering; all stored values are safely escaped. Activate it under Plugins.

### Fixed
- Shortcodes such as [form id=5] or [quiz id=3] could leak as raw text into a page’s meta description and social-share (Open Graph) snippet. They are now stripped from the description, so search results and shared links read cleanly.

---

## [2.65.85] - 2026-08-12  ·  _Patch_
**Core Cleanup: Removed Unused Legacy Modules**

### Improved
- Removed several unused code modules left over from earlier versions — a dead front-end controller, a duplicate image-optimizer class (the feature runs from a different code path and is unaffected), an unused string helper, a duplicate support-ticket class, two unused cache helpers, an unused query builder, and three already-disabled one-time scripts. This trims the codebase with no change to how the site behaves; every page and feature was re-verified afterward.

---

## [2.65.84] - 2026-08-12  ·  _Patch_
**Backup System Hardening: View-Safe Restore, Memory-Safe Dumps, Reliable Scheduling**

### Improved
- Database dumps are now streamed to disk instead of being assembled entirely in memory, so backups no longer risk running out of memory on busy sites with large analytics or log tables.
- Scheduled daily backups are more reliable on low-traffic sites: instead of only firing in a single exact hour (which a quiet site could miss entirely), the backup now runs at the first opportunity from the chosen hour onward, still once per day.
- Old pre-restore safety backups are now cleaned up on the same retention schedule as automatic backups, so they no longer accumulate and fill disk space over time.

### Fixed
- Restoring a backup could fail completely on databases that contain a SQL view: the dump treated the view as an ordinary table and the restore aborted partway. Backups now handle views correctly, so a restore runs cleanly from start to finish.
- Restoring a large backup could run out of time and stop halfway, leaving the database partly restored. The restore now lifts the same time and memory limits the backup step already used, and if a specific statement ever fails it reports exactly which one instead of a cryptic error.

---

## [2.65.83] - 2026-08-12  ·  _Patch_
**Comments & Newsletter Deep Audit: Closed-Post Guard, Accurate Counts, New Notification E-mails**

### Added
- Optional comment notification e-mails: get an e-mail when a new comment arrives (including ones awaiting moderation), and let commenters know when someone replies to them. Both are off by default and configurable under Settings → Discussion.

### Fixed
- Comments could still be posted to an article whose comments were closed: the theme hid the form, but the endpoint did not enforce it, so a direct submission slipped through. Closing comments on a post now truly rejects new submissions.
- The comment counter shown on posts could drift out of sync when comments were approved, unapproved, spammed, or deleted from the admin — the number is now recomputed from the approved comments on every change, so structured-data and listings stay correct.
- The newsletter signup box on the Lifestyle theme never worked — the form pointed at a blocked internal path and returned a silent error. It now uses the correct subscription endpoint and confirms properly.

---

## [2.65.82] - 2026-08-12  ·  _Patch_
**Fixed a Setting Collision: Comments, Newsletter & Spam “Enabled” Are Now Independent**

### Fixed
- Three separate features — comments, the newsletter, and the spam filter — were all storing their on/off state under the same internal “enabled” name, so they secretly shared a single database row. Turning one off could silently turn the others off too: disabling the newsletter, for example, could make comments disappear from your site. Each feature now uses its own dedicated setting, so their switches are fully independent. Existing sites are migrated automatically, keeping whatever state they were last showing — no action needed.

---

## [2.65.81] - 2026-08-12  ·  _Patch_
**General Settings Audit: “Posts Per Page” Now Actually Works**

### Fixed
- Settings → Reading → Posts Per Page was a dead knob on most themes: changing it did nothing to the category, tag, author, search and archive listings, because those theme templates read a hard-coded constant instead of your setting. The value you pick now drives pagination on all of them, with the constant kept only as a fallback. Every observable general setting was re-verified live: analytics snippets (GA4, GTM, Meta Pixel, AdSense), the cookie-consent banner, custom header/body/footer scripts, SEO verification tags, JSON-LD publisher data, the RSS full-content switch, robots crawler blocking, page-cache headers and maintenance mode all apply correctly.

---

## [2.65.80] - 2026-08-12  ·  _Patch_
**Plugin Deep Audit: License Gate, Quiz Fix, and Two 500s Closed**

### Fixed
- The Quiz plugin created no database tables when activated — it looked for a migration file that was never shipped, so every quiz admin page failed with a server error and the plugin was effectively dead on arrival. Its full schema is now built into the plugin itself; activating it (or simply loading a site where it was activated) creates the tables and heals existing broken installs on the next visit.
- Two endpoints returned a server error when reached over the web: the legacy contact-form submit shim and the newsletter weekly-digest web-cron. Both re-declared a core constant (and the digest re-loaded the whole framework a second time) when invoked through the site router. Both now run cleanly — the contact shim rejects a missing security token with a proper 403, and the digest cron enforces its secret key with a 403 before doing any work.
- Hardened the plugin authorization boundary. Plugins are a paid-tier feature: the loader now verifies the licence on every request, so plugin availability always matches the active licence tier — while never restricting a paid site whose token has not yet refreshed.

---

## [2.65.79] - 2026-08-12  ·  _Minor_
**Preview Bar on the Site + Live Preview in the Customizer**

### Added
- While you preview a theme, the site itself now pins a small dark bar to the bottom of every page: it names the theme being previewed, reminds you that only you can see it, and carries two links — activate this theme, or close the preview — so you decide right where you are looking, without returning to the panel. Visitors never see the bar; it exists only in your admin session, and preview pages are never written to the shared page cache.
- The theme customizer gained a live preview pane: your site sits in a small window next to the settings, and color, size and font fields repaint it the instant you change them — before saving. Fields that feed several style variables at once update all of them together; the remaining settings show after you save, and the pane can be refreshed or popped into a new tab. The whole appearance layer was re-verified on all 13 themes after these additions: 272 checks, all green.

---

## [2.65.78] - 2026-08-12  ·  _Patch_
**Theme Preview Now Actually Previews — Plus Two Appearance Fixes**

### Fixed
- Theme preview was a dead switch: the admin banner said preview mode was active, but nothing on the frontend ever read the flag, so the site kept rendering the active theme. The preview now genuinely applies to your own browser session — you browse the whole site in the candidate theme while visitors keep seeing the live one, then either activate it or close the preview.
- Switching themes could fail with a bare "database error" on customized sites: every activation stored a rollback backup that embedded the previous backup inside itself, so the record snowballed with each switch until it exceeded the database packet limit. The backup now stores only what rollback actually needs, a failed backup can no longer block the activation itself, and per-theme customizations are untouched as before.
- Saving the footer builder could return a silent server error when the payload lacked the logo-type field, losing the save. The whole appearance layer was then re-verified end to end on all 13 themes with a real admin session — activation, preview, rollback, customizer save, footer save, header logo and page rendering: 136 checks, all green.

---

## [2.65.77] - 2026-08-12  ·  _Patch_
**Trends Theme No Longer Crops In-Content Images**

### Fixed
- The Trends theme forced every in-content image into a fixed 1.45:1 frame and cover-cropped it to fit — a 16:9 image lost a wide strip on both sides, so infographics went out with their titles and edge elements cut off. The image looked correct in the editor and broken only on the published page, which made the cause hard to spot. Content images now keep their own aspect ratio at full width; covers, cards and hero areas keep their designed framing. The other thirteen themes were audited for the same pattern and are unaffected.

---

## [2.65.76] - 2026-08-11  ·  _Patch_
**n8n Templates: Live End-to-End Tested, Image Bug Fixed, Flow Slimmed**

### Fixed
- The queue templates were run live end to end — from a real queue task through research, writing, three image generations, media upload and publishing — and that run caught a real bug: the current image model returns JPEG while the templates named the files .png, so the site rejected every upload as a type mismatch and articles went out without their in-content images and cover. The templates now derive the file extension from the actual image type the model returns, so the images land no matter what format the model produces. After the fix the full live run passed end to end: article published with its cover and both in-content images in place.
- Both queue workflows were slimmed down: a pointless 2-second wait and a decorative dead-end node were removed, so the canvas shows only steps that actually do something.

---

## [2.65.75] - 2026-08-11  ·  _Patch_
**n8n Templates Upgraded to the Current Gemini Generation**

### Fixed
- The n8n templates shipped pointing at the previous Gemini generation, and the researched template's writer even defaulted to a model Google no longer offers to newly created API keys — a fresh key failed with a not-found error at the content-writer step on the very first run. All three templates now use the current generation the CMS itself uses: gemini-3.6-flash for writing, research and SEO, and gemini-3.1-flash-image for image generation. Every model was verified live against a plain free-tier key, including the Google Search research step.
- Token budgets in the templates were adjusted for the new generation's thinking behaviour: current models spend part of the output budget on reasoning, so the tight limits on the SEO and image-vetting steps could have returned empty answers. Already-imported workflows are fixed by re-downloading the template, or by updating the model names in its Settings node.

---

## [2.65.74] - 2026-08-11  ·  _Patch_
**A Direct Path from the n8n Box to Creating an API Key**

### Fixed
- The n8n box on the Content Panel shows the webhook URL and the templates, but the page where you create the site API key those requests need had no link pointing to it from there — on some plans it was effectively unreachable. The box now says it plainly under the webhook URL: requests need a site API key, with a direct "Create API Key" link.

---

## [2.65.73] - 2026-08-11  ·  _Patch_
**n8n Templates Live in Exactly One Place**

### Changed
- The n8n template downloads now live in exactly one place: the n8n integration box on the Content Panel, right under the webhook URL the templates use. The duplicate card sections added to Settings > API & Automation and to the API Keys guide page have been removed; the guide page instead points to the Content Panel with a single line.

---

## [2.65.72] - 2026-08-11  ·  _Patch_
**n8n Templates Right Where the Queue Lives**

### Changed
- The Content Panel's n8n integration box — the place that already shows your webhook URL and the workflow outline — now ends with the three ready-made template downloads. The queue-driven templates feed on exactly this page's task queue, so you grab the workflow right where you fill its queue: no jumping to another screen.

---

## [2.65.71] - 2026-08-11  ·  _Patch_
**n8n Templates Now Live Inside Settings > API & Automation**

### Changed
- The ready-made n8n templates are now embedded directly in Settings > API & Automation — the tab opens with the three template cards and their download buttons, followed by a link to the API key / webhook guide page. The separate menu entry added in the previous release has been removed: the admin menu stays as it was, and the automation page now behaves like the other settings sub-pages (the Settings menu item stays highlighted while you are on it).

---

## [2.65.70] - 2026-08-11  ·  _Patch_
**The Automation (n8n) Page Is Now in the Menu**

### Fixed
- The page that holds your site API keys, webhook URLs and the new n8n templates was practically unreachable: its only link lived inside Content Studio, so on plans without that screen the page existed but nothing pointed to it. It now has its own "Automation (n8n)" entry in the admin menu under System, and the Settings > API & Automation tab opens with a clear pointer to it. The page title now says what it is: Automation (n8n) & API Keys.

---

## [2.65.69] - 2026-08-11  ·  _Minor_
**Ready-Made n8n Workflow Templates**

### Added
- The API Keys page now offers three downloadable n8n workflow templates, so full content automation no longer starts from a blank canvas: an RSS Content Factory (collects fresh feed items, lets AI pick the best candidate, de-duplicates against your published posts, vets the source image and rewrites everything into an original post), a Content Queue Persona Writer (pulls tasks from your site's content queue, writes in a configurable author voice while producing SEO data in parallel, generates an AI cover and publishes), and a Researched Production template (genuinely researches the topic via Google Search first, writes strictly from the verified data under anti-hallucination rules, and produces a cover plus two in-content images in distinct art styles).
- Every template is configured in one single place: an "Ayarlar" (Settings) node at the start of the workflow holds your site URL, your site API key and your AI keys. No n8n credentials to set up for the queue templates, nothing scattered across nodes — and if you run a template before filling it in, it stops with a clear message telling you exactly what to do. The templates ship with no secrets inside; sticky notes in the canvas explain setup and how each stage works.

---

## [2.65.68] - 2026-08-11  ·  _Patch_
**Match Images No Longer Skips Your Pinterest Pin**

### Fixed
- Some AI models echo the file-naming contract back inside the article JSON — a plain file name like "slug-pinterest" in an image field. The importer stored that name as if it were the image's address, so the Pinterest slot looked already filled: Match Images refused to touch a "filled" slot and the pin you uploaded to the temp folder was never picked up, with no error anywhere. A bare file name is no longer treated as an address at import, and the matcher now recognizes such leftover values as unmatched — so previously imported articles heal themselves the next time you press Match Images.
- The same phantom value also inflated the matched/total badge in the queue, made prompt export skip the article as "already done", and could reach the published post as a broken image. All of these paths now check for a real image address before counting a slot as matched.

---

## [2.65.67] - 2026-08-10  ·  _Patch_
**Update Downloads Now Work on Hardened Hosting**

### Fixed
- On hosting accounts where the PHP setting allow_url_fopen is switched off — a common security hardening on shared hosting — the panel could find a new version but then fail with a download error. The update check had already been moved to the more capable cURL transport, but the actual package download (and the signed-manifest verification in front of it) was still using the old method, so the very same host that could see the update could not fetch it. Every network step of the update chain now uses the same cURL-first transport, so checking, verifying and downloading all work on the same hosts.
- When a download does fail, the panel no longer says only "failed to download": the message now carries the underlying transport reason (for example the exact cURL error or HTTP status), so support can diagnose the host from a screenshot instead of guessing.

---

## [2.65.66] - 2026-08-10  ·  _Patch_
**In-Content Image Count Now Means What It Says**

### Fixed
- The Content Wizard asked for the number of in-content images but quietly counted the cover as one of them: picking 2 delivered a cover plus only 1 in-content image. The count now means exactly what the label says — every article always gets its cover plan, and the number you pick is how many in-content images are planned on top of it. Both creation paths (your own AI and in-app generation), the copied prompt and the downloadable sample template all follow the same rule, and picking 0 now yields a clean cover-only plan instead of no images at all.
- The requested in-content image count is now capped at the article's section count, because each image goes under a different heading — previously an extreme request could instruct the AI to place more images than the article had sections.

---

## [2.65.65] - 2026-08-09  ·  _Patch_
**Batch Image Production: Prompt Export and a ChatGPT Automation Tool**

### Added
- Premium plans now solve the hardest part of importing content at scale: the images. A hundred articles easily mean three hundred image prompts, and producing those by hand is not realistic. The Content Queue (and the wizard's image-prompts card) now offers two new buttons: one downloads every pending image prompt as a single JSON file, the other downloads a small automation tool (Windows and macOS). Feed the JSON to the tool and it generates the images one by one in your own ChatGPT Plus account, saves each file under the exact name Match Images expects, stops by itself when your daily quota runs out and resumes where it left off the next day. A step-by-step setup guide for both operating systems is included in the ZIP; requirements (ChatGPT Plus, Python, Chrome) are stated up front.
- The image window of every queue item now shows, next to each prompt, the exact file name the image must be saved under — cover, in-content and Pinterest slots each get their name spelled out, so there is nothing left to guess before pressing Match Images.

### Fixed
- The Content Wizard told you to save in-content images as slug-2.jpg — a name the image matcher never recognized, so files saved that way were silently ignored and the posts went out without their in-content images. The matcher's real contract is slug-img02.jpg, and the wizard now shows exactly that.

---

## [2.65.64] - 2026-08-08  ·  _Patch_
**The Package Upload Box Is Now Always Visible**

### Fixed
- Manual package upload only appeared after a failed update check, so on a site where the check worked there was no way to find it at all. It is now a section of its own on the Updates screen and always available — whether you need it because the update server cannot be reached, or simply because you want to apply a particular package by hand.

---

## [2.65.63] - 2026-08-08  ·  _Patch_
**Update Your Site Even When It Cannot Reach the Update Server**

### Added
- You can now upload an update package straight into the panel. Until now, if a site could not reach the update server — because the host blocks outbound connections, for example — there was no way to update it from the panel at all; the only route left was editing files over FTP, which is not something a site owner should have to do. The option appears exactly where the problem shows up: when a check fails, the failure notice now carries the upload box, a link to your downloads page and the size this server accepts.
- An uploaded package goes through the same safety chain as a normal update: the archive is verified as a genuine jekcms package before anything is touched, your license and update settings are preserved, a full backup is taken first, and the result is written to the update history so you can roll it back from the History tab.

### Improved
- The installation wizard now says what the outbound-connection check actually affects. It was labelled as being about downloading remote images, so a missing connection looked like a detail about media — while it is in fact what updates depend on. The check now names updates explicitly, tells you to have the curl extension enabled, and mentions that packages can be applied by hand if it cannot be.

---

## [2.65.62] - 2026-08-07  ·  _Patch_
**Automatic Updates Are Now On by Default**

### Improved
- Automatic updates now arrive without being switched on first. The preference used to start in the off position, so a site only ever updated if its owner happened to find the setting — which meant most installations quietly stayed on old versions and never received fixes, security ones included. New and untouched installations now keep themselves current on their own.
- Nothing is expected from your hosting. Updates run off ordinary visitor traffic, so there is no cron job to set up and no server access needed. Each update still goes through the same chain as before: a signed manifest, a checksum, an automatic backup and a rollback you can use if anything looks wrong.
- Your own choice always wins. If you have already set the preference — including turning it off — that setting is left exactly as it is; the new default only applies where nobody has chosen yet. You can change it any time under Updates, and centrally managed installations are unaffected.

---

## [2.65.61] - 2026-08-07  ·  _Patch_
**Uploading a Logo No Longer Breaks the Settings Page**

### Improved
- Every file field in Settings — logo, dark logo, footer logo, favicon, touch icon and the social sharing image — now states the largest size this server accepts, and a file over that limit is stopped before it is sent instead of failing halfway.

### Fixed
- Uploading a logo could end on a bare "Server Error" page, losing everything else you had just filled in. The upload ran without any protection, so a single failure while processing the image took the whole settings page down with it. The upload is now contained: if it fails, the page stays, the rest of your settings still save, and a message names the field and the reason.
- A failed logo upload used to be silent. The old value was quietly kept and the page reported success, so you could press save repeatedly and never learn that the image had not been accepted. Failures are now reported.
- Image handling no longer assumes the server can write every modern format. On hosting where PHP is built without WebP support, an upload could stop with a fatal error instead of simply falling back — the fallback is now in place.

---

## [2.65.60] - 2026-08-07  ·  _Patch_
**Update Check Now Works on Hosts That Block URL File Access**

### Fixed
- "Update check failed — cannot reach the update server" appeared on hosting where everything else worked. The update check was the one place still fetching over PHP's URL file wrapper, which many shared hosts disable for security; every other outbound call in jekcms already used cURL. The check now uses cURL when it is available and only falls back to the old method otherwise, so it works on those hosts.
- The failure no longer hides its cause. The screen now shows what actually happened — the connection error, the HTTP status, or that neither transport is available — together with what to do about it, such as asking the host to enable cURL. Previously the only message was that the server could not be reached, which was impossible to act on.
- A rejected license used to be reported as "up to date". If the update server refused the key, the response was quietly treated as "nothing new", so a site could sit on an old version believing it was current. That case is now reported, and it says to check the key and the registered domain.
- A momentary network glitch no longer locks the screen out of update checks for half a day. The failed result was cached for the full check interval; it is now kept only briefly, so trying again actually retries.

---

## [2.65.59] - 2026-08-07  ·  _Patch_
**Image Upload Now Tells You the Size Limit Before You Hit It**

### Improved
- On hosting where the real limit sits in front of PHP — a proxy or web server rule that PHP cannot see — the site owner can now declare the true ceiling with a single setting, and both the on-screen limit and the pre-upload check honour it.

### Fixed
- Adding an image inside the editor could fail with nothing but "Connection error", most often with photos straight from a phone. The real cause was size: past a certain point the server stops accepting the request body, and the browser reports that as a network failure. The upload field now shows the largest size this server actually accepts, an oversized image is stopped before it is ever sent, and if the server still refuses one the message says so plainly and tells you to resize the image.
- The upload endpoint now always answers in a format the editor can read. Previously a server-side failure — an out-of-memory during image conversion, for example — produced an error page instead of a proper response, which the editor could only report as a connection problem. Fatal errors and size rejections are now reported as real, readable messages.
- When an upload exceeds the server's total request limit, PHP discards the whole request including the security token, so the upload used to be reported as a security error. The size is now checked first, so the message names the actual reason.

---

## [2.65.58] - 2026-08-07  ·  _Patch_
**The "Empty Content" AI Error Now Recovers By Itself**

### Fixed
- Some AI actions failed with "Gemini returned empty content (MAX_TOKENS)". Newer models think before they answer and that reasoning is paid for out of the same budget as the text, so a budget sized for a non-thinking model can run out before a single word is written. The model now gets a floor large enough to reason and still write, whatever the individual feature asked for. If it somehow still happens, the request is automatically retried once with a much larger budget instead of being reported as an error.
- Testing the API key in Settings could fail even though the key and model were perfectly fine. The test asked for a handful of tokens — enough for the word "OK", but not enough for a thinking model to finish reasoning first — so the test reported a failure that content generation never had. The test now asks for a realistic budget.
- When a model rejects the request to switch reasoning off, the retry no longer reuses the smaller budget that was chosen on the assumption that reasoning was disabled — which was itself a way to arrive at an empty response.

---

## [2.65.57] - 2026-08-07  ·  _Patch_
**Long AI Generations No Longer Time Out: No More 504s, No More Missing Articles**

### Fixed
- Generating a draft on the AI Draft screen often failed with a "504 Gateway Time-out", seemingly at random. The cause was a hard limit on the hosting side: a web server cuts a request off if no data reaches the browser for about 55 seconds, and a real article takes considerably longer than that to write — measured between 42 and 104 seconds, so a large share of generations were over the line. The work was actually finishing on the server; only the connection had already been closed. The connection is now kept alive while the model writes, so the result arrives however long it takes. Shortening the wait would have been the wrong fix — it would have killed generations that were about to succeed.
- Asking the Content Wizard for five articles could leave you with three. Each article is generated in its own request, but when one needed a second attempt the retry ran inside that same request and pushed it past the server's cut-off point. The browser then saw a broken response and counted a perfectly good article as an error. Those requests now survive, and the retry timings were rebuilt around how long generation actually takes instead of an assumed limit.
- The AI Draft screen no longer freezes on a blank page while it works. Generation runs in the background and the button shows a live counter, so you can see it is still working instead of guessing whether the page has hung.
- Some AI features returned "empty content" and stopped. Newer Gemini models think before they answer, and that reasoning is paid for out of the same output budget as the text — but the budget still defaulted to a value from before those models existed, and the highest value the settings page allowed could be consumed by the reasoning alone, leaving nothing for the article. Thinking models now get a budget large enough to reason and still write, and the ceiling in Settings has been raised accordingly.

---

## [2.65.56] - 2026-08-06  ·  _Patch_
**AI Images Plugin Hardened: OpenRouter Fixed, Response Limits, No More Duplicate Runs**

### Improved
- A temporary "high demand" response from the image service is retried briefly instead of being reported as a failed image, matching how text generation already behaves.

### Fixed
- Choosing OpenRouter as the image provider could never work. The settings screen stores that API key encrypted, but the generator read it back without decrypting, so the encrypted value itself was sent as the key — every request failed, and the stored ciphertext was handed to a third party in the process. The key is now decrypted on read, and an unresolvable value is never sent at all.
- Publishing the same post twice in quick succession — a double click, a manual publish racing the scheduler, an automation retry — ran image generation twice and produced duplicate images while spending the API quota twice. A short-lived lock now lets only one run work on a post at a time, and a stale lock is taken over automatically so a crashed run cannot block the post forever.
- An aborted download could be treated as a real response. When a transfer failed midway the partial body was returned alongside the error, and the caller only checked for outright failure — so truncated data reached the image parser. A transfer error now always means no response.

### Security
- Image responses had no size limit. A broken or hostile endpoint could return an arbitrarily large body and exhaust the server's memory before anything checked it. Responses are now capped at 24 MB and an oversized transfer is cut off immediately.
- Generated bytes are now validated in memory before anything is written to disk, and the file extension comes from the real content rather than the type the provider claimed. Previously the data was written first and inspected afterwards, so non-image content briefly existed on disk under an image name.
- Error messages from the image service are scrubbed of secrets before they reach the admin screen or the log: API keys, OpenRouter keys and stored ciphertext are now masked.
- TLS verification, redirect following and connection limits are set explicitly on every image request instead of relying on server defaults, and redirects are refused so a response cannot be pulled from an unexpected host.

---

## [2.65.55] - 2026-08-06  ·  _Patch_
**Security Fix in Imported Links, and Image Fields Understood From Every AI**

### Improved
- Image fields are now understood no matter which AI wrote the JSON. Every assistant names things differently — `imagePrompt` or `image_prompt` or just `prompt` or `description`; `cover`, `hero` or `featured`; `afterH2`, `after` or `section` — and anything unrecognised was silently dropped, leaving articles with no prompts. The importer now reads all of these, accepts an images object keyed by slot as well as a plain list, and even a bare list of prompt strings, which it aligns to the image markers in the article. Verified against ten different shapes: every one yields the same clean result.
- The instructions that ask an AI for image prompts now demand a prompt that works unchanged in any generator — Midjourney, DALL-E, Stable Diffusion, Nano Banana, Firefly. Tool-specific syntax such as `--ar` or `::weights` is explicitly banned because it breaks every other tool, and the prompt must name subject, setting, lighting, framing and mood in 25-60 words.

### Security
- Markdown link conversion in imported content is now strictly validated: only http, https, mailto, tel and same-site addresses are allowed, both the address and the label are escaped, and attempts to disguise the scheme are ignored. The converted output also passes through the content filter a second time as a backstop. Legitimate links, YouTube and Vimeo embeds, tables and code blocks are unaffected.
- Content sent straight to the API could publish a literal `[IMAGE: …]` marker. Those markers only mean something inside the publishing queue, where they are replaced with real images; on the direct API path nothing resolved them and they appeared on the page. They are now stripped on that path.

---

## [2.65.54] - 2026-08-06  ·  _Patch_
**The Image Prompts the Wizard Writes Are Now Actually Shown**

### Fixed
- The Content Wizard writes a ready image-generation prompt for every cover, in-content and Pinterest image — and there was no way to read any of them. The queue had a window built for exactly this, but the button that opens it had been removed as "redundant" while the window itself stayed, so the prompts were unreachable from anywhere in the admin. The button is back on every item that has an image plan, with a badge showing how many prompts it holds.
- The wizard's final step now lists every prompt it just produced, grouped per article, each with the exact filename to save the generated image under. There are copy buttons per prompt, a copy-all button, and a download-as-text button for taking the whole set into another tool. The wizard had been promising this since step 3 ("the final step explains exactly what to do") without delivering it.
- The queue preview window showed the article and, once images were matched, the images — but never the prompts. It now lists them under the content with a mark showing which ones already have an image and which are still waiting.

---

## [2.65.53] - 2026-08-06  ·  _Minor_
**Content From Any AI Now Renders Properly, and the AI SEO Panel Tells You What To Fix**

### Improved
- The AI panel in the post editor's SEO tab was a flat list of observations. It now opens with a score bar and a plain verdict ("fix before publishing", "ready to publish"), followed by a ranked "do these first" list, then ready-to-use text you can put straight into the post: two title options, a meta description, a rewritten opening paragraph and the headings the article is missing. Title and meta apply to their fields with one click; the rest copies.
- Each finding now quotes the sentence it is about, verbatim from your post, and carries an impact and effort label so you can tell a five-minute fix from a rewrite. Quotes are checked against the actual text before display — a paraphrased or invented one is dropped rather than shown. Findings are ordered problems-first, highest impact first.
- A cut-off AI response used to fail with "returned non-JSON despite schema", which said nothing about the cause. It now names the real problem — the response ran out of token budget — and the SEO analysis budget was raised so it stops happening.

### Fixed
- Content written by one AI and pasted or imported into jekcms could reach the site with raw `###` markers and text running together in one unbroken block. Every model writes differently — some produce Markdown, some HTML, most a mix of both — and mixed content was passed through untouched: the HTML parts rendered, everything between them did not. The converter now keeps the HTML exactly as it is and converts the Markdown islands sitting between it, so headings, lists, tables, quotes and paragraphs come out right no matter which assistant wrote them. Verified against pure Markdown, pure HTML, deliberately mixed and unmarked plain prose.
- Inline markers left inside HTML paragraphs — `**bold**`, `[text](link)`, backtick code — were printed literally on the page. They are now converted wherever they appear in text, while anything inside a code block is left untouched.
- Content sent through the public API or an automation was never converted at all: only the publishing queue did that. A Markdown body posted from n8n or a script published with its markers intact. The API now runs the same conversion.
- AI Draft produced thin articles — roughly 350 words when 1000-1500 was selected. Length is now requested the way models actually follow, as a paragraph budget per section, and the same quality and formatting rules the Content Wizard uses apply here too. Measured after the change: 1185-1733 words, each draft carrying a table, both list types, bolded terms and a callout, with no oversized paragraphs.
- AI Draft showed an API error on the first attempt and worked on the second. A single failed call now retries quietly with spacing between tries, and an error is only shown when generation genuinely could not complete. Transient "high demand" responses from the provider are also retried instead of being surfaced raw.

---

## [2.65.52] - 2026-08-06  ·  _Patch_
**Hotfix: API Settings Page Stopped Halfway, and the Key Row Now Shows What It Is Doing**

### Improved
- The Gemini key rows were cramped: the enable checkbox, Test and × were pushed against the right edge with the key field stretched across the rest. Each row is now a bounded card with its controls grouped together and room to breathe, and it stacks cleanly on narrow screens.

### Fixed
- Settings → API stopped rendering halfway through in 2.65.51: everything from the AI model selector down — the model list itself, the quota fields, the privacy options and the Save button — was missing, and the model dropdown appeared empty. A helper introduced with the new model list did not exist under that name, so PHP aborted the page at that exact point. Introduced in 2.65.51 and fixed here; no data was affected, only the page output.
- Removing a Gemini API key with × gave no visible feedback when it was the only key left. The saved key is shown as a masked placeholder rather than a value, so clearing it changed nothing you could see — it looked like the button did nothing. The row is now dimmed and struck through, the field reads "key will be deleted", the explanation appears full width instead of squeezed into the label column, and an Undo button restores the key if you clicked by mistake. The same explanation, and Undo, now also appear when one of several keys is removed.

---

## [2.65.51] - 2026-08-06  ·  _Minor_
**Newer AI Models, and Generated Articles That Actually Look Like Articles**

### Improved
- The AI now runs on Google's current generation of models instead of the 2.5 family. The default for writing is Gemini 3.6 Flash, chosen on measured reliability rather than version number: asked for a full 1200-1800 word Turkish article, the old default returned usable output in two runs out of three, the new one in three out of three. That single change is what fixes the complaint that selecting five articles produced only four — a five-article run now completes five for five. Image generation moves to Nano Banana 2, and the model list in Settings has been rebuilt from models verified to answer, so a retired name can no longer sit in the menu.
- Articles generated by the Content Wizard were arriving as unbroken walls of text: no tables, no lists, no sub-headings, nothing emphasized. The site has always rendered all of that — the instructions simply never asked for it. They now require short paragraphs, sub-headings, at least one comparison table, bulleted and numbered lists, bolded key terms, a practical callout and a closing takeaway list. Measured across generated articles: paragraphs over 80 words dropped from routine to zero, and every article now carries a table, roughly a dozen list items and around ten highlighted terms.
- Generated articles were also coming in short — around 900 words when 1200-1800 was requested. Length is now requested in a form models follow accurately, as a paragraph budget per section rather than a total word count, which brings articles back inside the range you asked for.
- The model you pick in Settings now actually drives content generation. Until now that choice only affected SEO analysis; the writing path ignored it and always used a fixed model, so changing it appeared to do nothing.

### Fixed
- The one-sentence visual brief that guides every AI image was being cut off after about two words. Its token budget left no room once the model's internal reasoning took its share, so a brief meant to describe a full scene arrived as a fragment — and every generated image was drawn from that fragment. Briefs now come through complete, around thirty-five words, which is the difference between a described scene and a guess.
- A model that Google retires no longer takes the site's AI features down with it. Gemini 2.5 Pro was offered in the Settings menu and now answers 404; any site left on it had every AI feature failing with no visible cause. Retired names are migrated on update, and if a configured model turns out to be unavailable — retired, or not included in your API key's tier — the request falls back to a working model instead of failing.
- Newer models reject the request we send to disable internal reasoning, and reply only with "invalid argument" without naming the field. Left alone, upgrading the model would have silently killed SEO analysis, content generation and image briefs at once. Each path now recognizes the refusal, retries without that setting and remembers the result per model.

---

## [2.65.50] - 2026-08-06  ·  _Patch_
**Automation Overhaul: Queue Publishing Unblocked, Bearer Auth Fixed, Imported Content Sanitized**

### Fixed
- Articles produced by the Content Wizard could not be published at all: the quality gate inspected the raw queued text and rejected every item for containing an unresolved image marker — even though publishing removes those markers moments later, so nothing could ever leak. In testing, six of six generated articles were blocked; with the gate now judging the text that will actually be published, six of six publish cleanly and no marker reaches the site. This affected every wizard and JSON import that had not matched images by hand.
- API requests authenticated with "Authorization: Bearer " were rejected with 401 even when the key was valid, because most Apache/CGI setups do not hand that header to PHP — while the admin's own API Keys screen recommends exactly this method and it is the default in n8n. The key is now read from every source the server may expose, and the site config passes the header through. X-API-Key keeps working unchanged.
- A malformed JSON body sent to the API produced a bare "Internal error" 500. Bad JSON now returns 400 with the parser's reason, and a create request missing title or content returns 400 naming the fields — so an automation shows you what to fix instead of a dead end.
- JSON import crashed with a 500 when a field arrived as an array or object instead of text (a hand-edited file, a mis-mapped automation), and when the articles wrapper was an object rather than a list. Both shapes are now accepted or skipped cleanly, with the reason reported per article.

### Security
- Content arriving through an automation channel is now sanitized before it can be published: imports, the Content Wizard and the public API strip script-capable markup on the way in, while keeping everything an article legitimately uses — headings, lists, tables, images, links, code blocks and video embeds from known providers. Content you write yourself in the editor is unchanged.

---

## [2.65.49] - 2026-08-06  ·  _Patch_
**Content Generation Is Around Four Times Faster, and Stop Now Works Instantly**

### Fixed
- Generation in the Content Wizard could sit for a long time and then end with a network error. Two causes, both fixed: Gemini 2.5 models spend invisible reasoning tokens from the same output budget as the text, which made every article slower and occasionally truncated it; reasoning is now switched off for content generation, exactly as the SEO analyzer already did. And a single request now stays inside a strict time budget — the automatic retry only runs when there is time left for it, so a request can no longer outlive the server's limit and leave the browser with a dropped connection. In testing, one article went from about 25-60 seconds to 8-12 seconds.
- The Stop button did nothing until the article in progress finished, which could take a minute. It now cancels the running request immediately, shows "Stopping…", and the interrupted item is no longer listed as an error.
- During generation the screen showed no sign of activity. Each article now displays a live counter ("generating #2 · 14 s"), so a long run never looks frozen, and a genuine connection failure now says so in plain language instead of just "network error".

---

## [2.65.48] - 2026-08-06  ·  _Patch_
**Cleaner Installer Packages: Build-Machine Runtime Files Are Excluded**

### Fixed
- The installer packages could include runtime files produced on the machine that built them — session files under storage/ and images under uploads/. A fresh install therefore started with unrelated media in its library, and session files had no business travelling with a package at all. Packaging now ships the folders (so permissions and protection rules stay intact) without their runtime contents, and skips stray temporary files in the project root. Your installed sites are unaffected; this only changes what a new download contains.

---

## [2.65.47] - 2026-08-06  ·  _Patch_
**Wizard Articles Get Their Images Automatically: One-Click AI Images Integration**

### Added
- The Content Wizard and the AI Images plugin now work as one system. The image plan the wizard writes for each article (the cover prompt and every in-content image prompt) is handed to the plugin at publish time, so the generated images match what the wizard planned for that specific article instead of a generic concept. In the wizard's final step, the Images card now enables the plugin with a single click — no detour through the Plugins page — and explains that an image-capable API key is required.

### Fixed
- With the AI Images plugin set to generate at publish, the quality gate no longer blocks queue items whose planned images haven't been manually matched — the plugin is about to produce those images, so the "unresolved image marker" warning doesn't apply. When the plugin is off, the gate still protects the manual workflow exactly as before.

---

## [2.65.46] - 2026-08-06  ·  _Patch_
**Content Wizard Generation Is Now Reliable: Structured JSON Mode and a Bigger Output Budget**

### Fixed
- Starting generation in the Content Wizard could fail with "Could not extract valid JSON from the AI response". Server diagnostics showed the model's answer was being cut off mid-article: on Gemini 2.5, invisible reasoning tokens share the same output budget as the text, so long articles hit the ceiling and arrived truncated. Generation now requests the provider's structured JSON mode (the reply is guaranteed to be syntactically valid JSON, with no markdown fences), the output budget was doubled, and if a response still can't be parsed the wizard automatically retries once before reporting an error. The AI Draft screen uses the same JSON mode and a larger budget too.

---

## [2.65.45] - 2026-08-06  ·  _Patch_
**On/Off Switches Render Correctly in Every Settings Row**

### Fixed
- On/off toggle switches placed inside standard form rows could collapse: the track disappeared and the On/Off labels overlapped each other (visible for example on the "How this content was made" switch at the bottom of Settings → API). A general form style was overriding the switch layout; the component now always keeps its shape, everywhere in the admin. The affected row also got clearer spacing between its title and description.

---

## [2.65.44] - 2026-08-06  ·  _Patch_
**AI Draft Now Recognizes Your Saved Gemini Keys, and Generation Rotates Between Them**

### Improved
- Content generation now honors your multiple Gemini keys: if a key hits its quota, is unauthorized, or has been revoked, jekcms automatically retries with the next key in your list — the same rotation the SEO analyzer already had. Previously only the first key was ever used for drafts and wizard articles.

### Fixed
- On fresh installs, saving a Gemini API key in Settings → API and then opening the AI Draft screen still showed an "API key required" warning with the Generate button disabled — the settings form stores Gemini keys in the multi-key list, but the AI Draft screen (and the Content Studio status card) only looked at the old single-key field. Both now read the same key store the settings page writes to, so a key you saved is a key that works.
- Generating a draft could be cut off mid-request on servers with a strict PHP time limit; the AI Draft screen now allows the same generous time window the Content Wizard already used.

---

## [2.65.43] - 2026-08-06  ·  _Patch_
**AI Draft Generation Works Again, and All Five AI Providers Are Now Fully Supported**

### Added
- Claude (Anthropic) and Cohere are now fully working AI providers for content generation. All five providers offered in Settings → API — Gemini, Groq, Cohere, OpenAI and Claude — generate drafts and wizard articles through the same client, each with a sensible default model.

### Improved
- The Content Wizard's article-generation endpoint now enforces the same license check as the wizard screen itself, and logs a diagnostic sample to the server log when an AI response cannot be parsed — making "could not extract JSON" reports actually debuggable.

### Fixed
- The AI Draft screen's Generate button had been failing with a server error on every click since v2.28.0 — an internal file was loaded after the code that needed it. Generating a draft from a topic now works end-to-end again: the article is produced, previewed, and saved as a draft through the quality gate.
- The Test button next to the Groq, OpenAI, Cohere and Claude API key fields used to reply "provider not wired" even for perfectly valid keys. It now performs a real test call against the selected provider — the same code path content generation uses, so a passing test means generation will work too.
- With Cohere or Claude selected as the provider, the AI Draft screen claimed no API key was configured even when one was saved. Provider key lookup now covers all five providers.
- Content pasted with a broken character encoding could make the AI request go out with an empty body, producing a baffling provider error. Invalid bytes are now cleaned before the request is built.
- When AI features are disabled because of the site's license status, the editor now says exactly that and points to the license page — previously it claimed AI was "not configured", sending users to reconfigure settings that were fine.
- AI task-specific settings (such as the SEO analyzer's larger response budget) were being overridden by the global defaults, which could truncate long analyses. Task settings now take precedence, and bulk SEO analysis now writes its suggestions in the site's content language rather than the admin panel language.

---

## [2.65.42] - 2026-08-05  ·  _Patch_
**SEO Preview in the Post Editor Now Always Shows Real Data**

### Fixed
- The search-result preview at the top of the SEO Settings box could render completely empty — just the URL, no title or description — whenever the SEO title and description fields were blank but an SEO record already existed for the post (for example after setting only a focus keyword). Your published page never had this problem: the site falls back to the post title and excerpt, but the preview didn't mirror that. The preview now uses the exact same fallback chain as the live site — SEO title → post title, SEO description → excerpt → content text — so it always shows what Google will actually see.
- The preview also updates live now: typing in the post title, excerpt or slug immediately refreshes the preview (previously it only reacted to the SEO fields themselves), long titles and descriptions are truncated at Google's display limits, and the URL line follows your slug as you edit it.

---

## [2.65.41] - 2026-08-05  ·  _Patch_
**Archive Pages Now Emit Breadcrumbs and a Proper Listing Type**

### Improved
- Category, tag and author archive pages now include BreadcrumbList structured data (Home › Category), so Google can show a breadcrumb trail under these pages in search results — previously only single posts had one. The archive pages are also now typed as CollectionPage instead of a generic WebPage, which more accurately tells search engines they are listing pages. Single posts and the homepage are unchanged.

---

## [2.65.40] - 2026-08-05  ·  _Patch_
**Heading Fixer Capitalizes Turkish Words Correctly**

### Fixed
- The Heading Fixer tool (Advanced SEO → Content) title-cases your headings, but it capitalized the first letter with a routine that follows English rules: a Turkish lower-case "i" became a dotless "I" instead of the correct dotted "İ". So on Turkish sites a heading like "içerik yönetimi" was turned into "Içerik Yönetimi" instead of "İçerik Yönetimi", and every word starting with i (izmir, internet, iş…) was mis-capitalized. Capitalization now follows the site's content language: Turkish sites get the correct İ/ı casing, English sites are unchanged (i → I). "ışık" → "Işık", "içerik" → "İçerik".

---

## [2.65.39] - 2026-08-05  ·  _Patch_
**A Failed Security Check No Longer Looks Like a Server Crash**

### Fixed
- When an admin action failed its CSRF security check — most commonly a benign case: you left a tab open long enough for the token to rotate — the server replied with HTTP status 419. That code is not part of the official HTTP standard, so Apache rewrote it to 500 on the way out, and the browser showed a scary "500 server error" for what was really just an expired token. The request is now rejected with the standard 403 Forbidden, which Apache passes through unchanged, so the admin gets the correct "please reload and try again" response and server logs stop showing phantom 500s. This affects every admin form and AJAX action, not only the SEO tools.

---

## [2.65.38] - 2026-08-05  ·  _Patch_
**Correct Social-Share Image Dimensions and Turkish Word Counts**

### Fixed
- The og:image:width / og:image:height tags were hardcoded to 1200×630 for every share image. Sites that use portrait featured images (common on recipe, pets and Pinterest-focused blogs) were telling Facebook, LinkedIn and Twitter the image was landscape, so the social-card preview came out cropped or letterboxed. The tags now report the image's real dimensions (read from the file), and are omitted entirely when the size can't be determined — a wrong size is worse than none.
- Word counts and "X min read" estimates were computed with a routine that only understands the English A–Z alphabet, so Turkish letters (ü, ı, ğ, ş, ç, ö) were treated as word breaks — "güzel" counted as two words. This inflated the reading-time badge, the JSON-LD wordCount and the schema "time required" value by roughly 40% on Turkish sites. All of these now count whole Unicode words, matching the SEO analyzer, so the numbers are correct across the article, its structured data and every theme.

---

## [2.65.37] - 2026-08-05  ·  _Patch_
**Traffic Setup Score Reads 0% Until You Connect a Channel**

### Fixed
- After the previous fix, a brand-new site still showed 17% instead of 0%. The AI-crawler policy was being counted as a completed setup step, and since it defaults to "allow all," every fresh site got that one step for free. But that setting is about letting bots read your site (inbound), not about distributing your content (outbound), so it never belonged in the distribution setup score. It has been removed from the calculation — a site with nothing connected now reads 0%, and the score rises only as you actually connect social, Pinterest, IndexNow, WebSub or the newsletter. The AI policy is still shown in the card, just not counted.

---

## [2.65.36] - 2026-08-05  ·  _Patch_
**SEO and Setup Scores Start at 0 on a Fresh Site**

### Fixed
- The dashboard's Traffic Control ("Distribution setup score") showed 48% on a brand-new site with nothing configured. It was built as "100 minus penalties," and because the penalties never summed to 100 the score floored around 48 no matter what. It is now a true completion score — done setup steps ÷ applicable steps — so an unconfigured site reads 0% and rises as you connect social, Pinterest, IndexNow, WebSub and the newsletter. Queue/bounce errors are no longer mixed into the score; they stay in the issues list.
- The single-post SEO analyzer showed 29/100 before you typed anything. Two categories scored full marks on a blank post: readability (an empty draft trivially has "no long paragraphs or sentences") and schema (a blank draft defaults to "auto"). Both are now only graded once there is real content, and a post with nothing entered reads 0. The posts list and the server-side recalculation were aligned the same way, so a blank post is 0 everywhere instead of 29 in the editor and 5 in the list.
- The AI analysis endpoint returned a 500 error for a non-POST request; it now returns a clean 405 Method Not Allowed.

---

## [2.65.35] - 2026-08-05  ·  _Minor_
**A Professional Media Library: Drag to Select, Edit Alt Text Without Leaving the Page**

### Added
- WebP and AVIF quality are now configurable from settings, with safe universal defaults (WebP 82, AVIF 60). As before, uploaded JPEG/PNG files are converted to a modern format and the original is not kept, keeping your uploads folder lean.

### Improved
- The Media library now works like a modern media manager. Drag a rectangle across the grid to select several images at once, or Ctrl/Cmd-click to add and remove items individually. A floating action bar appears with the count and one-click Delete, so bulk actions no longer need the dropdown.
- Each image has a pencil button that opens a slide-in panel where you can edit the title, alt text and caption without leaving the page — with a live character counter and guidance to keep alt text under ~125 characters. Images still missing alt text are marked with an "Alt missing" badge, and the badge clears the moment you add one.
- The library header now shows WebP and AVIF support at a glance, plus how many items are still missing alt text or a caption, so accessibility and SEO gaps are easy to spot.

---

## [2.65.34] - 2026-08-05  ·  _Patch_
**Your FAQ Now Shows on the Page, and Autosave Is Calmer**

### Fixed
- The FAQ questions and answers you enter under Structured Data were only sent to search engines as hidden schema — they never appeared on the page for readers. They now render as a clean expand/collapse "Frequently Asked Questions" section at the end of the article, on every theme. (This also matches Google's own requirement that FAQ content be visible on the page.)
- Autosave ran every 30 seconds, which was more often than needed and could collide with the editor switching a new post into draft-edit mode. It now runs every 2 minutes.

---

## [2.65.33] - 2026-08-05  ·  _Patch_
**URL Slugs Keep Turkish Letters When a Draft Is Saved**

### Fixed
- As you typed a title, the URL slug was built correctly ("Sokak Modası" → sokak-modasi). But the first time the draft was saved — by autosave or the Save button — the slug was rebuilt by a different, broken routine that dropped Turkish letters instead of converting them, turning sokak-modasi into sokak-modas. Because the editor then re-read that broken slug, a manual save kept it broken too. All slug generation now goes through the single correct routine that converts Turkish letters (ı→i, ş→s, ğ→g…) rather than dropping them.

---

## [2.65.32] - 2026-08-05  ·  _Patch_
**Checklist Boxes Line Up With Their Text**

### Fixed
- In a checklist, each checkbox sat slightly above its line of text. The box is now vertically centered on the first line of the item, so the list reads cleanly — and on a checklist item that wraps to two lines the box still lines up with the first line.

---

## [2.65.31] - 2026-08-05  ·  _Patch_
**Tables, Checklists and Captions Look Right on the Page**

### Fixed
- In the posts list, the row "Trash" action did nothing when clicked. The row's little form was nested inside the bulk-actions form, which browsers quietly ignore; the click is now handled correctly and the post moves to Trash. Restore, Delete and the "add sample content" button in the same list were affected the same way and are fixed too.
- Tables written in the editor appeared on the page as plain text with no borders or spacing. They now have proper borders, a shaded header row and cell padding, and scroll sideways on narrow screens instead of overflowing.
- Checklists (task lists) showed a bullet next to each checkbox with the text on a separate line. They now render as a clean checkbox and text on one line, with checked items struck through.
- An image caption sat far below its image, looking disconnected. It now sits directly under the image, centered and quietly styled.
- When a brand-new post was first saved automatically as a draft, the Revisions panel and the preview-link button did not appear until a manual reload — because the page was still showing its "new post" layout. The editor now switches to the full draft-editing view once the draft is saved, without interrupting your typing.

---

## [2.65.30] - 2026-08-05  ·  _Patch_
**Analytics Daily Totals Are More Robust**

### Fixed
- ZeroTrack Analytics builds a daily summary from visited paths and referrers. If a single visit carried text in a broken encoding, saving that whole day's summary could fail. The summary now stores such values safely, so a day's totals are never lost to one unusual request.

---

## [2.65.29] - 2026-08-05  ·  _Patch_
**Analytics Reach Subfolder Installs — and Forms Never Crash**

### Fixed
- On a site installed in a subfolder, ZeroTrack Analytics silently recorded nothing: the visit beacon was sent to the domain root, where nothing answers. It now targets the install itself, so visits are counted wherever jekcms lives.
- The newsletter, comment and contact forms answered with a server error when a field arrived in an unexpected shape. They now reject such input politely instead of failing the page.
- Recipe schema times typed as plain numbers — "15" instead of the ISO form — were published as-is, which fails Google's Rich Results validation. Times are now normalised on output ("15", "15 min" and "15 dk" all become PT15M), and a value that cannot be understood is left out rather than published broken.

---

## [2.65.28] - 2026-08-05  ·  _Patch_
**What You Type in the SEO Panel Is What Google Sees**

### Fixed
- The social share image chosen in the post editor was saved but never shown: every theme kept using the featured image when a post was shared. The image you pick is now the one social networks display.
- On the Lifestyle, News and Pets themes the SEO title you wrote was ignored — the browser tab and search results showed the plain post title instead. Lifestyle also ignored the SEO description. All three now honour the SEO panel.
- On the Health theme, category, tag, search and author pages all carried the same title — just the site name. Each archive now gets its own descriptive title, as on the other themes.
- A post whose SEO title field was cleared ended up with a browser-tab title that began with the separator, like " | My Site". It now falls back to the post title.
- A featured image stored with an extra path prefix produced a broken image address and silently dropped the share image. The prefix is now corrected on the way out.

---

## [2.65.27] - 2026-08-05  ·  _Patch_
**Search Returns Posts, Not Legal Pages**

### Fixed
- Site search on the Lifestyle, Minimalist and Tech themes returned pages — privacy policy, terms, cookie policy — mixed in with blog posts, and counted them in the result total. Search now returns posts only, and the count matches. The Pets theme's "not found" page listed pages among its recent posts for the same reason.
- A malformed request could make any page answer with a server error. Sending a form field in the wrong shape was enough; the page returned HTTP 500, which search engines read as "this page is broken". Such requests are now ignored instead of failing the page. The same applied to the login, contact and comment forms.
- Content carrying an older character encoding — typically brought over from WordPress — could stop a meta description or a URL slug from being generated, which in turn could halt an import. The text is now repaired as it comes in.
- Under the same conditions, media details, SEO analysis records and scheduled task logs could fail to save. They now store the repaired text instead of failing.

---

## [2.65.26] - 2026-08-05  ·  _Patch_
**The Dashboard Stops Counting Pages as Posts**

### Fixed
- The dashboard greeting could report posts you had not written. Publishing pages — the legal pages generator creates several at once — was counted as "5 posts published today", while the content calendar right below it correctly showed nothing for the same day. The greeting now counts posts only, so the two agree.
- The "Scheduled" list on the dashboard also showed scheduled pages among the posts. It now lists posts only, matching the drafts list next to it.

---

## [2.65.25] - 2026-08-05  ·  _Patch_
**Author Selection Works — and Your SEO Fields Stay Put**

### Fixed
- The Author dropdown in the post editor was empty on a newly installed site, so there was no way to say who a post belongs to. It now lists everyone who can write on the site — the administrator included — and opens on the account you are signed in with.
- When you did choose an author, your choice could be quietly replaced with a different writer on sites that have more than one. The name you pick is now the name that is saved.
- Text carrying an older character encoding — most often content brought over from a WordPress site — could stop a post from saving, or let it save while silently discarding the whole SEO panel with it: meta title, description and focus keyword all disappeared without a word. Such text is now repaired as it comes in and the SEO fields are kept.
- On installations served over a non-standard port, every save in the admin panel was refused as a security failure, which left the panel unusable. Ports are no longer part of that check.
- A writer account could publish a post under someone else's name, and a post could be assigned to a deleted or subscriber account. Both are now rejected on the server.

---

## [2.65.24] - 2026-08-04  ·  _Patch_
**Your Logo Shows Up — and You Decide How Big**

### Added
- Görünüm → Customize now has a logo height control for the header and the footer. Each theme starts from a sensible default for its own header, and you can change it with a slider; the width follows automatically and the aspect ratio is never distorted.

### Fixed
- A logo uploaded under Settings → Brand did not appear in the header or footer on several themes — the favicon, social share image and search-engine logo were all correct, only the site itself never showed it. Every theme now displays it.
- Saving your profile failed with a server error whenever social links were filled in. Saved links were not being shown back to you either. Both are fixed.

---

## [2.65.23] - 2026-08-03  ·  _Patch_
**Sites Stay Crawlable When the Database Is Busy**

### Fixed
- On shared hosting the database refuses new connections once the account hits its simultaneous-connection ceiling. A page that hit that moment returned HTTP 500 — the code search engines read as "this page is broken", which costs indexing. Measured under a parallel crawl, 1.7% to 6.7% of requests were failing this way.
- The connection is now retried briefly with a randomised backoff, so short collisions resolve invisibly. If the database is still unreachable, the page answers 503 with Retry-After instead of 500 — the signal that means "temporarily busy, come back" rather than "broken".
- Error responses are no longer cacheable, so a CDN cannot keep serving an outage page after the site has recovered.
- About page (travel theme): a stray backslash was printed in the "Popular topics" text.

---

## [2.65.22] - 2026-08-03  ·  _Minor_
**Footer Designer, Now in Every Theme**

### Added
- Appearance → Footer now opens the full footer designer in every theme: pick one of eight layouts, build your own columns (menu, categories, text, newsletter, contact, brand), set the brand block, social icons and bottom bar — with a live preview.
- Previously only one theme had this; the other thirteen offered a handful of fields. The designer now lives in the core, so any theme gets it.

### Fixed
- A footer saved before this release no longer changes your site on its own — the new designer only takes over once you save it yourself.

---

## [2.65.21] - 2026-08-03  ·  _Patch_
**Sidebar Label Fix**

### Fixed
- On Turkish installs the sidebar link for footer settings still read "Footer" instead of matching the tab name.

---

## [2.65.20] - 2026-08-03  ·  _Patch_
**Appearance → Footer Opens the Footer Settings Directly**

### Fixed
- Clicking Appearance → Footer bounced you to a different screen, which read as "this theme has no footer settings". The menu item now opens the footer settings directly, with no redirect in between.
- The sidebar item was still labelled "Footer" in Turkish; it now matches the tab name, "Alt Bilgi".

---

## [2.65.19] - 2026-08-03  ·  _Patch_
**Footer Tab Is Visible Again**

### Fixed
- In every theme the Footer settings were folded into the Advanced panel, so clicking Appearance → Footer opened Advanced and no Footer tab was anywhere to be seen. Footer is now its own tab, right next to Menu.
- Three tab labels in one theme were still in English.

---

## [2.65.18] - 2026-08-03  ·  _Patch_
**Menu and Footer Customization in Every Theme**

### Fixed
- Five themes — including the one new sites start with — opened an empty screen when you went to customise the menu or the footer. Every theme now has both.
- The "Copyright text" field under Appearance → Footer was saved but never appeared on the site. It works now, and supports {year} and {site_name} placeholders.

---

## [2.65.17] - 2026-08-03  ·  _Patch_
**Dark Mode Switch Fixes**

### Fixed
- In one theme the dark mode switch stopped responding after moving to another page, and only worked again after a refresh.
- In two themes the dark mode switch did nothing at all.
- Because those switches never worked, their dark palettes had gone unchecked: several cards kept a fixed white background and turned white-on-white in dark mode. Both themes are now readable in dark mode.

---

## [2.65.16] - 2026-08-03  ·  _Patch_
**Readability, Pages and Checkout Reliability**

### Improved
- Text contrast across themes was reviewed and raised where it fell short, improving readability and accessibility scores.
- Upgrading from the free plan to a paid licence now carries your existing site over instead of leaving it unlicensed.
- Licence checks are more forgiving of temporary network problems and no longer misread addresses that start with www.
- Password reset and update downloads are more robust.

### Fixed
- Order confirmation after payment could fail to record. Payments now complete reliably.
- Visitors whose device is set to dark mode could see unreadable text on some themes. Light and dark are now both checked.
- About and Contact pages written in the admin were ignored by several themes and never appeared on the site. They now show up.
- The homepage slider is aligned with the header width, keeps its rounded corners and shadow, and no longer clips its text on phones.
- Page numbers in one theme were listed vertically with bullet points instead of a row of buttons.
- The editorial box under articles had no styling and blended into the article text.
- Social icons in one theme's footer were invisible.

---

## [2.65.15] - 2026-08-02  ·  _Patch_
**Stability & Integrity Improvements**

### Improved
- Internal reliability and integrity improvements across the core. No changes to how you write or manage content.

---

## [2.65.14] - 2026-08-02  ·  _Patch_
**License Seats Stay in Sync**

### Fixed
- When a site's seat is released from the customer panel, that change now takes effect on the site itself. Previously a site could keep running on a seat that had already been freed, so the seat count and what was actually installed could drift apart. The admin now re-checks with the license server shortly after you open it and, if this domain is no longer registered to the license, shows a clear notice with a one-click reactivation link.

---

## [2.65.13] - 2026-08-02  ·  _Minor_
**What You Write Is What You Get**

### Added
- Galleries: multiple images render as a responsive grid, and clicking one opens it full-screen in a lightbox.

### Improved
- The editor now matches the published page. Paragraph spacing and Shift+Enter line breaks looked one way while writing and another way live — a shared content-typography standard now drives both the editor and every theme, so what you see in the editor is what readers get.
- A single, modern icon set (Lucide, self-hosted) replaces scattered inline SVGs. The news theme's Font Awesome CDN dependency is gone — icons now load from your own server, better for privacy, offline installs and speed.
- Images can now be placed left or right with text wrapping around them (like a magazine layout), or centered — straight from the editor's align buttons.
- The automatic logo is now also produced as a PNG, so Google's Organization logo and social shares get a real raster image instead of an SVG some platforms won't render.

### Fixed
- The homepage slider now actually works. Its settings (slide count, autoplay, duration, arrows, dots) were in Customize but no theme shipped a slider template, so choosing "Slider" quietly fell back to a plain hero. A universal slider template now honours every setting, in any theme.

---

## [2.65.12] - 2026-08-02  ·  _Patch_
**A Sharper Brand Image**

### Improved
- The automatic brand-image generator got a real upgrade. Your social share image (OG) now carries a proper corporate signature — a domain line along the bottom, depth on the title, and a lifted monogram badge — instead of a flat, generated look. Shared links finally look like they belong to a brand.
- The Branding screen's template picker now shows what each layout actually produces — badge, headline, tagline and signature line — with clean square corners, so you pick by seeing the real composition instead of guessing from two flat bars.
- The social share image is now managed in one place — Branding. The duplicate field that also lived in the SEO tab is gone, replaced by a pointer, so there's no more confusion about which one the site actually uses.

### Fixed
- Deactivating your license from the admin now actually brings the license warning back. Before, "Deactivate" cleared only part of the stored license, so the panel still believed a valid license was present and the reminder banner never returned — the deactivation was effectively invisible. It now clears the full local license state, and works even when only the settings-side token was left behind.

---

## [2.65.11] - 2026-07-29  ·  _Patch_
**A Fresh Install Tells the Truth**

### Improved
- Theme previews in the setup wizard are now twice the size, so you can actually see what you are choosing. Hovering a card reveals a "View demo" link that opens the live theme showcase in a new tab — pick with your eyes, not from a thumbnail.
- On the wizard's finish screen, "View Site" now opens your site in a new tab, so the completion page with your next steps stays where you left it.

### Fixed
- Right after installation the admin greeted you with "License validation has not succeeded for 999 days" — alarming, and not what was happening. When no license key has been entered yet, the panel now simply asks you to enter it; the day counter only ever appears after a real validation has aged.
- The free edition's Updates screen claimed all 14 themes and 13 plugins were installed. "Installed Components" now reports what is actually on your server — and when you upgrade to a paid license, the missing premium components are offered for install exactly as before.
- On installs without the distribution plugins, the dashboard showed a "Traffic Control" panel with a made-up setup score and links to screens that don't exist. Plugin panels now appear only when the plugin is actually installed, and the score is computed only from the channels you have.

---

## [2.65.10] - 2026-07-29  ·  _Patch_
**Quizzes Speak Your Panel's Language**

### Added
- The Recipe plugin now has a place in the admin menu. It used to work invisibly — recipe data is filled in per post in the editor — so there was nothing to click and no way to see which posts carry a recipe card. A Recipe Cards screen now lists those posts with their status, links straight to the editor, and explains where the data lives.

### Fixed
- The quiz screens now follow the panel language. On a Turkish panel the list page greeted you with "New Quiz", "All / Published / Draft", "Search quizzes…", "No quizzes found" — and the editor's placeholders and buttons were English too. Every label on the list and editor screens now reads in the panel language, and the search row uses the same layout as the rest of the panel instead of a stacked, misaligned one.
- Opening a quiz screen before the plugin was ever activated no longer ends in a server error. The quiz tables were created only when the plugin started; the screens now create them on first visit, the same self-healing the contact form received.

---

## [2.65.9] - 2026-07-29  ·  _Patch_
**The Messages Link Opens the Messages**

### Fixed
- The Contact Form entry in the admin menu answered "not found". The messages screen moved to its current address a while ago and old bookmarks were being redirected — but the menu itself still pointed at the old address, which redirects only from the old location, not from the one the menu produced. The menu now links straight to the messages screen.

---

## [2.65.8] - 2026-07-29  ·  _Patch_
**License State Is Not Public Reading**

### Security
- Your installation's internal state files — version.json and VERSION.txt — are no longer served over the web. They hold licence and component details that belong to your admin panel, not to the public internet; the panel keeps reading them from disk exactly as before, so nothing changes in daily use.

---

## [2.65.7] - 2026-07-29  ·  _Patch_
**The Wizard Cleans Up After Itself**

### Security
- The setup wizard now proves its own files are gone when installation finishes. The wizard and the package zip were already being deleted at the end, but the deletion was never checked — if the server refused it, both files stayed behind without a word, and a forgotten installer is an open door. Removal is now verified on disk, and when any file survives, the finish screen names it and gives exact instructions: open FTP or your hosting file manager, go to the site root, delete these files. Same behaviour on the paid and the free package.

---

## [2.65.6] - 2026-07-28  ·  _Patch_
**Only Your Software on Your Server**

### Changed
- Where the free edition stops, it now says so and shows what a paid plan adds. The plugins page, the themes page, the footer editor and the post editor each carry the same short card — what is closed, what opens, and a link to the plans in your customer portal — instead of an empty screen or a missing page.

### Fixed
- The footer editor no longer ends in a missing page. It used to forward every unsupported theme to the theme customizer, which the free edition does not ship — so the link answered "not found". It now explains where the footer logo lives on the free edition and links straight to it, and the menu entry is hidden when neither editor is available.
- The SEO analysis panel is no longer shown on the free edition. It appeared in the post editor and reported nothing, because the scoring engine is part of the paid package. The save and preview bar above it stays exactly where it was.
- The License screen now knows the free plan. A site running a valid free license was labelled "Unlicensed" on both the License and Updates screens, because the free tier was missing from the plan table — the product did not recognise the license it had issued itself. Plan names also read in the panel language now instead of always in English.
- Paid plans no longer show bought features as switched off. The feature badges came from an older tiering in which Personal had no premium themes and Standard had no plugins; every paid plan includes everything and only the number of sites differs, so the badges said otherwise to paying customers.
- A fresh installation no longer answers with an error on its own home page. The table that records reads was created only when the first post was viewed, but on a new site the first page anyone opens is the home page — and the Minimalist theme reads that table to build its popular-posts list. The table is now part of the installation, and the Reports screen, which is built entirely on it, opens on a brand-new site as well.

### Security
- The setup wizard belongs to whoever opens it first. The first visit claims the wizard for that browser session, and a session from another address is refused while installation is still in progress; the way out is one line on screen: delete config/.install-claim. The claim expires by itself after twelve hours, so an abandoned setup never locks the site permanently.

### Removed
- The installation package no longer carries storefront code that belongs to jekcms.com rather than to your site. Those files could never run on your server — the tables they need are not part of the product schema — so all they did was produce a broken page on your own domain and an error entry in your log. Your installation is smaller and quieter without them.

---

## [2.65.2] - 2026-07-28  ·  _Patch_
**One Language Per Page**

### Fixed
- Theme wording now follows the site language everywhere, not only in the footer. Sixty-six labels in the bundled themes carried a single hard-coded default — some English, some Turkish — so a page could show both at once. Each label now carries both languages, and the page language attribute follows the site setting instead of the language declared by the theme.

---

## [2.65.1] - 2026-07-28  ·  _Patch_
**A Site That Behaves: Logo, Language and Newsletter**

### Added
- Setup wizard: the site language and the admin panel language are chosen separately during installation, instead of being inherited from the language of the wizard itself.
- Setup wizard: the theme step shows a real preview of each theme instead of a coloured strip.

### Fixed
- The newsletter form no longer appears on installations that do not have the newsletter plugin. The free edition ships without it, yet themes still printed the form on every page — and a visitor who typed an email received a server error. The interface is now drawn only when the feature exists, and the endpoint answers "not found" instead of failing.
- A logo uploaded during setup now also appears in the footer. The footer was reading a separate setting and, when it was empty, printed a fixed letter left over from the original site the theme came from — so the site name could be anything and the footer still showed the same initial. You can still set a different footer logo, or remove it, under Appearance.
- Theme wording follows the site language. A site installed in Turkish had Turkish legal pages but an English footer, newsletter box and "Page Not Found" screen — two languages on one page. Theme labels may now carry both languages, and an English label from a theme no longer leaks onto a Turkish site.

---

## [2.65.0] - 2026-07-28  ·  _Minor_
**Update Channel Restored, and a Real Path from Free to Paid**

### Added
- Güncellemeler screen: components your plan covers but your installation does not have can now be downloaded one by one. Coming from the free edition, premium themes and plugins were never on disk, and the channel only ever offered updates for what was already installed — so a paid plan delivered nothing until the whole package was reinstalled by hand.
- Customer portal: a free licence now shows the paid plans, and once a paid licence exists the site can be moved onto it in one click. A domain belongs to one licence at a time, so the new licence previously could not be added while the free one still held the site; the move does both steps at once and does not spend a slot from the 30-day move allowance.

### Fixed
- Updates could be listed but never downloaded. The key used to verify the signed update manifest was rotated on the server and the matching key never reached the product, so every install refused each package with a verification error while the panel still advertised the update. The current key now ships with the product; core, theme and plugin downloads work again. This is the single most important reason to install 2.65.0.

### Security
- A licence upgraded in place from the free edition now receives a newly issued key. The key format itself marks a licence as free, so raising only the plan column would have left the customer paying for a plan the update channel still treated as free.

---

## [2.64.1] - 2026-07-28  ·  _Patch_
**Security Fix: Contact Notification Email Headers**

### Fixed
- Replies to a contact notification now go to the person who wrote the message. The reply-to address was being set through a method the mailer did not have, so the call quietly did nothing.
- A site name containing characters that look like a pattern reference no longer corrupts the header when the brand name is printed next to a square logo.

### Security
- The subject a visitor types into the contact form went into the notification email header as-is. A crafted subject could therefore add headers of its own — enough to have the site send mail to addresses the owner never chose, from the site's own domain. Every value that reaches a mail header is now stripped of line breaks and encoded, on both the SMTP and PHP mail paths, and recipient addresses are validated before use. Sites running 2.64.0 with the new contact notification should update.
- The AI draft screen now requires an administrator, matching the other content screens. It previously accepted any signed-in account, so an editor or author could generate content with the site's own API key.

---

## [2.64.0] - 2026-07-28  ·  _Minor_
**A Setup Wizard Worth The First Impression — And A Contact Form That Delivers**

### Improved
- The setup wizard was rebuilt around the first impression: a welcome that says what will happen, the four steps shown up front, the three ways to start side by side on one row, system checks in two columns, and motion that points at what matters. It respects reduced-motion settings and works the same on a phone.
- The contact form now brings its own appearance. It used to inherit whatever the theme happened to provide, which on most themes was nothing — raw browser fields with labels beside them. Themes that style the form themselves are left untouched.
- The wizard asks for the administrator name properly instead of silently filling in "Admin", and offers only the themes that are actually inside the package you are installing.

### Fixed
- The setup wizard would not start. A single unescaped apostrophe in a Turkish label broke the whole page script, so the wizard opened with empty labels and a spinner that never stopped. Every download since 2.60.0 carried it. The wizard now parses in both languages and a release check keeps it that way.
- Contact messages were being lost. On some installations the messages table had never been created — it was only built when a plugin was activated or an administrator happened to open the messages page — so submissions vanished while the visitor was told "message received". The table is now created the moment a message needs to be stored.
- No email ever went out for a contact message. The message sat in the panel and the site owner heard nothing. Owners now receive a notification with the sender set as reply-to, so a reply is one click away.
- A contact message could disappear silently. Four separate anti-spam paths dropped the message and still answered "sent". Nothing is discarded any more: a suspicious message is stored under Spam with the reason attached, so a false alarm can be recovered instead of lost.
- The spam filter was tuned for comments and flagged ordinary contact messages — a plain message could land in Spam and never reach the owner. Contact submissions now only count as spam on decisive signals, and lesser suspicion is recorded as a note instead of blocking the message.
- A stray search box appeared next to the logo on desktop headers. The in-menu search guarantee was modifying the page on load; it now only appears when the mobile menu opens and is removed when it closes.
- An uploaded brand logo could overflow the header at its natural size. Every theme now caps the header logo, and a square logo (an icon rather than a wordmark) is shown with the site name beside it instead of leaving the brand nameless.
- Related articles showed an initial instead of the author photo, while the same card showed the photo everywhere else.
- On the finance theme, the newsletter box in category and author pages stretched down the whole page, and the author header was hard to read on its coloured band.

---

## [2.63.5] - 2026-07-27  ·  _Patch_
**The Search Sits At The Top Of Every Mobile Menu**

### Improved
- Where a theme already puts a search inside its mobile menu, it is now moved to the top and given the same full width as everywhere else. The travel theme kept it at the very bottom, below every link, where it was easy to miss. All fourteen themes now open the menu the same way: search first, then the links.

---

## [2.63.4] - 2026-07-27  ·  _Patch_
**Search Always Inside The Mobile Menu**

### Fixed
- The mobile menu now always contains a search field. The search icon in the header disappears on narrow screens in different ways from theme to theme - one hides it at a breakpoint, another runs out of room, a third has it switched off in the theme settings. Rather than chase each theme, the menu itself now guarantees it: if the menu has no search of its own, one is added at the top. Themes that already put a search there keep theirs.

---

## [2.63.3] - 2026-07-27  ·  _Patch_
**Search On Mobile, In Every Theme**

### Fixed
- The search button was missing from the mobile header in the finance theme. Its buttons sat inside the navigation element, and the theme hides that element on small screens, so the search and day/night buttons went with it. They now sit outside it and stay visible.
- The personal and trends themes had no search on phones at all: the header search box is hidden on small screens and nothing replaced it. Both now carry a search field at the top of the mobile menu, the way the pets theme already did.
- The touch-target rule no longer resizes custom switches. The day/night control in the trends theme is a pill-shaped switch, and a 40px minimum turned it into a black circle.

---

## [2.63.2] - 2026-07-27  ·  _Patch_
**A Readable Mobile Menu In Dark Mode**

### Fixed
- In dark mode the mobile menu showed dark text on a dark panel, so the links were almost invisible. The shared mobile menu pinned its colours to light values for every theme, and nothing set the matching dark ones. The menu now reads the theme you are actually in, and follows it even if you switch the theme while the menu is open.
- The order of the header buttons on phones and tablets is now day/night, then search, then the menu button on the far right.

---

## [2.63.1] - 2026-07-27  ·  _Patch_
**Mobile Header, Dark Documentation, Readable Turkish**

### Fixed
- On phones and tablets the search and day/night buttons now sit on the right, next to the menu button, in that order. They used to be pushed up against the logo while the menu button stood alone at the far edge. The layout is the same in all fourteen themes.
- Documentation pages follow dark mode again. They were asking for colours that were never defined; a colour the browser cannot resolve makes it drop the whole line, so the backgrounds stayed white with no error anywhere.
- Turkish text that had been stored through the wrong character set, showing accented letters as pairs of unrelated symbols, has been repaired across the site.

---

## [2.63.0] - 2026-07-27  ·  _Minor_
**Empty Screens, Dark Logo And Instant Refresh**

### Improved
- On the Turkish site every page address is now Turkish: the cookie policy moved from /tr/cookie-policy to /tr/cerez-politikasi, with the old address redirected so existing links keep working.
- Language alternate links now describe the page you are actually on. Documentation sub-pages were all announcing the documentation index instead of themselves, which made search engines discard the annotation for a third of the site.

### Fixed
- An admin page could stop rendering halfway through, leaving everything below the greeting blank. A single empty date, image or e-mail column coming from the database was enough to do it. Every display helper now tolerates empty values, so one missing field can no longer take down a whole screen.
- The dark mode logo you upload under Settings → General → Branding is now the logo that appears in dark mode. Some themes were guessing it from the light logo's filename instead of reading your setting, which showed an unrelated file or a broken image.
- Uploading a logo now takes effect immediately. The address of the file carries a stamp derived from the file itself, and saving settings clears the CDN cache as well, so you no longer wait for the old copy to expire.
- Publishing or editing a post also refreshes the CDN copy of your home page, feed and sitemap.
- File sizes of zero are shown as "0 B" instead of producing a warning.

---

## [2.62.5] - 2026-07-27  ·  _Patch_
**Update Confirmation Shows The Version You Just Installed**

### Fixed
- The confirmation message after a core update now shows the version that was installed.
- Theme and plugin updates also name the component's new version in the confirmation message.

---

## [2.62.4] - 2026-07-27  ·  _Patch_
**Reliable Rollback For One-Click Updates**

### Fixed
- The backup taken before a core update now covers every file that update changes, so restoring it returns the site to exactly its previous state.
- Version information is included in the backup. After a rollback the admin panel and the update service report the same version.
- Your media is never placed in an update backup, so backups stay small and your files are untouched.

---

## [2.62.3] - 2026-07-27  ·  _Patch_
**Security Follow-Up: Environment Detection And Content Visibility**

### Security
- A site decides whether it is running locally by looking at the server itself, never at the address a visitor sends. Local development is unaffected; set the JEK_ENV environment variable if you want to pin the mode.
- Private network address matching was tightened, so lookalike external addresses are not treated as local.
- Posts marked private are now hidden not only on their own page but also in archives, search, related and featured lists, the sitemap and the RSS/Atom/JSON feeds. This matters for sites migrated from WordPress, where private posts arrive as published. Administrators and editors still see everything in the panel, and an author still sees their own.
- SVG files in a WordPress package are scanned as content during import; files carrying scripts or external references are not accepted. Static SVG logos import normally.

---

## [2.62.2] - 2026-07-27  ·  _Patch_
**Security Release: Stricter Input Validation And Reliable Throttling**

### Security
- Environment detection is decided by the server itself rather than by anything a visitor sends, so an installed site always runs in production mode.
- Rate limiting on login, API and upload paths is now accurate under concurrent traffic.
- Restoring a backup only accepts a .zip inside your own backups directory. Any other path is refused.
- A WordPress package import writes only recognised media files. Anything else in the package is skipped and counted, and never lands in your uploads folder.
- On an already-installed site, the setup wizard's remaining steps — including the WordPress cleanup — are tied to the browser session that performed the installation.
- The support endpoint gives the same answer for every licence key it does not accept, and is rate limited.
- The contact form links a message to a customer account only when the sender is signed in as that customer; everything else is filed as a guest request.
- Language alternate links are escaped on output and built from a sanitised page name.
- Newsletter click tracking verifies a signature before redirecting, so tracking links always lead where they say they do.
- The newsletter queue worker only runs with the configured cron secret. Running it from a real cron job is unchanged.
- Outgoing mail requires an encrypted connection: if TLS cannot be negotiated the send is aborted, and the newsletter mailer verifies the server certificate.

---

## [2.62.1] - 2026-07-27  ·  _Patch_
**Security Release: Tighter Role Boundaries And A Leaner Installation Package**

### Fixed
- Theme stylesheet and script addresses now carry a stamp derived from the file itself. Before this, a corrected theme file could sit on the server for months while browsers and the CDN kept serving the old copy for up to a year.
- Signing in on jekcms.com now updates the header immediately instead of leaving the "Sign In" button in place.

### Security
- The installation package is leaner: distribution-side components that a site owner never runs are no longer part of it.
- Admin screens that affect the whole site — the ad manager, banner editor and comment import — require an administrator account.
- Authors can edit, trash or delete only their own posts and their own media. Bulk actions skip anything that belongs to someone else and tell you how many items were skipped.
- The newsletter subscriber list and campaign sending are administrator-only.
- The order confirmation page shows an order only to the customer it belongs to.
- Invoice PDFs live in a directory that is closed to the web and carry a random filename. They remain downloadable from your customer portal, where ownership is checked.
- A licence that has been revoked or suspended cannot download the installation package.
- A post marked private is not served to visitors on its own page. Administrators and editors still see it.
- The example environment file ships with obvious placeholders, so a fresh installation always generates its own signing keys.

---

## [2.62.0] - 2026-07-25  ·  _Minor_
**Move From WordPress With One File: The jekcms Migrator Plugin**

### Added
- A WordPress plugin that packs your whole site into one file. Install "jekcms Migrator" on your WordPress site, press Start export, download the .zip -- that is the entire WordPress side. No database host, user or password, and no server-to-server MySQL connection, which most shared hosting blocks anyway. The export runs in batches and saves its progress, so sites with thousands of posts finish without hitting PHP time limits.
- The package carries posts, pages and drafts, the category tree with its parent-child structure, tags, authors with their bios, approved comments, menus, media files, SEO titles and descriptions from Yoast, Rank Math or All in One SEO, and a redirect map from every old URL to its new address.
- Two ways to bring the package in: the setup wizard has a third scenario ("Import a WordPress package") for brand-new installs, and an existing site takes it from Admin panel -> Import -> WordPress package. Both use the same import engine, so both apply exactly the same rules.
- Imported images are copied into your own uploads folder and the addresses inside the content are rewritten to those local copies -- including the scaled variants WordPress writes into post bodies. Your images keep working after the old site goes offline.
- Old WordPress URLs are installed as 301 redirects during the import, so links in search results and on other sites keep working.
- The plugin is in the Downloads section of your customer portal, in English and Turkish.

---

## [2.61.0] - 2026-07-24  ·  _Minor_
**Google Console Grows Up: Connect With One Click -- No Cloud Console -- and Real Performance Charts**

### Added
- Connect with your Google account in one click -- like the big-name SEO plugins. Press "Connect with Google", sign in, approve; done. No Google Cloud project, no API enabling, no client ID/secret. The flow runs through jekcms's central OAuth relay: tokens are handed to your site server-to-server with a one-time code and never appear in a browser URL. The old "your own Cloud app" method remains as an advanced option.
- Search Console now shows real charts and breakdowns: a clicks-and-impressions performance chart over the whole period, separate CTR and average-position trend charts, plus device and country breakdown tables -- alongside the existing top queries and top pages.
- Analytics gained a daily users-and-sessions chart for the selected period.

### Fixed
- The indexing-coverage scan tested page URLs with the redirecting /page/ prefix, so static pages were wrongly flagged as errors; it now checks the canonical /slug address.

---

## [2.60.5] - 2026-07-24  ·  _Patch_
**Content Wizard Tuned Like Clockwork: A Bulletproof AI Prompt, Multi-Part Imports, and a Working "Start Fresh"**

### Improved
- The copy-paste AI prompt now works like clockwork on ChatGPT, Claude and Gemini alike: hard JSON-validity rules (single-string escapes, plain quotes, first/last character contract) plus a chunking protocol for long batches -- the AI closes each part as valid JSON on its own and continues with only the remaining articles.
- The single-draft AI Content generator was upgraded from its v1 prompt to the wizard's quality standard: zero-fabrication rule, banned AI-tell phrases, honest handling of volatile figures, and the site language as the default -- with a larger response budget so long drafts no longer get cut off.

### Fixed
- The wizard's "Start fresh" button appeared to do nothing: it reloaded the page and the browser silently restored the old form values. It now performs a clean reset via a fresh navigation -- saved parameters are wiped and the wizard truly starts over.
- Importing the AI's answer in multiple parts overwrote the earlier batch: only the last part got scheduled. Imported items now accumulate across parts, the input box clears for the next part, and the calendar step covers every article.
- The AI Content page rendered the model's raw HTML straight into the admin preview. The preview now passes through a strict sanitizer (tag whitelist, event handlers and script URLs stripped).

---

## [2.60.4] - 2026-07-24  ·  _Patch_
**Single-Post Publishing Hardened: Clean Structured Data, and Scheduled Posts That Fire Every Publish Signal**

### Improved
- The editor's SERP preview and pixel meter now measure the full rendered title -- including the theme's " | Site Name" suffix -- matching what Google actually truncates.
- The permalink bar and SEO snippet preview now show the real canonical URL (/slug) instead of the redirecting /post/ prefix, and the SEO analyzer no longer marks empty FAQ rows as an applied FAQ schema.

### Fixed
- Hidden "enable" fields in the editor submitted even while invisible, so every save quietly wrote empty Product/Event/Review/Course/Recipe/LocalBusiness objects into the post's schema data -- and picking a type without filling its fields could emit an incomplete schema node on the live page (a Search Console error waiting to happen). Blocks are now saved only for the selected type when they carry real content, and the live output also skips all-empty legacy blocks.
- Selecting the Recipe or Local Business schema type showed no fields until the post was saved and reloaded; both panels now appear instantly, and the live JSON-LD preview covers them too.
- Scheduled publishing ran outside the content quality gate and stamped a fake 400-3000 view count on every calendar-published post. All scheduler entry points now converge on one gated engine: PublishPolicy decides, the recorded publish date is the planned time, and view counters stay untouched.
- Posts published by the calendar went out silently -- no social auto-share, newsletter, push or search-engine ping ever fired. The scheduler now runs the same post_published pipeline as a manual publish.
- A post marked as scheduled without a date could hang in the queue forever; it is now date-stamped on save and goes live on the next scheduler pass.

---

## [2.60.3] - 2026-07-24  ·  _Patch_
**Deep SEO Audit Pass: Correct Page Schemas, One Canonical URL per Post, and a News Sitemap That Respects Publish Time**

### Improved
- Static pages (About, Contact...) no longer declare themselves as blog articles in structured data: the misleading BlogPosting node is gone and the WebPage node gained a description. Posts keep their full Article graph untouched.
- More tracking parameters are now stripped with a 301 (gclid, msclkid, twclid, igshid, mc_eid and friends), and UTM parameters are caught anywhere in the query string -- fewer duplicate URLs reach the index.

### Fixed
- Uppercase or otherwise-cased URL variants of a post used to render as a 200 page pointing the canonical at the wrong variant -- a duplicate-content opening. Any request whose path differs from the stored slug now 301-redirects to the single canonical URL, in every theme.
- The Google News sitemap used the creation date instead of the publish date: scheduled posts could miss the 48-hour news window or report the wrong publication_date. It now keys on the actual publish time, and the keywords list is truly capped at five.

---

## [2.60.2] - 2026-07-24  ·  _Patch_
**Traffic & Distribution Untangled: One Flat Tab Bar Instead of Nested Menus, and Three Publisher Cards per Row**

### Improved
- The Traffic & Distribution screen dropped its inner module sidebar: modules are now a single horizontal tab bar, ending the confusing nested navigation.
- Publisher cards in News Publishers now lay out three per row (two on narrow screens), so the catalogue scans much faster.

---

## [2.60.1] - 2026-07-24  ·  _Patch_
**Traffic & Social, Sharpened: Full-Text Feeds Repaired, Fresh 2026 Backlink and Publisher Sources, and Far Less Text to Wade Through**

### Added
- New verified backlink sources in the Authority Builder: #JournoRequest tracking (X/Bluesky), the AllTop curated directory, product testimonial outreach, Product Hunt and Indie Hackers for tech sites, and the WalletHub expert panel for finance sites.
- New publisher channels in News Publishers: Refind (curated link digests) and Techmeme (the tech industry news river), each with honest, step-by-step guidance.

### Improved
- Much less text to wade through: publisher cards now show a two-line summary with full details folded away, backlink source cards fold their "why & how" paragraphs, and the Social Connections screen gained a status strip with a "connected channels only" filter.
- The News Publishers readiness checklist now performs real HTTP checks on your RSS feed and sitemaps (cached for 10 minutes) instead of always showing green.

### Fixed
- Critical: the main feed generator was silently failing on every request and falling back to a minimal RSS without full article content -- breaking the full-text requirement of platforms like NewsBreak and SmartNews. Full-text feeds are restored, and the "full content in feed" switch now defaults to on.
- Saving Traffic or Social settings on installs where the plugin tables were never created used to fail (silently or with a server error); both plugins now create their own tables on demand.
- The Hashnode documentation link in News Publishers pointed to a page that no longer exists.

---

## [2.60.0] - 2026-07-24  ·  _Minor_
**Cloud Backups Arrive: A Tabbed Backup Center, Truly Complete Backups, and an Import That Survives Every Broken CSV**

### Added
- Cloud backup: send backups to S3-compatible storage (AWS S3, Cloudflare R2, Backblaze B2, Wasabi, MinIO) or an FTP/FTPS server -- with a one-click connection test, encrypted credential storage, per-backup "send to cloud" buttons and an option to auto-upload the daily backup. Step-by-step setup guides for each provider are built into the page.
- The Backups screen is now a tabbed center: Backups, Cloud Backup and Schedule. Creating a backup shows a modern toast notification and the new backup appears right in the history list -- no more hunting at the bottom of the page.
- Import safety options: "skip existing content" (re-running the same CSV never creates duplicates) and an optional old-site address that rewrites internal links to your new domain.

### Improved
- Full backups are now truly full: themes and plugins are included alongside the database and media, and restore puts them back safely. Automatic maintenance keeps cleaning old auto-backups per your retention setting.
- The importer now handles real-world files: semicolon-separated Excel exports, Turkish Windows-1254 encoding, rows with missing or extra columns (repaired and reported instead of silently dropped), and huge CSVs are streamed without exhausting memory. Wrong files get a clear upfront error listing the missing columns.
- The import button locks while running with a progress note, so an impatient double-click can no longer import everything twice. The setup wizard's finish screen now offers a direct "Import Content" shortcut.

### Fixed
- Admin profile photos showed as broken images in the user list, user editing and the top bar when the avatar was stored with an absolute uploads path -- the admin now resolves avatars exactly like the site front end.
- Error messages on admin pages could silently vanish: the shared admin header overwrote the page's error variable while rendering flash notices. Import errors (wrong file, security token) are now actually visible.
- Custom S3 endpoints with a port number (e.g. MinIO) lost the port and the upload went to the wrong server.

---

## [2.59.3] - 2026-07-24  ·  _Patch_
**One Tidy General Tab: Media and Social Move In, and the API Tab No Longer Crashes on Fresh Installs**

### Improved
- Settings -> General now hosts seven sub-tabs: Site Info, Branding, Localization, Reading, Discussion, Media and Social Media. The sidebar got two entries shorter; old links redirect automatically and saving returns you to the same sub-tab.

### Fixed
- Settings -> API & Automation could crash halfway with a server error on installs where the AI tables were never created (the setup wizard did not install them). The tables now ship with the installer, are self-created on first visit, and the page renders safely even if creation fails.
- Daily background maintenance now also repairs the AI tables on existing installs, so the fix reaches every site without any manual step.

---

## [2.59.2] - 2026-07-24  ·  _Patch_
**Tidier Settings and Serious Spam Defense: General Now Has Sub-Tabs, and Bot Floods Can No Longer Bloat Your Database**

### Added
- Settings -> General is now organized into sub-tabs: Site Info, Branding, Localization, Reading and Discussion. Reading and Discussion moved out of the sidebar into General -- fewer clicks, less clutter; old links redirect automatically.
- Flood guard: comments, the contact form and newsletter signups now have hourly and daily per-IP caps plus a site-wide hourly ceiling. Requests over the cap are silently dropped without ever touching the database -- a bot army can no longer pump millions of rows into your site. Limits are adjustable under Comments -> Spam Protection.
- Newsletter hardening: a honeypot field catches bots, blacklisted addresses are filtered, and any single email address can receive at most 3 subscription emails per day -- so nobody can weaponize your signup form to mail-bomb a victim.

### Improved
- The spam filter got sharper: it now also scores bot-like browser signatures, missing user agents and shortened URLs (bit.ly and friends), on top of the existing link, keyword and timing checks.
- Definite spam is no longer stored: spam comments used to be written to the database and pile up -- now they are rejected outright, with only a compact trace kept in a self-pruning log (30-day retention, hard row cap). The contact form now runs through the same spam engine too.
- Automatic maintenance now also clears spam comments older than 30 days and stale rate-limit counter files.

### Fixed
- Database maintenance cleanup was silently doing nothing on MariaDB servers (the table checks always failed), so old logs and view records never got purged -- cleanup now actually runs.
- The logo and social-image generators read the site name from a field that now lives on another sub-tab; they fall back to your saved site name instead of a generic placeholder.

---

## [2.59.1] - 2026-07-24  ·  _Patch_
**Settings, Audited: Maintenance Mode, Static Homepage, Comment Rules, Media Sizes and Cache Controls Now Actually Work**

### Added
- Static homepage: Settings -> Reading can now show a published page as the homepage, with a page picker; switch back to latest posts anytime.
- A master "Comments" switch: turn commenting off site-wide and both the comment blocks and the submission endpoint respect it.
- Maintenance mode is real now: visitors get a proper 503 maintenance page (theme template when available) while signed-in admins keep browsing the site.

### Improved
- Comment rules are wired end to end: moderation on/off decides approved vs pending, "must log in to comment" is enforced on submit, and the default comment status applies to newly created posts.
- Media settings drive real processing: max image size, JPEG quality, thumbnail/medium/large dimensions and the WebP/AVIF conversion switches now control uploads (verified with real uploads).
- Cache controls are honest: the toggle and lifetime now set the Cache-Control header on visitor pages, and the lazy-load switch truly adds or removes lazy loading (LCP promotion preserved).
- The feed "full content" switch works across RSS, Atom and JSON feeds; the timezone setting is now applied to date handling.
- Dead settings that controlled nothing were removed: HTML minify and defer toggles, comments-per-page, time format, and the unused Google OAuth / n8n / ElevenLabs API fields.

### Fixed
- Comment submission could crash with a server error at the spam-check step because the spam filter was never loaded on that path -- submissions now always reach the spam check.
- Changes made on the Settings screen were missing from Settings History; every save from the form is now recorded with old and new values.
- Settings whose stored row lived under a different group could silently fall back to defaults (e.g. cache lifetime); readers are now group-agnostic.

---

## [2.59.0] - 2026-07-24  ·  _Minor_
**Every Theme Is Now Modular: Drag-and-Drop Sections, Menu Designs and Real Color Controls Across All 14 Themes**

### Added
- The modular layout engine now covers all 14 themes. Every homepage is built from reorderable cards in Customize → Homepage: drag to reorder, toggle sections on or off, and tune each one (post counts, titles, category lists) from its gear panel.
- New universal sections in the engine: category spotlights, opinion row, edition strip, video row, CTA band, photo gallery strip, plus sidebar widgets for popular posts, trending, search, social links, an about box and a free info box.
- A Menu tab in the customizer for every converted theme: pick between menu designs (classic, centered, slim and theme-specific variants), toggle sticky behavior, search and the light/dark switch.
- Sidebar control where the theme has one: choose whether it shows on the homepage and post pages, pick left/right placement, and manage the widget stack with the same cards.

### Improved
- Color and typography controls now bind to each theme's real CSS variables with defaults that match the current look exactly — changing a color changes the site, and not changing anything changes nothing.
- Themes that declared menu locations but never rendered them now consume them: primary menus you build in Appearance → Menus finally drive the header in News, Finance, Lifestyle and Recipes, and footer menus render as footer columns.
- Turkish sites get a Turkish storefront on News and Entertainment: section titles, dates, comment forms and newsletter copy now follow the site language instead of being hard-coded English.
- Dead customizer fields that controlled nothing (fake tickers, chart colors, unused archive filters) were removed across themes — every remaining control does something.

### Fixed
- Finance: the Related Posts section always came back empty — it now queries real related content by category and tags.
- News: the comment form silently attached comments to the wrong article (the last related post on the page). Comments now always land on the article you are reading.
- Crypto: trending and article vote counters showed fabricated numbers; they now display the real vote totals from the voting API.
- Lifestyle: menu items built in the admin now resolve page and category URLs correctly instead of printing raw stored links.

---

## [2.58.0] - 2026-07-24  ·  _Minor_
**Branding, Done Right: Generated Logos Publish for Real, OG Images, SERP-Safe Favicons**

### Added
- Social share (OG) image module under Settings → General → Branding: upload your own 1200×630 image or generate one from four professional templates (dark gradient, light minimal, color band, monogram) in your brand color — with live preview and one-click apply.
- Generated favicons now also produce real PNG files (48px + 180px Apple touch icon). Google's SERP crawler does not read SVG/data-URI favicons; the PNG link is emitted first so your icon shows up in search results.

### Improved
- The automatic logo generator was rebuilt: rounded monogram marks, balanced typography, two-letter initials, duotone and pill styles, and two new palettes (slate, rose). Same six styles, distinctly more professional output.
- Settings → General was redesigned in the theme customizer's card language: grouped cards with clear descriptions, two-column field rows, pill source toggles and round color swatches.
- Organization/Person schema now falls back to your site logo when no schema logo is set — search engines get a logo either way.

### Fixed
- Generated logos and favicons never reached the live site — they lived only as admin-side SVG settings while themes read the URL fields. On save, generated assets are now written to real files under uploads/branding and the URL fields are updated; the logo, favicon, OG image and schema all pick them up.
- The Health and Minimalist themes hard-coded favicon links in their header, overriding whatever favicon you uploaded. Removed — the favicon you set in Settings now always wins.
- The footer description text (Settings → General → Site Info) now actually renders under the footer logo on the Health theme.
- Footer customizer on themes that manage their footer via the Theme Customizer (e.g. Health) no longer shows a dead-end notice — it takes you straight to the right Footer section.

---

## [2.57.5] - 2026-07-24  ·  _Patch_
**Health Theme: The Footer Menu Location Now Actually Renders in the Footer**

### Fixed
- On the Health theme, a menu assigned to the Footer location never appeared — the footer columns were fixed. When the footer menu has items, it now replaces the "For You" column, titled with your menu's name; when empty, the footer keeps its current layout exactly.

---

## [2.57.4] - 2026-07-24  ·  _Patch_
**Menu Manager Redesigned: The Customizer's Card Language, Applied to Menus**

### Improved
- The Menus screen now speaks the same visual language as the theme customizer: menu items are drag-handle cards showing the title and a muted path, with a rotating chevron opening each item's settings; the menu list uses count badges and calm hover states; the add-item panels became clean scrollable pickers. Everything reads clearly in dark mode.
- Admin copy on this screen was tightened to short, direct statements.

---

## [2.57.3] - 2026-07-24  ·  _Patch_
**Menu Manager Repaired: No More Phantom Items, Instant Frontend Sync, One Save That Saves Everything**

### Fixed
- The menu manager silently re-created sample items ("Home, Recipes, About, Contact" in English, with categories nested under Recipes) every time the page was opened while a menu was empty — deleted menus kept coming back and the skeleton did not match the active theme or site language. That auto-seeding is gone; an empty menu simply falls back to the theme's own navigation, and the explicit "Fill Default Items" button remains for those who want a starter set built from real categories.
- Menu changes now reach the site immediately: every menu save clears the navigation cache. Previously the frontend could keep serving the old menu for up to half an hour, so the admin and the site disagreed.
- Menu name, display location and items are now one form with one save — pressing the items' save button used to silently discard a just-changed display location, which snapped back to "Primary" after refresh.

---

## [2.57.2] - 2026-07-24  ·  _Patch_
**Theme Switching Hardened: Switch as Often as You Like, Every Switch Lands Clean**

### Fixed
- Switching between certain theme pairs could crash mid-switch: the activation step loaded the new theme's helper functions into the same request as the old theme's, and shared helper names collided fatally, leaving the site half-switched. Activation now loads only the new theme's configuration — the next page load brings its helpers in cleanly. Verified with a new behavior test that cycles through all 13 themes twice, checks homepage, post and archive rendering on each, and asserts zero residue after returning to the original theme.

---

## [2.57.1] - 2026-07-23  ·  _Patch_
**License Activation and Heartbeat Restored on the Server, Plus Menu Tab Polish**

### Improved
- The Menu tab is tidier: the sizing sliders sit on one row and the four element switches (sticky, search, light/dark, social icons) align on a single row beneath them — powered by a new per-tab column layout theme authors can reuse.

### Fixed
- The license server's activation and heartbeat endpoints were failing with a server error due to a wrong database-call signature — activations could not complete and installs never got their periodic license confirmation, which surfaced as a persistent "license could not be verified" notice. Both endpoints now respond correctly; installs re-validate automatically on their next check-in.
- On the Personal theme, the menu's logo size slider had no effect when a wide brand logo was uploaded — the slider only drove the compact brand mark. It now sizes the wide logo too.
- Slider tracks in the customizer were invisible in dark mode — only the thumb showed. Sliders now use themed tracks and thumbs that read clearly in both light and dark.

---

## [2.57.0] - 2026-07-23  ·  _Minor_
**The Menu Tab Grows Up: Five Designs Including Floating Box and Two-Tier, Plus Logo Size and Padding Controls**

### Added
- Two new menu designs join the visual picker (Personal and Health): Floating Box — the menu sits in a rounded, softly-shadowed bar detached from the page edge — and Two-Tier, a classic editorial layout with the logo and tools on top and a full-width menu strip beneath.
- Fine-grained header sizing: a logo height slider and a vertical padding slider let you make the top menu as compact or as commanding as you want. The Slim design scales both proportionally.

---

## [2.56.0] - 2026-07-23  ·  _Minor_
**A Menu Tab for the Customizer: Visual Design Picker, Sticky Behavior and Element Switches**

### Added
- A new Menu tab sits between Post Page and Sidebar in the customizer (Personal and Health themes). Its centerpiece is a visual design picker — mini header mockups you click to switch the top menu between three layouts: Classic, Centered (logo on top, menu below) and Slim (a lower, quieter bar).
- Menu behavior and elements are now switches: keep the menu sticky or let it scroll away, and show or hide the search, the light/dark switch and social media icons (accounts come from Settings → Social). The Personal theme learned to show header social icons for the first time — off by default.
- The visual picker is a new reusable field type for theme authors (choice_cards): any theme option can now be presented as clickable design cards instead of a plain dropdown.

---

## [2.55.0] - 2026-07-23  ·  _Minor_
**Health Customizer, Brought Up to Par: Page-First Tabs, a Real Appearance Tab and Post-Page Structure Controls**

### Added
- The Health theme now has the same customizer structure as Personal: the tab bar reads Homepage, Post Page, Sidebar, Appearance, Advanced. Colors and typography live in Appearance, the newsletter widget copy sits inside the Sidebar tab, and footer texts moved under Advanced.
- Post-page structure controls for Health: header style (classic or compact), breadcrumb, excerpt lead, reading progress bar and a featured-image switch — new elements ship switched off, so nothing changes until you opt in.
- Appearance controls that actually work: Health's color pickers now drive the theme's real palette (primary, accent, text, muted, backgrounds, border) with separate light/dark values, and heading/body fonts, content text size and line height apply across the whole theme. Defaults match the current design exactly.

### Fixed
- The old Branding color fields on Health pointed at CSS variables the theme never used — they looked adjustable but changed nothing. They were replaced by the wired Appearance controls above.

---

## [2.54.3] - 2026-07-23  ·  _Patch_
**Customizer: The Variant Dropdown Panel Is No Longer Clipped by Its Card**

### Fixed
- The admin's styled dropdown component draws its option panel inside the layout card, and the card's overflow clipping was cutting the panel off — sometimes leaving just a sliver visible. A card now releases its clipping while its dropdown is open (the same proven rule the post editor's publish box uses), so the full option list always appears.

---

## [2.54.2] - 2026-07-23  ·  _Patch_
**Customizer: The Variant Dropdown Now Opens Cleanly on Layout Cards**

### Fixed
- The variant dropdown on layout cards could open glitched or misplaced. Cause: the whole card was permanently marked as draggable, which interferes with native dropdowns in Chrome. Cards now become draggable only while you are actually holding the drag handle — dropdowns open exactly like everywhere else in the admin, and the menus got the same arrow icon as the rest of the panel.

---

## [2.54.1] - 2026-07-23  ·  _Patch_
**Customizer: Live Sidebar Preview and a Dropdown Fix**

### Added
- The Sidebar tab now has its own live preview: the widget stack on the right mirrors your changes instantly — switch a widget on or off or drag it to a new spot and the preview follows.

### Fixed
- Opening a layout card's variant dropdown could nudge the card's content upward and clip its title. Cards no longer scroll internally, so the dropdown opens cleanly every time.

---

## [2.54.0] - 2026-07-23  ·  _Minor_
**The Health Theme Goes Modular: Drag-and-Drop Homepage, Widget Sidebar and Post-Page Blocks**

### Added
- The Health theme now runs on the modular layout engine — the second theme after Personal. Its homepage sections (hero, trending topics, most popular, recommended, latest articles) become drag-and-drop cards in the customizer: reorder them, switch them off, and tune hero autoplay and cycle speed, posts-per-tab and posts-per-page from each card's gear.
- A real sidebar for Health post pages: the About Me card and table of contents are now widgets you can reorder or disable, joined by five optional ones — latest articles, categories, tags, a newsletter mini-form and a free-form custom content box. Widget-level sticky control and a right/left position switch included.
- Post-page blocks are modular too: the author box, related posts (with a post-count setting) and the comments section can be reordered or turned off from the Post Page tab.

### Improved
- The layout engine learned per-theme capability declarations: a theme now lists exactly which variants and settings each section really supports, along with its own defaults — so the customizer only ever shows controls that actually do something in the active theme.
- The Health customizer was cleaned of controls that had no effect: leftover fields from an earlier design (hero texts, category row options, archive grid and disclaimer toggles among others) are gone, replaced by the working layout cards. Existing sites keep their exact current look until they change something.

---

## [2.53.2] - 2026-07-23  ·  _Patch_
**Customizer Polish: A Unified Appearance Tab with Rich Typography, One Toggle Language and Pixel-Aligned Cards**

### Added
- A new Appearance tab gathers Colors and Typography in one place — and both grew up. Typography now controls body text size, heading size, line height, paragraph spacing and content column width; Colors gained muted text, border and content-link colors. Defaults match the current look exactly, so nothing changes until you change it.
- The homepage hero and categories cards absorbed their text options (kicker tag, button label, section title) into their gear settings — the loose, confusing text-field pile at the bottom of the Homepage tab is gone.

### Improved
- The tab bar is now truly page-first: Homepage, Post Page, Sidebar, Appearance, Advanced. Layout cards align pixel-perfect — variant menus have a fixed width (no more shifting when you pick an option), and every card reserves the same columns so all toggles line up vertically.
- One toggle language everywhere: the customizer now uses the same switch component as the rest of the admin. The layout preview also reflects your variant choice by name, and the Reset Layout button moved up into the tab header where it belongs.

---

## [2.53.1] - 2026-07-23  ·  _Patch_
**Detail Controls, WordPress-Grade: Block Design Variants, Sticky Widgets and Post-Header Structure**

### Added
- Design variants for post-page blocks: the author box can render classic (horizontal) or as a centered card, comments come in classic or minimal (compact, avatar-free) style, and related posts switch between a card grid and a row list — each picked right on its layout card, with a round/square avatar shape option for author cards.
- Per-widget sticky control in the sidebar: every widget's gear now has a "Sticky" switch — decide whether the table of contents, share box or any other widget stays on screen while scrolling or flows with the page.
- Post-header structure controls: header style (classic centered or compact left-aligned), plus switches for the breadcrumb, the excerpt lead, the "continue reading" indicator and the reading progress bar.

### Improved
- The Advanced tab got tidier: a short description explains what lives there, its own fields are grouped under a "Custom Code" heading, and the Branding and Author sub-sections sit clearly separated below.

---

## [2.53.0] - 2026-07-23  ·  _Minor_
**The Customizer Thinks in Pages Now: Modular Sidebar with Widget Cards, a Modular Post Page, and a Cleaner Tab Structure**

### Added
- A brand-new Sidebar tab: the sidebar is now a widget stack you compose with cards — author card, table of contents, share, plus new widgets: recent posts, categories, tag cloud, a mini newsletter form and a Custom Content box for your own HTML. Drag to reorder, toggle, tune counts.
- Sidebar visibility matrix: decide where the sidebar appears — post pages, archive/category pages, search results and author pages each have their own switch, and you can dock the sidebar left or right. Pages without it get the full width automatically.
- The post page went modular too: the author box and comments are reorderable below-content blocks, related posts is a tunable end-of-page block, and a new toggle controls the featured image.

### Improved
- The customizer tabs were reorganized around pages: Colors and Typography first, then Homepage, Post Page and Sidebar — each page tab contains its own layout cards and options in one place. Branding and Author collapsed into Advanced as sub-sections, so the tab bar stays short and every control lives exactly where you would look for it.

---

## [2.52.1] - 2026-07-23  ·  _Patch_
**Layout Cards Grow Up: Per-Section Settings and a Live Page Preview**

### Added
- Every layout card now opens its own settings via a gear icon. The hero slider is fully tunable: slide count, autoplay on/off, seconds per slide, optional prev/next arrow buttons and dot indicators. Popular and Latest sections control their post counts from the card. Settings that only apply to one variant appear only when that variant is selected.
- A live page skeleton preview beside the cards: the final page is mirrored box by box in the order you arrange, updating instantly as you drag, toggle or retune sections — plus a one-click link to open the real site in a new tab. A page selector is in place for the post-page layout coming in the next phase.

### Improved
- The layout cards were rebuilt on a solid grid: no more overlapping variant menus or squeezed labels; existing slider preferences (like slide count) migrate into the new settings automatically, so nothing changes until you change it.

---

## [2.52.0] - 2026-07-23  ·  _Minor_
**Your Homepage, Your Order: Modular Layout Engine Arrives — Drag, Toggle and Restyle Sections**

### Added
- A new section-based layout engine turns theme pages into reorderable building blocks. In Customize → Layout, every homepage section (hero, intro grid, categories, popular, latest posts, newsletter band) is a card you can drag to reorder, switch off, or restyle with a variant — the page then renders top to bottom in exactly that order. No theme files are touched, and one click restores the theme default.
- Section variants: the hero can now run as a multi-post slider or a calm single-post opener, chosen from the layout card. The variant system is built into the engine, so future sections and themes gain variants without new UI work.
- The Personal theme is the first to go fully modular: its homepage is now composed of six independent sections. Existing sites look identical until you change something — saved settings and the classic order carry over untouched. Remaining themes migrate to the engine in upcoming releases.

### Improved
- The theme customizer got tidier: the newsletter tab moved out — newsletter design (email templates, signup placements, popup) is managed on its own Newsletter → Appearance page, and the customizer now links there. Legacy per-section show/hide toggles are absorbed into the Layout tab so each control exists in exactly one place.

---

## [2.51.3] - 2026-07-23  ·  _Patch_
**One Brand Voice: jekcms Now Introduces Itself the Same Way Everywhere**

### Added
- EULA 2.1: the agreement now records the jekcms trademark application before the Turkish Patent and Trademark Office (Application No. 2026/095211, Nice Classes 09 and 42), turning the trademark clause from a general statement into a verifiable fact.

### Improved
- jekcms now speaks with one voice: the positioning is "Next-Generation Blog CMS", the homepage slogan is "Start Your Blog. Publish Your Posts." and a single product definition explains what it manages (posts, pages, images and comments in one panel). The same wording now appears on the marketing site, the admin login screen, the license screen and site metadata — replacing four different, jargon-heavy taglines that each described the product differently.
- Technical qualifiers like "self-hosted" and hosting requirements moved out of the first impression and into the feature and comparison sections where technically minded buyers actually look for them.

---

## [2.51.2] - 2026-07-23  ·  _Patch_
**License Protection Hardened: Installations Now Report Their Integrity, and Every Copy Stays Traceable**

### Added
- License heartbeats now include a signed-manifest integrity summary: an installation whose protected core files have been modified is flagged on the license server, so tampered or cracked copies surface automatically instead of going unnoticed.
- Every release now carries a SHA-256 manifest of its source tree as timestamped evidence of authorship — the record that backs your licence if a copy of jekcms ever turns up where it should not be.

### Improved
- Official core updates now regenerate the file-integrity manifest automatically, so a legitimate update is never mistaken for tampering.
- The footer credit is now generated through the integrity layer and tied to the installation's fingerprint, strengthening the traceability chain of every deployed copy.
- The pricing page now explains, in plain language, how the license you pay for is protected: traceable copies, non-functional pirated installs, and the legal guarantees of EULA 2.0.

---

## [2.51.1] - 2026-07-23  ·  _Patch_
**EULA 2.0: A Hardened License Agreement with Stronger Electronic-Acceptance Evidence**

### Improved
- The End User License Agreement was upgraded to version 2.0 with maximum commercial protection: explicit bans on publishing the source code to public repositories, sharing or publishing license keys, and using the code to train AI models or build datasets — each now covered by the liquidated-damages clause. New sections cover electronic acceptance as a binding signature (with an evidence agreement), agency/third-party installations, trial/developer license limits, personal-data processing grounds (KVKK), the no-withdrawal rule for instantly delivered digital goods, and standard severability/no-waiver/entire-agreement terms. Domain limits now correctly reflect the purchased plan.
- Acceptance records got stronger evidentiary value: both the checkout consent and the first-login admin consent now record the agreement's own version (EULA 2.0) and a SHA-256 hash of the exact text accepted, alongside the existing timestamp, IP, browser and identity records.
- The agreement is now readable at a public /eula page rendered from the very same file that ships with the product, showing the version and text hash; the checkout consent link points there instead of the general Terms of Service.

---

## [2.51.0] - 2026-07-23  ·  _Minor_
**Newsletter Grows Up: 6 Email Templates, Selectable Signup Placements and a Scheduled Popup; Contact Form Admin Rebuilt**

### Added
- Six selectable email designs for campaigns and newsletters — Signature, Clean, Bold, Editorial, Dark and Minimal — chosen from a visual picker with live previews (Newsletter → Appearance), applied to the campaign template with one click. All designs are email-client-safe (table layout, inline CSS).
- Signup form placements you control: choose where the newsletter form appears — end of every post, top of the sidebar, a band above the footer, and/or a popup. No theme files are touched; the plugin injects the form on every theme through one universal point.
- A polite newsletter popup: shown after a delay you set (in seconds), at most once per day per visitor, never again after subscribing, with four selectable styles — centered card, corner card, bottom bar or mini card.

### Fixed
- The Contact Form admin link no longer 404s: its pages moved to the standard plugin-admin location and the inbox was rebuilt as a tabbed page (Inbox + Settings in one place) with unread badge, filters, search, mark-all-read and the message settings alongside.

---

## [2.50.4] - 2026-07-23  ·  _Patch_
**Theme/Plugin Updates No Longer Resurface After a Core Update; Admin Visits Now Drive the Scheduler Too**

### Improved
- The visitor-triggered scheduler (scheduled publishing + automatic updates, no cron required) now also fires on admin panel visits — on a low-traffic site, simply logging into the admin is enough to keep automation running. A real cron job remains optional.

### Fixed
- Fixed an update loop where an already-applied theme update kept coming back: the core package carries a version ledger, and a stale entry in it could mark an up-to-date theme as outdated again after every core update. The updater now rebuilds the theme/plugin ledger from what is actually on disk after each core update, and the release pipeline generates the packaged ledger from the real component versions — so the loop cannot recur from either side.
- Automatic updates now apply the core first and then theme/plugin updates (with a fresh check in between), so a core update can no longer overwrite the version records of components updated in the same run.

---

## [2.50.3] - 2026-07-23  ·  _Patch_
**Automatic Updates Now Work from Real Cron Jobs**

### Fixed
- Update downloads triggered from a real (CLI) cron job were rejected by the license check: without a web request there is no host header, so the download request reported "localhost" instead of the licensed domain and the server refused it — automatic updates could never actually install from cron. The updater now always uses the domain stored with the license activation (matching how the update check already behaved), so scheduled automatic updates install correctly. Verified end-to-end: a live install auto-updated its core from cron with the license intact.

---

## [2.50.2] - 2026-07-23  ·  _Patch_
**Your License Now Survives Core Updates; Plugin Cards, System Menu and AdSense Intro Polished**

### Improved
- Plugin cards are aligned and consistent: the action button row now sits at the same height on every card, descriptions are standardized to a fixed length range (with a display clamp as a safety net), and previously unlocalized plugins (Stories, Cloudflare, AdSense Readiness, ZeroTrack) got proper Turkish/English names and descriptions.
- The System section of the sidebar is reordered by frequency of use: Settings, Updates, License, Import, Backups, Users.
- The AdSense Readiness first-run screen was redesigned to match the admin design language: a calm card with the scan scope listed as chips and a single standard primary action, replacing the dashed box with duplicate oversized dark buttons.
- The automatic-updates note on the Updates page now stays on a single line on desktop.

### Fixed
- Critical: applying a core update no longer wipes the license activation. The core package ships its own version file and overwriting it dropped the stored license — the panel fell back to "activate your license" and theme/plugin update buttons disappeared. The updater now preserves the license (and a custom update-server address) across core updates. A related latent bug was fixed too: database migrations no longer overwrite the new package version metadata while recording their progress.
- The header update banner now says what is actually pending: the core version when a core update is ready, otherwise the number of theme/plugin updates — instead of a bare "Update available!" that lingered confusingly after a core update.

---

## [2.50.1] - 2026-07-23  ·  _Patch_
**Plugin Cards Now Show a Distinct Icon per Plugin**

### Improved
- Every plugin card on the Plugins page now has its own recognizable icon (newsletter envelope, SEO magnifier, social share graph, analytics bars, cloud, quiz, recipe and more) instead of the same generic circle repeated on every card. Plugins without a dedicated icon fall back to a package icon.

---

## [2.50.0] - 2026-07-23  ·  _Minor_
**Automatic Updates Arrive; the Updates Page Gets Even Simpler**

### Added
- Automatic updates: on the Updates overview you can now choose "Off", "Plugins + Themes" or "Everything (core included)". With it enabled, the scheduler checks once a day and applies pending updates through the same signed channel — backup first, automatic rollback on failure, and every run is recorded in the History tab.

### Changed
- The Updates page is simpler by design: the in-panel ZIP install form was removed. Updates are applied with one click from the overview (or automatically); releases arrive through the signed update channel, so there are no ZIPs to juggle. Update history and release notes keep their own tabs.

### Fixed
- Fixed a server-side configuration blind spot dating back to the security hardening that moved secrets out of the web root: the update/license API could no longer load its database credentials, so the component update catalog silently served empty results. The API now searches the relocated secrets directory as well — theme and plugin updates published to the channel are actually visible to installations again, verified end-to-end against the signed manifest.

---

## [2.49.1] - 2026-07-23  ·  _Patch_
**Updates Page Reorganized into Tabs; Package Install Stays Visible (Locked) on Managed Sites**

### Improved
- The System Updates page now uses the same tabbed layout as Settings: Overview (status strip + available updates + installed components), Install Package, History (updates + backups) and Release Notes each have their own tab, instead of one long scrolling page. The Overview tab shows a pending-update count badge.
- Package type selection on the install tab is now a visual card picker (Plugin / Theme / Core) with the SHA-256 field appearing only for core packages.
- On centrally-managed installations the Install Package tab is no longer hidden: it explains why ZIP installs are disabled there and how they can be enabled when genuinely needed (JEK_ALLOW_SELF_UPDATE); with the flag set, the full install form is available with an overwrite warning.

---

## [2.49.0] - 2026-07-23  ·  _Minor_
**System Updates Page Rebuilt: Plugin/Theme/Core Package Installs, Update History and In-Panel Release Notes**

### Added
- The System Updates page can now install packages by ZIP upload — plugins and themes as well as the core. Plugin and theme packages are structure-validated before install (single safe root folder, a real plugin.php version header or theme.json), a backup is taken automatically and a failed install rolls back. Core packages keep the stricter rule: the official release SHA-256 digest is required.
- A local update history now records every applied update — component, old and new version, whether it came from the update channel or a manual upload, and whether it completed, failed or was rolled back. The history survives cache clears and deployments.
- Release notes are now readable inside the panel: the page shows the full recent core changelog (bilingual, categorized) plus published theme and plugin releases, fetched from jekcms.com and cached for 12 hours. Centrally-managed sites see them too, so operators and site owners follow the same history.
- The installed themes and plugins lists moved into their own collapsible "Installed Components" card with counts, so a site with many themes no longer stretches the version summary into a full-page column.

### Fixed
- Backup folders no longer appear as installed components: a leftover directory like "Trends.bak-20260430-210630" was listed as a theme on the updates page and even reported to the update server. Backup-named folders (.bak/.old/.backup) are now excluded everywhere.
- Live sites no longer display a stale core version: the per-site version file was left behind by deployments (a site could show 2.16.20 while actually running the current release), and it is now synchronized on every release.
- The update report sent after a core update now carries the real previous version instead of always reporting "unknown".

---

## [2.48.0] - 2026-07-23  ·  _Minor_
**Update Notifications Across the Admin: Sidebar Badges, Plugin/Theme Cards and a Dashboard Core Alert**

### Added
- WordPress-style update notifications throughout the admin panel. When an update is published for an active plugin, the "Plugins" sidebar item shows a numbered badge; installed-theme updates show the same badge on "Themes", and the "Updates" item now shows the total pending count instead of a generic mark.
- Plugin and theme cards now show an "Update available vX.Y.Z" notice (with the current → new version in the tooltip) linking straight to the Updates page. The notice appears on every installed plugin, active or not — the sidebar badge only counts active ones.
- A core update now shows a clear notification band on the dashboard with the installed and available version, including a "critical update" emphasis for security releases. Centrally-managed installations receive updates from the operator, so they intentionally show none of these prompts.
- All notifications are fed by a single per-request status helper sitting on top of the existing 12-hour update-check cache, so no extra requests are made to the update server.

### Fixed
- Repaired a disconnect in the update release channel: versions uploaded through the release management panel were stored in a legacy catalog that the client update API never read, so published releases were invisible to installations. The panel now writes to the same catalog the update API, the signed manifest and the download endpoint all read, and lists the SHA-256 of every uploaded package.
- Contact Form 1.0.1: server-side responses (validation errors, rate-limit and security messages) now follow the site language — English sites no longer show Turkish error messages to visitors. Field length limits are now counted in characters rather than bytes, so messages with accented or non-Latin characters near the limit are no longer rejected even though the form allowed them.

---

## [2.47.10] - 2026-07-22  ·  _Patch_
**Content Quality Gate Now Blocks Leaked Rewrite Notes and Stray Image Markers**

### Added
- The Content Quality Gate now blocks publishing when a post contains a leaked editorial process-note — the kind an automated rewrite step can leave behind, e.g. a fake "Kaynak" (Source) section whose text is "metindeki … temizlendi/çıkarıldı" (commentary about what was edited) rather than a real citation. The check is precise: it triggers only on the "Kaynak"+"metindeki" leak signature, so legitimate uses of the word "metindeki" (e.g. in a regex or text-processing article) are never blocked.
- The gate also blocks any post still containing an unresolved [IMAGE:] placeholder marker, which would otherwise leak into the published page as raw text instead of an image.

---

## [2.47.9] - 2026-07-22  ·  _Patch_
**Cloudflare Safety: "Apply Recommended" Is Now Origin-Aware and Can Never Take Your Site Down**

### Fixed
- Fixed a serious bug where "Apply recommended settings" could take a live site offline. It set the Cloudflare SSL mode to Full (Strict) unconditionally; if the origin server's certificate was expired the site returned 526, and if the origin had no HTTPS certificate at all the site returned 525 (SSL handshake failed). Both make the whole site unreachable.
- The recommended SSL mode is now Full (not Full/Strict). Full encrypts browser-to-Cloudflare with a valid certificate and Cloudflare-to-origin as well, but does not reject an expired or self-signed origin certificate, so it can never cause the 526 that Strict does. If your origin certificate is valid you can still upgrade to Full (Strict) manually in the Cloudflare dashboard.
- Added an origin-HTTPS safety gate: before touching the SSL mode the plugin checks whether your origin server can complete a TLS handshake at all. If it cannot (no certificate installed), the SSL setting is skipped entirely and the plugin explains that you need to install a certificate (e.g. free Let's Encrypt) in your hosting panel first. All the other recommended settings still apply. The connected panel also shows this warning up front.

---

## [2.47.8] - 2026-07-22  ·  _Patch_
**Accessibility: Primary Navigation No Longer Trips the "aria-hidden Contains Focusable Elements" Audit**

### Fixed
- Fixed an accessibility violation flagged by page audits (and the newer AI-agent accessibility scan): the shared mobile-navigation script set aria-hidden="true" on the primary unconditionally, but that same element is the visible horizontal menu on desktop. An element with aria-hidden="true" must not contain focusable links, so on desktop the audit reported a malformed accessibility tree.
- aria-hidden (and inert) are now applied only while the mobile panel is genuinely hidden on small screens, and removed on desktop where the navigation is visible and focusable. Also removed a redundant static aria-hidden="true" from the lifestyle theme mobile-nav so it can never leak into the desktop tree. Applies across every installation via the shared, cache-busted navigation script.

---

## [2.47.7] - 2026-07-22  ·  _Patch_
**Cloudflare Panel: Consistent Status Icons and a Truthful Exception-Rule State**

### Fixed
- The two checklists in the connected panel now use the exact same status icons. Previously the recommended-settings list used a plain checkmark while the exception-rules list used a different check-in-a-circle icon, which looked inconsistent.
- The exception-rules list now reflects its real, live state instead of always showing green. The panel reads the current custom rules from Cloudflare and marks each jekcms exception as applied (green check) or not-yet (empty), with an "ALL APPLIED" badge and a re-apply / apply-count button that mirror the recommended-settings card.

---

## [2.47.6] - 2026-07-22  ·  _Patch_
**Cloudflare Exception Rules Now Actually Apply: Right Permission, Modern API, Your Own Rules Preserved**

### Improved
- Removed the colored left-rail line from the sidebar warning cards (a design-system rule) and reworked them into clean, softly tinted alert cards -- amber for attention, blue for info -- that fit the rest of the admin.

### Fixed
- Fixed "Apply exception rules" failing with an Authentication error even when the token had "Firewall Services -> Edit". Diagnosed against the live Cloudflare API: the legacy Firewall Rules API is now frozen (maintenance mode, no new rules), and modern WAF custom rules (Rulesets API) require the separate "Zone WAF" permission -- which "Firewall Services" does not grant. The setup wizard now asks for "Zone -> Zone WAF -> Edit" (with a note explaining why), and every permission error message names the exact permission needed.
- The jekcms exception rules now use a proper skip action that bypasses the relevant Cloudflare security products (WAF managed, browser integrity check, security level, rate limiting, UA/zone lockdown) for the automation and crawler paths, instead of an ineffective placeholder.
- Applying the exceptions no longer wipes your own custom WAF rules. The plugin now reads the existing rules first, refreshes only the jekcms ones, and preserves everything else -- so re-applying is safe and idempotent.

---

## [2.47.5] - 2026-07-22  ·  _Patch_
**Cloudflare Wizard: "Connect" Now Really Connects, Clearer Token Steps, Calmer Sidebar**

### Improved
- The token step now walks through Cloudflare's real screens in order: My Profile -> API Tokens -> Create Token, then explicitly "under Custom token click Get started" (so users do not pick a template that grants the wrong permissions), then naming the token (Token name, e.g. jekcms) before the permission table. This closes the most common wrong-permission trap.
- Reworked the setup wizard into the same calm two-column layout as the connected panel: the step-by-step guide on the left, the critical warnings in a refined right-hand sidebar. Removed the remaining red boxes in the wizard (red read as an error); warnings are now amber "attention" / blue "info" with a clean left-rail accent instead of the previous generic colored icon tiles.

### Fixed
- Fixed a bug where the setup wizard's "Connect" button never actually connected. The test-mode toggle was accidentally nested as a inside the connect ; browsers flatten nested forms, so pressing Connect submitted the toggle action instead -- the token was never saved or verified and the panel stayed stuck in test (mock) mode no matter what. The two forms are now separate, and connecting with a real token always runs a real verification (and clears any leftover test mode).

---

## [2.47.4] - 2026-07-22  ·  _Patch_
**Cloudflare Panel: Real Action Feedback, Permission Diagnostics and a Calmer Layout**

### Improved
- Reworked the connected Cloudflare panel into a two-column layout: the actionable cards (status, recommended settings, automation exceptions, your own rules) sit in the main column, and the "Critical warnings" moved into a calm right-hand sidebar. The warnings are no longer shown as loud red error boxes -- red read like something was broken; they are now amber "attention" and blue "info" notes.
- Unified the panel header (title + description on one clean band with a direct "Open Cloudflare dashboard" button once connected), and the marketing value strip now only shows before you connect, so the connected panel leads with live status instead of a sales pitch.

### Fixed
- Fixed missing feedback on the Cloudflare panel: Purge cache, I'm Under Attack, Apply recommended and Apply exceptions all reloaded the page silently with no confirmation. The panel was writing its flash message under one key while the admin renderer read another, so nothing ever showed. Every action now shows a clear success / warning / error banner.
- Fixed the SSL and Security tiles showing a bare "?" with no explanation when the connected API token lacked the Zone Settings permission. The panel now detects the read failure, shows a plain-language notice telling you to recreate the token with "Zone Settings -> Edit" (and surfaces Cloudflare's own error), instead of a silent question mark.

---

## [2.47.3] - 2026-07-22  ·  _Patch_
**Cloudflare Setup Wizard: Cleaner Layout and a Token Table That Mirrors Cloudflare**

### Improved
- The token step now shows the required permissions as a table that matches Cloudflare's real "Create Token" screen one-to-one (Group / Item / Access), plus a matching Zone Resources row (Include / Specific zone / your domain). You can copy each dropdown value straight across instead of decoding a run-on sentence.

### Fixed
- Fixed a layout bug in the Cloudflare setup wizard where the click-path chips (Domains, Add domain, Overview, etc.) were placed inline inside wrapping paragraph text; their padding was taller than the line, so wrapped lines overlapped and the guide looked jumbled. Each navigation path now sits on its own dedicated breadcrumb row with chevrons, so the text stays clean at every width.

---

## [2.47.2] - 2026-07-22  ·  _Patch_
**Cloudflare Wizard Matched to the Real Onboarding Flow: DNSSEC, AI Policies, and the MX/TXT Nuance**

### Improved
- The Cloudflare setup wizard now mirrors Cloudflare's current add-site flow step by step: Domains → Add domain → "Connect a domain", the new "AI training & search policies" screen (with a jekcms recommendation — Search: Allow and Agent: Allow so you stay visible to search and AI answer engines, matching your llms.txt), picking the Free plan, and reviewing the auto-scanned DNS records before activation.
- Two easy-to-miss but breaking details are now called out explicitly. Turn DNSSEC OFF at your registrar before switching nameservers — leaving it on while you move NS to Cloudflare makes the site completely unreachable. And keep email records (MX, SPF/DKIM TXT) grey "DNS only" while web records (A/AAAA/CNAME) go orange (proxied) — proxying mail records breaks delivery.
- The token step now points at the shorter path too (Overview → API → "Get your API token", or My Profile → API Tokens), and the step indicator reflects the real four phases: Connect, Plan + DNS, NS, Token.

---

## [2.47.1] - 2026-07-22  ·  _Patch_
**Cloudflare Wizard Leveled Up: Polished Steps, Current Dashboard Paths, and a Bot Fight Mode Warning**

### Improved
- The Cloudflare setup wizard was rebuilt to feel like a real onboarding flow: a visual step indicator, a value strip (protection / speed / jekcms-aware), and richer step content with breadcrumb-style dashboard paths that match Cloudflare's current interface — creating a custom token now lists the exact permissions to grant (Zone Read, Zone Settings Edit, Cache Purge, Firewall Services Edit) scoped to the one site, and each step points at the right menu (Overview, DNS, My Profile → API Tokens).
- A critical-warnings block now surfaces two things the API can't safely automate: keep Free-plan Bot Fight Mode OFF — it is aggressive and does NOT honor the jekcms skip rules, so turning it on breaks scheduled publishing, n8n and search/AdSense crawling — and make sure your DNS records are proxied (orange cloud) or the whole CDN/WAF layer is bypassed. The advanced panel also links straight to Cloudflare's Bot settings and WAF custom-rules pages.

---

## [2.47.0] - 2026-07-22  ·  _Minor_
**New Plugin: Cloudflare — a CDN + WAF Edge Layer With a jekcms-Aware Setup Wizard**

### Added
- A Cloudflare plugin puts an optional CDN + WAF layer in front of your site — extra protection and speed on top of jekcms's built-in security (2FA, encrypted keys, signed updates), not instead of it. A four-step wizard walks you through it: create a free Cloudflare account and add your domain, change your nameservers (with the exact NS to set at your registrar), create a scoped API token (the wizard lists the precise permissions — Zone Settings, Cache Purge, Firewall — limited to this one site), then paste the token to connect. The token is stored encrypted with the same AES-256-GCM vault used for AI keys, and is never shown again.
- One click applies the settings that actually fit jekcms — and each one explains why: SSL Full (Strict) because "Flexible" would loop against the server's own http→https redirect; Always Use HTTPS; a TLS 1.2 floor; HTTP/3 and Brotli for speed; a sensible security level and browser integrity check.
- A second one-click step writes the exception rules that keep jekcms working behind Cloudflare — the part a generic plugin gets wrong. Cloudflare's bot/challenge layer is told to skip /api/v1 (n8n and integrations), the scheduled-publishing loopback and the analytics beacon, and robots/sitemap/ads.txt — without these, scheduled posts, automation and search/AdSense crawling silently break. The real visitor IP is already restored safely from CF-Connecting-IP for rate limiting and logs.
- The status panel shows zone/SSL/security state live, offers one-click cache purge and an "I'm Under Attack" switch, and deep-links to Cloudflare's own WAF editor for your custom rules — deliberately kept there, since a mis-written rule can lock you out. Publishing, updating or deleting a post now purges the affected URLs from the edge automatically. A test (mock) mode lets you preview the whole flow before connecting a real token.

---

## [2.46.5] - 2026-07-22  ·  _Patch_
**Dark Theme Pass: the Root Cause of White Boxes Fixed, With a Permanent Guard**

### Improved
- The SERP Identity report's code window now uses a fixed GitHub-dark palette — identical and fully readable in both the light and the dark admin theme, instead of inheriting ambient colors that could lose contrast.

### Fixed
- Several admin screens kept glaring white patches in dark mode — the contact messages card, the sticky "Save settings" bar, the social-profiles box on the user form, the backup info strip. The root cause was one pattern, not many bugs: pages referenced CSS variables under local names (--card-bg, --admin-surface, --bg-subtle…) that the admin stylesheet never defines, so their light fallback color won in every theme. Those names are now bridged to the real theme tokens in one place, the remaining hardcoded light strips were converted to tokens, and a static guard runs with the release gate: any future undefined variable with a light fallback fails the build before it can ship a white box.
- Browser autofill was punching light-lavender fields into dark forms (social connections, backup inputs). Autofilled inputs now keep the admin theme's own background and text color.

---

## [2.46.4] - 2026-07-22  ·  _Patch_
**SEO Tools Accuracy Pass: ads.txt False Negative, Honest Heading Warnings, Stale-Year Scanner, and a Code-Style SERP Report**

### Improved
- The SERP Identity Check turned from a raw text dump — unreadable on the dark admin theme — into a GitHub-style code window: line numbers, syntax coloring on the admin's own theme tokens (correct in light and dark), a clean/review status chip, one-click copy, and the old plain-text output still available for support scripts.

### Fixed
- SEO Health Check could report ads.txt (and favicon) as missing while the file was live: the checker requests a byte range, and web servers answer static files with HTTP 206 Partial Content — which the check treated as failure. 206 is now recognized as success and redirects are followed, so sites with a physical ads.txt are reported truthfully.
- The Heading Fixer's "starts lowercase" warning looked wrong because it never said WHICH heading it meant — it checks subheadings inside the article body, not the post title, so a flag on "Linux RAID Setup: mdadm…" read like a false alarm. The warning is now honest twice over: the label says "a content subheading", the message quotes the actual heading text, and the technical-term whitelist grew by ~40 commands (mdadm, vmstat, iostat, netsh, adb and friends) so command-titled sections are no longer flagged at all.
- The Year Updater only suggested last year by default, quietly missing older leftovers. It now scans every title and slug for any past year and shows them as clickable chips — "2021: 4 posts, 2019: 2 posts" — one click selects that year for the bulk update.

---

## [2.46.3] - 2026-07-22  ·  _Patch_
**Advanced SEO Ships Active by Default — the Single SEO Panel Works Out of the Box**

### Improved
- The Advanced SEO hub — the single panel that 2.46.2 made the one way into every SEO tool — used to require manual activation on a fresh install, which would have left new sites with the old scattered entry points until someone flipped the switch. The plugin now activates itself on first install, so the sidebar entry, the module menu and the single-navigation routing are all there from minute one. Existing installs are untouched: whatever activation state you chose stays exactly as it is.

---

## [2.46.2] - 2026-07-22  ·  _Patch_
**One SEO Panel: Duplicate Entry Points Now Route to the Advanced SEO Hub, Legacy Duplicate Screens Retired**

### Fixed
- The standalone SEO Optimizer page and the Advanced SEO hub were the same tool with two front doors: the dashboard's "SEO score" tiles opened /seo-optimizer.php directly, where the sidebar showed no active section and the hub's module menu was missing. Every tool embedded in the Advanced SEO hub (optimizer tabs, health check, heading fixer, content optimizer, auto-linker, redirects and friends) now routes its direct URL into the hub with the right module selected — old links and bookmarks keep working, the sidebar highlights correctly, and there is exactly one way in. The routing is careful: POST requests, embedded (iframe) loads and unknown internal tabs are never redirected, and if the Advanced SEO plugin is deactivated the standalone pages behave exactly as before.
- Two hidden screens left over from old versions were retired into safe redirects, found by a full inbound-link scan of the admin: "Advanced Ad Manager" duplicated banners.php on the same database table, and "Content Scheduler" duplicated the Content Queue — worse, it carried its own outdated CREATE TABLE that could seed a fresh install with the wrong schema. Both now 301 to their successors; nothing was deleted, old bookmarks land in the right place.
- The WordPress REST API migration tool existed but was linked from nowhere — you could only reach it by typing the URL. It now has a visible entry on the Import screen, next to the SQL/CSV path it complements.

---

## [2.46.1] - 2026-07-22  ·  _Patch_
**Customizer Polish: Light/Dark Color Rows Are Now One Aligned Component**

### Fixed
- The light/dark color pair introduced in 2.46.0 looked cluttered: the disabled dark swatch was squeezed into a thin gray sliver by the flex layout, the two rows didn't line up, and the override checkbox floated awkwardly at the end. Each color is now a single aligned component — a fixed four-column grid (sun/moon tag, swatch, hex, control) shared by both rows, so swatches and hex fields sit exactly under each other; the checkbox became a proper toggle switch; and a disabled dark row dims cleanly with a "theme default" placeholder instead of collapsing.

---

## [2.46.0] - 2026-07-22  ·  _Minor_
**Theme Customizer, Reworked: Separate Light & Dark Palettes, New Theme-Specific Sections**

### Added
- Every color in the theme customizer can now be set separately for light and dark mode. Each color shows a Light and a Dark picker; the dark value is written under the theme's real dark mechanism — the data-theme attribute on ten themes, the .dark-mode class on Finance, and the system preference (prefers-color-scheme) on Lifestyle. An "override" switch per color keeps the theme's own dark tone until you opt in, and themes without a dark mode (Crypto is light-only, Tech is dark-native) simply don't show dark pickers — no fake settings. All twelve theme-specific schemas gained the pairing automatically, without a single line changed in their definitions.
- Minimalist and Lifestyle — the two themes that had been falling back to a thin generic panel — got full, hand-written customizer schemas wired to their actual stylesheets: every color maps to the variable the theme really uses (defaults read from the CSS itself, including Minimalist's dark block), font pickers, layout controls (content width; on Lifestyle also section spacing and grid gap), and real section toggles that were wired into the templates — hero, categories bar and newsletter on the homepage; breadcrumbs, share buttons, author card and related posts on articles (Lifestyle additionally: table of contents and the popular-posts widget). Toggles physically remove the markup, they don't just hide it.
- The default schema for future themes also grew: heading, border and surface colors, body line-height, and font pickers that emit their CSS variables directly.

### Improved
- jekcms.com now tells both stories on the features page: the reworked Theme Customizer (with its light/dark palettes) and the AdSense Readiness plugin shipped in 2.45 — described honestly, including that approval is always Google's call.

### Fixed
- The Lifestyle theme's customizer had never actually worked: the theme's header never printed the customization stylesheet, so every saved setting was silently ignored. The calls are now in place — and covered by a behavior test that catches any theme dropping them again.
- The customizer spoke Turkish to English admins in two themes: Personal and Trends had their panel labels written in Turkish inside the theme definition, and the translation dictionary only worked in one direction. All their labels are now bilingual at the source, help texts pass through localization too, a reverse mapping catches any legacy Turkish label, and a new two-language scan across all fourteen themes runs with the test suite — zero leakage, permanently guarded.

---

## [2.45.3] - 2026-07-21  ·  _Patch_
**AdSense Readiness: Stored Scans Auto-Refresh After a Plugin Update**

### Fixed
- After updating the plugin, the dashboard could keep showing the previous version's stored scan — old wording, and no "Show posts" modal button, because that list simply doesn't exist in the old result. The panel now compares the stored scan's plugin version on load and silently re-runs the audit when it's stale, so a new feature never appears to be "missing" just because the visible result predates it. The scan is measurement-only and changes nothing on the site.

---

## [2.45.2] - 2026-07-21  ·  _Patch_
**AdSense Readiness: Sticky Insight Panel, Full-Width Header, and a Post-List Modal**

### Added
- Checks that carry a post list — thin content first — now open a modal: every affected post is listed by title with its word count, and clicking a row opens that post's edit screen in a new tab. No more hunting post IDs from a summary sentence; the list is capped at 200 rows with an honest "first N of M shown" note beyond that.

### Improved
- The empty right side of the AdSense Readiness dashboard is now a sticky insight panel that follows you as you scroll. It carries the full "maturity — honest note" (why green checks alone don't guarantee approval, with your site's first-publish date and last-30-days output), an application-process card with the key numbers (2–14 day review, ~1 week wait after a rejection), and an application-day checklist: single-source AdSense snippet, automatic ads.txt verification, Search Console, and keep-publishing-during-review.
- The header now spans the full layout: the intro paragraph is no longer truncated into a narrow column, and the Re-scan button sits at the far right of the title row.

---

## [2.45.1] - 2026-07-21  ·  _Patch_
**AdSense Readiness: 5 New Checks, a Legal-Page False Negative Fixed, and a Polished Dashboard**

### Added
- Five new checks in the AdSense Readiness audit. SSL certificate: a real TLS handshake verifies the chain and reports the issuer and days until expiry (expiring within 14 days warns, expired fails). Domain: the site must live on a real domain — an IP address or a bare host fails, and IDN (unicode) domains get a punycode heads-up. Google bot access: the homepage is actually requested with Googlebot and Mediapartners-Google user agents to prove the server doesn't block the crawlers AdSense review depends on (honestly labeled as an in-server test — a CDN/WAF in front should also be verified externally). noindex is now its own heavyweight check covering both the homepage meta tag and the SEO setting. Meta description: presence and length of the homepage description (target 120–160 characters).

### Improved
- The dashboard got a design pass: the five category cards now sit in a single equal-width row with ellipsized titles (no more ragged two-line wrapping), and the previously empty right side of the score hero hosts a compact "maturity — honest note" summary with a link to the full text. Status filters became a proper segmented control, fix buttons are now solid primary actions, cards gained consistent depth and hover states, and the score ring color follows the overall verdict instead of the raw number — no more green ring next to "fix the gaps".

### Fixed
- Legal pages were reported missing on sites that serve them through the built-in route templates instead of database pages. jekcms renders complete, AdSense-compliant legal texts at /privacy-policy, /cookie-policy and friends even when no page row exists — the audit now recognizes both paths (plus every slug alias, Turkish and English), and the About/Contact checks follow the same logic: a database page, a theme template or the contact-form plugin all count; only sites left with the bare built-in fallback get a warning.
- Clicking a category card scrolled the section heading under the fixed admin header, landing mid-section. Anchor targets now reserve headroom, so every jump lands with the section title fully visible.

---

## [2.45.0] - 2026-07-21  ·  _Minor_
**New Plugin: AdSense Readiness — a Full Site Audit Through a Reviewer's Eyes**

### Added
- AdSense Readiness plugin: one click scans your site the way an AdSense reviewer would — about 30 real measurements across five areas. Content: published post count against the 25+ target, average post length, thin posts under 300 words listed one by one, category structure (no empty or 3-post-starved categories), duplicate titles, publishing freshness, leftover "lorem ipsum" and still-installed sample content. Legal & trust: all four legal pages (privacy, cookie, terms, disclaimer — the built-in generator creates them in one click if missing), a real About page, a reachable contact channel and the cookie-consent banner. Authors: every active author checked for a real bio in the 3–5 sentence sweet spot (overlong "epic" bios are flagged too), job title, photo, and posts piled onto a single admin account. Technical: HTTPS, site name/tagline/logo, live homepage fetch (indexability, schema, og:site_name, single H1), sitemap.xml, robots.txt access for Googlebot and Mediapartners-Google, 404 behavior and Search Console verification. AdSense: snippet detection with an explicit double-loader warning, and ads.txt validation against your pub-id.
- Every finding shows the measured value — "18 posts (target: at least 25)", not a vague tip — and ships with a direct fix link into the right admin screen: legal page generator, user profiles, category manager, settings. A weighted 0–100 readiness score with an animated gauge, per-category progress bars and status filters (missing / warnings / passed) make the gap list actionable at a glance.
- The report is honest by design: an unscored "maturity" panel states clearly that technical hygiene is necessary but not sufficient — real traffic, site age and perceived content value drive the final decision — and documents the typical 2–14 day review window and the wait-before-reapplying rule. The plugin never promises approval; it removes every reason to be rejected on the measurable side.

---

## [2.44.0] - 2026-07-21  ·  _Minor_
**Person Publisher Support, an SEO Signal Test Matrix for All Themes, and Single-H1 / Language Fixes**

### Added
- Publisher type setting: a personal site can now publish its structured-data publisher as a Person instead of an Organization. Pick "Person" under Settings → SEO and the WebSite node, article publisher references and the about-page reference all switch to a single Person identity — with the contact e-mail expressed the way a Person node expects it. Business sites are untouched: the default remains Organization, and nothing changes unless you opt in.
- An SEO signal regression matrix now guards every release. It activates all fourteen themes in sequence on a live test install and asserts, for each one: exactly one WebSite JSON-LD node; the site name — Turkish characters included — reproduced identically in WebSite.name, og:site_name and the page title; no auto-generated alternateName; the correct publisher type (both Organization and Person modes are exercised); exactly one visible H1; the right html lang; canonical equal to og:url; valid JSON-LD; and no character corruption. The harness ships in the repository and runs as part of the release gate.

### Improved
- One positioning sentence, everywhere: jekcms is a self-hosted blog CMS with built-in SEO and image optimization, running on standard PHP + MySQL hosting. The vague "Next-Gen Smart CMS" phrasing is gone from the homepage, metadata, structured data and the admin login — and so are claims we can't prove: "24/7 support" now reads as support actually works (e-mail, response within 24–48 business hours), "Enterprise Security" now names the real controls (2FA, CSRF protection, rate limiting), and the theme count says exactly 14. The n8n integration is described in one place, as what it is: content arrives as drafts and publishes only after your editorial approval. A security.txt contact file is now published as well.

### Fixed
- The minimalist theme's homepage rendered two H1 headings — the brand in the header and the featured post title. The featured post title is now an H2, so every page has exactly one visible H1 and the brand heading keeps carrying the site-name signal to Google.
- Seven themes read the site language through a helper that falls back to Turkish, while the other themes fell back to English — on a fresh install where no language row existed yet, the same site could declare html lang="tr" on one theme and lang="en" on another. All fourteen themes now read the same source, which follows the language chosen during installation.
- The crypto theme's error and maintenance pages hardcoded lang="tr" regardless of the site's language; they now follow the site language setting.
- The "Powered by jekcms" footer credit across all themes now carries rel="nofollow". It is a technology credit for readers, not an SEO signal — sitewide template links from one network shouldn't pass link authority, and search engines discount them anyway.

---

## [2.43.4] - 2026-07-21  ·  _Patch_
**Theme Switching Verified End-to-End — About and Contact Now Work on Every Theme**

### Improved
- Theme switching itself was exercised the way a real user would do it: all fourteen themes were activated in sequence on a live test install — each activation running the theme's own migration hook — and after every switch, eight real pages (home, a post, a category, search, about, contact, a static page, and the 404 page) were fetched over HTTP and checked for errors. 112 page loads, zero failures. Per-theme customizations were also verified to survive a switch away and back, without leaking into the other theme's settings. The test harness ships in the repository so this can be re-run before any release.

### Fixed
- Switching themes no longer breaks the About and Contact pages. Eleven themes ship without their own about template (and two without a contact template); on a site that hadn't created those pages yet, switching from a theme that had the template to one that didn't turned working footer links into 404s. The router now falls back to an honest built-in default rendered through the theme's page template — with the contact form auto-injected — and the moment you create a real "about" or "contact" page in the admin, your content takes over.
- Three themes (crypto, minimalist, health) ignored page content handed to them by the router and re-queried the database by slug, which broke the new built-in defaults and any router-provided page. They now use the provided content first, exactly like the other eleven themes.

---

## [2.43.3] - 2026-07-21  ·  _Patch_
**AI Keys Encrypted at Rest Everywhere, and the Main CI Pipeline Now Runs Every Quality Gate**

### Improved
- The main GitHub deployment pipeline now runs the same quality gates as a local release: the fresh-install acceptance test, the hardening regression suite, the schema linter and the i18n linter all execute on every push to main — a regression in any of them stops the deployment before it reaches production. The hardening suite itself grew to 37 checks, including real cryptographic behavior tests for the new key vault (plaintext never lands in the stored JSON, legacy entries migrate, masked hints never leak the full value).
- The fresh-install schema now includes the multi-key AI columns, which previously existed only in a secondary schema file — saving multiple Gemini keys on a brand-new install could fail with a database error.

### Security
- AI provider API keys are now stored encrypted everywhere. The multi-key Gemini list and the flat provider key fields (OpenAI, Groq, Cohere, Claude) are encrypted with authenticated AES-256-GCM before they touch the database, the settings form shows only a masked hint and never echoes a stored key, and every consumer — content tools, cron, connection tests — reads through the same decryption gate. A one-shot migration converts existing records automatically on the next cron pass, verified end-to-end on a real database.
- Signing out is a pure POST form now. The interim design carried the CSRF token in a GET link, which could land in access logs, browser history and prefetchers; the admin logout links are now styled POST forms, so the token never appears in a URL.
- A short mixed-version window could crash AI key reads: the migration check called a brand-new method without guarding against the older class still being loaded mid-deploy. All migration detection now runs behind a guarded helper and inside its own try block, with failures logged instead of swallowed.

---

## [2.43.2] - 2026-07-21  ·  _Patch_
**Review Follow-up: Crypto Edge Case, Transparent Secret Migration, CSRF-Protected Logout, and Permanent Hardening Tests**

### Fixed
- Decrypting an encrypted empty value works again. The new authenticated-encryption format rejected the shortest valid packet (a zero-byte ciphertext), breaking the encrypt/decrypt round-trip contract for empty strings.
- The schema linter's success message now reports the number of currently open findings instead of the raw baseline line count, which had kept showing already-resolved entries.

### Security
- Stored secrets now migrate to authenticated encryption on their own. When an AI provider key or a Google OAuth token stored in the legacy format is read successfully, it is transparently re-saved in the new integrity-checked format — long-lived secrets no longer wait for the user to re-enter them.
- Signing out is now CSRF-protected. A plain GET to the logout address could previously be triggered by an external page to force-end an admin session; logout now requires a valid token (admin links carry it — still one click) and shows a small confirmation page otherwise.
- The audit fixes are locked in by a permanent hardening test suite that runs on every release: encryption round-trips including the empty-value and tampering cases, route targets that must exist, fail-closed API role checks, the cron result contract, and error-message masking. A regression in any of these now blocks the release.

---

## [2.43.1] - 2026-07-21  ·  _Patch_
**Audit Fixes: Reliable Cron Output, Working /login Route, and Authenticated Encryption**

### Fixed
- The cron runner no longer crashes when a run is already in progress. The lock branch returned a bare error string while the CLI reporter expected structured results, producing a fatal error on every overlapping run — and the shutdown path then tried to send an HTTP status from the command line, masking the original error. The result contract is now uniform, the reporter is defensive, and CLI errors go to stderr with a proper exit code.
- The public /login and /logout routes work again. They pointed at an auth/ directory that never shipped, so every hit returned a server error; they now redirect to the admin login and logout pages.
- The optional AI bulk worker no longer logs database errors on installations without its table: the web-side tick now checks for the table first, exactly like the cron side always did.
- Two more fresh-install schema gaps closed by the new acceptance test: scheduled task results and the social queue's completion timestamp now exist in the shipped schema, and failed tasks write to the correct error column.

### Security
- Stored secrets are now protected with authenticated encryption. Encrypted values (AI provider keys, Google OAuth tokens) are written as versioned AES-256-GCM with integrity checking; existing records keep decrypting and migrate transparently as they are re-saved.
- The API's write authorization is now fail-closed: a user record with an empty or unknown role gets no write capabilities.
- API error responses no longer echo raw exception details. Clients receive a fixed message with a correlation ID; the full detail goes only to the server log.

---

## [2.43.0] - 2026-07-20  ·  _Minor_
**Offline Documentation in Every Package, and Fresh-Install Schema Repairs**

### Added
- The installation package now ships the full documentation offline. All 37 guides are bundled as self-contained HTML in both English and Turkish under documentation/ — no external assets, readable without an internet connection. The admin panel's "How to use this" links open the local copy first and only fall back to jekcms.com when the folder is absent, so in-product help keeps working even if the vendor site is unreachable.
- One-click sample content. On an empty site, the Posts screen now offers to load six short, well-formatted starter articles across three categories — with generated cover images — so a fresh install shows what your theme really looks like. The samples double as a formatting guide (headings, lists, quotes, images) and are removed with a single click, covers and categories included, without touching anything you created yourself.
- Fresh-install acceptance testing joined the release pipeline. Every release now installs the shipped database schema into a clean MySQL and runs the product's critical write paths against it in strict mode — the class of bug where code writes a column the packaged schema doesn't know is caught before a package ever reaches a customer. The internationalization check runs in the same pipeline, so untranslated admin text can no longer slip into a release unnoticed.

### Fixed
- Creating an API key on a fresh install works again. The admin screen stores API keys as a SHA-256 hash, but the shipped schema still described the old plaintext-token layout, so the very first "Create key" click on a new install failed with a database error. The schema now matches the code, and existing installations are repaired automatically on their next cron pass.
- Automation logging and the social share queue no longer lose data on strict-mode databases. The automation log rejected entries whose source was "system" or "admin" (values the code actually writes), and the social queue had nowhere to store the published-at time and the platform's post ID after a successful share. Both tables are aligned with the code and heal themselves on existing installations.
- The pricing page FAQ no longer claims online payments are "coming soon" while the checkout buttons on the same page are live — it now explains card payment, instant delivery, and the invoice/bank-transfer option honestly, in both languages.

---

## [2.42.0] - 2026-07-14  ·  _Minor_
**Auto-Activated Plugins Now Create Their Tables, a Rate-Limited License Endpoint, and Gates That Are Honestly Green**

### Fixed
- Auto-activated plugins now install their database tables on a fresh install. A plugin marked AutoActivate was switched on automatically, but its activate.php — which creates the tables — only ever ran when you toggled the plugin by hand in the admin. On a brand-new install Newsletter therefore appeared active while newsletter_campaigns, email_templates, newsletter_queue, newsletter_clicks and email_logs were never created, and the Campaigns screen died with a fatal error. Activation now runs once per plugin version, is idempotent, adds no query on the hot path, and repairs installations that are already in the broken state on their next request. If one plugin fails to install its schema, the site stays up and the attempt is retried.
- Author social links, the reader-facing editorial box and the similarity gate carry the fixes shipped since 2.41.0: social profiles were invisible on author archives in seven themes, and the similarity gate now uses roughly a quarter of the memory it used to on large sites (measured: 64MB → 16MB on a 2,000-post blog).

### Security
- License activation is rate limited (20 attempts per IP per hour), matching the limiter the heartbeat already had.

---

## [2.41.0] - 2026-07-13  ·  _Minor_
**Editorial Transparency Readers Can See, Paraphrase-Aware Similarity, and a Test That Actually Runs**

### Added
- "How this content was made" box: the editorial fields you fill in (AI usage disclosure, original-contribution note, sources, YMYL flag) are now shown to readers under the post — in every theme, with no template edits. Sources also continue to be emitted as schema.org citations. The box appears only when you have filled the fields in, and it can be turned off in Settings.
- Editorial fields are now part of the REST API: every post response carries an "editorial" object (ai_disclosure, original_notes, sources, ymyl), so external editors, archives and n8n flows can read and act on them.
- Editorial checklist in the post editor: missing sources, missing original-contribution note or an undisclosed AI usage are listed as informational reminders. YMYL-flagged posts without sources or without a human approval are called out. Nothing here ever blocks publishing.

### Improved
- Content-similarity protection now catches rewrites, not just copies. Three measures work together: verbatim overlap (5-gram), partial copy (containment — a copied section buried inside an otherwise original post), and term overlap (TF-IDF cosine — the same article rewritten with different sentences). Each has its own threshold in Settings. The comparison window grew from the last 120 posts to a configurable 500, and each post is compared over its first 12,000 characters (chunked, so a wider scope does not raise memory use).
- Honest naming: this is lexical near-duplicate and term-overlap protection, not embedding-based semantic analysis. It catches verbatim copies, near-duplicates, reordered sentences, embedded partial copies and same-term rewrites; it does not claim to catch two posts that target the same search intent with entirely different wording. The acceptance test fails the build if the product ever over-claims this.

### Fixed
- The publishing-policy acceptance test now proves behaviour instead of matching text. It builds an isolated MySQL fixture and measures the real decisions on real SQL: publish/block outcomes, gate_state persistence, the absence of fabricated approvals, approval invalidation on edit, seven content-similarity scenarios (verbatim, near-duplicate, reordered, partial, paraphrase, false-positive control, and window depth) and the editorial-field consumers. It runs on every push in CI. Previously it could report success while a fatal error had occurred; a fatal now fails the build.

---

## [2.40.0] - 2026-07-12  ·  _Minor_
**Editorial Transparency, Near-Duplicate Protection, and a Tighter CSP**

### Added
- Editorial Details panel in the post editor: declare the sources a post is based on (one URL per line — they are emitted as schema.org citations on the published page), record an original-contribution note, disclose AI usage (none / AI-assisted / AI-generated, human-reviewed), and flag YMYL content. Everything is optional, stored per post, and requires no theme changes.
- Content-similarity protection in the quality gate: in addition to the existing title checks, the gate now measures body-level overlap between a new post and the last 120 published posts. Content that overlaps above the threshold (default 80%, configurable in Settings) is blocked before publishing; noticeably-similar content produces a cannibalization warning. This closes the near-duplicate class that title checks alone cannot see.
- The publishing-policy acceptance test now runs automatically: it is wired into both the local release gate and the CI pipeline, so no future change can silently reopen a publish path around the quality gate.

### Security
- Content-Security-Policy hardened: 'unsafe-eval' removed from script-src after a full inventory (no first-party or third-party script in use requires eval). 'unsafe-inline' remains by documented decision — themes use inline scripts and the Custom Header Scripts feature outputs user-pasted snippets that cannot carry nonces.

---

## [2.39.0] - 2026-07-12  ·  _Minor_
**Publishing Policy: One Gate, Your Choice, an Honest Record**

### Added
- A single publishing policy now governs every path that can put a post live — the AI draft screen, the content queue, scheduled publishing, the REST API and n8n webhooks. Automatic publishing remains entirely your choice: if you turn it on, posts go live without review, exactly as you asked. What changed is that no path can quietly skip the quality gate while it is switched on, and every publication is recorded honestly.
- Publication audit trail: each post now records how it reached the reader — its source (manual, AI, JSON, n8n, API, queue) and its publication mode (draft, scheduled, automatic, reviewed). When a human editor approves a post, jekcms stores who approved it, when, and a fingerprint of the exact content they approved. Automatic publishing never fabricates a human approval — it is recorded as automatic, plainly.
- Approval invalidation: if an approved post is edited afterwards, the stored fingerprint no longer matches and the old approval is treated as void.
- Risk notices in the admin: the AI Draft, JSON Import and content automation screens now carry a permanent, non-blocking note explaining that generated or imported content can be inaccurate or low-value, that publishing without review can affect search visibility, and that the choice of draft, schedule or direct publish is yours. Turning auto-publish on, or turning the quality gate off, shows a visible warning next to the setting — never a modal, never a forced checkbox.

### Fixed
- The AI draft screen wrote posts straight to the database and never consulted the quality gate, even when the gate was switched on. It now goes through the same publishing policy as every other path; if the gate holds a post back, it is saved as a draft and the reasons are shown.

---

## [2.38.0] - 2026-07-12  ·  _Minor_
**Honest Freshness Signals, a Content Quality Gate for Automation, and Full-Document Revision Restore**

### Added
- Editorial date model: posts now track "last meaningful content change" separately from internal system touches. Schema.org dateModified, article:modified_time and sitemap lastmod are generated from the new signal — so bulk SEO passes, counters and cache refreshes no longer make hundreds of posts look "updated today" to search engines. When editing a published post you can also override the automatic detection: mark a save as a content update or a technical fix.
- Content Quality Gate: every automated publish path — content queue approval and publish (single and bulk), scheduled publishing, REST API and n8n webhooks — runs the same deterministic quality checks before anything goes live: minimum content length, duplicate and near-duplicate titles, and broken local image references block publication with visible reasons; missing featured image, internal links or headings raise warnings. The gate re-runs at the moment of publishing (so post-approval edits are re-checked), and fails closed: if the check itself errors, nothing is published. Thresholds are configurable in Settings.
- Full-document revisions: each revision now stores a complete snapshot — SEO meta, categories, tags, featured image, author, status and dates — and restoring one brings back the content, SEO, taxonomy, featured image and author. Publication status and dates are deliberately not restored, so restoring never unpublishes a live post or rewrites its history. The state before a restore is saved as its own revision, and the revision limit is now configurable (default raised from 10 to 50).
- Author Person schema now includes verifiable sameAs links built from the author's social profiles and website, alongside the job title, bio and photo added in the previous release.

### Improved
- The REST API now returns explicit ISO 8601 editorial dates (content_modified_at, reviewed_at) on post endpoints and accepts content_modified_at on writes, so migrations and rewrites can preserve original dates.

### Fixed
- Schema dateModified and sitemap lastmod could report a date earlier than the publish date on scheduled posts; both are now clamped so a modification date never precedes publication.
- The sample admin account seeded by a manual database import now ships with an unusable password hash, and the installer sets real credentials as before.

---

## [2.37.0] - 2026-07-10  ·  _Minor_
**Legal Pages Repaired and Expanded, Author Archives Fixed, Tag Indexing Made Consistent**

### Improved
- The default Cookie Policy was rewritten to be genuinely comprehensive in both languages: cookie categories with purposes, legal bases and durations in a table, first/third-party and session/persistent distinctions, named third parties with opt-out links, consent management and withdrawal, browser instructions, Do Not Track / Global Privacy Control, and a legal-basis section (KVKK on Turkish sites, GDPR/ePrivacy on English ones).

### Fixed
- The built-in legal page templates shipped with corrupted text in all 13 themes — Turkish characters and arrow symbols rendered as garbage ("â†’", "Çerez") on fresh installs that had not saved their own legal pages. The templates were re-encoded and every character now renders correctly in both languages.
- Opening an author archive on the Personal theme returned a server error: a routing variable leaked into the template and shadowed the real author record. Author pages now render on every theme, and a non-existent author correctly returns 404.
- Tag archives could be indexed by search engines even while tag archives were disabled in SEO settings — the sitemap respected the setting but the page-level robots meta did not. With tag archives off (the default), every tag page is now noindex.
- On the Finance theme, the author box at the end of a post showed the author's name as plain text; it now links to the author's archive page, and the Pets theme's archive pages now emit a proper page title and meta description instead of just the site name.

---

## [2.36.0] - 2026-07-10  ·  _Minor_
**Personal Theme: Full-Width Brand Logo with Automatic Light/Dark Switching**

### Added
- The Personal theme now supports a full-width brand logo in the header: upload your logo (and an optional dark variant) under Settings → Branding and it replaces the icon + site-name pair, switching automatically with the visitor's light/dark preference. The site name stays in the markup as a visually-hidden heading, so the Google site-name signal is preserved. Nothing changes for sites without an uploaded logo.

---

## [2.35.0] - 2026-07-10  ·  _Minor_
**Stories, the Instagram Way: One "Latest Posts" Bubble That Plays Your Recent Content**

### Improved
- Automatic post stories were redesigned around how Instagram actually works: instead of one bubble per post crowding the strip, there is now a SINGLE "Latest Posts" bubble — tap it and the posts from your chosen window (3, 7, 15, 30 days… up to 90) play as slides, newest first, each with its featured image, title and a "Read Post" button. The bubble is fully virtual: nothing is written to the stories database, new posts appear in it the moment they are published, old ones drop off as they leave the window, and the ring lights up again whenever a new post arrives.
- The bubble's name follows the site language ("Son İçerikler" / "Latest Posts") and can be customized in settings. Bubbles you created by hand are untouched and keep their place next to it; the per-post bubbles generated by the previous version are cleaned up automatically.

### Fixed
- Opening the Stories admin page by its direct URL (without a module parameter) returned a server error — a strict-mode array access crashed before the page could render. The page now opens correctly from anywhere.

---

## [2.34.0] - 2026-07-10  ·  _Minor_
**Stories Strip Becomes a True Latest-Posts Showcase**

### Improved
- With auto-stories enabled, the strip now carries EVERY post published within the story lifetime window (7 days by default) — not just posts published after the feature was switched on. Older posts are backfilled automatically every hour, each story retires based on its post's publish date, and the newest post always sits first in the strip, Instagram-style.
- The strip now announces itself: when auto-stories are on and no custom heading is set, a heading in the site's language appears above the circles — "Son İçerikler" on Turkish sites, "Latest Posts" on English ones. Set your own heading to override it, or enter "-" to hide it entirely.

---

## [2.33.0] - 2026-07-10  ·  _Minor_
**Image Captions Done Right: Visible Captions Are Now a First-Class Editor Feature**

### Added
- New "Caption" field in the image details dialog: add a visible caption under any image, shown identically on every theme via self-contained styling. The dialog now clearly separates the two concepts — alt text is invisible and for search engines and screen readers; the caption is the text readers actually see. Captions render live in the editor and are editable with one click.

### Fixed
- Editing a post that contained figure-wrapped images could leak the old caption markup as a visible plain paragraph under the image — the editor did not understand the figure/figcaption structure, so saving unwrapped it and turned caption text into body text. The editor now parses figures natively: real captions survive editing round-trips intact, and legacy captions that merely duplicated the alt text are dropped automatically instead of becoming visible.
- Opening the image details dialog could scroll the page behind it, so you lost sight of which image you were editing. The background now stays exactly where it was while the dialog is open and after saving.

---

## [2.32.0] - 2026-07-10  ·  _Minor_
**Click, Resize, Align: Full Image Editing Inside the Editor**

### Added
- Images in the post editor are now fully editable in place, the way WordPress users expect. Click an image and a floating toolbar appears right on it: size presets (Small 300px / Medium 600px / Full width), left-center-right alignment, a details button and remove — plus four corner handles you can drag to resize freely, with a live pixel readout while you drag. Aspect ratio is always preserved.
- New image details dialog (toolbar pencil or double-click the image): see and edit the alt text, title tooltip, exact pixel width and the image URL in one place, with a live preview. Alt text finally gets a proper editing home after insertion — good for accessibility and image SEO.
- Sizing and alignment are written into the content as self-contained inline styles, so they render identically on every theme — no theme CSS support required, and images never overflow on mobile (max-width is built in).

### Fixed
- The alt text label in the image insert dialog was hardcoded in Turkish and appeared untranslated on English admin panels.

---

## [2.31.2] - 2026-07-10  ·  _Patch_
**Posts List: One-Click SEO Score Refresh, Editor and List Finally Agree**

### Added
- New "Recalculate SEO Scores" button on the posts list: refreshes every post's stored SEO score with the current scoring engine — in batches of 100 with live progress, so a 1,000-post site takes seconds instead of hitting a timeout. Useful after upgrading, since scores saved by older versions used the old scoring rules.

### Fixed
- The score in the editor and the score in the posts list could differ: the editor's live analyzer inspects the actual page structure (headings, tables, snippet blocks) while the save-time engine cannot, so recomputing on save produced a different number. The editor now passes its own score along when you save — the list shows exactly what the editor dial showed.
- The "Analyze All" AI button appeared on every installation, including ones with no AI provider configured, where clicking it could only show a setup notice. The button now appears only when AI is actually configured.

---

## [2.31.1] - 2026-07-10  ·  _Patch_
**SEO Score You Can Trust: Fixed Budgets, No More Reward for Leaving Fields Empty**

### Improved
- Each check group in the SEO widget now shows its point contribution (e.g. "20/25p" next to Keyword) so you can see exactly where a score comes from and which section is worth fixing first.

### Fixed
- A post with NO focus keyword could score 80-90, and the score DROPPED the moment you entered one — the old ratio model removed the keyword checks from the denominator when the field was empty, so withholding information was mathematically rewarded. Scoring now uses fixed category budgets (keyword 25, content 20, structure 15, basics 15, readability 10, visuals 10, schema 5): an empty keyword field burns its whole 25-point budget, and filling in information can only raise your score, never lower it. The same flaw existed in the score saved on every post update (an even stronger version: keyword-less posts were graded out of 50 and could reach 100) — post saves now use the same fixed-budget engine as the SEO Optimizer page, so all scores finally speak the same language.
- Turkish keywords containing İ/I (e.g. "İçerik Pazarlaması") silently failed every match — title, content and density checks all reported "keyword not found" because of a Unicode case-folding quirk. Keyword matching is now Turkish-aware across the editor widget, the save-time score and the SEO Optimizer. Density also counts whole words only (a short keyword inside longer words no longer inflates the percentage) and word counting is UTF-8 correct.
- The title length check said "good" up to 70 characters while the SERP preview's pixel meter showed the same title being cut at ~580px — the two now agree (60-character budget), and a keyword missing from the title is no longer punished twice.

---

## [2.31.0] - 2026-07-10  ·  _Minor_
**SEO Assistant: Content Structure Checks, Pixel-Accurate SERP Preview, Wider AI Analysis**

### Added
- New "Content Structure" check group in the editor's SEO assistant — seven checks that mirror how editors actually review a draft: duplicate H1 in the body (your title is already the page H1), skipped heading levels (H2→H4), a too-thin intro before the first heading, a missing conclusion/summary section on long posts, table and list usage, and a featured-snippet readiness check that looks for a question heading followed by a concise 40–60 word answer.
- The SERP preview now measures your title and description in pixels, the way Google actually truncates them (~580px for titles, ~990px for descriptions on desktop). Character counts stay, pixel widths appear next to them and turn red when the limit is exceeded — no more titles that pass the character check but still get cut in results.
- AI deep analysis covers four new dimensions: overall content quality (informativeness, originality, freshness), Google Helpful Content fit, AI-search readiness (would an AI Overview cite this page?), and AdSense policy suitability — including thin-content and clickbait-mismatch warnings before you publish.

### Fixed
- The SERP preview showed a broken icon instead of your favicon: it pointed at a file path that only exists on jekcms.com, not on customer installations. The preview now resolves the site's real favicon through the same priority chain the front end uses (uploaded favicon, site-root favicon files, generated icon), with a letter-badge fallback so the slot is never empty.

---

## [2.30.0] - 2026-07-09  ·  _Minor_
**Google Console: PageSpeed Tab, Fresh Search Data, Stability Fixes**

### Added
- New PageSpeed tab: measure any page of your site with Google PageSpeed Insights (Lighthouse) right from the panel — mobile and desktop scores for Performance, Accessibility, Best Practices and SEO, lab metrics (FCP, LCP, TBT, CLS, Speed Index) and real-user Core Web Vitals (CrUX) when Google has field data for your site. Works without a Google connection; results are cached for 24 hours. An optional API key setting raises the measurement quota.

### Fixed
- Search Console reports were consistently thinner than the GSC interface: the API omits the last ~2 days by default ("final" data), so recent queries and clicks simply never appeared — the exact "my search terms don't show up" complaint. All Search Console reports now request fresh data, matching what the GSC UI shows.
- The Top Queries and Top Pages cards swallowed API errors and displayed a misleading "No data" — a quota or permission problem now shows its actual, actionable message on the card itself (same for the Analytics tables).
- When Google was unreachable, every page load fired the full set of live API calls with 20-second timeouts each, freezing the panel; failed responses are now briefly cached so the page stays responsive, and the Refresh button retries immediately. The response cache table also cleans up its expired rows, which previously accumulated forever.

---

## [2.29.1] - 2026-07-09  ·  _Patch_
**ZeroTrack Analytics: Data Collection Restored on Production Sites**

### Fixed
- ZeroTrack silently stopped recording visits on production installations: the standalone beacon endpoint read database credentials only from .env, but production installs keep the real credentials in .env-production (the installer writes them there). The endpoint could never connect, answered every beacon with a polite 204, and the dashboard showed zeros while the site had traffic. The endpoint now uses the same environment-file priority as the rest of the CMS (.env-production first), and a failed database connection is written to the error log instead of disappearing without a trace.
- Page views could be counted twice: both the plugin hook and the core footer injected the tracker script, and the plugin side ignored the once-per-page guard. The guard is now honored on both paths — one tracker, one beacon, one count per view.

---

## [2.29.0] - 2026-07-09  ·  _Minor_
**SEO Analyzer: Turkish-Correct Matching, Keyword Cannibalization Warning, New Checks**

### Added
- Keyword cannibalization warning: as you type a focus keyword, the analyzer checks whether another post already targets it and names that post — the classic premium-plugin feature, built in.
- Three new checks: a warning when the meta description merely copies the title, a nudge when no image alt text contains the focus keyword, and a heads-up for slugs containing Turkish/special characters.

### Fixed
- Turkish focus keywords were silently failing: JavaScript lowercases dotted İ into a combining character, so a title like "İçerik Rehberi" never matched the focus keyword "içerik" — the analyzer wrongly reported the keyword missing from the title, description, headings, and first paragraph. A Turkish-aware folder now backs every comparison, and the slug check ascii-folds the keyword ("beslenme önerileri" correctly matches "beslenme-onerileri").
- Keyword density counted substrings ("spor" also counted "sporcu"); it now counts whole words. Internal/external link detection resolves the real hostname instead of matching the site name anywhere in the URL. The analyzer also stopped re-rendering every 2.5 seconds, which used to force categories you had collapsed back open.
- On installations without the AI settings table, the editor died mid-page with "Server Error" while rendering the AI tab; the check is now failure-safe and the editor always loads.
- The social preview card showed a broken image for uploads-relative featured paths; description length limits were aligned to 160 everywhere.

---

## [2.28.3] - 2026-07-09  ·  _Patch_
**Health Theme Speaks Your Site Language on the Frontend**

### Fixed
- On Turkish sites the Health theme still printed dozens of hardcoded English strings — section titles (Most Popular, Trending Topics, Latest Articles, Recommended), the entire footer navigation (About, Categories, For You, Editorial, Connect and every link inside them), the author card (About Author, View All Articles), the comment form (Leave a comment, Name, Email, Post comment), search, 404, tags, and the fallback header menu (Home, About). All of them now follow the site language setting: Turkish sites read fully Turkish, English sites are unchanged.

---

## [2.28.2] - 2026-07-09  ·  _Patch_
**Health and Travel Headers No Longer Leak Broken Markup**

### Fixed
- On the Health and Travel homepages the brand link's H1 was printed inside the aria-label attribute, breaking the attribute and leaking a literal « — home"> » text next to the logo (most visible on fresh installs without a logo). The H1 now renders inside the link body where it belongs; the accessibility label and the SEO site-name signal both work as intended.

---

## [2.28.1] - 2026-07-09  ·  _Patch_
**Wizard Polish: Come Back Days Later, Nothing Is Lost**

### Improved
- Take the prompt, close the browser, come back next week with the AI's JSON: the wizard now remembers every choice, greets you with a "Jump to import" shortcut, and the step chips are clickable so you can move to any step directly — no more starting over.
- The Content Studio menu is now one flat list in a clear order (Overview, Content Wizard, AI Content, Automation, Content Queue) — the confusing "Advanced" sub-group is gone — and it stays visible inside the Content Queue and Automation pages too, so sub-pages no longer feel like leaving the studio.
- The Pinterest and external-link option cards were realigned (checkbox beside the title instead of floating above it) and light up when selected.

### Fixed
- The sample JSON no longer carries a fixed example date in scheduled_at — some AIs copied that stale date into every article. Scheduling belongs to the wizard's own final step.
- The old JSON generator form inside the import tab was removed (the wizard replaced it); the tab now cleanly hosts the raw import tools (JSON file, Google Sheets, CSV) with a pointer to the wizard.

---

## [2.28.0] - 2026-07-09  ·  _Minor_
**Content Wizard: Plan, Create, and Schedule in One Guided Flow**

### Added
- The new Content Wizard (Content Studio → Content Wizard) replaces the old maze of JSON wizard, batch planner, and import tab with one step-by-step experience: how many articles → topic and keywords → richness (word count, images, Pinterest, authority links) → who creates it → schedule. Your theme profile is auto-detected, so recipe, travel, and finance themes automatically request their special fields.
- Two creation paths, same quality contract: use your own ChatGPT/Claude/Gemini account for free (copy one prompt, drop the returned JSON back — the wizard imports and validates it), or let jekcms generate everything through your API key, article by article with a live progress bar. Both land in the same review queue.
- The final step schedules the whole batch on a rhythm (daily, every 2-3 days, weekly) with a randomized time window, and explains the image workflow plainly: every article ships with a ready image plan (per-image generation prompts); generate covers automatically via the AI Images plugin, or create them anywhere, name them by slug, upload to uploads/temp and press Match Images.

### Improved
- Content Studio's inner menu was decluttered (Posts and New Post moved back to the main sidebar where they belong) and it now stays visible on every studio sub-page, so you never lose your bearings. The n8n automation planner and raw queue live under a clearly labeled "Advanced" section.
- The single-draft AI tool now shares one AI client with the wizard (Gemini, Groq, and OpenAI — OpenAI upgraded to gpt-4o-mini).

---

## [2.27.6] - 2026-07-09  ·  _Patch_
**The Finance Footer Shows Your Logo Instead of Plain Text**

### Fixed
- The Finance theme footer always printed the site name as plain text and never used the logo you uploaded. It now shows the logo, preferring the dark-mode variant because the footer background is dark in both themes. Sites without a logo keep the text heading exactly as before.

---

## [2.27.5] - 2026-07-09  ·  _Patch_
**A Newly Uploaded Logo Now Appears Immediately**

### Fixed
- Replacing your logo from Settings → Branding could leave visitors looking at the old one for a long time. Uploads are served with a one-year "immutable" cache header, so once a browser or CDN had the file at that address it never asked again — and a CDN could keep serving a stale copy even after the file on the server changed. Logo URLs now carry the file's modification time, so a new upload is a new address and every visitor sees it on the next page load.

---

## [2.27.4] - 2026-07-09  ·  _Patch_
**Author Pages Get Photos and an Archive Layout Fix**

### Improved
- Author archive pages now show the author's photo next to their name in both Finance and Pets — the header no longer reads as an anonymous text block.

### Fixed
- Finance archive pages (category, tag, author) stacked the sidebar full-width below the article cards because the layout container had no grid rules; the sidebar is back in its right-hand column. The archive breadcrumb also lost its detached white band, matching single posts.
- Author archive pages claimed every author was a "Financial Analyst" when no credential was set; the fabricated fallback was removed and only real credentials render.
- On the Pets homepage, when the newest post was the only one published, the grid below the featured card rendered as a large blank area; a short "more articles on the way" note now fills it.

---

## [2.27.3] - 2026-07-09  ·  _Patch_
**Finance Theme: Sans Headings, Breadcrumb Fix, Dark-Mode Readability**

### Improved
- The default heading font switched from the serif Fraunces to Inter: every heading across the theme now shares one modern sans family. Sites that picked a custom heading font in the Customizer keep their choice.

### Fixed
- On single posts the breadcrumb sat in a detached band that ended up unreadable behind the colored post header; it now lives inside the header as light, legible text.
- In dark mode, links inside articles and the table of contents used the light-mode teal and nearly disappeared against the dark background; dark mode now switches them to a bright, readable tone without touching buttons or the hero.

---

## [2.27.2] - 2026-07-09  ·  _Patch_
**Finance Theme: Sticky Table of Contents, Author Bio, Tidier Cards**

### Improved
- The "In This Article" table of contents no longer pushes the article down from the top of the content: it moved into the right sidebar, where it stays visible (sticky) while the reader scrolls through long articles.
- Article cards were tidied up: date and reading time sit on one muted line separated from the content, and the author appears as an aligned chip with a round photo instead of a loose letter placeholder. The homepage now also loads author photos for its cards.
- More breathing room between the homepage hero and the "Latest Articles" section.

### Fixed
- The author box under articles rendered without the author's biography because the router does not pass it; the template now loads the bio itself, so the full author card (photo, name, bio) appears.

---

## [2.27.1] - 2026-07-09  ·  _Patch_
**Finance Theme: Design Consistency Pass and Author Byline Fix**

### Fixed
- Every Finance article showed "Staff Writer" as the byline and skipped the author box entirely, even when the post had a real author. The template expected author data in a nested array while the router provides flat fields; the template now reads both, so the correct name, avatar and author box render on every post.
- The Finance theme received a design consistency pass: the serif display font is now reserved for article headlines while all interface labels use the sans family, the color palette was unified around the theme's navy and gold (the off-brand purple button and blue underlines are gone), the newsletter box no longer blends into the hero, the unused gray band between header and hero was removed, the trending numbers and footer fine print are readable, the author avatar aligns with its name, and archive pages say "1 Article" instead of "1.00 Articles".
- Hardcoded newsletter and footer texts that promised "market analysis and investment tips" were replaced with neutral wording that fits any finance site built on the theme.

---

## [2.27.0] - 2026-07-09  ·  _Minor_
**Logo Variants: Dark-Mode and Retina Logos, Uploaded from the Panel**

### Added
- Settings → Branding now accepts three optional logo variants alongside your main logo: a dark-mode logo and 2x (retina) versions of both. When the visitor switches to dark mode the logo swaps instantly — no page reload — and high-density screens automatically receive the sharper file. If you never upload a dark logo, nothing changes: the light logo is used everywhere, exactly as before.
- Themes with permanently dark areas (like the Pets footer) automatically prefer the dark-mode logo there when one is uploaded, so a dark-text logo no longer disappears into a dark background.

### Fixed
- The Finance homepage never listed articles on any installation: the home route loaded the template without passing it data, so the "Latest Articles" section always claimed the site was empty. The template now queries published posts itself, with pagination.
- A sweep of rough edges reported on fresh installs: the tagline no longer duplicates next to the logo in the Finance header, raw emoji icons were removed from category chips and lists in both Finance and Pets, a literal "NULL" tag and a "0.00 views" line no longer render in the Finance sidebar, empty tag boxes hide themselves, the featured-post category badge no longer overlaps the title in Pets, and legal pages regained a readable header in all themes.

---

## [2.26.1] - 2026-07-09  ·  _Patch_
**Theme Honesty: Placeholder Stats Removed, Fresh-Install Language Fixed**

### Fixed
- The Finance theme homepage shipped with hard-coded placeholder claims — invented reader counts, satisfaction percentages and a fake "expert analysts" figure. All of it is gone: the hero now speaks with your site name and tagline, and the stats strip only appears once it has real numbers from your own database to show.
- Fresh installs now seed the site language from the setup wizard. Previously the language row was never written, so every new site quietly fell back to Turkish in the footer and legal pages — even when everything else was in English.
- Finance and Pets headers printed the logo and the site name side by side, doubling the brand. With a logo set, the text is now kept for screen readers only; without a logo, the text brand still shows.
- The Pets homepage listed every category — including empty ones and the seeded "Uncategorized" — each with a "0" badge. Category lists now show only categories that actually have published posts, without count badges.

---

## [2.26.0] - 2026-07-09  ·  _Minor_
**Zero-Setup Scheduling: Posts Publish On Time Without a Server Cron**

### Added
- Scheduled posts and the content queue no longer depend on a server cron job. A built-in scheduler keeps a "next job due" timestamp and, when that moment arrives, runs the publishing engine right after a page response has been delivered to the visitor — so a post scheduled for 14:37 goes live on the first visit at or after 14:37, and the visitor never waits for it. On hosts that cannot detach the response, the work is handed to a lightweight background request instead.
- A real cron job is still first-class: when one is configured it takes over completely and the visitor-triggered scheduler switches itself off, adding zero overhead. It can also be disabled explicitly with the JEK_DISABLE_PSEUDO_CRON constant.

### Improved
- The old fallback rolled a dice on every request (a 1% chance), which meant late posts on quiet sites and wasted database work on busy ones. The new scheduler is deterministic: on a normal request it reads one or two tiny files and does nothing else — no database queries, no guesswork.

---

## [2.25.0] - 2026-07-09  ·  _Minor_
**First-Publish Journey: Redesigned Welcome Guide**

### Improved
- The dashboard welcome guide was rebuilt as a slim one-line journey rail: a circular progress ring, five connected step dots and a single call-to-action for whatever comes next. It takes a fraction of the space of the old checklist and reads at a glance.
- The five steps now follow the real order of setting up a site: site identity (name and tagline), logo, first category, first published post, and securing your admin password. Every step updates live as you complete it anywhere in the admin, and each links straight to the right screen.
- "Pick a theme" and "connect an AI provider" are no longer setup steps — keeping the theme you chose during installation is a perfectly good choice, and AI is optional.

---

## [2.24.2] - 2026-07-09  ·  _Patch_
**Featured Image Path Fix in Theme Templates**

### Fixed
- A handful of theme templates (Recipes cards and pages, Starter posts, Pets error page) printed the featured image path exactly as stored in the database. Relative paths then resolved against the site root and returned 404, so those images never showed. All of these now resolve through the central image helper, which builds the correct uploads URL and serves the best available format.

---

## [2.24.1] - 2026-07-09  ·  _Patch_
**Logo Aspect Ratio & Accessibility Fixes**

### Fixed
- Site logos in the Health and Travel themes now declare their real pixel dimensions instead of fixed placeholder values, so uploaded logos of any shape render at the correct aspect ratio without distortion or layout-shift warnings.

---

## [2.24.0] - 2026-07-08  ·  _Minor_
**Setup Wizard 2.0: WordPress Migration at Scale & Smart Recovery**

### Added
- Resumable WordPress migration: progress is saved on the server after every batch — if your browser closes or the connection drops mid-migration, reopening the wizard offers to continue exactly where it left off.
- Same-server fast path: when WordPress lives on the same hosting account, images are copied directly from disk instead of downloaded over HTTP — large media libraries migrate in a fraction of the time.
- Smarter server pre-check: disk space, memory limit, upload size and next-gen image support are now verified up front, with plain-language guidance for anything that needs attention — required items block, optional ones just warn.
- Full WordPress fidelity: pending, private and scheduled posts keep their status, comment reply threads are preserved, comment author links are carried over, and your site logo is localized automatically.

### Improved
- Wizard actions are protected with a per-session token, and the legacy parameter that allowed re-running installation on an already-installed site has been removed.

### Fixed
- In-place migrations (same domain) now migrate images correctly: previously same-domain image URLs were skipped as "already local", and removing the old WordPress files afterwards broke every image in your content.
- Large sites no longer risk server timeouts: imports run in time-budgeted batches with keyset pagination, and comments are imported in batches too — sites with tens of thousands of posts and comments migrate reliably on shared hosting.
- Tag and category names containing commas are no longer split into separate terms, and long tag lists are no longer truncated.
- Your existing .htaccess is backed up before installation replaces it, featured images resolve from WordPress metadata instead of unreliable legacy URLs, and stale responsive image attributes pointing at the old site are cleaned up.
- The setup wizard now speaks your language end to end — every server-side message is available in English and Turkish, and unrecoverable server errors return a readable explanation instead of a blank response.

---

## [2.23.1] - 2026-07-08  ·  _Patch_
**Managed-Install Indicator Hardening**

### Fixed
- Centrally-managed installations without the license enforcement stack no longer show a dead-end "Update Available" banner and sidebar badge — the managed-install marker is now honored everywhere the update UI is rendered.

---

## [2.23.0] - 2026-07-08  ·  _Minor_
**Commerce Core: Updates, License Portability, Plan Upgrades & Support**

### Added
- License portability from the customer panel: see every site bound to your license, remove one to free the slot, add a new domain, and activate there — moving a license between sites takes a minute and needs no support ticket.
- Theme and plugin updates now flow through the same signed channel as core: RSA-signed manifest covers every package, one-click theme/plugin updates work in the admin panel, and a publish pipeline ships them (package → verified upload → catalog).
- Plan upgrades from the customer panel: pay only the difference, your license key stays the same, and your site limit rises the moment payment completes — no re-activation on your sites.
- Support hardening: ticket confirmation emails to customers, staff notifications on replies, customer file attachments, priority support wired to your plan (Pro+ can open urgent tickets), and contact-form messages now land in the support queue instead of a write-only table.

### Improved
- Core update notes in the admin panel now show the real release changelog instead of a generic package label.
- Update access tier is now read from the license record, so plan upgrades take effect on the update channel instantly.

### Fixed
- License seat operations no longer depend on the execution context — the customer panel, admin, and API all use the same database seam (previously the panel path could fail fatally).
- Support tables are now guaranteed with self-healing schema (including legacy installs), so the customer portal cannot hit a missing-table error.

---

## [2.22.0] - 2026-07-08  ·  _Minor_
**Site-Wide SEO Hardening**

### Added
- Archive pages (category, tag, author, search) now generate their own unique titles, meta descriptions, and Open Graph tags — no more duplicate-title clusters across archives, on every theme, with no theme changes required.
- Optional tag archives: a new SEO setting turns /tag/ pages into real, sitemap-listed archives (thin tags stay auto-noindexed). Off by default, matching modern crawl-budget guidance.
- Feeds now declare a WebSub hub, so feed readers and discovery services get real-time update pushes; uploaded images receive an automatic humanized alt text when none is provided.

### Improved
- The first large content image on each page is now promoted to eager loading with high fetch priority — a direct LCP (Core Web Vitals) win on image-led pages.
- Meta descriptions no longer cut words in half: automatic descriptions now end on word boundaries with clean punctuation.
- Retired Google/Bing sitemap-ping calls were removed from the publish path (they only added seconds of dead waiting), and duplicate IndexNow submissions were deduplicated to a single ping per publish.
- Sitemap accuracy: real last-modified dates in the index, paginated post sitemaps are announced above 50k URLs, and video sitemaps join the index when video posts exist.

### Fixed
- Structured data is now hardened against content that contains script-closing sequences (JSON_HEX_TAG across all emitters) — schemas can no longer be broken or exploited by post content.
- Open Graph URLs on archive pages pointed to the homepage; they now match the canonical URL. og:locale now always agrees with the html lang attribute.
- On subdirectory installs the og:image check failed silently and social cards shipped without an image; the base path is now resolved correctly.
- Non-existent category and author URLs returned an empty page with HTTP 200 (soft-404); they now return a real 404. Duplicate Recipe/FAQ schema emissions are prevented page-wide.

---

## [2.21.2] - 2026-07-08  ·  _Patch_
**Stories: Consistent Emoji Art, Reaction Switching & Live Reaction Stream**

### Improved
- Reactions now use embedded SVG emoji art (Twemoji) instead of OS emojis — the same crisp, modern look on every device and browser, with no external requests.
- You can now change your reaction: tap a different emoji and the previous one is replaced, with counts adjusted correctly behind the scenes.
- Earlier reactions are now visible to every viewer as a subtle ambient stream — tiny emojis float up the story while it plays, proportional to how many reactions the slide collected.
- The Statistics page was redesigned: KPI tiles on top, per-slide view bars, CTR column, emoji-by-emoji reaction breakdowns, inline poll result bars, and a visual completion meter per story.

---

## [2.21.1] - 2026-07-08  ·  _Patch_
**Instagram-Style Story Reactions**

### Improved
- Story reactions were redesigned in Instagram's quick-reaction language: six bare emojis (❤️ 😂 😮 😢 🔥 👏) with a springy pop on tap and a shower of emojis floating up the story — no button chrome, no grey chips.

---

## [2.21.0] - 2026-07-08  ·  _Minor_
**Stories v1.1 — Auto-Stories, Polls, Reactions & Analytics**

### Added
- Auto-stories: when you publish a post, a story is created automatically from its featured image, title, and link — and retires on its own after a configurable lifetime. Your story strip stays fresh with zero manual work.
- Poll slides: ask a question with 2–4 answers; visitors tap to vote and instantly see live percentage bars. One vote per visitor, no login required.
- Emoji reactions (🔥 ❤️ 👏) on every slide — a single tap, cookie-free, one reaction per slide, with a satisfying burst animation.
- Statistics tab: per-slide views with a 7-day column, link clicks with CTR, reactions, poll result breakdowns, and a completion rate showing how many viewers reach the last slide.

---

## [2.20.2] - 2026-07-08  ·  _Patch_
**Stories Cache Fix & Cleaner Admin**

### Improved
- The Stories admin was decluttered: slide editing is now collapsed behind an Edit toggle, add-slide tools are grouped into tidy accordions, and settings use aligned rows with inline inputs.

### Fixed
- The Stories viewer script is now served with a server-cache bypass, so viewer fixes reach visitors immediately after an update instead of being pinned to a stale cached copy.
- Closing the viewer is hardened at the style level as well — the close button, Escape, and swipe-down work even if a theme stylesheet interferes.

---

## [2.20.1] - 2026-07-08  ·  _Patch_
**Stories Viewer Fixes & Inline Links**

### Fixed
- The story viewer close button (and Escape / swipe-down) now reliably closes the overlay.
- Slide links are now clickable text instead of a separate button: the caption or card text itself opens the link, and inline links can be placed on any word with [visible text](url) syntax.
- The story-age indicator in the viewer header now shows explicit units (e.g. "3 h"), so it can no longer be mistaken for the slide duration.

---

## [2.20.0] - 2026-07-08  ·  _Minor_
**Stories — Instagram-Style Stories for Your Site**

### Added
- New Stories plugin: a tappable story strip with a full-screen viewer — image, video (MP4/WebM), and text-card slides with auto-advancing progress bars, swipe/keyboard navigation, and hold-to-pause. Mobile-first, dependency-free, and zero page weight when no story is live.
- Every slide can carry a caption, a custom duration, and a call-to-action link with its own label — turn announcements into traffic.
- Scheduling and auto-expiry: stories go live and retire on their own; permanent "Highlight" stories pin to the end of the strip. View counts are tracked per story, cookie-free.
- Placement is yours: choose the strip position (below header, top of content, top of page, above footer, or a custom CSS selector) and target pages from settings — saved per theme, works on every theme without touching theme files.
- Appearance controls with live preview: circle or vertical-card shape, three sizes, classic gradient / solid / no ring, alignment, optional strip heading, and automatic gray rings for already-watched stories.

---

## [2.19.4] - 2026-07-08  ·  _Patch_
**License Enforcement Gap-Closing**

### Improved
- The managed-install marker is now cryptographically signed and bound to its domain. Legitimate managed installs are unaffected.

---

## [2.19.3] - 2026-07-08  ·  _Patch_
**License Enforcement & EULA Hardening**

### Improved
- Licence verification records which distribution a copy came from, so an unauthorised redistribution of a licensed copy can be identified. Legitimate installations are unaffected.
- The End User License Agreement (EULA) was strengthened with explicit clauses on embedded copy-tracking, its evidentiary value, liquidated damages, and reverse-engineering/rebranding bans; checkout now records EULA acceptance.

---

## [2.19.2] - 2026-07-08  ·  _Patch_
**Install Integrity Hardening**

### Improved
- The install-integrity subsystem was strengthened so unauthorized modification or redistribution of a licensed copy is detected and traceable more reliably. Legitimate installs are unaffected.

---

## [2.19.1] - 2026-07-08  ·  _Patch_
**Traffic & Distribution: Web Push Repair, Single IndexNow Key and Outreach Pacing**

### Improved
- The weekly opportunity limit in the backlink workspace is now actually enforced: once the week's quota is used, new additions are paused with a clear message — keeping outreach deliberate, exactly as the screen promises.
- Traffic Health now includes a Web Push row: service-worker reachability, subscriber count and the last send at a glance.

### Fixed
- Web Push now works end-to-end. The public endpoints the browser needs (service worker, key, subscribe) were never wired into the router, so enabling push could not deliver a single notification. They are now first-class routes, subscriptions are validated before being stored, and sending respects a time budget so a large subscriber list can never stall publishing.
- One IndexNow key per site. The plugin and the core search pinger each generated their own key, leaving two key files in the site root and duplicate submissions. Both layers now share a single key; changing or regenerating it updates everything and removes the stale key file.
- Saving a setting after a test or an error no longer shows a generic "Saved." — the real result (test outcome, error detail) is now displayed.
- If VAPID keys could not be generated during activation, Web Push stayed permanently broken with no way to recover; the settings screen now regenerates them automatically and reports failures clearly.

---

## [2.19.0] - 2026-07-08  ·  _Minor_
**Social Auto-Publish: Instagram Stories, Discord, Evergreen Re-sharing and Reliability**

### Added
- Instagram Stories. Every new post can now also be shared as a 9:16 story a few minutes after the feed post — the image is prepared automatically from the featured image. On by default, one toggle in settings.
- Discord channel publishing. Zero-friction: paste a channel webhook URL and every new post lands in your community as a rich embed (title, description, image, link). No app registration, no OAuth.
- Evergreen re-sharing. Opt-in: older evergreen posts are periodically re-shared to your text channels for steady archive traffic — age threshold and daily cap are configurable, visual channels are excluded, and the same post is never repeated within the window.
- Failed-item recovery. The queue screen now lets you retry or delete failed items (one or all) and shows a 7-day per-platform success-rate table.

### Improved
- Adding a new token-based platform no longer requires editing the admin screen: connection forms are generated from the platform registry.
- Facebook Page connections now exchange for a long-lived token and refresh themselves — previously the token silently died within hours and the account broke on first publish.
- The queue is now claimed atomically per item, so overlapping schedulers can never double-publish; stuck items self-recover after 30 minutes, and web-cron runs respect a time budget.

### Fixed
- Pinterest "Diagnose" results were never written to the log (a status value the table did not accept was silently dropped).
- Expired connections are now labeled as expired with a clear reconnect signal instead of a generic error.
- The X/Twitter authorization no longer requests a media permission the adapter never uses.

---

## [2.18.34] - 2026-07-07  ·  _Patch_
**Admin Raw-Key Repair: 249 Missing Translations Restored**

### Fixed
- Several admin pages showed raw translation keys instead of text (e.g. "admin_blog_posts.th_title") — in both languages. 249 missing dictionary entries were authored in Turkish and English across the blog posts, licenses, email templates, order detail, invoices, backups and login screens; a new linter check now blocks any future use of an undefined key.
- The theme catalog page and the sidebar's First-Install Package label were hardcoded in Turkish; they now follow the admin language.
- The invoices screen crashed on load: its overdue-count query referenced a column that never existed (due_at → due_date).

---

## [2.18.33] - 2026-07-07  ·  _Patch_
**Customer Portal Fully Bilingual + a Language-Leak Shield**

### Improved
- A new internal language-leak linter guards every future change: any new user-facing string that is not born as a TR/EN pair is caught before release, so this class of bug cannot silently return.

### Fixed
- Turkish text no longer leaks into the English customer portal (and vice versa). Every remaining single-language page was made properly bilingual: security settings, email verification, forgot/reset password, checkout and its success/cancel pages, support tickets, downloads and order details.
- The setup wizard now speaks English. The first screen a new buyer sees was almost entirely Turkish; it is now fully bilingual with a TR/EN switcher, follows the browser language by default, and all of its error messages are translated too.

---

## [2.18.32] - 2026-07-07  ·  _Patch_
**Site Name Signal Completed Across All 14 Themes**

### Fixed
- Every theme's homepage now marks the site name as an H1 heading — completing all four signals Google documents for choosing the site name shown in search results, so Google stops falling back to the bare domain. The heading renders with zero visual change; inner pages keep their content H1. (Personal shipped in the previous release; the remaining 13 themes are covered now.)
- The Minimalist theme's header brand was hardcoded to a specific site name; it now follows the Site Name setting like every other theme.
- The Finance theme showed no brand at all when no logo was uploaded, and its homepage detection could mislabel search or paginated pages; both were corrected.
- The Recipes theme rendered its brand as an H1 on every page, giving articles two H1s; the brand is an H1 on the homepage only now.

---

## [2.18.31] - 2026-07-07  ·  _Patch_
**Personal Theme: Site Name Signal Completed for Google (Homepage H1)**

### Fixed
- Google could fall back to showing your domain instead of your site name in search results. The Personal theme's homepage had no H1 heading — one of the four signals Google documents for choosing a site name (WebSite structured data, og:site_name, title, and a prominent heading). The header brand now renders as an H1 on the homepage only, with identical visual styling; inner pages keep their content H1.

---

## [2.18.30] - 2026-07-07  ·  _Minor_
**Buying Goes Live: Pricing-Page Checkout and a Discount Campaign Manager**

### Added
- The pricing page now sells. Every plan's button opens the secure checkout with that plan preselected; signed-in customers get their email and name prefilled, and the checkout language follows the site language.
- Discount campaign manager. Define campaigns in the admin — percentage or fixed amount, date windows, redemption limits, per-plan restrictions and special-day presets (New Year, Black Friday, and more). Campaigns sync to the payment provider automatically; the pricing page shows a campaign banner and can apply the code at checkout without the customer typing anything.

### Fixed
- Plan prices defined in code had drifted from the public pricing page; they are aligned again.

---

## [2.18.29] - 2026-07-07  ·  _Minor_
**International Payments via Polar, Instant License Delivery, and an Account Security Overhaul**

### Added
- International card payments via Polar (Merchant of Record). Every paid Polar order automatically creates the customer account, issues the license key, generates the invoice and emails the key — no manual steps. Deliveries are idempotent, webhook signatures are verified, and the checkout thank-you page shows the license key the moment it is ready.
- Email verification for customer accounts. New registrations receive a verification link (sign-in is never blocked); changing your email re-requires verification of the new address and notifies the old one. A new resend-verification page replaces links that previously led nowhere.
- Account deletion (GDPR/KVKK). Customers can permanently anonymize their account from the Security page with password confirmation; order and invoice records are retained as required by law.
- Real login history. The Security page now shows actual sign-in attempts (date, IP, outcome) — the old list was wired to a table nothing ever wrote to.

### Improved
- Brute-force protection is now database-backed. The old limiter counted attempts inside the visitor's own session, so clearing cookies reset it; limits are now enforced per email and per IP across sessions, and every attempt is audit-logged.
- Changing your password now confirms it by email and refreshes the session; the non-functional "Remember me" checkbox was removed (sessions already persist for 30 days).

### Fixed
- The email verification page queried columns that never existed in production, so verification links could not work; it now uses the real schema.
- Viewing a support ticket linked to an order could fail due to a query against a non-existent table.
- Site-validation bots of payment providers were blocked by an over-broad user-agent filter, which made provider onboarding fail with "could not reach this URL".

---

## [2.18.28] - 2026-07-07  ·  _Patch_
**Sign-In Flow Streamlined: Session-Aware Header and Google-Only Social Login**

### Improved
- The site header now recognizes signed-in customers. After signing in or registering, the "Sign In / Get Started" buttons are replaced with "Dashboard" and "Sign Out" — on desktop and in the mobile menu.
- Signing in no longer pulls you away from the page. Logging in or registering from the site keeps you where you were instead of forcing a redirect to the customer dashboard; Google sign-in returns you to the page you started from.
- Your language choice follows you into the customer portal. Browsing the site in English opens the dashboard in English after sign-in; browsing in Turkish opens it in Turkish.
- Social sign-in is now Google only. The rarely used GitHub, Facebook and Microsoft sign-in options were removed from the sign-in modal, the portal pages and the admin settings.
- Signing out now returns you to the homepage instead of the login screen.

### Fixed
- Google sign-in errors are now shown. The login page listened for the wrong URL parameter, so OAuth errors (cancelled sign-in, misconfiguration, inactive account) were silently swallowed; all error codes now surface with bilingual messages.
- The registration modal accepted submissions without the Terms of Service checkbox being ticked; acceptance is now enforced.
- Sign-in and registration API calls resolved to the wrong path on subfolder installations; they now respect the site base path.
- Password reset now works on installations missing its table. The password_resets table only existed in a development migration; when absent, the forgot-password form crashed. The table now self-heals on first use, and a mail delivery failure no longer breaks the flow.
- Login error messages mixed English and Turkish regardless of the chosen portal language; they now follow it.

---

## [2.18.27] - 2026-07-05  ·  _Patch_
**Content Tables Are Now Styled in the Personal Theme**

### Fixed
- Tables inside articles now have proper borders, a header row and spacing. The Personal theme had no table styling, so tables rendered as plain unbordered columns that were hard to read. They now have cell borders, a shaded header row, comfortable padding, zebra striping and horizontal scrolling on small screens.

---

## [2.18.26] - 2026-07-05  ·  _Patch_
**Schema Gaps Closed for Voting, AI SEO Analysis and IP Blocking**

### Fixed
- Article voting now works. The up/down vote feature (used by the crypto theme) wrote to a post_votes table and a posts.votes column that the schema never created — and an old migration even defined the table with mismatched column names. The table and column are now part of the schema, self-heal on existing sites, and the stale migration was corrected.
- AI SEO analysis is now saved. The editor's AI analysis wrote to seo_meta columns (ai_score, ai_analysis, ai_analyzed_at) that did not exist, so results were never persisted. The columns were added to the schema and self-heal on existing sites.
- The IP block list has a proper schema table. Previously it only existed when an admin happened to open the Security Center; it is now part of the core schema and self-heals.

---

## [2.18.25] - 2026-07-05  ·  _Patch_
**Schema Consistency: Silent Database Errors Fixed + Drift Guard**

### Improved
- A schema drift guard now runs in the release pipeline. A new tool cross-checks every table/column written by the code against the schema and plugin definitions; any newly introduced mismatch fails the release, preventing this class of fresh-install error from recurring.

### Fixed
- Comment replies and API comment creation now save reliably. Both wrote to a column name (ip_address) that did not exist on the comments table (the correct column is author_ip), so these paths failed on every install. They now use the correct column.
- Automatic IP blocking now actually blocks. The security module wrote a non-existent blocked_at column, so blocks were silently dropped; it now uses the correct column.
- Theme switching and settings saves are safe on fresh installs. The settings table gained created_at/updated_at columns (added to the schema and self-healed on existing sites) — code wrote these timestamps but the fresh-install schema lacked them.
- ZeroTrack registers correctly on activation. Its plugin record used the wrong column names (active/core instead of is_active/is_core).

---

## [2.18.24] - 2026-07-05  ·  _Patch_
**Log and Data Hygiene: A Self-Limiting CMS**

### Improved
- Automatic maintenance now covers every accumulating store. Raw view records (180 days), auto-link logs, SEO ping logs and expired Google Console cache entries are pruned on the existing maintenance schedule, and oversized log files (including php-errors.log) are rotated centrally with 30-day cleanup of old rotations.

### Fixed
- The database error log can no longer grow without bound. It now rotates at 5 MB with a single backup kept, matching the application log. A recurring cron error had been able to grow this file indefinitely.
- Two chronic error sources were silenced at the root. The webhook queue self-heals missing api_tokens columns on older installs (and the webhook feature starts working), and the AI bulk worker skips quietly when its table is not installed — both had been writing an error entry every minute.

---

## [2.18.23] - 2026-07-05  ·  _Patch_
**ZeroTrack: Interactive Trend Chart and Full Localization**

### Improved
- The trend chart was redesigned from scratch. The bare line chart is now an interactive bar chart: hovering highlights the bar and its neighbors, shows a tooltip with views and unique visitors, and updates the live value in the header. Days with no data render as zero instead of being skipped, and the "Today" range now shows an hourly breakdown.
- KPI cards now compare against the previous period. Page views, unique visitors and sessions show a rise/fall percentage next to the label.
- The whole plugin follows the admin design system and language. Every label on the dashboard and settings pages is fully localized (Turkish admin shows Turkish everywhere), and hard-coded light-theme colors were replaced with design tokens so dark mode renders correctly. Top pages gained proportional usage bars.

---

## [2.18.22] - 2026-07-05  ·  _Patch_
**Google Console: Consistent Reports and a Permanent-Connection Guide**

### Improved
- Search Console and Analytics now report the same date window. GA4 requests previously ended "today" while Search Console ended yesterday, so overview KPIs compared different periods. Both now use the identical range, making trends directly comparable.
- Keyword and page tables show up to 50 rows (previously 20), and indexing-coverage scans now cover up to 2,000 URLs (previously 500) in line with Google's URL Inspection daily quota.
- Reconnect banner now explains the most common cause. When Google drops the connection with invalid_grant — typically because the OAuth app was left in "Testing" mode, which expires grants after 7 days — the panel says so and walks through publishing the app to production for a permanent connection. The setup guide covers this too.
- Search Console site addresses are normalized on save. Entering a bare domain becomes a proper domain property (sc-domain:), and URL-prefix properties get their required trailing slash — malformed values used to fail silently with empty reports.

---

## [2.18.21] - 2026-07-05  ·  _Patch_
**Newsletter Result Pages Work on Every Theme, in Both Languages**

### Fixed
- Newsletter subscribe/confirm/unsubscribe pages no longer crash on non-Personal themes. These pages called a Personal-theme helper directly, which caused a server error on any other active theme. They now use a theme-safe helper and render their texts in the site language (Turkish or English) instead of hard-coded Turkish.

---

## [2.18.20] - 2026-07-05  ·  _Patch_
**Visible Spam Protection, Reliable Newsletter Signup, Consistent Plugin Naming**

### Improved
- The built-in spam filter is now visible and explainable. The Comments screen links directly to Spam Protection settings, flagged comments show their spam score with the reasons that triggered it, and the spam tab offers a one-click "Not Spam" action. The filter itself (link limits, keyword/IP/e-mail blacklists, submit-speed and repeat-offender checks) was already scoring every comment behind the scenes.
- Plugin names and ordering are consistent everywhere. The sidebar now uses the same localized plugin names as the Plugins screen, and both lists are sorted alphabetically by the displayed name.
- Theme customizer is fully localized. Tab and theme descriptions now appear in Turkish on Turkish admin panels, and the page title follows the admin language.

### Fixed
- Newsletter signup now works from every theme. Several themes posted their subscribe forms to endpoints that did not exist (/newsletter, /api/v1/newsletter/subscribe), so signups silently failed. Both endpoints now reach the newsletter plugin, and the API works in sub-directory installs too.
- Fresh installs no longer break on comments or subscribers. The installer schema was missing the spam-score columns on comments and the subscribed_at column on newsletter subscribers; both are now in the schema and self-heal on existing sites.
- New-post notification e-mails render correctly. The notification campaign stored post data as raw JSON that would have been printed into the e-mail; the sender now resolves it into the template placeholders.
- Crypto theme footer now obeys the customizer. The "Brand blurb" field is actually rendered, the social-icons toggle works, the site name is no longer hard-coded, and the footer subscribe form posts to the correct endpoint.

---

## [2.18.19] - 2026-07-05  ·  _Patch_
**Instant Admin Asset Updates, Dropdown Clipping Fix**

### Fixed
- Admin CSS/JS updates now reach the browser immediately. Stylesheet and script URLs are versioned by file modification time instead of the CMS version number, so hotfixes no longer require a hard refresh or a version bump to become visible.
- Custom dropdown panels are no longer clipped by their card. When a select panel (such as the Author picker in the post editor) is open, its containing card temporarily allows overflow so the full option list is visible.

---

## [2.18.18] - 2026-07-05  ·  _Patch_
**Author Picker on the Post Editor, Sentence-Aware Excerpts**

### Added
- Posts can now be assigned to a different author from the editor. A new Author dropdown in the Publish box lists the site's writers; the change is saved with the post. Autosave and quick-edit paths are unaffected.

### Fixed
- Auto-generated excerpts no longer cut off mid-phrase. The generator now prefers the last full sentence within the window, ignores version-number dots (like "GPT-3.5"), is UTF-8 safe for Turkish characters, and inserts spaces where block tags met. Existing truncated excerpts across all sites were regenerated from content.

---

## [2.18.17] - 2026-07-04  ·  _Minor_
**Pro Theme Customizer: Font Previews, Import/Export, Turkish UI, Deeper Options**

### Added
- Theme settings can now be exported and imported as JSON — move a finished design to another install in one click, with schema-validated import, cross-theme confirmation and a one-click "Reset to defaults" that preserves footer-builder data.
- Font pickers became real font pickers. A central 38-family library backs every font field (empty dropdowns are gone), the current font sits selected at the top, every option renders in its own typeface, and a live preview line updates as you browse.
- Deeper per-theme options, all wired to real output: the Personal theme gained homepage controls (hero slide count, popular section and count, categories toggle, posts-per-page for the latest grid) and a Post Page tab (sidebar, author card, related posts and count, comments) — every switch verified to change the rendered page.

### Improved
- The customizer speaks Turkish now. Over a hundred remaining English field and tab labels across all theme schemas were translated for Turkish admin sessions.

---

## [2.18.16] - 2026-07-04  ·  _Patch_
**Fresh-Install Audit: Theme Switching, Customizer and Setup Hardened End-to-End**

### Fixed
- A full customer-journey audit (installer → theme switching → customizer → import) fixed nine fresh-install bugs. Subdirectory installs no longer hit an infinite redirect on About/legal pages; single-post pages now receive author data, so the News theme no longer crashes; the Tech theme's missing helper, the Finance theme's missing comments partial, and Health theme null-image crashes are all resolved.
- Search works on every host now. Reusing one SQL placeholder twice broke search with an SQL error on servers where PDO prepares are not emulated — fixed in the core query builder, the Health theme and the quiz plugin.
- Saving the Theme Customizer no longer wipes other settings. It used to replace the theme's whole customization record, silently deleting footer-builder data; it now updates only its own fields. The footer builder likewise activates only on themes that render it, instead of corrupting other themes' footer settings.
- Setup polish: application logging now creates its log directory on first use (it was silently dead on fresh installs), broken absolute-path ErrorDocument rules were removed, and session ini warnings on first requests are gone.

---

## [2.18.15] - 2026-07-04  ·  _Patch_
**Media Library: Click-to-Edit Restored, Smarter Alt Text Editing**

### Improved
- Alt text editing got a live character counter and guidance (ideal ≤125 characters) so image SEO fields are filled properly, not just filled.

### Fixed
- Clicking an image in the media library opens its detail/edit screen again. The lightbox was capturing every click on image cards, so the screen where alt text, caption and description are edited had become unreachable. Zooming now has its own magnifier button on the card (and clicking the preview on the detail page).

---

## [2.18.14] - 2026-07-04  ·  _Patch_
**Ad Placements Standardised Across All Themes, Honest Slot Panel**

### Improved
- Every theme now renders the standard ad placement set. An audit found the personal and trends themes rendered no ad slots at all, health and recipes only one or two — ad code pasted in the admin simply never appeared. All themes now support: below navigation, above/inside/below the article, between archive cards and above the footer.
- The ad manager now tells the truth per slot. Each slot card shows whether the active theme actually renders it ("In theme" / "Not in theme" badge), and the four legacy slots that no current theme uses are hidden unless they hold saved code.

---

## [2.18.13] - 2026-07-04  ·  _Patch_
**Hotfix: Footer Customizer Save No Longer Rejected**

### Fixed
- The real root cause of the footer customizer's "CSRF token mismatch" was a field-name mismatch, now fixed at the core. The form emits its token as `_token` while the handler read `csrf_token` and passed an empty string, which blocked the fallback lookup — so every save was rejected even in a fresh session. The validator now treats an empty token as "not provided" and falls back to all accepted field names; invalid tokens are still rejected.

---

## [2.18.12] - 2026-07-04  ·  _Patch_
**Footer Customizer Redesign, Newsletter Styling, Session-Lifetime CSRF**

### Improved
- The footer customizer got a visual overhaul. Templates are now picked from illustrated layout thumbnails instead of a text list, sections follow a consistent card design, and a sticky save bar keeps the action always in reach.
- The footer newsletter block is now fully configurable. Besides the title and intro, you can set the input placeholder, the button text and a display style — plain, boxed card or accent-tinted card — with matching styles for dark footers and mobile.

### Fixed
- "CSRF token mismatch" on save is gone. Security tokens used to hard-expire after one hour, so any admin form left open longer — the footer customizer, a long post edit — died on submit. Tokens are now valid for the whole login session, per the standard per-session pattern.

---

## [2.18.11] - 2026-07-04  ·  _Patch_
**One-Click Edit for Every Legal Page**

### Improved
- Every row in the legal page status table now has an Edit button. For pages still served from the theme's built-in template, clicking Edit creates the page from the ready-made text using your site settings and opens the editor immediately — no detour through the generator form. The explanatory text on the screen was also rewritten in plain language.

---

## [2.18.10] - 2026-07-04  ·  _Patch_
**Pages Hub With Inner Navigation, Legal Pages Finally Editable at a Glance**

### Improved
- The Pages screen is now a proper hub with an inner sidebar — the same pattern as Settings. Modules are grouped under headings: Pages (all pages, new page) and Legal Pages (status & edit, generator). The old single-scroll screen that mixed the generator, a status table and a legacy record list into one confusing page is gone.
- Every legal page now has a clear path to editing. Pages backed by a CMS record show an Edit button; pages currently served from the theme's built-in template are labelled "theme default" and offer a one-click Create action that jumps to the generator with that page preselected.

### Fixed
- Hover row actions (Edit | View | Trash) in content lists are left-aligned under the title again. A shared action-cell style had pushed them to the right edge of the title column in posts, categories, tags and quiz lists.
- The legacy legal-records block was removed from the CMS admin. It edited a marketing-site table that has no effect on a CMS site's public pages, which made the screen genuinely misleading.

---

## [2.18.9] - 2026-07-04  ·  _Patch_
**Category Slug Renames Get Automatic 301s, 404 Logging Heals Itself**

### Added
- Renaming a category slug now creates a 301 redirect automatically — in both the admin panel and the REST API. Combined with v2.18.8's post-slug redirects, no rename anywhere in jekcms can silently orphan an indexed URL anymore.

### Fixed
- 404 logging works on every install now. The not-found log table was only created when an admin first opened the Redirects page; on sites where that never happened, every 404 was silently discarded and the "suggest redirect" list stayed empty forever. The logger now creates its own table on first use.

---

## [2.18.8] - 2026-07-04  ·  _Patch_
**Automatic 301 on Slug Change, Legacy URL Guard, Cleaner Crawl Budget**

### Added
- Renaming a published post now creates a 301 redirect automatically. Previously every slug change silently left the old URL as a 404 in Google until someone noticed and added a manual redirect — a across every installation Search Console audit found exactly this pattern in the wild. The redirect is created on save, existing chains pointing at the old slug are re-pointed at the new one, and duplicate sources are never inserted.
- Built-in guard for legacy WordPress URL families. Retired Turkish tag archives (/etiket/…) now return 410 instead of soft-404 redirects, taxonomy AMP leftovers (/author/…/amp, bare /amp, /amp/page/N) redirect in a single hop, so migrated sites stop accumulating Search Console errors.

### Improved
- Crawlers no longer waste budget on write-only endpoints. robots.txt now disallows the analytics beacon (/zt-track) and webhook paths, which previously showed up as "other 4xx" noise in Search Console.

---

## [2.18.7] - 2026-07-04  ·  _Patch_
**Search Console Cleanup: Retired Tag URLs Are Now Crawlable (410)**

### Fixed
- Retired /tag/ URLs can now leave Google's index. robots.txt disallowed /tag/ while the pages correctly returned 410 Gone — but a crawler that is blocked can never see the 410, so hundreds of dead tag URLs stayed frozen in Search Console error reports indefinitely. The disallow is removed; Google can now crawl the 410 responses and drop the URLs for good.

---

## [2.18.6] - 2026-07-02  ·  _Patch_
**Comprehensive Legal Pages, Unified Footer Credit, Author Card Fix**

### Improved
- Legal pages are now comprehensive and professional out of the box. The default Privacy Policy, Terms of Service, Cookie Policy and Disclaimer texts were rewritten editorially in both languages: data categories, legal bases, retention periods, Google AdSense/analytics disclosures with opt-out links, a cookie category table, permitted-use and liability sections. Sites that publish their own legal pages are unaffected — defaults apply only when no custom page exists.
- One footer credit everywhere. The footer bottom bar now reads "Powered by jekcms" in every language — the former Turkish translation of the credit was dropped in favor of a single brand-standard phrase.

### Fixed
- Legal pages are readable on dark-bodied themes. The universal legal template had no background of its own, so themes with a dark page body rendered near-invisible headings on a dark surface. The template now pins an explicit light panel with fixed text colors, plus proper list and table styling.
- Author card uses its full width. The author bio in the crypto theme was capped at 480px, wrapping sentences into a cramped column next to the avatar; the cap is removed.

---

## [2.18.5] - 2026-07-02  ·  _Patch_
**Crypto Theme: Legacy TOC Cleaner No Longer Swallows Article Bodies**

### Fixed
- Articles no longer render truncated. A legacy WordPress-import cleaner in the single template removed inline tables of contents with overly broad patterns: any H2 merely containing the word "içerik" — e.g. "AI content production" — triggered deletion of everything up to the next list, silently cutting up to 90% of an article at render time (the database content was intact). The cleaner now only scans the first 3000 characters, matches exact TOC phrases, and caps the removal window.

---

## [2.18.4] - 2026-07-02  ·  _Patch_
**Crypto Theme: Full-Width Layout and Styled Content Tables**

### Improved
- Homepage post grid and single articles now align with the header width. The "All Posts" section and the article layout previously used a narrower container, and the article body was additionally capped at 736px — both now follow the site's full 1400px line, so wide screens are actually used.

### Fixed
- Content tables render properly in articles. Table styling was scoped only to static pages, so tables inside posts appeared bare (no borders, no header background). Article bodies now get the same professional table look, with zebra rows and horizontal scrolling on mobile.

---

## [2.18.3] - 2026-07-02  ·  _Patch_
**Winning Content: Traffic Trends on Your Dashboard**

### Added
- Winning Content card on the dashboard. Your top 5 posts of the last 30 days with rise/fall indicators, powered by the built-in privacy-first ZeroTrack analytics — no external service, no cookies. Appears automatically once traffic data exists.
- Content Trend report in ZeroTrack. A rising/falling comparison (last 30 days vs the previous 30) at post level; falling posts are labelled as refresh candidates, so you know exactly which articles need attention before rankings slip further.

---

## [2.18.2] - 2026-07-02  ·  _Patch_
**Uniform Row Actions Across All SEO Lists**

### Improved
- List action buttons follow one clean standard. In Heading Fixer, Content SEO, Content Optimization and Orphan Content, row actions (Preview / Fix / Save / Edit) no longer wrap onto multiple lines or mix button styles — they sit in a single compact row with a consistent look; secondary validator shortcuts (Rich Results, Schema) are now subtle links instead of heavy buttons.
- Less noise in the Content SEO list. The redundant content-type label before each slug was removed; pages are marked with a small badge only when relevant.

---

## [2.18.1] - 2026-07-02  ·  _Patch_
**Advanced SEO Panel v2: One Navigation, Auto-Linked Orphans, Brand-Safe Headings**

### Added
- Orphan content fixes itself. The Orphan Content module gained an Auto-Link action: for every post with no inbound internal links, related posts (same category first) are scanned and a natural internal link pointing at the orphan is injected automatically — no manual editing, with the full markup-safety net and at most one new link per source post.
- SEO Health Check is now tabbed. Identity, AdSense, content, files and HTTP checks each get their own tab with issue-count badges — no more scrolling through long card columns.

### Improved
- One navigation, zero duplication. The Advanced SEO panel sidebar is now grouped (Overview, Content, Images, Links, Site) and each optimizer tab is its own module; inside the panel the old duplicate top tab bar is gone, and confusingly-named entries were renamed (Image SEO vs. Featured Images).
- Redirects & 404 opens clean. The module previously rendered the whole Settings page — including its own settings menu — inside the panel; it now opens as a standalone tool.
- Year Updater and Content Optimization follow the design line. Cards, tables and buttons match the rest of the admin; action buttons no longer wrap into circle-shaped blobs, and the Edit button got its missing style.

### Fixed
- Technical terms are no longer "fixed" into broken casing. Heading checks flagged titles like "cPanel Guide" or "iptables and ufw" as lowercase errors, and title-case would mangle them (cPanel → Cpanel). Brand-like words — mixed-case names, terms with digits or dots, and a broad list of lowercase tool names — are now left untouched in both detection and repair; Turkish conjunctions (ve, ile, için…) also stay lowercase in title case, in both languages.

---

## [2.18.0] - 2026-07-02  ·  _Minor_
**Advanced SEO Overhaul: Internal Linking Repaired, Turkish-Aware Matching, New Modules**

### Added
- Turkish-aware internal linking. On Turkish sites the linker now recognizes inflected forms ("e-posta pazarlamasında" matches "E-posta Pazarlama"), and posts' multi-word tags become anchor candidates — noticeably more natural internal links, with the same markup-safety net that reverts anything suspicious.
- Orphan Content module. Lists published posts with no inbound internal links and uncategorized posts, with linking-candidate suggestions from the same category.
- Bulk meta editor. Edit meta title/description inline in the post list with live character counters; scores recompute on save. CSV export is one click away.
- The panel now surfaces SEO Health Check, Redirects & 404 log and the SERP Identity test — previously hidden in Settings.

### Fixed
- Posts that matched no links are no longer excluded from future scans. A "processed, no links" marker made such posts invisible to the incremental scan forever and miscounted the panel statistics; they are now retried as your library grows, and the stats distinguish processed, linked and awaiting posts.
- Internal-linker silence is over. Every skipped, failed or successful on-publish linking attempt is now recorded to a dedicated log, so "why did this post publish without links?" is answerable — a read-only diagnostic page shows settings truth, log distribution and a live dry-run.
- The SEO panel no longer breaks inside its frame. Saving a form could render a second admin shell inside the panel, and edit links trapped you inside the frame; both fixed.
- Turkish content scores are measured correctly. Word counting was not UTF-8 aware, so Turkish posts scored artificially low; generated meta titles also respect your title separator and site name now.
- All SEO tools require administrator rights and use a single heading-hierarchy engine, ending inconsistent results between modules.

---

## [2.17.6] - 2026-07-02  ·  _Patch_
**No More Style Flash on Inner Pages, Analytics Beacon Restored**

### Fixed
- Pages no longer flash unstyled for a split second. The Personal theme async-loaded its full stylesheet while the inline critical CSS did not fully cover any page type; navigation briefly rendered bare. The stylesheet now loads normally — it is same-origin, versioned and immutable-cached, so the change costs nothing after the first visit.
- ZeroTrack page views are recorded again. The tracker posted to a plugin route that 404'd in production; it now uses the standalone /zt-track endpoint that works independently of plugin bootstrap.
- Cloudflare Insights no longer triggers console CSP errors. Its beacon origin was missing from the Content-Security-Policy script allowlist.

---

## [2.17.5] - 2026-07-02  ·  _Patch_
**Zero Validator Errors: noscript Guard & Footer Style Leftovers**

### Fixed
- The font-defer optimizer no longer touches noscript fallbacks. It could wrap the fallback link inside an existing noscript block, producing nested noscript markup and a dead stylesheet for no-JS visitors.
- Personal footer layouts dropped their duplicate legal bar. All eight variants carried a leftover legal-links block and an in-body stylesheet from before the standard bottom bar; links were doubled and the markup failed validation.

---

## [2.17.4] - 2026-07-02  ·  _Patch_
**Three Gaps Caught by the New Live Signal Checks**

### Fixed
- Health theme now emits the WebSite/Organization schema. Its header never called the central schema emitter, so sites on this theme published no structured data — invisible to Google's site-name and rich-result systems.
- Personal theme search pages are noindexed again. The header skipped the robots-meta helper entirely, leaving search results indexable.
- News-theme language attribute reads the correct setting. A legacy key left Turkish sites reporting lang="en".

---

## [2.17.3] - 2026-07-02  ·  _Patch_
**Theme Integrity: Every Theme File Now Ships From One Source**

### Fixed
- Recipe featured images resolve to the correct URL everywhere. A media-path fix that lived on a single install (cards/hero images could 404 when stored without the uploads prefix) is now part of the core Recipes theme.
- Theme copies can no longer silently drift. Previously only ~30 hand-picked theme files were integrity-checked; now every theme template and stylesheet is verified against the canonical source, and deliberately customized installs are tracked explicitly instead of being overwritten.
- Hardened against a class of update crashes. Syncing a theme's function file onto a customized install could remove helpers its templates still call, cutting pages off mid-render. Sync tooling now knows about customized theme sets and never overwrites them.

---

## [2.17.2] - 2026-07-02  ·  _Patch_
**Valid Markup, Correct Language Tags & Faster Font Loading**

### Improved
- Fonts no longer block first paint. Google Fonts and icon stylesheets across all themes now load with the non-blocking preload pattern, improving Core Web Vitals.

### Fixed
- Turkish search pages are no longer indexable. The /arama route escaped the noindex rule that /search already had, leaving thin search results crawlable — a "low value content" risk for ad-network review.
- Removed the hidden duplicate H1 from homepages. An old experiment injected an invisible site-name heading on every homepage, producing two H1 elements on themes that render their own. Each page now has a single, visible heading.
- Article pages no longer break on customized Entertainment installs. A sidebar helper call could crash mid-page on sites with a customized theme copy, cutting the page off before the footer. The sidebar now degrades gracefully.
- Markup validates cleanly. Headings inside inline wrappers, a mis-scoped ARIA label and the footer bar's in-body stylesheet (now emitted in the head) were the last W3C validator errors.
- Language attribute now follows your site language. Five themes hard-coded lang="en"; Turkish sites reported the wrong language to browsers and crawlers.

---

## [2.17.1] - 2026-07-02  ·  _Patch_
**Your Site Name Now Reaches Google Exactly As You Typed It**

### Fixed
- Google could show your domain instead of your site name in search results. The system auto-generated a spaceless copy of your site name as a schema alternate name, and a Turkish-character comparison bug let this domain-lookalike value slip into the page. Google's site-name algorithm could then fold your brand into the bare domain. The auto-generated alternate name is gone, the comparison now transliterates Turkish characters correctly, and existing installs clean up the stray value automatically — the Site Name setting is now the single source of truth, emitted verbatim.
- Removed weaker duplicate schema emitters from five themes. Personal, Trends, Recipes, News and Lifestyle carried their own WebSite/OpenGraph generators missing fields Google uses for site-name selection; all themes now use the central, complete emitter.
- Admin SEO preview now matches the real page output. The preview showed a different homepage title pattern than what the site actually emitted.

---

## [2.17.0] - 2026-07-02  ·  _Minor_
**Content Rendering, Performance & AdSense-Ready Theme Pass**

### Improved
- Faster pages with responsive images. Article cards and thumbnails now load an appropriately sized image variant instead of the full-resolution original, cutting page weight significantly.
- Navigation and footers are data-driven. Menus, category bars and footer links now come from your real categories, so a fresh site never shows dead example links — better for visitors and for ad-network review.
- Dark mode stays correct with custom colors. Setting brand colors no longer overrides the dark theme; dark mode renders reliably regardless of customization.
- Cleaner article intros. The first paragraph is auto-capitalized at publish, so content never starts lowercase.

### Fixed
- Markdown headings no longer leak as raw “###” text. Content that mixed HTML with Markdown could print literal “### Heading” or merge a heading and its first paragraph into one oversized block. Headings are now correctly separated and rendered, both at publish time and on render — across every theme.
- Queued articles that silently failed to publish now go out reliably. A session-cookie error during manual publishing could leave items stuck as “failed”. The underlying call is now guarded, so publishing completes instead of aborting mid-way.
- Removed placeholder/demo content from themes. Sample authors, demo article bodies, fabricated statistics and dead example links could appear on real pages; these are gone, so only your real content is shown.
- Legal links now appear in the Personal theme footer. The standard bottom bar (copyright · legal links · credit) was missing from all Personal footer layouts, so privacy/terms pages existed but were unreachable from the footer. Every footer variant now renders the shared bottom bar.
- Theme stylesheets update reliably after an upgrade. Tech, Entertainment and Pets linked their CSS without a version stamp, so browsers could keep serving a cached stylesheet indefinitely; the link is now stamped per file change.

---

## [2.16.37] - 2026-06-23  ·  _Patch_
**No More Dead-End Update Banner on Centrally Managed Sites**

### Fixed
- The “Update available / Update Now” banner no longer appears on centrally managed sites. On these installations self-update is disabled and new versions are delivered by operator deployment, so the banner, the header update icon and the sidebar update badge were a dead end — clicking “Update Now” did nothing. They are now hidden whenever the install is centrally managed, matching the System Updates page which already showed “Central deployment ready”.

---

## [2.16.36] - 2026-06-23  ·  _Patch_
**Professional Single-Bar Footer & Permanent CSS Cache Fix**

### Improved
- The footer bottom is now a single clean bar — copyright, legal links and the credit line share one row instead of a separate, duplicated legal strip below the copyright. Legal links used to render twice (in the footer columns and again in an injected bar); the redundant strip is removed across all themes.

### Fixed
- Theme CSS no longer serves a stale cached copy after an update — the stylesheet is cache-busted by its file modification time, so visitors get the current styles without a hard refresh.

---

## [2.16.35] - 2026-06-17  ·  _Patch_
**Canonical Cleanup: /page Redirects, Alias Consolidation & AdSense Readiness**

### Improved
- robots.txt is now AdSense- and Google-safe — the Googlebot group mirrors the base disallow rules (a crawler obeys only its most-specific group, so admin/api paths were previously left crawlable), and the AdSense crawler `Mediapartners-Google` is now explicitly allowed.
- The site now serves a valid `ads.txt` declaring the authorised AdSense publisher, resolving the “authorised sellers” warning that appears when the ad code is present but ads.txt is missing.

### Fixed
- The duplicate `/page/{slug}` URL now 301-redirects to the clean `/{slug}` and is no longer emitted in the sitemap — previously every static page was reachable at two URLs (a soft-duplicate that dilutes ranking signals and trips content-quality audits). The clean slug is now the single canonical address.
- Legal, about and contact aliases consolidate onto one canonical URL with a 301 — language and spelling variants (e.g. `/privacy`, `/privacy-policy`, `/gizlilik`) used to each return 200 with their own canonical, signalling duplicate pages. They now redirect to the page’s real address and the canonical tag matches the redirect target.
- About/Contact pages that have no content now return 404 instead of an empty soft-200 — an alias with no template and no published page no longer renders a blank page whose canonical pointed at the homepage.

---

## [2.16.34] - 2026-06-16  ·  _Patch_
**Image SEO: In-Content Images in Schema & Sitemap**

### Improved
- Article structured data now lists every image, not just the featured one — the Article/BlogPosting `image` property is now an array of ImageObjects covering the featured image plus the images embedded in the article body, each resolved with width, height and caption from the media library. This gives the in-content images a real shot at ranking in Google Images.
- The image sitemap now includes in-content images — previously only the featured (and gallery) image of each post was submitted; the images inside the article body are now listed too, so Google can discover and index them.
- Fixed a silent bug where the featured image carried no dimensions in structured data — the media lookup queried a non-existent column, so width/height/caption were always dropped. Image objects now include their real dimensions.

---

## [2.16.33] - 2026-06-11  ·  _Patch_
**SEO: Archive Canonicals, Unique Titles & Schema Fixes**

### Improved
- The homepage FAQ is now eligible for rich results — FAQPage structured data is emitted from the marketing site’s FAQ section.

### Fixed
- Category, tag and author pages now point their canonical to themselves — in the travel theme these archive pages were inheriting the homepage’s canonical, title and description, which told search engines they were duplicates of the home page and effectively dropped them from the index. They now emit their own canonical URL, a unique title and description, and correct rel=prev/next for pagination.
- Every page now has a unique title and meta description — the recipes and finance themes were falling back to the site name on all pages (and recipes single posts had no meta description at all). Titles and descriptions now come from the page’s own content.
- The finance theme showed a hard-coded “FinancePro” heading regardless of the site’s real name, and rendered a second H1 on article pages — both fixed (real site name, single H1 per page). The news theme’s duplicate H1 was also resolved.
- News article structured data is now generated by the central engine — replacing an older version that referenced a missing logo file and could emit an invalid date, so news articles now carry correct Article/NewsArticle schema with the configured logo.

---

## [2.16.32] - 2026-06-11  ·  _Patch_
**PageSpeed: Responsive Images, Accessibility & Security Headers**

### Improved
- Images now download at the size they are displayed — the responsive image engine was emitting wrong width descriptors, so browsers fetched the 1600px version into ~800px slots. Descriptors now match the real variants (800/1600) and the size hint reflects the actual layout, cutting roughly 500 KiB from a typical page. Tip-card and recipe-card covers, which shipped a single full-size source, now serve responsive variants; continent illustrations were resized to their display size and the footer logo serves AVIF/WebP.
- Accessibility fixes across the travel theme and marketing site — section labels, hero chips and the newsletter button use an accent that meets WCAG AA contrast; decorative continent images no longer repeat adjacent link text; tip “Read” links carry the article title for screen readers; footer headings follow proper heading order.
- Smoother homepage animation — the step progress bar animates with a compositor-friendly transform instead of width, and the FAQ accordion no longer triggers a forced reflow on open.

### Security
- Content-Security-Policy now declares `script-src` and a Cross-Origin-Opener-Policy header is sent — script sources are restricted to the site itself plus the required Google advertising, analytics and font origins, closing the “missing script-src / COOP” findings without affecting ads.

---

## [2.16.31] - 2026-06-11  ·  _Patch_
**Security Hardening from a Full Code Audit**

### Security
- Hardened the content scheduler's status filter — it now uses a strict allow-list and a parameterized query.
- The post listing helper now enforces a column allow-list — sort field, direction and limits are validated and type-cast before they touch the query.
- The automation webhook secret falls back to an installation-unique key — when no webhook secret is configured it is now derived from the per-install security key instead of a guessable time-based value.

---

## [2.16.30] - 2026-06-11  ·  _Minor_
**Publisher Catalog & Backlink Opportunities, Verified for 2026**

### Improved
- The Backlink Opportunities module now lists real, verified programs — every niche grew from a couple of search shortcuts to 10-19 named opportunities checked live in 2026: Source of Sources and the relaunched free HARO, unlinked-mention reclamation, Lonely Planet Correspondents, BoardingArea, Matador Creators, foodgawker, mindbodygreen, the Plutus Awards, CryptoPanic, BlogPaws, Google/Bing/Apple business listings and more — each with priority, effort, and a concrete first step.
- The News Publishers catalog was re-verified for 2026 — Apple News (ANF, four countries), Flipboard (program closed; magazine + bookmarklet path documented), SmartNews and NewsBreak requirements updated; Bundle and SQUID added as open application channels; Pocket and Yandex Dzen removed.

---

## [2.16.29] - 2026-06-11  ·  _Minor_
**Brand Consistency, robots.txt Compliance & Full Turkish Admin**

### Improved
- The Turkish admin is now fully Turkish — dozens of hardcoded English labels were localized across the post editor (Recipe/LocalBusiness schema fields), backups schedule, comment replies, duplicate finder, media upload, banner manager, theme customizer, user profiles and the traffic plugin menu (now "Hızlı İndeksleme", "Anında Bildirim", "RSS Beslemesi", "Backlink Fırsatları", "Tarayıcı Bildirimi"). The English admin remains fully English.

### Fixed
- robots.txt now passes Bing validation — the non-standard `Host:` directive (a legacy Yandex extension that Bing flags as an error) was removed from the generated robots.txt on every site.
- The brand reads "jekcms" everywhere — a repo-wide sweep replaced every wrong-case variant across emails, feeds, installer screens, API docs, theme metadata, user-agent strings and comments. License-key format and code identifiers are untouched, so nothing breaks.

---

## [2.16.28] - 2026-06-11  ·  _Patch_
**Proper-Noun Anchors in Internal Linking**

### Improved
- Auto internal linking now recognises single-word proper nouns — place, brand and topic names such as a city or a dish (capitalised, 5+ letters) can now become link anchors, not just multi-word phrases. Lowercase generic words stay excluded, so the links remain relevant. This noticeably improves internal linking on niche sites (travel, food, local guides) where titles are often a single proper noun.

### Fixed
- Fixed the content-import wizard showing the "External authority links" label in English on a Turkish admin (it now follows the admin UI language).

---

## [2.16.27] - 2026-06-11  ·  _Minor_
**Smarter Internal Linking & E-E-A-T Outbound Links**

### Added
- External authority links in the content generator — the content-queue import wizard can now request a set number (0–5) of in-content outbound links to high-authority, non-competitor sources. When enabled, the AI prompt weaves them naturally into the body on descriptive anchors (never a "Sources" list), strengthening E-E-A-T.

### Improved
- Auto internal linking now waits for a real library — on a brand-new site there is nothing useful to link to, so auto-linking stays dormant until a configurable minimum number of published posts exists. The Auto Linker screen explains the threshold and shows current progress. As before, only published posts are link targets — queued/scheduled content is never linked.

---

## [2.16.26] - 2026-06-11  ·  _Patch_
**Pinterest Production Setup Instructions**

### Improved
- Clearer Pinterest go-live instructions — after Pinterest grants Standard access, the setup guide now tells you to remove the existing connection and connect again in Production mode, instead of using plain Reconnect (which can silently stay in Sandbox).

---

## [2.16.25] - 2026-06-10  ·  _Patch_
**Admin Customer Detail Fix**

### Fixed
- The customer detail screen in the admin panel opens reliably again — orders, licenses, invoices, support tickets and internal notes loaded with queries that did not match the production database, so the page returned a server error. Every section now reads the live schema correctly, and the customer create/edit forms save address details to the right fields.

---

## [2.16.24] - 2026-06-10  ·  _Patch_
**Clearer Product Positioning Copy**

### Improved
- jekcms is now described the same way everywhere — a next-gen smart CMS that installs on any PHP + MySQL hosting. The vague "self-hosted" label (which could read as if hosting were included) and the inaccurate "plugin-free" label were removed from the homepage, the WordPress-alternative page, site metadata and structured data.

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
- Payment webhook is now fail-closed — the iyzico webhook now rejects any unsigned or invalid-signature event (matching the Stripe gateway) before an order can be marked paid
- CSRF enforcement extended to GET admin actions — central CSRF enforcement now also covers authenticated GET action handlers (delete/toggle/activate)
- API input is column-whitelisted — the categories/tags update endpoints now accept only known fields
- SVG uploads disabled — SVG is no longer an allowed upload type; standard image formats are unaffected
- SSRF guards added to server-side fetchers — bulk-import and remote content-image fetching now validate the URL against private/loopback/metadata ranges and no longer follow redirects
- Customer portal forms fixed — the CSRF token field referenced a non-existent method (so it rendered empty); corrected to the proper token, and a status parameter in pagination links is now URL-encoded
- Removed a leftover temporary password-reset utility from the web root

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
- Client IP detection is now trustworthy for blocking — forwarded headers are accepted only when they carry a public IP, so the address used for IP blocking is reliable
- Redirect Manager blocks dangerous redirect schemes — javascript:/data:/vbscript: targets are refused at emit time
- Admin error messages no longer leak internals — Security Center and Redirect Manager now show a generic message and log the detail
- Cross-domain Sitemap line removed from the shipped robots.txt fallback — robots is served dynamically with the site’s own domain; the static fallback no longer carries a hardcoded foreign domain
- Google Console snippets can no longer double-inject — the head injector is guarded against firing on both head hooks
- Removed the misleading dead Pinterest-template dropdown in Social Publishing settings (it was never read)

---

## [2.16.11] - 2026-06-04  ·  _Patch_
**Deep Audit Fixes — CSRF Enforcement, Cache, SEO & Systems**

### Fixed
- CSRF protection is now enforced centrally across the admin — validation blocks state-changing authenticated requests centrally (clean 419, JSON for AJAX) without affecting public forms or page rendering
- "Clear Cache" buttons work again — they called a method that did not exist and fataled (purging nothing). Added the missing prefix-delete method and hardened the handler
- Sitemap index no longer miscounts pages as posts — the posts-sitemap presence/lastmod now filter on post type, fixing false "empty posts sitemap" and wrong freshness signals
- Update manifest hash guard now fully active — the signed update manifest exposes the core package hash under the field the client checks
- Social Publishing "Hold for approval" no longer silently stops publishing — held items now appear in the queue with one-click Approve / Approve-All / Cancel actions
- Traffic & Distribution now verifies TLS — IndexNow/WebSub/Web-Push calls now enforce certificate verification

---

## [2.16.9] - 2026-06-04  ·  _Patch_
**Security Center Now Matches the Admin Design System**

### Fixed
- The Security Center looked disconnected from the rest of the admin — it shipped its own stylesheet with hardcoded light-mode colors (white cards, grey borders) instead of the admin’s shared design tokens, so it ignored dark mode and its tabs/cards/tables didn’t match the other panels. Every color now uses the admin theme variables, so it adapts to dark/light and looks like one consistent product. Status indicators keep a subtle tinted badge instead of solid blocks, and the brand wordmark was corrected to lowercase

---

## [2.16.8] - 2026-06-04  ·  _Patch_
**Strip Byte-Order Marks From Core Files — Fixes Admin Layout & AJAX**

### Fixed
- Admin pages no longer render with broken styling — several core PHP files (bootstrap, constants, helpers, theme functions) carried an invisible UTF-8 byte-order mark (BOM) before their opening tag. That BOM was emitted before the document’s doctype, which forced browsers into "quirks mode" and broke list/table layouts across the admin. The BOM has been stripped from every PHP file across every installation
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
- Payment webhooks now fail closed (Stripe + iyzico): an order is marked paid only on a valid signed webhook, and the paid amount is verified against the order total
- Admin payment/customer/order pages now require admin role; maintenance scripts locked to CLI; session cookie set to `SameSite=Lax` (fixes being logged out when returning from external links)

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
**A Homepage That Names What jekcms Replaces**

### Improved
- The homepage says what you actually get — instead of an abstract feature list, it names the tools jekcms replaces (analytics, SEO, backup, security, two-factor login, redirects, image optimisation, caching) so you can compare against what you pay for today.

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
- Newsletter admin link corrected — the Newsletter plugin manifest pointed its admin page to a non-existent path; corrected so the dashboard opens from the plugin manager (the sidebar entry still requires the plugin to be activated)
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
- Removed the redundant static JSON and Google Sheets format reference blocks — the Assistant already generates a ready-to-use example, so the extra boilerplate only added clutter. Applied across every installation

---

## [2.3.0] - 2026-05-18  ·  _Minor_
**Reliability, Security & Always-On Delivery**

### Added
- Two-Factor Authentication (TOTP) — Modern QR setup card in every site's Security settings. Scan with Google Authenticator / Authy / 1Password; self-hosted QR (no third party), with a manual key fallback. Login enforcement is fail-open by design — a 2FA glitch can never lock you out
- Zero-downtime auto-deploy — Updates now reach your site automatically within minutes of a release, over HTTPS, with a health check afterwards. No manual uploads, no SSH, no lockouts

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
- Centrally managed installations carry a marker that blocks self-update so their version never drifts; packages shipped to customers omit the marker, so your own self-update is unaffected

---

## [2.1.3] - 2026-05-18  ·  _Patch_
**Security Hardening & Update Integrity**

### Fixed
- Critical: SSRF blocked — Server-side image fetch (media-from-URL) now allows only http/https public hosts; private/loopback/link-local and cloud-metadata addresses are rejected, redirects disabled, size-capped
- High: Markdown XSS blocked — Link/image URLs in content are scheme-allowlisted; `javascript:`, `data:`, `vbscript:` and protocol-relative URLs can no longer reach `href`/`src`
- High: Cross-site request hardening — State-changing requests now also enforce same-origin (Origin/Referer) on top of the CSRF token, covering all admin action pages at once
- SVG upload XSS blocked — Uploaded SVGs containing scripts, event handlers, foreignObject, external refs or XML entities (XXE) are rejected; static SVGs still allowed
- Update integrity mandatory — Updates without a verified SHA-256 are refused; manual ZIP apply is off by default unless the official hash is provided; developer-license localhost detection now requires a real loopback connection

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
- Turkish slug generation fix: `generateSlug()` now properly transliterates ç, ğ, ı, ö, ş, ü across all sites
- `fix-slugs.php` utility script for repairing existing corrupted Turkish slugs in production databases

### Fixed
- robots.txt files had unresolved `{{SITE_DOMAIN}}` placeholders in affected sites
- CSP header in production was blocking Google Analytics, AdSense, and Facebook Pixel domains

---

## [1.3.1] - 2026-01-24  ·  _Patch_
**Critical SEO Fix, Multi-Site Template & Documentation**

### Added
- Dual-environment configuration: `.env` (local development) and `.env-production` (live server) with automatic detection based on hostname
- Standard error pages: 400, 401, 403, 404, 500, 502, 503 with consistent branding
- Maintenance mode page (`maintenance.php`) with countdown timer
- Standardized `.htaccess` with GZIP compression, browser caching (1 year for static assets), security headers, and URL rewriting
- Complete deployment documentation: architecture guide, SEO checklist, responsive images reference, upgrade instructions

### Fixed
- Critical: Removed `X-Robots-Tag: noindex` HTTP header that was accidentally blocking all Google indexing across production sites
- Admin content queue retry: `attempts` counter now resets to 0 when a failed task is re-queued
- Removed obsolete Pinterest sharing code from post editor panel
- Removed e-commerce menus (Sales, Customers) from blog-only site admin panels — these belong to the storefront, not to a blog installation
- Synchronized missing AJAX endpoints (comment, newsletter, comment-like) across all sites

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
