# Note layout

Apply this guidance after the source inventory exists. Adapt the shape to the domain and the user's requested mode; examples are patterns, not mandatory decoration.

## File plan

Use one Markdown file for a coherent, moderate source. Use a directory when the source contains multiple independent topics, exceeds roughly 20,000 words, or has more than 40 leaf inventory items.

Suggested multi-file layout:

```text
<name>-notes/
├── 00-overview.md
├── 01-<topic>.md
├── 02-<topic>.md
└── 99-quick-reference.md   # only when useful
```

`00-overview.md` should briefly explain the collection, give a sensible reading route, and link every topic file with a one-line description. Use relative links and verify them.

## Hierarchy

- One H1 per file.
- Use H2 for major source sections and H3/H4 to keep dense explanations scannable.
- Preserve the source's hierarchy unless `教程改造` mode calls for reordering. When reordering, include a source-to-output map.
- Use whitespace and headings before adding decorative elements.

Emoji may serve as sparse semantic landmarks—such as `💡` for an insight, `⚠️` for a trap, `🔑` for a definition, and `🧪` for a derivation—but should not appear on every line or distort a serious source. Follow the user's style preference.

## Concept treatment

For `学习材料`, give each meaningful concept the fields that actually help:

1. a clear definition;
2. explanation in the source's context;
3. source example or a clearly labeled added example;
4. use case or significance;
5. trap, limitation, or edge case when one exists;
6. comparison with a related concept when it clarifies a real distinction.

Do not invent a trap or comparison merely to fill a template. For `速查卡`, prefer definition, compact example, and the highest-value trap. For `教程改造`, add transitions and prerequisites so the reordered sequence teaches coherently.

## Useful blocks

Use blocks only where they improve retrieval:

```markdown
> 💡 **Key insight:** One concise takeaway.

> ⚠️ **Common trap:** What goes wrong and why.

> ❗ **Correction:** Source claim → corrected claim, with evidence when required.

> 💎 **Section summary:** A synthesis of the detail above, never a substitute for it.
```

Tables are effective for genuine comparisons, timelines, taxonomies, and quick reference. Keep them readable—usually six columns or fewer—but include all relevant rows. Use lists or subsections when cells become paragraphs.

Specify a language on fenced code blocks. Preserve executable source examples exactly unless correcting an error; show corrections separately. Preserve formulas and units, and check that Markdown math delimiters render correctly in the target editor.

## Visual material

Integrate figures into the explanation instead of appending raw OCR text.

- For a diagram, explain components and relationships, then cite the source page or figure.
- For a chart, state axes, units, comparison, trend, and any visible caveat.
- For a table, preserve header-to-cell relationships and units.
- For a screenshot, distinguish interface labels from the underlying concept.

If an image must be embedded, use a stable relative path and copy it only when the user authorized creating the deliverable. Add concise alt text.

## Coverage record

Maintain a work inventory such as:

```markdown
- [x] S001 — Original section title — full — 01-topic.md#section
- [x] S002 — Original subtopic — merged — 01-topic.md#combined-section
- [x] S003 — Repeated appendix — omitted: duplicate of S001
- [ ] S004 — Unreadable scan, page 17 — needs user input
```

An item is covered by meaning, not merely because its heading text appears. Search can identify candidates, but verification requires checking the note content.

Report `covered/total` and separately list `omitted`, `uncertain`, and `needs input`. Do not use a word-count compression ratio as proof of completeness; use it only as a warning signal when the output is unexpectedly small.
