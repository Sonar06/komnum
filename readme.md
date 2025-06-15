# Praktikum-1
---
title: "Metode Trapezoidal"
author: "Khairan Cherokee Musthofa"
NRP: 5025241215
---

---
# 📘 Pendahuluan
Metode Romberg adalah teknik numerik untuk menghitung integral tentu berdasarkan metode trapezoida yang disempurnakan dengan teknik ekstrapolasi Richardson. Ekstrapolasi ini digunakan untuk memperbaiki hasil integral numerik dengan menggabungkan pendekatan trapezoida pada berbagai ukuran partisi yang lebih kecil.

Formulasi umum:
- angkah pertama: gunakan metode trapezoida biasa.
- Langkah selanjutnya: bangun tabel Romberg, dengan formula:
  $$
  R[i][j] = R[i][j-1] + (R[i][j-1] - R[i-1][j-1]) / (4^j - 1)
  $$

  ---
