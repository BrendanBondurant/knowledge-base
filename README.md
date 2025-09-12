# Knowledge Base Schema Overview

| Field            | Podcast Chunks                   | Blogs                             | Webinars                          | Notes |
|------------------|----------------------------------|-----------------------------------|-----------------------------------|-------|
| `type`           | `podcast-chunk`                  | `blog`                            | `webinar` or `webinar-chunk`      | Always explicit |
| `title`          | ✅                               | ✅                                | ✅                                | Human-readable |
| `slug`           | `epXX-YY-topic`                  | `YYYY-MM-DD-title`                | `YYYY-MM-DD-webinar-title`        | Unique ID |
| `series`         | `The Good Thing`                 | `WunderGraph Blog`                | `WunderGraph Webinars`            | Static per type |
| `date`           | Episode date                     | ✅ Publish date                    | ✅ Webinar date                    | |
| `episode`        | ✅ Episode number                 | `null`                            | `null`                            | **Use `null` explicitly** when not applicable |
| `chunk`          | ✅ Chunk number                   | `null` unless chunked             | `null` unless chunked             | |
| `segment`        | ✅ Short descriptive title        | `Full article` unless chunked     | Required if chunked               | |
| `timecode`       | ✅ `HH:MM:SS:FF – HH:MM:SS:FF`   | n/a                               | Optional                          | Use if timestamped |
| `start_time`     | ✅                                | n/a                               | Optional                          | |
| `end_time`       | ✅                                | n/a                               | Optional                          | |
| `speakers`       | ✅ List                           | Empty list `[]`                   | ✅ List                            | |
| `topics`         | ✅ Title Case                     | ✅                                 | ✅                                 | Human-facing |
| `tags`           | ✅ from `tags_master.yaml`        | ✅ from `tags_master.yaml`         | ✅ from `tags_master.yaml`         | No ad-hoc tags |
| `entities`       | ✅                                | ✅                                 | ✅                                 | People, products, orgs, standards |
| `summary`        | ✅ (2–5 sentence abstract)        | ✅ (2–5 sentence abstract)         | ✅ (2–5 sentence abstract)         | Neutral, factual |
| `faqs`           | Optional                          | Optional                          | Optional                          | Q&A retrieval |
| `canonical_url`  | Optional but recommended          | ✅ Required                        | ✅ Required                        | Public source URL |

---

## Governance Rules

- **Tags:** Must exist in `tags_master.yaml`. No ad-hoc tags in content files.
- **Add a new tag:**  
  1) Edit `tags_master.yaml` (kebab-case)  
  2) Validate (script TBD)  
  3) Document in changelog  
- **Nulls:** Use `null` explicitly for non-episodic fields (`episode`, `chunk`) in blogs/webinars.
- **Topics:** Title Case, readable; keep broad.  
- **Tags style:** lowercase, kebab-case; avoid over-specific variants.  
- **Consistency:** Same frontmatter order across files; summaries are neutral, 2–5 sentences.

---

## Overview

This repo stores:
- **Podcast chunks** of *The Good Thing* (time-coded, speaker-labeled, metadata-rich)
- **Blogs** (single-file by default; chunk only if sections are reused)
- **Webinars** (single-file or chunked like podcasts)

Designed for accurate search, LLM retrieval, and reuse.

---

## Podcast Chunking

### Directory Structure
- `epXX-full.md` — full transcript for episode `XX`  
- `epXX/` — directory of chunked `.md` files for episode `XX`  
- Each chunk is a separate file

**Filename format:** `epXX/epXX-YY-topic.md`  
**Slug format:** `epXX-YY-topic`

### Quick Metadata Reference
| Field | Notes |
|------|------|
| `series` | Always `The Good Thing` |
| `episode` | Integer |
| `chunk` | Integer, sequential |
| `segment` | Short, descriptive |
| `timecode` / `start_time` / `end_time` | Required |
| `speakers` | List of participants |
| `topics` | Title Case (human-friendly) |
| `tags` | From `tags_master.yaml` |
| `entities` | People/companies/products/standards |
| `summary` | 2–5 sentences, neutral |

### Example (Podcast Chunk)
```yaml
---
title: Podcast Origins and the Engineering of Tradeoffs
slug: ep01-01-intro-podcast-origins-tradeoffs
series: The Good Thing
episode: 1
chunk: 1
segment: Introduction and Show Philosophy
timecode: 00:00:01:18 – 00:02:32:04
start_time: 00:00:01:18
end_time: 00:02:32:04
speakers:
  - Stefan
  - Jens
topics:
  - Why the podcast is called "The Good Thing"
  - Engineering as Tradeoffs
  - Co-Host Dynamic and Format
  - First Intro to Jens
tags:
  - podcast-intro
  - engineering-philosophy
  - tradeoffs
  - graphql
entities:
  - The Good Thing
  - WunderGraph
  - GraphQL
  - Federation
  - Jens Neuse
  - Stefan Avram
  - Bjorn
summary: |
  Stefan introduces the podcast and its central theme of tradeoffs in engineering and life. The episode title is inspired by cofounder Bjorn's optimism. Jens is introduced as the co-host, with Stefan playing the facilitator role for technical discussions.
---

00:00:01:18 - 00:00:19:19
Stefan
Ladies and gentlemen, welcome to an episode of The Good Thing, episode one, where we're...
```

