---
layout: post
title:  "instal jekyll"
date:   2024-01-23 11:24:23 +0800
categories: jekyll update
---
Untuk menginstal Jekyll di Windows, Anda dapat menggunakan RubyInstaller, yang mencakup Ruby dan RubyGems. Berikut adalah langkah-langkahnya:

Instal Ruby:

Unduh RubyInstaller dari https://rubyinstaller.org/downloads/.
Pilih versi yang sesuai dengan sistem operasi Anda (32-bit atau 64-bit).
Ikuti panduan instalasi yang disediakan oleh installer.
Pastikan opsi "Add Ruby executables to your PATH" dicentang selama instalasi.
Verifikasi Instalasi Ruby:

Buka Command Prompt (CMD) atau PowerShell dan ketik perintah berikut untuk memastikan Ruby terinstal dengan benar:
bash
Copy code
ruby -v
Instal Jekyll:

Setelah Ruby terinstal, buka Command Prompt atau PowerShell dan jalankan perintah berikut untuk menginstal Jekyll dan Bundler:
bash
Copy code
gem install jekyll bundler
Verifikasi Instalasi Jekyll:

Setelah instalasi selesai, verifikasi instalasi Jekyll dengan perintah:
bash
Copy code
jekyll -v
Buat Proyek Jekyll Baru:

Navigasikan ke direktori tempat Anda ingin membuat proyek Jekyll.
Jalankan perintah berikut untuk membuat proyek baru:
bash
Copy code
jekyll new namaprojek
Pindah ke Direktori Proyek:

Pindah ke direktori proyek yang baru dibuat:
bash
Copy code
cd namaprojek
Jalankan Server Lokal:

Jalankan perintah berikut untuk melihat proyek Anda secara lokal:
bash
Copy code
bundle exec jekyll serve
Buka browser dan akses http://localhost:4000 untuk melihat situs lokal Anda.
Sekarang, Anda telah berhasil menginstal Jekyll di Windows dan membuat proyek Jekyll baru. Anda dapat terus mengedit dan menambahkan konten ke proyek Anda, dan melihat perubahan secara lokal dengan menjalankan server Jekyll. Jangan lupa untuk mengkomit dan mendorong perubahan ke repositori GitHub Anda jika Anda ingin meng-host situs Jekyll di GitHub Pages.






