# Spark_Running_in_Docker_with_bitnami_image

## Open Docker Hub and pull the Spark bitnami docker images

Search for "Spark" image and select the "bitnami/spark" images 

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/6cc0220b-f973-440c-b9b7-eff896de786e)

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/3508d752-5254-41aa-bc7e-9bc69d635845)

## Pull the Spark image to our local laptop

Run the command:

```
docker pull bitnami/spark
```

## Download and run the docker-compose file

Create a folder and open the command prompt as Administrator. 

Run this command to download the docker-compose.yml file to our local folder:

```
curl -LO https://raw.githubusercontent.com/bitnami/containers/main/bitnami/spark/docker-compose.yml
```

![image](https://github.com/luiscoco/Spark_Running_in_Docker_with_bitnami_images/assets/32194879/c0275773-bb79-44bc-9740-c1a4da0a3ccd)

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


