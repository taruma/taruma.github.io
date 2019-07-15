---
title: Rilis hidrokit 0.2.0
tags: [python, hidrokit, open-source]
style: fill
color: success
description: Rilisnya hidrokit 0.2.0 disertai situs resminya. Penjelasan mengenai proyek hidrokit 0.2.0.
---

[Enam bulan yang lalu (Januari 2019)](https://medium.com/@taruma/hidrokit-analisis-hidrologi-dengan-python-bdcad9e5865d), saya merilis hidrokit 0.1.0. Pada saat itu, banyak sekali kekurangan dari segi dokumentasi maupun teknis sehingga cukup sulit untuk memulai berkontribusi bagi yang tertarik untuk ikut serta dalam proyek _open-source_ ini. Dengan rilis 0.2.0, saya mencoba menjawab permasalahan tersebut dengan menyertai berbagai fitur untuk paket python hidrokit maupun dokumentasi sehingga memudahkan berkontribusi bagi yang tertarik dengan proyek ini. 

## Pengenalan

Hidrokit merupakan proyek _open-source_ paket/_package_ python yang dapat digunakan untuk membantu proses analisis hidrologi berupa pengolahan data, analisis data, dan visualiasi data. Proyek ini cocok bagi yang tertarik untuk ikut serta dalam proyek _open-source_. Hidrokit juga bertujuan membangun komunitas pengguna python (dan jupyter notebook) dan para praktisi atau akademisi yang memanfaatkan python dalam bidang hidrologi.  

Baca [abstrak dan tujuan hidrokit](https://taruma.github.io/hidrokit/tentang-hidrokit) untuk informasi lebih lanjut.

Jika ingin langsung melihat kegunaan hidrokit bisa lihat daftar notebook berikut:
- [Prediksi Kualitas Air menggunakan Metode _Artificial Neural Networks_ oleh taruma.](https://nbviewer.jupyter.org/github/taruma/hidrokit-nb/blob/master/notebook/taruma_demo_ann_ka_2_0_0.ipynb) (demonstrasi modul `prep.timeseries`, `prep.read`, `viz.table`, `viz.graph`)
- [Daftar tutorial fungsi/modul pada hidrokit.](https://notebook.hidrokit.online/kumpulan-notebook#hidrokit-)

Jika Anda tertarik berkontribusi pada proyek ini, baca bagian [kontribusi](#Berkontribusi).

-----

## Apa yang baru di hidrokit 0.2.0?

Pada hidrokit 0.2.0, proses pengembangan python diusahakan untuk mengikuti standar yang ada dimulai dari _packaging_, _versioning_, _testing_, dan _continous integration_. Hal tersebut mengakibatkan hidrokit 0.2.0 tidak _backward-compatibility_ dengan hidrokit 0.1.x. Diharapkan dengan struktur sekarang, hidrokit 0.2.0 memiliki kapasitas untuk _forward-compatibility_ dan memudahkan bagi _developer_ mengembangkan fitur baru atau memperbaiki fitur.

Dengan rilisnya hidrokit 0.2.0, diperkenalkan **tiga** situs utama yang berhubungan dengan proyek ini. 
- [hidrokit.online]\: Situs resmi proyek hidrokit yang berisikan dokumentasi berupa tentang hidrokit (tujuan/abstrak), tutorial/panduan berkontribusi, dll. 
- [notebook.hidrokit.online]\: Situs pelengkap yang berisikan kumpulan jupyter notebook mengenai penggunaan hidrokit dan pemanfaatan python dalam bidang hidrologi.
- [hidrokit.readthedocs.io]\: Situs berbahasa inggris yang digunakan sebagai dokumentasi teknis berisikan daftar lengkap _Application Program Interface_ (API) yang tersedia di proyek hidrokit. Situs ini ditujukan untuk pengembang / _developer_.

Dibuatnya situs agar memudahkan akses informasi melalui berbagai media (komputer, telepon genggam). Navigasi dan tampilan pada situs juga lebih mudah dibandingkan melalui halaman github karena halaman github lebih ditujukan untuk _developer_. 

Berikut perubahan penting pada proyek ini:

### hidrokit 0.2.0 (_Python Package_)

Perubahan berikut ditujukan untuk membuat proyek hidrokit lebih terstruktur dan lebih mudah untuk dikembangkan lebih lanjut.  Berikut perubahan penting hidrokit 0.1.x ke 0.2.0:

**Baru**
- Paket dibagi menjadi tiga subpaket (_subpackage_) utama yaitu persiapan (`hidrokit.prep`), analisis (`hidrokit.analysis`), dan visualisasi (`hidrokit.viz`). 
- Integrasi [travis-ci], [codecov], [codacy].
- Testing menggunakan [pytest] dengan 90%+ _coverage_.
- Situs khusus untuk dokumentasi teknis di [hidrokit.readthedocs.io](https://hidrokit.readthedocs.io) yang berisikan daftar API hidrokit dibangkitkan menggunakan _docstring_.

**Perubahan**
- Penamaan modul dan fungsi diubah dan disesuaikan dengan [standar PEP8](https://www.python.org/dev/peps/pep-0008/).
- Fungsi pada modul berikut digantikan dengan modul baru dibawah subpaket baru.
  - Fungsi pada `dlkit` dialihkan ke `prep.timeseries`.
  - Fungsi pada `viewkit` dialihkan ke `viz.table` dan `viz.graph`.
  - Fungsi pada `prepkit` dialihkan ke `prep.excel`.
  - Fungsi pada `datakit` dialihkan ke `prep.read`.
- Perubahan nama fungsi agar lebih jelas dan mengubah fungsi yang bukan ditujukan untuk penggunaan menjadi _private function_.
  - Seluruh fungsi pada `prepkit` yang berfungsi membaca berkas _excel_, untuk sementara menjadi _private function_.
  - Perubahan nama fungsi pada `dlkit` dan `datakit`.

| 0.1.x                             | 0.2.0                            |
| :-------------------------------- | :------------------------------- |
| `dlkit.plot_dataset`              | `viz.graph.subplots`             |
| `datakit.dict_null_data`          | `prep.read.missing_row`          |
| Fungsi column timesteps           | `prep.timeseries.timestep_table` |
| - `dlkit.single_column_timesteps` | _private_                        |
| - `dlkit.multi_column_timesteps`  | _private_                        |

**Penghilangan**
- Modul `bmkgkit` dihapuskan dan tidak digantikan.
- Modul berikut ini telah dihapus/digantikan sehingga tidak dapat digunakan lagi:
  - `dlkit`, `viewkit`, `bmkgkit`, `prepkit`, `datakit`.

<!-- LINK -->
[travis-ci]: https://travis-ci.org/taruma/hidrokit
[codecov]: https://codecov.io/gh/taruma/hidrokit
[codacy]: https://app.codacy.com/project/taruma/hidrokit/dashboard
[pytest]: https://pytest.org/

### Situs hidrokit ([hidrokit.online])

Situs hidrokit digunakan sebagai situs utama untuk memperoleh informasi mengenai proyek ini. Situs ini dibuat menggunakan [Jekyll](https://jekyllrb.com/) dan [Github Pages](https://pages.github.com/) _hosting_. _Repository_ situs dapat diakses di [cabang gh-pages](https://github.com/taruma/hidrokit/tree/gh-pages).

Berikut halaman penting yang tersedia pada situs hidrokit:

| Halaman | Keterangan |
| :---------------- | :----- |
| [tentang-hidrokit] | Abstrak dan Tujuan hidrokit. Dorongan untuk berkontribusi. |
| [berkontribusi] | Informasi umum untuk memulai berkontribusi. |
| [kode-etik] | Kode etik dalam proyek. |
| [instalasi] | Pemasangan/instalasi paket hidrokit. |
| [penggunaan] | Penggunaan paket hidrokit. |
| [sumber] | Daftar sumber yang digunakan dalam proyek. |

<!-- LINK -->
[tentang-hidrokit]: https://hidrokit.online/tentang-hidrokit
[berkontribusi]: https://hidrokit.online/berkontribusi
[kode-etik]: https://hidrokit.online/berkontribusi/kode-etik
[instalasi]: https://hidrokit.online/panduan/instalasi
[penggunaan]: https://hidrokit.online/panduan/penggunaan
[sumber]: https://hidrokit.online/serbaneka/sumber

### Situs Hidrokit Notebook ([notebook.hidrokit.online])

Situs Hidrokit digunakan sebagai situs pelengkap yang berisikan kumpulan jupyter notebook mengenai penggunaan hidrokit dan pemanfaatan python dalam bidang hidrologi. Situs ini dibuat menggunakan [Jekyll](https://jekyllrb.com/) dan [Github Pages](https://pages.github.com/) _hosting_. _Repository_ situs dapat diakses di [hidrokit-nb](https://github.com/taruma/hidrokit-nb/tree/master/docs).

Berikut halaman penting yang tersedia pada situs Hidrokit Notebook:

| Halaman | Keterangan |
| :---------------- | :----- |
| [kumpulan-notebook] | Daftar kumpulan notebook yang telah dikategorikan dan tersedia. |
| [mengunggah-notebook] | Panduan _upload_/mengunggah notebook. |
| [lisensi-notebook] | Keterangan lisensi notebook. |
| [pull-request] | Panduan lanjutan untuk memperbarui repo dan melakukan _pull request_ berikutnya. |
| [tambah-notebook] | Panduan menambah notebook ke halaman [kumpulan-notebook]. |
| [unduh-notebook] | Panduan mengunduh notebook. |

<!-- LINK -->
[kumpulan-notebook]: https://notebook.hidrokit.online/kumpulan-notebook
[mengunggah-notebook]: https://notebook.hidrokit.online/panduan/mengunggah-notebook
[lisensi-notebook]: https://notebook.hidrokit.online/panduan/lisensi-notebook 
[pull-request]: https://notebook.hidrokit.online/panduan/pull-request
[tambah-notebook]: https://notebook.hidrokit.online/panduan/tambah-notebook
[unduh-notebook]: https://notebook.hidrokit.online/panduan/unduh-notebook

-----
## Berkontribusi

Seluruh yang disebutkan pada proyek ini berupa paket python hidrokit, situs hidrokit, situs Hidrokit Notebook, situs readthedocs bersifat _open-source_ sehingga Anda bisa mengajukan perubahan, berkontribusi, atau bahkan Anda bisa mengembangkannya sebagai proyek Anda sendiri. Karena seluruh proyek ini menggunakan [**MIT License**](https://choosealicense.com/licenses/mit/) dan [**Creative Common Attribution 4.0 International**](https://choosealicense.com/licenses/cc-by-4.0/) kecuali disebutkan secara terpisah seperti pada [notebook](https://notebook.hidrokit.online/panduan/lisensi-notebook).

-----
## Frequently Asked Questions

Saya akan berusaha menjawab pertanyaan yang mungkin menjadi perhatian/pertimbangan.

#### Siapa dibalik proyek hidrokit?

> Proyek hidrokit dibuat dan dimulai oleh [Taruma Sakti Megariansyah](https://taruma.info) (saya sendiri. 😁). Saya merupakan lulusan sarjana teknik sipil dari Universitas Katolik Parahyangan, Bandung angkatan 2008. Sebagai informasi, saya belum memiliki pengalaman kerja pada bidang hidrologi ataupun _python/data science_.

#### Apakah proyek ini bagian dari tugas/kerjaan?

> Proyek hidrokit, _murni_ merupakan **proyek hobi** dan **pribadi**. 
> 
> **Proyek ini bukan**:
> - Bagian dari pekerjaan (yang tidak saya miliki. 🤣)
> - Menyelesaikan kewajiban akademis (tugas akhir/tesis)
> - Permintaan dari perusahaan / konsultan / praktisi / akademisi / individu. 

#### Keuntungan apa yang segera didapatkan jika menggunakan hidrokit?

> Pertama-tama, hidrokit bukan merupakan program instan yang tinggal memasukkan _input data_ kemudian langsung memperoleh _output data_ atua laporan. Sehingga tidak bisa "segera" diuntungkan saat beralih ke penggunaan hidrokit/python.
> 
> Jika Anda telah menggunakan python dan jupyter notebook pada alur kerja Anda, kemungkinan paket hidrokit bisa mempersingkat/mempercepat alur kerja tersebut. Jadi, sebelum menggunakan hidrokit, **diasumsikan sudah terbiasa** menggunakan python dan jupyter notebook. 
> 
> Bagi yang belum tahu python dan jupyter notebook, proyek ini memperkenalkan keuntungan hal tersebut dan membantu Anda memulai petualangan tersebut. Saat tulisan ini dipublikasi, belum ada halaman panduannya, tapi jika Anda membutuhkan bantuan, buat isu/diskusi [disini](https://github.com/taruma/hidrokit/issues/new/choose).
> 
> Pandangan pribadi saya adalah lebih praktis dan intuitif menggunakan python + jupyter notebook + hidrokit dibandingkan menggunakan spreadsheet excel. 

#### Lalu apa alasan dibuatnya hidrokit?

> Sejak dari dulu saya memiliki ketertarikan pada bidang komputer dan teknologi. Tahun 2016, saya membaca artikel mengenai _data science_ dan _machine learning_. Dan pada momen itu, saya berniat untuk mempelajarinya. 
> 
> Pada perjalanan belajar tersebut, disarankan untuk melatih pada proyek open-source. Sayangnya, dengan kemampuan bahasa inggris yang terbatas, saya kesulitan untuk ikut serta dalam proyek open-source yang ada. Terlebih lagi, saya bukan lulusan pada bidang komputer/informatika sehingga membaca istilah yang digunakan jadi pusing sendiri. 
> 
> Akhirnya, saya memutuskan untuk membuat proyek _open-source_ sendiri yang mungkin bisa membantu para individu di Indonesia untuk ikut sensasi "open-source" dengan kemampuan terbatas seperti saya dulu dan mengasah pengetahuan yang telah dipelajari tanpa mempermasalahkan bahasa.
> 
> Tidak lupa bahwa saya merupakan lulusan teknik sipil yang mengambil KBI Sumberdaya Air, saya menggabungkan disiplin tersebut dengan hasil yang saya pelajari mengenai python dan *data science*. Dan dibuatlah proyek hidrokit. 🎊
> 
> Dan dari alasan pribadi diatas berkembang menjadi [abstrak dan tujuan hidrokit](https://hidrokit.online/tentang-hidrokit).

Pada versi hidrokit 0.1.0, saya sempat membuat halaman khusus mengenai tanya jawab mengenai proyek ini pada umumnya. Anda bisa membacanya [disini](https://taruma.online/articles/tanya-jawab-hidrokit). 


<!-- LINK -->
[hidrokit]: https://taruma.github.io/hidrokit
[hidrokit-notebook]: https://taruma.github.io/hidrokit-nb
[hidrokit.online]: https://taruma.github.io/hidrokit
[notebook.hidrokit.online]: https://taruma.github.io/hidrokit-nb
[hidrokit.readthedocs.io]: https://hidrokit.readthedocs.io
