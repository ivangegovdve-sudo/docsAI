# AGENTS.md - docsAI Working Guide

This repository is intended to become the dedicated home for documentation intelligence products. Treat it as the future standalone repo for docs search, abbreviations, glossary tooling, and source ingestion.

## Goal

- make this the real home for the LLM documentation database and abbreviation / glossary search products
- split docs-centric tooling out of Forest HUB when the standalone repo is ready
- build a trustworthy docs intelligence system with safe ingestion, structured search, and embeddable surfaces

## Current Idea And Progress

- Intended purpose:
  the future repo for the current Forest HUB `LLM Platforms DB` and `AI_INIT` / abbreviation search work
- Current state:
  effectively empty
- Progress level:
  concept plus migration target, not implementation

## Product Scope

- docs source registry
- safe ingestion and refresh workflows
- searchable LLM platform database
- abbreviations and glossary search
- embeddable search widgets
- future documentation observability and source health tooling

## Initial Setup Requirements

- start with a real project skeleton instead of ad hoc files
- recommended initial stack:
  Python 3.11+ or 3.12+
  FastAPI
  SQLite first, Postgres later if needed
  static-first frontend or a minimal web UI
- create at minimum:
  `README.md`
  `.env.example`
  `backend/`
  `web/` or `frontend/`
  `data/`
  `tests/`

## Environments

- local development:
  split local frontend + local API
- staging:
  recommended once ingestion and search exist
- production:
  later, only after source-safety, rate limits, and persistence are solid

## Dependencies

- backend framework:
  FastAPI
- persistence:
  SQLite first, Postgres later if the product grows
- ingestion:
  safe HTTP fetching, parsing, and snapshot storage
- optional later dependencies:
  vector search, embeddings, queueing, scheduled jobs, auth

## Backend Need

- backend required:
  yes
- likely backend shape:
  FastAPI API plus ingestion jobs and persistent storage
- frontend relationship:
  the frontend should be a thin consumer of the docs/search APIs rather than containing all logic inline

## Backend Development Plan

1. Define the data model:
   source, fetch run, document, section, tag, glossary term, abbreviation, embed config.
2. Port the current safe-ingestion lessons from Forest HUB without weakening SSRF protections.
3. Build source list, ingest, search, and document detail APIs first.
4. Migrate the glossary / abbreviation data and search behavior next.
5. Add scheduled refreshes, source health tracking, and admin tools after core search works.
6. Add auth only if editing or multi-user administration becomes necessary.

## Migration Plan From Forest HUB

1. Keep the Forest HUB versions working during migration.
2. Move backend docs ingestion first.
3. Move `LLM Platforms DB` UI next.
4. Move `AI_INIT` and embed widget after the search API is stable.
5. When the standalone repo is strong enough, Forest HUB should link into docsAI instead of carrying the long-term ownership burden.

## End Goal

The end goal is a dedicated docs intelligence repo that owns docs ingestion, search, glossary lookup, and embeddable docs tooling, with Forest HUB acting as the launcher rather than the permanent home.
