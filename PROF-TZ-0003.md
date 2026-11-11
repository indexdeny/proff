# PROF-TZ-0003 — Isolated Git Repository, Security Gates & Verified Checkpoints

**Project:** PsychoPassport Engine (`proff`)
**Task ID:** `TZ-0003-isolated-git-checkpoints`
**Phase:** PH-03
**Task Class:** COMPLEX
**Primary Engine:** Architecture + Workflow
**Secondary Engine:** Red Team
**Governance:** PGSM v1.0.0
**Current Structure Version:** 1.1.0
**Current State Revision:** 4
**Target Structure Version:** 1.2.0, conditional
**Environment:** Windows / PowerShell 5.1 / Git 2.38.1
**Execution:** Antigravity IDE
**Status:** READY FOR EXECUTION

---

# 1. Goal

Создать независимую, безопасную и восстанавливаемую систему
версионирования PsychoPassport Engine.

Внедрить:

1. Независимый локальный Git-репозиторий.
2. Защиту исходных персональных данных от Git tracking.
3. Доказательную проверку R0 backup.
4. Классификацию файлов перед первым коммитом.
5. Политику обязательных Git checkpoints.
6. Workspace Rule для контроля Git-операций.
7. Контроль SHA-256 локальных и удалённых состояний.
8. Подготовку к приватному GitHub remote.
9. Восстановимый процесс при сбоях.
10. Полную интеграцию с PGSM.

Создание GitHub-репозитория и push допускаются
только после отдельного явного разрешения пользователя.

Не использовать существующие удалённые репозитории
предыдущих проектов.

---

# 2. Project Boundary

Единственный разрешённый корень записи:

`C:\Users\candy\Desktop\lil_projects\proff`

Все операции выполняются внутри него.

## 2.1 Allowed Read Scope

Разрешено читать:

- Project Root и его технические конфигурации.
- `AGENTS.md`
- `governance/`
- `project_state/`
- `.agents/`
- `.gitignore`
- `README.md`
- относящиеся к задаче технические документы.

Разрешено проверять наличие `tg_save/`
исключительно по метаданным директории.

Запрещено открывать файлы внутри `tg_save/`.

## 2.2 Allowed Write Scope

Разрешены изменения:

- `.git/`, после прохождения Preflight Gate.
- `.gitignore`
- `.agents/rules/`
- `AGENTS.md`, только минимальная ссылка на Git policy.
- `governance/`
- `project_state/`
- task-specific reports.

## 2.3 Forbidden Scope

Запрещены изменения:

- родительских директорий;
- глобального Git configuration;
- Windows Credential Manager;
- Global Antigravity configuration;
- Global Rules, Skills, Plugins, MCP и Hooks;
- конфигураций других проектов;
- существующих GitHub-репозиториев;
- любых файлов внутри `tg_save/`.

Запрещено создавать symlinks, junctions или hardlinks
для обхода границы проекта.

## 2.4 Network Boundary

До отдельного пользовательского разрешения:

- никаких GitHub repository creation;
- никаких push;
- никаких remote configuration writes;
- никаких GitHub Actions;
- никаких отправок конфиденциальных файлов.

Разрешена локальная Git-инициализация
после выполнения всех защитных проверок.

---

# 3. Context

## 3.1 Previous Tasks

`TZ-0001-workspace-bootstrap`

Status: COMPLETED
Structure Version: 1.0.0

`TZ-0002-environment-audit`

Status: COMPLETED according to WALKTHROUGH
Structure Version: 1.1.0
State Revision: 4

## 3.2 Current Environment

Согласно предыдущему Discovery:

- PowerShell: 5.1
- Git: 2.38.1.windows.1
- Python: NOT_AVAILABLE
- Antigravity CLI (`agy`): NOT_AVAILABLE
- Git repository: NO_GIT_REPOSITORY
- Knowledge Base: IMPORT_PENDING

Эти значения являются историческими результатами.

До выполнения операций повторно проверить
фактическое состояние окружения.

## 3.3 Existing Recovery Baseline

Предыдущим заданием созданы:

`project_state/tasks/TZ-0002-environment-audit/R0_BACKUP.zip`

`project_state/tasks/TZ-0002-environment-audit/R0_MANIFEST.json`

Согласно отчёту:

- 29 файлов;
- размер архива 54 947 байт;
- restore-test: PASS.

Однако обнаружено расхождение SHA-256.

R0_MANIFEST.json:

`9AA491D6E08F4DF733E0022B4F0175F2FBBD7D0A75B960D1FA81ECDCA9121267`

WALKTHROUGH.md:

`51FDC91FDCFBEB5A5C782944359D461FDC20BBE4484E9D0219C481EC1F2DB6E4`

Расхождение требует разрешения до Git init.

Не объявлять ни один из двух хешей правильным
без физической проверки архива.

## 3.4 Previous Audit Findings

C-01:
20 GCP/Data Skills помечены как EXACT_DUPLICATE.

C-02:
Notebook MCP semantic overlap.

C-03:
Science Plugin irrelevant.

