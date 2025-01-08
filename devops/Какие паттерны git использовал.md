### Шанс вопроса: 6%

1. **Резервное копирование**: Использую `git stash` для временного сохранения изменений, чтобы переключиться на другую ветвь или выполнить обновление без фиксации текущих изменений.
   ```sh
   git stash
   git checkout branch-name
   git pull origin main
   git checkout - f HEAD
   git stash pop
   ```

2. **Именование веток**: Придерживаюсь именования веток, которое отражает их назначение (например, `feature/new-feature`, `bugfix/issue-123`). Это облегчает понимание истории коммитов и упрощает управление.

3. **Git Flow**: Придерживаюсь шаблона Git Flow для управления разработками. Создаю ветки для фич (`feature`), исправлений багов (`bugfix`), релизов (`release`) и hotfixes (`hotfix`). После завершения работы над функциональностью или исправлением создаю пулл-реквест в основную ветку, а затем мерджим его.
   ```sh
   git flow feature start new-feature
   git flow feature finish new-feature
   git flow release start 1.0
   git flow release finish 1.0
   ```

4. **Squash и Merge**: Использую `squash merge` для упрощения истории коммитов, чтобы каждый пулл-реквест представлял собой логически завершенную функциональность, а не серию промежуточных изменений.
   ```sh
   git checkout main
   git merge --squash feature-branch
   ```

5. **Использование Git Hooks**: Настроил Git Hooks для автоматизации задач, таких как статический анализ кода или тестирование перед мержем изменений в основную ветку.
   ```sh
   # Пример pre-commit hook для статического анализа
   cat << 'EOF' > .git/hooks/pre-commit
   #!/bin/bash
   eslint .
   if [ $? -ne 0 ]; then
     exit 1
   fi
   EOF
   chmod +x .git/hooks/pre-commit
   ```

6. **Использование Git LFS**: Для управления большими файлами (например, медиафайлами) использую Git Large File Storage (LFS). Это позволяет отслеживать и хранить файлы вне основного репозитория.
   ```sh
   git lfs install
   git lfs track "*.mp4"
   git add .gitattributes
   git add video-file.mp4
   git commit -m 'Add large video file'
   git push origin main
   ```

7. **Использование Git Bisect**: Для поиска коммита, который ввел ошибку или изменение, использую `git bisect` для автоматического бинарного поиска проблемы между известным хорошим и плохим состоянием.
   ```sh
   git bisect start
   git bisect bad # текущий коммит с ошибкой
   git bisect good <good-commit>
   ```

Эти практики помогают в управлении версиями, обеспечивая гибкость и эффективность при работе над проектами.