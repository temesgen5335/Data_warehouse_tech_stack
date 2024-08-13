# Data_warehouse_tech_stack
10 Academy Cohort B - Week 2 Challenge: Data Engineering: Data warehouse tech stack with MySQL/PostgreSQL, DBT, Airflow


## Project Overview
This project aims to analyze vehicle trajectories using SQL and Python. The analysis includes calculating the maximum speed, minimum speed, fastest time, and total distance traveled for each vehicle. The project also uses dbt for data transformation and lineage graph generation.

### Data Source
pNEUMA is an open large-scale dataset of naturalistic trajectories of half a million vehicles that have been collected by a swarm of drones and static roadside cameras in the congested downtown area of Athens, Greece.


The vehicle trajectory data is extracted from analyzing traffic footage.
Each file for a single (area, date, time) is ~87 MB data.

## Tech Stack

### PostgreSQL
PostgreSQL is a powerful, open-source object-relational database system. It uses and extends the SQL language combined with many features that safely store and scale complicated data workloads. In this project, PostgreSQL is used as the data warehouse to store vehicle trajectory data. This data is extracted from footage taken by swarm drones and static roadside cameras. The data is loaded into PostgreSQL from your data source (like a CSV file) using an Airflow task.

### Airflow
Apache Airflow is an open-source platform used to programmatically author, schedule, and monitor workflows. In this project, Airflow is used to schedule and automate tasks in the data pipeline. These tasks include loading data into PostgreSQL and running transformation codes with dbt. Each task in Airflow is defined as a Python function and organized into a Directed Acyclic Graph (DAG). The DAG defines the sequence in which tasks run and their dependencies.

### dbt (Data Build Tool)
dbt is a command-line tool that enables data analysts and engineers to transform data in their warehouses more effectively. In this project, dbt is used to transform the data loaded into PostgreSQL. It does this by executing SQL scripts that are defined in your dbt project. These scripts can perform operations like aggregation, joining, filtering, and cleaning on your data. The transformed data is then loaded back into PostgreSQL, where it can be queried for analysis. dbt also provides features for testing your data (to ensure it meets certain conditions) and documenting your data models.

### Redash
Redash helps you make sense of your data. It allows you to connect and query your data sources, build dashboards to visualize data, and share them with your company. In this project, Redash is used to create visualizations and dashboards from the transformed data. It connects to your PostgreSQL database, allows you to write SQL queries to fetch data, and provides tools to visualize this data in various formats (like tables, line charts, bar charts, etc.). These visualizations can be organized into dashboards and shared with others.

## Getting Started

### Prerequisites
- Python 3.x
- PostgreSQL
- dbt
- Airflow

### Installation
1. Clone the repository
```bash
git clone git@github.com:temesgen5335/Data_warehouse_tech_stack.git
```

#### 2. Install the required Python packages
```bash
pip install -r requirements.txt
```

#### 3. Set up PostgreSQL
- Install PostgreSQL
- Create a new database
- Update the database connection string in the `dags/vehicle_trajectory_dag.py` file

#### 4. Set up dbt
- Install dbt
- Create a new dbt project

#### 5. Set up Airflow
- Install Airflow
- Initialize the Airflow database
```bash
airflow db init
```
- Start the Airflow web server
```bash
airflow webserver --port 8080

```
- Start the Airflow scheduler
```bash
airflow scheduler
```
- Access the Airflow web interface
```
http://localhost:8080
```
- Create a new connection in Airflow for your PostgreSQL database

- Create a new connection in Airflow for your dbt project

- Create a new DAG in Airflow using the `dags/vehicle_trajectory_dag.py` file
- Trigger the DAG to run
- Monitor the DAG run in the Airflow web interface
- Check the transformed data in your PostgreSQL database
- Create visualizations in Redash using the transformed data


## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