C-04:
Android Plugin irrelevant.

C-05:
Unconfigured GCP integrations.

C-06:
Science visualization rule overlap.

Эти находки не относятся к разрешённым
операциям модификации в настоящем задании.

Не удалять и не отключать перечисленные компоненты.

## 3.5 Known Governance Discrepancies

1. ADR-0001–0005 зарегистрированы,
   но отдельные ADR-файлы не подтверждены.

2. VAL-10:
   IDE Rule Activation = NOT_VERIFIED.

3. WALKTHROUGH:
   RULE_ACTIVATION обозначен PASS,
   но фактически подтверждена только статическая проверка.

4. В предыдущем Validation выполнено хеширование файлов
   внутри `tg_save/`, несмотря на запрет чтения содержимого.

5. Указание EXACT_DUPLICATE для 20 Skills
   не подкреплено представленной побайтовой сверкой.

Все расхождения необходимо учесть.

Запрещено переписывать исторические отчёты
ради устранения несоответствий.

---

# 4. Assumptions

1. Проект ещё не является Git-репозиторием.
2. Git установлен и доступен.
3. Пользователь разрешает локальную Git-инициализацию.
4. Пользователь не давал разрешения создавать GitHub remote.
5. Пользователь не давал разрешения изменять глобальную Git identity.
6. Пользовательские переписки являются конфиденциальными.
7. R0 backup существует физически, но требует проверки.
8. Рабочая среда рассчитана на последовательное выполнение задач.
9. Внешняя синхронизация будет включена позднее.
10. Другие проекты могут использовать те же глобальные настройки.

При несовпадении любого допущения с Discovery
исполнитель обязан скорректировать план
без нарушения Invariants.

---

# 5. Scope

## Included

- Project Discovery.
- Git boundary verification.
- Recovery baseline integrity audit.
- File classification.
- Gitignore hardening.
- Secret and personal-data exposure assessment.
- Independent local repository initialization.
- Initial Git checkpoint.
- Local Git policy.
- Workspace Git Rule.
- ADR for Git isolation.
- Negative tests.
- PGSM synchronization.
- GitHub readiness report.

## Excluded

- GitHub repository creation without approval.
- Automatic remote push.
- Global Git configuration changes.
- Git credential modification.
- Global Plugins/Skills cleanup.
- Python installation.
- Scientific literature import.
- Telegram data ingestion.
- Profiling engine implementation.
- LLM/API integration.
- CI/CD deployment.
- GitHub Actions creation.
- Automatic cloud backups.

---

# 6. Discovery Phase

Discovery обязателен до изменения любых файлов.

## 6.1 Read Governance

Прочитать:

1. `AGENTS.md`
2. `project_state/CURRENT_STATE.md`
3. `project_state/ROADMAP.md`
4. `project_state/TASK_REGISTER.md`
5. `project_state/ISSUES.md`
6. `project_state/DECISIONS.md`
7. `project_state/structure/STRUCTURE.md`
8. `project_state/structure/STRUCTURE_CHANGELOG.md`
9. `governance/policies/privacy_boundary.md`
10. `governance/policies/recovery_policy.md`
11. `project_state/tasks/TZ-0002-environment-audit/WALKTHROUGH.md`
12. `project_state/tasks/TZ-0002-environment-audit/VALIDATION.md`
13. `project_state/tasks/TZ-0002-environment-audit/R0_MANIFEST.json`

Проверить фактическое дерево проекта.

Не предполагать, что перечисленные файлы
существуют только потому, что они указаны в отчёте.

## 6.2 Git Discovery

Выполнить из Project Root:

```powershell
git --version
git rev-parse --is-inside-work-tree
git rev-parse --show-toplevel
git remote -v
```

Для нового репозитория ожидается:

- Git executable доступен;
- `rev-parse` сообщает отсутствие репозитория;
- существующих remotes нет.

Если обнаружен Git root,
отличный от Project Root:

STOP.

Не создавать вложенный репозиторий автоматически.

Проверить фактическую структуру,
не изменяя родительский Git.

## 6.3 Filesystem Identity

Проверить:

- canonical path;
- non-reparse root;
- фактические файловые права;
- существующие `.git` entries;
- вложенные Git-репозитории;
- symlinks/junctions в потенциально отслеживаемых путях;
- состояние `.gitignore`;
- наличие task collision.

## 6.4 Git Identity

Проверить эффективные значения:

```powershell
git config --show-origin --get user.name
git config --show-origin --get user.email
```

Не публиковать персональный email в отчётах.

Допускается отметить:

- identity configured;
- identity missing;
- identity source;
- identity scope.

Если identity отсутствует:

STOP перед первым commit.

Запросить у пользователя разрешённую Git identity.

Не устанавливать вымышленные имя/email.

## 6.5 Discovery Output

Создать:

`project_state/tasks/TZ-0003-isolated-git-checkpoints/DISCOVERY.md`

Содержимое:

