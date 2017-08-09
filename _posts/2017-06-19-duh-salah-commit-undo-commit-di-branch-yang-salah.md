---
layout: post
title: "Duh, salah commit - Undo commit di branch yang salah"
description: "Undo commit di branch yang salah"
keywords: "git, salah commit"
date: 2017-06-19
categories: git
author:     "dehamzah"
header-img: ""
tags:
    - Git
    - Notes
---

Jika kalian pernah bekerja dengan git untuk menulis software, biasanya kalian akan punya beberapa branch. Saya sempat menulis di branch yang salah, dan sudah terlanjur di commit, tapi belum di push.

Googling-googling sebentar, ternyata caranya cukup mudah.

Kita tinggal melakukan soft reset 1 langkah ke belakang dengan cara ini: 

```bash
$ git reset --soft HEAD^
```

perintah ini akan mengeluarkan commitan terakhir dan menaruhnya di index, jadi kita tinggal pindah branch, dan melakukan commit di branch yang seharusnya.

