# Why?

After many years working in software engineering & technical operations, I've seen lots of ways to fail. When you're lucky, these get fixed by technical guardrails that prevent it ever being possible again anywhere in the world. Unfortunately, that happens almost never. The next best is that your company automation systems help prevent it. This is great until you leave and work somewhere else that doesn't have those guardrails and you've become so used to the automation that you never even knew the safety you had. So, with the high hopes of helping others learn from past mistakes, this repository was created. 

## How to use

The general goal is that guidance is grouped together under high level categories. 

# Databases

## Connecting to your production database

> Try as hard as possible to never connect to your production database (i.e. as you at your terminal). 

This exposes you to significant unnecessary risk of typos, unintentional changes, or unintentional load on the server.  If you must connect, then in decreasing order of preference,

1. Connect to a readonly slave
1. Connect through an automated system that limits your queries and permissions
1. Connect as a READONLY user

> When using MySQL, do not use "auto-rehashing". 

This can incur a _significant_ load on your database server. 

```bash
# Use this flag when connecting
mysql -A

# Better, set this in your my.cnf
no-auto-rehash
```
