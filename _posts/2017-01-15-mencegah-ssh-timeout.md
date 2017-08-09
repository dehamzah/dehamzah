---
layout: post
title: "Mencegah SSH Timeout"
description: "Cara mencegah ssh timeout"
keywords: "ssh timeout"
date: 2017-01-15
categories: server administration
author:     "dehamzah"
header-img: ""
tags:
    - Ops
    - Notes
---

Agak nyebelin memang, ketika lagi remote ssh, ditinggal sebentar, terus disconnect. Terminal hang, dan musti buka tab baru.

Supaya koneksi SSH ga terputus, bisa diakali dengan mengrimkan `null packet` ke server secara berkala selama kurang dari ssh value timeout.

Caranya mudah, tinggal edit ssh config-mu:

```
$ vim ~/.ssh/config
```

dan tambahkan baris berikut:

```
ServerAliveInterval 120
```

Ini akan mengirimkan `null packet` setiap 120 detik dari komputermu ke komputer server, agar koneksimu tetap `hidup`.
