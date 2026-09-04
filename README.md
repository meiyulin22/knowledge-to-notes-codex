# Knowledge to Notes for Codex

A vision-native Codex skill that turns notes, documents, PDFs, scans, and images into complete, well-structured Markdown learning notes.

It is designed around two goals:

- make dense source material pleasant to study;
- maintain an explicit coverage inventory so sections are not silently dropped.

This is a Codex-native adaptation of the original [knowledge-to-notes](https://github.com/meiyulin22/knowledge-to-notes) project. The original repository remains independent and unchanged.

## Highlights

- Uses Codex's native visual understanding for scanned pages, screenshots, diagrams, charts, tables, and formulas.
- Combines PDF text extraction with visual page inspection when layout carries meaning.
- Supports three output styles: quick reference, complete learning material, and tutorial restructuring.
- Tracks every meaningful source section with stable inventory IDs and verifies its disposition before delivery.
- Produces Notion- and Obsidian-friendly Markdown.
- Does not automatically install Python packages or require PaddleOCR for ordinary visual sources.

## Install

Clone the repository into your personal Codex skills directory.

PowerShell:

```powershell
git clone https://github.com/meiyulin22/knowledge-to-notes-codex.git "$env:USERPROFILE\.codex\skills\knowledge-to-notes"
```

Bash:

```bash
git clone https://github.com/meiyulin22/knowledge-to-notes-codex.git ~/.codex/skills/knowledge-to-notes
```

The skill becomes available to a new Codex turn after installation.

## Use

Explicit invocation is the most reliable:

```text
Use $knowledge-to-notes to turn this PDF into complete study notes.
```

The `$knowledge-to-notes` prefix is optional when the request clearly matches the skill, for example:

```text
Turn this scanned PDF into complete learning notes and preserve every chapter.
```

Default behavior is medium-depth learning material in the source language. You can request:

- `速查卡` for compact scan-and-recall notes;
- `学习材料` for complete explanations and examples;
- `教程改造` for a pedagogically reordered tutorial with source mapping.

## Supported sources

- PDF, including scanned and mixed text/image PDFs
- Images and screenshots
- Markdown and plain text
- DOCX
- EPUB
- HTML and RTF
- MOBI/AZW/AZW3 when Calibre is already installed

The included `scripts/extract.py` is a local helper for text-bearing sources. Visual sources are handled by the host model's visual tools. See [source handling](references/source-handling.md) for details.

## Repository structure

```text
knowledge-to-notes-codex/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── note-layout.md
│   └── source-handling.md
└── scripts/
    └── extract.py
```

## License

MIT. See [LICENSE](LICENSE).
