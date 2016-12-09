# https://hub.docker.com/_/postgres/
Environment Variables
The PostgreSQL image uses several environment variables which are easy to miss. While none of the variables are required, they may significantly aid you in using the image.

POSTGRES_PASSWORD
This environment variable is recommended for you to use the PostgreSQL image. This environment variable sets the superuser password for PostgreSQL. The default superuser is defined by the POSTGRES_USER environment variable. In the above example, it is being set to "mysecretpassword".

POSTGRES_USER
This optional environment variable is used in conjunction with POSTGRES_PASSWORD to set a user and its password. This variable will create the specified user with superuser power and a database with the same name. If it is not specified, then the default user of postgres will be used.

PGDATA
This optional environment variable can be used to define another location - like a subdirectory - for the database files. The default is /var/lib/postgresql/data, but if the data volume you're using is a fs mountpoint (like with GCE persistent disks), Postgres initdb recommends a subdirectory (for example /var/lib/postgresql/data/pgdata ) be created to contain the data.

POSTGRES_DB
This optional environment variable can be used to define a different name for the default database that is created when the image is first started. If it is not specified, then the value of POSTGRES_USER will be used.

POSTGRES_INITDB_ARGS
This optional environment variable can be used to send arguments to postgres initdb. The value is a space separated string of arguments as postgres initdb would expect them. This is useful for adding functionality like data page checksums: -e POSTGRES_INITDB_ARGS="--data-checksums".


For those taking it to the next level by:
Physically distributed service
Load balancing
Unlimited scaling by adding new nodes
Automatic recovery from failures, deleting, and loss of connection between the nodes
Design with no single point of failure

Here is the link:
https://medium.com/@dpaunin/postgresql-cluster-into-kubernetes-cluster-f353cde212de#.xl00oi4ta
