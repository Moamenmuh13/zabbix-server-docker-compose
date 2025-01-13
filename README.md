## Overview

This repository contains a `docker-compose.yml` file to set up a Zabbix monitoring environment using Docker. The setup includes the following services:

- **zabbix-db**: MySQL database for Zabbix
- **zabbix-server**: Zabbix server
- **zabbix-web**: Zabbix web interface
- **zabbix-agent**: Zabbix agent for local monitoring
- **phpmyadmin**: phpMyAdmin for managing the MySQL database

## Prerequisites

- Docker
- Docker Compose

## Usage

1. Clone the repository:
    ```sh
    git clone /home/zabbix/zabbix-server-docker-compose
    cd zabbix-server-docker-compose
    ```

2. Create a `.env` file in the root directory and set the following environment variables:
    ```env
    MYSQL_ROOT_PASSWORD=your_root_password
    MYSQL_DATABASE=zabbix
    MYSQL_USER=zabbix
    MYSQL_PASSWORD=your_password
    ZBX_SERVER_HOST=zabbix-server
    PHP_TZ=UTC
    PMA_HOST=zabbix-db
    PMA_PORT=8081
    ```

3. Start the services:
    ```sh
    docker-compose up -d
    ```

4. Access the Zabbix web interface at `http://localhost:8080` and phpMyAdmin at `http://localhost:8081`.

## Volumes

The following volumes are used to persist data:

- `./zabbix_db:/var/lib/mysql`: MySQL data
- `./zabbix_server:/var/lib/zabbix`: Zabbix server data
- `./zabbix_agent:/var/lib/zabbix`: Zabbix agent data

## Networks

A custom bridge network `zabbix-net` is created for the services to communicate.

## Stopping the Services

To stop and remove the containers, network, and volumes defined in the `docker-compose.yml` file, run:
```sh
docker-compose down
```

## License

This project is licensed under the MIT License.
