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

## Do not delete columns / tables / etc. lightly

Migrating your database schema in general is no light matter. 

1. Adding or updating a column can bring your application to a halt if the table is very large
1. Adding a column before you've fully fleshed out the design can incur risky rename or type alteration costs

_Deleting_ a column is almost always a risky change. Don't forget that _renaming_ or _updating_ a column is akin to deleting because your *code* won't necessarily know the column was renamed / changed. 

If you're deleting a column, it's good practice to create a migration plan and get approval from senior leaders in your engineering & ops team. 


# Temporary?

Almost nothing ends up being temporary. Many more times than not, the hacks or fixes to temporarily punt a problem down the road end up sticking around for much longer than intended. Is this a problem? Not necessarily. Problems will get fixed correctly when their time comes; but the important takeaway from this is that method taken to implement a temporary fix and the supporting documentation around it (wiki, emails, communication, etc.) should be treated seriously. Their absence will otherwise most surely come back to bite you!

