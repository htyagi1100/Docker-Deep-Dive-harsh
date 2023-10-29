
# 2. Nginx application container creation part1
```
docker pull nginx
docker image ls
docker container run -d nginx
docker container ps
curl 172.17.0.2
ip a
docker network ls
docker container ps
docker container inspect fervent_shockley
docker container ps
docker ps
docker container stop fervent_shockley
docker container ps
docker container ps -a
docker container start fervent_shockley
docker container ps
docker container restart fervent_shockley
docker container ps
```



# 3. Nginx application container creation part2
```
docker container run -d -t --name nginx-demo --hostname aginxwebserver nginx
docker container ps
docker container stop fervent_shockley
docker container rm fervent_shockley
docker container ps
docker container inspect nginx-demo
docker container exec -t -i nginx-demo bash
docker container ps
docker container exec -t -i nginx-demo ip a
docker container ps
docker container rm -f nginx-demo
docker container ps
docker container ps -a

```






# Lab 4. Nginx application container creation part2

```
root@node-2:~# docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
mysql        latest    a3b6608898d6   4 days ago   596MB


root@node-2:~# docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS              PORTS                 NAMES
1c91ad734d8b   mysql     "docker-entrypoint.s…"   About a minute ago   Up About a minute   3306/tcp, 33060/tcp   mysql-server


root@node-2:~# docker container inspect mysql-server

            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "04a891dbce979e47d5a9a89b7c34aff671fefe24ddfcd5590fa605b11547cd5a",
                    "EndpointID": "0c9659900966e6c5ec3fe9c1c794be4688df856c8fbd58ffabeb4e32424de8c9",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",







- Here we can not access our mysql docker container so we need to install mysql package in our docker host machine to talk to our container 
root@node-2:~# mysql
Command 'mysql' not found, but can be installed with:
apt install mysql-client-core-8.0     # version 8.0.34-0ubuntu0.22.04.1, or
apt install mariadb-client-core-10.6  # version 1:10.6.12-0ubuntu0.22.04.1
root@node-2:~# apt install mysql-client-core-8.0
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2
Use 'apt autoremove' to remove them.
The following NEW packages will be installed:
  mysql-client-core-8.0
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 2,754 kB of archives.
After this operation, 62.0 MB of additional disk space will be used.
Get:1 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 mysql-client-core-8.0 amd64 8.0.34-0ubuntu0.22.04.1 [2,754 kB]
Fetched 2,754 kB in 3s (1,053 kB/s)
Selecting previously unselected package mysql-client-core-8.0.
(Reading database ... 182212 files and directories currently installed.)
Preparing to unpack .../mysql-client-core-8.0_8.0.34-0ubuntu0.22.04.1_amd64.deb ...
Unpacking mysql-client-core-8.0 (8.0.34-0ubuntu0.22.04.1) ...
Setting up mysql-client-core-8.0 (8.0.34-0ubuntu0.22.04.1) ...
Processing triggers for man-db (2.10.2-1) ...



- Connect the mysql docker container database
root@node-2:~# mysql -h 172.17.0.2 -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.2.0 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>



- to create a test database in mysql
mysql> create database tset;
Query OK, 1 row affected (0.00 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| tset               |
+--------------------+
5 rows in set (0.00 sec)

```
