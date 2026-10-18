# goit-rdb-hw-04 — Olist: typed-схема, DML (RETURNING / ON CONFLICT), JOIN, агрегати, set operations

## Датасет
Brazilian E-Commerce Public Dataset by Olist — https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
Використовуються 6 файлів: customers, orders, order_items, products, sellers, order_reviews.

## Як отримати дані
- **Варіант A (за замовчуванням):** `kagglehub.dataset_download('olistbr/brazilian-ecommerce')` — у Colab мають бути налаштовані Kaggle credentials.
- **Варіант B:** покласти CSV у `data/olist/` (курсовий архів) — notebook автоматично використає їх замість Kaggle.

## Запуск
1. Відкрити `hw4_olist_notebook.ipynb` у Google Colab.
2. *Runtime → Restart session and run all* (перша клітинка встановлює залежності, запускає `pgserver`, показує версію PostgreSQL).
3. Notebook повністю відтворюваний: DDL починається з `DROP ... CASCADE`, upsert/UPDATE ідемпотентні.

## Структура
1. Setup, raw-таблиці, typed-схема, `INSERT ... SELECT`, smoke-test кількості рядків
2. DML: `INSERT ... RETURNING`, `ON CONFLICT DO UPDATE`, `UPDATE ... FROM`, `DELETE ... RETURNING`
3. `olist_customer_dim` + `customer_segments` (RFM на рівні `customer_unique_id`)
4. JOIN-запити: INNER (4 таблиці), LEFT + COALESCE, FULL OUTER, SELF, anti-join (`LEFT JOIN ... IS NULL` і `NOT EXISTS`)
5. GROUP BY / HAVING / `STRING_AGG`
6. `UNION`, `INTERSECT`, `EXCEPT`, `ROW_NUMBER()`, data-quality перевірка; Reflection
