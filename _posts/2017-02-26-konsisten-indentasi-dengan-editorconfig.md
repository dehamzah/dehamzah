---
layout: post
title: "Konsisten Indentasi dengan Editorconfig"
description: "Konsisten Indentasi dengan Editorconfig"
keywords: "editorconfig, konsisten indentasi"
date: 2017-02-26
categories: texteditor
author:     "dehamzah"
header-img: ""
tags:
    - Notes
    - Text Editor
---

Katanya menulis software itu harus rapih dan konsisten. Mengerjakan satu proyek dengan kolaborasi banyak orang, hasilnya harus tetap seperti satu orang yang menulis. Hal sederhana yang sering kali diperhatikan adalah indentasi, tentukan untuk menggunakan indentasi dengan tab atau spasi, panjang tab 2 atau 4.

Setelah menentukan beberapa aturan, kita harus berpegang pada aturan tersebut, dan mungkin akan ada kesalahan jika dilakukan manual, seperti tercampurnya soft tab (spasi) dan hard tab (real tab).


## Editorconfig

Kenalkan [editorconfig](http://editorconfig.org/). Editorconfig ini hanya sebuah file bernama `.editorconfig` berisi aturan-aturan penulisan yang harus di ikuti. File `.editorconfig` ini akan dibaca oleh text editor kita dan akan menyesuaikan sesuai dengan aturan penulisan yang yang ada di dalam file ini.

### Contoh konfigurasi

```
# top-most EditorConfig file
root = true

[*]
charset = utf-8
indent_style = space
indent_size = 2
```

File ini disimpan di root folder proyek kita dengan nama `.editorconfig`, dan text editor kita akan menyesuaikan sesuai dengan aturan yang telah tertulis di file ini.

### Instalasi

Tentunya, diperlukan plugin tambahan bagi text editor kita untuk bisa membaca konfigurasi tersebut.
Silahkan lihat apakah text editor Anda sudah tersedia plugin editorconfig atau belum di tautan [http://editorconfig.org/#download](http://editorconfig.org/#download).

Jika tersedia, silahkan install sesuai dengan petunjuk yang disediakan pada plugin tersebut.

### Fixing Indentation

Bagaimana jika kode saya sudah terlanjur tidak konsisten dalam indentasi dan saya ingin memperbaikinya?

Jika kalian menggunakan text editor atom, di plugin editorconfig sebenarnya sudah ada fitur fix configuration, tetapi setelah saya coba, tidak berefek.

Setelah saya coba cari aternatif, saya menemukan plugin atom lain yang bisa melakukan tugas fixing indentation, yaitu [auto-indent](https://atom.io/packages/auto-indent).

Kalian bisa menginstall plugin tersebut dengan cara :

```
$ apm install auto-indent
```

Setelah itu kita bisa membenarkan indentasi dari file yang sedang dibuka dengan cara :

Tekan `cmd + shift + p` / `ctrl + shift + p` dan ketik `Auto Indent: Apply`

Tadaa, sekarang indentasi kita sudah benar sesuai dengan yang tertulis di editorconfig.


#### Tips

Di text editor atom, ada opsi `Show Indent Guide` dan `Show Invisibles`. Saya sarankan untuk meng-enable opsi ini untuk melihat perbedaan antara soft tab dan hard tab di text editor atom.

Caranya, klik menu Atom / File -> Preferences -> Editor dan ceklis opsi `Show Indent Guide` dan `Show Invisibles`.
