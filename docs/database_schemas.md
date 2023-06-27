---
layout: default
title: Database Schemas
nav_order: 1
---

# Logs

## Logs

|id        	    |Time                       |Level          |Process        |Message                    |
|---        	|---                        |---            |---            |---                        |
|UUID         	|datetime                   |tinyInt (FK)   |text           |text                       |
|urterg 	    |2023-06-19 12:28:05.700    |1 (Info)       |Procesnavn1	|Dette er en besked bip bop |

## Log_Level

|id         |value 	  |
|---	    |---	  |
|0          |Trace    |
|1 	        |Info     |
|2          |Error    |

# Triggers

## Scheduled_Triggers

|id        	    |cron_expr      |last_run                   |next_run                  |process_path             |status            |is_git_repo |force_update|
|---        	|---            |---                        |---                       |---                      |---               |---         |---         |
|UUID         	|varchar(255)   |datetime                   |datetime                  |text                     |tinyInt (FK)      |bit         |bit         |
|kasdlkf 	    |'0 0 * * *'    |2023-06-19 00:00:00.000    |2023-06-20 00:00:00.000   |C:\processes\process1.py |1 (Running)       |True        |True        |

## Email_Triggers

|id        	    |email_folder   |last_run                   |process_path             |status            |is_git_repo |force_update|
|---        	|---            |---                        |---                      |---               |---         |---         |
|UUID         	|text           |datetime                   |text                     |tinyInt (FK)      |bit         |bit         |
|sadfsd	        |Inbox/AKBO     |2023-06-19 00:00:00.000    |C:\processes\process1.py |1 (Running)       |True        |True        |

## Single_Triggers

|id        	    |time                       |last_run                   |process_path             |status            |is_git_repo |force_update|
|---        	|---                        |---                        |---                      |---               |---         |---         |
|UUID         	|datetime                   |datetime                   |text                     |tinyInt (FK)      |bit         |bit         |
|jrthzc 	    |2023-06-30 12:30:00.000    |2023-06-19 00:00:00.000    |C:\processes\process1.py |3 (Done)          |True        |True        |

## Trigger_Status

|id     |value 	     |
|----   |---	     |
|0      |Idle     	 |
|1 	    |Running     |
|2      |Failed   	 |
|3      |Done   	 |

# Storage

## Credentials

|id        	    |username 	|password               	|
|---        	|---    	|---                    	|
|text         	|text     	|text (encrypted)        	|
|sap_login 	    |user123  	|DToN4CzwFYLy4930XgLLPA 	|

## Constants

|id        	    |value 	        |
|---    	    |---            |
|text         	|text     	    |
|reciever_email |hello@hi.com   |
