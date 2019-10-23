---
title: Does adding a non-null default column cause downtime in MySQL 5.7?
date: '2019-10-22'
tags:
  - daily
  - mysql
  - infrastructure
---

# Overview
We wanted to add a boolean column to an existing table to represent suppressing an entry for the UI and other downstream consumers to filter on. Since we wanted the column to default as `FALSE` and be non-`null`, I wanted to double check and see if it would cause downtime - locking and preventing reads and/or writes on the table.

I found that on MySQL 5.7, adding a column (for the most part) would not cause downtime and you can enforce zero-downtime by adding `ALGORITHM=INPLACE, LOCK=NONE` to your SQL statement.

## Details
Searching for the answer took a while to be honest. Database questions in particular can be very nuanced since database engines, like MySQL, Postgres and Oracle, have difference features and handle cases differently. So when you search for more complex questions, adding the name of the engine, the version of your engine and the storage engine used is very helpful.

In this case, searching for `does adding a column with default cause lock mysql` was sufficient to give a good first [result](https://stackoverflow.com/questions/35424543/alter-table-without-locking-the-entire-table).

Adding `does adding a column with default cause lock mysql 5.7` led to the [official docs](https://dev.mysql.com/doc/refman/5.7/en/innodb-online-ddl-operations.html).

I find Stack Overflow questions helpful when they reference the same DB versions and point to the offical documentation. MySQL official documentation can be intimidating but they're very detailed and digestible if given enough additional googling.

For example, what does `Online DDL Operations` mean?

After googling DDL, it stands for Data Definition Language and are the commands used to change the DB like `CREATE DATABASE` and `ALTER TABLE`. Reading the docs, being online can be thought of as allowing read and writes when the action is being performed.

So if there and words or phrases that are unfamiliar, give yourself some time and determination. You got it.

Back to adding the non-null column, the docs provide this example but give context on what `ALGORITHM` and `LOCK` mean.
```sql
ALTER TABLE tbl_name ADD COLUMN column_name column_definition, ALGORITHM=INPLACE, LOCK=NONE;
```

Again, googling for `algorithm mysql 5.7` points me [here](https://dev.mysql.com/doc/refman/5.7/en/alter-table.html) and searching for `algorithm` point us to [this](https://dev.mysql.com/doc/refman/5.7/en/alter-table.html#alter-table-performance):

> ALTER TABLE operations are processed using one of the following algorithms:

> COPY: Operations are performed on a copy of the original table, and table data is copied from the original table to the new table row by row. Concurrent DML is not permitted.

> INPLACE: Operations avoid copying table data but may rebuild the table in place. An exclusive metadata lock on the table may be taken briefly during preparation and execution phases of the operation. Typically, concurrent DML is supported. 

and searching for lock points us [here](https://dev.mysql.com/doc/refman/5.7/en/alter-table.html#alter-table-concurrency):

> For ALTER TABLE operations that support it, you can use the LOCK clause to control the level of concurrent reads and writes on a table while it is being altered. Specifying a non-default value for this clause enables you to require a certain amount of concurrent access or exclusivity during the alter operation, and halts the operation if the requested degree of locking is not available.

This is great since we can provide the `LOCK` at the level we want (DEFAULT, NONE, SHARED, or EXCLUSIVE) and test the command locally and in lower environments.

## Potential Future Topics
- Software versions and semantic versioning

## Meta
I'll be posting more short-form posts on interesting things I learn and obeserve. If there's anything you'd like for me to write about, send me a msg on Twitter [@lamroger](https://twitter.com/lamroger)!
