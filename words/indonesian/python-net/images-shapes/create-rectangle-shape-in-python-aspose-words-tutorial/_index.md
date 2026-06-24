---
category: general
date: 2026-06-21
description: Buat bentuk persegi panjang di Python menggunakan Aspose.Words. Pelajari
  cara menambahkan bayangan pada bentuk, mengatur warna isi bentuk, dan menyimpan
  dokumen sebagai PDF dalam hitungan menit.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: id
og_description: Buat bentuk persegi panjang di Python dengan Aspose.Words. Panduan
  ini menunjukkan cara menambahkan bayangan ke bentuk, mengatur warna isi bentuk,
  dan menyimpan dokumen sebagai PDF.
og_title: Buat bentuk persegi panjang di Python – tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Buat bentuk persegi panjang di Python – tutorial Aspose.Words
url: /id/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang di Python – Tutorial Aspose.Words

Pernah bertanya-tanya **bagaimana cara membuat bentuk persegi panjang** dalam dokumen Word saat Anda menulis kode di Python? Anda bukan satu-satunya. Banyak pengembang menemui kebuntuan ketika mereka membutuhkan elemen visual cepat—seperti kotak berwarna dengan bayangan halus—dan kemudian mengekspor seluruhnya sebagai PDF.  

Dalam panduan ini kami akan menelusuri contoh lengkap yang dapat dijalankan yang **membuat bentuk persegi panjang**, **mengatur warna isi bentuk**, **menambahkan bayangan ke bentuk**, dan akhirnya **menyimpan dokumen sebagai PDF**. Tanpa referensi yang samar, hanya kode konkret yang dapat Anda salin‑tempel dan jalankan hari ini.

## Apa yang Anda Butuhkan

Sebelum kita mulai, pastikan Anda memiliki hal‑hal berikut di mesin Anda:

- Python 3.8 atau lebih baru (sintaks yang kami gunakan bekerja pada versi terbaru apa pun).
- Lisensi Aspose.Words for Python yang aktif atau percobaan gratis (perpustakaan ini murni‑Python, tidak memerlukan interop COM).
- Editor teks atau IDE yang Anda nyaman gunakan—VS Code bekerja dengan baik, tetapi apa saja dapat dipakai.

Itu saja. Tanpa kerangka kerja berat, tanpa ketergantungan tingkat OS tambahan. Mari kita mulai.

## Langkah 1: Instal Aspose.Words untuk Python

Hal pertama yang harus dilakukan. Jika Anda belum melakukannya, ambil paketnya dari PyPI:

```bash
pip install aspose-words
```

Mengapa langkah ini penting: Aspose.Words menyediakan kelas `Document` dan `DocumentBuilder` yang akan kita gunakan. Tanpa perpustakaan ini, tidak ada panggilan selanjutnya—seperti `insert_shape`—yang ada, sehingga skrip akan gagal sebelum bahkan menggambar satu garis pun.

> **Pro tip:** Jaga lingkungan virtual Anda tetap rapi. Jalankan `python -m venv .venv && source .venv/bin/activate` sebelum menginstal, sehingga perpustakaan tetap terisolasi dari paket sistem.

## Langkah 2: Buat Dokumen Baru dan DocumentBuilder

Sekarang kita benar‑benar **membuat bentuk persegi panjang** – tetapi pertama-tama kita membutuhkan kanvas kosong.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

Objek `Document` mewakili seluruh file, sementara `DocumentBuilder` adalah pembantu praktis yang mengetahui posisi kursor dan dapat menyisipkan elemen pada titik tersebut. Anggap builder sebagai pena yang menulis di halaman.

## Langkah 3: Sisipkan Bentuk Persegi Panjang

Di sinilah aksi utama terjadi. Kami akan **membuat bentuk persegi panjang** dengan lebar dan tinggi tetap, lalu menempatkannya di halaman.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Mengapa persegi panjang? Itu adalah bentuk paling sederhana yang tetap memungkinkan kami menampilkan warna isi dan bayangan. Jika Anda membutuhkan lingkaran atau bintang nanti, cukup ganti `ShapeType.RECTANGLE` dengan nilai enum lain.

## Langkah 4: Atur Warna Isi Bentuk

Kotak putih polos tidak terlalu menarik, jadi mari **atur warna isi bentuk** ke sesuatu yang lembut—biru muda cocok untuk laporan.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Anda dapat menggunakan salah satu anggota `aw.Color` yang telah ditentukan (`red`, `green`, `dark_gray`, dll.) atau memberikan tuple RGB (`aw.Color.from_argb(255, 30, 144, 255)`). Warna isi adalah apa yang dilihat pengguna sebelum bayangan atau border diterapkan.

## Langkah 5: Tambahkan Bayangan ke Bentuk

Sekarang untuk sentuhan visual: **tambahkan bayangan ke bentuk**. Bayangan memberikan kedalaman dan membuat persegi panjang menonjol di halaman.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Bagaimana menambahkan bayangan**? Kode di atas melakukannya tepat, tetapi mari kita uraikan mengapa setiap properti penting:

