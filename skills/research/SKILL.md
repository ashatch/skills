---
name: research
description: Plan and conduct research on any topic — not just academic literature — by defining a question, sourcing and screening evidence, evaluating it, and writing findings as a private, local Open Knowledge Format (OKF) bundle with tracked source links and access dates. Use when researching a topic, building a personal or team knowledge base from research, or asked to save findings as structured Markdown notes.
---

# Research into an Open Knowledge Format bundle

Use this process to research any topic — technical, product, academic, market, or personal — and capture findings as a local, private collection of Markdown documents. Adapt the depth to the goal: a quick investigation may only need a few concept documents, while a deep review may need a full bundle with an index and citations throughout. Do not claim systematic or exhaustive coverage unless your methods support that claim.

This workflow is local-first and does not depend on hosted research databases, citation managers, or external accounts. Sources can be anything you can access directly: web pages, documentation, codebases, internal wikis, interviews, academic papers, or prior conversations. Keep confidential source material and sensitive research details local; do not send them to external services. If an external query could disclose private information, ask the user before sending it.

## 1. Define and design

- If it is unclear, clarify the purpose of the research. Formulate and state a focused research question.
- Scope should be clear before gathering sources. Resolve material ambiguity with the user; if proceeding with assumptions, state them.
- **Before writing any file, ask the user where the findings bundle should live** (for example `research/<topic>/` in the current project, or another local path). Do not create a bundle directory or files until the user confirms a destination.

## 2. Search and source

- Use whatever sources are directly accessible for the question — the web, local documentation, source code, prior session history, or the user's own files. Do not imply access to a paywalled database, journal, or archive you cannot actually reach.
- Translate the question into search terms and follow promising leads (links, references, related files) outward. Prefer primary sources over summaries when available.
- For every source you use, record its link (URL or local path) and the date you accessed it; you will need both when writing citations.

## 3. Screen and select

- Skim before committing: check a source's relevance and apparent reliability before reading it in full.
- Keep a short working list of which sources you kept and why, and which you discarded, so the trail is reconstructable later.
- When a source's reliability or relevance is unclear, note that uncertainty rather than silently including or dropping it.

## 4. Evaluate

- For each source, judge authorship, currency, and whether its claims are actually supported by what it shows — not just whether it's topically relevant.
- Separate what a source states from your own interpretation or inference.
- Treat conflicting information across sources as something to investigate and note, not to quietly resolve in the write-up.

## 5. Synthesize and organize

- Group findings into concepts: coherent units of knowledge (a topic, a comparison, a decision, an entity) that each deserve their own document.
- Decide on a directory structure for the bundle under the destination confirmed in step 1 — flat for a small topic, nested by theme for a larger one.
- Identify cross-links between concepts (e.g., a concept that depends on or relates to another) before writing, so the bundle reads as a connected whole rather than isolated notes.

## 6. Write findings as an OKF bundle

Write findings as Markdown files following the [Open Knowledge Format spec](https://github.com/GoogleCloudPlatform/open-knowledge-format/blob/main/SPEC.md) (OKF). Use the local [OKF summary](references/okf.md) for the subset this workflow needs; the official specification is authoritative if details change or conflict.

- Create one Markdown file per concept. Each concept file needs YAML frontmatter with at least a `type` field (e.g., `type: Finding`, `type: Comparison`, `type: Entity` — choose descriptive values and stay consistent within a bundle). Add optional `title`, `description`, and `tags` when they help navigation.
- You may add extra frontmatter fields beyond the spec's recommended set (e.g., `confidence`, `owner`) as producer extensions — OKF permits this, but don't invent a rigid required schema beyond what the spec defines.
- Write the body as structured Markdown (headings, lists, tables) over dense prose, so both humans and agents can scan it.
- For each concept's sources, add a `sources` frontmatter list with a stable `id`, the required `resource` URL or local path, and a title when available. Record the access date using the local `accessed_on` extension described in the OKF summary. Attribute specific claims with Markdown footnotes keyed to those source IDs; do not use a numbered `# Citations` section in place of OKF v0.2 provenance:

  ```
  ---
  type: Finding
  sources:
    - id: vendor-pricing
      resource: https://example.com/pricing
      title: Vendor pricing page
      accessed_on: "2026-11-10"
  ---

  The listed price was $20 per month.[^vendor-pricing]

  [^vendor-pricing]: Vendor pricing page
  ```

- Link related concepts with ordinary Markdown links: bundle-root-relative (`/concept.md`) is the more stable form; relative links (`./other.md`) also work.
- Add an `index.md` at the bundle root listing its concepts with one-line descriptions. For nested bundles, add subdirectory indexes when they help navigation. Indexes have no frontmatter except that the bundle-root `index.md` may include `okf_version`.
- Do not route findings through a hosted citation manager, reference database, or external research platform — the bundle itself is the record, kept private and local to the destination the user chose.

## 7. Refine

- Re-check that every non-trivial claim in a concept document traces to a citation with a link and access date, and that no citation was invented.
- Re-read for argument and structure first, then evidence and citations, then clarity. Flag anything you could not verify instead of smoothing over it.
- Confirm the bundle is conformant: every concept file has frontmatter with a non-empty `type`; `index.md` and `log.md` follow their spec formats. Index files have no frontmatter except that the bundle-root `index.md` may include `okf_version`.
