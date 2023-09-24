# airflow-dbt-example

A simple example of integrate DBT into airflow inspired by instraction from https://www.datafold.com/blog/running-dbt-with-airflow. 

## Start the example

* Build docker image
  
```bash
cd docker
docker build . -t airflow-dbt
```

* Run docker compose

```bash
docker compose up
```

wait for airflow standalone service start up, then go to localhost:8080, login, and check the dag test_dbt.
It may take a while to load the test_dbt from the manifest.json file. Refresh a few times and it should show up. 
Now you can trigger the dag. 

After all tasks finished, login to the pgadmin and you should see 'dev.my_first_dbt_model' created in dbt database. 

Now everything is setup for you. 

## Extend the example with your dbt model

open dbt/test_project and add your own dbt models

## Stop and clean up

```bash
docker compose down
rm -rf airflow/*
rm -rf dbt/*
rm -rf postgres/*
```
