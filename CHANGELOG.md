# jekcms — Changelog

All notable changes to jekcms. This file is generated from a single
source of truth and mirrors the public changelog at https://jekcms.com/changelog

_Do not edit by hand — edit `marketing-includes/changelog-data.php`, then run_
_`php tools/gen-changelog-md.php` and commit._

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
- The Updates page is simpler by design: the in-panel ZIP install form was removed. Updates are applied with one click from the overview (or automatically); publishing releases is an operator-side pipeline, not something site owners juggle ZIPs for. Update history and release notes keep their own tabs.

### Fixed
- Fixed a server-side configuration blind spot dating back to the security hardening that moved secrets out of the web root: the update/license API could no longer load its database credentials, so the component update catalog silently served empty results. The API now searches the relocated secrets directory as well — theme and plugin updates published to the channel are actually visible to installations again, verified end-to-end against the signed manifest.

---

## [2.49.1] - 2026-07-23  ·  _Patch_
**Updates Page Reorganized into Tabs; Package Install Stays Visible (Locked) on Managed Sites**

### Improved
- The System Updates page now uses the same tabbed layout as Settings: Overview (status strip + available updates + installed components), Install Package, History (updates + backups) and Release Notes each have their own tab, instead of one long scrolling page. The Overview tab shows a pending-update count badge.
- Package type selection on the install tab is now a visual card picker (Plugin / Theme / Core) with the SHA-256 field appearing only for core packages.
- On centrally-managed installations the Install Package tab is no longer hidden: it now explains why ZIP installs are disabled there and how an operator can deliberately enable them (JEK_ALLOW_SELF_UPDATE); with the flag set, the full install form is available with an overwrite warning.

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
- aria-hidden (and inert) are now applied only while the mobile panel is genuinely hidden on small screens, and removed on desktop where the navigation is visible and focusable. Also removed a redundant static aria-hidden="true" from the lifestyle theme mobile-nav so it can never leak into the desktop tree. Applies fleet-wide via the shared, cache-busted navigation script.

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
- One positioning sentence, everywhere: jekcms is a self-hosted CMS for publishers and agencies with built-in SEO and image optimization, running on standard PHP + MySQL hosting. The vague "Next-Gen Smart CMS" phrasing is gone from the homepage, metadata, structured data and the admin login — and so are claims we can't prove: "24/7 support" now reads as support actually works (e-mail, response within 24–48 business hours), "Enterprise Security" now names the real controls (2FA, CSRF protection, rate limiting), and the theme count says exactly 14. The n8n integration is described in one place, as what it is: content arrives as drafts and publishes only after your editorial approval. A security.txt contact file is now published as well.

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
- AI provider API keys are no longer stored in plaintext anywhere. The multi-key Gemini list and the flat provider key fields (OpenAI, Groq, Cohere, Claude) previously saved raw keys into the database and echoed them back into the settings form HTML. Keys are now encrypted with authenticated AES-256-GCM before they touch the database, the settings form shows only a masked hint and never echoes a stored key, and every consumer — content tools, cron, connection tests — reads through the same decryption gate. A one-shot migration converts existing plaintext records automatically on the next cron pass, verified end-to-end on a real database.
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
- Stored secrets are now protected with authenticated encryption. Encrypted values (AI provider keys, Google OAuth tokens) previously used AES-CBC without an integrity check, so a tampered ciphertext could not be detected. New values are written as versioned AES-256-GCM; existing records keep decrypting and migrate transparently as they are re-saved.
- The API's write authorization is now fail-closed: a user record with an empty or unknown role gets no write capabilities instead of inheriting full admin rights through a legacy fallback.
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

### Improved
- Fleet consistency checks now cover every managed site and every core file. Two sites were outside the drift gate and had silently fallen behind the core: seven admin screens (customers, invoices, orders, support tickets, billing settings) were guarded only by "must be logged in" instead of "must be an admin". They are back in line with the core, and the gate now watches them.
- Line endings are pinned to LF via .gitattributes. Without it the drift gate reported hundreds of phantom mismatches on Windows checkouts — noise a genuine drift could hide in.

### Fixed
- Auto-activated plugins now install their database tables on a fresh install. A plugin marked AutoActivate was switched on automatically, but its activate.php — which creates the tables — only ever ran when you toggled the plugin by hand in the admin. On a brand-new install Newsletter therefore appeared active while newsletter_campaigns, email_templates, newsletter_queue, newsletter_clicks and email_logs were never created, and the Campaigns screen died with a fatal error. Activation now runs once per plugin version, is idempotent, adds no query on the hot path, and repairs installations that are already in the broken state on their next request. If one plugin fails to install its schema, the site stays up and the attempt is retried.
- Author social links, the reader-facing editorial box and the similarity gate carry the fixes shipped since 2.41.0: social profiles were invisible on author archives in seven themes, and the similarity gate now uses roughly a quarter of the memory it used to on large sites (measured: 64MB → 16MB on a 2,000-post blog).

### Security
- The license activation endpoint is now rate limited (20 attempts per IP per hour). Heartbeat already had a limiter; activation did not, which left it usable as an unthrottled oracle for guessing license keys. The counter is per IP rather than per key, because an attacker tries a different key on every request.
- The release tooling no longer reads credentials from the git remote URL, and the secret preflight now scans .git/config as well — a token embedded in a remote URL is invisible to a tracked-files scan.

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
- The sample admin account seeded by a manual database import shipped with a known example password; the seed now ships with an unusable password hash, and the installer sets real credentials as before.

---

## [2.37.0] - 2026-07-10  ·  _Minor_
**Legal Pages Repaired and Expanded, Author Archives Fixed, Tag Indexing Made Consistent**

### Improved
- The default Cookie Policy was rewritten to be genuinely comprehensive in both languages: cookie categories with purposes, legal bases and durations in a table, first/third-party and session/persistent distinctions, named third parties with opt-out links, consent management and withdrawal, browser instructions, Do Not Track / Global Privacy Control, and a legal-basis section (KVKK on Turkish sites, GDPR/ePrivacy on English ones).

### Fixed
- The built-in legal page templates shipped with corrupted text in all 13 themes — Turkish characters and arrow symbols rendered as garbage ("â†’", "Ã‡erez") on fresh installs that had not saved their own legal pages. The templates were re-encoded and every character now renders correctly in both languages.
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
- The managed-install marker is now cryptographically signed and domain-bound, so it can no longer be forged to bypass license enforcement. Legitimate managed installs are unaffected.
- Operators now receive automatic alerts (email digest) for suspected redistribution, license clones, and installs that stopped verifying — detection no longer depends on manually opening a dashboard.

---

## [2.19.3] - 2026-07-08  ·  _Patch_
**License Enforcement & EULA Hardening**

### Improved
- License verification now reports the copy's distribution origin, so unauthorized redistribution of a licensed copy is detected automatically and surfaced in the operator's installs dashboard. Legitimate installs are unaffected.
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
- Renaming a published post now creates a 301 redirect automatically. Previously every slug change silently left the old URL as a 404 in Google until someone noticed and added a manual redirect — a fleet-wide Search Console audit found exactly this pattern in the wild. The redirect is created on save, existing chains pointing at the old slug are re-pointed at the new one, and duplicate sources are never inserted.
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
- Closed a SQL injection in the content scheduler — the status filter on the scheduler screen now uses a strict allow-list and a parameterized query, so a crafted filter value can no longer reach the database.
- The post listing helper now enforces a column allow-list — sort field, direction and limits are validated and type-cast before they touch the query, removing a latent injection path for themes and plugins.
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
