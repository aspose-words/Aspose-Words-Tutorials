---
category: general
date: 2026-06-30
description: Cara mengganti nama gambar saat mengonversi DOCX ke markdown. Pelajari
  cara mengubah nama gambar dan menyimpan Word sebagai markdown dengan nama file gambar
  khusus.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: id
og_description: Cara mengganti nama gambar saat mengonversi DOCX ke markdown. Panduan
  ini menunjukkan cara mengubah nama gambar, menyimpan Word sebagai markdown, dan
  menggunakan nama file gambar khusus.
og_title: Cara Mengganti Nama Gambar Saat Mengonversi DOCX ke Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: Cara Mengganti Nama Gambar Saat Mengonversi DOCX ke Markdown
url: /id/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengganti Nama Gambar Saat Mengonversi DOCX ke Markdown

Pernah bertanya-tanya **bagaimana cara mengganti nama gambar** secara otomatis ketika Anda mengonversi file DOCX ke Markdown? Anda bukan satu-satunya. Dalam banyak alur kerja dokumentasi, nama gambar default (seperti `image1.png`) menjadi mimpi buruk untuk dilacak, terutama ketika markdown yang sama dikontrol versi di antara tim.  

Kabar baiknya, Aspose.Words untuk Python membuatnya sangat mudah untuk **mengubah nama gambar** secara langsung, dan Anda dapat menjaga Markdown tetap bersih sambil mempertahankan folder aset dengan nama khusus yang rapi.  

Dalam tutorial ini Anda akan belajar cara:

* Memuat dokumen Word (`.docx`) di Python.  
* Menyambungkan ke proses penyimpanan Markdown dengan callback yang memberi setiap gambar nama file berbasis GUID.  
* Menyimpan dokumen sebagai Markdown sehingga file yang dihasilkan merujuk pada gambar yang baru dinamai.  

Jika Anda nyaman dengan Python dasar dan telah menginstal Aspose.Words, Anda akan siap dalam kurang dari lima menit. Tanpa skrip eksternal, tanpa penamaan manual—hanya satu program mandiri yang melakukan semua pekerjaan berat untuk Anda.

---

## Prasyarat — Apa yang Anda Butuhkan Sebelum Memulai

| Requirement | Why It Matters |
|-------------|----------------|
| **Python 3.7+** | Contoh ini menggunakan f‑strings dan type hints yang diperkenalkan pada 3.6, tetapi 3.7+ memberikan kemudahan `os.path.splitext`. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | Perpustakaan ini menyediakan kelas `aw.Document` dan `MarkdownSaveOptions` yang kami andalkan. |
| **Write permission** to the output folder | Callback akan membuat file gambar baru, jadi skrip harus diizinkan menulisnya. |
| **A DOCX file** you want to convert | Apa saja, mulai dari laporan sederhana hingga manual kompleks, akan berfungsi. |

> **Pro tip:** Jika Anda menggunakan lingkungan virtual, aktifkan terlebih dahulu sebelum menginstal Aspose.Words. Ini mengisolasi dependensi dan menghindari benturan versi.

---

## Langkah 1: Muat Dokumen Word  

Hal pertama yang Anda lakukan ketika ingin **mengonversi docx ke markdown** adalah membuka file sumber. Aspose.Words mengabstraksi semua penanganan OPC tingkat rendah, sehingga satu baris kode sudah cukup.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Mengapa ini penting:* Tanpa memuat dokumen Anda tidak dapat memeriksa sumber dayanya, dan pengekspor Markdown tidak akan memiliki apa pun untuk ditulis. Objek `aw.Document` menyimpan seluruh paket Word di memori, sehingga aman untuk dimanipulasi sebelum disimpan.

---

## Langkah 2: Tulis Callback yang **Mengganti Nama Sumber Daya Gambar**  

Aspose.Words memungkinkan Anda menyematkan `resource_saving_callback` ke dalam `MarkdownSaveOptions`. Callback menerima setiap sumber daya (gambar, CSS, dll.) tepat sebelum ditulis ke disk. Dengan memodifikasi `resource.file_name` kita dapat menegakkan **nama file gambar khusus**.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### Mengapa Menggunakan GUID?

* **Unik** – GUID (`uuid4`) menjamin dua gambar tidak akan pernah bentrok, bahkan pada beberapa kali menjalankan.  
* **Dapat Dilacak** – Jika Anda perlu melakukan debug nanti, GUID dapat dicatat bersama nomor paragraf Word asli.  
* **Portabel** – Tidak bergantung pada skema penamaan Word asli, yang mungkin mengandung spasi atau karakter khusus yang merusak tautan Markdown.

---

## Langkah 3: Lampirkan Callback ke Markdown Save Options  

Sekarang kami memberi tahu Aspose untuk menggunakan logika penggantian nama kami setiap kali menulis gambar ke folder output.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Penjelasan:* Kelas `MarkdownSaveOptions` mengontrol segala hal mulai dari pemutusan baris hingga lokasi folder gambar. Dengan mengatur `resource_saving_callback`, Anda mendapatkan **hook** yang dipicu untuk setiap sumber daya tersemat, memberi Anda kesempatan untuk **mengubah nama gambar** sebelum file dituliskan ke disk.

---

## Langkah 4: Simpan Dokumen sebagai Markdown – Bagian Akhir  

Dengan callback yang sudah dipasang, langkah akhir menjadi sederhana.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

Saat skrip selesai, Anda akan menemukan:

* `CustomResources.md` – representasi Markdown dari file Word Anda.  
* Folder `images/` (atau apa pun yang Anda tentukan) yang berisi file seperti `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`.  

File Markdown akan merujuk pada nama file berbasis GUID yang baru, sehingga setiap proses downstream (GitHub, MkDocs, dll.) akan mengambil gambar yang tepat tanpa Anda harus menamainya secara manual.

### Output yang Diharapkan (kutipan)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

GUID akan berbeda setiap kali dijalankan, tetapi pola tetap sama.

---

## Menangani Kasus Tepi dan Pertanyaan Umum  

### Bagaimana jika dokumen berisi sumber daya non‑gambar?  

Callback kami sudah memeriksa ekstensi file dan mengembalikan `True` untuk apa pun yang bukan gambar. Ini berarti file CSS, font, atau objek OLE tersemat mempertahankan nama aslinya, yang biasanya yang Anda inginkan ketika Anda **menyimpan word sebagai markdown**.

### Bisakah saya menggunakan skema penamaan khusus alih-alih GUID?  

Tentu saja. Ganti pemanggilan `uuid.uuid4()` dengan fungsi apa pun yang mengembalikan string. Misalnya, Anda dapat menambahkan indeks paragraf asli di depan:

```python
new_name = f"para{resource.resource_id}{ext}"
```

Pastikan nama yang dihasilkan unik di seluruh dokumen.

### Bagaimana ini memengaruhi kinerja pada dokumen besar?  

Callback dijalankan sekali per sumber daya, jadi overheadnya minimal—hampir hanya waktu untuk menghasilkan GUID. Bahkan laporan 200‑halaman dengan puluhan gambar selesai dalam kurang dari satu detik pada laptop modern.

### Bagaimana jika saya membutuhkan nama file gambar yang deterministik (misalnya, untuk build CI)?  

Ganti `uuid.uuid4()` dengan hash dari byte gambar asli:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

Ini menghasilkan nama file yang sama setiap kali Anda menjalankan skrip pada gambar sumber yang sama.

---

## Skrip Lengkap yang Berfungsi – Salin, Tempel, Jalankan  



## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}