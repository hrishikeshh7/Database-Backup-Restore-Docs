---------------------------------------------------------------------------------------------------------------------------

---------------------------------------------------------------------------------------------------------------------------

# MongoDB Backup and Restore

## 1. Backup MongoDB Database

1) Access the MongoDB container's shell:

```
Syntax:
docker exec -it '<container_id_or_name>' bash

Example:
docker exec -it mongodb bash
```

2) Inside the container's shell, run the mongodump command to create a backup

```
Syntax:
mongodump --username '<username>' --password '<password>' --out '<Backup_Folder_Name>'

Example:
mongodump --username root --password root --out /backup
```

3) Copy the backup data from the container to your host machine

```
Syntax:
docker cp <container_id_or_name>:/backup /host/path/to/save/backup

Example:
docker cp mongo_db:/backup /hrishikesh/home/mongodb_backup
```

## 2. Restore MongoDB Database

1) If you don't have a MongoDB instance running, Host a new MongoDB container

2) Copy the backup Folder to the new container OR Do the volume Mounting to that Backup Folder

```
** Copying Backup Folder To Conatiner ** 

Syntax:
docker cp '</host/path/to/backup>' '<new_container_id_or_name>':/backup

Example:
docker cp /hrishikesh/home/mongodb_backup new_mongo_db:/backup
```

3) Access the new container's shell

```
Syntax:
docker exec -it '<new_container_id_or_name>' bash

Example:
docker exec -it new_mongo_db bash

```

4) Inside the container's shell, restore the database using Mongorestore

```
Syntax:
mongorestore --drop --dir /backup --username '<username>' --password '<password>'

Example:
mongorestore --drop --dir /backup --username root --password root
```

5) Verify Data on New MongoDB
