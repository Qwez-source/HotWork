### Шанс вопроса: 3%

DCI (Data-Context-Interaction) — это архитектурное паттерн, которое представляет собой способ структурирования программного обеспечения, где данные (data), контекст (context) и взаимодействие (interaction) являются ключевыми компонентами. DCI фокусируется на том, как данные используются в приложении и каким образом они взаимодействуют с пользователем или другими системами.

В рамках DCI:
- **Данные (Data)** представляют собой структуру, которая хранит информацию о состоянии приложения.
- **Контекст (Context)** определяет среду выполнения и правила, по которым данные могут изменяться или использоваться.
- **Взаимодействие (Interaction)** включает в себя логику обработки данных и взаимодействия с пользователем или другими компонентами системы.

Пример:
Предположим, у нас есть приложение для управления задачами. В рамках DCI это можно представить следующим образом:
- **Данные (Data)** — структура `Task` с полями `id`, `title`, `completed`.
- **Контекст (Context)** — включает в себя список задач и логику для добавления, редактирования и удаления задач.
- **Взаимодействие (Interaction)** — включает в себя функции для отображения списка задач, добавления новой задачи и изменения статуса задачи.

```javascript
class Task {
  constructor(id, title, completed = false) {
    this.id = id;
    this.title = title;
    this.completed = completed;
  }
}

class TaskContext {
  constructor() {
    this.tasks = [];
  }

  addTask(title) {
    const newTask = new Task(this.tasks.length + 1, title);
    this.tasks.push(newTask);
  }

  toggleComplete(taskId) {
    const task = this.tasks.find(t => t.id === taskId);
    if (task) {
      task.completed = !task.completed;
    }
  }

  getTasks() {
    return this.tasks;
  }
}

class TaskInteraction {
  constructor(context) {
    this.context = context;
  }

  displayTasks() {
    const tasks = this.context.getTasks();
    console.log('Tasks:', tasks);
  }

  addTask(title) {
    this.context.addTask(title);
    console.log(`Added task: ${title}`);
  }

  toggleComplete(taskId) {
    this.context.toggleComplete(taskId);
    console.log(`Toggled status for task id: ${taskId}`);
  }
}

// Пример использования
const taskContext = new TaskContext();
const taskInteraction = new TaskInteraction(taskContext);

taskInteraction.addTask('Buy groceries');
taskInteraction.displayTasks(); // Вывод списка задач
taskInteraction.toggleComplete(1);
taskInteraction.displayTasks(); // Вывод обновленного списка задач
```

Таким образом, DCI позволяет разделить данные и логику обработки данных, что делает код более модульным и легко расширяемым.