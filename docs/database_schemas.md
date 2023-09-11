---
layout: default
title: Database Schemas
nav_order: 4
---

# Logs

## Logs

|id        	    |log_time                   |log_level      |process_name   |log_message                |
|---        	|---                        |---            |---            |---                        |
|UID         	|datetime                   |tinyInt (FK)   |varchar(100)   |varchar(8000)              |
|urterg 	    |2023-06-19 12:28:05.700    |1 (Info)       |Procesnavn1	|Dette er en besked bip bop |

## Log_Level

|id         |level_text |
|---	    |---	    |
|0          |Trace      |
|1 	        |Info       |
|2          |Error      |

# Triggers

## Scheduled_Triggers

|id        	 |process_name  |cron_expr      |last_run                   |next_run                  |process_path             |process_status    |is_git_repo |force_update |blocking    |
|---         |---           |---            |---                        |---                       |---                      |---               |---         |---          |---         |
|UID         |varchar(100)  |varchar(200)   |datetime                   |datetime                  |varchar(250)             |tinyInt (FK)      |bit         |bit          |bit         |
|kasdlkf 	 |Process1      |'0 0 * * *'    |2023-06-19 00:00:00.000    |2023-06-20 00:00:00.000   |C:\processes\process1.py |1 (Running)       |True        |True         |True        |

## Email_Triggers

|id        	    |process_name  |email_folder   |last_run                   |process_path             |process_status    |is_git_repo |force_update  |blocking    |
|---        	|---           |---            |---                        |---                      |---               |---         |---           |---         |
|UID         	|varchar(100)  |varchar(250)   |datetime                   |varchar(250)             |tinyInt (FK)      |bit         |bit           |bit         |
|sadfsd	        |Process1      |Inbox/AKBO     |2023-06-19 00:00:00.000    |C:\processes\process1.py |1 (Running)       |True        |True          |True        |

## Single_Triggers

|id        	    |process_name  |next_run                   |last_run                   |process_path             |process_status    |is_git_repo |force_update  |blocking    |
|---        	|---           |---                        |---                        |---                      |---               |---         |---           |---         |
|UID         	|varchar(100)  |datetime                   |datetime                   |varchar(250)             |tinyInt (FK)      |bit         |bit           |bit         |
|jrthzc 	    |Process1      |2023-06-30 12:30:00.000    |2023-06-19 00:00:00.000    |C:\processes\process1.py |3 (Done)          |True        |True          |True        |

## Trigger_Status

|id     |status_text |
|----   |---	     |
|0      |Idle     	 |
|1 	    |Running     |
|2      |Failed   	 |
|3      |Done   	 |

# Storage

## Credentials

|cred_name	    |cred_username 	|cred_password            	|
|---        	|---    	    |---                    	|
|varchar(255)  	|varchar(255)   |varchar(255) (encrypted)  	|
|sap_login 	    |user123  	    |DToN4CzwFYLy4930XgLLPA 	|

## Constants

|constant_name  |constant_value |
|---    	    |---            |
|varchar(255)  	|varchar(1000)  |
|reciever_email |hello@hi.com   |
