---
category: general
date: 2026-09-27
description: Pelajari cara mengatur bayangan pada bentuk dengan Aspose.Words untuk
  Python. Panduan ini mencakup menambahkan bayangan ke bentuk, menerapkan efek bayangan,
  dan mengatur warna bayangan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: id
lastmod: 2026-09-27
og_description: Cara mengatur bayangan pada bentuk menggunakan Aspose.Words untuk
  Python. Ikuti panduan langkah demi langkah untuk menambahkan bayangan pada bentuk,
  menerapkan efek bayangan, dan mengatur warna bayangan.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Cara mengatur bayangan pada bentuk di Aspose.Words untuk Python
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Cara mengatur bayangan pada bentuk di Aspose.Words untuk Python
url: /id/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengatur bayangan pada bentuk di Aspose.Words untuk Python

Jika Anda perlu **cara mengatur bayangan** untuk objek gambar, panduan ini menunjukkan proses lengkapnya. Anda akan melihat cara menambahkan bayangan ke bentuk, mengonfigurasi blur, offset, dan warna bayangan, serta menyimpan dokumen yang diperbarui tanpa meninggalkan kode.

Tutorial ini mengasumsikan Anda sudah memiliki lingkungan Aspose.Words untuk Python dasar. Pada akhir artikel Anda akan dapat menerapkan efek bayangan yang tampak profesional pada bentuk apa pun dalam file DOCX.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Python 3.8+ terinstal.
* Aspose.Words untuk Python via .NET (`pip install aspose-words`) terinstal.
* Dokumen Word (`input.docx`) yang berisi setidaknya satu bentuk (misalnya, persegi panjang atau gambar).  
  Jika dokumen kosong, kode akan membuat bentuk baru untuk demonstrasi.

Item-item ini menjamin bahwa langkah-langkah berikutnya dapat dijalankan tanpa kesalahan impor.

## Langkah 1: Muat atau buat dokumen Word

Operasi pertama adalah memperoleh objek `Document`. Anda dapat memuat file yang ada atau membuat yang baru.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*Mengapa langkah ini penting*: Objek `Document` adalah titik masuk untuk semua operasi pengolahan Word. Tanpa itu Anda tidak dapat mengakses bentuk atau menerapkan efek visual.

## Langkah 2: Dapatkan bentuk target

Untuk memanipulasi tampilan bentuk, Anda memerlukan referensi ke node bentuk. Contoh di bawah mengambil bentuk pertama yang ditemukan dalam hierarki dokumen.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*Mengapa langkah ini penting*: `add shadow to shape` memerlukan objek bentuk yang konkret. Kode menangani dengan aman kasus tepi di mana dokumen tidak berisi bentuk apa pun, memastikan tutorial ini berfungsi untuk setiap pembaca.

## Langkah 3: Konfigurasikan tampilan bayangan

Sekarang Anda dapat **menerapkan efek bayangan** dengan menyesuaikan properti `shadow` pada bentuk. Pengaturan berikut memberikan bayangan halus dan gelap.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*Mengapa setiap properti penting*:

| Properti | Efek |
|----------|--------|
| `blur`   | Mengontrol seberapa kabur bayangan terlihat. |
| `offset_x` / `offset_y` | Menentukan arah dan jarak dari bentuk. |
| `color`  | Menentukan warna bayangan; Anda dapat menggunakan `aw.Color` apa pun. |
| `visible`| Memastikan bayangan dirender dalam file output. |

Anda dapat mengganti `aw.Color.black` dengan `aw.Color.from_argb(255, 0, 0, 0)` untuk nilai RGBA kustom, atau warna bawaan lainnya.

## Langkah 4: Simpan dokumen yang dimodifikasi

Setelah mengonfigurasi bayangan, simpan perubahan ke file baru.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

Saat Anda membuka `output.docx` di Microsoft Word, bentuk yang dipilih akan menampilkan bayangan hitam lembut yang dipindahkan 2 pt ke kanan dan 2 pt ke bawah.

## Contoh lengkap yang berfungsi

Menggabungkan semua langkah menghasilkan skrip mandiri yang dapat Anda salin‑tempel ke IDE Anda.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

Menjalankan skrip menghasilkan `output.docx` di mana bentuk pertama memiliki bayangan yang telah dikonfigurasi.

## Kesalahan umum dan cara menghindarinya

| Masalah | Alasan | Solusi |
|-------|--------|-----|
| `shape` adalah `None` bahkan setelah memuat dokumen | Dokumen tidak berisi objek gambar. | Gunakan blok pembuatan bentuk cadangan yang ditampilkan pada Langkah 2. |
| Bayangan tidak muncul di Word | `shape.shadow.visible` dibiarkan `False` atau dokumen disimpan dalam format lama (mis., `.doc`). | Pastikan `visible = True` dan simpan sebagai `.docx`. |
| Warna terlihat berbeda dari yang diharapkan | Tema dokumen menimpa warna eksplisit. | Setel `shape.shadow.color` setelah menonaktifkan penimpaan tema, atau gunakan `aw.Color.from_argb`. |

Menangani kasus tepi ini membuat solusi menjadi kuat untuk kode produksi.

## Memperluas efek (langkah selanjutnya)

Sekarang Anda tahu **cara menambahkan bayangan**, Anda dapat menjelajahi peningkatan terkait:

* **apply shadow effect** dengan gradien atau beberapa bayangan dengan menyesuaikan sub‑properti `shape.shadow`.
* Gunakan **set shadow color** secara dinamis berdasarkan input pengguna atau warna tema.
* Gabungkan **add shadow to shape** dengan tindakan pemformatan lain seperti rotasi, gaya garis, atau efek 3‑D.
* Otomatisasi penambahan bayangan untuk setiap bentuk dalam dokumen dengan mengiterasi `doc.get_child_nodes(aw.NodeType.SHAPE, True)`.

Ekstensi ini memungkinkan Anda membangun pipeline pembuatan dokumen yang canggih yang menghasilkan output yang halus dan konsisten secara visual.

## Kesimpulan

Anda kini memiliki solusi lengkap dan dapat dijalankan untuk **cara mengatur bayangan** pada bentuk menggunakan Aspose.Words untuk Python. Panduan ini mencakup memuat dokumen, mengambil atau membuat bentuk, mengonfigurasi blur, offset, dan **set shadow color**, serta akhirnya menyimpan file. Terapkan pola ini pada bentuk apa pun dalam proyek otomatisasi Anda dan bereksperimen dengan penyesuaian visual tambahan untuk memenuhi kebutuhan desain Anda.

--- 

*Silakan sesuaikan kode untuk tipe bentuk lain, warna, atau nilai offset. Jika Anda menemukan masalah, meninjau tabel “Kesalahan umum” adalah langkah pertama yang baik.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menambahkan bayangan ke bentuk di C# – Panduan Lengkap untuk Menerapkan Efek Bayangan](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Menambahkan bayangan ke bentuk di Word – Panduan Lengkap Aspose.Words](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Buat bentuk persegi panjang, tambahkan bayangan & simpan PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}