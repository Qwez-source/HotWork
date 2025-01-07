### Шанс вопроса: 3%

Apache Airflow — это платформа для программирования, управления и мониторинга асинхронных задач. Она позволяет создавать графы задач (DAGs), определять зависимости между задачами, настраивать параметры выполнения и отслеживать выполнение задач. Airflow используется для управления потоками работ в больших корпоративных системах, а также в научных и аналитических проектах.

Основные компоненты Apache Airflow включают:
1. **DAG (Directed Acyclic Graph)**: Граф задач, который представляет собой набор всех задач и их зависимостей.
2. **Operators**: Операторы — это блоки, которые выполняют определенные действия. Например, оператор BashOperator используется для выполнения команд в bash.
3. **Triggers**: Триггеры позволяют запускать задачи по расписанию или в ответ на событие.
4. **Web Interface**: Веб-интерфейс, который предоставляет визуальное представление о выполнении DAG и задачах.
5. **Schedulers**: Планировщики задач, которые запускают выполнение DAG по расписанию или при срабатывании триггеров.

Пример создания простого DAG в Airflow:
```python
from airflow import DAG
from airflow.operators.bash_operator import BashOperator
from airflow.utils.dates import days_ago
from datetime import timedelta

default_args = {
    'owner': 'airflow',
    'start_date': days_ago(1),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

dag = DAG(
    dag_id='example_bash_operator',
    default_args=default_args,
    description='A simple tutorial DAG',
    schedule_interval=timedelta(days=1),
)

run_this_first = BashOperator(
    task_id='run_this_first',
    bash_command='echo "Hello World!"',
    dag=dag,
)

run_this_second = BashOperator(
    task_id='run_this_second',
    bash_command='echo "Hi!"',
    dag=dag,
)

run_this_first >> run_this_second
```

Этот пример создает DAG с двумя задачами: первая выводит "Hello World!", а вторая — "Hi!". Задачи связаны так, что вторая задача запускается после первой.