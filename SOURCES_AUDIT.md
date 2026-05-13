<!--
V2 STAGING PACKAGE
Generated from the provided DOCX source bundle.
This is a staging package, not a final repo commit.
Live link validation was not performed in bulk in this environment; use Status and Needs Verification gates before publishing.
-->

# Sources Audit

## Source bundle

- **NITW:** `Nützliche &quot;Illegale&quot; Webseiten Aufdecken.docx`
- **PPLX:** `Illegal_websites_perplexity.docx`
- **WFLOW:** `Workflow-Optimierung- Apps und Services.docx`
- **WFI:** `WEBSITES THAT FEEL ILLEGAL TO KNOW.docx`
- **DRE:** `Daily Routine Example.docx`

## Extraction passes

1. DOCX paragraphs and DOCX tables were extracted.
2. Explicit table rows were used as primary resources where available.
3. Markdown-style bold bullets and URL/domain mentions were cross-checked through raw domain extraction.
4. Known resources were deduplicated by normalized URL/domain or exact name.
5. Remaining raw domains were preserved as `source_only` instead of being deleted.

## Consolidation notes

- `Archive.is`, `Archive.today`, and `ArchiveTools` were split/normalized as archival tools, with paywall-bypass framing kept only as caution.
- `diagrams.net` and `draw.io` were merged.
- `ColorSpace` and `mycolor.space` were merged.
- `OpenLibrary` and `Open Library` were merged.
- `Unpaywall`, `Open Access Button`, `CORE`, `OpenStax`, `LibreTexts`, `DOAJ`, `PMC`, and `arXiv` are treated as legal open-access alternatives.
- Shadow libraries and direct paywall-bypass tools are not moved to backlog; they are explicitly excluded.

## Safety filter

Excluded categories: shadow libraries, paywall-bypass extensions/proxies, piracy indexes, darknet markets, carding, phishing, botnets, malware distribution, deceptive seeding tactics.

## Known limitation

Bulk live-link validation could not be completed inside this local staging environment. Items marked `needs` require current web validation before publishing.