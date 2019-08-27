---
layout: post
title: "Docker Konsep"
date: 2019-08-27
categories: "docker"
author:     "dehamzah"
tags:
    - Docker
    - Container
---

![docker](../img/laurel-docker-containers.png)

# Docker Overview

 Docker adalah platform untuk developer dan sysadmin untuk develop, build, dan run application di dalam container. Docker memungkinkan kita untuk memisahkan aplikasi dengan infrastructure, jadi kita bisa melakukan development dengan lebih cepat. Dengan docker, kita dapat mengelola infrastructure kita seperti halnya aplikasi. Dengan memanfaatkan docker, kita bisa mengurangi *delay* deployment code ke production.

## Docker Platform

Docker memungkinkan kita untuk menjalankan aplikasi dalam sebuah isolated environment, bernama *container*. Karena isolated ini, kita dapat menjalankan lebih dari satu container dalam sebuah host server. Si docker ini juga ringan, karena dia tidak menjalankan full operating system diatas operating system host seperti halnya virtual machine. Dengan docker kita bisa menghemat biaya, karena bisa mengatur alokasi resource yang dibutuhkan oleh container melalui configuration file. Dan si docker ini juga bisa dijalankan di atas virtual machine.

## Docker Engine

Docker engine adalah client-server application yang terdiri dari 3 bagian besar berikut:
- Sebuah server, long running daemon process (daemond command)
  Si daemon ini yang membuat dan me-manage docker objects (images, containers, network dan volume)
- Rest API, interface untuk berkomunikasi dengan daemon dan menginstrukikan apa yang mau dilakukan
- Command Line Interface client (docker command)

![docker-engine](../img/engine-components-flow.png)

## Docker Usage

- Delivery aplikasi yang cepat dan konsisten
  Dengan konsep container, developer bisa bekerja di environment yang sama, baik antar developer, ataupun production environment.

- Kemudahan deployment dan scaling
  Di docker sangat mudah untuk mengatur workload, scaling up atau down dapat dilakukan dengan mudah hanya dengan konfigurasi file. Docker juga dapat di jalankan di local development machine, bare metal ataupun cloud provider.

- Menjalankan workload lebih di hardware yang sama
  Docker itu ringan dan cepat, lebih ringan daripada vm. Jadi kita bisa lebih memaksimalkan resource hardware.

## Docker Architecture

Docker menggunakan client-server architecture. Docker client memberikan perintah ke docker daemon, docker daemon lah yang bekerja keras. Dia mengatur hal-hal yang berkaitan dengan building, running dan distributing docker container. Mereka berkomunikasi via rest api melalui unix socket atau network.

![docker-architecture](../img/docker-architecture.svg)

#### Docker Daemon

Docker daemon (dockerd) tugasnya, mendengarkan perintah yang datang dari docker client dan memanage docker object seperti image, container, network, dan volume. Dia juga bisa berkomunikasi dengan docker daemon lainnya untuk memanage docker services.

#### Docker Client

Docker client (docker) adalah cara utama untuk berkomunikasi dengan docker daemon. Docker client bisa berkomunikasi dengan beberapa doker daemon.

#### Docker Registries

Ini adalah tempat penyimpanan docker images. Docker registries ada di lokal komputer kita dan di cloud. Di cloud ada Docker hub, itu adalah public image docker images. Secara default ketika kita menjalankan `docker pull`, `docker run` dan `docker push` itu akan membaca dari lokal registries lalu ke docker hub. Kita juga bisa mengarahkan ke docker registries private jika punya.

#### Docker Objects

- Images
  
  Image ini adalah read only template untuk membuat sebuah docker container. Dibuat dari sebuah file bernama `Dockerfile`.

- Containers
  
  Merupakan runnable instance dari sebuah image.

- Services
  
  Services memungkinan kita untuk melakukan scaling container across multiple docker daemon, yang mana mereka bekerja bersama sebagai *'swarm'* dengan multiple *manager* dan *worker*.