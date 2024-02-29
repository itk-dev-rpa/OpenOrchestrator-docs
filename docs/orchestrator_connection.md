---
layout: default
title: Orchestrator Connection
nav_order: 5
---

# Orchestrator Connection

## Intro

When developing automation processes for use with OpenOrchestrator you
need a way to interface with the data in OpenOrchestrator's database. This could
be when fetching queue elements, reading credentials or creating logs.

For this purpose you can use the OrchestratorConnection Python object.

## Creating the OrchestratorConnection

First you need to have the OpenOrchestrator package installed in the environment your automation
process is running in.

Then you need to import the OrchestratorConnection object:

```python
from OpenOrchestrator.orchestrator_connection.connection import OrchestratorConnection
```

In most cases your automation process is started from the Scheduler application. In this case you can
use this simple code to create the connection:

```python
orchestrator_connection = OrchestratorConnection.create_connection_from_args()
```

This will create a OrchestratorConnection object that is configured to connect to the same database
as the Scheduler is connected to. Additionally any process arguments and the process name defined on
the trigger in Orchestrator is also passed along to the OrchestratorConnection.

If you for some reason want to define a custom OrchestratorConnection you can construct it using the objects
constructor:

```python
orchestrator_connection = OrchestratorConnection(process_name: str, connection_string: str, crypto_key: str, process_arguments: str)
```

**Note** it's not possible to have multiple OrchestratorConnections connected to different databases simultaneously
or with different encryption keys within the same process as the connection is dependent on global state.
Ideally you should only create a single connection and then pass it around.

## Creating logs

When creating logs you need to use one of three functions: 

- log_trace
- log_info
- log_error

Each of these functions takes a string message as input and creates a log of the appropriate level
in Orchestrator. The log is automatically stamped with the current time and the name of the process.

Example:

```python
orchestrator_connection.log_info("My hovercraft is full of eels.")
```

## Working with constants and credentials

When you want to get a constant or credential from Orchestrator you use the functions:

```python
get_constant(self, constant_name: str) -> Constant
get_credential(self, credential_name: str) -> Credential
```

Both take a name string as input and returns a Constant or Credential object respectively.

Example:

```python
my_credential = orchestrator_connection.get_credential("My credential name")
print(my_credential.password)
```

You can also update constants and credentials with the functions:

```python
update_constant(self, constant_name: str, new_value: str) -> None
update_credential(self, credential_name: str, new_username: str, new_password: str) -> None
```

Example:

```python
orchestrator_connection.update_constant("My constant name", "My new value")
```

When working with credentials all encryption and decryption of passwords are done automatically.

## Working with queues

### Creating queue elements

Before you can work with queue elements you need to create some first.

You can either create them one by one:

```python
create_queue_element(queue_name: str, reference: str = None, data: str = None, created_by: str = None) -> QueueElement
```

Example:

```python
orchestrator_connection.create_queue_element("My queue name", reference="1254", created_by="Me")
```

Or you can create them in bulk to be more efficient:

```python
bulk_create_queue_elements(queue_name: str, references: tuple[str], data: tuple[str], created_by: str = None) -> None
```

Example:

```python
# Create 5 queue elements at once
references = [1, 2, 3, 4, None]
data = ["Ha", "He", "Ultron", "Nop", None]
orchestrator_connection.bulk_create_queue_elements("My bulk queue", references=references, data=data)
```

### Fetching queue elements

When you have some queue elements and now need to process you need to fetch them from the database.
You can get them one by one:

```python
get_next_queue_element(queue_name: str, reference: str = None,
                               set_status: bool = True) -> QueueElement | None
```

This will get the next queue element with status "New". If you specify a reference the first
queue element with that exact reference and status "New" will be fetched.
The **set_status** argument tells Orchestrator if the queue element should be marked as "In Progress"
or not.

Example:

```python
queue_element = orchestrator_connection.get_next_queue_element("My queue name")
```

You can also fetch multiple queue elements at once:

```python
get_queue_elements(queue_name: str, reference: str = None, status: QueueStatus = None,
                           offset: int = 0, limit: int = 100) -> tuple[QueueElement, ...]
```

Here you can filter on reference and status. Additionally you can set a limit on how many queue elements
to fetch and how many queue elements to skip. The queue elements are returned in order of their creation time
with the newest first.

Example:

```python
from OpenOrchestrator.database.queues import QueueStatus
failed_elements = orchestrator_connection.get_queue_elements("My fail queue", status=QueueStatus.FAILED)
```

### Changing queue element status

When working with queue elements you need to set their status when they are done or failed:

```python
set_queue_element_status(element_id: str, status: QueueStatus, message: str = None) -> None
```

The **status** is an enum that has the possible values "New", "In Progress", "Done", and "Failed.
The **message** is an optional string to attach some message to the queue element. This could be
an error message or a description of the outcome.

Example:

```python
from OpenOrchestrator.database.queues import QueueStatus

queue_element = orchestrator_connection.get_next_queue_element("My queue name")

try:
    result = do_something_useful(queue_element)
    orchestrator_connection.set_queue_element_status(queue_element.id, QueueStatus.DONE, message=result)
except:
    orchestrator_connection.set_queue_element_status(queue_element.id, QueueStatus.FAILED)
```

### Deleting queue elements

You can also delete a queue element:

```python
delete_queue_element(element_id: str) -> None
```