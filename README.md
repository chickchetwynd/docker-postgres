# PostgreSQL Docker Setup

This repository contains a Dockerfile to quickly set up a PostgreSQL database.

## Prerequisites

- Docker installed and running

## Setup Instructions

1. Clone this repository:
   ```bash
   git clone <your-repo-url>
   cd <repo-name>
   ```

2. Create your environment file:
   ```bash
   cp .env.template .env.local
   ```
   Then edit `.env.local` with your desired values

3. Build the Docker image:
   ```bash
   docker build -t ny-taxi-postgres --build-arg POSTGRES_USER=$(grep POSTGRES_USER .env.local | cut -d '=' -f2) \
       --build-arg POSTGRES_PASSWORD=$(grep POSTGRES_PASSWORD .env.local | cut -d '=' -f2) \
       --build-arg POSTGRES_DB=$(grep POSTGRES_DB .env.local | cut -d '=' -f2) .
   ```

4. Run the container:
   ```bash
   docker run -d \
       -v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data \
       -p 5432:5432 \
       ny-taxi-postgres
   ```

## What this does

Creates a PostgreSQL database with:
- Username: from .env.local
- Password: from .env.local
- Database name: from .env.local
- Port: 5432
- Data persisted in `./ny_taxi_postgres_data/`

## Security Note

Make sure to never commit your `.env.local` file to version control. It's already added to `.gitignore` for your protection. 