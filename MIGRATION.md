# A complete website migration example

[English](MIGRATION.md) | [简体中文](MIGRATION.zh-CN.md) | [日本語](MIGRATION.ja.md) | [繁體中文](MIGRATION.zh-HK.md)

The example moves `/old-contact.html` to `/contact/`, merges `/company-profile.html` into `/about/`, and retires `/expired-campaign/`. These are invented paths. The work is complete only after the deployed responses and destination content have been checked.

## 1. Choose the outcome before writing a rule

Use [the URL inventory](url-inventory.csv). Record the old URL, intended action, final destination, reason, owner and observed result. Keep a useful page at its existing URL when possible. Redirect a moved page to its relevant replacement. A retired page with no suitable replacement should return an appropriate 404 or 410 response instead of a generic homepage redirect.

Keep campaign parameters when they still have a purpose; remove obsolete parameters through a deliberate rule. Paths, case, query strings and trailing slashes must be reviewed separately. The mapping checker treats them as different URLs.

## 2. Export only the actual redirects

```text
/old-contact.html	/contact/
/company-profile.html	/about/
```

The separator is a tab. Do not include a header, the other inventory columns, unchanged pages, or 404/410 decisions. [redirect-map.tsv](redirect-map.tsv) is a ready-to-run example.

Clone [the local checker](https://github.com/awesomellm/redirect-map-checker/blob/main/README.md), then run this command from its directory with the path to your exported file:

```sh
node check.mjs ../website-migration-kit/redirect-map.tsv https://example.com
```

Resolve loops, conflicting destinations and intermediate hops. Review external destinations explicitly. A clean graph does not establish that a server is serving those rules.

## 3. Configure the actual hosting layer

Use [the configuration recipes](https://github.com/awesomellm/redirect-map-checker/blob/main/DEPLOYMENT.md) for Cloudflare, Nginx or Apache. Use the same exact path and final destination as the approved inventory. Keep specific rules ahead of broader matching rules. Test in a preview environment, preserve the previous configuration, and assign a rollback owner.

Update internal links, canonical URLs, navigation, language switches and sitemap entries to point directly to final pages. A redirect is a recovery path for old links, not a reason to keep using them throughout the new website.

## 4. Verify a GET response after deployment

```sh
curl -sS -D - -o /dev/null 'https://example.com/old-contact.html?utm_source=test'
curl -sS -L --max-redirs 5 -D - -o /dev/null 'https://example.com/old-contact.html?utm_source=test'
```

The first command exposes the initial status and `Location`; the second exposes the chain. Replace the example domain with a site you operate. Check the permanent status, intended query handling, final 200 response and relevant destination content. Check the retired path separately. Also exercise the destination on a phone and submit an agreed test inquiry to a receiver you control.

## 5. Record acceptance and follow-up

Use [the launch checklist](launch-checklist.csv), [inquiry acceptance](inquiry-acceptance.csv) and [tracking plan](tracking-plan.csv). Record the tested URL, time, result, evidence and owner. Immediately inspect important old paths, navigation and receiving systems. During the following days and weeks, review actual 404s, sitemap processing and Search Console indexing for the affected pages. Compare full reporting windows; a short fluctuation is not proof of success or failure.

## 6. Keep the handover usable

Deliver [the handover checklist](handover-checklist.csv), the approved inventory, deployed rules, test results and rollback steps. The business should know who controls the domain, hosting, content and inquiry receiver. This tutorial plans and checks a migration; it does not deploy rules or guarantee search rankings.

[Google's site migration guidance](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes?hl=en) · [ZequnWeb](https://zequnweb.com/)
