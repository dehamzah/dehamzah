---
layout: post
title: "Pip dan Virtualenv di Python"
description: "Pip dan Virtualenv merupakan tools wajib yang perlu diketahui jika ingin memulai ngoding di python."
keywords: "pip, virtualenv, python"
date:   2016-11-21
categories: web
author:     "dehamzah"
header-img: ""
tags:
    - Python
    - Learning
---

Python mempunyai packaging ecosystem sendiri seperti halnya bahasa pemrograman lain seperti nodejs, ruby, dan lainnya. Pip dan Virtualenv ini merupakan tools wajib yang perlu diketahui jika ingin memulai ngoding di python.

### `pip`

Pip merupakan tool untuk menginstall python packages dari [Python Package Index](http://pypi.python.org/). Tool ini secara default sudah terinstall ketika kalian menginstall python. Atau jika belum, kalian bisa meng-installnya dengan perintah berikut :

```
$ sudo easy_install pip
```

Pip ini akan memudahkan kalian untuk meng-install dependencies yang dibutuhkan untuk membuat project python. Misalnya, ketika kalian ingin memulai project django, kalian perlu meng-install django-nya terlebih dahulu. Seperti ini :

```
# Tidak perlu melakukan ini
$ sudo pip install django
```

Python akan menginstall package `django` secara global pada sistem. Tapi ini tidak di rekomendasikan. Kenapa?

Sebagai developer, kemungkinan besar kita akan mempunyai lebih dari satu project lokal di komputer, dan tentunya setiap project akan memiliki dependencies yang berbeda-beda pula. Akan sangat mungkin di project yang satu kita membutuhkan `django 1.7` dan di project lainnya membutuhkan `django 1.10`. Jika kita meng-install django secara global, tentunya kita hanya akan bisa menggunakan satu versi django saja.


### `virtualenv`

Disinilah virtualenv berperan. Dengan virtualenv, memungkinkan kita untuk membuat 'lingkungan virtual', khusus untuk spesifik project kita. Kita bisa menambahkan dependencies apapun disini tanpa perlu khawatir bentrok dengan dependencies project lain.

Bagaimana cara memakai virtualenv?

Pertama kita harus meng-install terlebih dahulu package virtualenv secara global. Kalian bisa melakukannya dengan pip :

```
$ sudo pip install virtualenv 
```

Setelah itu, pindah ke folder project python kalian dan jalankan perintah berikut :

```
$ virtualenv venv
```

Perintah tersebut akan membuat 'lingkungan virtual' yang disimpan pada folder `venv`. Kalian bisa menggunakan nama lain selain `venv` tentunya, tapi dengan penamaan `venv` ini tentunya akan lebih semantic.

Selanjutnya, kita aktifkan 'lingkungan virtual' kita, sebelum mulai meng-install dependencies project python yang dibutuhkan. Caranya seperti ini :

```
$ source venv/bin/activate
```

Sekarang kalian telah berada di dalam 'lingkungan virtual',  yang ditandai dengan adanya tulisan `(venv)` di atas baris lokasi folder kalian di terminal.

Dengan adanya tanda `(venv)` kalian bisa meng-install dependencies apapun yang kalian butuhkan untuk spesifik project python kalian.

Kalian bisa melihat daftar dependencies apa saja yang telah kalian install dengan perintah berikut :

```
$ pip freeze
```

Lalu kalian bisa meng-eksport dependencies kalian kedalam satu file `requirements.txt` dengan perintah berikut :

```
$ pip freeze > requirements.txt
```

Jika kalian menggunakan versioning control seperti git, disarankan untuk tidak mem-push folder `venv` ke repositori. Kalian hanya perlu mem-push file `requirements.txt` nya saja, dan biarkan orang lain yang menginstall dependencies-nya melalui file tersebut seperti ini :

```
$ pip install -r requirements.txt
```

Oh iya, ada satu lagi yang lupa. Jika kalian ingin keluar dari 'lingkungan virtual' kalian. Kalian tinggal menjalankan perintah ini :

```
$ deactivate
```

Kesimpulannya, gunakanlah selalu 'lingkungan virtual' jika ingin memulai project python.

Semoga bermanfaat!



