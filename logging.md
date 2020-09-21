

# 1. The basics
## 1.1. Why Logs?
Logs are a way to log what's going on in our application. Logs show up in the console or in log files on disk. See history of the term.


## 1.2. Logging Levels

### ERROR

Something troubling has happened that will break something else. This almost always precedes an exception or an end to execution

### WARN

Warning is often used for handled 'exceptions' or other important log events. For example, if your application requires a configuration setting but has a default in case the setting is missing, then the Warning level should be used to log the missing configuration setting.

### INFO

Output information that is useful to the running and management of your system. Information would also be the level used to log Entry and Exit points in key areas of your application. However, you may choose to add more entry and exit points at Debug level for more granularity during development and testing.

### DEBUG

Debug is considered out-of-bounds for a production system and used it only for development and testing. I prefer to aim to get my logging levels just right so I have just enough information and endeavour to log this at the Information level or above.


## 1.3. How to write a useful log message

### 1.3.1 SMART
All log messages should be:

Specific -- easy to pinpoint where

Meaningful -- provide discerning information to identify what's wrong & some context

Actionable -- provide information with which to attempt to fix the problem or further debug / recreate

Relevant -- provide information pertinent to the situation, not redundant or superfluous

Terse -- Get to the point and be clear about it

# 2. Best practices

## 2.1. Hot loops
Be thoughtful about putting log >DEBUG statements in any loop. If the loop length can grow to extreme sizes, you run the risk of eating up all the disk on your machine or paying lots of money in logging bills.

## 2.2. Disk out of space
Caught an exception and want to log it? What if your exception is that there is no space left on the disk? If you are writing your logs to disk, this introduces a paradox. 
