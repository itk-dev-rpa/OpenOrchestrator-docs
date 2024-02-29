---
layout: default
title: Database Schemas
nav_order: 7
---

# Database Schemas

## Intro

This sections showcases the database schemas in detail. This is probably not
relevant to most users and can be skipped. If you want to extract data for
statistics it's nice to know what data is located where.

Since OpenOrchestrator uses an ORM to handle SQL transactions
and because it's designed to be SQL dialect agnostic, the exact data types
and layout may vary.

## Triggers

There are 4 trigger tables even if there's only 3 kinds of triggers. Most of the trigger
data is in one common table and then type specific data are in 3 sub-tables.

### Triggers

| Column         | Type          | Note     |
| -------------- | ------------- | -------- |
| id             | UUID          | PK       |
| trigger_name   | varchar(100)  |          |
| process_name   | varchar(100)  |          |
| last_run       | datetime      | nullable |
| process_path   | varchar(250)  |          |
| process_args   | varchar(1000) | nullable |
| process_status | Enum          |          |
| is_git_repo    | bit           |          |
| is_blocking    | bit           |          |
| type           | Enum          |          |

### Scheduled_Triggers

| Column    | Type         | Note             |
| --------- | ------------ | ---------------- |
| id        | UUID         | PK, FK(Triggers) |
| cron_expr | varchar(200) |                  |
| next_run  | datetime     |                  |

### Queue_Triggers

| Column         | Type         | Note             |
| -------------- | ------------ | ---------------- |
| id             | UUID         | PK, FK(Triggers) |
| queue_name     | varchar(100) |                  |
| min_batch_size | int          |                  |

### Single_Triggers

| Column   | Type     | Note             |
| -------- | -------- | ---------------- |
| id       | UUID     | PK, FK(Triggers) |
| next_run | datetime |                  |

## Logs

| Column       | Type          | Note |
| ------------ | ------------- | ---- |
| id           | UUID          | PK   |
| log_time     | datetime      |      |
| log_level    | Enum          |      |
| process_name | varchar(100)  |      |
| log_message  | varchar(8000) |      |

## Constants

| Column     | Type          | Note |
| ---------- | ------------- | ---- |
| name       | varchar(100)  | PK   |
| value      | varchar(1000) |      |
| changed_at | datetime      |      |

## Credentials

Credential passwords are stored as AES encrypted strings in the database and
needs to be decrypted using the encryption key to be usable.

| Column     | Type          | Note |
| ---------- | ------------- | ---- |
| name       | varchar(100)  | PK   |
| username   | varchar(250)  |      |
| password   | varchar(1000) |      |
| changed_at | datetime      |      |

## Queues

All queues and queue elements actually exists in a single table in the database. Queues
are differentiated by the queue_name column. Practically speaking a queue doesn't exist
if there are no queue elements in it because there's no separate definition of the queue
anywhere.

| Column       | Type          | Note     |
| ------------ | ------------- | -------- |
| id           | UUID          | PK       |
| queue_name   | varchar(100)  |          |
| status       | Enum          |          |
| data         | varchar(2000) | nullable |
| reference    | varchar(100)  | nullable |
| created_date | datetime      |          |
| start_date   | datetime      | nullable |
| end_date     | datetime      | nullable |
| message      | varchar(1000) | nullable |
| created_by   | varchar(100)  | nullable |