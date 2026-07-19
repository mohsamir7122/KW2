# MOHX — Fresh Boursa Kuwait Data Rebuild

Clean-room data engineering project for rebuilding Boursa Kuwait datasets from newly collected internet sources.

## Core rule

Legacy project files are `REFERENCE_ONLY__NON_AUTHORITATIVE__DO_NOT_INGEST`.

Only newly acquired data with source URL, retrieval timestamp, publication date, SHA-256, extraction method, and validation status may enter Bronze, Silver, Gold, or AI-ready outputs.

## Pipeline

1. Fresh source discovery
2. Raw immutable acquisition
3. Document and table extraction
4. Canonical entity history
5. Historical market data
6. Financial statements and disclosures
7. Corporate actions
8. Normalization and validation
9. Gold verified datasets
10. AI-ready, RAG, DuckDB, and release packaging

## Storage

The repository contains code, schemas, configuration, tests, and release manifests. Large datasets are published separately to Google Drive under `mohx/` after quality gates pass.
