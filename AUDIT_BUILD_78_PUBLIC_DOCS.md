# Build 78 – public documentation alignment audit

Reviewed: 5 October 2026  
App baseline: `rskjonbe/P40ParkAssist release/build-78` at `3ecdbcb7d79b084e029b598eabc72de2908c0539`  
Documentation baseline: `main`  
Correction branch: `audit/build-78-doc-alignment`

## Result

The public Norwegian and English documentation was compared with the frozen Build 78 implementation.

Two documentation drifts were identified and corrected on this branch:

1. **Additional UI languages**
   - Old wording incorrectly required both Apple Foundation Models and Apple Translation.
   - Build 78 intentionally separates these capabilities.
   - Additional UI languages depend on Apple Translation support for the English-to-target pair.
   - Apple Foundation Models are used separately for optional on-device AI diagnostics.

2. **Live Activity vehicle photo**
   - Old security wording still described an ActivityKit retry/fallback without the image.
   - Build 78 no longer places vehicle-image bytes in ActivityKit `ContentState`.
   - The optional image is resized locally to a dedicated **144 × 108 JPEG** in the P40 App Group and read by the Live Activity extension.
   - The image is not sent to the developer, SmartPark or the vehicle-lookup service by this feature.

The Norwegian and English privacy/support/terms language descriptions were aligned, and both public security pages were updated to the Build 78 Live Activity architecture.

## Regression guard

`.github/workflows/site-check.yml` on this branch now guards against reintroducing:

- the obsolete dual Foundation Models + Translation requirement; and
- the obsolete ActivityKit image-fallback wording.

The guard also requires the Build 78 144 × 108 local-thumbnail disclosure on both security pages.

## Manual validation without GitHub Actions

GitHub Actions capacity was unavailable during this audit, so the corrected branch was validated without dispatching or triggering Actions.

Manual static validation covered all ten public HTML pages and confirmed:

- 10/10 expected HTML pages present;
- no broken internal page/style links;
- no `script`, `form` or `iframe` elements;
- no obsolete dual-model language requirement;
- no obsolete Live Activity image-fallback statement;
- Norwegian and English security pages document the 144 × 108 local App Group thumbnail;
- Norwegian and English two-hour safety wording still states that an unused scheduled parking session is **not** stopped automatically and requires explicit user choice.

## Publication status

This branch is deliberately **not merged to `main` during the audit**, because `main` pushes trigger the documentation GitHub Actions workflow and the current Actions allowance is exhausted.

When Actions capacity is available:

1. review the branch diff;
2. merge/publish the branch to `main`;
3. allow the normal public-documentation quality gate to run;
4. verify the GitHub Pages deployment and public Norwegian/English pages.

Until then, this branch is the reviewed Build 78 documentation correction set.
