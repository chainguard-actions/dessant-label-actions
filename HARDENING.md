<!-- markdownlint-disable -->

# Hardening Report: dessant--label-actions/v5.0.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dessant--label-actions/v5.0.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference GitHub Actions using mutable version tags instead of pinned full-length SHA digests, making them vulnerable to supply-chain attacks if the referenced tag is moved or the upstream repository is compromised.

- `.github/workflows/label-actions.yml` line 17: `uses: dessant/label-actions@v5` (tag ref, not a SHA)
- `.github/workflows/release.yml` line 14: `uses: softprops/action-gh-release@v3` (tag ref, not a SHA)

Each should be pinned to a full 40-character commit SHA, e.g. `uses: dessant/label-actions@<40-char-sha> # v5`.

Locations:

- `.github/workflows/label-actions.yml:17`
- `.github/workflows/release.yml:14`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned both unpinned action references to full 40-character commit SHAs:
- `.github/workflows/label-actions.yml` line 17: `dessant/label-actions@v5` → `dessant/label-actions@65225c179d3b2502f6eda7b3d15101a3f412366b # v5`
- `.github/workflows/release.yml` line 14: `softprops/action-gh-release@v3` → `softprops/action-gh-release@3d0d9888cb7fd7b750713d6e236d1fcb99157228 # v3`

SHAs were resolved via lookup_action_sha. The original tag names are preserved as inline comments for readability.

