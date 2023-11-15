---
layout: default
title: Database
nav_order: 0
parent: Setup
---

# Database Setup
{:.no_toc}

## Table of Contents
{:.no_toc}
- TOC
{:toc}

## Intro

OpenOrchestrator is designed to be agnostic towards the dialect of the central database.
At the moment only Microsoft SQL Server with ODBC has been tested properly, but support for the
following dialects should be possible:
- PostgreSQL
- MySQL and MariaDB
- SQLite
- Oracle
- Microsoft SQL Server

When your database is setup and running you need to identify the connection string to use in the coming steps.
OpenOrchestrator uses [SQLAlchemy-style connection strings](https://docs.sqlalchemy.org/en/20/dialects/index.html).

For a MSSQL+ODBC database the connection string looks something like this:
```
mssql+pyodbc://<username>:<password>@<dsnname>
```

Or for when using windows credentials to log in instead of username/password:
```
mssql+pyodbc://<server>/<database>?driver=ODBC+Driver+17+for+SQL+Server
```

Getting the connection string right can be a little difficult the first time you try it, but luckily you
only need to do it once!

## Creating Database Tables

The creation of all the needed database tables is done in the Orchestrator app which is introduced in a later section.

## Managing User Access

One of the design principles of OpenOrchestrator is to use existing solutions whenever possible.
For this reason all user access management is done on the database. 

In other words: To control which users has access to OpenOrchestrator and all of its data you need to
edit user permissions on the database and not in OpenOrchestrator.

If you need to have different environments for different users to separate data access, simply create multiple databases
with different user access schemas.