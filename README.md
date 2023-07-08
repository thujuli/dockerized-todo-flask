# Dockerized Todo Flask

## Backgourd

This repository discuss about, How do i deploy [todo-flask](https://github.com/thujuli/todo-flask "todo-flask") with Docker Compose and Backup & Restore database postgres from host to docker container using bash script

## Requirements

- Text Editor (nano/vi/nvim)
- Linux/MacOS
- Docker
- Docker Compose
- Cron/Cronie (jobs scheduling)

## Setup and Running Project

##### Clone repository [todo-flask](https://github.com/thujuli/todo-flask "todo-flask")

![clone repository](images/git-clone.png?raw=true "clone repository")

```
# clone repository (ssh)
git clone git@github.com:thujuli/todo-flask.git

# clone repository (https)
git clone https://github.com/thujuli/todo-flask.git
```

##### Change directory

![change directory](images/cd-todo.png?raw=true "change directory")

```
cd todo-flask/
```

##### Running docker compose

![docker compose](images/docker-compose.png?raw=true "docker compose")

```
docker compose up -d
```

##### Check services

![docker ps](images/docker-ps.png?raw=true "docker ps")

```
docker ps
```

##### Copy script

![copy script](images/cp-script.png?raw=true "copy script")

```
cp script/backup.sh ~
```

##### Edit crontab (using nvim)

![edit crontab](images/edit-crontab.png?raw=true "edit crontab")

```
EDITOR=nvim crontab -e
```

##### Add cronjobs (auto backup at 23:59 every day)

![add cronjobs](images/add-cronjobs.png?raw=true "add cronjobs")

```
59 23 * * * /bin/sh ~/backup.sh
```

##### Exit nvim

![exit nvim](images/exit-nvim.png?raw=true "exit nvim")

```
:wq
```

##### List documents (because, backup file store in documents)

![list documents](images/ls-documents.png?raw=true "list documents")

```
ls ~/Documents/
```

##### Copy backup file to postgres services

![copy backup file](images/copy.png?raw=true "copy backup file")

```
bash script/copy.sh
```

##### Restore database from backup file

![restore database](images/restore.png?raw=true "restore database")

```
bash script/restore.sh
```

##### Exec psql on flask-psql service

![docker exec](images/docker-exec.png?raw=true "docker exec")

```
docker exec -it flask-psql -U postgres
```

##### List database

![list database](images/db-list.png?raw=true "list database")

```
\l
```
