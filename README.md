# Django-PostgreSQL

A starter template for Django projects with PostgreSQL.

## Requirements

First, setup a virtual environment.

```
$ python3 -m venv venv
$ source venv/bin/activate
$ pip install --upgrade pip
$ pip install requirements.txt
```

Run a local PostgreSQL server with Docker:

```
$ docker run --rm \
    --name db \
    -e POSTGRES_PASSWORD=<pwd> \
    -e POSTGRES_USER=<user> \
    -e POSTGRES_DB=<db> \
    -p 5432:5432 \
    -v data:/var/lib/postgresql/data \
    postgres
$ cat <<EOF >> ~/.pg_service.conf
[my_service]
host=localhost
port=5432
user=<user>
dbname=<db>
EOF
```

Set up a local `.pgpass` file.

```
$ echo "localhost:5432:<db>:<user>:<pwd>" > .pgpass
$ chmod 600 .pgpass
```

Check that Django can interact with the database:

```
$ ./manage.py showmigrations
```
