# Website Migration Kit

Practical URL planning, project brief, and launch acceptance templates for website redesigns. The examples use fictional paths; replace them with your approved project data.

[Website redesign workflow](https://zequnweb.com/blog/website-redesign-checklist/) · [中文说明](README.zh-CN.md)

## Templates

| File | Purpose |
| --- | --- |
| [url-inventory.csv](url-inventory.csv) | Decide which pages stay, move, merge, or retire; record an owner and verification |
| [redirect-map.tsv](redirect-map.tsv) | Three direct redirect mappings compatible with the checker |
| [project-brief.csv](project-brief.csv) | Capture audience, scope, languages, inputs, integrations, and acceptance |
| [seo-deliverables.csv](seo-deliverables.csv) | Make each SEO deliverable observable and assign responsibility |
| [launch-checklist.csv](launch-checklist.csv) | Review content, redirects, indexing, forms, devices, and release ownership |

Traditional Chinese versions: [URL inventory](url-inventory.zh-HK.csv), [project brief](project-brief.zh-HK.csv), and [SEO deliverables](seo-deliverables.zh-HK.csv).

## How to use

1. Download the ZIP using **Code → Download ZIP**, or clone this repository.
2. Open the CSV files in a spreadsheet. Retain useful old URLs, select relevant replacements, and assign an owner to each decision.
3. Export only the old URL and destination for rows that actually redirect. Use tabs between the two columns, remove the header, and retain one mapping per line.
4. Review the map with the [Redirect Map Checker](https://zequnweb.com/tools/redirect-map-checker/) or its [local JavaScript version](https://github.com/awesomellm/redirect-map-checker).
5. Implement the rules on the host, then test the actual HTTP responses, destination content, internal links, and indexing settings.
6. Record form delivery, launch approval, rollback responsibility, and post-launch issues in the checklist.

**The multi-column CSV inventory is not checker input.** Keep and retire decisions must not be pasted into the checker. The included `redirect-map.tsv` is already two columns without a header.

## Limits

These are planning templates, not hosting configuration or a crawler. They do not validate production redirects or guarantee stable rankings. Do not send every retired URL to the homepage; choose a relevant replacement or an appropriate not-found response when no replacement exists.

## References

- [Google: Site moves with URL changes](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes)
- [ZequnWeb: Website redesign checklist](https://zequnweb.com/blog/website-redesign-checklist/)

## Contributing

Suggest a concrete missing decision, acceptance check, or example. Use synthetic data in public issue reports.

## Maintainer and license

Prepared by [ZequnWeb](https://zequnweb.com/), an independent B2B web design and development studio. Templates and documentation are available under the [MIT License](LICENSE).
