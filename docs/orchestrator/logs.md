---
layout: default
title: Logs
nav_order: 2
parent: Orchestrator
---

# Logs
{:.no_toc}

## Table of Contents
{:.no_toc}
- TOC
{:toc}

## Intro

The logging tab displays all logs created by automation processes.

A log contains the following information:

**Log time**: The time and date the log was created.

**Log level**: The level the log was created at. There are 3 levels: Trace, Info and Error.

**Process Name**: The name of the process that created the log. This is defined on the trigger.

**Message**: The message of the log.

---

## Description of the UI

At the top of the log tab are filtering options to only show relevant logs.

Below that a table of all the relevant logs are displayed. By default the logs are sorted by
the log time with the newest log first. The sorting can be changed by clicking the column names.

![logging tab](images/logs.png)

---

## Filter Options

When applying filters the table is automatically updated to match the filter.

The filter options are as follows:

**From date**: The date and time where the logs must be created after.

**To date**: The date and time where the logs must be created before.

**Process name**: The name of the process that created the log. The dropdown menu
will contain all processes that has created logs in the database.

**Level**: The level of the log. Trace, Info or Error.

**Limit**: The maximum amount of logs to load from the database. Loading many logs
can potentially be slow. The newest logs matching the filters will be loaded first.

---

## Viewing long messages

To view log messages that don't fit in the table click the log in the table
to open it in a pop-up window. Click outside of the popup to close it.