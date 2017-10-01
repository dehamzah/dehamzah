---
layout: post
title: "Merubah Lokasi Screenshots Mac OS"
date: 2017-10-01
categories: "random"
author:     "dehamzah"
header-img: "public/macos_sierra_stock.jpg"
tags:
    - Notes
---

Desktop saya sudah mulai sesak dengan file-file temporary. Salah satu yang paling banyak adalah file screenshots.

Jadi saya perlu merubah lokasi screenshots default Mac OS.

Tinggal jalankan perintah ini di terminal, dan sekarang lokasi default screenshotmu sudah berubah.

```
$ defaults write com.apple.screencapture location <LOKASI-BARU>
$ killall SystemUIServer
```

Ganti <LOKASI-BARU> dengan lokasi screenshots baru yang diinginkan.

