Step 1: Download Dockerfile and docker-compose file

```sh
$ git clone https://github.com/jaihuayen/docker-airflow.git
```
Step 2: Build the adjusted Docker Image of Airflow

```sh
$ cd docker-airflow
 
$ docker build -t airflow-image-adjusted .
```

Step 3: Construct the files for Airflow and set the enviornment variables.

```sh
$ mkdir ./logs ./plugins ./dags

$ chmod -R 777 logs/ dags/ plugins/

$ echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env
```

Step 4: 使用docker compose設定並建置airflow webserver

```sh
$ docker-compose up airflow-init
 
$ docker-compose up -d --build
```

需要下架Airflow時，執行

```sh
$ docker-compose down --volumes --rmi all
```

**使用docker compose V2時，執行

```sh
$ docker compose up airflow-init
 
$ docker compose up -d --build
```
(將docker-compose 改成docker compose)

需要下架Airflow時，執行

```sh
$ docker compose down --volumes --rmi all
```
