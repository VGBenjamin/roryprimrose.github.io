---
title: Visual Studio for Database Professionals
date: 2006-09-24 23:11:00 +10:00
---

I am working on a personal project that I have wanted to do for quite a while. The project requires a database and I have been putting this part of the system together tonight. I remembered reading about the new edition of [Visual Studio for Database Professionals][0] that was blogged about the other month. I have decided to give this a run because I would like a full Visual Studio development experience as much as possible.

There are two major things that I would like to get out of this new project model. Firstly, version control for database objects. I will get the project onto CodePlex sometime soon so that should be a good test of its version control capabilities. Secondly, a good deployment (including upgrade) model. 

<!--more-->

Deployment is going to be the really interesting thing for me. How is a database project going to be built/deployed and how will the new project model cater for updating a live database to a new version. 

Within a couple of minutes of creating my database project, I imported an existing script. I was really impressed with this. The script I had was a script that created tables, constraints, relationships and triggers. The import wizard did a really good job of splitting the single script into separate database objects for the project. All is not smooth sailing though. 

Already, the latest CTP has halted my machine a couple of times. Adding a table to the project and then viewing Solution Explorer was the latest culprit. But hey, that's what you get for playing with the CTP's. A couple of other minor issues that I have found so far are that trigger files are not related to the table in the Schema View window and you can't right click multiple files in Solution Explorer to get a context menu (I was trying to include multiple files after one of the aforementioned halts).

[0]: http://msdn.microsoft.com/vstudio/teamsystem/products/dbpro/
