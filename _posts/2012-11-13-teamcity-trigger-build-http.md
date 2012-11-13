---
layout: blog_entry
title: "Teamcity: trigger build with http request"
---

Teamcity: trigger build with http request
===========================================
It is very usefull to link teamcity build with github repositories from the repository side. Example, we have
a job which should be ran after a commit into repository.

There is a possibility to do it with the help of functionality described in this
[manual](http://confluence.jetbrains.net/display/TCD4/Accessing+Server+by+HTTP#AccessingServerbyHTTP-TriggeringaBuildFromScript)

In my case it looked like this

    http://admin:qwer1234@teamcity.jetbrains.com/httpAuth/action.html?add2Queue=bt21

Where `bt21` is a build id