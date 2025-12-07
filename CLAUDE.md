# CLAUDE.md — AI Agent Instructions

**Framework:** Claude Code Starter v2.0
**Purpose:** Meta-documentation framework for AI-assisted development

## Triggers

**"start", "начать":**
→ Execute Cold Start Protocol (section below)

**"заверши", "завершить", "finish", "done":**
→ Execute Completion Protocol (section below)

## Cold Start Protocol

### Step 1: Quick Status
Read `SNAPSHOT.md` — current version, what's in progress, pending tasks

### Step 2: Context (on demand)
- `BACKLOG.md` — detailed tasks
- `FUTURE_IMPROVEMENTS.md` — roadmap
- `Init/CLAUDE.md` — template for users (reference)

### Step 3: Confirm
```
Context loaded. Directory: [pwd]
Framework: v2.0 (PR #28 pending / merged)
Ready to work! What's the task?
```

## Completion Protocol

Execute on trigger words. Steps:

### 1. Update Metafiles
- `BACKLOG.md` — mark completed tasks `[x]`
- `SNAPSHOT.md` — update date, status
- `CHANGELOG.md` — add entry (if release)

### 2. Git Commit
```bash
git add -A
git status
git commit -m "$(cat <<'EOF'
type: Brief description

- Detail 1
- Detail 2

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>
EOF
)"
```

Commit types: `feat:`, `fix:`, `docs:`, `refactor:`, `chore:`

### 3. Ask About Push
```
Commit created. Push to remote?
```

## Repository Structure

```
Project_init/
├── Init/                   # Russian templates (v2.0)
│   ├── CLAUDE.md          # AI instructions template
│   ├── SNAPSHOT.md        # Project state template
│   ├── .claude/commands/  # 18 slash commands
│   └── .claude-export/    # Dialog export utility (NEW!)
│
├── init_eng/              # English templates (sync pending)
│
├── init-project.sh        # Installer v2.0.0
├── init-starter.zip       # Russian archive (316KB)
├── init-starter-en.zip    # English archive (sync pending)
│
├── CLAUDE.md              # THIS FILE (framework context)
├── SNAPSHOT.md            # Current state (v2.0)
├── BACKLOG.md             # Tasks
├── CHANGELOG.md           # Version history
└── README.md / README_RU.md
```

## Development Workflow

### Making Changes to Templates
1. Edit files in `Init/` (Russian version)
2. Sync to `init_eng/` (English version)
3. Update CHANGELOG.md
4. Regenerate ZIP archives
5. Use `/release` for version bumps

### Testing Installation
```bash
# Test in temp directory
mkdir /tmp/test-project && cd /tmp/test-project
cp /path/to/init-starter.zip .
cp /path/to/init-project.sh .
bash init-project.sh
```

## Key Concepts (v2.0)

### Simplified Structure
- CLAUDE.md + PROCESS.md → single CLAUDE.md (-48% lines)
- PROJECT_SNAPSHOT.md → SNAPSHOT.md (shorter name)
- Clear trigger words for protocols

### New Features
- Crash recovery via `.last_session`
- Dialog export utility integrated
- `/fi` completion command
- npm scripts auto-injection

### Principles
- **Single Source of Truth** — one place per concept
- **Token Economy** — minimal context loading
- **Security by Default** — see SECURITY.md

## Slash Commands

Framework-specific:
- `/release` — create new release
- `/commit` — create git commit
- `/pr` — create pull request

Template commands (in Init/.claude/commands/):
- `/fix`, `/feature`, `/review`, `/test`
- `/security`, `/explain`, `/refactor`, `/optimize`
- `/migrate`, `/migrate-resolve`, `/migrate-finalize`
- `/fi` — completion protocol (NEW!)

## Warnings

- DO NOT change version manually — use `/release`
- DO NOT modify Init/ without syncing init_eng/
- DO NOT commit without updating CHANGELOG.md
- ALWAYS read SNAPSHOT.md before starting work
- ALWAYS sync both language versions

## Links

- **Repository:** https://github.com/alexeykrol/claude-code-starter
- **PR #28:** https://github.com/alexeykrol/claude-code-starter/pull/28
- **Courses:** https://alexeykrol.com/courses/

---
*Framework: Claude Code Starter v2.0 | Updated: 2025-12-07*
