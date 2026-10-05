# Домашнє завдання №3 — PostgreSQL та DQL/EDA

## Датасет

Для домашнього завдання використано датасет **NYC TLC Yellow Taxi Trip Records за січень 2026 року**.

Офіційне джерело даних:

https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

Для роботи використовується Parquet-файл `yellow_tripdata_2026-01.parquet`.

## Формування вибірки

Початковий файл завантажується з офіційного джерела безпосередньо в Google Colab.

Для домашнього завдання з повного датасету сформовано вибірку з **50 000 рядків**:

```python
df = df.sample(n=50_000, random_state=42).copy()
```

Використання `random_state=42` дозволяє отримувати однакову вибірку при повторному запуску notebook.

Після підготовки вибірка зберігається у файл:

`data/hw3_taxi_sample.csv`

## Завантаження в PostgreSQL

CSV спочатку завантажується в staging-таблицю `hw3_taxi_staging` через `COPY FROM STDIN`.

Після цього очищені та типізовані дані переносяться в таблицю `hw3_taxi_trips` за допомогою `INSERT INTO ... SELECT`.

Фінальна вибірка містить **50 000 рядків**.

## Запуск

Основна робота виконана в Google Colab notebook.