- verified root;
- effective Git version;
- current Git boundary;
- Git identity readiness без раскрытия email;
- filesystem link inventory;
- R0 availability;
- existing task records;
- known issues;
- preflight results.

Если обнаружено критическое несоответствие,
не продолжать Git init.

---

# 7. Functional Requirements

## FR-01. Recovery Baseline Verification

Проверить R0 до любых Git mutations.

Алгоритм:

1. Найти физический R0_BACKUP.zip.
2. Вычислить его фактический SHA-256.
3. Сравнить с R0_MANIFEST.json.
4. Сравнить с предыдущим WALKTHROUGH.
5. Проверить структуру ZIP.
6. Проверить наличие всех 29 заявленных файлов.
7. Проверить отсутствие лишних записей.
8. Выполнить безопасное пробное извлечение.
9. Сверить хеши восстановленных файлов.
10. Документировать результат.

Перед распаковкой проверить ZIP entries:

- нет абсолютных путей;
- нет `..` traversal;
- нет путей за Project Root;
- нет symlink escapes;
- нет файлов вне разрешённого набора.

Восстановление выполнять только
в специально созданный временный каталог
внутри Project Root.

Не перезаписывать рабочие файлы.

Если фактический архив не соответствует manifest:

`R0_INTEGRITY_FAILURE`.

Зарегистрировать ISSUE.

Остановить Git init.

Не исправлять контрольные суммы задним числом.

Новый backup вместо старого допускается
только отдельным документированным решением.

## FR-02. Sensitive Data Classification

Все потенциальные Git artifacts разделить на категории:

`GIT_REQUIRED`

Нормативные документы, код, тесты,
проектные правила, безопасные шаблоны.

`GIT_EXCLUDED`

Персональные переписки, медиа, секреты,
временные файлы, результаты анализа,
локальные backup, кеши.

`REVIEW_REQUIRED`

Файлы с неизвестным содержимым,
сомнительной лицензией или чувствительными данными.

Файл категории REVIEW_REQUIRED не может быть
автоматически добавлен в Git.

## FR-03. GitIgnore Contract

Обеспечить исключение:

- `tg_save/`
- `inputs/raw_exports/`
- `inputs/source_staging/` кроме безопасных `.gitkeep`
- персональных кейсов;
- аудио/видео исходников;
- приватных транскриптов;
- outputs с результатами анализа;
- `.env` и аналогичных локальных конфигураций;
- credentials/tokens/private keys;
- backup archives;
- `.venv/`;
- Python caches;
- IDE caches;
- temporary directories;
- случайных дампов данных.

Не исключать без необходимости:

- `AGENTS.md`;
- workspace rules;
- governance policies;
- PGSM records;
- безопасные схемы;
- исходный код;
- тесты без персональных данных.

Общее расширение файла не является
достаточным доказательством его безопасности.

Не ослаблять существующие исключения
ради прохождения тестов.

## FR-04. Native GitIgnore Testing

После инициализации Git выполнить
реальные проверки через `git check-ignore`.

Примеры категорий:

1. Telegram export.
2. Raw audio.
3. Raw video.
4. Personal transcript.
5. Environment secret.
6. Private key.
7. Backup ZIP.
8. Cache.
9. Workspace Rule.
10. Governance file.
11. Task record.
12. README.

Ожидаемое поведение определить
по классификации файла.

Для игнорируемых путей `git check-ignore`
должен подтвердить совпадение.

Для trackable путей отсутствие совпадения
является ожидаемым результатом.

Не трактовать любой ненулевой exit code
как ошибку тестирования.

## FR-05. Secret Exposure Gate

Перед первым commit проверить staged contents.

Искать:

- API keys;
- access tokens;
- passwords;
- private keys;
- authentication cookies;
- connection strings with credentials;
- embedded authentication headers;
- personal communication content;
- private reports;
- unexpected binary attachments.

Использовать доступные локальные инструменты.

Не отправлять содержимое файлов внешним сервисам
для проверки секретов.

При обнаружении секрета:

1. Остановить commit.
2. Исключить файл из staging.
3. Зафиксировать sanitized finding.
4. Не выводить значение секрета.
5. Запросить решение при необходимости.

Не считать regex-only проверку абсолютной
гарантией отсутствия секретов.

## FR-06. Initial Git Repository

Создать независимый локальный Git repository
только после прохождения всех защитных gates.

Условия:

- canonical root verified;
- R0 verified;
- no unsafe staged files;
- valid Git identity;
- no inherited repository conflict;
- no unresolved blocking security issue.

Инициализировать ветку `main`.

После init проверить:

```powershell
git rev-parse --show-toplevel
git branch --show-current
git status --porcelain
```

Точный Git top-level должен совпасть
с canonical Project Root.

Если совпадения нет:

STOP.

## FR-07. Initial Checkpoint

Перед commit сформировать
список staged files.

Использовать точечное добавление
разрешённых файлов.

Не выполнять слепой `git add -A`
до завершения полной классификации.

Commit message:

`TZ-0003: initialize isolated proff repository`

Сохранить:

