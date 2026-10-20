---
category: general
date: 2026-06-24
description: Cara mengatur callback untuk mengekspor gambar dari DOCX saat menyimpan
  sebagai Markdown. Pelajari cara mengekstrak gambar, mengekstrak SVG dari Word, dan
  menyimpan DOCX sebagai Markdown dengan penanganan khusus.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: id
og_description: Cara mengatur callback untuk mengekspor gambar dari DOCX saat mengonversi
  ke Markdown. Panduan ini menunjukkan cara mengekstrak gambar dan SVG secara efisien.
og_title: Cara Mengatur Callback untuk Mengekspor Gambar dari DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: Cara Menetapkan Callback untuk Mengekspor Gambar dari DOCX
url: /id/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menetapkan Callback untuk Mengekspor Gambar dari DOCX

Pernah bertanya-tanya **bagaimana cara menetapkan callback** sehingga Anda dapat **mengekspor gambar dari DOCX** saat mengonversinya ke Markdown? Anda bukan satu-satunya. Banyak pengembang mengalami kebuntuan ketika konversi default menumpahkan semua gambar ke dalam folder umum atau, lebih buruk lagi, kehilangan grafik SVG sepenuhnya.  

Dalam tutorial ini kami akan membahas solusi lengkap yang siap dijalankan yang menjawab pertanyaan “bagaimana cara menetapkan callback”, menunjukkan **cara mengekstrak gambar**, dan bahkan mencakup **ekstraksi SVG dari Word**. Pada akhir tutorial Anda akan dapat **menyimpan DOCX sebagai Markdown** dengan skema penamaan khusus untuk setiap sumber gambar—tanpa perlu mengatur secara manual.

## Apa yang Akan Anda Pelajari

- Mengapa callback adalah cara paling bersih untuk mengontrol nama file gambar selama konversi.  
- Cara mengaitkan ke `MarkdownSaveOptions.resource_saving_callback` milik Aspose.Words.  
- Kode langkah‑demi‑langkah yang mengekstrak **PNG**, **JPG**, **SVG**, dan sumber daya tersemat lainnya.  
- Tips untuk menangani benturan nama, file besar, dan keanehan jalur lintas‑platform.  

> **Pro tip:** Jika Anda sudah menggunakan Aspose.Words dalam pipeline yang lebih besar, Anda dapat menambahkan callback ini tanpa mengubah kode lainnya.

