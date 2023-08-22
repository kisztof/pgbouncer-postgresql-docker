# PgBouncer and PostgreSQL

This repository provides an example of setting up PgBouncer and PostgreSQL

## How to Use

1. Clone the Repository

If you haven't already, clone the repository to your local machine:

```
git clone https://github.com/kisztof/pgbouncer-postgresql-docker.git
```

2. Navigate to the Project Directory

Change to the project directory:

```
cd pgbouncer-postgresql-docker
```

3. Build and Start the Containers
Use Docker-Compose to build and start the containers:

```
docker-compose up -d
```

The -d flag will run the containers in detached mode.

4. Verify the Containers Are Running

You can list the running containers to ensure that both PgBouncer and PostgreSQL are up:

```
docker-compose ps
```

5. Connect to PostgreSQL Through PgBouncer

You can use a PostgreSQL client to connect to the database through PgBouncer on port 6432. Here's a command-line example using psql:

```
psql -h localhost -p 6432 -U username -W
```

Replace username with the appropriate PostgreSQL username you have configured.

6. Run Queries and Tests

Once connected, you can run SQL queries and test the connection pooling by opening multiple connections. You may also want to implement specific tests for your application's requirements.

7. Monitor PgBouncer

You can monitor PgBouncer by connecting to its admin console:

```
PGPASSWORD=password psql -p 6432 -U username -d pgbouncer
```

Then, you can run various commands to see the state:

```
SHOW STATS; will show statistics about the current databases.
SHOW POOLS; will show information about the connection pools.
SHOW CLIENTS; will show information about client connections.
```

Then, you can run commands like SHOW STATS; to view the connection statistics.

To test connection pooling specifically, you can open multiple connections to the database through PgBouncer and then use the SHOW POOLS; command to see how PgBouncer is managing those connections.

8. Stop the Containers

When you're done testing, you can stop the containers:

```
docker-compose down
```