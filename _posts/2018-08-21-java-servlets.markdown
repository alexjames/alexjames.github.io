---
layout: default
title:  "Java Servlets"
date:   2018-08-21 20:56:00
categories: excursions
---

A simple web server is just a process that is running on a remote machine with an open socket, listening in on
incomming requests and serving responses to those. If this type of content you get back changes based on the
sort of request, we say that the application is a web application. For instance, based on your request, you 
may get back an image or a webpage or have the content change. Most web pages served through popular websites
on the internet such as news, social networking and media-hosting websites tend to be dynamic.

CGI (Common Gateway Interface) is one way of having processes generate and serve dynamic content. The idea is
that the webserver will execute a script writen in PERL, Python, PHP, etc, which contains all the logic. This
can be implemented in many ways, but is hard to do optimally since you typically run a separate process to execute
the script and then serve back the result of the script. Java Servlets provide a powerful way to create webapps. 
They run on Java, thus having access to all of Java's libraries and its inherent platform independence. They also
run in the address space of the webserver, thus providing better performance. Servlets are built to be secure.



References:

[1] https://www.studytonight.com/servlet/how-a-servlet-application-work.php

[2] https://www.tutorialspoint.com/servlets/

[3] https://docs.oracle.com/javaee/6/tutorial/doc/bnadp.html
