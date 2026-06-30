# Good AI-Assisted Research Methodology

> Last updated: 2026-06-30
> Status: Current

## Summary

High-quality AI-assisted research is evidence synthesis with AI as an auditable assistant, not an authority. The workflow should start with a scoped question and a reproducible search plan, prefer primary peer-reviewed literature and official methodology sources, document source selection and exclusions, use AI for retrieval support and structured comparison, and keep every substantive claim traceable to a cited source. This is a lightweight operational adaptation inspired by formal evidence-synthesis guidance; it is not a claim that routine workspace research is a full PRISMA- or Cochrane-compliant systematic review.

## Sources

- PRISMA 2020 statement: <https://www.prisma-statement.org/prisma-2020>
- EQUATOR PRISMA 2020 record and bibliographic metadata: <https://www.equator-network.org/reporting-guidelines/prisma/>
- Cochrane Handbook for Systematic Reviews of Interventions, version 6.5 (2024): <https://training.cochrane.org/handbook/current>
- PRISMA-S search-reporting extension, Systematic Reviews 2021;10:39: <https://systematicreviewsjournal.biomedcentral.com/articles/10.1186/s13643-020-01542-z>
- PubMed record for PRISMA-S, PMID 33499930: <https://pubmed.ncbi.nlm.nih.gov/33499930/>
- AHRQ Methods Guide for Effectiveness and Comparative Effectiveness Reviews: <https://www.ncbi.nlm.nih.gov/books/NBK47095/>
- University of Chicago Library CRAAP source-evaluation guide: <https://guides.lib.uchicago.edu/c.php?g=1241077&p=9082343>
- LitLLM: A Toolkit for Scientific Literature Review, arXiv:2402.01788v2 (2025): <https://arxiv.org/abs/2402.01788>

## Key Findings

### 1) Start with a protocol, not a pile of links

For consequential research, define the question, scope, inclusion/exclusion criteria, source types, search strings, target databases, and stopping rule before synthesis. Cochrane organizes evidence synthesis around determining scope, inclusion criteria, searching/selecting studies, collecting data, assessing bias, synthesizing, grading certainty, and interpreting results. PRISMA 2020 provides the reporting checklist and flow diagrams for transparent review reporting.

### 2) Search must be reproducible

PRISMA-S exists because literature search reporting is often too vague to reproduce. Record database names and platforms, exact queries, dates searched, filters/limits, study registries, grey-literature/web searches, citation chasing, deduplication, and screening counts. If using web search, record enough detail to make personalization and ranking bias visible.

### 3) Source quality is a hierarchy plus context fit

Prefer, in order: peer-reviewed systematic reviews/meta-analyses and official methodology handbooks; peer-reviewed primary studies; official standards/regulators/professional bodies; preprints such as arXiv only when current or field-appropriate and clearly labeled; vendor/blog/SEO material only for tool behavior or practice signals, not scientific claims. Apply source-quality checks for currency, relevance, authority, accuracy, and purpose.

### 4) AI can accelerate retrieval and comparison, but cannot carry evidentiary burden

AI tools can help generate candidate search terms, cluster papers, extract study features, draft evidence tables, and identify contradictions. They must not be treated as a source. LitLLM's motivation highlights common LLM risks: hallucinated non-factual content and missing recent research. Every AI-produced claim must be verified against the cited source text before it enters the knowledge base.

### 5) Synthesis should separate evidence, inference, and judgment

Use evidence tables with columns for claim, source, study/design type, quality caveats, date, and implication. Mark disagreements and uncertainty explicitly. Do not smooth away minority findings. Separate what the sources state from what this workspace should do.

### 6) Bias and certainty must be explicit

Track publication bias, language bias, sponsor/conflict signals, population/context mismatch, search-engine ranking bias, and outdated evidence. For health or formal evidence synthesis, use the domain's accepted risk-of-bias and certainty tools; for general technical research, at minimum record source type, recency, independence, reproducibility, and corroboration.

## Operational Method

1. **Date and scope gate**: record current date; state the research question, intended decision, and acceptable source classes.
2. **Knowledge-first gate**: read `knowledge/INDEX.md` and relevant existing notes before external search.
3. **Protocol-lite gate**: write search terms, databases/sites, inclusion/exclusion criteria, and stopping rule in the run log or research file.
4. **Search wave 1**: search peer-reviewed/indexed and official methodology sources first; avoid SEO summaries as seed sources.
5. **Search wave 2**: chase citations, check contradictory sources, and inspect recent preprints only when they add current field evidence.
6. **Evidence table**: capture claim -> source -> source class -> caveat -> implication.
7. **AI audit gate**: verify every AI-assisted summary against the source; remove unsupported statements.
8. **Challenge gate**: run at least one skeptical review/red-team pass for consequential methodology or policy updates.
9. **Synthesis gate**: publish concise findings, uncertainty, maintenance date, and re-check path.
10. **Index gate**: update `knowledge/INDEX.md` with freshness, value, and stale/reference-risk notes.

## Maintenance Rules for This Repository

- Keep `ai.md/knowledge` as curated research and methodology, not active OpenCode prompts or copied config.
- Mark each research file with `Last updated`, `Status`, and an index row containing freshness and value.
- Treat files older than 3 months as `Aging`; older than 6 months as `Stale` until key claims are re-verified.
- If a source path no longer exists locally, classify the file as valuable-but-needs-maintenance rather than silently trusting it.
- Prefer adding one concise methodology note over duplicating source material.
- Record research evidence in the active `.opencode/works/<slug>/` ledger before claiming completion.

## Implications for OpenCode

- OpenCode should load only distilled operational guidance: read `knowledge/INDEX.md` when a task needs research, use curated notes as sources, and avoid copying `knowledge/` into prompts.
- A knowledge-curation cron should maintain this repository's evidence base.
- A separate config-application cron should inspect this repository's curated changes and selectively update `~/.config/opencode`.

## Limits and Re-check Path

- This method was created for workspace knowledge curation, not formal publication-grade systematic reviews.
- For regulated, clinical, legal, or high-stakes scientific conclusions, use the domain's full protocol, screening, risk-of-bias, and reporting standards.
- Re-check this note when PRISMA/Cochrane/AHRQ guidance changes, when AI literature-review tools materially improve, or after a review panel finds repeated misses.
