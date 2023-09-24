# airflow-dbt-example

This is a straightforward example demonstrating the integration of DBT (Data Build Tool) into Apache Airflow. The inspiration for this example comes from the instructions outlined in [this blog post](https://www.datafold.com/blog/running-dbt-with-airflow).

## Getting Started

### Build Docker Image
  
```bash
cd docker
docker build . -t airflow-dbt
```

### Run Docker Compose

```bash
docker compose up
```

Wait for the Airflow standalone service to start up. Then, open your web browser and go to `localhost:8080`. 
Log in, and you should see the test_dbt DAG. Note that it may take a moment to load the test_dbt DAG from the manifest.json file. 
If it doesn't show up immediately, try refreshing the page.
Once you see it, you can trigger the DAG to start the process.

After all tasks are finished, log in to PgAdmin, and you should observe the `dev.my_first_dbt_model` created in the `dbt` database. Your setup is now complete.

## Extend the example with your dbt model

To extend this example with your DBT model, navigate to the `dbt/test_project` directory and add your own DBT models.

## Stop and clean up

```bash
docker compose down
rm -rf airflow/*
rm -rf dbt/*
rm -rf postgres/*
```
