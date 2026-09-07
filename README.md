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
