---
layout:     post
title:      Dockerized my dev environment
date:       2015-02-08 12:00:00
summary:    Used docker to create an image of CentOS 7 + JBOSS EAP 6.3 + PostgreSQL
categories: development
---

Few days ago I stumbled upon [Docker](https://www.docker.com/) on Hacker News and wanted to give it a try. So over the weekend I read few tutorials and docker's documentation
and built sample images. Though the learning curve is a bit steep but I managed to overcome it. I was really interested in creating an image(s) that I would
be able to use for my development environmnet. I came up with the following image design - CentOS 7 + JBOSS EAP 6.3 + Oracle Java 8 + PostgreSQL 9.3.

Source code avilable on [cointify/docker](https://github.com/cointify/docker) repository on [Github.com](https://github.com)

I've never worked with [NGINX](http://nginx.org) before so it was a bit challenging at first but then it all made sense after I read through the official documentation. And below
are some of the steps I took to set-up everything:

* Start JBOSS Server 1 (make sure to give it a name which we'll later use to link with NGINX);
* Start JBOSS Server 2 (make sure to give it a name which we'll later use to link with NGINX);
* Use docker's `inspect` command to check IP Addresses of both JBOSS servers;
* Enter both IP Addresses in the `upstream` block of `nginx.conf` file as shown below;
* Start NGINX and link both JBOSS Servers using their names;
* Done! Visit browser to test.

### Start JBOSS Servers
Replace `$1` with server name like `jboss1:jboss1` or `jboss2:jboss2`

{% highlight ruby %}
docker run -it --name $1 cointify/jboss630:latest
{% endhighlight %}

### Check IP Address of your JBOSS Server

{% highlight ruby %}
docker inspect CONTAINER_ID
{% endhighlight %}

### Nginx.conf

{% highlight ruby %}
upstream myapp1 {
    server IP_OF_JBOSS_SERVER_1:8080;
    server IP_OF_JBOSS_SERVER_2:8080;
}

server {
    listen 80;

    location / {
        proxy_pass http://myapp1;
    }
}
{% endhighlight %}


