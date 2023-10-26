# Spark_Running_in_Docker_with_bitnami_image

https://hub.docker.com/r/bitnami/spark

## What is Apache Spark?

Apache Spark is a high-performance engine for large-scale computing tasks, such as data processing, machine learning and real-time data streaming. 

It includes APIs for Java, Python, Scala and R.

## Open Docker Hub and pull the Spark bitnami docker images

Search for "Spark" image and select the "bitnami/spark" images 

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/6cc0220b-f973-440c-b9b7-eff896de786e)

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/3508d752-5254-41aa-bc7e-9bc69d635845)

## Pull the Spark image to our local laptop

Run the command:

```
docker pull bitnami/spark
```

or better

```
docker pull bitnami/spark:latest
```

## Download and run the docker-compose file

Create a folder and open the command prompt as Administrator. 

Run this command to download the docker-compose.yml file to our local folder:

```
curl -LO https://raw.githubusercontent.com/bitnami/containers/main/bitnami/spark/docker-compose.yml
```

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/c0275773-bb79-44bc-9740-c1a4da0a3ccd)

This is the docker-compose file you downloaded to your local machine:

```
# Copyright VMware, Inc.
# SPDX-License-Identifier: APACHE-2.0

version: '2'

services:
  spark:
    image: docker.io/bitnami/spark:3.5
    environment:
      - SPARK_MODE=master
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
      - SPARK_USER=spark
    ports:
      - '8080:8080'
  spark-worker:
    image: docker.io/bitnami/spark:3.5
    environment:
      - SPARK_MODE=worker
      - SPARK_MASTER_URL=spark://spark:7077
      - SPARK_WORKER_MEMORY=1G
      - SPARK_WORKER_CORES=1
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
      - SPARK_USER=spark
```

Run this command to execute the docker-compose file

```
docker-compose up
```

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/c82bd928-a17e-45b9-81e6-3c56e638eb12)

Once the spark docker container is running we can run the spark-shell, but first we need to download Spark to out local hard drive.

## Download the Spark to out local hard drive

Go to the URL: https://spark.apache.org/downloads.html

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/86af0951-3baf-4fdc-a7eb-8f9d9781de9e)

Unzip the "" file and place in C:

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/7efa8356-1f82-4dcb-b8ac-72d0eb02e933)

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/db9816f9-608c-4786-8db1-b6cc28e78fd2)

## Run the spark-shell

First we go to Docker Desktop and click on the Spark Master link 

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/6c950cdf-cec1-4700-b6e3-82c2ab4015f5)

After we will see the Spark Master Web Page

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/5d54153e-2bbd-4c65-a93e-31df3123ca30)

Then we open a command prompt as Administrator and navigate to the bin folder inside the "C:\spark-3.5.0-bin-hadoop3"

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/bcda282c-f140-41c9-a566-63a63227bdb1)

Then we can run the command "spark'shell", this command is inside the "C:\spark-3.5.0-bin-hadoop3\bin" folder, and this command is followed by the spark master node URL

```
spark-shell spark://e7cbedd69027:7077
```

You can see now the "scala" propmpt and you can start coding:

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/6ccb4808-8e49-4369-960f-2b901a35df18)

## Setting up an Apache Spark Cluster

A Apache Spark cluster can easily be setup with the default docker-compose.yml file from the root of this repo. 

The docker-compose includes two different services, spark-master and spark-worker.

By default, when you deploy the docker-compose file you will get an Apache Spark cluster with 1 master and 1 worker.

If you want N workers, all you need to do is start the docker-compose deployment with the following command:

```
docker-compose up --scale spark-worker=3
```
