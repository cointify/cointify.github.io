---
layout:     post
title:      Protocol switch behind proxy
date:       2015-10-26 12:00:00
summary:    Unable to download atom.io package behind corporate proxy
categories: solution
---

I had a need to install atom package inside [Atom.io](https://atom.io) editor but every time I tried it failed. I was behind a proxy. Initially I thought there was a network issue but couldn't figure out what exactly. When a given package download fails it outputs a message at the top. Looking at the message carefully I realized the URL (hosted at Amazon AWS) didn't have `HTTPS` anymore and had made a switch to `HTTP` (from `HTTPS`). I've run into this problem before at work so I knew it was a proxy problem as proxies don't allow such a switch. But since I could not make any configuration change to the proxy I had to Google for alternatives. Luckily, the issue was discussed at Github on Atom.io account. The solution is to set the below environmental variable (example for `Fish` shell):

{% highlight ruby %}
set -g -x  ATOM_NODE_URL "http://gh-contractor-zcbenz.s3.amazonaws.com/atom-shell/dist"
{% endhighlight %}
