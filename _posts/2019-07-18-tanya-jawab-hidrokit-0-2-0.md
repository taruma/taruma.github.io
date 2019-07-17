---
title: Tanya Jawab Hidrokit 0.2.0
tags: [hidrokit, faq]
style: fill
color: info
description: Tanya Jawab mengenai hidrokit rilis 0.2.0
---

Halaman ini memberikan tambahan FAQ yang dibuat pada halaman rilis hidrokit 0.2.0. Beberapa pertanyaan dialihkan ke halaman ini agar memperingkas halaman rilis hidrokit 0.2.0. Pertanyaannya juga diperoleh dari respon dari berbagai [komunitas/grup](#pertanyaan-dari-komunitasgrup). 

**Lalu apa alasan dibuatnya hidrokit?**
> Sejak dari dulu saya memiliki ketertarikan pada bidang komputer dan teknologi. Tahun 2016, saya membaca artikel mengenai _data science_ dan _machine learning_. Dan pada momen itu, saya berniat untuk mempelajarinya. Saya memulai mempelajari python dari akhir tahun 2017. 
> 
> Pada perjalanan belajar tersebut, disarankan untuk melatih pada proyek open-source. Sayangnya, dengan kemampuan bahasa inggris yang terbatas, saya kesulitan untuk ikut serta dalam proyek open-source yang ada. Terlebih lagi, saya bukan lulusan pada bidang komputer/informatika sehingga membaca istilah yang digunakan jadi pusing sendiri. 
> 
> Akhirnya, saya memutuskan untuk membuat proyek _open-source_ sendiri yang mungkin bisa membantu para individu di Indonesia untuk ikut sensasi "open-source" dengan kemampuan terbatas seperti saya dulu dan mengasah pengetahuan yang telah dipelajari tanpa mempermasalahkan bahasa.
> 
> Tidak lupa bahwa saya merupakan lulusan teknik sipil yang mengambil KBI Sumberdaya Air, saya menggabungkan disiplin tersebut dengan hasil yang saya pelajari mengenai python dan *data science*. Dan dibuatlah proyek hidrokit. 🎊
> 
> Dan dari alasan pribadi diatas berkembang menjadi [abstrak dan tujuan hidrokit](https://hidrokit.online/tentang-hidrokit).

**Kenapa belum ada fitur baru dari hidrokit 0.1.x atau fitur yang fungsional?**
> Tiga bulan terakhir saya memastikan bahwa proyek hidrokit bersifat _future-compatibility_, sehingga selama tiga bulan terakhir ini saya lebih disibukkan memastikan apa yang saya buat sudah mematuhi _guideline_. Saya juga disibukkan dengan mempersiapkan situs hidrokit dan memisahkan _notebook_ ke repository yang terpisah. Hal tersebut belum ditambah kemampuan saya dalam python ataupun pengembangan situs. Selama tiga bulan juga diisi dengan menonton/membaca dokumentasi/tutorial mengenai cara penulisan python, penulis docstring, dll. Selain itu, saya juga disibukkan dengan mempelajari mempublikasikan situs dengan Jekyll melalui Github Pages yang merupakan pengalaman pertama saya sama sekali menyentuh Jekyll.
> 
> Dokumentasi juga menjadi beban tersendiri. Menulis panduan/tutorial, halaman depan, menulis ulang "hidrokit adalah ...." bisa lebih dari 30 kali. Setiap besoknya, selalu ada saja yang bisa diperbaiki agar lebih baik untuk mudah di baca atau jelas. Anda bisa melihatnya dari _commit_ yang saya buat. 😅😅
> 
> Jadi, maaf kalau tidak begitu banyak fitur baru di hidrokit 0.2.0. Karena saya sendiri masih awam di dunia python ataupun _open-source_. 🙇‍♀️🙇‍♂️. Semoga di 0.3.0 setidaknya saya sudah menambahkan fitur baru, terutama untuk analisis. Dan diharapkan juga saya sudah mulai menguasai memanfaatkan OOP. 

**Apa yang akan datang di versi berikutnya?**
> Saat ini, saya sedang belajar mengenai penggunaan deep learning dan hidrologi. Kemungkinan besar fitur hidrokit ditambah sesuai kebutuhan saya saat melakukan pembelajaran/penelitian. Fungsi `prep.timeseries` merupakan salah satu bentuk modul yang saya buat untuk membantu saya saat menggunakan ANN. Akan tetapi, rencana penelitian saya belum tentu sesuai dengan yang saya inginkan, sehingga pengembangan fitur akan bergantung apa yang saya lakukan kedepannya.
> 
> Jika ada ide/isu pada proyek ini, saya akan coba membalasnya dan mengatasinya meski tidak bisa janji atau respon cepat. 

**Saya bukan orang bidang hidrologi/python, bagaimana saya bisa berkontribusi?**
> Jujur, saya juga bukan ahli atau tahu banyak mengenai kedua bidang tersebut. Saya belum pernah bekerja pada kedua bidang tersebut, jadi saya bisa dibilang masih awam. Satu saya peroleh dari jalur akademis, satunya lagi karena jalur hobi dengan modal internet. 
> 
> Menurut saya, hidrologi memiliki konsep yang mudah ditangkap bagi kebanyakan orang karena bisa diobservasi dengan mudah. Curah hujan yang turun, ke permukaan, mengalir, menguap, dll. Akan tetapi bisa menjadi sangat kompleks ketika memulai berbicara interaksi proses tersebut dengan detail. Jadi, jangan takut gara-gara Anda tidak memiliki latar belakang tersebut. Tanyakan saja kepada komunitas. Bisa jadi setelah Anda bergabung di proyek ini, Anda tertarik mengambil bidang sumberdaya air di teknik sipil. 😉
> 
> Untuk python, saya juga terhitung baru belajar. Ini merupakan proyek "besar" pertama saya dan kelihatan bahwa saya masih mencari tahu python itu sendiri. Proyek ini bisa jadi kesempatan untuk belajar bersama. 
> 
> Proyek ini bersifat inklusif, jadi jangan ragu berkontribusi karena "saya bukan orang komputer / teknik sipil / hidrologi / praktisi / apapun itu".

-----
### Pertanyaan dari komunitas/grup

#### Komunitas Telegram Python Indonesia

**Biasa dijalanin di Google Colab ya? [link](https://t.me/pythonID/123707)**
> Sekarang saya lebih suka menggunakan layanan Google Colab untuk mencoba hidrokit atau python. Selain layanan itu gratis, lebih praktis dibandingkan jika mengatur/menyalakan jupyter notebook di komputer saya sendiri. Kemungkinan kedepannya, selama layanan Google Colab masih terbuka, saya akan menggunakannya untuk bereksperimen atau membagikan hasilnya.

#### Komunitas Telegram Indonesia Python Warriors

**Analisis Hidrologi itu kaya apa ya? Ada video penggunaannya? [link](https://t.me/idpyplc/2791)**
> Contoh penerapan analisis hidrologi bisa baca di [Hydrology#Applications](https://en.wikipedia.org/wiki/Hydrology#Applications). <br>
> Untuk video penggunaannya sih saya kurang tahu. Di teknik sipil sendiri, analisis hidrologi digunakan saat menghitung debit banjir, debit sungai, irigasi, drainase, dll. 

**Bisa gak memprediksi debit dari ketinggian air? [link](https://t.me/idpyplc/2794)**
> Jawaban singkatnya, bisa. Jika menggunakan machine learning, mungkin nanti terbatas dengan data yang tidak begitu banyak. Tapi jika menggunakan model fisik/konseptual, rasanya sudah ada model yang mampu memberikan hubungan antara debit dan ketinggian air. 

----

Dari Grup Whatsapp (Karena tidak dapat diakses publik, tidak ada informasi grup apa dan ditanyakan oleh siapa.)

#### Grup 1

**Akan lebih keren kalo ada fungsi kalibrasi dan validasi secara otomatis.**
> Alasan lain saya tidak menyertakan atau merancang fungsi apa saja yang akan disediakan dalam hidrokit adalah sudah BANYAK paket python yang menjawab berbagai permasalahan dalam bidang hidrologi. Dan saya yakin bahwa sudah banyak juga yang pernah mengembangkan _script_ pada python atau program. Jika dapat diakses terbuka, mungkin kita tidak perlu memulai dari 0. <br>
> Saya menemukan daftar berbagai paket python yang bersifat open-source. Bisa baca di [Open Source Python Packages in Hydrology oleh Raoul Collenteur](https://github.com/raoulcollenteur/Python-Hydrology-Tools). Anda juga bisa mengikuti blog [Water Programming: A Collaborative Research Blog](https://waterprogramming.wordpress.com/) yang membahas penggunaan python/R dalam mengatasi permasalahan dalam bidang sumberdaya air. <br>
> Jika dapat menggunakan paket yang sudah tersedia, gunakan paket tersebut. Mungkin rencana di hidrokit adalah membuat semacam _wrapper_ yang memudahkan penggunaan paket-paket tersebut. 

### Grup 2

**Apakah ini sistem open source programming yang berbasis online?**
> Istilah open-source memiliki makna sendiri. Proyek hidrokit mengikuti kriteria [Open Source Definition](https://opensource.org/osd) dari OpenSource.org. <br>
> Mungkin istilah yang tepat adalah _cloud computing_. Jawabannya iya, contoh notebook yang telah saya buat [disini](https://nbviewer.jupyter.org/github/taruma/hidrokit-nb/blob/master/notebook/taruma_demo_ann_ka_2_0_0.ipynb) mendemonstrasikan penggunaan python berbasis _cloud computing_ yang menggunakan [Google Colab](https://colab.research.google.com/) sebagai servernya. Pribadi, saya baru pernah menggunakan layanan Google Colab dan [Microsoft Azure](http://azure.microsoft.com/en-us/).

**Seperti apa _user interface_-nya, apakah seperti ArcMap pada ArcGIS tapi ada koding pythonnya?**
> Saat ini paket hidrokit tidak memiliki _Graphical User Interface_ (GUI). Akan tetapi bisa dikembangkan GUI menggunakan [pyQT](https://riverbankcomputing.com/software/pyqt/intro) jika memang diperlukan. <br>
> Tidak ada interfacenya karena hidrokit murni hanya sebagai paket python. Untuk python sendiri, dimungkinkan membungkus program yang sudah ada dan digunakan selayaknya paket python. Jadi python bisa memanfaatkan program .exe yang pernah dibuat tapi menggunakan tampilan python. Yang saya tangkap sih seperti ArcGIS/QGIS + python.

Terima kasih atas perhatiannya, jika Anda memiliki pertanyaan/kritik/saran mengenai proyek ini Anda bisa membuat isu/diskusi di [halaman github](https://github.com/taruma/hidrokit/issues/new/choose). Anda bisa menghubungi saya melalui email di hi@taruma.info (Jika terkait proyek hidrokit, dianjurkan untuk melalui github).
