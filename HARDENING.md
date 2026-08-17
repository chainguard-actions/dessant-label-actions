<!-- markdownlint-disable -->

# Hardening Report: dessant--label-actions/v5.0.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dessant--label-actions/v5.0.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference external actions using mutable version tags instead of pinned full-length SHA digests, making them vulnerable to supply-chain attacks if the upstream tag is moved or the repository is compromised.

- `.github/workflows/label-actions.yml` line 21: `uses: dessant/label-actions@v5` (tag `@v5` is mutable)
- `.github/workflows/release.yml` line 16: `uses: softprops/action-gh-release@v3` (tag `@v3` is mutable)

These should be pinned to their full 40-character commit SHAs, e.g. `uses: dessant/label-actions@<sha> # v5`.

Locations:

- `.github/workflows/label-actions.yml:21`
- `.github/workflows/release.yml:16`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned two unpinned action references to full commit SHAs:
1. `.github/workflows/label-actions.yml` line 21: `dessant/label-actions@v5` → `dessant/label-actions@65225c179d3b2502f6eda7b3d15101a3f412366b # v5`
2. `.github/workflows/release.yml` line 16: `softprops/action-gh-release@v3` → `softprops/action-gh-release@3d0d9888cb7fd7b750713d6e236d1fcb99157228 # v3`

Original version tags are preserved as inline comments for readability. No other findings were present.

