Установка постгрес
Method 1

Step 1

sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'  

Step 2

wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O - | sudo apt-key add - 

Step 3.

sudo apt-get update  
sudo apt-get upgrade 
sudo apt-get install postgresql-9.6 


postgres_exporter port 9187

Пропишем сервис

cp ./postgres_exporter.bin/postgres_exporter /usr/bin

vi /etc/systemd/system/postgres_exporter.service

после прописания службы

systemctl daemon-reload
systemctl start postgres_exporter

создать базу
create database test_db;

Создаются тестовые таблички
pgbench -i test

тестовая нагрузка
pgbench -c 50 -C -j 2 -P 10 -T 30 -M extended test

c 50 создать 50 коннектов, каждый раз по 50

-j 2 два потока

-P 10 показывать прогресс каждые 10 секунд