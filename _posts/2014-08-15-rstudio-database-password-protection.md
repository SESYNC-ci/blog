---
layout: post
title:  "Database Password Protection in R	"
date:   2014-08-07 14:06:14
categories: database
author: msmorul
---


A nice tip Ian found to prompt for a database password when connecting:

    Require(RMySQL)
    con = dbConnect("MySQL", user='username', 
        password=.rs.askForPassword("Enter password:"), 
        dbname='database_name', 
        host='database.host.org')

You don't want to do something like password <- .rs.askForPassword("Enter password:") as this will store your password in memory. Not the worst solution, but not the best either.

Why don't you want to store your password directly in code? Simple, if you track your code in git or another version control software, its too easy to accidentally push your code public with the password in it. (Yikes!). Even if you remove it from your current version, your commit history likely still contains it.
