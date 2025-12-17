# SNAPSHOT — Claude Code Starter Framework

*Last updated: 2025-12-16*

## Current State

**Version:** 2.3.1
**Status:** Production - Complete bug reporting system (Phase 1-3)
**Branch:** main

## What's New in v2.0

### Structural Changes
| Before | After |
|--------|-------|
| Docs only | Docs + Code |
| `.claude-export/` (hidden) | `src/claude-export/` (visible) |
| No package.json | Full npm project |
| No ARCHITECTURE.md | Documented code structure |

### New Files
- `package.json` — npm scripts and dependencies
- `tsconfig.json` — TypeScript configuration
- `ARCHITECTURE.md` — code documentation
- `src/claude-export/` — source code

### Removed
- `init_eng/` — will be regenerated
- `init-starter.zip` — will be regenerated
- `init-starter-en.zip` — will be regenerated
- `dev/`, `test/`, `t2.md` — temporary files
- Historical files → `archive/`

## Current Structure

```
claude-code-starter/
├── src/claude-export/     ✅ Source code
├── dist/claude-export/    ✅ Compiled
├── .claude/
│   ├── commands/          ✅ Framework commands
│   ├── SNAPSHOT.md        ✅ This file
│   ├── ARCHITECTURE.md    ✅ Code structure
│   └── BACKLOG.md         ✅ Tasks
├── dialog/                ✅ Dev dialogs
│
├── package.json           ✅ npm scripts
├── tsconfig.json          ✅ TypeScript config
├── CLAUDE.md              ✅ AI protocols
├── CHANGELOG.md           ✅ Version history
└── README.md / README_RU.md
```

## Completed Tasks (Phase 1 & 2)

