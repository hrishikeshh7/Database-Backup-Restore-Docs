---------------------------------------------------------------------------------------------------------------------------

---------------------------------------------------------------------------------------------------------------------------

# Postgres Backup and Restore

## 1. Backup Psql Database

1) Take Backup of Single Database using PG Dump Command

```
Syntax:
sudo docker exec -t '<psql container name>' pg_dump -c -U '<postgres user>' '<database to dump>' > '<dump_file_name>'.sql

Example:
sudo docker exec -t postgres_db pg_dump -c -U postgres prod_db > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql
```

2) Copy the Backup File to Another Server

```
Syntax:
scp -r '<Backup_file>.sql' '<username>'@'<IP>':'</Path/in/machine>'

Example:
scp -r dump_01-04-2024_12_34_56.sql hrishikesh@192.168.1.195:/home/hrishikesh
```

## 2. Restore Psql Database

3) Create a Blank Database

```
Syntax:
create database '<database_name>'

Example:
create database test_db
```

4) Restore the Database

```
Syntax:
cat '<dump_file_name>'.sql | sudo docker exec -i '<psql container name>' psql -U '<postgres user>' -d '<database name>'

Example:
cat dump_01-04-2024_12_34_56.sql | sudo docker exec -i postgres_cont psql -U postgres -d test_db
```
