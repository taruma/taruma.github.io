---
title: Mencari nilai perbedaan pada MultiIndex
tags: [python, pandas]
style: fill
color: primary
description: |
    Mencari nilai perbedaan pada MultiIndex.
---

<div align="center">

{% include elements/highlight.html text="Original Post: <a href='https://github.com/teamalgoritma/community/discussions/170#discussioncomment-3589476' target='_blank'>diskusi @teamalgoritma/community #170</a>" %}
<br>
</div>

---

Untuk melakukan perhitungan dengan multiindex index, bisa juga menggunakan `.groupby(...)`.

Pada contoh kasus diatas, bisa menggunakan:

```python
test['Visitor Growth'] = test.groupby('Weekday').diff()
```

atau selain menggunakan key, bisa juga menggunakan level indexnya `level=`, menjadi:

```python
test['Visitor Growth'] = test.groupby(level=0).diff() # 0 = multiindex index pertama
```

---

Saya belum cek apakah konteksnya sama atau tidak, tapi saya bangkitkan dataframe yang menyerupai data aslinya:

```python
import numpy as np
import pandas as pd

np.random.seed(1234)

index_date = pd.date_range('20100101', '20151231')
dummy = pd.DataFrame(np.random.randint(100, 3000, index_date.size), index=index_date, columns=['VALUE'])
# dummy['DATE'] = dummy.index.strftime('%d')
dummy['DAY'] = dummy.index.strftime('%A')
dummy['MONTH'] = dummy.index.strftime('%B')
dummy['YEAR'] = dummy.index.strftime('%Y')
test = dummy.groupby(['YEAR', 'MONTH', 'DAY']).sum()

test
```

![image](https://user-images.githubusercontent.com/1007910/188986102-9c1567c8-770c-4638-a3be-f24a26a5cdbc.png)

dengan data tersebut, misalnya saya mau melihat `VALUE_GROWTH` setiap bulannya (level=1). Maka, perintah yang digunakan:

```python
test.groupby(['YEAR', 'MONTH']).diff()
# bisa juga ditulis menggunakan level
# test.groupby(level=[0, 1]).diff()
```

![image](https://user-images.githubusercontent.com/1007910/188989900-80ff3122-36b9-4e6c-9d28-3e853c58128e.png)

untuk memastikan apakah nilainya benar, bisa dibandingkan langsung dengan .diff() seperti tahapan awal solusi dari @triarm

```python
testcopy = test.copy()
testcopy['VALUE_GROWTH_MONTH'] = test.groupby(by=['YEAR', 'MONTH']).diff()
testcopy['DIFF'] = test.diff()
testcopy
```

![image](https://user-images.githubusercontent.com/1007910/188990965-6cad65e7-1503-49e9-b179-72f8947aac13.png)

Diperoleh hasil yang sama juga. Jadi, penggunaan `.groupby(...).diff()` bisa dijadikan alternatif.

---

Mungkin pertanyaan berikutnya, kenapa harus argumennya `by=['YEAR', 'MONTH']`? dan tidak `by='MONTH'` (ini pertanyaan yang muncul pas saya buat jawaban ini soalnya. 🤣) karena saya lihat sekilas hasilnya sama saja? seperti dilihat di gambar ini: 

![image](https://user-images.githubusercontent.com/1007910/188991432-d41feaef-db5e-4a16-ae81-8633e9ad16bd.png)

Rekomendasi saya pada saat melakukan ini, selalu evaluasi awal dan akhir dari dataframe, karena bisa saja bagian atasnya benar tapi bawahnya salah. Jika dilihat menggunakan tail akan muncul perbedaannya, dan hasilnya tidak sesuai ekspetasi kita. Coba dilihat menggunakan `.tail(...)`. Hasilnya sebagai berikut:

![image](https://user-images.githubusercontent.com/1007910/188991738-b0c32e26-06d1-4aee-9aa1-2a73ced3200d.png)

disini setiap nilai awal index `DAY` nilainya tidak `NaN` terlepas hasil `.diff()`-nya sama.  

---

Hal tersebut dikarenakan pada proses `.groupby(...)`, jika yang digunakan hanya label tertentu (pada kasus ini yaitu `MONTH` saja), maka dia akan mengelompokkan keseluruhan data dengan label tersebut saja. Sehingga, index label lainnya (`YEAR`) akan diabaikan.

Contoh ilustrasinya jika digunakan hanya `MONTH` saja (level=1):

![groupby_single](https://user-images.githubusercontent.com/1007910/188995422-867d842c-73bc-4d0e-ab6d-2b6cc6d6d1b7.png)

Di ilustrasi tersebut, terlihat pada `B1` yang bagian dari `A2`, diurutkan sebelum `B2`. Maka dari itu, elemen awal setiap `B`, perintah `.diff()` akan mengacu pada nilai sebelumnya terlepas pemisah dari index `A`. Pada gambar tersebut nilai `A2-B1-C1` merupakan hasil dari `D7-D3`, dimana nilai `D3` berada di `A1-B1-C3`. 

Dan jika kita menggunakan level secara bertahap yaitu `['YEAR', 'MONTH']` atau `[0, 1]`, maka dapat diilustrasikan sebagai berikut: 

![groupby_multi](https://user-images.githubusercontent.com/1007910/188995825-c8360bc8-cd6f-4cf6-a1e2-22365616945d.png)

Pada gambar diatas, hasilnya sesuai dengan harapan kita, dimana nilai dikelompokkan per `YEAR`, baru dikelompokkan kembali per `MONTH`. 

Untuk contoh kasus @RanggaGemilang, sebenarnya bisa langsung dengan mengetikkan `by='Weekday'` / `level=0` dikarenakan itu index pertama dari multiindex-index. Sedangkan contoh kasus saya, nilai yang ingin direkap merupakan index kedua, sehingga pada saat perhitungan pengelompokkan, harus juga disertakan dengan index pertama. 

---

Jadi, solusi ini lebih mengarahkan bagaimana mengelompokkan nilai menjadi `Series` terlebih dahulu dan baru menerapkan sebuah fungsi (contohnya: `.diff()`). 

Semoga bermanfaat. :)