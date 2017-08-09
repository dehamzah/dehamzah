---
layout: post
title: "Kenalan dengan Vagrant"
description: "Pengenalan dasar Vagrant untuk local development environment"
keywords: "vagrant, virtualbox, local development setup"
date: 2016-12-15
categories: web
author:     "dehamzah"
header-img: ""
tags:
    - Development Environment
    - Vagrant
---

Biasanya untuk develop aplikasi web seperti php, kita akan meng-install LAMPP/MAMPP yang sudah satu bundel siap untuk di gunakan di komputer/laptop kita, atau kita bisa menginstall manual satu-satu dependencies yang dibutuhkan. Sering kali kita mempunyai local environment yang berbeda dengan teman satu tim kita, atau bahkan berbeda juga dengan environment di server production. Hal ini terkadang kita abaikan selama masih 'bekerja'. Tetapi, jika sedang menangani project yang kompleks ataupun sedang mencoba-coba project open source yang besar, perbedaan environment bisa menimbulkan error yang tak dapat diduga.

Kenali 'Vagrant', dia adalah tool yang dapat membantu kita dalam mengkonfigurasi dan memproduksi portable virtual work environment diatas VirtualBox (default-nya akan menggunakan ini), VMWare ataupun provider lainnya. Pada dasarnya, kita akan bekerja di dalam virtual os diatas VirtualBox sehingga development environment kita akan terisolasi. Nah, Vagrant ini akan memudahkan kita untuk me-manage pembuatan dan konfigurasi si virtual os tersebut, ditambah lagi kemampuan-kempampuan lain yang dapat memudahkan di sisi deployment ke server. Hal ini dapat dengan mudah dilakukan melalui terminal dengan Vagrant.


### Instalasi

Unduh dan install VirtualBox + Extension Pack :

```
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
```
*Pastikan unduh versi yang stabil ya, jangan yang beta


Unduh dan install Vagrant :

```
[https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html)
```

Setelah selesai, cek versi Vagrant kita dengan mengetikkan ini di terminal :

```
$ vagrant -v		# akan keluar versi vagrant yang ter-install, misal: Vagrant 1.8.5
```
*Jika command tidak tersedia, coba tutup terminal yang ada, dan buka kembali.


### Vagrant Boxes

Pada Vagrant, box adalah sebuah format package untuk Vagrant environments. Untuk membuat environtment baru, kita akan mengunduh satu box ubuntu server 14.04 LTS 64bit dan akan memulainya pada path `~/sandboxes/ubuntu` :

```
$ mkdir -p ~/sandboxes/ubuntu		# buat direktori jika belum tersedia
$ cd ~/sandboxes/ubuntu				# pindah ke direktori tersebut
$ vagrant init ubuntu/trusty64		# inisiasi environment Vagrant dengan box ubuntu 14.04
```
*Untuk box-box lainnya, dapat dicari disini: [https://atlas.hashicorp.com/boxes/search](https://atlas.hashicorp.com/boxes/search)


### Starting up Vagrant Box

Untuk memulai box Vagrant kita, dapat dilakukan dengan perintah ini :

```
$ vagrant up
```

Setelah itu, kita dapat konek ke local development box kita dengan ssh :

```
$ vagrant ssh
```

Sekarang kita seharusnya sudah berada di dalam box ubuntu 14.04 kita. Disini kita bisa melakukan setup dan konfigurasi layaknya server di cloud.

<img src="/public/vagrant-in.png" alt="vagrant-in">

Untuk keluar dari server, bisa dilakukan dengan perintah `exit`, seperti melakukan ssh ke server saja.

Untuk melihat vagrant yang sedang berjalan, bisa dengan perintah :

```
$ vagrant status
```

Untuk mematikan komputer vagrant bisa dengan perintah :

```
$ vagrant halt
```

Untuk perintah-perintah cli vagrant lainnya bisa dilihat dengan perintah `vagrant -h` atau bisa di lihat di [dokumentasi resminya](https://www.vagrantup.com/docs/cli/).


#### Vagrant Configuration

Pengaturan-pengaturan dasar Vagrant telah di sediakan pada file `Vagrantfile` dalam bentuk komentar. Sehingga memudahkan untuk orang yang baru mengenal Vagrant. Konfigurasi ditulis di dalam block ini :

```
Vagrant.configure("2") do |config|
	.
	.
	.
end
```


#### Konfigurasi Akses IP Box Vagrant di Host Komputer

Konfigurasi ini dilakukan agar kita dapat mengakses ip komputer virtual kita.

```
config.vm.network "private_network", ip: "192.168.99.10"
```
IP bebas di ganti dengan IP yang diinginkan, saya sarankan untuk memberikan IP Private saja (192.168.0.0 - 192.168.255.255).


#### Setting shared folder

Konfigurasi ini berguna untuk dapat membuka file yang terdapat di dalam box vagrant, jadi kita tidak perlu berada di dalam vagrant box untuk merubah-rubah file.

```
config.vm.synced_folder "www", "/usr/share/nginx/html"
```

Parameter pertama adalah nama folder di komputer host kita, lokasinya relatif dengan dimana `Vagrantfile` berada. Parameter kedua adalah path absolut di vagrant box kita. Folder di komputer host kita harus dibuat terlebih dahulu, atau proses provisioning vagrant box kita akan gagal. Untuk folder yang di dalam vagrant box akan dibuatkan secara otomatis jika belum terbuat. Proses sinkronisasi akan terjadi dari komputer host ke vagrant box, jadi dalam kasus diatas, isi file yang terdapat di folder `/usr/share/nginx/html` akan kosong jika di komputer host kita isi folder `www`-nya kosong.


#### Setting Upstart Script ketika Provisioning Box

Dengan Vagrant kita bisa membuat script yang dapat otomatis di jalankan ketika server baru dibuat (provisioning). Misal kita ingin membuat web server sederhana dengan nginx. Kita mengkonfigurasi Vagrant untuk secara otomatis meng-install-kan nginx untuk kita pada saat `vagrant init`.

```
config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y nginx
   SHELL
```


#### Menerapkan konfigurasi

Untuk menerapkan konfigurasi pada vagrant yang sudah berjalan, bisa dilakukan dengan perintah ini : 

```
$ vagrant reload
```

Jika ingin me-reload konfigurasi disertai melakukan proses provisioning ulang, lakukan dengan perintah ini :

```
$ vagrant reload --provision
```


Nanti ketika ada teman satu tim yang ingin involve di dalam project, mereka tinggal di kasih `Vagrantfile`-nya saja, dan tinggal provision dengan `vagrant up`. Kita seperti memberikan satu komputer penuh kepada teman kita, sehingga bisa dipastikan environtment development kita sama persis. Hal ini bisa mengurangi bug "Doesn't work in another machine but works in my machine".

Next, kita akan kenalan dengan docker, mirip seperti vagrant tetapi lebih 'ringan'.




Cheers. 

Selamat mencoba!


---
Further reading : [https://www.vagrantup.com/docs](https://www.vagrantup.com/docs)

