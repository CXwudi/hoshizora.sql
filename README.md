# hoshizora.sql (CXwudi's fork)

This fork simply added the docker support so that running a dump DB is as simple as running one command.

## Prerequisites

- Docker
- Docker Compose

It is also recommended to use MacOS or *nix system. For Windows users, you can use WSL2 with Docker Desktop on host OS.

## Usage

1. Clone the repository:

    ```
    git clone https://github.com/CXwudi/hoshizora.sql.git
    ```

2. Download `dump.zip` from [here](https://vocaloid.eu/vocadb/dump.zip), and unzip it to `hoshizora.sql/dump`.

    Your directory structure should look like this:

    ![image](https://s2.loli.net/2023/06/05/V2CzlNHPo4wrsd9.png)

3. Run the following command in `hoshizora.sql/docker` directory:

    ```
    docker compose --profile initializer up -d
    ```

    And wait until both the `vocadump-hoshizora` and `vocadump-importer` containers are exited. Only the `vocadump-mariadb` is running.

    At this point, the DB is ready to be used 🙂

    To stop the DB, run:

    ```
    docker compose --profile initializer down
    ```

4. Next time when you want to run the dump DB again, simply run the following command in `hoshizora.sql/docker` directory:

    ```
    docker compose up -d
    ```

    To stop, run:

    ```
    docker compose down
    ```

Optionally, you can add `--profile debug` to the above commands to enable the [Adminer](https://hub.docker.com/_/adminer) container, then you can login to Adminer with the user/password/detabase defined in [`.env`](docker/.env) file to checkout the database schema.

## Original README

### Prerequisites

- [Node.js](https://nodejs.org/en/) (18.12.1 LTS)
- [yarn](https://yarnpkg.com/) (1.22.19)
- [MariaDB](https://mariadb.org/) (10.4.22)

### Usage

1. Clone the repository and change the current working directory:

```
git clone https://github.com/VocaDB/hoshizora.sql.git
cd hoshizora.sql
```

2. Download `dump.zip`, and unzip it.
3. Run the following commands:

```
yarn
yarn build
yarn start
mariadb -u root vocaloid_site < ./output/mariadb.sql
```
