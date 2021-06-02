---
title: Airflow Remove Example Dags
date: 2021-06-02
categories: 
 - Dev
 - Python
tags: 
 - dev
 - python
 - airflow
---

When you start your local airflow based on the [official documentation](https://airflow.apache.org/docs/apache-airflow/1.10.14/start.html), the airflow will fill the db with a bunch of examples. If you want to remove them, first you need to find the `airflow.cfg` find under the airflow home directory (usually it is `$HOME/airflow`) and change the line `load_examples = True` to `load_examples = False`. After the change, however, the examples are still in you airflow's DB. You need to run `airflow resetdb` to reset the airflow DB. Finally the examples are gone. 

