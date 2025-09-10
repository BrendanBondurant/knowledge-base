# The Good Thing Podcast Transcript Chunking

## Quick Reference — Metadata Rules

| Field      | Purpose                                         | Format                                     | Human-Friendly? | Machine-Friendly? | Source of Truth    |
| ---------- | ----------------------------------------------- | ------------------------------------------ | --------------- | ----------------- | ------------------ |
| `topics`   | Main discussion themes for the chunk            | Title Case, spaces between words           | ✅               | ❌                 | Written per chunk  |
| `tags`     | Global, reusable categorization for all content | lowercase, kebab-case (graphql-federation) | ❌               | ✅                 | `tags_master.yaml` |
| `entities` | People, teams, products, standards referenced   | Canonical names or IDs                     | ❌               | ✅                 | `entities.json`    |
| `summary`  | One-sentence chunk summary                      | Plain English, ≤3 sentences                | ✅               | ✅                 | Written per chunk  |



## Governance Rules

- All tags must match entries in tags_master.yaml
- No ad hoc tags in individual files
- Adding a new tag requires updating `tags_master.yaml` and documenting it
- Each chunk must have at least one tag
- Keep topics readable for humans; keep tags consistent for machines
- Avoid pluralization drift (api vs. apis — pick one form)
- Avoid over-specific tags (use `ai-security`, not `ai-security-prompt-injection-v1`)

### Where to Find and Update the Master Tag List

The approved vocabulary for tags lives in the `tags_master.yaml` file at the root of this repository.

**Do not create tags directly in chunk files that aren't already in `tags_master.yaml`.**

#### To add a new tag:

1. Edit `tags_master.yaml` to include the new kebab-case tag
2. Run the tag validation script (`/scripts/validate_tags.md`) before committing (Doesn't exist yet)
3. Document the addition in the repo changelog
4. Pre-commit hooks will reject changes that contain invalid or missing tags

## Overview

This repository contains full transcripts of "The Good Thing" podcast, as well as "chunked" versions of each episode. The goal is to break down long podcast transcripts into smaller, structured, and metadata-rich chunks suitable for insertion into a knowledge base or for use in downstream applications (e.g., search, summarization, LLMs).

## Directory Structure

- `epXX-full.md`: The full, unprocessed transcript for episode XX
- `epXX/`: Directory containing chunked `.md` files for episode XX
- Each file represents a single chunk (a segment of the episode)

```
chunks/
  ep01-full.md
  ep01/
    ep01-01-intro-podcast-origins-tradeoffs.md
    ...
  ep02-full.md
  ep02/
    ep02-01-intro-retreat-norway.md
    ...
```

## What is a "Chunk"?

A chunk is a small, self-contained segment of the podcast transcript, typically corresponding to a single topic, story, or discussion segment. Each chunk includes:

- YAML frontmatter with rich metadata
- The verbatim transcript for that segment

### Example Chunk File

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
  - Engineering as tradeoffs
  - Co-host dynamic and format
  - First intro to Jens
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
```

```
00:00:01:18 - 00:00:19:19

Stefan

Ladies and gentlemen, welcome to an episode of The Good Thing, episode one, where we're...
```

## Chunking Instructions

### 1. Read the Full Transcript
Open the relevant `epXX-full.md` file. Read through the transcript and identify natural breakpoints—topic changes, new stories, or significant shifts in the conversation.

### 2. Define Chunks
- Each chunk should be coherent and self-contained (usually 2–8 minutes of audio, but use your judgment)
- Chunks should not be too short (avoid splitting every speaker turn) or too long (avoid 10+ minute blocks)

### 3. Create Chunk Files
For each chunk:

1. Create a new file in the appropriate episode directory (e.g., `ep04/ep04-01-topic-title.md`)

2. Add YAML frontmatter at the top, including:
   - `title`: Short, descriptive title for the chunk
   - `slug`: Unique identifier (e.g., `ep04-01-topic-title`)
   - `series`: Always "The Good Thing"
   - `episode`: Episode number
   - `chunk`: Chunk number (sequential, starting from 1)
   - `segment`: Short description of the segment
   - `timecode`, `start_time`, `end_time`: Use transcript timestamps
   - `speakers`: List of speakers in the chunk
   - `topics`: Bullet list of main topics discussed (Title Case, human-readable)
   - `tags`: Short, machine-friendly tags (lowercase, kebab-case) from `tags_master.yaml`
   - `entities`: People, companies, or products mentioned
   - `summary`: 1–3 sentence summary of the chunk (in plain English)

3. Paste the transcript for that segment below the frontmatter, preserving timestamps and speaker labels

### 4. Repeat
Continue until the entire episode is chunked. Each chunk should be a separate file.

## Metadata Field Rules (Detailed)

### Topics
**Purpose:** Human-readable description of discussion themes in the chunk.

**Format:**
- Title Case (e.g., GraphQL Federation, Wedding Preparation)
- Spaces between words; no hyphens or underscores
- 1–4 words preferred; avoid overly specific one-off phrasing unless essential

**Usage:** Used for browsing and human-facing displays.

### Tags
**Purpose:** Global, machine-friendly vocabulary for categorizing all content.

**Format:**
- Lowercase only
- Kebab-case: words separated by hyphens
- No special characters except hyphens
- Must be broad enough for reuse across multiple files

**Usage:** Pulled from `tags_master.yaml`.

## Why Chunk?

- **Improved search:** Smaller, topic-focused segments are easier to search and retrieve
- **Knowledge base ready:** Chunks can be indexed, summarized, or embedded for LLMs
- **Reusability:** Chunks can be referenced independently in other projects or tools