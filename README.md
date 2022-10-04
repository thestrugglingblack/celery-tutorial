```text

 ______     ______     __         ______     ______     __  __        ______   __  __     ______   ______     ______     __     ______     __        
/\  ___\   /\  ___\   /\ \       /\  ___\   /\  == \   /\ \_\ \      /\__  _\ /\ \/\ \   /\__  _\ /\  __ \   /\  == \   /\ \   /\  __ \   /\ \       
\ \ \____  \ \  __\   \ \ \____  \ \  __\   \ \  __<   \ \____ \     \/_/\ \/ \ \ \_\ \  \/_/\ \/ \ \ \/\ \  \ \  __<   \ \ \  \ \  __ \  \ \ \____  
 \ \_____\  \ \_____\  \ \_____\  \ \_____\  \ \_\ \_\  \/\_____\       \ \_\  \ \_____\    \ \_\  \ \_____\  \ \_\ \_\  \ \_\  \ \_\ \_\  \ \_____\ 
  \/_____/   \/_____/   \/_____/   \/_____/   \/_/ /_/   \/_____/        \/_/   \/_____/     \/_/   \/_____/   \/_/ /_/   \/_/   \/_/\/_/   \/_____/ 
                                                                                                                                                     

```
## Table of Contents
* [Overview](#overview)
* [Dependencies](#dependencies)
* [Installation](#installation)
* [Getting Started](#getting-started)
  * [Start RabbitMQ](#start-rabbitmq)
  * [Start Sqlite3](#start-sqlite3)
  * [Start Celery](#start-celery)
* [Things I Learned](#things-i-learned)

## Overview
Celery is an open source asynchronous task/job queue library.  It is a task queue that holds the tasks and distributes them to workers in an even and proper manner.  It is ideally focus on real-time operation and supports scheduling.  This library is often used for cases such as firing off emails, processing large amounts of data, updating database and other tasks that require some scheduling or processing time.  

The components of Celery are the following:
* **Producers** are _web nodes_ that manage web requests.  When the application is processing, tasks are assigned to Celery into the task queue.
* **Consumer** are _worker nodes_ that monitors the queue head, the workers take the task and perform it. 
* **Queue** is the message broker that acts as a bridge between producer and consumer.  Its passes messages between the web application and celery workers.

## Dependencies
* Sqlite3
* Python 3.6
* RabbitMQ

## Installation
1. Run `pip install celery` to install Celery library

## Getting Started
Before getting started, all dependencies must be downloaded.

### Start RabbitMQ
1. Run `rabbitmq-server` in terminal.
2. Go to `http://localhost:15672` graphic interface.
3. Enter `guest` for both username and password. (Default settings)
4. Verify that the database is running.

### Start Sqlite3
1. Run `sqlite3 db.sqlite3`
2. Enter `.tables` to view the list of tables in sqlite3.

### Start Celery
1. Run `celery -A task worker --loglevel=info`


## Things I Learned
* There are two tables that are created when a task is executed. These tables are used  to keep track of which tasks have been completed. To view these tables in sqlite3 run the following
```
 select * from celery_taskmeta
```

## References
* [Asynchronous Tasks in Python](https://www.youtube.com/watch?v=THxCy-6EnQM)
* [My Experiences With a Long-Running Celery-Based Microprocess](https://theblog.workey.co/my-experiences-with-a-long-running-celery-based-microprocess-b2cc30da94f5)

