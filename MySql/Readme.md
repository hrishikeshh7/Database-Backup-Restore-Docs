---------------------------------------------------------------------------------------------------------------------------

---------------------------------------------------------------------------------------------------------------------------

# MySQL Backup and Restore

## 1. Backup MySQL Database

1) Take Backup of Single Database using mysqldump Command

```
Syntax:
sudo docker exec -t '<mysql_cont_name>' mysqldump -u '<USERNAME>' -p'<PASSWORD>' '<DB_NAME>' > '<BACKUPFILE_NAME>.sql'

Example:
sudo docker exec -t mysql_test mysqldump -u root -padmin test_db > backup.sql
```

2) Copy the Backup File to Another Server

```
Syntax:
scp -r '<Backup_file>.sql' '<username>'@'<IP>':'</Path/in/machine>'

Example:
scp -r backup.sql hrishikesh@192.168.1.195:/home/hrishikesh
```

## 2. Restore Psql Database

3) Create a Blank Database

```
Syntax:
create database '<database_name>'

Example:
create database test_db_2
```

4) Restore the Database

```
Syntax:
mysql -u '<USERNAME>' -p '<New_DB_NAME>' < '<Backup_File>'

Example:
mysql -u root -p test_db_2 < backup.sql
```
