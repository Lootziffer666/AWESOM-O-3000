# AWESOME_ILLEGAL_TO_KNOW — V2 Staging Package

**State:** Adapting / Recovery Build  
**Generated:** 2026-05-13 02:34 local session  
**Purpose:** Recover the missing resources from the original source bundle and prevent silent loss.

## What changed from V1

V1 over-curated too aggressively. This staging pass uses a stricter rule:

> Every extracted resource must land somewhere: Main, Caution, Needs Verification, Backlog, Source Only, or Excluded.

## Package contents

- `AWESOME_ILLEGAL_TO_KNOW.md` — expanded public-facing Awesome List.
- `RESOURCE_INVENTORY.md` — complete known resource inventory with status.
- `RESOURCE_INVENTORY.csv` — machine-editable inventory.
- `EXCLUDED_DANGEROUS_OR_ILLEGAL.md` — individual exclusion list for source cleanup.
- `NEEDS_VERIFICATION.md` — candidates that need link/product verification.
- `OPTIONAL_BACKLOG.md` — legitimate but non-core/supporting candidates.
- `SOURCE_ONLY_REFERENCE_DOMAINS.md` — auto-extracted domains used mostly as citations/sources.
- `SOURCES_AUDIT.md` — extraction and consolidation notes.
- `DAILY_ROUTINE_EXAMPLES.md` — workflow examples using the V2 resource set.
- `QUALITY_GATE_REPORT.md` — status counts and remaining risks.
- `MANIFEST.json` — generated counts and file list.

## Current counts

- Total inventory rows: **422**
- Main list candidates: **117**
- Caution entries: **32**
- Needs verification: **24**
- Backlog/supporting: **109**
- Source-only/reference domains: **119**
- Excluded: **21**

## Important limitation

This staging pass consolidates source content and performs safety classification. It does **not** claim that every current URL is live today. Items marked `needs` must be verified before publication.
