# Gitleaks Viewer

A single-file, local-only HTML viewer for [Gitleaks](https://github.com/gitleaks/gitleaks) JSON reports. Paste your `leaks.json`, triage findings in a clean table, mark items as fixed or false-positive, and export filtered reports.

**Live:** https://miglen.github.io/gitleaks-viewer
**Repo:** https://github.com/miglen/gitleaks-viewer

No build step. No dependencies. No network calls. Just open the HTML in a browser.

## Features

- **Local only** — everything runs in your browser; secrets never leave your machine
- **Triage table** — sortable, searchable, filter by rule or status, mask/reveal secrets per row
- **Persistent marks** — mark findings as Fixed ✓ or Test/False-positive 🚩 (stored in `localStorage` by Gitleaks fingerprint)
- **Export** — HTML, CSV, PDF, JSON, or Full JSON. Respects current filters and marks. Optional toggle to include raw secret values
- **Dark / light theme**

## Quick start

Generate a Gitleaks report:

```bash
# working directory
gitleaks detect --source . --report-format json --report-path leaks.json --no-banner

# full git history (recommended)
gitleaks detect --source . --log-opts="--all" --report-format json --report-path leaks.json --no-banner
```

Open https://miglen.github.io/gitleaks-viewer (or `gitleaks-viewer.html` locally), import the JSON, and triage.


Use **Reset marks** in the Import tab to wipe triage state.

## Security note

The viewer makes zero network requests, but exports with "Include real secret values" turned on contain raw credentials — treat them as confidential and rotate anything still in use. Removing secrets from git history isn't enough if they were ever pushed.

## License

MIT
