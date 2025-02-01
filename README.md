# PostgreSQL Docker Setup

This repository contains a Dockerfile to quickly set up a PostgreSQL database.

## Prerequisites

- Docker installed and running
- Docker Compose installed

## Setup Instructions

1. Clone this repository:
   ```bash
   git clone <your-repo-url>
   cd <repo-name>
   ```

2. Create your environment file:
   ```bash
   cp .env.template .env
   ```
   Then edit `.env` with your desired values

3. Start the database:
   ```bash
   docker-compose up -d
   ```
   This will automatically create a directory called `ny_taxi_postgres_data`  in your project root to persist the database data.

## What this does

Creates a PostgreSQL database with:
- Username: from .env
- Password: from .env
- Database name: from .env
- Port: 5432
- Data persisted in `./ny_taxi_postgres_data/` (automatically created)

## Security Note

Make sure to never commit your `.env` file or the `ny_taxi_postgres_data` directory to version control. Both are already added to `.gitignore` for your protection.

## Stopping the Database

To stop the database:
```bash
docker-compose down
``` 