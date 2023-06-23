---
layout: default
title: Database Schemas
nav_order: 1
---

# Logs table

|Time                       |Level      |Process        |Message                    |
|---                        |---        |---            |---                        |
|datetime                   |tinyInt    |text           |text                       |
|2023-06-19 12:28:05.700    |2          |Procesnavn1	|Dette er en besked bip bop |

# Triggers table

|Cron_expr      |Last_run                   |Next_run                  |process_path                                  |is_git_repo |Force_update|
|---            |---                        |---                       |---                                           |---         |---         |
|varchar(255)   |datetime                   |datetime                  |text                                          |bit         |bit         |
|'0 0 * * *'    |2023-06-19 00:00:00.000    |2023-06-20 00:00:00.000   |C:\Repos\OS2RPA-docs\docs\database_schemas.md |True        |True        |

# Credentials table

| id        	| username 	| password               	|
|-----------	|----------	|------------------------	|
| text         	| text     	| text (encrypted)        	|
| sap_login 	| user123  	| DToN4CzwFYLy4930XgLLPA 	|

# Constants table

| id        	    | value 	    |
|-----------	    |----------	    |
| text         	    | text     	    |
| reciever_email 	| hello@hi.com  |
