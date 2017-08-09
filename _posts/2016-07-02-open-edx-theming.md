---
layout: post
title: Open edX Theming dengan Stanford Theming
subtitle: "Open edX, Open edX Theming, Open edX Stanford Style"
date:   2016-07-02
categories: openedx
author:     "dehamzah"
header-img: ""
tags:
    - Open edX
    - Theming
---

Ada beberapa metode untuk melakukan custom theming di open edx. Salah satu yang paling mudah menurut saya adalah 'Stanford Theming'. 
Cara yang mau saya share disini adalah cara manual, dengan melakukan recompile assetsnya saja. Dan menurut [wiki](https://github.com/edx/edx-platform/wiki/Stanford-Theming), metode stanford ini hanya bisa untuk modifikasi LMS nya saja.

Langsung saja kita ke tahapannya :

1. Buat folder baru dengan `<nama-tema>` kamu di `/edx/app/edxapp/themes/`.  
2. Isi theme kamu dengan struktur file seperti ini,  
{% highlight ruby %}
```
      ├── [nama-tema]                      
      |   |   └── static                   
      |   |   |   └── css
      |   |   |   └── images
      |   |   |   └── js
      |   |   |   └── sass
      |   |   |       └── _<nama-tema.scss>  // nama ini harus sama dengan nama folder tema kamu diawali _. (wajib ada)
      |   |   |   └── vendor
      |   |   |   └── vendor-extensions
      |   |   └── templates                // tempat overriding template files openedx.
      |   |       └── theme-head-extra.html         // (wajib ada)
      |   |       └── theme-header.html             // (wajib ada)
      |   |       └── theme-footer.html             // (wajib ada)
      |   |       └── theme-google-analytics.html   // (wajib ada)  
```
{% endhighlight %}

3. Edit file `/edx/app/edxapp/lms.env.json`, lalu rubah variabel ini:  
    ```
    USE_CUSTOM_THEME: false   // dirubah menjadi `true`
    THEME_NAME: ""            // dirubah menjadi `"<nama-tema>"`
    ```

4. Setelah itu, kita recompile static assets nya dengan melakukan perintah ini:  
    ```
    sudo -H -u edxapp bash
    source /edx/app/edxapp/edxapp_env
    cd /edx/app/edxapp/edx-platform
    paver update_assets lms --settings=aws --debug
    ```

5. Lalu restart LMS nya :  
    `sudo /edx/bin/supervisorctl restart edxapp:lms`
    

Selesai. Selamat mencoba.


sumber: [Stanford Theming](https://github.com/edx/edx-platform/wiki/Stanford-Theming)
