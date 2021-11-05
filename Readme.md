Step 1: 下載需求檔案
$ git clone http://scm.tutorabc.com/kevinyen/docker-airflow.git


Step 2: 將Dockerfile建置成Image
$ cd docker-airflow
 
$ docker build -t airflow-dockerimage-adjusted .


Step 3: 建立所需要的資料夾以及設定所需的環境變數
$ mkdir ./logs ./plugins ./dags

$ chmod -R 777 logs/ dags/ plugins/

$ echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env


Step 4: 使用docker compose設定並建置airflow webserver (port:8080)
$ docker-compose up airflow-init
 
$ docker-compose up -d --build


需要下架Airflow時，執行
$ docker-compose down --volumes --rmi all
**使用docker compose V2時，執行
$ docker compose up airflow-init
 
$ docker compose up -d --build
(將docker-compose 改成docker compose) (目前在172.16.19.253上的Airflow即是用此版本上版)