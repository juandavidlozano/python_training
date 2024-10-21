
# Apache Airflow Cheat Sheet

## 1. Core Concepts

- **DAG (Directed Acyclic Graph)**: A DAG defines a workflow with tasks. It must not contain loops.
- **Task**: A single unit of work (e.g., executing a script, transferring data).
- **Operator**: Defines a single task (e.g., `PythonOperator`, `BashOperator`, `S3ToRedshiftOperator`).
- **Sensor**: A special operator that waits for a condition to be met (e.g., waiting for a file in S3).
- **Task Instance**: Represents a task in a specific DAG run at a specific time.
- **Execution Date**: Represents the logical date and time for which the DAG run is working (not the time it is running).
- **Trigger Rule**: Determines when a task should run (e.g., `all_success`, `all_failed`, `one_success`).
- **XCom**: Cross-communication mechanism for sharing data between tasks.
- **Scheduler**: Triggers tasks based on schedules or external events.
- **Worker**: Executes the tasks.
- **Executor**: Manages how and where tasks are run (e.g., `LocalExecutor`, `CeleryExecutor`, `KubernetesExecutor`).

---

## 2. DAG Structure

- **DAG Parameters**:
  - `start_date`: Defines when the DAG starts.
  - `schedule_interval`: Defines how often the DAG runs (e.g., `@daily`, `@hourly`).
  - `catchup`: If `False`, Airflow won’t run missed intervals (backfilling).
  - `retries`: Defines how many times to retry a failed task.
  - `retry_delay`: Time between retries (e.g., `timedelta(minutes=5)`).

### Basic DAG Example:

```python
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from datetime import datetime

def print_hello():
    print("Hello, World!")

default_args = {
    'start_date': datetime(2023, 10, 20),
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

dag = DAG(
    'hello_world_dag',
    default_args=default_args,
    schedule_interval='@daily', 
    catchup=False
)

task_hello = PythonOperator(
    task_id='hello_task',
    python_callable=print_hello,
    dag=dag
)
```

---

## 3. Operators

### Common Operators:
- **PythonOperator**: Executes Python code.
    ```python
    PythonOperator(
        task_id='task_name',
        python_callable=my_python_function
    )
    ```
  
- **BashOperator**: Executes Bash commands.
    ```python
    BashOperator(
        task_id='bash_task',
        bash_command='echo "Hello Airflow!"'
    )
    ```

- **EmailOperator**: Sends an email.
    ```python
    EmailOperator(
        task_id='send_email',
        to='email@example.com',
        subject='Subject',
        html_content='<h1>Email Content</h1>'
    )
    ```

- **Sensors**:
  - **S3KeySensor**: Waits for a file in S3.
  - **HttpSensor**: Waits for an HTTP response.
  
  Example:
  ```python
  S3KeySensor(
      task_id='s3_sensor_task',
      bucket_key='my_key',
      bucket_name='my_bucket',
      timeout=600,
      poke_interval=60
  )
  ```

---

## 4. Task Dependencies

- **Setting Dependencies**:
    ```python
    task1 >> task2  # Task 2 runs after Task 1
    task3.set_downstream(task4)  # Task 4 runs after Task 3
    ```

- **Trigger Rules**:
  - `all_success`: Default, task runs when all upstream tasks succeed.
  - `all_failed`: Task runs only if all upstream tasks fail.
  - `one_success`: Task runs if any upstream task succeeds.

    ```python
    task3 = PythonOperator(
        task_id='task_3',
        python_callable=my_function,
        trigger_rule='all_failed'
    )
    ```

---

## 5. XComs (Cross-Communications)

- **Pushing Data**:
  ```python
  def push_data(**kwargs):
      kwargs['ti'].xcom_push(key='my_key', value='my_value')
  ```

- **Pulling Data**:
  ```python
  def pull_data(**kwargs):
      value = kwargs['ti'].xcom_pull(task_ids='push_task', key='my_key')
  ```

---

## 6. Scheduling and Timing

- **Schedule Intervals**:
  - `@daily`: Once a day.
  - `@hourly`: Once an hour.
  - `@weekly`: Once a week.
  - Custom intervals using cron (e.g., `0 12 * * *` for every day at noon).

- **Backfilling**:
  - `catchup=False` ensures that DAGs do not run retroactively for missed intervals.

- **Start Date vs. Execution Date**:
  - **Start Date**: The time the DAG is allowed to run from.
  - **Execution Date**: Logical date representing when the DAG run is meant to be applied.

---

## 7. Parallelism and Concurrency

- **max_active_runs**: Limits the number of active DAG runs.
- **concurrency**: Limits the number of tasks a DAG can run in parallel.
- **pool**: Manages the resource allocation of tasks to avoid overloading the system.

Example:

```python
dag = DAG('my_dag',
          default_args=default_args,
          schedule_interval='@daily',
          concurrency=5,  # Max 5 tasks at a time
          max_active_runs=3,  # Max 3 DAG runs at the same time
          catchup=False)
```

---

## 8. Executors

- **LocalExecutor**: Runs tasks on the local machine.
- **CeleryExecutor**: Distributed task execution using Celery.
- **KubernetesExecutor**: Runs tasks in Kubernetes pods for isolated execution.

---

## 9. DAG Monitoring and Management

- **Airflow UI**: Provides a graphical interface for monitoring DAGs, task statuses, logs, etc.
- **Task Instance States**:
  - `success`, `failed`, `upstream_failed`, `skipped`, `queued`, `running`, `shutdown`.

- **CLI Commands**:
  - List DAGs: `airflow dags list`
  - Trigger DAG manually: `airflow dags trigger <dag_id>`
  - Pause a DAG: `airflow dags pause <dag_id>`
  - View task instances: `airflow tasks list <dag_id>`

---

## 10. Best Practices

1. **Idempotency**: Ensure that tasks can run multiple times without causing unintended side effects.
2. **Small, Independent Tasks**: Break large workflows into smaller tasks to improve maintainability and scalability.
3. **Avoid Heavy Processing**: Offload heavy processing to external systems (e.g., use Spark or AWS Batch for data processing).
4. **Testing**: Use unit tests and integration tests for DAGs.
5. **Error Handling**:
   - Use retries for transient issues.
   - Implement custom error notifications (e.g., EmailOperator or SlackOperator).
6. **Observability**:
   - Use proper logging for tasks.
   - Monitor Airflow UI and check task logs for debugging.

---

## 11. Interview Questions Examples

### Basic Questions:
- What is a DAG in Airflow?
- How do you set task dependencies in Airflow?
- What is XCom and how is it used?
- What is the role of the Airflow scheduler?
  
### Advanced Questions:
- How do you handle task retries and failure recovery?
- Explain the difference between `start_date` and `execution_date` in Airflow.
- How would you scale an Airflow setup for a large number of DAGs and tasks?
- What are the benefits of using `CeleryExecutor` over `LocalExecutor`?

### Scenario-Based Questions:
- How would you set up an ETL pipeline in Airflow that processes files from an S3 bucket?
- Explain how to troubleshoot a DAG run where a task fails due to a transient issue.
- What strategy would you use to monitor and alert on task failures in a production Airflow environment?

---

## 12. Debugging and Troubleshooting

- **View Task Logs**: Go to the Airflow UI > DAG > Task > Logs to view detailed logs for debugging.
- **Check XComs**: View XCom values in the UI for troubleshooting data passing between tasks.
- **Common Issues**:
  - **Tasks stuck in `queued` state**: Check if there are enough workers, or if concurrency limits are reached.
  - **Task failures**: Review logs, check dependencies, and ensure external services are available (e.g., database connections, API calls).

