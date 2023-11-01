# MySQL & phpMyAdmin Docker Setup

This is a basic setup for mysql and phpmyadmin to run mysql locally on machine for development using docker.

This repository contains a `docker-compose.yml` file that sets up MySQL 5.7 and phpMyAdmin for local development.

## Prerequisites

- Docker
- Docker Compose

## Quick Start

1. **Clone the repository**

   ```bash
   git clone https://github.com/haidertm/mysql-docker.git
   ```

2. **Navigate to the repository folder**

   ```bash
   cd mysql-docker
   ```

3. **Start the containers**

   ```bash
   docker-compose up -d
   ```

4. **Access phpMyAdmin**

   Open your web browser and go to [http://localhost:9090](http://localhost:9090).

   - **Username**: `root`
   - **Password**: `admin`

5. **Access MySQL**

   - **Host**: `localhost`
   - **Port**: `3306`
   - **Username**: `root`
   - **Password**: `admin`

## Configuration

The `docker-compose.yml` contains the following services:

### MySQL

- **Image**: `mysql:5.7`
- **Environment Variables**:
  - `MYSQL_ROOT_PASSWORD`: The password for the MySQL root user.
  - `MYSQL_DATABASE`: The name of the initial database to be created.
- **Ports**: `3306:3306`
- **Volumes**: 
  - `${MYSQL_DATA_DIR-./data/mysql}:/var/lib/mysql`: Data directory.
  - `${MYSQL_LOG_DIR-./logs/mysql}:/var/log/mysql`: Log directory.

### phpMyAdmin

- **Image**: `phpmyadmin/phpmyadmin`
- **Environment Variables**:
  - `PMA_HOST`: The hostname of the MySQL service.
  - `PMA_USER`: The user for accessing MySQL.
  - `PMA_PASSWORD`: The password for the MySQL user.
- **Ports**: `9090:80`
- **Depends On**: MySQL container.

## Customize Environment Variables

To change default environment variables, you can create a `.env` file in the root of your project and specify the values for the variables. For example:

```
MYSQL_ROOT_PASSWORD=mysecretpassword
MYSQL_DATABASE=mydatabase
```

---
Don't forget to replace placeholders like `YOUR_GITHUB_USERNAME` and `YOUR_REPOSITORY_NAME` with actual values.

