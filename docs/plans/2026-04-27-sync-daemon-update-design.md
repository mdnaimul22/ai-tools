# Design Document: Sync Daemon Update & Rebranding

**Date:** 2026-04-27  
**Topic:** Sync Daemon Enhancements  
**Status:** Approved

## 1. Goal
Transition the project from its "Human Skills" origin to a dedicated "AI Tools" sync utility. Key requirements include supporting file renaming during synchronization and cleaning up obsolete terminology.

## 2. Architecture Changes

### 2.1 Renaming Logic in `sync.py`
The `forward_skills` (to be renamed `forward_assets`) function will be updated to:
- **Directory Mode:** Triggered if the `to` path ends with a slash or points to an existing directory. Source files are copied inside with their original names.
- **Rename Mode:** Triggered if the `to` path includes a filename. The source file is copied and renamed to the specified destination.

### 2.2 Configuration Fixes
- Fix typo in `.github/upstream.yaml`: `.toolss` → `.tools`.
- Update `.github/path_forward.yaml` to point to `.github/tools.md` as the destination for the upstream README.

### 2.3 Context Rebranding
- Rename functions and variables in `sync.py` to remove "skills" (e.g., `forward_skills` → `sync_assets`).
- Update comments and log messages to reflect the "AI Tools" project context.

## 3. Data Flow
1. **Pull**: Upstream repo `Top-AI-Tools` is cloned/pulled into `.tools`.
2. **Forward**: `README.md` is copied from `.tools` and renamed to `.github/tools.md` in the repo root.
3. **Commit/Push**: Changes are pushed to the user's repository.

## 4. Error Handling
- Ensure parent directories are created for both directory and file destinations.
- Maintain existing error logging for missing sources or failed git operations.

## 5. Verification Plan
- Run `sync.py` and verify:
  1. `.tools` directory is created correctly.
  2. `.github/tools.md` is created/updated with content from the upstream README.
  3. No "skills" references remain in logs or active code.
