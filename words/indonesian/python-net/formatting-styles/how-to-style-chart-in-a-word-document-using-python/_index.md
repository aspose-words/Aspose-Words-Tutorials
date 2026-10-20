---
category: general
date: 2026-08-11
description: Cara menata gaya grafik dalam dokumen Word menggunakan Python – memuat
  dokumen Word dengan Python dan menerapkan gaya grafik yang telah ditentukan dengan
  cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style chart
- load word document python
- apply predefined chart style
- apply chart style word
language: id
lastmod: 2026-08-11
og_description: Cara menata grafik dalam dokumen Word menggunakan Python. Pelajari
  cara memuat dokumen Word dengan Python, menerapkan gaya grafik yang telah ditentukan,
  dan menyimpan file yang telah diperbarui.
og_image_alt: Screenshot of Python code applying a chart style to a Word document
og_title: Cara menata grafik di Word dengan Python – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: How to style chart in a Word document using Python – load Word document
    python and apply predefined chart style quickly.
  headline: How to style chart in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Chart styling
- Word automation
title: Cara menata grafik dalam dokumen Word menggunakan Python
url: /id/python/formatting-styles/how-to-style-chart-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memberi gaya pada chart di dokumen Word menggunakan Python

Jika Anda perlu **how to style chart** dalam file Word, tutorial ini menunjukkan langkah-langkah tepatnya. Pada akhir dua kalimat pertama Anda akan tahu cara memuat dokumen Word dengan Python, mengambil chart, dan menerapkan gaya chart yang telah ditentukan. Solusi ini bekerja dengan pustaka Aspose.Words untuk Python dan tidak memerlukan penyuntingan manual dokumen.

Anda akan belajar cara **load word document python**, memilih shape chart pertama, menetapkan gaya bawaan, dan menyimpan file yang telah dimodifikasi. Panduan ini juga mencakup jebakan umum, seperti menangani dokumen tanpa chart dan memilih enumerasi gaya yang tepat. Tidak ada alat eksternal yang diperlukan selain paket Aspose.Words.

## Cara memberi gaya pada chart di dokumen Word menggunakan Python

Menerapkan gaya pada chart adalah operasi satu baris setelah Anda memiliki objek `Chart`. Pustaka ini menyediakan enumerasi `ChartStyle`, yang berisi puluhan tampilan yang telah ditentukan (Style 1 … Style 50). Pada bagian ini kami menetapkan **Style 5**, tetapi Anda dapat mengganti nilai enum dengan gaya apa pun yang sesuai dengan pedoman desain Anda.

```python
import aspose.words as aw

# Load the Word document that contains a chart
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# Retrieve the first chart shape in the document
chart_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
chart = chart_shape.as_chart()

# Apply a predefined chart style (Style 5) to the chart
chart.style = aw.drawing.ChartStyle.STYLE_5

# Save the modified document
doc.save("YOUR_DIRECTORY/output.docx")
```

**Mengapa ini berhasil:**  
- `aw.Document` mengurai file .docx dan membangun model objek.  
- `get_child(..., aw.NodeType.SHAPE, ...)` menemukan shape pertama, yang merupakan kontainer chart.  
- `as_chart()` mengubah shape menjadi objek `Chart`, memperlihatkan properti `style`.  
- Menetapkan `ChartStyle.STYLE_5` memberi tahu Aspose.Words untuk mengganti tema visual chart dengan definisi yang telah ditentukan.

File output `output.docx` berisi data yang sama dengan yang asli tetapi chart ditampilkan menggunakan gaya yang dipilih.

## Memuat dokumen Word di Python

Sebelum Anda dapat memberi gaya pada chart, Anda harus **load word document python** dengan benar. Konstruktor `aw.Document` menerima path ke file .docx, .doc, atau .rtf. Pastikan path file bersifat absolut atau direktori kerja mengarah ke lokasi file input Anda.

```python
# Example: absolute path on Windows
doc_path = r"C:\Projects\Charts\input.docx"
doc = aw.Document(doc_path)
```

**Tips untuk memuat dokumen:**  
- Gunakan string mentah (`r"..."`) di Windows untuk menghindari escape backslash.  
- Verifikasi bahwa file ada dengan `os.path.isfile(doc_path)` untuk mencegah error runtime.  
- Jika dokumen berisi bagian yang dilindungi, berikan password melalui `aw.LoadOptions`.

```python
import os
if not os.path.isfile(doc_path):
    raise FileNotFoundError(f"Document not found: {doc_path}")
```

## Terapkan gaya chart yang telah ditentukan

Langkah **apply predefined chart style** adalah tempat transformasi visual terjadi. Aspose.Words mendefinisikan enum `ChartStyle` dengan nilai mulai dari `STYLE_1` hingga `STYLE_50`. Setiap gaya memetakan sekumpulan warna, penanda, dan format garis yang meniru tema chart bawaan Microsoft Office.

```python
# Choose any style from STYLE_1 to STYLE_50
desired_style = aw.drawing.ChartStyle.STYLE_12
chart.style = desired_style
```

**Kapan menggunakan gaya yang telah ditentukan:**  
- Anda membutuhkan tampilan konsisten di banyak dokumen.  
- Data chart sering berubah, tetapi tema visual harus tetap tetap.  
- Anda ingin menghindari pemformatan manual di UI Word.

