# Content Management

The common content-management vocabulary -- the content types that define structure, the entries written against them, the pages and posts a site publishes, the media assets they embed and the locales they are translated into -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Content Management, Headless CMS, CMS, Content Management System, Web Content Management, Digital Experience Platform in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| content_type | 6 | 6 | id 67%, name 67%, fields 50% | content-types 4, contenttypes 2, content_types 1 |
| entry | 6 | 6 | id 100%, created_at 83%, updated_at 67%, locale 50%, name 50% | entries 4, items 2, stories 1 |
| page | 16 | 14 | id 93%, name 93%, created_at 50% | pages 14, page 3 |
| post | 12 | 11 | id 82%, name 73%, created_at 64%, status 64%, body 55%, tags 55%, updated_at 55% | posts 6, blogposts 2, post 2, article 1 |
| asset | 21 | 19 | id 95%, name 84%, created_at 74%, updated_at 63% | assets 14, media 5, asset 4, uploads 2 |

Cohort: 73 providers with harvested OpenAPI, 36 crosswalks. Of the providers exposing a content_type: 33% create, 100% list, 67% fetch, 17% update, 17% delete. Generated 2026-11-10 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A post agrees on id, title, status, body, tags and dates: WordPress set the shape of a blog post and the rest of the market kept it.
- An asset agrees only on id, name and dates; MIME type falls just short. A CMS asset is a file, but CMSs describe the bytes less consistently than storage APIs do.
- Headless CMS is barely represented (6 providers each for content types and entries): the leading headless platforms either publish GraphQL or no OpenAPI the catalog holds.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Content and Publishing are not cohort tags: they cover media companies and news as much as content-management software.
- A page and a post are separate concepts: pages are a site's structure, posts its chronological content, and the measured cores differ.
- Stories (Storyblok) and items beneath a collection (Webflow) are entries; Box's collection items are files and excluded.
- Articles and blog posts are posts.
- Duplicates merged: Confluence, Webflow, NewsCred into Optimizely.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
