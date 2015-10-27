---
layout:     post
title:      Software Architecture
date:       2015-10-25 12:00:00
summary:    Reading Software Architecture by Martin Fowler, Simon Brown, and Sam Newman
categories: architecture
---

I started reading on Software Architecture this weekend and went through a variety of different books, articles and blog posts. I decided to pursue  resources by Martin Fowler, Simon Brown, and Sam Newman.

The very first book I read was by Simon Brown [The Art of Visualizing Software Architecture](https://leanpub.com/visualising-software-architecture/) where he discusses his C4 model. It's a software architecture model that simplifies communication and visualization of software architecture at different levels and by far the simplest I've come across. The model is comprised of Context, Containers, Components, and Classes in this respective order. The first "C" (Context) in this model communicates information at high level but sets a clear picture. And as we go through the remaining C's we zoom in at each level. We start with a zoomed out version and zoom in as go further into Containers, Components, and Classes.

I've also started reading on Microservices a term well defined by Martin Fowler in his [blog article](http://martinfowler.com/articles/microservices.html) and Sam Newman in his book called [Building Microservices](http://shop.oreilly.com/product/0636920033158.do). The idea behind Microservices is to break down a monolithic software system into scalable and autonomous services. In a monolithic software system the communication is enabled through method invocation or function call. In Microservices the communication is enabled through a REST API or RPC. As you can see it's a change in communication pattern. The authors do reveal that it's not a silver bullet and the architectural approach does have its pros and cons.
