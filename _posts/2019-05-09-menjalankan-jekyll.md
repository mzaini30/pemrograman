---
layout: post
title: Menjalankan Jekyll
---

Apa itu Jekyll? Jekyll adalah Static Site Generator (SSG) yang digunakan secara default oleh Github Pages. Jadi, setiap yang dihosting di Github Pages, maka akan secara otomatis dijalankan dengan Jekyll seperti blog yang sedang kamu lihat ini.

Nah, tentunya kan sebelum diupload ke Github, kita mau coba dulu nih bagaimana tampilannya jika sudah di-compile dengan Jekyll. Nah, berikut ini adalah skripnya:

# Cara Biasa

Cara biasa di bawah ini akan menghasilkan <http://localhost:4000>

```bash
jekyll s
```

# Menggunakan Port yang Berbeda

Nah, kadang kan kita sudah menggunakan port `4000` yang secara default-nya Jekyll sehingga akan terjadi bentrok karena port sudah digunakan. Berarti kan kita coba menggunakan port yang berbeda. Kita coba nih menggunakan port `2019`. Berikut ini adalah skripnya:

```bash
jekyll s --port=2019
```

Maka, outputnya adalah <http://localhost:2019>