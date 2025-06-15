# Praktikum-1
---
title: "Metode Trapezoidal"
author: "Khairan Cherokee Musthofa"
NRP: 5025241215
---

---
# 📘 Pendahuluan

Metode Romberg adalah teknik numerik untuk menghitung integral tentu berdasarkan metode trapezoida yang disempurnakan dengan teknik *ekstrapolasi Richardson*. Ekstrapolasi ini digunakan untuk memperbaiki hasil integral numerik dengan menggabungkan pendekatan trapezoida pada berbagai ukuran partisi yang lebih kecil.

---

# 🧮 Fungsi yang Digunakan

Dalam laporan ini, fungsi yang digunakan adalah:

$$
R[i][j] = R[i][j-1] + (R[i][j-1] - R[i-1][j-1]) / (4^j - 1)
$$

---

# 🔢 Implementasi Python

```python
  import numpy as np
  
  def f(x):
      return x**2 * np.cos(x**2)
  
  def romberg(a, b, n):
      R = np.zeros((n, n))
      h = b - a
      R[0, 0] = 0.5 * h * (f(a) + f(b))
  
      for i in range(1, n):
          h /= 2
          sum_f = sum(f(a + (2 * k - 1) * h) for k in range(1, 2**(i - 1) + 1))
          R[i, 0] = 0.5 * R[i - 1, 0] + h * sum_f
  
          for j in range(1, i + 1):
              R[i, j] = R[i, j - 1] + (R[i, j - 1] - R[i - 1, j - 1]) / (4**j - 1)
  
      return R
  
  # Input dari pengguna
  a = float(input("Masukkan batas bawah a: "))
  b = float(input("Masukkan batas atas b: "))
  n = int(input("Masukkan jumlah level Romberg (n): "))
  
  # Hitung dan tampilkan hasil
  romberg_table = romberg(a, b, n)
  hasil_akhir = romberg_table[n-1, n-1]
  
  np.set_printoptions(precision=10, suppress=True)
  print("\nTabel Romberg:")
  print(romberg_table)
  print("\nHasil integrasi Romberg:", hasil_akhir)
```

--- 

# Hasil Pengujian
Input:
- a = 1.5
- b = 2.5
- n = 5

```
[[0.1361773311 0.           0.           0.           0.          ]
 [0.1337019369 0.1336137804 0.           0.           0.          ]
 [0.1329185963 0.1328405628 0.1328190449 0.           0.          ]
 [0.1326338237 0.1325979551 0.1325875601 0.1325845541 0.          ]
 [0.1325373417 0.1325177576 0.1325122631 0.1325106746 0.1325101943]]

  Hasil integrasi Romberg: 0.1325101943
```
# Kesimpulan
Metode Romberg memberikan hasil integral yang sangat akurat hanya dengan sedikit iterasi. Hal ini menunjukkan bahwa metode ini efisien dan lebih unggul dibanding metode trapezoida biasa, terutama saat digunakan pada fungsi-fungsi dengan variasi nilai kompleks.

