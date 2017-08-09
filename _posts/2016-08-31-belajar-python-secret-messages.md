---
layout: post
title: "Belajar Python: secret_messages.py"
description: "Project kali ini tentang pengurai pesan rahasia. Diberikan kumpulan gambar-gambar berisi huruf yang harus kita susun agar terbentuk sebuah kalimat."
keywords: "belajar python"
date: 2016-08-31
categories: python
author:     "dehamzah"
header-img: ""
tags:
    - Python
    - Learning
---

Project kali ini tentang pengurai pesan rahasia. Diberikan kumpulan gambar-gambar berisi huruf yang harus kita susun agar terbentuk sebuah kalimat. Gambar-gambar ini mempunyai nama file huruf dan angka yang acak. Tugas kita adalah menghapus setiap angka yang terdapat pada nama file tersebut.

Hal ini dapat dilakukan python dengan mudah. Berikut ini kode programnya.

{% gist 70c3356399493597a10e9fb60b154fa7 %}

Cobalah dengan mengunduh pesan rahasia ini:

[Pesan Rahasia](https://dl.dropboxusercontent.com/u/62189606/secret-messages.zip)

Ubah variabel `target_dir` dengan lokasi folder gambar yang telah terunduh, dan coba jalankan script tersebut.

Apa yang saya pelajari?

- Gunanya rawpack string pada python. [Read more](http://stackoverflow.com/questions/2081640/what-exactly-do-u-and-r-string-flags-do-in-python-and-what-are-raw-string-l)
- Melakukan perintah yang berhubungan dengan sistem operasi menggunakan module os. [Read more](https://docs.python.org/2/library/os.html)
- Jika ingin melakukan rename files, jangan lupa untuk pindah ke direktori dimana file tersebut berada.