**Kasus tepi – dokumen tanpa chart:**  
Jika `doc.get_child(aw.NodeType.SHAPE, 0, True)` mengembalikan `None`, skrip akan menghasilkan `AttributeError`. Lindungi dari hal ini dengan memeriksa tipe node sebelum melakukan casting.

```python
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart found in the document.")
chart = shape.as_chart()
```

## Simpan dokumen yang telah diberi gaya

Setelah memberi gaya, menyimpan perubahan menjadi mudah. Metode `doc.save` menulis model objek yang diperbarui kembali ke file .docx. Anda juga dapat mengekspor ke format lain seperti PDF, HTML, atau PNG jika konsumsi selanjutnya memerlukan representasi yang berbeda.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)          # Saves as DOCX
doc.save("output.pdf")         # Optional: export to PDF
```

**Verifikasi:** Buka `output.docx` di Microsoft Word. Chart harus menampilkan tema baru, dan setiap seri data mempertahankan nilai aslinya. Jika Anda mengekspor ke PDF, gaya visual tetap identik.

## Jebakan umum dan tips praktis

| Masalah | Penyebab | Solusi |
|-------|-------|-----|
| `AttributeError: 'NoneType' object has no attribute 'as_chart'` | Tidak ada shape chart yang ditemukan pada indeks 0 | Gunakan `doc.get_child(..., 0, True)` dalam blok try/except atau iterasi semua shape dengan `doc.get_child_nodes(aw.NodeType.SHAPE, True)`. |
| Gaya salah diterapkan | Menggunakan nilai enum yang tidak ada (mis., `STYLE_0`) | Pilih nilai `ChartStyle` yang valid (1‑50). |
| File tidak tersimpan | Path output mengarah ke direktori hanya-baca | Pastikan proses memiliki izin menulis atau ubah direktori. |
| Chart menghilang setelah disimpan | Shape bukan chart (mis., gambar) | Verifikasi `shape.has_chart` sebelum casting. |

**Pro tip:** Cache `ChartStyle` yang paling sering Anda gunakan dalam sebuah konstanta sehingga Anda dapat menggunakannya kembali di banyak skrip tanpa mengetik enum setiap kali.

```python
DEFAULT_CHART_STYLE = aw.drawing.ChartStyle.STYLE_5
chart.style = DEFAULT_CHART_STYLE
```

## Contoh lengkap end‑to‑end

Berikut adalah skrip lengkap yang dapat dijalankan yang menggabungkan semua praktik terbaik yang dibahas di atas. Ganti `YOUR_DIRECTORY` dengan folder sebenarnya yang berisi file Word Anda.

```python
import os
import aspose.words as aw

# ----------------------------------------------------------------------
# Configuration
# ----------------------------------------------------------------------
INPUT_PATH = r"YOUR_DIRECTORY/input.docx"
OUTPUT_PATH = r"YOUR_DIRECTORY/output.docx"
DEFAULT_STYLE = aw.drawing.ChartStyle.STYLE_5

# ----------------------------------------------------------------------
# Load the document
# ----------------------------------------------------------------------
if not os.path.isfile(INPUT_PATH):
    raise FileNotFoundError(f"Input file not found: {INPUT_PATH}")

doc = aw.Document(INPUT_PATH)

# ----------------------------------------------------------------------
# Locate the first chart
# ----------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart shape found in the document.")

chart = shape.as_chart()

# ----------------------------------------------------------------------
# Apply the predefined chart style
# ----------------------------------------------------------------------
chart.style = DEFAULT_STYLE

# ----------------------------------------------------------------------
# Save the modified document
# ----------------------------------------------------------------------
doc.save(OUTPUT_PATH)

print(f"Chart style applied successfully. Saved to {OUTPUT_PATH}")
```

**Hasil yang diharapkan:**  
Saat Anda membuka `output.docx`, chart pertama menampilkan tema visual yang didefinisikan oleh `STYLE_5`. Semua titik data, sumbu, dan legenda tetap tidak berubah, menunjukkan bahwa pemberian gaya independen dari data yang mendasarinya.

## Kesimpulan

Anda sekarang tahu **how to style chart** di dokumen Word menggunakan Python. Tutorial ini mencakup cara **load word document python**, mengambil shape chart, **apply predefined chart style**, dan menyimpan file yang diperbarui. Dengan blok bangunan ini Anda dapat mengotomatiskan pembuatan laporan, menegakkan branding perusahaan, atau memproses batch puluhan dokumen tanpa upaya manual.

Selanjutnya, jelajahi kustomisasi chart lainnya seperti mengubah warna seri, menambahkan label data, atau mengekspor chart sebagai gambar. Lihat dokumentasi Aspose.Words untuk topik seperti **apply chart style word**, **chart data manipulation**, dan **document conversion** untuk memperluas kemampuan otomatisasi Anda.

Silakan bereksperimen dengan nilai `ChartStyle` yang berbeda dan integrasikan skrip ini ke dalam pipeline yang lebih besar yang menghasilkan laporan Word dari basis data atau API. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Masukkan Chart Kolom ke Dokumen Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Masukkan Chart Kolom Sederhana ke Dokumen Word](/words/english/net/programming-with-charts/insert-simple-column-chart/)
- [Masukkan Chart Area ke Dokumen Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}