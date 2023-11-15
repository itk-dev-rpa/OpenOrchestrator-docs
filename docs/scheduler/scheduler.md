---
layout: default
title: Scheduler
nav_order: 3
has_children: true
---

# Scheduler

The Scheduler is run on the worker machines where the automation processes should run.

To run Scheduler make sure OpenOrchestrator is installed and run the following command:

```
python -m OpenOrchestrator -s
```

If you want to create a shortcut instead of typing into the command line, you can simply create a .bat file containing the command above. Then you just have to double-click the .bat file to launch Scheduler.

## Git repo folder

When defining a trigger in Orchestrator it's possible to define the trigger's process
path as a git repo. When Scheduler want to run such a process it clones the git
repo to the machine before launching the process.

At the moment it defaults to cloning the repos to a folder on the desktop called
'Scheduler Repos'. Unless Scheduler is terminated unexpectedly this folder will
be deleted when no processes are running.
