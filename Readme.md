# Symfony Docker Development Environment

This repository sets up a Docker environment for developing Symfony 6.4 applications using PHP 8.3, PostgreSQL, Redis, and Nginx. The project is organized for ease of development and local execution without requiring Composer to be installed locally.

## Project Structure

```bash
project-root/
├── app/                    # Symfony application files (installed automatically)
├── bin/                    # Executable scripts for Docker management and Symfony commands
│ ├── start                 # Script to start Docker containers
│ ├── stop                  # Script to stop Docker containers
│ ├── console               # Shortcut to Symfony console commands
│ ├── composer              # Shortcut to run Composer inside Docker container
│ └── install-symfony       # Script to install Symfony with optional version
├── config/                 # Configuration files for Docker services
│ ├── nginx/                # Nginx configuration for serving the Symfony app
│ └── php/                  # PHP Dockerfile and configuration files
└── docker-compose.yml      # Docker Compose configuration file
```

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Setup and Usage

### 1. Build and Start the Docker Environment

Run the following command to start the Docker environment. This will build the PHP, Nginx, PostgreSQL, and Redis containers and start them:

```
./bin/start
```

### 2. Install Symfony

Use the install-symfony script to install a specific Symfony version in the /app directory. If a version is not specified, the latest version will be installed by default.

Example Usage
Install a specific version (e.g., 6.4):

```bash
./bin/install-symfony "6.4.*"
```

Install the latest version:

```bash
./bin/install-symfony
```

Note: The script will prompt you to confirm if any files are present in the /app directory. All contents, including hidden files like .env, will be deleted to ensure a clean installation.

### 3. Running Symfony Commands

You can use the console script to run Symfony console commands inside the Docker container.

```bash
./bin/console <command>
```

Example:

```bash
./bin/console cache:clear 4. Managing Dependencies with Composer
```

Use the composer script to run Composer commands inside the Docker container.

```bash
./bin/composer <command>
```

Example:

```
./bin/composer require symfony/orm-pack 5. Stop the Docker Environment
```

To stop all running containers, use the stop script:

```bash
./bin/stop
```

## Configuration Details

PHP: Version 8.3 with necessary extensions for Symfony, configured in config/php/Dockerfile.
Nginx: Configured to serve the Symfony application from /app/public, with configuration in config/nginx/default.conf.
PostgreSQL: Configured as the database, with default credentials in docker-compose.yml.
Redis: Available for caching.

## Troubleshooting

Directory Not Empty: If /app is not empty, the install-symfony script will prompt you to confirm deletion of all contents, including hidden files.

Permissions Issues: If you encounter permission issues with the bin scripts, ensure they are executable:

```bash
chmod +x bin/\*
```

## License

This project is licensed under the MIT License. See the LICENSE file for details.