- commit SHA;
- branch;
- staged file count;
- committed file count;
- validation results.

Не создавать пустой фиктивный commit,
если необходимые проверки не пройдены.

## FR-08. Git Policy

Создать:

`governance/git_policy.md`

Обязательные разделы:

1. Repository ownership.
2. Project Boundary.
3. Pre-task Git checks.
4. File classification.
5. Secret scanning.
6. Local checkpoints.
7. Remote authorization.
8. Allowed branches.
9. Push and SHA verification.
10. Failure recovery.
11. Human approval gates.
12. Forbidden destructive commands.

## FR-09. Always-On Git Rule

Создать:

`.agents/rules/03-git-checkpoints.md`

Использовать подтверждённый синтаксис
Antigravity Workspace Rules.

Назначение:

- проверка Git перед задачей;
- запрет коммитов с секретами;
- разрешённый staging;
- task-specific commit;
- проверка локального HEAD;
- подтверждение remote SHA при разрешённом push;
- PUSH_PENDING при отсутствии разрешения;
- запрет destructive Git operations.

Не дублировать полный git_policy.md.

В `AGENTS.md` добавить только короткую
обязательную ссылку на правило/политику,
если это совместимо с существующими инструкциями.

## FR-10. GitHub Readiness

Проверить наличие GitHub CLI,
если это возможно без внешних мутаций.

```powershell
gh --version
```

Если `gh` отсутствует:

`GH_CLI_NOT_AVAILABLE`.

Не устанавливать его автоматически.

Не выполнять login.

Не читать и не выводить credential store.

Создать GitHub readiness report с полями:

- GitHub owner: UNKNOWN / VERIFIED;
- desired repository name: UNKNOWN / APPROVED;
- visibility: PRIVATE_REQUIRED;
- authentication readiness;
- remote creation authorization: NOT_GRANTED;
- push authorization: NOT_GRANTED;
- local commit SHA;
- next action.

До явного разрешения не создавать remote.

---

# 8. Architecture / Workflow Requirements

## 8.1 Repository Ownership

Git управляет:

- исходным кодом;
- проектной архитектурой;
- Rules;
- Skills конфигурациями, когда они появятся;
- тестами;
- нормативными документами;
- схемами;
- PGSM history.

Git не является хранилищем:

- приватных переписок;
- исходных медиа;
- персональных паспортов;
- credentials;
- резервных копий с чувствительными файлами;
- крупных научных PDF без проверки прав.

## 8.2 Checkpoint Lifecycle

Целевой поток:

`DISCOVERY`

↓

`R0_VERIFICATION`

↓

`FILE_CLASSIFICATION`

↓

`SECURITY_PREFLIGHT`

↓

`LOCAL_GIT_INIT`

↓

`STAGED_CONTENT_REVIEW`

↓

`LOCAL_COMMIT`

↓

`LOCAL_SHA_VERIFICATION`

↓

`REMOTE_APPROVAL_GATE`

↓

`PUSH_PENDING` или `REMOTE_VERIFIED`

Для текущего ТЗ штатный результат:

`LOCAL_CHECKPOINT_VERIFIED`

Допустимое отсутствие GitHub remote
не является ошибкой локального checkpoint.

## 8.3 Remote Verification

Если пользователь отдельно разрешил
создание приватного GitHub-репозитория,
перед сетевыми операциями дополнительно проверить:

- точный GitHub account/owner;
- точное имя репозитория;
- видимость PRIVATE;
- отсутствие конфликта существующего remote;
- отсутствие чувствительных файлов в истории;
- разрешение на push.

После разрешённого push:

1. Получить local HEAD SHA.
2. Получить remote branch SHA.
3. Сравнить SHA.
4. Проверить PRIVATE visibility.
5. Сохранить подтверждение.

Не считать успешный вывод `git push`
достаточным доказательством remote parity.

В рамках настоящего ТЗ,
если отдельное разрешение отсутствует,
этот этап остаётся `PUSH_PENDING`.

## 8.4 Failure Handling

Если Git init не выполнен:

- не объявлять репозиторий созданным;
- сохранить Discovery и ISSUE;
- не пытаться автоматически обходить ограничения.

Если commit не выполнен:

- сохранить текущее состояние;
- не использовать `reset --hard`;
- зарегистрировать причину;
- не удалять staged files.

Если remote недоступен:

- сохранить локальный commit;
- установить PUSH_PENDING;
- не выполнять force push.

Если обнаружены sensitive files:

- остановить staging/commit;
- исключить обнаруженные файлы;
- документировать причину без раскрытия данных.

## 8.5 PGSM Ownership

`CURRENT_STATE.md`
— единственный актуальный статус.

`TASK_REGISTER.md`
— история задач.

`DECISIONS.md`
— индекс ADR.

`project_state/decisions/`
— самостоятельные ADR-документы.

`STRUCTURE.md`
— действующая структура каталогов.

`STRUCTURE_CHANGELOG.md`
— журнал версий структуры.

`WALKTHROUGH.md`
— результаты фактически выполненной задачи.

---

