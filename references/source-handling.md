# Source handling

Read only the sections relevant to the supplied file types.

## Plain text and Markdown

Read directly. Preserve heading order, fenced code blocks, links, lists, tables, and frontmatter that carries meaning. If the file is too large for one pass, read it in stable line or section ranges and record those ranges in the inventory.

## PDF

Use the available PDF tooling and follow its render-and-inspect workflow when layout matters.

1. Inspect metadata, page count, and whether a usable text layer exists.
2. Extract the text layer for search and inventory building.
3. Render pages that contain diagrams, tables, formulas, screenshots, unusual columns, or suspiciously little extracted text.
4. For a scan, render every relevant page and inspect it visually in page order. Maintain a page checklist.
5. Reconcile visual observations with extracted text before drafting. Retain page numbers for important facts and artifacts.

Do not assume an empty text layer means an empty page. Do not treat visually extracted text as perfectly reliable when resolution is poor.

## Images and screenshots

Use native image viewing at high or original detail. Inspect every supplied image unless the user requests sampling. Record:

- visible text and its reading order;
- relationships conveyed by arrows, grouping, position, color, or scale;
- chart axes, units, legends, and trend direction;
- table headers and row/column associations;
- cropped, blurred, or ambiguous regions.

For screenshots of code or terminal output, preserve indentation and punctuation where legible. Mark uncertain characters rather than guessing.

## DOCX

Prefer the available document tooling when headings, tables, comments, footnotes, or layout matter. The helper script is suitable for ordinary paragraphs and simple tables but may flatten rich structure. Build the inventory from heading structure when it is available.

## EPUB

The helper first uses `ebooklib` and Beautiful Soup when present, then a standard-library ZIP/HTML fallback. Confirm chapter order because EPUB spine and file-name order can differ. Ignore navigation duplicates and boilerplate only after recording their disposition.

## HTML, RTF, and ebooks

- HTML: exclude script, style, and head content; retain meaningful headings, lists, tables, captions, and links.
- RTF: the regex fallback loses some formatting, so flag ambiguity when structure matters.
- MOBI/AZW/AZW3: the helper requires an existing Calibre `ebook-convert`; it does not install Calibre.

## Extraction helper usage

Resolve `scripts/extract.py` relative to this skill directory. Set a task-specific work directory; do not reuse broad system paths.

PowerShell:

```powershell
$env:K2N_WORKDIR = '<workspace>\\work\\k2n\\<run-id>'
python '<skill-dir>\\scripts\\extract.py' '<source-path>' --mode text --install-missing no
```

Bash:

```bash
K2N_WORKDIR='<workspace>/work/k2n/<run-id>' \
python '<skill-dir>/scripts/extract.py' '<source-path>' --mode text --install-missing no
```

Use `--mode technical` for text-bearing technical PDFs when Docling is already available and layout-aware Markdown is useful. Package installation changes the environment and may require network access, so name the missing packages and obtain authorization before using `--install-missing yes`.

After extraction, read `metadata.json`, then read `full_text.txt` completely before finalizing the inventory. If the extracted output is unexpectedly short, fall back to visual inspection or a more appropriate document tool.
