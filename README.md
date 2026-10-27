# PDF Studio

A responsive PDF toolbox built with plain HTML, CSS and JavaScript. No build step, account, or backend is needed for the local tools.

## Run

```sh
cd /workspace/pdf
python3 -m http.server 8000 --bind 0.0.0.0
```

Serve over HTTP rather than opening index.html directly so the PDF.js worker loads correctly. Any static hosting service can host these files.

## Features

- Merge PDFs; order files with the up arrow.
- Extract pages, or reorder/duplicate/delete pages by specifying the desired page sequence. Organize keeps all pages when the sequence is blank.
- Rotate pages; add text watermarks, annotations, and page numbers.
- Convert JPG/PNG images (including document photos) to PDF.
- Export PDF pages as individual JPG downloads.
- Extract selectable text to TXT. Scanned pages need OCR, which is not included.
- Compress PDFs by rasterizing pages at adjustable JPEG quality. This removes selectable text, forms and links, and does not always reduce file size.
- Search, category filters, file drag-and-drop, responsive layout and keyboard-accessible dialogs. Header navigation clears prior searches. Downloads reset when inputs change, and controls are locked while processing to avoid conflicting operations.

PDF to Word, PDF to Excel, password removal, and password encryption are explicitly marked unavailable: they need an additional conversion/encryption implementation. Scan to PDF accepts existing photos; live camera capture, OCR, digital signatures and advanced PDF editing are not implemented. Text annotations use Helvetica's supported Latin characters; unsupported characters produce an error. Large PDFs can exhaust browser memory. Password-protected PDFs are not processed.

Documents are processed locally. The interface uses system fonts and does not request external font services. PDF libraries and worker are vendored locally: pdf-lib 1.17.1 (MIT) and PDF.js 3.11.174 (Apache 2.0); licenses are in vendor/. No npm install is required to run the site. Evaluate current library security advisories before exposing this prototype to untrusted documents in production.

## Validation

Browser smoke checks exercise functional PDF output and responsive behavior. Setup uses the existing checkout; do not create a separate worktree.
