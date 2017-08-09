---
layout: post
title: "Belajar Python: Project Take a Break"
description: "Di minggu ini saya mau mencoba mendalami python, setelah googling sana sini, akhirnya saya memutuskan untuk mencoba belajar lewat kursus Udacity Programming Foundation with Python"
keywords: "python, belajar python, project take a break"
date: 2016-08-29
categories: python
author:     "dehamzah"
header-img: ""
tags:
    - Python
    - Learning
---

Di minggu ini saya mau mencoba mendalami python, setelah googling sana sini, akhirnya saya memutuskan untuk mencoba belajar lewat kursus [Udacity Programming Foundation with Python](https://www.udacity.com/course/programming-foundations-with-python--ud036). Beberapa project dan konsep yang saya pelajari akan saya coba tulis di blog ini agar saya lebih paham, dan juga sekalian itung-itung latihan menulis.

Di udacity kita belajar by doing projects, projects pertama adalah Project Take a Break. Program ini akan mengingatkan kita (yang sering main komputer lama-lama) agar keluar dari tempat duduk. Setiap beberapa jam sekali, program akan membuka browser dan membuka youtube video.

Step pertama sebelum nyentuh kode, kita definisikan terlebih dahulu pseudo code nya :

1. Beritahu program untuk menunggu selama 2 jam.
2. Buka browser dan buka youtube.
3. Ulangi.

Kodenya nanti akan seperti ini (akan saya mention di bawah beberapa poin pentingnya) :

{% gist 64cce4c2a61d9342a6c51f8e2b2d6cff %}

Apa yang saya pelajari :

- Pada line 1, itu adalah magic syntax environment mac untuk memberitahu bash ini adalah kode program python. Jadi file ini bisa langsung di panggil dengan cara `./take_a_break.py` (tentu setelah di `chmod +x` ya filenya) tidak perlu lagi `python take_a_break.py`
- Di python ada namanya standard library, standard library akan otomatis tersedia ketika kita menginstall python. Tapi ketika kita ingin menggunakannya kita harus import library yang kita inginkan terlebih dahulu. Daftar standard library apa aja yang ada, bisa di lihat pada dokumentasi [https://docs.python.org/2/library/](https://docs.python.org/2/library/). Contoh penggunaannya ada pada line 3 dan 17 ketika kita ingin menggunakan library webbrowser untuk membuka url.
- Konsep `while loops` [https://learnpythonthehardway.org/book/ex33.html](https://learnpythonthehardway.org/book/ex33.html)
- Rangkuman sintaks pada python [https://learnxinyminutes.com/docs/python/](https://learnxinyminutes.com/docs/python/)







