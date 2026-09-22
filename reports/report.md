# Отчёт по практическим работам №2 и №3

Студент: Ивановский Сергей Станиславович  
Группа: ЭФБО-14-24  
Репозиторий: https://github.com/Serg-I-1904/devops-course-2026

## Практическая работа №2

### Задание 1. Работа с ветками в терминале

Создана ветка `feature/hobby-project`.

Создан файл `hobby.md`:

- идея: онлайн-визитка с краткой информацией, контактами и ссылками на проекты;
- стек: HTML, CSS, JavaScript;
- цель: научиться создавать простую статическую страницу и публиковать её в интернете.

Коммит:

```text
feat: add hobby project description
```

Отчётные материалы:

- вывод `git branch`: ветка `feature/hobby-project` была создана и отправлена в `origin`;
- вывод `git log --oneline --all --graph`: коммит `feat: add hobby project description` находится в отдельной feature-ветке.

### Задание 2. Pull Request и Code Review

Ветка отправлена в GitHub:

```text
git push origin feature/hobby-project
```

Ссылка для создания Pull Request:

```text
https://github.com/Serg-I-1904/devops-course-2026/pull/new/feature/hobby-project
```

Текст Pull Request:

```md
## Что сделано
- Добавлено описание пет-проекта в hobby.md

## Зачем
- Фиксация идеи для дальнейшей разработки

## Чек-лист
- [x] Файл создан
- [x] Сообщение коммита по Conventional Commits
```

Комментарий ревьюера:

```text
Можно добавить раздел со сроками реализации или первым минимальным результатом, чтобы идея стала ближе к плану разработки.
```

### Задание 3. Git в VS Code

Создан файл `ide_notes.md`.

Коммит:

```text
docs: add IDE vs CLI notes
```

В файле описаны 3 удобные возможности VS Code для Git и 1 действие, которое удобнее выполнять в терминале.

### Задание 4. Знакомство с SVN

Создан файл `svn_comparison.md`.

Коммит:

```text
docs: add SVN comparison answers
```

В файле даны ответы на вопросы:

1. Почему в Git ветвление "дешёвое", а в SVN - "дорогое"?
2. Можно ли в SVN сделать коммит без интернета?
3. В каких сценариях SVN до сих пор может быть предпочтительнее Git?

## Практическая работа №3

### Задание 1. Разрешение merge-конфликтов

Созданы учебные ветки:

- `conflict/readme-update-1`;
- `conflict/readme-update-2`.

Получен конфликт в `README.md`, затем оба варианта объединены в осмысленный файл.

Отчётные материалы:

- `reports/readme_conflict_before.md` - файл с маркерами конфликта;
- `reports/readme_conflict_resolved.md` - итоговый вариант после разрешения конфликта.

### Задание 2. Rebase vs Merge

Создана ветка `demo/merge-example` и два коммита:

```text
feat: add feature A description
docs: add details for feature A
```

Для демонстрации merge использован `--no-ff`, чтобы получить видимый merge-коммит в истории.

Отчётные материалы:

- `reports/git_log_after_merge.txt` - граф истории после merge;
- `reports/git_log_after_rebase.txt` - граф истории после rebase и fast-forward merge.

Разница:

- после merge история содержит merge-коммит и показывает две линии разработки;
- после rebase история стала линейной, а merge в `main` прошёл как fast-forward.

### Задание 3. Interactive Rebase

Создана ветка `feature/calculator`.

Сначала создана "грязная" история из 6 коммитов:

```text
start calculator
wip
add subtract
fix typo in subtract
add docs
oops
```

Затем выполнен `git rebase -i HEAD~6`:

- `start calculator` переименован в `feat: implement add function`;
- `wip` приклеен через `fixup`;
- `add subtract` переименован в `feat: implement subtract function`;
- `fix typo in subtract` приклеен через `fixup`;
- `add docs` переименован в `docs: add calculator README`;
- `oops` удалён через `drop`.

Отчётные материалы:

- `reports/calculator_dirty_history.txt` - история до rebase;
- `reports/calculator_clean_history.txt` - история после rebase;
- `reports/calculator_final.txt` - итоговый `calculator.py`.

### Задание 4. Multi-Remote

Для полного выполнения нужно создать пустой mirror-репозиторий на GitHub или GitLab. Это действие создаёт внешний репозиторий, поэтому требуется отдельное подтверждение.

План выполнения после подтверждения:

```text
git remote add mirror <ssh-url>
git push mirror --all
git push mirror --tags
git remote set-url --add --push origin <ssh-url>
git remote -v
```

### Задание 5. Cherry-pick, Reflog и Revert

#### Cherry-pick

Создана ветка `hotfix/urgent-fix`.

Коммиты:

```text
fix: critical bug in calculator
feat: add multiply and divide (experimental)
```

В `main` применён только коммит:

```text
fix: critical bug in calculator
```

Отчётные материалы:

- `reports/cherry_pick_source_history.txt` - история ветки hotfix;
- `reports/cherry_pick_main_log.txt` - история `main` после cherry-pick;
- `reports/cherry_pick_calculator.txt` - `calculator.py` после cherry-pick без экспериментальных функций.

#### Reflog

Создана и удалена ветка `temp/lost-branch` с коммитом:

```text
feat: add very important data
```

Коммит найден через `git reflog` и восстановлен во временной ветке.

Отчётные материалы:

- `reports/reflog_lost_commit.txt` - reflog с потерянным коммитом;
- `reports/important_data_recovered.txt` - восстановленный файл.

#### Revert

Создан "вредный" коммит:

```text
feat: add new feature (accidentally broken)
```

Затем выполнен безопасный откат:

```text
git revert HEAD
```

Отчётные материалы:

- `reports/revert_log.txt` - история с revert-коммитом;
- `reports/revert_calculator.txt` - `calculator.py` без `BROKEN_CODE`.

## Что осталось выполнить через браузер

1. Войти в GitHub в открытой вкладке.
2. Создать Pull Request из `feature/hobby-project` в `main`.
3. Добавить комментарий ревьюера.
4. Выполнить `Squash and merge` и удалить ветку `feature/hobby-project`.
5. Подтвердить создание mirror-репозитория для задания Multi-Remote.
6. Для контрольной работы №4 отдельно подтвердить fork шаблона и создание mirror-репозитория.