![Diagram cara menetapkan callback](https://example.com/images/how-to-set-callback.png "cara menetapkan callback")

## Prasyarat

- Python 3.8+ (contoh menggunakan f‑strings, jadi 3.6+ sudah cukup).  
- `aspose-words` package terinstal (`pip install aspose-words`).  
- File DOCX yang berisi gambar raster **dan** grafik vektor (SVG).  
- Pemahaman dasar tentang fungsi Python dan I/O file.

Jika Anda sudah memiliki semuanya, mari kita mulai.

## Cara Menetapkan Callback untuk Mengekspor Gambar dari DOCX

Inti solusi berada dalam **callback penyimpanan sumber daya**. Aspose.Words memanggil delegasi ini untuk setiap gambar atau SVG yang ingin ditulis ketika Anda memanggil `document.save`. Dengan mengembalikan tuple `(new_name, data)` Anda menentukan nama file serta payload byte.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Mengapa Callback?

Tanpa callback, Aspose.Words membuat file dengan nama `image1.png`, `image2.svg`, dll., dan menempatkannya di folder sebelah file Markdown. Ini cukup untuk demo cepat, tetapi dalam produksi Anda sering membutuhkan:

1. **Nama deterministik** – berguna untuk kontrol versi atau publikasi CDN.  
2. **Menghindari benturan** – dua gambar dengan nama asli yang sama tidak akan menimpa satu sama lain.  
3. **Struktur folder khusus** – mungkin Anda ingin semua aset berada di bawah `/assets/docs/`.

Callback memberi Anda kontrol penuh atas tiga hal tersebut.

---

## Mengekspor Gambar dari DOCX Menggunakan Callback Sumber Daya

Berikut adalah implementasi callback. Ia menghasilkan hash dari data biner untuk menghasilkan sufiks unik, mempertahankan ekstensi file asli, dan mengembalikan nama file baru bersama dengan byte mentah.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Penanganan Kasus Tepi

- **File besar:** SHA‑256 berfungsi baik untuk ukuran apa pun; hash dihitung di memori, jadi perhatikan batas memori jika Anda memproses PDF yang sangat besar.  
- **Ekstensi hilang:** Beberapa file Word lama mungkin menyimpan gambar tanpa ekstensi eksplisit. Dalam kasus tersebut `extension` akan kosong; Anda dapat menggunakan default `.bin` atau memeriksa beberapa byte pertama untuk menebak formatnya.  
- **Sumber daya non‑gambar:** Callback dipanggil untuk setiap sumber daya eksternal (mis., objek OLE). Jika Anda hanya peduli pada gambar/SVG, filter berdasarkan `resource.type` sebelum melanjutkan.

---

## Cara Mengekstrak Gambar dan SVG dari Word

Sekarang kami menghubungkan callback ke pipeline penyimpanan Markdown. Objek `MarkdownSaveOptions` menyediakan properti `resource_saving_callback` tepat untuk tujuan ini.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Menetapkan `resource_folder` bersifat opsional tetapi sering berguna. Jika Anda mengabaikannya, gambar akan berada di sebelah file Markdown, yang dapat membuat akar proyek Anda berantakan.

### Saving the Document

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

When you run the script, you’ll see a series of files like:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

And the generated `output.md` will contain image links that point to those exact filenames:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Itulah bagian **cara mengekstrak gambar** yang beraksi—setiap gambar, raster atau vektor, kini menjadi aset terpisah dengan nama unik.

---

## Simpan DOCX sebagai Markdown dengan Penanganan Gambar Kustom

Menggabungkan semuanya, berikut skrip lengkap yang dapat Anda salin‑tempel ke file bernama `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Mengapa ini berhasil:**  
- `resource_callback` menjamin setiap gambar mendapatkan nama yang unik dan dapat direproduksi.  
- `resource_folder` menjaga Markdown tetap rapi dengan memisahkan aset.  
- Panggilan `os.makedirs` melindungi Anda dari error “folder tidak ditemukan” ketika skrip dijalankan pada mesin baru.

---

## Ekstrak SVG dari Word – Bagaimana dengan Grafik Vektor?

SVGs diperlakukan sama seperti PNGs oleh callback karena mereka hanyalah `resource` lain. Nuansa satu-satunya adalah bahwa beberapa versi Word lama menyematkan SVG sebagai objek *OfficeArt*, yang secara otomatis dikonversi Aspose.Words menjadi PNG raster kecuali Anda secara eksplisit mengaktifkan flag **preserve SVG**:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Tambahkan baris itu sebelum menyimpan, dan callback akan menerima sumber daya dengan ekstensi `.svg`, mempertahankan data vektor yang tajam—sempurna untuk dokumen web responsif.

---

## Pertanyaan Umum & Hal-hal yang Perlu Diwaspadai

| Question | Answer |
|----------|--------|
| **Bagaimana jika dua gambar identik?** | Hash SHA‑256 akan identik, sehingga nama file bentrok. Jika Anda membutuhkan kedua salinan, sertakan `resource.name` asli dalam perhitungan hash (mis., `hash(resource.name + resource.data)`). |
| **Bisakah saya mengubah folder per tipe file?** | Ya. Di dalam `resource_callback` Anda dapat memeriksa `extension` dan mengembalikan path seperti `f"png/{new_name}"` untuk gambar raster dan `f"svg/{new_name}"` untuk vektor. |
| **Apakah ini bekerja di Linux/macOS?** | Tentu saja. Kode menggunakan `os.path` yang mengabstraksi pemisah jalur. Pastikan Anda memiliki file lisensi Aspose.Words (`aspose.words.lic`) yang dapat diakses jika Anda menggunakan versi berbayar. |
| **Bagaimana dengan penggunaan memori untuk dokumen besar?** | Callback menerima **array byte penuh** untuk setiap sumber daya, yang berarti seluruh gambar berada di memori sementara. Untuk file multi‑gigabyte Anda mungkin ingin men‑stream data ke disk di dalam callback alih‑alih mengembalikannya. |

---

## Kesimpulan

Anda kini tahu **cara menetapkan callback** untuk mengontrol ekstraksi gambar ketika Anda **menyimpan DOCX sebagai Markdown**. Pendekatan ini memungkinkan Anda **mengekspor gambar dari DOCX**, **mengekstrak SVG dari Word**, dan menjaga Markdown Anda tetap bersih serta deterministik.  

Dalam satu skrip mandiri kami mencakup pemuatan dokumen, mendefinisikan callback penyimpanan sumber daya, mengonfigurasi `MarkdownSaveOptions`, dan menangani kasus tepi seperti benturan nama dan grafik vektor. Hasilnya adalah sekumpulan aset dengan nama unik berdampingan dengan file Markdown yang terhubung sempurna—siap untuk generator situs statis, pipeline dokumentasi, atau alur kerja apa pun yang membutuhkan aset bersih dan dapat digunakan kembali.  

**Langkah selanjutnya?**  
- Coba menggabungkan ini dengan generator situs statis seperti MkDocs untuk secara otomatis mempublikasikan dokumen berbasis Word.  
- Bereksperimen dengan `markdown_options.export_images_as_base64 = True` jika Anda lebih suka gambar inline daripada file eksternal.  
- Selami lebih dalam callback lain Aspose.Words (mis., `document_saving_callback`) untuk mengontrol output Markdown itu sendiri.  

Ada pertanyaan lebih lanjut tentang **cara mengekstrak gambar** dari format Office lainnya, atau butuh bantuan menyesuaikan callback untuk konvensi penamaan tertentu? Tinggalkan komentar di bawah, dan selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara Mengubah Nama Gambar Saat Mengonversi DOCX ke Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [Cara Menyimpan Markdown dari DOCX – Panduan Langkah‑demi‑Langkah](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}