# MOHX Agent Rules

## Mission
Rebuild Boursa Kuwait data from the internet from scratch. Do not repair or continue old processed datasets.

## Legacy-data boundary
- Old files may be read only to identify prior errors, source hints, regression tests, and coverage gaps.
- Never copy legacy values into new datasets.
- Mark all legacy inputs as `REFERENCE_ONLY__NON_AUTHORITATIVE__DO_NOT_INGEST`.

## Mandatory provenance
Every accepted record must include source URL, retrieved_at, publication_date when available, available_at when relevant, content_sha256, extraction_method, and validation_status.

## Data layers
- Raw immutable: exact downloaded bytes and request metadata.
- Bronze: extracted values without silent correction.
- Silver: normalized and entity-resolved.
- Gold: verified, source-backed, and quality-gated only.
- AI-ready: derived only from accepted records with leakage checks.

## Known regression guards
- Security code 418 must not resolve to TAMINV.
- Security code 242 resolves to TAMINV unless a newer official effective-dated source proves otherwise.
- Security code 832 resolves to ALFTAQA unless a newer official effective-dated source proves otherwise.
- Buy-In instruments never determine the ordinary listing market.
- Ticker is not a stable primary key.
- REITs, historical securities, and current ordinary equities remain separate universes.
- Template placeholders such as `{{row.close}}` are not market data.
- Shares outstanding and market capitalization are not Free Float.
- Raw prices and adjusted prices remain separate.
- No corporate-action adjustment factor enters Gold without official terms and prior-close reconciliation.
- No feature may use information after its prediction timestamp.

## Release rule
Build locally in the runner, run all hard gates, create manifests and SHA-256 hashes, then publish a closed release to Google Drive. Never update LATEST for a failed release.

## Secrets
Never commit OAuth tokens, service-account JSON, cookies, API keys, or credentials. Use environment secrets only.
