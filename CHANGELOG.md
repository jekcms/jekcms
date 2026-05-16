# jekcms — Changelog

All notable changes to jekcms. This file is generated from a single
source of truth and mirrors the public changelog at https://jekcms.com/changelog

_Do not edit by hand — edit `marketing-includes/changelog-data.php`, then run_
_`php tools/gen-changelog-md.php` and commit._

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
