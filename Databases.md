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

## Long Running Processes That Use the Database

A database server will typically only hold open a client connection for a fixed amount of time. 

In the case of long-running processes (which can include a web server that doesn't get much traffic overnight), the client's connection may be terminated by the server unbeknownst to the client. The impact is that when the client next attempts to communicate with the database, an exception is raised. 

If you're lucky, your client SDK code addresses this for you; but if you're not so lucky, then your best bet is to close and reestablish the connection automatically at relevant stages of your code or script. 


