---
title: Shortcut Anaconda Prompt menghilang 😲
tags: [python, anaconda, miniconda]
style: border
color: success
description: Mengembalikan shortcut Anaconda Prompt
---

Hari ini mau coba latihan dan belajar Python dari [video ini](https://www.youtube.com/watch?v=mUu_4k6a5-I). Eh, pas mau coba buka jupyter notebook, saya cari di shortcut windows gak nemu. Entah karena saya baru update conda atau apa, intinya saya kehilangan shortcut untuk windows. Untungnya saya bisa mengatasinya manual karena saya menggunakan conda environment di vscode. Coba cari masalah ini, nemu [isu ini](https://github.com/ContinuumIO/anaconda-issues/issues/8794) yang berbicara hilangnya shortcut Anaconda prompt. 

Berhubung saya menggunakan miniconda, jadi gak begitu terpengaruh sama Anaconda Navigator. Saya pakai miniconda juga karena punya pengalaman seperti hilangnya shortcut di navigator, yang akhirnya saya pakai miniconda.

Kembali ke permasalahan tadi, dari isu tadi saya menemukan komentar bahwa ditemukan solusi dengan memasang _console\_shortcut_. Dan tada, anaconda prompt muncul lagi di shortcut windows saya (start menu). Berikut langkah yang saya lakukan

- Buka explorer, dan buka direktori miniconda (`C:\Miniconda3\)
- Ketik `cmd` di _address bar_ untuk membuka Command prompt. Muncul tampilan dibawah:
```
C:\Miniconda3> 
```
- Arahkan ke direktori `Scripts` kemudian ketik `activate`. 
```
C:\Miniconda3> cd Scripts
C:\Miniconda3\Scripts> activate
(base) C:\Miniconda3\Scripts> 
```
- Setelah conda berjalan, tinggal install `conda install console_shortcut`.
```
(base) C:\Miniconda3\Scripts> conda install console_shortcut
```

Beres deh. Muncul deh shortcut untuk Anaconda Prompt di start menu. 

Sebenarnya gak perlu-perlu amat sih buka anaconda prompt. Kalau pakai vscode, terminal sudah diatur sedemikian rupa jadi gak perlu repot buka command prompt di luar vscode. Ini buka Anaconda prompt sekedar ingin menjalankan jupyter notebook saja. 

Oke deh, cukup cerita hari ini.