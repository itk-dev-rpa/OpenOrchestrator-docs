---
layout: default
title: Orchestrator
nav_order: 2
has_children: true
---

# Orchestrator

The Orchestrator application is used by admins to control process schedules,
read logs and edit constants/credentials used by automation processes among other things.

To run Orchestrator make sure OpenOrchestrator is installed and run the following command
in the command line:

```
python -m OpenOrchestrator -o
```

If you want to create a shortcut instead of typing into the command line, you can simply create a .bat
file containing the command above. Then you just have to double-click the .bat file to launch Orchestrator.

## Using the application

The Orchestrator application contains 5 tabs which will be introduced in the following subsections.

All data in the UI is updated every 10 seconds as long as the window is in focus. I you want to manually
force an update you can press the refresh button in the top right corner.
Next to the refresh button you can toggle dark mode on and off.

![header](images/header.png)
