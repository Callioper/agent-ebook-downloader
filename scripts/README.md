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
python3 scripts/inject_bookmarks.py input.pdf bookmarks.txt --offset 10

# With OCR cross-reference (pass OCR PDF path)
python3 scripts/inject_bookmarks.py input.pdf bookmarks.txt --ocr ocr_version.pdf

# TOC only mode (adds only the TOC page bookmark)
python3 scripts/inject_bookmarks.py --toc-only input.pdf output.pdf
```

### config_reader.py

Configuration reader module. Reads `config.yaml` with type-safe getters and masked display.

**Usage:**
```bash
# Display channel configuration status (sensitive values masked)
python3 scripts/config_reader.py

# Output full config as JSON (sensitive values masked)
python3 scripts/config_reader.py --json

# Check if minimal config is complete (exit code reflects result)
python3 scripts/config_reader.py --check
```

## Dependencies

- `parse_bookmark_hierarchy.py`: Pure Python, no external dependencies
- `inject_bookmarks.py`: `PyMuPDF`
- `config_reader.py`: `pyyaml`
