# Introduction to Dask

Lab materials for the **Big Data Technologies** course at the University of Trento. This lab introduces [Dask](https://www.dask.org/), a Python library for parallel and distributed computing, covering its three core abstractions through guided tutorials and hands-on exercises.

## Contents

### Tutorials

| Notebook | Topic |
|----------|-------|
| `Dask Array.ipynb` | Chunked NumPy-like arrays, lazy evaluation, large-scale numerical computing |
| `Dask Bags.ipynb` | Unstructured/semi-structured data processing, working with JSON |
| `Dask Dataframe.ipynb` | Distributed pandas DataFrames, local clusters, remote data (GCS), Parquet |


## Setup

**Requirements:** Python 3.x, pip

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

### Dependencies

```
dask[complete]   # Dask with all extras (distributed, dataframe, array, bag)
jupyterlab       # Notebook interface
pandas           # DataFrame support
mimesis          # Synthetic data generation
graphviz         # Task graph visualization
gcsfs            # Google Cloud Storage access
```

## Learning Objectives

By the end of this lab, students will be able to:

- Explain the difference between **eager** and **lazy** evaluation and how Dask uses task graphs
- Use **Dask Arrays** for chunked numerical computation beyond RAM limits
- Use **Dask Bags** to process collections of unstructured JSON records
- Use **Dask DataFrames** for distributed tabular data processing (filter, groupby, aggregation)
- Read data from multiple sources: local files, CSV, Parquet, and remote object storage (GCS)
- Set up and monitor a **local Dask cluster** using the dashboard
- Apply performance best practices: `.persist()`, column pruning, Parquet over CSV

## Key Concepts

**Lazy evaluation** — Dask builds a task graph describing the computation but does not execute it until `.compute()` is called. This allows Dask to optimize the execution plan and handle datasets larger than available RAM.

**Partitioning** — data is split into chunks (arrays) or partitions (DataFrames/Bags) that can be processed in parallel across cores or machines.

**The Dask dashboard** — when running a `LocalCluster`, a real-time dashboard is available (typically at `http://localhost:8787`) showing task progress, memory usage, and worker activity.

## Data

The `data/` directory contains 100 JSON files of synthetic person records generated via `dask.datasets.make_people()`. These are used in the Bags tutorial and Exercise 1.

Exercises 2–4 access NYC Taxi data from Google Cloud Storage (internet connection required).
