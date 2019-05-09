---
layout: post
title: Skrip untuk Membuat Postingan Baru di Jekyll Secara Otomatis
---

Skrip di bawah ini menggunakan bahasa Python versi 3:

```python
import datetime, os

judul = input('Masukkan judul postingan: ')
# print(judul.lower())

sekarang = datetime.datetime.now()
# print(sekarang.strftime('%Y-%m-%d %H:%M:%S'))

karakter_terlarang = ['\\', '/', ':', '*', '?', '"', '\'', '<', '>', '|', '!']

# INI BAGIAN JUDUL

judul_kecil = judul.lower().replace(' ', '-')
for x in karakter_terlarang:
	judul_kecil = judul_kecil.replace(x, '')
# print(judul_kecil)
tanggal_untuk_judul = sekarang.strftime('%Y-%m-%d-')
# print(tanggal_untuk_judul)
judul_sekarang = tanggal_untuk_judul + judul_kecil + '.md'
# print(judul_sekarang)

# INI BAGIAN ISI

judul_baru = str(judul)
# judul_baru = judul_baru.replace('"', '\\\\\"')
# judul_baru = '"' + judul_baru + '"'
# judul_baru = judul_baru.replace('"', '')
# judul_baru = "\'" + judul_baru + "'"
# judul_baru = judul_baru.replace("'", '"')
# print(judul_baru)

perintah = [
	'cd _posts',
	'touch ' + judul_sekarang,
	'echo --- > ' + judul_sekarang,
	'echo layout: post >> ' + judul_sekarang,
	'echo "title: ' + judul_baru + '" >> ' + judul_sekarang,
	'echo --- >> ' + judul_sekarang
]

perintah_string = ''
for x in perintah:
	perintah_string += x + ';'
os.system(perintah_string)
```

# Cara Menjalankan

```bash
python3 new-post.py
```

# Ketika Dijalankan

- Muncul tulisan `Masukkan judul postingan: `
- Terus kamu masukkan dah itu judulnya. Misalnya aja aku mengetikkan `Cara Membuat Opor Ayam`
- Maka akan secara otomatis terbuat file `2019-05-09-cara-membuat-opor-ayam.md` di dalam folder `_posts` yang isinya:

	```yaml
	---
	layout: post
	title: Cara Membuat Opor Ayam
	---
	```

# Penjelasan Skrip

Skrip dibuka dengan:

```python
import datetime, os
```

Maksud dari skrip di atas berarti kita meng-import modul `datetime` yang berfungsi untuk mengolah waktu seperti tahun, bulan, hari, jam, menit, detik; dan kemudian modul `os` yang berfungsi untuk menjalankan perintah-perintah yang biasa kita ketikkan di Terminal. Kalau di Linux itu berarti Terminal sedangkan kalau di Windows itu namanya Command Prompt.

Contoh dari perintah yang biasa kita ketikkan di Terminal:

- Terminal (Linux)
	- ls
	- sudo apt install nama-aplikasinya
	- sudo dpkg -i nama-aplikasi.deb
- Command Prompt (Windows)
	- tree
	- dir
	- title

Berarti kalau kita menggunakan modul `os`, maka kita akan memanggilnya dengan:

```python
os.system('ls')
```

```python
judul = input('Masukkan judul postingan: ')
```

Skrip di atas berarti kita menginginkan suatu inputan yang akan mengisi variabel `judul`.

```python
sekarang = datetime.datetime.now()
```

Variabel `sekarang` berisi dengan waktu saat ini.

```python
karakter_terlarang = ['\\', '/', ':', '*', '?', '"', '\'', '<', '>', '|', '!']
```

Nah, maksud dari karakter terlarang ini adalah karakter-karakter yang tidak dibolehkan sebagai nama suatu file. Aku dapatnya sih dari Windows. Mungkin kalau Linux kurang lebih.

```python
# INI BAGIAN JUDUL

judul_kecil = judul.lower().replace(' ', '-')
for x in karakter_terlarang:
	judul_kecil = judul_kecil.replace(x, '')
# print(judul_kecil)
tanggal_untuk_judul = sekarang.strftime('%Y-%m-%d-')
# print(tanggal_untuk_judul)
judul_sekarang = tanggal_untuk_judul + judul_kecil + '.md'
# print(judul_sekarang)
```

Itu adalah bagian judul dari file Markdown yang akan dibuat oleh skrip.