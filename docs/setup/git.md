---
layout: default
title: Git
nav_order: 2
parent: Setup
---

# Git Setup
{:.no_toc}

## Table of Contents
{:.no_toc}
- TOC
{:toc}

## Intro

OpenOrchestrator features the possibility to host your automation processes in
a remote git repository. This way you can control and update the code for each process
in a centralized manner.

OpenOrchestrator then clones the code from your remote Git repository whenever your automation
process is triggered.

## Installing Git

Every computer that runs the Scheduler application needs to have Git installed if you want
to use the integrated Git functionality. Go to [Git](https://git-scm.com/) to download and install Git.

## Using private GIT repos

If you're using private repos on Github or similar to host your automation processes
it's important to setup the worker machines to be able to clone these private repos.

On Github you can set up an SSH connection that uses a key file on the computer to
authenticate. Other Git hosting services probably has something similar.
[Github: Connection with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)