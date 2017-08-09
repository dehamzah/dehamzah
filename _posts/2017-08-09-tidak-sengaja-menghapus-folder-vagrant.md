---
layout: post
title: "Tidak sengaja menghapus folder `.vagrant`"
date: 2017-08-09
categories: ops
author:     "dehamzah"
header-img: "public/bg-post-hapus-vagrant.jpeg"
tags:
    - Vagrant
    - Notes
---

Ketika saya sedang mencoba menginstall openedx devstack ginkgo, proses instalasinya sering mengalami kegagalan, dan secara tidak sengaja menghapus folder `.vagrant` di openedx devstack ficus saya.   Awalnya saya panik, karena harus mengulang proses instalasi yang begitu memakan waktu dan bandwidth untuk si ficus yang saya hapus.   Tetapi ternyata file yang terdelete itu hanya file konfigurasi vagrant yang mengarahkan akan menjalankan VM yang mana, tidak menghapus VM nya. Hal ini bisa dicek dengan membuka VirtualBox, dan melihat masih adanya instance openedx ficus saya disitu.  

Hal perlu saya lakukan adalah, cek UUID VM VirtualBox openedx ficusnya: 

```bash
$ VBoxManage list vms
```

```bash
"Google Nexus 5 - 6.0.0 - API 23 - 1080x1920" {c69327e8-af61-4244-9ebe-0bbe48cdd153}
"devstack_default_1485404938992_3530" {300fca71-638b-4552-9599-253f527543fe}
"devstack-ficusmaster_default_1501805222426_26031" {429456bd-a39d-4ff6-9a7b-f573aec35cf3}
```  

Setelah itu di copy UUID VM yang ingin di hubungkan, dan buat file `id` di:

```bash
.vagrant/machines/default/virtualbox/id` 
```

Isi file tersebut dengan UUID VM, misalnya saya ingin menghubungkan `"devstack-ficusmaster_default_1501805222426_26031" {429456bd-a39d-4ff6-9a7b-f573aec35cf3}`, maka saya akan meng-copy  `429456bd-a39d-4ff6-9a7b-f573aec35cf3` ke dalam file `id`.    Sekarang coba jalankan kembali `vagrant up` di dalam folder openedx anda. Si vagrant sekarang akan menjalankan VM yang telah kita hubungkan tadi.   


Cheers!


---

Reference : 

- [https://stackoverflow.com/questions/37949635/how-can-i-restore-my-vagrant-vm-all-file-have-been-deleted](https://stackoverflow.com/questions/37949635/how-can-i-restore-my-vagrant-vm-all-file-have-been-deleted)
