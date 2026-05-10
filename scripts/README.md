# Scripts

This directory contains Python scripts for the ebook-downloader pipeline.

## Scripts

### parse_bookmark_hierarchy.py

Bookmark hierarchy inference engine. Uses a stack depth model to parse flat bookmark text into hierarchical structure.

**Usage:**
```bash
python3 scripts/parse_bookmark_hierarchy.py
```

Running without arguments outputs 4 built-in test cases.

### inject_bookmarks.py

Bookmark injection engine. Injects bookmarks into PDF files with offset calculation and post-injection verification.

**Usage:**
```bash
# Basic injection
python3 scripts/inject_bookmarks.py input.pdf bookmarks.txt output.pdf

# With offset
python3 scripts/inject_bookmarks.py input.pdf bookmarks.txt output.pdf --offset 10

# OCR mode
python3 scripts/inject_bookmarks.py input.pdf bookmarks.txt output.pdf --ocr

# TOC only mode
python3 scripts/inject_bookmarks.py input.pdf bookmarks.txt output.pdf --toc-only
```

### config_reader.py

Configuration reader module. Reads `config.yaml` with type-safe getters and masked display.

**Usage:**
```bash
python3 scripts/config_reader.py
```

Running without arguments displays the current configuration status (with sensitive values masked).

## Dependencies

- `parse_bookmark_hierarchy.py`: Pure Python, no external dependencies
- `inject_bookmarks.py`: `pikepdf`, `PyMuPDF`
- `config_reader.py`: `pyyaml`
