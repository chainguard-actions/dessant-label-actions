<!-- markdownlint-disable -->

# Hardening Report: dessant--label-actions/v4.0.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dessant--label-actions/v4.0.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Two workflow files reference GitHub Actions using mutable version tags instead of pinned full-length SHA digests, making them vulnerable to supply-chain attacks if the tag is moved to a different (potentially malicious) commit.

- `.github/workflows/label-actions.yml` line 20: `uses: dessant/label-actions@v4` — `@v4` is a mutable tag, not a SHA.
- `.github/workflows/release.yml` line 15: `uses: softprops/action-gh-release@v1` — `@v1` is a mutable tag, not a SHA.

Both should be pinned to a full 40-character hex commit SHA, e.g. `uses: softprops/action-gh-release@<40-char-sha> # v1`.

Locations:

- `.github/workflows/label-actions.yml:20`
- `.github/workflows/release.yml:15`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned both unpinned action references to full 40-character SHA digests:
1. `.github/workflows/label-actions.yml` line 20: `dessant/label-actions@v4` → `dessant/label-actions@102faf474a544be75fbaf4df54e73d3c515a0e65 # v4`
2. `.github/workflows/release.yml` line 15: `softprops/action-gh-release@v1` → `softprops/action-gh-release@de2c0eb89ae2a093876385947365aca7b0e5f844 # v1`

Mutable version tags are preserved as inline comments for readability.