- `visible` – mengaktifkan/mematikan efek.
- `color` – menentukan warna; abu‑abu gelap meniru pencahayaan alami.
- `blur` – nilai yang lebih tinggi menghasilkan tepi yang lebih lembut.
- `offset_x` / `offset_y` – memindahkan bayangan menjauh dari bentuk; sesuaikan ini untuk mensimulasikan sudut cahaya yang berbeda.
- `transparency` – 0 berarti solid, 1 tidak terlihat; 0.2 memberikan kesan halus.
- `type` – `OUTER` menempatkan bayangan di luar bentuk, sementara `INNER` akan menempatkannya di dalam.

Jika Anda pernah membutuhkan bayangan jatuh yang dramatis, tingkatkan `blur` menjadi 10‑15 dan naikkan `offset_x`/`offset_y` menjadi 6‑8.

## Langkah 6: Simpan Dokumen sebagai PDF

Semua kerja keras itu tidak berguna kecuali kita dapat **menyimpan dokumen sebagai PDF** dan membagikannya. Aspose.Words menjadikannya satu baris kode:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Mengapa PDF? PDF mempertahankan tata letak di semua platform, menjadikannya ideal untuk laporan, faktur, atau materi cetak apa pun. Metode `save` secara otomatis mendeteksi ekstensi file dan memilih format yang tepat—pastikan jalur berakhir dengan `.pdf`.

### Hasil yang Diharapkan

Buka `ShapeWithShadow.pdf` yang dihasilkan dan Anda akan melihat persegi panjang biru muda yang terpusat di dekat bagian atas halaman pertama, dengan bayangan abu‑abu gelap yang lembut sedikit bergeser ke kanan dan ke bawah. Tepi bentuk tajam, bayangannya halus, dan ukuran file biasanya di bawah 100 KB.

## Bonus: Menyesuaikan Bayangan – Jawaban untuk “bagaimana menambahkan bayangan”

Anda mungkin bertanya, *“Bisakah saya mengubah arah bayangan tanpa memindahkan bentuk?”* Tentu saja. Posisi bayangan terpisah dari koordinat bentuk; cukup sesuaikan `offset_x` dan `offset_y`. Nilai positif menggerakkan bayangan ke kanan/bawah, nilai negatif menggerakkannya ke kiri/atas. Untuk sumber cahaya dari kiri‑atas, gunakan `offset_x = -3` dan `offset_y = -3`.

Pertanyaan lain yang sering muncul: *“Bagaimana jika saya membutuhkan beberapa bayangan pada bentuk yang sama?”* Aspose.Words hanya mendukung satu bayangan per bentuk. Jika Anda memerlukan efek berlapis, buat bentuk duplikat, geser sedikit, dan terapkan bayangan berbeda pada masing‑masing. Ini agak hacky, tapi berhasil.

## Skrip Lengkap – Siap Dijalan

Di bawah ini adalah skrip lengkap yang berdiri sendiri. Salin ke file bernama `create_rectangle_with_shadow.py` dan jalankan dengan `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Catatan:** Ganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif yang ada di mesin Anda. Jika folder tidak ada, Python akan mengeluarkan `FileNotFoundError`.

## Kesalahan Umum & Cara Menghindarinya

| Masalah | Mengapa Terjadi | Solusi |
|---------|----------------|--------|
| Bayangan tidak muncul | `shadow.visible` dibiarkan default `False` | Pastikan `shadow.visible = True` |
| Bentuk tidak terlihat | Warna isi diatur ke `aw.Color.transparent` atau `None` | Gunakan warna solid seperti `aw.Color.light_blue` |
| PDF kosong | Lupa memanggil `doc.save` atau menyimpan dengan ekstensi yang salah | Panggil `doc.save("output.pdf")` dan pastikan pathnya benar |
| Kesalahan runtime `ImportError` | Aspose.Words tidak terinstal atau lingkungan Python salah | Jalankan `pip install aspose-words` di dalam venv yang aktif |

## Langkah Selanjutnya – Jelajahi Lebih Banyak Bentuk dan Pemformatan

Sekarang Anda telah menguasai **membuat bentuk persegi panjang**, Anda dapat:

- Ganti `ShapeType.RECTANGLE` dengan `ShapeType.ELLIPSE` atau `ShapeType.PENTAGON` untuk bereksperimen dengan geometri lain.
- Tambahkan teks di dalam bentuk menggunakan `builder.move_to(rectangle.absolute_position)` dan kemudian `builder.writeln("Hello World")`.
- Gabungkan beberapa bentuk menjadi satu grup dengan `group = aw.drawing.GroupShape(doc)` untuk diagram yang kompleks.
- Ekspor ke format lain seperti DOCX (`doc.save("output.docx")`) atau HTML (`doc.save("output.html")`) untuk melihat bagaimana bayangan diterjemahkan.

Setiap ekstensi ini dibangun di atas konsep inti yang sama: **tambahkan bayangan ke bentuk**, **atur warna isi bentuk**, dan **simpan dokumen sebagai PDF** (atau format lain).

---

### Pratinjau Gambar *(opsional)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*Cuplikan layar menunjukkan output PDF akhir dengan persegi panjang biru muda dan bayangan luar yang halus.*

---

## Kesimpulan

Kami telah menelusuri setiap langkah yang diperlukan untuk **membuat bentuk persegi panjang** di Python, menerapkan isi khusus, **menambahkan bayangan ke bentuk**, dan akhirnya **menyimpan dokumen sebagai PDF**. Kode sepenuhnya dapat dijalankan, penjelasan mencakup *mengapa* di balik setiap properti, dan kami telah menyentuh kasus tepi umum serta langkah selanjutnya‑


## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}