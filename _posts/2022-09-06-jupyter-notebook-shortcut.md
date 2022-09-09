---
title: Menjalankan Jupyter Notebook via shortcut (Windows)
tags: [python, conda]
style: border
color: success
description: |
    Alternatif menjalankan <i>jupyter notebook</i> pada <i>conda environment</i> menggunakan shortcut di Windows 11. 
---

<div align="center">

{% include elements/highlight.html text="Original Post: <a href='https://github.com/teamalgoritma/community/discussions/288' target='_blank'>diskusi @teamalgoritma/community #288</a>" %}
<br>
{% include elements/highlight.html text="Artikel ini merupakan balasan dari pertanyaan <a href='https://github.com/teamalgoritma/community/discussions/287' target='_blank'>diskusi @teamalgoritma/community #287</a>" %}

</div>

---

Ada alternatif lain untuk menjalankan jupyter notebook yaitu dengan membuat shortcut yang mampu membuka environment dan langsung menjalankan jupyter notebook (atau script lainnya). Lebih ribet sih saat pengaturannya, tapi setidaknya ini menghemat waktu untuk jangka panjangnya. 

Sistem yang saya gunakan: Windows 11, Miniconda

## Buat shortcut

Buat shortcut dengan klik kanan di Desktop/Folder Desktop > New > Shortcut. Disarankan di desktop agar lebih mudah mengakses shortcut ini.

![image](https://user-images.githubusercontent.com/1007910/188513332-2000bbc3-31bc-41af-a2ea-7bcb04a18bf2.png)

## Isi lokasi/perintah shortcut

Setelah itu, akan dimintai lokasi aplikasinya. Lokasi ini bisa diisi juga dengan perintah seperti _command prompt_ juga (dengan menggunakan aplikasi cmd). Gunakan perintah dibawah ini untuk menjalankan/mengaktivasi _conda environment_, dan membuka _conda environment_ spesifik (dalam kasus ini yaitu base), kemudian menjalankan perintah jupyter notebook.

```cmd
%windir%\System32\cmd.exe "/K" C:\Miniconda3\Scripts\activate.bat base & jupyter notebook && exit
```

![image](https://user-images.githubusercontent.com/1007910/188514379-674200df-d906-4af8-b373-4760599e52a1.png)


Berikut penjelasannya:

```python
> %windir%\System32\cmd.exe  # alamat aplikasi command prompt. 
> "/K" # ini argumen cmd untuk menjalankan perintah setelah argumen ini (lebih jelasnya ketik cmd /? di terminal). 
> C:\Miniconda3\Scripts\activate.bat base & jupyter notebook && exit
    > C:\Miniconda3\Scripts\activate.bat # mengaktivasi conda environment. Ubah alamat ini sesuai dengan lokasi Anaconda/Miniconda. Untuk instalasi menggunakan anaconda menjadi C:\Anaconda3\Scripts\activate.bat
    > base # pada "base" environment. Bagian ini bisa digantikan dengan environment tertentu
    > & # dan eksekusi perintah berikutnya
    > jupyter notebook # jalankan perintah "jupyter notebook"
    > && # dan eksekusi perintah berikutnya jika perintah sebelumnya success/selesai
    > exit # keluar dari terminal/command prompt
```

Kode ini tidak jauh berbeda dengan _console shortcut_ yang dibuat oleh anaconda/miniconda saat instalasi pertama. 

## Menamai shortcut

Isi nama shortcut yang deskriptif, contoh "Run Jupyter Notebook (base)". Dan akhiri pembuatan shortcut dengan memilih "Finish". 

![image](https://user-images.githubusercontent.com/1007910/188514571-2e06ca83-77ce-4ad5-8abe-6dab2d8d022d.png)

## Mengatur lokasi current working directory

Setelah selesai membuat shortcut, kita harus mengatur _current working directory_ (CWD). CWD ini menentukan folder aktif yang akan digunakan saat membuka jupyter notebook. Pada contoh ini, saya ingin menjalankan jupyter notebook dan menggunakan CWD di folder `C:\_github\algo-DAS`. 

Caranya, klik kanan pada shortcut, pilih Properties, ubah nilai "Start in:" menjadi `C:\_github\algo-DAS`. 

![image](https://user-images.githubusercontent.com/1007910/188515122-943a9db5-d08f-4734-be39-6ee1fd26d077.png)

Catatan: jika alamatnya memiliki spasi, tidak perlu menggunakan `"` di textbox "Start In:". Contoh: `D:\05 Reference and Textbook\04 Others`. karena secara otomatis akan ditambahi `"` jika alamat memiliki spasi. 

Tips: ubah nama shortcut dengan lebih detail seperti "Run Jupyter Notebook (base) algo-DAS", atau biar lebih singkat "Run Notebook (base) algo-DAS". atau variasi lainnya yang mudah mengingatkan Anda saat menggunakan shortcut tersebut. 

## Pin shortcut di taskbar atau start

Klik kanan pada shortcut yang telah dibuat, dan pilih Pin to Start atau Pin to Taskbar. Opsi ini dilakukan jika tidak menampilkan shortcut di desktop. 

![image](https://user-images.githubusercontent.com/1007910/188514677-b7e31c31-ff20-4252-8da5-5436372b9495.png)

Dan selesai sudah membuat shortcut untuk menjalankan jupyter notebook pada base environment. 

---

Sekarang tinggal klik shortcut tersebut tanpa repot-repot mengetik jupyter notebook. (meski membiasakan diri dengan command line interface itu cukup penting sih). Dan kalau mau dimodifikasi lebih lanjut juga lebih mudah (seperti buka jupyter lab, atau tambah argument --no-browser, dlsbnya).

![image](https://user-images.githubusercontent.com/1007910/188516673-5cba7fe9-6f47-4243-94a2-86e62073479e.png)

---

Use case saya biasanya saat menjalankan server lokal untuk google colab, atau aktivasi aplikasi dash. Dan ini menghemat waktu saya. Sayangnya, karena kebiasaan ini, saya suka lupa lagi perintah-perintahnya kalau ditanya lagi. 🤣🤣🤣🤣. Jadi ini untuk catatan saya juga sih. 

Semoga membantu!

Bonus: untuk instruktur bisa distribusikan file .lnk (shortcut) ke peserta, tinggal ubah Start In: menjadi %HOMEPATH%. (tapi rute ini tidak disarankan karena jika sembarang menjalankan shortcut itu berbahaya (bisa disisipi oleh perintah berbahaya). Jadi, tetap direkomendasikan untuk membuatnya sendiri dan mandiri). 

---

_ini sebenarnya jawaban pertanyaan [#287](https://github.com/teamalgoritma/community/discussions/287). saya buat terpisah, biar lebih mudah dilihatnya_. 