# 9. Architecture Decision Records

Необходимо оформить новое решение:

`ADR-0006-git-isolation.md`

при условии, что Discovery подтвердит:
ADR-0001–ADR-0005 уже заняты.

Расположение:

`project_state/decisions/ADR-0006-git-isolation.md`

Содержимое:

- Context;
- Problem;
- Alternatives;
- Decision;
- Consequences;
- Security impact;
- Recovery implications;
- Approval references.

Не создавать фиктивные ADR-0001–ADR-0005.

Не реконструировать исторические решения
из кратких записей реестра без первичных материалов.

Зафиксировать существующий documentation gap
как отдельный tracked issue.

Если новый каталог `project_state/decisions/`
создаётся впервые, это архитектурное расширение.

Повысить Structure Version:

`1.1.0 → 1.2.0`

Создать:

`project_state/structure/versions/v1.2.0.md`

Обновить:

- STRUCTURE.md;
- STRUCTURE_CHANGELOG.md;
- CURRENT_STATE.md.

Если Discovery обнаружит, что каталог уже
предусмотрен действующим контрактом структуры,
применить соответствующее правило PGSM
и не повышать версию без основания.

---

# 10. Invariants

I-01.
Project Root является единственной границей записи.

I-02.
Никаких изменений родительских Git repositories.

I-03.
Никаких изменений Global Git Config.

I-04.
Никаких секретов в Git.

I-05.
Никаких персональных переписок в Git.

I-06.
Никаких файлов из `tg_save/` в Git.

I-07.
Не читать содержимое `tg_save/`.

I-08.
Не использовать Git как замену резервному копированию.

I-09.
Не переписывать Git history.

I-10.
Не выполнять force push.

I-11.
Не выполнять destructive reset.

I-12.
Не удалять существующие project artifacts.

I-13.
Не подменять исторические snapshots.

I-14.
CURRENT_STATE.md остаётся единственным SSOT.

I-15.
Не создавать GitHub remote без разрешения.

I-16.
Не объявлять remote sync успешной без SHA parity.

I-17.
Не менять Global Rules, Skills, Plugins, MCP.

I-18.
Каждый новый каталог учитывается в PGSM structure contract.

I-19.
Любой PASS подтверждается фактической проверкой.

I-20.
Нельзя продолжать после провала security gate.

I-21.
Между финальной проверкой staging и commit
не должно происходить неконтролируемых изменений
индекса или набора файлов.

I-22.
Фактическая загрузка Workspace Rule не может
считаться подтверждённой одной проверкой Markdown.

---

# 11. Implementation Steps

## Stage A — Discovery & Recovery

1. Прочитать AGENTS.md и CURRENT_STATE.md.

2. Прочитать ROADMAP.md и TASK_REGISTER.md.

3. Прочитать STRUCTURE.md и предыдущий WALKTHROUGH.

4. Проверить canonical Project Root.

5. Проверить фактический Git boundary.

6. Проверить доступную Git identity.

7. Проверить отсутствие конкурирующей активной задачи.

8. Создать task directory.

9. Сохранить утверждённый текст задания в TZ.md.

10. Зарегистрировать задачу в TASK_REGISTER.md.

11. Создать новый immutable state snapshot
    для перехода IN_PROGRESS.

12. Обновить CURRENT_STATE.md.

13. Вычислить фактический SHA-256 R0_BACKUP.zip.

14. Сверить архив с R0_MANIFEST.json.

15. Проверить безопасную структуру ZIP entries.

16. Выполнить test restore в разрешённом временном каталоге.

17. Сравнить все восстановленные файлы с manifest.

18. Сохранить R0_INTEGRITY_REPORT.md.

19. При FAIL остановить Git-часть задачи
    и зарегистрировать blocking issue.

## Stage B — Git Security Design

20. Составить полный inventory кандидатов для Git.

21. Классифицировать кандидатов:
    GIT_REQUIRED / GIT_EXCLUDED / REVIEW_REQUIRED.

22. Сохранить FILE_CLASSIFICATION.md.

23. Проверить действующий `.gitignore`.

24. Добавить отсутствующие защитные исключения,
    если они обоснованы.

25. Проверить, что R0 archive исключён из Git.

26. Проверить, что персональные каталоги исключены.

27. Сформировать локальную политику git_policy.md.

28. Проверить формат Workspace Rules.

29. Создать `.agents/rules/03-git-checkpoints.md`.

30. Проверить синтаксис правила.

31. Проверить фактическую загрузку правила,
    если доступен поддерживаемый механизм IDE.

32. Зафиксировать RULE_ACTIVATION как
    VERIFIED / NOT_VERIFIED / FAILED.

## Stage C — Repository Initialization

33. Повторно проверить Git boundary непосредственно
    перед инициализацией.

34. Проверить все blocking gates.

35. Инициализировать независимый Git в Project Root.

36. Проверить `git rev-parse --show-toplevel`.

37. Проверить текущую ветку.

38. Проверить отсутствие remote.

39. Выполнить нативные negative tests `.gitignore`.

