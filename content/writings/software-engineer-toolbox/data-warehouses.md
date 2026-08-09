---
title: "Data Warehouses & Analytics"
---

Operational aggregation is not analytics. A warehouse lets analytical workloads
run without harming transactional application traffic.

- Distinguish OLTP, OLAP, lake, lakehouse, batch, streaming, and serving layers.
- Model facts, dimensions, grain, star/snowflake schemas, slowly changing dimensions, partitions, clustering, and materialized views.
- Build ETL/ELT pipelines with reliable ingestion, idempotency, late-arriving data handling, backfills, schema evolution, lineage, ownership, and data-quality checks.
- Know columnar formats (Parquet/ORC), compression, predicate pushdown, distributed query engines, and the cost of scans/shuffles.
- Learn one cloud warehouse/lakehouse deeply (for example BigQuery, Snowflake, Redshift, Databricks) plus SQL and a transformation tool such as dbt.
- Treat analytics data as production data: access control, PII masking, retention, observability, and documented metric definitions matter.
