---
layout: default
title: Scheduler
nav_order: 3
has_children: true
---

# Scheduler

The Scheduler is run on the worker machines where the automation processes should run.
It needs to be active at all times when you want automation processes to be run.
It then checks the database periodically for any automation process triggers that needs to be run.

When a trigger in the database should be run the Scheduler first checks to see if the
process is allowed to run in parallel with other processes and if any other processes are running.

To run Scheduler make sure OpenOrchestrator is installed and run the following command:

```
python -m OpenOrchestrator -s
```

If you want to create a shortcut instead of typing into the command line, you can simply create a .bat file
containing the command above. Then you just have to double-click the .bat file to launch Scheduler.

---

## Processes hosted in Git

When defining a trigger in Orchestrator it's possible to define the trigger's process
path as a git repo. When Scheduler want to run such a process it clones the git
repo to the machine before launching the process.

The Git folder is then scanned for a file named "main.py" which will be executed.
This file can be anywhere in the folder or subfolders but if you have multiple the first found is used.

At the moment it defaults to cloning the repos to a folder on the desktop called
'Scheduler Repos'. Unless Scheduler is terminated unexpectedly this folder will
be deleted when the processes are done running.
