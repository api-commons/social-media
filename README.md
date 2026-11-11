# Social Media

The common social-media vocabulary -- the social accounts and profiles that publish, the posts they publish and schedule, the comments on those posts and the analytics that measure them -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Social Media, Social, Social Media Management, Social Networking, Creator Economy, Influencer Marketing, Social Listening in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| social_account | 22 | 21 | id 52% | profiles 12, profile 12, creators 5, influencers 2 |
| post | 45 | 39 | id 74%, text 69%, created_at 64%, platform 51% | posts 38, post 9, tweets 9, statuses 5 |
| social_comment | 20 | 15 | id 80%, author_id 53%, created_at 53%, text 53% | comments 19, replies 4 |

Cohort: 118 providers with harvested OpenAPI, 53 crosswalks. Of the providers exposing a social_account: 41% create, 77% list, 32% fetch, 9% update, 0% delete. Generated 2026-11-10 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A post agrees on id, text and created_at across networks (X, Mastodon-compatible servers, LinkedIn) and the publishing tools that schedule onto them.
- A comment agrees on id, author, text and created_at -- the same core as a post, one level down.
- A social account agrees on nothing outright: networks expose a user, publishing tools a connected channel, and creator platforms an influencer profile.

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

- A social account is `/social-accounts`; profiles, connected channels, creators and influencers all count.
- Tweets, statuses and publications beneath a social path are posts; newsletters are not.
- Post analytics were measured and dropped: too few providers, no shared metric names.
- Duplicates merged: Lithium and Spredfast into Khoros, Mavrck into Later, Opus into OpusClip, Impact.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
