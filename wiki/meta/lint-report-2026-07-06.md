---
type: meta
title: "Lint Report 2026-07-06"
created: 2026-07-06
updated: 2026-07-06
tags: [meta, lint]
status: developing
---

# Lint Report: 2026-07-06

## Summary
- Pages scanned: 54
- Issues found: 15 (real issues; 67 raw dead-link hits include ~52 false positives)
- Auto-fixed: 0
- Needs review: 15

## Orphan Pages

7 orphans found. 4 are acceptable (meta/fold artifacts by design), 3 need attention:

- [[methodology-modes]]: reference doc, no inbound links. Suggest: link from wiki-mode SKILL or index.md.
- [[transport-fallback]]: reference doc, no inbound links. Suggest: link from wiki-cli SKILL or CLAUDE.md.
- [[显微镜下的大明-精华帖]]: user-ingested ebook source, no inbound links. Suggest: link from index.md or create concept page linking back.

Acceptable orphans (by design):
- [[fold-k3-from-2026-04-23-to-2026-04-24-n8]]: fold artifact
- [[2026-04-10-backlink-empire-session]]: session log
- [[retrieval-benchmark-v1.7]]: benchmark report
- [[tiling-report-2026-04-24]]: tiling report

## Dead Links

67 raw hits. After analysis, ~52 are false positives (see Classification below). Real issues:

### Filename mismatch (1)
- `[[How does the LLM Wiki pattern work?]]` in 4 pages (Persistent Wiki Artifact, Query-Time Retrieval, Source-First Synthesis, hot.md, log.md). Actual file: `wiki/questions/How does the LLM Wiki pattern work.md` (no question mark). Fix: remove the `?` from wikilinks, or rename the file to include it.

### Missing concept page (1)
- `[[E-commerce SEO]]` in Claude SEO.md + session log. Suggest: create stub page or remove link.

### Test/example links (2)
- `[[Foo]]` and `[[notes/Foo]]` in DragonScale Memory.md and log.md. These are illustrative examples in documentation. Acceptable, but could be converted to code blocks to avoid false lint hits.

### False positive classification (52 hits, no action needed)
- **`#` heading references** (15 hits): `[[cherry-picks#N. ...]]` — target file `cherry-picks.md` exists in `wiki/concepts/`. Heading anchors, not dead links.
- **Path-style `_index` links** (12 hits): `[[concepts/_index]]` etc. — `_index.md` exists in each folder. Obsidian path-format wikilinks.
- **Non-.md targets** (5 hits): `[[Wiki Map]]` (canvas), `[[dashboard.base]]` (base file) — exist as non-markdown files.
- **Cross-directory refs** (6 hits): `[[mcp-setup]]`, `[[methodology-modes-guide]]`, `[[fold-template]]` — exist in `skills/` or `docs/`, not `wiki/`.
- **Skill name refs** (6 hits): `[[wiki-fold]]`, `[[wiki-mode]]`, `[[wiki-cli]]` — refer to skills, not wiki pages.
- **Historical session names** (5 hits): `[[Claude Canvas]]`, `[[Rankenstein]]` etc. in session logs — historical context, not page refs.
- **Template refs** (3 hits): `[[fold-template]]` in fold file — references skill template.

## Frontmatter Gaps

3 pages missing required fields:

- [[retrieval-benchmark-v1.7]]: missing `tags`
- [[transport-fallback]]: missing `tags`
- [[显微镜下的大明-精华帖]]: missing `status`, `tags`

## No Frontmatter

1 page:
- [[tiling-report-2026-04-24]]: auto-generated report, no frontmatter. Acceptable.

## Empty Sections

4 empty sections, all acceptable:
- `concepts/_index.md`: "Add new concepts here..." (template placeholder)
- `entities/_index.md`: "Add new entities here..." (template placeholder)
- `sources/_index.md`: "Add new sources here..." (template placeholder)
- `sources/_index.md`: "Transcripts" (empty by design)

## Address Validation

DragonScale addresses detected (`.vault-meta/address-counter.txt` exists). Counter peek: 3.
- `c-000001` on DragonScale Memory.md: valid
- `c-000002` reserved-unassigned (validation gap, acceptable per spec)
- No post-rollout pages missing addresses
- No counter drift

## Semantic Tiling

Skipped (ollama not running). To enable: `ollama pull nomic-embed-text` then re-run lint.

## Recommendations (priority order)

1. Fix `[[How does the LLM Wiki pattern work?]]` -> remove `?` in 5 pages (or rename file)
2. Add `tags` to 3 pages with frontmatter gaps
3. Link 3 orphan pages (methodology-modes, transport-fallback, 显微镜下的大明) from index or related pages
4. Create `[[E-commerce SEO]]` stub or remove the link
