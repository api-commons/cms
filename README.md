# Content Management

The common content-management vocabulary -- the content types that define structure, the entries written against them, the pages and posts a site publishes, the media assets they embed and the locales they are translated into -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Content Management, Headless CMS, CMS, Content Management System, Web Content Management, Digital Experience Platform in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
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
