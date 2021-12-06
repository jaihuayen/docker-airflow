Step 1: Download Dockerfile and docker-compose file

```sh
$ git clone https://github.com/jaihuayen/docker-airflow.git
```
Step 2: Switch to the project folder

```sh
$ cd docker-airflow
```

Step 3: Construct the files for Airflow and set the enviornment variables.

```sh
$ mkdir ./logs ./plugins ./dags

$ chmod -R 777 logs/ dags/ plugins/

$ echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env
```

Step 4: Use docker compose to build airflow webserver

```sh
$ docker-compose up airflow-init
 
$ docker-compose up -d --build
```

To stop and delete containers, delete volumes with database data and download images, run

```sh
$ docker-compose down --volumes --rmi all
```

** Use docker compose V2 to build airflow webserver

```sh
$ docker compose up airflow-init
 
$ docker compose up -d --build
```

**To stop and delete containers, delete volumes with database data and download images in Docker Compose V2, run

```sh
$ docker compose down --volumes --rmi all
```
