---
title: Reindex untuk MultiIndex di pandas
tags: [python, pandas]
style: fill
color: primary
description: |
    Reindex untuk MultiIndex di pandas.
---

<div align="center">

{% include elements/highlight.html text="Original Post: <a href='https://github.com/teamalgoritma/community/discussions/169#discussioncomment-3590640' target='_blank'>diskusi @teamalgoritma/community #169</a>" %}
<br>
</div>

---

Untuk kasus ini, saya menangkapnya bahwa urutan index `Quarter` ingin diurutkan secara terbalik (terbaru diatas). Solusi lain adalah dengan membuat objek index `pd.MultiIndex` yang menyerupai dari original index. 

Kalau lihat polanya bahwa ada dua label di multiindex yaitu `Country` dan `Quarter`. Dari sampel data diatas bisa disajikan dalam bentuk `list`. 

```python
COUNTRY = ['EIRE', 'France', 'Australia']
QUARTER = ['2010Q4', '2011Q1', '2011Q2']
```

Untuk membalikkan elemen di `QUARTER` bisa menggunakan metode slicing `[::-1]`.

```python
quarter_reverse = QUARTER[::-1]
```

setelah itu bisa membuat objek `pd.MultiIndex` dengan kedua list tersebut.

```python
new_index = pd.MultiIndex.from_product([COUNTRY, quarter_reverse])
>>> MultiIndex([(     'EIRE', '2011Q2'),
                (     'EIRE', '2011Q1'),
                (     'EIRE', '2010Q4'),
                (   'France', '2011Q2'),
                (   'France', '2011Q1'),
                (   'France', '2010Q4'),
                ('Australia', '2011Q2'),
                ('Australia', '2011Q1'),
                ('Australia', '2010Q4')],
            )
```

Dari sini tinggal memanggil dataframe `invoice_topq.loc[new_index]` dan akan muncul dengan urutan yang baru.

Berikut kode solusi yang serupa tanpa _hardcode_ nilai `Country` atau `Quarter`:

```python
country = invoice_topq.index.get_level_values(0).unique() # index multiindex pertama (0) / country
quarter = invoice_topq.index.levels[1][::-1] # index multiindex kedua / quarter (dan dibalikkan)
new_index = pd.MultiIndex.from_product([country, quarter])
invoice_topq.loc[new_index]
```

Alasan menggunakan `.index.get_level_values(...).unique()` untuk mempertahankan posisi urutan index. Jika urutan bukanlah hal yang penting, maka untuk memperoleh list cukup dengan `.index.levels[...]`. 

---

Berikut contoh kasus lainnya (sama dengan jawaban saya di [#170](https://github.com/teamalgoritma/community/discussions/170)). Dataframe test:

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

Saya ingin mengurutkan dengan bulan January-December dan hari Monday-Sunday.

```python
import calendar

level0 = test.index.levels[0]
level1 = list(calendar.month_name)[-12:] # first element is empty
level2 = list(calendar.day_name)
new_index = pd.MultiIndex.from_product(
    [level0, level1, level2], names=['YEAR', 'MONTH', 'DAY']
)
new_index
>>> MultiIndex([('2010',  'January',    'Monday'),
                ('2010',  'January',   'Tuesday'),
                ('2010',  'January', 'Wednesday'),
                ('2010',  'January',  'Thursday'),
                ('2010',  'January',    'Friday'),
                ('2010',  'January',  'Saturday'),
                ('2010',  'January',    'Sunday'),
                ('2010', 'February',    'Monday'),
                ('2010', 'February',   'Tuesday'),
                ('2010', 'February', 'Wednesday'),
                ...
                ('2015', 'November',    'Friday'),
                ('2015', 'November',  'Saturday'),
                ('2015', 'November',    'Sunday'),
                ('2015', 'December',    'Monday'),
                ('2015', 'December',   'Tuesday'),
                ('2015', 'December', 'Wednesday'),
                ('2015', 'December',  'Thursday'),
                ('2015', 'December',    'Friday'),
                ('2015', 'December',  'Saturday'),
                ('2015', 'December',    'Sunday')],
            names=['YEAR', 'MONTH', 'DAY'], length=504)
```

Dari sini tinggal menggunakan `.loc[new_index]`.

```python
test.loc[new_index]
```

![image](https://user-images.githubusercontent.com/1007910/189026032-303838a6-fcd6-44ad-a1d7-3eb2b5aff0b6.png)

Untuk mengecek nilainya benar atau tidak, bisa menggunakan _slice_:

```python
test.loc[pd.IndexSlice[:, 'January', 'Monday']]
```

![image](https://user-images.githubusercontent.com/1007910/189026172-ece5364f-f043-4f67-8ede-afa110ff92b9.png)


---

Referensi:
- [Pandas User Guide: Hierarchical Indexing Multiindex](https://pandas.pydata.org/docs/user_guide/advanced.html#hierarchical-indexing-multiindex)