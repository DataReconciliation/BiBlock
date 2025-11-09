# Entity Resolution Benchmark Dataset

## Overview
This dataset is a comprehensive collection of entity resolution (ER) benchmarks, based on the standard ER_Magellan datasets. The dataset contains real-world entity matching tasks across different data quality categories and domains, designed for evaluating and developing entity resolution systems and algorithms.

## Dataset Structure
```
data/
├── Dirty/
│   ├── amazon-google/
│   ├── dblp-acm/
│   ├── dblp-googlescholar/
│   └── walmart-amazon/
├── Structured/
│   ├── amazon-google/
│   ├── dblp_acm/
│   ├── dblp-googlescholar/
│   └── walmart-amazon/
└── Textual/
    └── abt_buy/
```

## Dataset Categories

### Dirty Datasets
Contains datasets with dirty, noisy, or inconsistent data representing real-world data quality challenges.

**Datasets included:**
- **Amazon-Google**: Product matching between Amazon and Google Shopping
- **DBLP-ACM**: Academic publication matching between DBLP and ACM digital libraries
- **DBLP-GoogleScholar**: Academic publication matching between DBLP and Google Scholar
- **Walmart-Amazon**: Product matching between Walmart and Amazon

### Structured Datasets
Contains clean, well-structured datasets with consistent schemas and high data quality.

**Datasets included:**
- **Amazon-Google**: Clean version of product matching
- **DBLP-ACM**: Clean version of academic publication matching
- **DBLP-GoogleScholar**: Clean version with structured academic data
- **Walmart-Amazon**: Clean version of retail product matching

### Textual Datasets
Contains datasets primarily focused on text-based entity matching with unstructured or semi-structured content.

**Datasets included:**
- **Abt-Buy**: Product matching between Abt and Buy.com with textual descriptions

## Data Organization

Each dataset directory contains the following standard files:

```
[dataset_name]/
├── table_a.parquet          # First entity table (Table A)
├── table_b.parquet          # Second entity table (Table B)
├── gold.parquet             # Ground truth matches (positive examples)
```

### File Format
- **Format**: Apache Parquet files
- **Compression**: Efficient binary format for fast loading and processing
- **Compatibility**: Compatible with pandas, PySpark, and other data processing frameworks

### Data Schema
Each dataset typically contains:
- **table_a**: Source entities from the first data source
- **table_b**: Source entities from the second data source
- **gold**: Known matching pairs between table_a and table_b entities

## Usage Examples

### Loading Data with Python
```python
import pandas as pd

# Load a specific dataset
dataset_path = "dirty/amazon-google/"
table_a = pd.read_parquet(f"{dataset_path}/table_a.parquet")
table_b = pd.read_parquet(f"{dataset_path}/table_b.parquet")
gold_matches = pd.read_parquet(f"{dataset_path}/gold.parquet")

print(f"Table A shape: {table_a.shape}")
print(f"Table B shape: {table_b.shape}")
print(f"Gold matches: {len(gold_matches)}")
```

### Loading Data with PySpark
```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("EntityResolution").getOrCreate()

# Load datasets
table_a = spark.read.parquet("dirty/amazon-google/table_a.parquet")
table_b = spark.read.parquet("dirty/amazon-google/table_b.parquet")
gold = spark.read.parquet("dirty/amazon-google/gold.parquet")
```

## Dataset Statistics

### Dataset Sizes
- **Dirty**: 4 datasets containing noisy, real-world data
- **Structured**: 4 datasets with clean, consistent data
- **Textual**: 1 dataset focused on text-based matching

### Applications
These datasets are suitable for:
- Entity resolution algorithm development
- Machine learning model training and evaluation
- Blocking and indexing technique evaluation
- Similarity measure assessment
- Performance benchmarking

## Citation
When using this dataset, please cite the original ER_Magellan benchmark papers and acknowledge this enhanced version if applicable.
# BiBlock
