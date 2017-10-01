---
layout: post
title: "Show Homepage after user logged in in OpenEdx  "
date: 2017-10-01
categories: "openedx"
author:     "dehamzah"
header-img: "public/openedx.png"
tags:
    - Open edX
    - Notes
---

By default, after user login into LMS, user cannot see the homepage. They always redirected to their dashboard.

What if i want to set user can see the homepage, even after they are logged in?

This can be set in `lms.env.json`, by putting this config inside block `”FEATURES”` :

```
"ALWAYS_REDIRECT_HOMEPAGE_TO_DASHBOARD_FOR_AUTHENTICATED_USER": false
```

After that, restart your edxapp lms service to see the changes, by calling : 

```
$ sudo /edx/bin/supervisorctl edxapp:lms restart
```

Thats it. Now you can see the homepage after user logged in.