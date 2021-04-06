# Assignment 
To make an API to fetch latest videos sorted in reverse chronological order of their publishing date-time from YouTube for a given tag/search query in a paginated response.

## Features
 - Django-Rest-Framework used to build REST API
 - Containerized using Docker and managed using Docker Compose
 -  Used Celery and Redis to call asynchronus services
 - In-built Admin Dashboard provided by django to view all videos in Database
   

## Prerequisites

This project is built on top of docker containers. So ensure that you have
Docker and Docker Compose installed on your system For installation
instructions refer: https://docs.docker.com/install/

Make appropriate changes in .env.sample file such as PAGINATED_PAGE_SIZE, FETCH_INTERVAL


## Starting the Server

Start Redis first:
```sh
docker-compose up -d redis
```
Then start whole project:
```
docker-compose up
```

> After the server is up, Go to http://localhost:8000/admin and add your Youtube v3 API.
> For using admin panel at `/admin`, default credentails are `admin:admin`
> Youtube v3 API can be generated from https://developers.google.com/youtube/v3/getting-started
> By default query's subject is "football", if you want to change go to ./app/video/task.py line number 103

## Details of the Project
 - As soon as server starts, the synchronization service starts fetching videos in a fixed interval. The interval can be configured through `.env.sample` file.
 - The video dashboard will be available at `http://127.0.0.1:8000/admin/video/video/`
 - The GET API to list all videos stored in the database is available at `http://127.0.0.1:8000`. This API is paginated and has `previous` and `next` url field.


