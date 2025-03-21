# DBT Migration

A proof of concept (POC) project for migrating data from Snowflake to Databricks. Designed for small to medium-sized migrations and incremental migrations.

## Getting Started

### 1. Set Up Python Virtual Environment

Create and activate a virtual environment:

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 2. Install Requirements

Install the required packages:

```bash
# Run in the root folder
pip install -r requirements.txt
```

### 3. Configure dbt Profiles

Set up your dbt profiles with credentials:

```bash
# Create dbt directory if it doesn't exist
mkdir -p ~/.dbt

# Copy the sample profiles file
cp profiles_sample.yml ~/.dbt/profiles.yml

# Edit the profiles file with your credentials
# nano ~/.dbt/profiles.yml
```

### 4. Test Connections

Verify your connections to both Snowflake and Databricks:

```bash
# Test Snowflake connection
dbt debug --target snowflake

# Test Databricks connection
dbt debug --target databricks
```

### 5. Run dbt Models

#### A. Create a View in Snowflake

Example of using model names in the folders:

```bash
# Run full refresh on Snowflake
dbt run --select snowflake_table --full-refresh --target snowflake
```

#### B. Run Incremental Models in Databricks

```bash
# Run incremental models in Databricks
dbt run --select orders_final --target databricks
```

### 6. Run dbt Tests

Validate your data models with dbt tests:

```bash
# Run tests on Databricks models
dbt test --target databricks
```


