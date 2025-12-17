# BACKLOG — Claude Code Starter Framework

*Последнее обновление: 2025-12-16*

> 📋 **SINGLE SOURCE OF TRUTH для текущих задач**
>
> Этот файл содержит только конкретные согласованные задачи, которые точно делаем.
>
> **Workflow:**
> - 💡 Сырые идеи → [IDEAS.md](./IDEAS.md)
> - 🗺️ Структурированные фичи (v2.2+) → [ROADMAP.md](./ROADMAP.md)
> - 🎯 Конкретные задачи (сейчас) → **BACKLOG.md** (этот файл)
> - ✅ Завершенное → Архив (внизу)

---

## 🎯 Текущие задачи (приоритизированные)

### Phase 7: Bug Reporting System — Phase 2 & 3 v2.3.1 ✅

**Статус:** Завершено
**Цель:** Завершить bug reporting систему — централизованная коллекция и аналитика

**Задачи:**
- [x] **Phase 2: Centralized Collection**
  - [x] Создать submit-bug-report.sh для автоматической отправки в GitHub Issues
  - [x] Создать GitHub issue template (.github/ISSUE_TEMPLATE/bug_report.yml)
  - [x] Обновить CLAUDE.md Step 6.5 — два этапа подтверждения (create → submit)
  - [x] Обновить build-distribution.sh для копирования submit script
  - [x] Тестирование: syntax check, gh CLI availability
- [x] **Phase 3: Analytics & Pattern Detection**
  - [x] Создать analyze-bug-patterns.sh (bash 3.2 compatible)
  - [x] Реализовать анализ: версии, протоколы, ошибки, шаги
  - [x] Генерация recommendations и summary файлов
  - [x] Создать /analyze-local-bugs command
  - [x] Обновить build-distribution.sh для копирования analyze script
  - [x] Тестирование: работает с пустыми и заполненными логами

**Результат:**
- Полная 3-фазная система bug reporting (Local → Centralized → Analytics)
- Автоматическое обнаружение паттернов и рекомендации
- Privacy-first с двойным подтверждением
- Совместимость с bash 3.2+ (macOS)

---

## 📚 Архив (завершённые фазы)

### Phase 6: Bug Reporting & Logging System v2.3.0 ✅

**Статус:** Завершено
**Цель:** Добавить систему логирования протоколов и анонимных bug reports

**Задачи:**
- [x] Спроектировать систему bug reporting
  - [x] Opt-in consent dialog (privacy-first)
  - [x] Anonymization стратегия (paths, keys, emails, IPs)
  - [x] Framework Developer Mode для сбора отчетов
- [x] Реализовать Step 0.15: Bug Reporting Consent
  - [x] First-run consent dialog
  - [x] .framework-config структура
  - [x] Opt-in по умолчанию (disabled)
- [x] Реализовать Step 0.3: Protocol Logging
  - [x] Cold Start logging с timestamps
  - [x] log_step() и log_error() функции
  - [x] Лог файлы в .claude/logs/cold-start/
- [x] Реализовать Completion Protocol Logging
  - [x] Step 0: Initialize Completion Logging
  - [x] Step 6.5: Finalize Log & Create Bug Report
  - [x] Автоматическое обнаружение ошибок
- [x] Создать /bug-reporting command
  - [x] enable/disable/status/test подкоманды
  - [x] Показывать статистику логов
- [x] Создать anonymization script
  - [x] .claude/scripts/anonymize-report.sh
  - [x] Удаление paths, API keys, tokens, emails, IPs
  - [x] Замена project name на {project}_anon
- [x] Реализовать Framework Developer Mode
  - [x] Step 0.4: Read Bug Reports from Host Projects
  - [x] Проверка открытых Issues с label "bug-report"
  - [x] Активируется только на framework project
- [x] Создать /analyze-bugs command
  - [x] Fetch reports from GitHub Issues
  - [x] Группировка по типу ошибок
  - [x] Генерация analysis файлов
- [x] Обновить build system
  - [x] build-distribution.sh копирует scripts и templates
  - [x] init-project.sh генерирует .framework-config
  - [x] .gitignore для .claude/logs/
- [x] Тестирование на santacruz
  - [x] Config creation ✅
  - [x] Cold Start logging ✅
  - [x] /bug-reporting status ✅
  - [x] Anonymization script ✅
  - [x] Все файлы на месте ✅

---

## 📚 Архив (завершённые фазы)

<details>
<summary>Phase 5: Auto-Update Framework v2.2.4 ✅ (2025-12-16)</summary>

**Завершено:** Система автоматического обновления фреймворка

