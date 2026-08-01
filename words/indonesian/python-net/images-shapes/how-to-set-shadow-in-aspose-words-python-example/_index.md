---
category: general
date: 2026-08-01
description: Cara mengatur bayangan pada bentuk Word menggunakan Aspose.Words untuk
  Python. Pelajari cara mengubah opasitas, menyesuaikan blur, dan mengubah jarak bayangan
  dengan cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: id
lastmod: 2026-08-01
og_description: Cara mengatur bayangan pada bentuk dengan Aspose.Words untuk Python.
  Ikuti tutorial langkah demi langkah ini untuk mengubah opasitas, menyesuaikan blur,
  dan mengubah jarak bayangan.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: Cara Menetapkan Bayangan di Aspose.Words – Panduan Python Cepat
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: Cara Mengatur Bayangan di Aspose.Words – Contoh Python
url: /id/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengatur Bayangan di Aspose.Words – Contoh Python

Pernah bertanya-tanya **cara mengatur bayangan** pada bentuk Word tanpa membuka dokumen secara manual? Anda bukan satu-satunya—banyak pengembang mengalami kendala ini saat mengotomatisasi laporan atau membuat templat yang konsisten dengan merek. Kabar baik? Dengan Aspose.Words untuk Python Anda dapat menyesuaikan bayangan bentuk, opasitas, blur, dan jarak hanya dengan beberapa baris kode.

Dalam tutorial ini kami akan membahas contoh lengkap yang dapat dijalankan yang menunjukkan **cara mengatur bayangan**, **cara mengubah opasitas**, **cara menyesuaikan blur**, dan bahkan **mengubah jarak bayangan**. Pada akhir tutorial Anda akan memiliki pemahaman yang kuat tentang **cara menggunakan Aspose.Words** untuk menata bentuk secara programatis.

---

![Cara mengatur bayangan pada bentuk menggunakan Aspose.Words](image-placeholder.png){alt="Cara mengatur bayangan pada bentuk menggunakan Aspose.Words"}

## Prerequisites

Sebelum kita mulai, pastikan Anda memiliki:

| Persyaratan | Alasan |
|-------------|--------|
| Python 3.8+ | Sintaks modern, tipe petunjuk |
| `aspose-words` package (pip install aspose-words) | Pustaka inti untuk manipulasi Word |
| Contoh `input.docx` dengan setidaknya satu bentuk | Bentuk yang akan diberi bayangan |
| Izin menulis ke folder tempat Anda menyimpan `output.docx` | Untuk menyimpan perubahan |

Tidak ada DLL tambahan atau interop COM—Aspose.Words murni‑Python, sehingga Anda dapat menjalankannya di Windows, macOS, atau Linux.

---

## Cara Mengatur Bayangan pada Bentuk dengan Aspose.Words

Berikut adalah skrip **lengkap**. Skrip ini memuat dokumen, menemukan bentuk pertama (secara rekursif), mengonfigurasi bayangan, dan menyimpan hasilnya. Setiap baris diberi komentar sehingga Anda memahami **mengapa** ada, bukan hanya **apa** yang dilakukannya.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### Mengapa Ini Berfungsi

* **`doc.get_child(..., True)`** – Flag `True` memberi tahu Aspose.Words untuk mencari **secara rekursif**, sehingga bahkan bentuk di dalam header, footer, atau objek yang dikelompokkan dapat ditemukan. Ini penting ketika Anda tidak tahu persis di mana bentuk tersebut berada.
* **`shadow_format`** – Properti ini mengelompokkan semua pengaturan terkait bayangan. Dengan mengatur `distance`, `blur`, dan `opacity` Anda mengontrol kedalaman visual bentuk. Mengubah nilai-nilai ini menunjukkan **cara mengubah opasitas**, **cara menyesuaikan blur**, dan **mengubah jarak bayangan** dalam satu panggilan yang kohesif.
* **Menyimpan** – `doc.save` menulis file `.docx` baru. Dokumen asli tetap tidak tersentuh, yang merupakan pola aman untuk pemrosesan batch.

---

## Cara Mengubah Opasitas Bayangan Bentuk

