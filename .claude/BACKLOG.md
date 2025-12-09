# BACKLOG — Claude Code Starter Framework

*Последнее обновление: 2025-12-08*

> 📋 **SINGLE SOURCE OF TRUTH для всего планирования фреймворка**
>
> Этот файл объединяет:
> - ✅ Приоритизированные задачи (что делаем сейчас/скоро)
> - 💡 Идеи и пожелания (backlog идей для будущих версий)
> - 🔗 GitHub Issues (ссылки на детальные обсуждения)
> - 📚 Архив (завершённые фазы)

---

## 🎯 Текущие задачи (приоритизированные)

### Phase 4: Distribution v2.1.1 ⏳

**Статус:** В работе
**Цель:** Финализировать v2.1.1 и создать релиз

**Задачи:**
- [ ] Тестирование init-project.sh на legacy проектах
  - [ ] chatRAG (уже протестировано, найдены баги)
  - [ ] Другие проекты с Framework v1.x
- [ ] Создать GitHub Release v2.1.1
  - [ ] Загрузить init-project.sh (5.3KB)
  - [ ] Загрузить framework.tar.gz (56KB)
  - [ ] Написать Release Notes
- [ ] Обновить README.md с инструкциями по установке
- [ ] Объявить релиз пользователям

**GitHub Issues:**
- Связанные: #4 (init-project.sh не копирует .claude/commands/)

---

## 💡 Идеи и пожелания (не приоритизировано)

> Идеи для будущих версий. Ещё не преобразованы в конкретные задачи.
> Источники: FUTURE_IMPROVEMENTS.md, GitHub Issues, user feedback

### 🔥 Priority 1: Critical Enhancements

#### 1. Post-Compact Hook — Auto Context Restoration
**Проблема:** После context compaction AI теряет инструкции из CLAUDE.md
**Решение:** Hook который восстанавливает критический контекст после compaction
**Статус:** Идея, требует исследования Claude Code hooks API
**GitHub Issue:** #12

#### 2. Enhanced `/finalize` Command
**Проблема:** `/fi` работает, но можно улучшить проверки метафайлов
**Идея:** Автоматическая валидация что все метафайлы актуальны
**Статус:** Улучшение существующего функционала
**GitHub Issue:** #11

#### 3. Legacy Project Migration Issues
**Набор багов/улучшений:**
- #4: init-project.sh не копирует .claude/commands/ для legacy
- #7: /migrate пропускает docs/ с мета-документацией
- #3: Ненужный перезапуск Claude Code в инструкции

---

### 🚀 Priority 2: Modular Context Management (v3.0 Vision)

**Концепция:** Работа с огромными проектами (100k+ строк кода)

#### Идеи из FUTURE_IMPROVEMENTS:
1. **Hierarchical CLAUDE.md** — module-level context (#13)
2. **Sprint Focus Declaration** — explicit scope in BACKLOG (#14)
3. **Module Templates** — reusable templates (#15)
4. **Checkpoint Workflow** — /rewind for sprint resume (#16)
5. **Best Practices Guide** — documentation (#17)

**Проблема решает:**
- Large projects overwhelm context window
- AI wastes tokens on irrelevant code
- No clear "resume point" after breaks

**Статус:** Долгосрочная концепция, требует дизайна архитектуры

---

### 🛠️ Priority 3: UX Improvements

#### Migration UX (#2, #5, #6, #9, #10)
- [ ] Интерактивное создание .migrationignore (#2)
- [ ] Прогноз стоимости миграции (токены + $) (#5)
- [ ] Post-Migration Quick Start Guide (#6)
- [ ] Health Check после миграции (#9)
- [ ] Interactive Post-Migration Checklist (#10)

#### Documentation (#8)
- [ ] Стандартизация формата GitHub Issues (#8)
- [ ] Пояснение к 'Continue or commit first?' (#41)

---

## 📚 Архив (завершённые фазы)

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
