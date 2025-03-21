# dbt_migration
POC to move data from snowflake to databricks for small and medium sized migrations and incremental migrations.


---

Getting Started

1. Set Up Python Virtual Environment

# Create and activate a virtual environment
python -m venv venv

source venv/bin/activate   # On Windows: venv\\Scripts\\activate

2. Install requirements 

#pip install in root folder

pip install -r requirements.txt

3. Configure dbt profiles

#edit ~/.dbt/profiles.yml with credentials

mkdir -p ~/.dbt

cp profiles_sample.yml ~/.dbt/profiles.yml

4. Test Connections

dbt debug --target snowflake
dbt debug --target databricks


5. Run dbt models

A. Create a view in Snowflake

example of using models name in the folders

dbt run --select snowflake_table --full-refresh --target snowflake

incremental after

dbt run --select orders_final --target databricks


6. Run dbt tests

dbt test --target databricks
