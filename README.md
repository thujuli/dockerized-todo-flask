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

```
# clone repository (ssh)
git clone git@github.com:thujuli/todo-flask.git

# clone repository (https)
git clone https://github.com/thujuli/todo-flask.git
```

![clone repository](images/git-clone.png?raw=true "clone repository")

##### Change directory

```
cd todo-flask/
```

![change directory](images/cd-todo.png?raw=true "change directory")

##### Running docker compose

```
docker compose up -d
```

![docker compose](images/docker-compose.png?raw=true "docker compose")

##### Check services

```
docker ps
```

![docker ps](images/docker-ps.png?raw=true "docker ps")

##### Copy script

```
cp script/backup.sh ~
```

![copy script](images/cp-script.png?raw=true "copy script")

##### Edit crontab (using nvim)

```
EDITOR=nvim crontab -e
```

![edit crontab](images/edit-crontab.png?raw=true "edit crontab")

##### Add cronjobs (auto backup at 23:59 every day)

```
59 23 * * * /bin/sh ~/backup.sh
```

![add cronjobs](images/add-cronjobs.png?raw=true "add cronjobs")

##### Exit nvim

```
:wq
```

![exit nvim](images/exit-nvim.png?raw=true "exit nvim")

##### List documents (because, backup file store in documents)

```
ls ~/Documents/
```

![list documents](images/ls-documents.png?raw=true "list documents")

##### Copy backup file to postgres services

```
bash script/copy.sh
```

![copy backup file](images/copy.png?raw=true "copy backup file")

##### Restore database from backup file

```
bash script/restore.sh
```

![restore database](images/restore.png?raw=true "restore database")

##### Exec psql on flask-psql service

```
docker exec -it flask-psql -U postgres
```

![docker exec](images/docker-exec.png?raw=true "docker exec")

##### List database

```
\l
```

![list database](images/db-list.png?raw=true "list database")