Opasitas menentukan seberapa tembus pandang bayangan terlihat. Rentangnya 0.0 (sepenuhnya tidak terlihat) hingga 1.0 (sepenuhnya padat). Pada kode di atas Anda cukup memodifikasi argumen `opacity`:

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **Tip profesional:** Saat menghasilkan PDF nanti, opasitas yang lebih tinggi biasanya menghasilkan bayangan yang lebih dalam dan lebih mudah dicetak. Bereksperimenlah dengan nilai antara 0.4 dan 0.9 untuk menemukan titik optimal sesuai pedoman merek Anda.

---

## Cara Menyesuaikan Blur untuk Tampilan Lebih Lembut

Blur adalah radius Gaussian blur yang diterapkan pada tepi bayangan. Angka yang lebih besar menghasilkan efek berbulu:

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

Jika Anda membutuhkan tampilan bayangan tajam (bayangkan gaya “Microsoft PowerPoint”), atur `blur` ke nilai rendah seperti `1.0`.

---

## Ubah Jarak Bayangan untuk Menciptakan Kedalaman

Jarak diukur dalam poin (1 pt = 1/72 in). Memindahkan bayangan lebih jauh membuat bentuk tampak melayang lebih tinggi:

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

Gabungkan `distance` yang lebih besar dengan `blur` yang sedang untuk efek dramatis, “terangkat”.

---

## Menggabungkan Semua – Proyek Mini

Bayangkan Anda sedang membangun generator laporan otomatis yang menyisipkan logo perusahaan ke dalam kotak teks. Anda menginginkan setiap logo memiliki bayangan halus yang sesuai dengan gaya korporat. Dengan menggunakan fungsi `apply_shadow` Anda dapat:

1. **Buat dokumen** (atau muat templat).
2. **Sisipkan bentuk logo** (melalui `DocumentBuilder.insert_image` atau `Shape`).
3. **Panggil `apply_shadow`** dengan spesifikasi bayangan merek Anda.
4. **Ekspor** ke DOCX, PDF, atau HTML dengan satu baris kode.

Karena fungsi ini menerima parameter, Anda dapat menyimpan pengaturan bayangan dalam file JSON dan menerapkannya pada puluhan dokumen—tanpa perlu penyesuaian manual.

---

## Pertanyaan Umum & Kasus Pojok

| Pertanyaan | Jawaban |
|----------|--------|
| **Bagaimana jika dokumen memiliki banyak bentuk?** | Contoh ini menargetkan *bentuk pertama*. Untuk memengaruhi semua bentuk, lakukan loop dengan `doc.get_child_nodes(aw.NodeType.SHAPE, True)` dan terapkan pengaturan `shadow_format` yang sama pada setiap node. |
| **Bisakah saya mengatur warna bayangan yang berbeda?** | Tentu saja. Gunakan `shape.shadow_format.color = aw.Color(255, 0, 0)` untuk bayangan merah, atau `aw.Color` apa pun yang Anda suka. |
| **Apakah pengaturan ini tetap setelah konversi ke PDF?** | Ya. Aspose.Words mempertahankan properti bayangan saat merender ke PDF, meskipun nilai blur yang sangat tinggi mungkin diperkirakan. |
| **Apakah ada penurunan kinerja untuk dokumen besar?** | API bayangan hanya menyentuh objek bentuk, sehingga bahkan laporan 500‑halaman diproses dalam milidetik. Bottleneck biasanya I/O, bukan konfigurasi bayangan. |
| **Bisakah saya menghapus bayangan nanti?** | Atur `shape.shadow_format.is_visible = False` atau cukup reset properti ke nilai default. |

---

## Ringkasan Contoh Kerja Lengkap

Berikut seluruh skrip lagi, tanpa komentar untuk penyalinan cepat:

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

Jalankan skrip, buka `output.docx`, dan Anda akan melihat bentuk dengan bayangan rapi yang sesuai dengan parameter yang Anda atur.

---

## Kesimpulan

Kami telah membahas **

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Tutorial Bayangan Bentuk Aspose.Words – Menambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Cara Menerapkan Komentar dan Balasan dalam Dokumen Word menggunakan Aspose.Words untuk Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [Cara Mengelola Variabel Dokumen dengan Aspose.Words dalam Python: Panduan Lengkap](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}