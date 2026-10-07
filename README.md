<div align="center">

# jekcms

**A self-hosted CMS for blogs, news and review sites, with SEO and image optimisation in the core.**

[![Website](https://img.shields.io/badge/site-jekcms.com-2563EB)](https://jekcms.com)
[![Changelog](https://img.shields.io/badge/changelog-live-059669)](https://jekcms.com/changelog)
[![Free edition](https://img.shields.io/badge/free%20edition-1%20site-7c3aed)](https://jekcms.com/pricing)

</div>

---

jekcms is a content management system you run on your own hosting. The parts
most WordPress sites put together from plugins are part of the core: JSON-LD
schema, canonical tags, XML sitemaps, hreflang for bilingual sites, AVIF and
WebP conversion on upload, and full-page caching.

It is plain PHP 8 with MySQL or MariaDB. There is no Composer, Node or build
step, so it runs on ordinary shared hosting.

> **This repository holds documentation and release notes. jekcms is not open
> source.** There is a free edition for one site with no time limit.

## Try it

- Admin panel demo, no signup: **https://demo-en.jekcms.com/admin/**
- Themes, each one a live demo: **https://jekcms.com/demos**
- Free edition and pricing: **https://jekcms.com/pricing**
- Documentation: **https://jekcms.com/docs**

## What is in the core

- **SEO:** JSON-LD schema per post, canonical URLs, XML sitemaps, hreflang,
  redirect manager, automatic internal linking, broken link checks, IndexNow
- **Images and speed:** AVIF/WebP conversion on upload, responsive srcset,
  full-page cache, critical CSS
- **Publishing:** modern editor, revisions, scheduling, editorial approval and
  a check that runs before a post goes live
- **Migration:** WordPress import for posts, pages, media and comments
- **Security:** two-factor sign-in, security center, daily backups with
  restore, signed updates that roll back by themselves if the site starts
  returning server errors
- **Integration:** REST API and outgoing webhooks
- **Themes:** 15 ready-made themes (news, finance, tech, travel, recipes and
  more), adjustable from the admin panel

Paid licences add modules such as newsletter, web push, form builder, digital
downloads and a social publisher. The full list is on
[jekcms.com/features](https://jekcms.com/features).

## Requirements

- PHP 8.0 or later
- MySQL 5.7+ or MariaDB 10.3+
- Apache or LiteSpeed

Install by uploading the installer to your web root and finishing the setup
wizard in the browser.

## Licensing

- **Free edition:** one site, no time limit, three themes, all updates. Keeps
  a "Powered by jekcms" line; documentation instead of support.
- **Paid licences** are yearly and never renew automatically. If a licence
  lapses, the site keeps running on the free edition.

Prices: [jekcms.com/pricing](https://jekcms.com/pricing)

## Release history

[`CHANGELOG.md`](./CHANGELOG.md) mirrors the public changelog at
**https://jekcms.com/changelog**. Every release is also published under
[Releases](https://github.com/jekcms/jekcms/releases).

## Issues

Bug reports and feature requests are welcome in
[Issues](https://github.com/jekcms/jekcms/issues). For security reports, see
[SECURITY.md](./SECURITY.md).

---

<div align="center">
<sub>jekcms is an <a href="https://alfadizayn.com">ALFA Dizayn</a> brand.</sub>
</div>
