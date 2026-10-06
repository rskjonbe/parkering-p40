# Parkeringsassistent P40 – public documentation

Public Norwegian/English documentation used by the app and App Store metadata.

Current documentation baseline: **Build 80**. The public pages distinguish the latest automatic attempt/result from the last confirmed automatic parking start, document the local language-independent outcome state, and describe the separate roles of Apple Translation and Apple Foundation Models.

- Privacy: `index.html` / `en/index.html`
- Terms: `vilkar.html` / `en/vilkar.html`
- Support: `support.html` / `en/support.html`
- Automatic P40 / Shortcuts guide: `automation.html` / `en/automation.html`
- Security overview: `security.html` / `en/security.html`

The site is static: no forms, tracking scripts or analytics are required for these pages.

A GitHub Actions quality gate checks internal links and guards the current safety semantics so public documentation does not drift from the app.
