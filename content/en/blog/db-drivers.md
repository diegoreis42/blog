+++
title = 'Database Drivers'
date = 2024-06-05T23:05:53-03:00
author = 'Diego Reis'
tags = [
    "databases",
    "databases drivers",   
]
+++


One of the main purposes of a typical back-end API is to be a wrapper of the database. Sure,
it also handles business logic, sends e-mails, calls others APIs and so on, but at some point
it needs to be able to talk with a database. This post is about this talk.

Given that is a so important and common task, a lot of abstractions have been made to make this 
interaction easier, but abstractions have a cost, at some point it leaks [1](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/) 
and you'll be forced to go some levels deeper.

> "Abstractions save us time working, but they don’t save us time learning."

I'll try to give you glimpse about the interaction between the server and 
the database, from drivers to ORMs. Given that you, the reader, probably know some Javascript and
some Postgres, I'll use the great [node-postgres](https://github.com/brianc/node-postgres) library
throughout this post to exemplify some concepts.


Databases typically, but not always[2](https://www.sqlite.org/)[3](https://github.com/tursodatabase/limbo/),
runs _solo_ in its own machine and interacts with the external world as a server, using its own protocol[4](https://dev.mysql.com/doc/dev/mysql-server/latest/PAGE_PROTOCOL.html) over TCP/IP. So clients, our backend API, must have a way to interact with
it considering the correct protocol, the guy who abstract this is called: **database driver**.  


#### Disclamer

If you're already familiar with computer terminology you probably asked yourself: "Why databases drivers
are called drivers?" That's a good question, at the end of the day, database drivers are just
clients of a server (the database) _driver_ is a common term used by OS guys to name a 
program that **translate specific** hardware **twerks in a common API**. Indeed, if you take a look
on Postgres protocol documentation[1](https://www.postgresql.org/docs/current/protocol-overview.html), you
will understand why it is called a driver.





