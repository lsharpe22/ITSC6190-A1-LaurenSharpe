# ITCS6190 Assignment 1 

## Overview

This project demonstrates a two-container application using Docker and Docker Compose. 
One container runs a PostgreSQL database containing seeded trip data. The second 
container runs a Python application that connects to the database, performs SQL queries, 
computes summary statistics, and writes the results to `out/summary.json`.

## Project Structure

```text
app/
    main.py
    Dockerfile

db/
    init.sql
    Dockerfile

out/
    summary.json

compose.yml
Makefile
.gitignore
README.md

```
## How to Run

To run the full stack in the terminal, either use:
```
docker compose up --build
```
Or:
```
make
```

## Example output:
The output is print to out/summary.json and looks like:
```
{
  "total_trips": 6,
  "avg_fare_by_city": [
    {
      "city": "Charlotte",
      "avg_fare": 16.25
    },
    {
      "city": "New York",
      "avg_fare": 19.0
    },
    {
      "city": "San Francisco",
      "avg_fare": 20.25
    }
  ],
  "top_by_minutes": [
    {
      "id": 6,
      "city": "San Francisco",
      "minutes": 28,
      "fare": 29.3
    },
    {
      "id": 4,
      "city": "New York",
      "minutes": 26,
      "fare": 27.1
    },
    {
      "id": 2,
      "city": "Charlotte",
      "minutes": 21,
      "fare": 20.0
    },
    {
      "id": 1,
      "city": "Charlotte",
      "minutes": 12,
      "fare": 12.5
    },
    {
      "id": 5,
      "city": "San Francisco",
      "minutes": 11,
      "fare": 11.2
    },
    {
      "id": 3,
      "city": "New York",
      "minutes": 9,
      "fare": 10.9
    }
  ]
}
```
## Troubleshooting
If the database is not ready, Docker Compose uses a PostgreSQL health check and waits for the database to become healthy before starting the Python application.

If the application cannot write to out/summary.json, check that the out directory exists and that Docker has permission to access the project directory
