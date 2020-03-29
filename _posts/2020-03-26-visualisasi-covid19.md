---
title: Visualisasi Covid-19 di Indonesia
tags: [python]
style: fill
color: primary
description: Visualisasi data infeksi COVID-19 di Indonesia menggunakan matplotlib.
---

Halaman ini berisikan visualisasi data infeksi COVID-19 di Indonesia menggunakan modul `inkovis`. Grafik dibawah ini **HANYA** mengolah data yang diperoleh dan memvisualisasikannya menggunakan matplotlib. Keterangan mengenai dataset bisa baca di _repository_ [taruma/inkovis](https://github.com/taruma/inkovis).

Bagi yang ingin membuat grafik seperti dibawah ini dengan dataset sendiri dan untuk kasus apapun (tidak terbatas untuk COVID-19), dapat menggunakan modul/kode yang disediakan di _repository_ [taruma/inkovis](https://github.com/taruma/inkovis). Modul/kode menggunakan lisensi MIT. 

## Visualisasi Data 15 Hari Terakhir (Harian)

{% include covid19viz.md data="15 Hari Terakhir" add_data="Harian"%}

## Visualisasi Seluruh Data (Per 2 Hari)

{% include covid19viz.md data="Seluruh Data" add_data="Per 2 Hari"%}