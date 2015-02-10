---
layout:     post
title:      Dockerized my dev environment
date:       2015-02-08 12:00:00
summary:    Used docker to create an image of CentOS 7 + JBOSS EAP 6.3 + PostgreSQL
categories: development
---

Few days ago I stumbled upon Docker on Hacker News and wanted to give it a try. So, over the weekend I read few tutorials and docker's documentation
and built sample images. Though learning curve is a bit steep but I managed to overcome it. I was really interested in creating an image(s) that I would
be able to use for my development environmnet. I came up with the following image design - CentOS 7 + JBOSS EAP 6.3 + Oracle Java 8 + PostgreSQL 9.3.

I've never worked with NGINX before so it was a bit challenging for me at first but then it all made sense after I read the official documentation. And below
are some of the steps I took to set-up everything:

* Start JBOSS Server 1 (make sure to give it a name which we'll later use to link with NGINX);
* Start JBOSS Server 2 (make sure to give it a name which we'll later use to link with NGINX);
* Use docker's `inspect` command to check IP Addresses of Both JBOSS servers;
* Enter both IP Addresses in the `upstream` block of `nginx.conf` file as shown below;
* Start NGINX and link both JBOSS Servers using their names;
* Done! Visit browser to test.
