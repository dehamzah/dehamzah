---
layout: post
title: Serve Your Custom Domain Github Pages with HTTPS
date:   2016-07-02
categories: web
author:     "dehamzah"
header-img: ""
tags:
    - Github
---


As per [9 June 2016](https://github.com/blog/2186-https-for-github-pages), github giving their user using github pages with free https domain *.github.io. But this free https doesn't support with custom domain.

So i googled for awhile to find out is there is some trick to make my custom domain github pages became https.

The result is, there is.

We will be using cloudflare to serve our website as [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy).
Basicly, our visitor of our websites will be redirected to cloudflare first then to our github pages server.


<img src="/public/flexible-ssl.png" alt="flexible-ssl">


## Requirements
1. Github pages with preconfigured custom domain
2. Cloudflare account

## Steps

##### 1. Add your websites to cloudflare and choose free plan.
Follow the instructions as instructed. Things to notes is, when in the steps crypto, choose __Flexible SSL__. (This process may take effects after a couple of hours).


##### 2. Then add rules to your domain to force redirect http access to https
By choosing __Page Rules__ on top menu. Click __Create Page Rules__ and follow this configuration.

<img src="/public/page-rule.png" alt="page-rule">


##### 3. Make sure all assets like css, and js in your github pages now serving as https.

```
<!-- change this -->
<link rel="stylesheet" href="http://yoursite.com/path/to/styles.css">

<!-- to this: -->
<link rel="stylesheet" href="//yoursite.com/path/to/styles.css">`
```


##### 4. Let search engine knows.
Modify your `_config.yml` to use https :

```
url: https://yoursite.com   # with the https protocol
enforce_ssl: yoursite.com   # without any protocol
```

And add this canonical url to your head :

```
<link rel="canonical" href="{{ "{{ site.url "}}}}{{ "{{ page.url "}}}}" />
```

This way, there will be no trace of your http website anywhere on the internet even though it works.


#### Done.

That's it. After a couple of hours your site will be serving as https. Just comment if you have some issues.
