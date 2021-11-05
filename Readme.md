Step 1: 下載需求檔案

```sh
$ git clone https://github.com/jaihuayen/docker-airflow.git
```
Step 2: 將Dockerfile建置成Image

```sh
$ cd docker-airflow
 
$ docker build -t airflow-image-adjusted .
```

Step 3: 建立所需要的資料夾以及設定所需的環境變數

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
