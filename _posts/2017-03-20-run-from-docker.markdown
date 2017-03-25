---
layout: post
title:  "Run Jekyll from Docker!"
date:   2017-03-20 13:29:59 +0000
categories: jekyll docker
author: anupvarghese
---
You are in this page because you like Docker. I like docker because it's an easy solution to keep everything in a container and not to make your local environment messy. So, I was wondering how to run `jekyll` from docker. After spending some time on the jekyll build process I was able to do it properly. Here is the `docker-compose.yml` to do the magic

{% highlight yaml %}
version: '2'

services:
  jekyll:
    image: jekyll/jekyll:pages
    command: jekyll serve --port=4004
    ports:
      - 4004:4004
    volumes:
      - .:/srv/jekyll
{% endhighlight %}

Pretty simple right?

If you like to initialize a new site, just run the below command

`docker-compose run jekyll jekyll . --force`

Then run `docker-compose up jekyll`

Go to `http://localhost:4004` to see the static site


