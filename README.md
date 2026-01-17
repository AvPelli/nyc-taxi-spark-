# NYC Taxi Spark - Performance Analysis

[![PySpark](https://img.shields.io/badge/PySpark-3.5.0-orange)](https://spark.apache.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-blue)](https://jupyter.org/)

Hands-on exploration of **Apache Spark performance optimization** using NYC Yellow Taxi January 2024 data (CSV → Parquet conversion, caching, partitioning, aggregations, shuffle analysis). 

## 🎯 Project Objectives

- Convert NYC Taxi CSV → Parquet with statistics analysis 
- Benchmark **Spark caching** (`MEMORY_ONLY` vs uncached) 
- Analyze **partitioning effects** (6 vs 12 partitions, task distribution) 
- Study **shuffle behavior** during `groupBy().agg(sum())` operations 
- Understand lazy evaluation, storage levels, and task parallelism 
- Analyze **execution plan** (4 levels of abstraction)

## 🚀 Quick Start

Ensure Java 17 for compatibility with Spark

```bash
git clone https://github.com/AvPelli/nyc-taxi-spark.git
cd nyc-taxi-spark

# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate

# Install exact dependencies
pip install -r requirements.txt

# Start Jupyter
jupyter lab
```

## 🔮 Future Experiments

### Immediate (1-2 days)
- [ ] **Full-year NYC Taxi dataset** (1.7GB, ~20M rides)
- [ ] **Column pruning analysis**: `select(3 cols)` vs all 21 columns

### Medium-term (2 weeks)
- [ ] **Databricks Community Edition + Delta Lake**
  ```python
  df.write.format("delta").save("/delta/nyc-taxi")
  spark.read.format("delta").load("/delta/nyc-taxi")
  ```
- [ ] **Photon engine comparison vs local CPU**

### Long-term (1-3 months)

- [ ] **AQE Deep Dive** - analyze Adaptive Query Execution optimization
  **Objective**: Learn runtime optimization (partition coalescing, skew handling)

- [ ] **Production Spark Configs** - `spark.sql.shuffle.partitions=200`
  **Objective**: Understand production-scale partitioning vs local defaults

- [ ] **Scale to ADLS Gen2** - Petabyte storage with `abfss://` paths
  **Objective**: Scale to handle 1.7GB→100GB+ datasets

- [ ] **Production Pipeline Mockup** - End-to-end DAG automation
  **Objective**: Build orchestrated workflow (Airflow/Meltano) simulating real ETL

### Goal (6 months)

- [ ] **Databricks Production Compute** - Full cloud Spark on production mockup
  **Objective**: Run optimized NYC Taxi pipeline on **Databricks clusters** with:
  - **Photon engine** (2-10x faster than CPU)
  - **Delta Lake** (ACID transactions, time travel)
  - **Unity Catalog** (governance across teams)
  - **Auto-scaling clusters** (1 → 1000 nodes)
  - **Production monitoring + alerting**