## Chunking Instructions
1. Read epXX-full.md and mark natural breakpoints.
2. Target 2–8 minutes per chunk; avoid >10 minutes.
3. Create chunk files in epXX/ with full frontmatter.
4. Paste transcript for that segment below frontmatter, preserving timestamps and speakers.
5. Repeat until the episode is fully chunked.

## Blogs in the Knowledge Base

Blogs are single-file by default. Chunk only if sections are reused independently (e.g., spec comparisons, benchmarks).

### Directory & Filenames
- Directory: /blogs/
- Filename: YYYY-MM-DD-title.md
- Slug: YYYY-MM-DD-title

## Blog Frontmatter (Required Fields)
| Field           | Notes                          |
| --------------- | ------------------------------ |
| `type`          | `blog`                         |
| `title`         | Full blog title                |
| `slug`          | `YYYY-MM-DD-title`             |
| `series`        | `WunderGraph Blog`             |
| `date`          | Publish date `YYYY-MM-DD`      |
| `author`        | Full name                      |
| `speakers`      | Empty list `[]`                |
| `episode`       | `null`                         |
| `chunk`         | `null` unless chunked          |
| `segment`       | `Full article` unless chunked  |
| `topics`        | Title Case                     |
| `tags`          | From `tags_master.yaml`        |
| `entities`      | People/products/orgs/standards |
| `summary`       | 2–5 sentences                  |
| `faqs`          | Optional                       |
| `canonical_url` | **Required**                   |

```yaml
---
type: blog
title: Cosmo Connect vs Apollo Federation vs GraphQL Federation
slug: 2025-09-09-cosmo-connect-vs-apollo-federation-vs-graphql-federation
series: WunderGraph Blog
date: 2025-09-09
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - API Architecture
  - Entity Layer
tags:
  - graphql
  - graphql-federation
  - apollo-federation
  - cosmo-connect
  - grpc
  - supergraph
  - schema-governance
entities:
  - Apollo Federation
  - GraphQL Federation
  - Cosmo Connect
  - Cosmo Router
  - Composite Schemas
summary: |
  Compares Cosmo Connect, Apollo Federation, and GraphQL Federation through the lens of an entity layer.
  Explains why a unified API layer matters, how batching and entity lookups differ (_entities vs @lookup vs gRPC),
  and when to choose Connect over GraphQL subgraphs. Frames tradeoffs for architecture, governance, and operations.
faqs:
  - q: What is the difference between Apollo Federation and GraphQL Federation?
    a: Apollo Federation extends GraphQL with entity types, @key directives, and the _entities field for batching. GraphQL Federation, defined by the Composite Schemas specification, keeps GraphQL vanilla and uses explicit directives like @lookup for composition.
canonical_url: https://your-site/blog/cosmo-connect-vs-apollo-federation
---
```

## Webinars
Treat webinars like podcasts with a different type. Chunk if long or highly reusable; otherwise one file.

### Directory & Filenames
- Directory: `/webinars/`
- If single file: `/webinars/2025-08-20-webinar-schema-collaboration.md`
- Chunked:
  - Directory: `/webinars/2025-08-20/`
    - `2025-08-20-01-intro-schema-collaboration.md`
    - `2025-08-20-02-governance-workflows.md`

### Webinar Frontmatter (minimum)
| Field                                  | Notes                                 |
| -------------------------------------- | ------------------------------------- |
| `type`                                 | `webinar` or `webinar-chunk`          |
| `title`                                | Webinar title                         |
| `slug`                                 | `YYYY-MM-DD-webinar-title`            |
| `series`                               | `WunderGraph Webinars` (optional)     |
| `date`                                 | Webinar date `YYYY-MM-DD`             |
| `episode`                              | `null`                                |
| `chunk`                                | `null` unless chunked                 |
| `segment`                              | Required if chunked                   |
| `timecode` / `start_time` / `end_time` | Optional, recommended if timestamped  |
| `speakers`                             | List of presenters                    |
| `topics`                               | Title Case                            |
| `tags`                                 | From `tags_master.yaml`               |
| `entities`                             | People/products/orgs/standards        |
| `summary`                              | 2–5 sentences                         |
| `faqs`                                 | Optional                              |
| `canonical_url`                        | **Required** (replay page or YouTube) |

## Rules

- Chunk webinars if > ~20 minutes or if sections will be reused.  
- Single-file webinars should still include `timecode` if you have it.  
- `canonical_url` should point to a replay page (not a storage bucket).

---

## Metadata Field Rules (Detailed)

### Topics (human-facing)
- Title Case; short and clear (1–4 words)
- No hyphens/underscores; use spaces
- Avoid overly specific one-offs

### Tags (machine-facing)
- Lowercase, kebab-case
- Must exist in `tags_master.yaml`
- Broad and reusable; avoid micro-variants

---

## Why Chunk?

- Better search and retrieval
- Cleaner reuse in marketing and docs
- Faster, more accurate LLM grounding

Keep chunks self-contained with strong summaries.
