# OKF v0.2 summary for research bundles

This is a local, task-focused summary of the [Open Knowledge Format v0.2 specification](https://github.com/GoogleCloudPlatform/open-knowledge-format/blob/main/SPEC.md). The [OKF annotated guide](https://okf.md/spec/) is also useful; use the official specification as the source of truth if they differ.

An OKF bundle is a directory tree of Markdown files. It is a format, not a database or hosted service. Organize files locally under the destination the user chooses.

## Concept documents

- Each concept is a Markdown file with YAML frontmatter and a Markdown body.
- `type` is the only required frontmatter field. Choose a descriptive value; `title`, `description`, `tags`, and other metadata are optional.
- OKF permits producer-defined frontmatter fields. Do not treat this summary's optional conventions as required OKF fields.
- Link concepts using standard Markdown links. Bundle-root-relative links such as `/topic.md` and ordinary relative links are supported.

## Sources and claim attribution

- Record source materials in a concept's `sources` frontmatter list. Each source entry requires a `resource` (URL, bundle-relative path, or another valid OKF source locator). Use a stable `id` when attributing claims.
- Attribute a specific claim with a Markdown footnote whose label matches the source `id`, for example `[^manual]`, and define that footnote in the document body. OKF v0.2 does not use a numbered `# Citations` list as its provenance mechanism.
- Research bundles also record when each source was accessed. OKF has no standard access-date property, so use the producer-defined `accessed_on` field as a quoted `YYYY-MM-DD` date:

  ```yaml
  sources:
    - id: manual
      resource: https://example.com/manual
      title: Product manual
      accessed_on: "2026-11-10"
  ```

  Treat `accessed_on` as this workflow's extension, not a field required by OKF. Do not invent source URLs or access dates.

## Index and log files

- `index.md` is an optional directory listing and has no frontmatter. The bundle-root `index.md` is the exception: it may include `okf_version`.
- `log.md` is an optional chronological update log and has no frontmatter.
- Use standard Markdown headings and links in indexes; list the contained concepts and concise descriptions when an index is useful.

## Conformance essentials

- Every concept document has parseable YAML frontmatter with a non-empty `type`.
- Reserved `index.md` and `log.md` files follow their special formats.
- Other fields and conventions are optional unless the producer defines them. Unknown frontmatter fields are allowed.