40. Подготовить точный список файлов для staging.

41. Добавить только разрешённые файлы.

42. Проверить staged filenames.

43. Проверить staged content на секреты.

44. Проверить staged content на персональные данные.

45. Проверить отсутствие symlink escape.

46. При FAIL остановить commit.

47. При PASS создать initial commit.

48. Получить local HEAD SHA.

49. Проверить Git status после commit.

50. Сохранить LOCAL_CHECKPOINT_RECEIPT.json.

## Stage D — Architecture Governance

51. Проверить реестр ADR и фактические ADR-файлы.

52. Зафиксировать documentation gap
    по историческим ADR.

53. Создать новый ADR для Git isolation.

54. Если введён новый каталог решений,
    обновить Structure Version до 1.2.0.

55. Обновить STRUCTURE.md.

56. Добавить запись в STRUCTURE_CHANGELOG.md.

57. Создать immutable structure version snapshot.

58. Проверить ссылочную целостность ADR.

## Stage E — Remote Readiness

59. Проверить доступность GitHub CLI.

60. Проверить отсутствие существующего remote,
    если пользователь не разрешал его создавать.

61. Создать GITHUB_READINESS.md.

62. Зафиксировать Remote Authorization = NOT_GRANTED,
    если отдельное разрешение отсутствует.

63. Установить статус PUSH_PENDING
    для удалённой синхронизации.

64. Не создавать GitHub repository.

65. Не выполнять push.

## Stage F — Finalization

66. Проверить отсутствие tracked sensitive files.

67. Проверить local HEAD.

68. Проверить Git working tree status.

69. Проверить PGSM structure contract.

70. Проверить сохранность исторических state snapshots.

71. Проверить актуальность TASK_REGISTER.md.

72. Проверить ISSUES.md.

73. Проверить DECISIONS.md.

74. Проверить CHANGELOG.md.

75. Создать VALIDATION.md.

76. Создать WALKTHROUGH.md.

77. Подготовить финальный PGSM state snapshot.

78. Обновить CURRENT_STATE.md.

79. Создать завершающий Git checkpoint,
    если после initial commit изменены
    разрешённые governance-файлы.

80. Проверить, что HEAD содержит финальное
    состояние задачи и что рабочее дерево чистое,
    кроме заведомо исключённых данных.

81. Сформировать Final Handoff Matrix.

---

# 12. Allowed Changes

- `.git/`
- `.gitignore`
- `AGENTS.md`
- `.agents/rules/03-git-checkpoints.md`
- `governance/git_policy.md`
- `project_state/CURRENT_STATE.md`
- `project_state/ROADMAP.md`
- `project_state/TASK_REGISTER.md`
- `project_state/ISSUES.md`
- `project_state/DECISIONS.md`
- `project_state/CHANGELOG.md`
- `project_state/structure/`
- `project_state/history/state/`
- `project_state/decisions/`
- `project_state/tasks/TZ-0003-isolated-git-checkpoints/`

Все изменения должны соответствовать данному ТЗ.

---

# 13. Forbidden Changes

- Изменение `tg_save/`.
- Чтение сообщений из `tg_save/`.
- Перенос приватных данных в Git.
- Изменение Global Git Config.
- Изменение credential stores.
- Создание публичного GitHub repository.
- Создание приватного GitHub repository без разрешения.
- Push без разрешения.
- Force push.
- Rebase существующей истории.
- Reset --hard.
- Удаление `.git` других проектов.
- Удаление старых task records.
- Изменение исторических snapshots.
- Удаление глобальных Skills.
- Отключение глобальных Plugins.
- Добавление MCP.
- Установка Python.
- Загрузка научных источников.
- Обработка мультимодальных данных.

---

# 14. Edge Cases

## EC-01 — Repository Already Exists

Если обнаружен `.git`:

Не выполнять повторный git init автоматически.

Проверить ownership и фактический Git root.

Если обнаружено непредусмотренное состояние:

BLOCKED.

## EC-02 — Parent Git Detected

Если Git root находится выше Project Root:

STOP.

Никаких вложенных Git mutations
до отдельного архитектурного решения.

## EC-03 — R0 SHA Mismatch

Если ZIP SHA отличается от manifest:

FAIL.

Проверить, существует ли документированное
основание изменения архива.

Не переписывать manifest.

## EC-04 — R0 Archive Corrupted

Не выполнять Git init.

Сохранить ISSUE и validation evidence.

## EC-05 — Missing Git Identity

Не выдумывать user.name или user.email.

Запросить разрешённую identity.

## EC-06 — Sensitive File in Staging

Остановить commit.

Исключить файл из индекса безопасным способом.

Не удалять исходный файл.

## EC-07 — GitIgnore False Negative

Исправить правило.

Повторить все native ignore tests.

## EC-08 — GitHub CLI Missing

Сохранить локальный Git.

Отметить GH_CLI_NOT_AVAILABLE.

Не устанавливать CLI автоматически.

## EC-09 — GitHub Permission Missing

Сохранить локальный checkpoint.