- [x] Restructure to src/, dist/, package.json
- [x] Update CLAUDE.md with full protocols
- [x] Verify Cold Start Protocol
- [x] Verify Completion Protocol (/fi)
- [x] Update BACKLOG.md for v2.0.0
- [x] Remove distribution files (Init/, init_eng/, zip)
- [x] Teacher UI — Force Sync working
- [x] Student UI — template replacement fixed
- [x] Path encoding — underscore/dash variations support
- [x] Manual summaries — 6 dialogs (SUMMARY_SHORT/FULL format)
- [x] CLI testing — list, export, init, watch verified
- [x] Privacy management — Teacher UI → Student UI sync tested
- [x] **Dialog export sync bug** — fixed runExport to call syncCurrentSession
- [x] **Summary parsing** — simplified from 37 to 17 lines (-54% code)
- [x] **Marker system** — SUMMARY: PENDING/ACTIVE for generation tracking
- [x] **UI auto-refresh** — 10-second interval for data updates
- [x] **README updates** — both EN and RU versions updated for v2.0
- [x] **File reorganization** — AI metafiles moved to .claude/
- [x] **Completion Protocol** — enhanced to include README.md + README_RU.md
- [x] **Cold Start Protocol** — added Step 0.5 for closed session export
- [x] **Student UI sync** — html-viewer now updates on Cold Start (not Completion)
- [x] **CLI --no-html flag** — export without HTML generation
- [x] **CLI generate-html command** — separate HTML generation for students
- [x] **Migration system** — complete system for installing FW into projects
- [x] **Meta file templates** — SNAPSHOT, BACKLOG, ARCHITECTURE templates
- [x] **init-project.sh** — self-extracting installer (88KB)
- [x] **build-distribution.sh** — distribution package builder
- [x] **README.md restructure** — Installation integrated, "How It Works" added
- [x] **Documentation cleanup** — removed outdated file references
- [x] **dist-release/** — removed from git tracking
- [x] **Bug #2 Fix (Parasitic folders)** — watcher.ts now uses project root cwd
- [x] **sed escaping fix** — init-project.sh handles special chars in descriptions
- [x] **Token economy fix** — init-project.sh architecture redesigned (88KB → 5.3KB, 16.6x smaller!)
- [x] **Loader pattern** — init-project.sh now downloads framework.tar.gz separately from GitHub Releases
- [x] **Installation UX** — unified workflow for all scenarios (new/legacy/upgrade)
- [x] **New project setup** — CLAUDE.md handles "mode": "new" with welcome message
- [x] **Qualifying questions** — added explicit "Сделай, как лучше" option
- [x] **Migration summary** — simplified to concise message instead of large tables
- [x] **README updates** — simplified installation instructions for beginners
- [x] **Two-phase CLAUDE.md** — CLAUDE.migration.md + CLAUDE.production.md
- [x] **Migration crash recovery** — migration-log.json for interrupted migrations
- [x] **Step 0/9 migrate-legacy** — log init and CLAUDE.md swap on completion
- [x] **Step 0/8 upgrade-framework** — log init and CLAUDE.md swap on completion
- [x] **Production testing** — santacruz project successfully migrated v1.x → v2.2
- [x] **Migration reports bug fix** — Made MIGRATION_REPORT.md generation mandatory before cleanup

## v2.2.3 Critical Fixes

**Source File Synchronization Issue (RESOLVED):**
- Fixed migration/CLAUDE.production.md being out of sync with bug fixes
- All 4 production bugs now fixed in source templates
- Framework → Host project update cycle now working correctly

**Bug Fixes:**
- BUG-001: Migration cleanup recovery (Step 0.05)
- BUG-002: Missing chokidar dependency
- BUG-003: Port conflict detection (EADDRINUSE handler)
- BUG-004: Session cleanup false positives

**Distribution:**
- framework.tar.gz rebuilt with corrected source files
- GitHub Release v2.2.3 updated (CORRECTED)
- santacruz host project updated and verified

## What's New in v2.3.0

**Bug Reporting & Logging System (Phase 6):**
- [x] Step 0.15: Bug Reporting Consent - First-run opt-in dialog
- [x] Step 0.3: Cold Start Protocol Logging with timestamps
- [x] Completion Protocol Logging (Step 0 & Step 6.5)
- [x] /bug-reporting command - manage settings (enable/disable/status/test)
- [x] Anonymization script - removes paths, keys, emails, IPs
- [x] Framework Developer Mode (Step 0.4) - reads bug reports from GitHub Issues
- [x] /analyze-bugs command - group and prioritize bug reports
- [x] .framework-config - privacy preferences storage
- [x] Tested on santacruz - all features working

**Privacy-First Design:**
- Opt-in by default (disabled until user enables)
- Complete anonymization before sharing
- User control via /bug-reporting command
- Local logs in .claude/logs/ (gitignored)

**What Gets Logged:**
- Protocol execution steps with timestamps
- Error messages and stack traces (anonymized)
- Framework version and step information

**What Does NOT Get Logged:**
- Your code or file contents
- File paths (replaced with /PROJECT_ROOT/...)
- API keys, tokens, secrets (removed)
- Email addresses, IP addresses

## What's New in v2.3.1

**Bug Reporting System Complete — Phase 2 & 3 (Phase 7):**

**Phase 2: Centralized Collection**
- [x] `.claude/scripts/submit-bug-report.sh` - Auto-submit to GitHub Issues
- [x] `.github/ISSUE_TEMPLATE/bug_report.yml` - Structured issue template
- [x] CLAUDE.md Step 6.5 enhanced - Two-step confirmation (create → submit)
- [x] GitHub CLI integration with graceful fallback
- [x] Issue URL tracking in report metadata
- [x] Auto-create "bug-report" label if missing
- [x] Smart title generation: `[Bug Report][Protocol Type] vX.Y.Z - Status`

**Phase 3: Analytics & Pattern Detection**
- [x] `.claude/scripts/analyze-bug-patterns.sh` - Pattern analyzer (bash 3.2 compatible)
- [x] `/analyze-local-bugs` command - Local bug analysis
- [x] Framework version distribution analysis
- [x] Protocol type distribution (Cold Start vs Completion)
- [x] Top 5 most common errors detection
- [x] Step failure analysis with recommendations
- [x] Auto-generated summary reports

**Quick Update Utility:**
- [x] `quick-update.sh` - Standalone updater for existing framework installations
- [x] Smart detection - auto-downloads init-project.sh if framework not found
- [x] Prevents user confusion between update vs installation

**Framework Developer Mode (Cold Start Protocol):**
- [x] Step 0.4: Automatic bug report checking from GitHub Issues
- [x] Shows count of open reports and recent ones (last 7 days)
- [x] Lists 5 most recent bug reports with titles
- [x] Suggests running `/analyze-bugs` for detailed analysis
- [x] Only runs in framework project (claude-code-starter)
- [x] Non-blocking: gracefully handles missing gh CLI

**Completion Protocol Self-Check:**
- [x] Step 0: Re-read Completion Protocol before execution
- [x] Prevents "сапожник без сапог" problem (forgetting to document changes)
- [x] Self-check questions for metafile updates
- [x] Works for both framework and host projects
- [x] Counters context compaction during long sessions

**System Architecture:**
```
Phase 1: Local Logging → Phase 2: Centralized Collection → Phase 3: Analytics
   (v2.3.0)                      (v2.3.1)                      (v2.3.1)
```

**Privacy & Control:**
- Bug reports created ALWAYS (analytics/telemetry, not just errors)
- Double confirmation (create report + submit to GitHub)
- All analysis runs locally first
- User decides what to share
- Complete anonymization before submission

## Next Phase

- [ ] Monitor bug report patterns from host projects
- [ ] ML-based categorization of recurring issues
- [ ] Auto-fix suggestions for common errors

## npm Commands

```bash
npm install              # Install dependencies
npm run build            # Compile TypeScript
npm run dialog:export    # Export dialogs
npm run dialog:ui        # Web UI :3333
npm run dialog:watch     # Auto-export
```

## Key Concept

Framework is now a **meta-layer over Claude Code** that:
1. Adds structured protocols (Cold Start, Completion)
2. Provides crash recovery
3. Enables dialog export
4. Standardizes documentation

---
*Quick-start context for AI sessions*
