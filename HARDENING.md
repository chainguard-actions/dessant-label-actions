<!-- markdownlint-disable -->

# Hardening Report: dessant--label-actions/v5.0.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dessant--label-actions/v5.0.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference GitHub Actions using mutable version tags instead of full 40-character commit SHA hashes. This exposes the workflow to supply-chain attacks: if the referenced action's tag is moved (intentionally or by a compromised maintainer), the workflow will silently execute different code.

- `.github/workflows/label-actions.yml`: `uses: dessant/label-actions@v5` — `@v5` is a mutable tag, not a pinned SHA.
- `.github/workflows/release.yml`: `uses: softprops/action-gh-release@v3` — `@v3` is a mutable tag, not a pinned SHA.

Fix: Replace each tag with the full 40-character commit SHA of the intended release, e.g. `uses: dessant/label-actions@<40-char-sha> # v5`.

Locations:

- `.github/workflows/label-actions.yml:18`
- `.github/workflows/release.yml:14`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned both mutable action tags to their full 40-character commit SHAs:
1. `dessant/label-actions@v5` → `dessant/label-actions@65225c179d3b2502f6eda7b3d15101a3f412366b # v5` in `.github/workflows/label-actions.yml`
2. `softprops/action-gh-release@v3` → `softprops/action-gh-release@3d0d9888cb7fd7b750713d6e236d1fcb99157228 # v3` in `.github/workflows/release.yml`
Original version tags are preserved as inline comments for readability.