Установить PUSH_PENDING.

## EC-10 — Rule Activation Unverified

Не заявлять PASS.

Отразить ограничение в Validation.

Не использовать отсутствие ошибки
как доказательство загрузки Rule.

## EC-11 — Git Commit Failure

Не выполнять destructive reset.

Сохранить индекс и рабочие файлы.

Зафиксировать ISSUE.

## EC-12 — Dirty Worktree After Finalization

Выявить конкретные изменённые файлы.

Не выполнять blind `git add -A`.

Завершить разрешённый checkpoint
или документировать BLOCKED.

## EC-13 — Unexpected Files

Не удалять и не добавлять автоматически.

Классифицировать REVIEW_REQUIRED.

## EC-14 — Inconsistent PGSM State

Не переписывать параллельно обновлённый state.

Остановить выполнение.

## EC-15 — Archive Path Traversal

Если ZIP содержит небезопасные пути:

Не извлекать.

Зафиксировать SECURITY_FAILURE.

## EC-16 — Nested Repository

Если обнаружен вложенный `.git`:

Не добавлять nested repository как обычную папку.

Проверить происхождение.

## EC-17 — Git Hooks

Не исполнять неизвестные внешние Hooks.

При наличии сторонних Hooks:

Зафиксировать происхождение и полномочия.

## EC-18 — Commit Contains Unsupported Artifacts

Если в commit попали запрещённые файлы:

Не выполнять push.

Остановить задачу.

Не переписывать историю автоматически.

Запросить отдельный recovery decision.

---

# 15. Security Requirements

## SEC-01. No Secret Disclosure

Никакие реальные токены, ключи,
cookies и credentials не выводить в логи.

## SEC-02. Private By Default

Любой будущий GitHub remote
обязан иметь PRIVATE visibility.

## SEC-03. No External Data Transmission

Никакие пользовательские кейсы
не должны отправляться сторонним сервисам.

## SEC-04. Explicit Approval

Создание GitHub remote и push —
только после отдельного подтверждения.

## SEC-05. SHA Evidence

Каждый checkpoint должен содержать
фактический Git commit SHA.

## SEC-06. Immutable History

Запрет автоматической перезаписи истории.

## SEC-07. Least Privilege

Не расширять права агента ради Git.

## SEC-08. Scope Confinement

Работа только внутри Project Root.

## SEC-09. Sensitive Folder Isolation

`tg_save/` должен оставаться физически
и логически изолированным.

## SEC-10. No False Verification

Проверка `.gitignore` не доказывает,
что файл невозможно добавить через force-add.

Дополнительно проверять фактический индекс Git
и состав commit.

---

# 16. Definition of Done

Каждый пункт оценивается PASS / FAIL / NOT_RUN.

## Repository

DOD-01:
`git rev-parse --show-toplevel`
совпадает с canonical Project Root.

DOD-02:
`git branch --show-current`
возвращает утверждённую ветку.

DOD-03:
`git rev-parse HEAD`
возвращает действительный commit SHA.

DOD-04:
`git status --porcelain`
не содержит незавершённых разрешённых изменений
после финального checkpoint.

## Recovery

DOD-05:
R0_INTEGRITY_REPORT.md существует.

DOD-06:
Фактический SHA-256 R0_BACKUP.zip проверен.

DOD-07:
Различие между manifest и предыдущим
WALKTHROUGH документировано.

DOD-08:
Trial restore выполнен с полным SHA parity.

## Security

DOD-09:
`tg_save/` отсутствует в `git ls-files`.

DOD-10:
Sensitive directories отсутствуют в Git index.

DOD-11:
Секреты не обнаружены при проверке
staged и committed files применёнными тестами.

DOD-12:
Нативные `.gitignore` tests выполнены.

DOD-13:
Никакие глобальные Git settings
не изменялись исполнителем.

DOD-14:
Никакие remote операции не выполнялись
без подтверждённого разрешения.

## Governance

DOD-15:
`governance/git_policy.md` существует.

DOD-16:
`.agents/rules/03-git-checkpoints.md` существует
и проходит статическую проверку формата.

DOD-17:
Фактическая Rule Activation имеет честный статус:
VERIFIED / NOT_VERIFIED / FAILED.

DOD-18:
ADR Git isolation зарегистрирован
и имеет самостоятельный документ.

DOD-19:
Structure Version соответствует
фактическому контракту каталогов.

DOD-20:
Immutable structure snapshot существует
при изменении версии.

DOD-21:
CURRENT_STATE.md содержит новую ревизию.

DOD-22:
Все переходы состояния представлены
уникальными историческими snapshots.

DOD-23:
TASK_REGISTER.md отражает фактическое завершение.

DOD-24:
WALKTHROUGH.md содержит список изменений,
команд, результатов и известных ограничений.

## Checkpoint

DOD-25:
LOCAL_CHECKPOINT_RECEIPT.json существует.

DOD-26:
В receipt записан фактический HEAD SHA.

DOD-27:
Committed files соответствуют
FILE_CLASSIFICATION.md.

