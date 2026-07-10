# Agent guidance for FDX

## Repository purpose

FDX (Frontier Disambiguation Experience) is a small, static reference site that helps readers distinguish among organizations, programs, credentials, frameworks, and industry terms that use the word "Frontier." The landing page in `index.html` presents one tile per topic and renders the corresponding root-level Markdown file in a dialog.

Treat the active Markdown files as concise reference entries, not blog posts, announcements, or marketing pages. A reader should be able to answer three questions quickly:

- What exactly does this use of "Frontier" name?
- Who created it or whom is it for?
- How is it meaningfully different from the other Frontier concepts in this repository?

Files under `archived/` are historical snapshots. Do not use them as the style baseline or restore their content to the active experience unless the task explicitly calls for it.

## Content principles

- Be factual, neutral, and direct. Translate promotional source language into plain English while preserving official product, program, and organization names.
- Lead with the distinguishing definition. The first section should identify the concept's type, owner or origin, intended audience, and purpose when those facts are known.
- Prefer concrete details over broad claims. Include eligibility, operating model, benefits, requirements, dates, preview status, or scale only when they help disambiguate the topic.
- Keep scope tight. Explain the named concept rather than expanding into a general overview of AI, Microsoft, OpenAI, or partner programs.
- Distinguish fact from interpretation. Attribute frameworks, claims, survey findings, and forecasts to the organization or report that made them.
- Qualify time-sensitive statements with a date or status such as "announced in April 2026," "in private preview," or "expected in FY26." Do not present roadmap details as settled facts.
- Verify names, numbers, dates, eligibility rules, and availability against current sources before changing them. Prefer first-party product pages, announcements, reports, FAQs, and official documentation.
- Do not invent details to make entries symmetrical. Omit a section when reliable sources do not support it.

## Markdown structure

Use this default shape, adapting the middle sections to the topic:

```markdown
# Official topic name

## What is it?

A short definition that begins with the exact topic name and identifies its owner, type, audience, and purpose.

## Distinguishing aspect

A short paragraph or focused unordered list.

## Why it matters

Only include this when it adds concrete context rather than promotional language.

## Resources

- [Descriptive source title](https://example.com/source)
```

- Use exactly one H1. It must be the official display name because `index.html` derives the topic tile and dialog title from it.
- Make `## What is it?` the first H2 for new entries. Answer it immediately; do not add an abstract, metadata block, or introductory preamble.
- Use descriptive H2 sections for the body and H3 only when a section genuinely needs subdivision. Prefer sentence case for headings while preserving proper nouns.
- End every active entry with an H2 named exactly `## Resources`. The site detects that label and gives the source list special presentation.
- Keep entries compact and scannable. Favor short paragraphs and small lists; avoid repeating the definition in later sections.
- Use unordered lists for parallel facts, requirements, capabilities, or outcomes. Use nested lists sparingly and indent nested items with four spaces.
- Use bold lead-ins such as `**Eligibility:**` when they make list items easier to scan. Use bold for emphasis, not decoration.
- Use descriptive link text. Do not use raw URLs or generic labels such as "click here."
- Do not add YAML frontmatter, an H1 subtitle, a table of contents, or a closing summary.

## Renderer constraints

The Markdown is rendered by the small custom parser in `index.html`, not by a full CommonMark implementation. Keep active topic files within its supported subset:

- H1 through H3 headings
- Plain paragraphs
- Unordered lists using `-` or `*`
- HTTP or HTTPS links in `[label](URL)` form
- `**bold**` and inline code using backticks

Do not rely on tables, ordered lists, images, blockquotes, task lists, fenced code blocks, footnotes, HTML, emphasis with single asterisks, or relative links. They may be displayed as plain text or parsed incorrectly. If richer Markdown support is intentionally added to the renderer, update this guidance in the same change.

## Editorial conventions

- Use American English and contractions only when they sound natural in explanatory prose.
- Use the official capitalization of brands and offerings, including Microsoft 365, GitHub Copilot, Microsoft Foundry, Copilot Studio, and OpenAI.
- Spell out an uncommon term on first use and place its abbreviation in parentheses. A well-known product name does not need expansion.
- Use numerals for dates, percentages, certification codes, monetary amounts, and measured quantities.
- Use the serial comma. Use an en dash for numeric ranges and an em dash only when it improves a sentence; do not use double hyphens as punctuation.
- Avoid unsupported superlatives, calls to action, second-person sales language, and vague phrases such as "cutting-edge" when a precise description is available.
- Keep source titles recognizable and specific. Put primary sources first, followed by supporting sources.
- Link directly to the source page when possible. Use an `aka.ms` link when it is the official durable link or the direct source is unavailable.

## Adding or changing topics

- Active topic files live at the repository root and use short lowercase filenames without spaces, consistent with the existing files.
- Adding a Markdown file alone does not expose it in the site. Add a matching `{ id, src }` entry to the `TOPICS` array in `index.html`; the `id` becomes the URL hash and should be stable, lowercase, and hyphenated.
- When renaming a topic, consider existing shared hash URLs before changing its `id`. Prefer keeping the current `id` unless the task requires a URL change.
- Check nearby entries for overlapping terminology and clarify the distinction in the definition when readers could confuse them.
- Keep `Resources` links aligned with claims added or changed in the entry. Remove dead, superseded, or irrelevant links.
- After content changes, serve the repository over HTTP and verify that every tile loads, the H1 appears as the tile/dialog title, lists render correctly, the Resources block is styled, and external links open as expected.

## Scope discipline

Keep content-only requests focused on Markdown. Do not redesign `index.html`, rewrite unrelated entries, or normalize the archive unless requested. Preserve the site's dependency-free static architecture unless a task explicitly requires a broader implementation change.