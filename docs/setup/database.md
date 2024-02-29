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

OpenOrchestrator revolves around a central database which holds all information
needed for OpenOrchestrator to function.

OpenOrchestrator is designed to be agnostic towards the dialect of the central database.
At the moment only Microsoft SQL Server with ODBC has been tested properly, but support for the
following dialects should be possible:
- PostgreSQL
- MySQL and MariaDB
- SQLite
- Oracle
- Microsoft SQL Server

How to setup a database is outside the scope of this documentation.

---

## Connection string

When your database is setup and running you need to identify the connection string to use in the coming steps.
A connection string can be thought of as the address of the database and is needed for OpenOrchestrator
to connect to the database.

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

---

## Creating Database Tables

The creation of all the needed database tables is done in the Orchestrator app which is introduced in a later section.

---

## Managing User Access

One of the design principles of OpenOrchestrator is to use existing solutions whenever possible.
For this reason all user access management is done on the database. 

In other words: To control which users has access to OpenOrchestrator and all of its data you need to
edit user permissions on the database and not in OpenOrchestrator.

If you need to have different environments for different users to separate data access, simply create multiple databases
with different user access schemas.

---

## SQLite

**NOTE**: There's currently a bug in OpenOrchestrator which prevents SQLite to function properly. Most basic functions works
but some issues may occur.

SQLite is a lightweight database that exists in a single file on your computer and it comes pre-installed on most systems.

For production use it's not very useful with OpenOrchestrator but for testing it's excellent.
One could also use it for a 'single pc' setup if that's useful to you.

There's no setup required to use an SQLite database in OpenOrchestrator. Simply use a connection string in the following format:

```
sqlite+pysqlite:///<path to file>
```

Insert a path to where you want the database file to be with whatever name you want and OpenOrchestrator will
create the file for you when creating the database tables.

Example connection string:

```
sqlite+pysqlite:///C:\Users\abc\Desktop\temp\db.db
```