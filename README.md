# airflow-dbt-example

This is a straightforward example demonstrating the integration of DBT (Data Build Tool) into Apache Airflow. The inspiration for this example comes from the instructions outlined in [this blog post](https://www.datafold.com/blog/running-dbt-with-airflow).

## Getting Started

### Run Docker Compose

Go to docker-compose directory and create a new directory called shared. And the run following command to change the permission

```bash
sudo chmod -R 777 shared
```

```bash
docker compose up -d
```

You may need to run following command again if the image stuck in starting stage caused by lack of permission. 
```bash
sudo chmod -R 777 shared
```


Wait for the Airflow services to start up. Then, open your web browser and go to `localhost:8080`. 

Log in, and you should see the test_dbt DAG. Note that it may take a moment to load the test_dbt DAG from the manifest.json file. 
If it doesn't show up immediately, try refreshing the page.
Once you see it, you can trigger the DAG to start the process.

After all tasks are finished, log in to PgAdmin, and you should observe the `dev.my_first_dbt_model` created in the `dbt` database. Your setup is now complete.

## Extend the example with your dbt model

To extend this example with your DBT model, navigate to the `dbt/test_project` directory and add your own DBT models.

Then trigger the dbt build by

```bash
docker exec -it airflow-dbt-example-airflow-dbt-1 /bin/bash   # log into the docker container
cd /root/dbt/test_project
dbt run
dbt docs generate
```

Then wait for about 1 minute, the dag should be updated in airflow.

## Stop and clean up

```bash
docker compose down --volumes
```