**Ключевые достижения:**
- Step 0.2: Framework Version Check в Cold Start Protocol
- Парсинг версии из CLAUDE.md и GitHub API
- Aggressive update strategy (без подтверждения пользователя)
- framework-commands.tar.gz для быстрых обновлений
- Обновление только framework файлов, данные проекта не затрагиваются
- Тестирование на santacruz: v2.2 → v2.2.4 успешно

</details>

<details>
<summary>Phase 4: Distribution v2.2.3 ✅ (2025-12-16)</summary>

**Завершено:** Финализация v2.2.3 с критическими исправлениями

**Ключевые достижения:**
- Успешная миграция santacruz v1.x → v2.2
- Исправлены 4 критических бага (BUG-001 до BUG-004)
- Migration reports теперь обязательны
- Упрощенные qualifying questions
- Corrected GitHub Release v2.2.3

</details>

<details>
<summary>Phase 3.5: Bug Fixes v2.1.1 ✅ (2025-12-08)</summary>

### Исправленные баги:
1. **watcher.ts parasitic folders** — Fixed cwd to prevent `project-name-dialog` folders
2. **sed escaping** — Added `sed_escape()` function for special characters
3. **Token economy** — Redesigned to loader pattern (88KB → 5.3KB, 16.6x!)
4. **Legacy metafile preservation** — Don't overwrite existing SNAPSHOT/BACKLOG/ARCHITECTURE

**Source:** BUG_REPORT_FRAMEWORK.md from chatRAG production testing

</details>

<details>
<summary>Phase 3: Installation System ✅ (2025-12-08)</summary>

- [x] migration/templates/ structure
- [x] init-project.sh loader (5.3KB)
- [x] build-distribution.sh
- [x] README cleanup
- [x] dist-release/ gitignored

</details>

<details>
<summary>Phase 2: Protocol Verification ✅</summary>

- [x] Cold Start Protocol implemented
- [x] Completion Protocol (/fi) implemented
- [x] Dialog Export UI (Teacher + Student)
- [x] Crash Recovery tested

</details>

<details>
<summary>Phase 1: Framework Restructuring ✅ (v2.0.0)</summary>

- [x] src/claude-export/ TypeScript source
- [x] dist/claude-export/ compiled
- [x] npm project structure
- [x] Full protocols in CLAUDE.md

</details>

<details>
<summary>v1.4.3 — Sprint Completion ✅ (2025-10-23)</summary>

- 5-layer reminder system
- Sprint Completion Protocol
- Dogfooding (framework uses itself)

</details>

<details>
<summary>v1.4.0 — Cold Start ✅ (2025-10-11)</summary>

- PROJECT_SNAPSHOT.md template
- 85% token economy improvement

</details>

---

## 📊 Структура текущей версии (v2.1.1)

```
claude-code-starter/
├── src/claude-export/     # TypeScript source
├── dist/claude-export/    # Compiled JS
├── .claude/
│   ├── commands/          # 19 slash commands
│   ├── SNAPSHOT.md        # Current state
│   ├── ARCHITECTURE.md    # Code structure
│   └── BACKLOG.md         # THIS FILE
├── migration/
│   ├── init-project.sh    # Installer template (5.3KB)
│   ├── build-distribution.sh
│   └── templates/         # Meta file templates
├── dialog/                # Dialog exports
├── package.json           # npm scripts
├── CLAUDE.md              # AI protocols
├── CHANGELOG.md           # Version history
└── README.md / README_RU.md
```

---

## 🔗 Связанные документы

- [SNAPSHOT.md](./.claude/SNAPSHOT.md) — текущее состояние
- [ARCHITECTURE.md](./.claude/ARCHITECTURE.md) — структура кода
- [CLAUDE.md](../CLAUDE.md) — протоколы AI
- [CHANGELOG.md](../CHANGELOG.md) — полная история
- [GitHub Issues](https://github.com/alexeykrol/claude-code-starter/issues) — детальные обсуждения

---

## 📝 Процесс работы с BACKLOG

### Для разработчика:
1. **Начало работы:** Проверить "Текущие задачи"
2. **Новая идея:** Добавить в "Идеи и пожелания"
3. **Приоритизация:** Переместить из идей в задачи когда готовы
4. **Завершение:** Переместить в архив, обновить CHANGELOG

### Для AI:
1. **Cold Start:** Читать "Текущие задачи" для контекста
2. **Planning:** Превращать идеи в конкретные задачи по запросу
3. **Completion:** Обновлять статусы, переносить в архив

---

*Обновляй после каждой завершенной задачи или новой идеи!*