DOD-28:
Ни один файл категории GIT_EXCLUDED
не находится в Git history.

DOD-29:
Финальный Git checkpoint содержит
итоговые PGSM records текущего задания.

## Remote

DOD-30:
GITHUB_READINESS.md существует.

DOD-31:
Без отдельного разрешения
remote creation = NOT_EXECUTED.

DOD-32:
Без отдельного разрешения
push = NOT_EXECUTED.

DOD-33:
При отсутствии remote зафиксирован
PUSH_PENDING, а не REMOTE_VERIFIED.

---

# 17. Self Validation

Перед закрытием задания проверить:

1. Canonical Project Root.
2. Git top-level.
3. Current branch.
4. Git HEAD.
5. Git status.
6. Git remote list.
7. Git tracked files.
8. Git staged contents.
9. Sensitive-data exclusions.
10. Secret scan results.
11. R0 manifest consistency.
12. R0 restore-test.
13. Gitignore native tests.
14. Structure Version.
15. STRUCTURE_CHANGELOG.
16. Immutable structure snapshot.
17. TASK_REGISTER.
18. CURRENT_STATE.
19. Historical state snapshots.
20. ADR registry.
21. ADR standalone document.
22. Workspace Rule syntax.
23. Workspace Rule activation status.
24. No global config modifications.
25. No unauthorized network writes.
26. Final commit SHA.
27. Final walkthrough.

Любое невыполненное обязательное условие
фиксируется как FAIL или NOT_RUN.

Не превращать NOT_RUN в PASS.

---

# 18. Required Deliverables

В task directory:

`project_state/tasks/TZ-0003-isolated-git-checkpoints/`

Создать:

- `TZ.md`
- `DISCOVERY.md`
- `R0_INTEGRITY_REPORT.md`
- `FILE_CLASSIFICATION.md`
- `GITHUB_READINESS.md`
- `LOCAL_CHECKPOINT_RECEIPT.json`
- `VALIDATION.md`
- `WALKTHROUGH.md`

При ошибках:

- `ISSUES.md`

При прерывании:

- `CHECKPOINT.md`

Дополнительно:

- `governance/git_policy.md`
- `.agents/rules/03-git-checkpoints.md`
- `project_state/decisions/ADR-0006-git-isolation.md`
  с проверкой актуального следующего ADR-ID.

---

# 19. Final Handoff Contract

После выполнения предоставить следующую матрицу:

| Parameter | Required Value |
|---|---|
| ROOT | Canonical Project Root |
| TASK_ID | TZ-0003-isolated-git-checkpoints |
| OUTCOME | COMPLETED / BLOCKED / FAILED |
| STRUCTURE_VERSION | Actual version |
| STATE_REVISION | Actual revision |
| R0_INTEGRITY | PASS / FAIL |
| R0_ACTUAL_SHA256 | Actual computed hash |
| GIT_BOUNDARY | Verified path |
| GIT_BRANCH | Actual branch |
| LOCAL_HEAD_SHA | Actual SHA |
| TRACKED_FILES | Actual count |
| SECRET_SCAN | PASS / FAIL |
| PII_EXCLUSION | PASS / FAIL |
| GITIGNORE_TESTS | Passed / Total |
| RULE_ACTIVATION | VERIFIED / NOT_VERIFIED / FAILED |
| GITHUB_REMOTE | NOT_CONFIGURED / CONFIGURED |
| REMOTE_AUTHORIZATION | GRANTED / NOT_GRANTED |
| PUSH_STATUS | PUSH_PENDING / REMOTE_VERIFIED |
| GLOBAL_MUTATIONS | NONE / DETECTED / NOT_VERIFIED |
| OPEN_ISSUES | Exact Issue IDs |
| NEXT_PHASE | PH-04 if eligible |

## Completion Policy

Если локальный Git repository создан,
финальный checkpoint проверен,
security gates пройдены,
PGSM синхронизирован,
а GitHub не был разрешён:

Task Outcome = COMPLETED
Local Status = LOCAL_CHECKPOINT_VERIFIED
Remote Status = PUSH_PENDING

Это допустимое завершение PH-03 в локальном объёме.

Если обязательные локальные проверки не пройдены:

Task Outcome = BLOCKED или FAILED.

Если найден конфликт с инвариантами:

STOP.
Создать ISSUE.
Запросить решение владельца.

Не исправлять конфликт на основании догадки.

---

# 20. Next Phase

После успешного завершения:

`PH-04 — Scientific Knowledge Base Intake & Normalization`

Следующее задание должно включать:

- импорт оригинальных Grok Knowledge Base файлов;
- SHA-256 регистрацию;
- сверку каталога научных источников;
- устранение расхождения заявленных 62 источников
  с фактическим количеством записей;
- проверку доступности научных ссылок;
- проверку лицензий;
- нормализацию каталога;
- структурирование источников;
- подготовку Knowledge Base для будущего pipeline.

В рамках TZ-0003 эти действия не выполнять.

# End of PROF-TZ-0003