---
title: Home
layout: home
nav_order: 0
---

# Intro

This documentation introduces the OpenOrchestrator project.

The design goals of OpenOrchestrator where:

- To be simple and easy to use.
- To run processes automatically based on simple scheduling rules.
- To make scaling up or down as simple as possible.
- To make everything asynchronous.
- To give administrators full control of their setup and data.
- To use as many standard components as possible.

A very simple drawing of how OpenOrchestrator works can be seen below:

![Architecture](docs/illustrations/setup/architecture.png)

A database holds all information regarding the automation processes:

- Schedules
- Logs
- Constants
- Credentials

Administrators uses an app 'Orchestrator' to control and view the data in the database,
and another app 'Scheduler' runs on the worker machines reading the data from the database.

With this simple setup it's theoretically possible to have an unlimited number of administrators 
and worker machines, with the ability to add and remove them as needed.