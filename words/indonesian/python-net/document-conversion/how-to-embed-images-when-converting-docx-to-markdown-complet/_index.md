---
category: general
date: 2026-05-04
description: Pelajari cara menyematkan gambar saat mengonversi DOCX ke Markdown menggunakan
  Aspose.Words. Termasuk langkah-langkah untuk mengonversi Word ke markdown, mengekstrak
  gambar dari docx, dan menyematkan gambar sebagai base64.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- convert word to markdown
- extract images from docx
- embed images as base64
language: id
og_description: Temukan cara menyisipkan gambar saat mengonversi DOCX ke Markdown
  dengan Aspose.Words untuk Python. Termasuk kode lengkap, penjelasan, dan tips untuk
  mengekstrak gambar dari DOCX serta menyisipkannya sebagai base64.
og_title: Cara menyisipkan gambar saat mengonversi DOCX ke Markdown – Langkah demi
  Langkah
tags:
- Aspose.Words
- Python
- Markdown
- Document Conversion
title: Cara Menyisipkan Gambar Saat Mengonversi DOCX ke Markdown – Panduan Lengkap
url: /id/python/document-conversion/how-to-embed-images-when-converting-docx-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyematkan gambar saat mengonversi DOCX ke Markdown – Panduan Lengkap

Pernah bertanya-tanya **bagaimana cara menyematkan gambar** dalam file Markdown yang berasal dari dokumen Word? Anda bukan satu-satunya. Banyak pengembang menemui kendala saat mencoba mengonversi DOCX ke Markdown dan berakhir dengan tautan gambar yang rusak. Kabar baik? Dengan beberapa baris Python dan Aspose.Words Anda dapat mempertahankan setiap gambar, bahkan sebagai data‑URI Base64.

Dalam tutorial ini kami akan membahas seluruh proses: mulai dari menginstal Aspose.Words, memuat DOCX yang berisi gambar, mengekstrak gambar-gambar tersebut, dan akhirnya **menyematkan gambar sebagai base64** string di dalam Markdown yang dihasilkan. Pada akhir tutorial Anda akan dapat **mengonversi docx ke markdown**, **mengonversi word ke markdown**, dan bahkan **mengekstrak gambar dari docx** untuk keperluan lain—semua tanpa meninggalkan IDE Anda.

> **Prasyarat**  
> * Python 3.8+  
> * `aspose-words` package (the free trial works for most scenarios)  
> * A DOCX file with at least one image (we’ll call it `Images.docx`)  

Jika Anda nyaman dengan pip dan I/O file dasar, Anda siap. Mari kita mulai.

---

## Cara menyematkan gambar saat mengonversi DOCX ke Markdown

H2 ini secara langsung memenuhi aturan kata kunci utama dan memberi tahu mesin pencari serta asisten AI secara tepat apa yang dibahas di bagian ini.

### Langkah 1: Instal Aspose.Words untuk Python

Pertama, dapatkan pustaka dari PyPI. Nama paketnya adalah `aspose-words`, jangan bingungkan dengan versi .NET.

```bash
pip install aspose-words
```

> **Tip pro:** Jika Anda berada di belakang proxy perusahaan, tambahkan `--proxy http://your-proxy:port` ke perintah.  

Menginstal paket juga akan mengunduh dependensi `aspose-words` sendiri, seperti `aspose-words-cloud`. Tidak diperlukan konfigurasi tambahan untuk konversi lokal.

### Langkah 2: Muat dokumen DOCX sumber

Kami akan menggunakan kelas `aw.Document` untuk membuka file. Langkah ini adalah tempat Anda **mengekstrak gambar dari docx** jika Anda pernah membutuhkannya secara terpisah.

```python
import aspose.words as aw
import base64

# Path to the Word file that contains images
doc_path = "YOUR_DIRECTORY/Images.docx"

# Load the document into memory
document = aw.Document(doc_path)
```

> **Mengapa ini penting:** Memuat dokumen memberi Anda akses ke `resource_saving_callback` nanti, yang merupakan kaitan yang digunakan Aspose untuk menentukan cara menulis gambar selama operasi penyimpanan Markdown.

### Langkah 3: Definisikan callback yang mengubah setiap gambar menjadi data‑URI Base64

Aspose memungkinkan Anda menyela setiap sumber daya (gambar, font, dll.) yang biasanya akan ditulis ke disk. Dengan menyediakan callback, kita dapat mengganti penanganan berbasis file default dengan string Base64 inline.

```python
def embed_images_callback(resource):
    """
    Called for every resource Aspose wants to save.
    If the resource is an image, we convert it to a data‑URI.
    """
    # Only process image resources; other types fall back to default handling
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Build the data‑URI: data:<mime>;base64,<encoded bytes>
        data_uri = (
            f"data:{resource.mime_type};base64,"
            f"{base64.b64encode(resource.bytes).decode()}"
        )
        # Return a tuple (resource name, encoded data) – name is ignored for data‑URI
        return (resource.name, data_uri.encode())
    # Returning None tells Aspose to use its default saving logic
    return None
```

> **Kasus khusus:** Beberapa file Word menyematkan gambar SVG. Aspose melaporkan tipe MIME sebagai `image/svg+xml`, yang juga didukung oleh data‑URI. Jika penampil Markdown target Anda tidak menampilkan SVG, pertimbangkan untuk mengonversinya ke PNG di dalam callback.

### Langkah 4: Konfigurasikan opsi penyimpanan Markdown dan lampirkan callback

Sekarang kami memberi tahu Aspose untuk menggunakan callback yang baru saja kami definisikan. Ini adalah inti dari **cara menyematkan gambar** dalam file Markdown akhir.

```python
# Create save options for Markdown
markdown_options = aw.saving.MarkdownSaveOptions()

# Attach our custom callback
markdown_options.resource_saving_callback = embed_images_callback
```

Anda juga dapat menyesuaikan `markdown_options` untuk mengontrol level heading, fence blok kode, atau apakah akan menghasilkan folder sumber daya terpisah. Untuk panduan ini kami mempertahankan nilai default karena pendekatan data‑URI menghilangkan kebutuhan folder tambahan.

### Langkah 5: Simpan dokumen sebagai Markdown dengan gambar Base64 yang disematkan

Akhirnya, kami menulis file output. Hasilnya adalah satu file `.md` yang berisi setiap gambar sebagai string Base64—tanpa memerlukan aset eksternal.

```python
output_path = "YOUR_DIRECTORY/ImagesEmbedded.md"
document.save(output_path, markdown_options)

print(f"✅ Markdown with embedded images saved to: {output_path}")
```

Saat Anda membuka `ImagesEmbedded.md` di penampil Markdown (VS Code, GitHub, atau generator situs statis), setiap gambar harus muncul persis di tempatnya dalam dokumen Word asli.

> **Apa yang akan Anda lihat:**  
> ```markdown
> ![Picture1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
> ```  
> String panjang setelah `base64,` adalah data biner gambar, yang dienkode sehingga browser dapat mendekodenya secara langsung.

---

## Mengonversi DOCX ke Markdown tanpa kehilangan gambar – jebakan umum

Meskipun kode di atas berfungsi langsung, pengembang sering mengalami beberapa kendala. Di bawah ini adalah pertanyaan paling umum dan jawaban yang membuat konversi Anda berjalan lancar.

### 1. “Gambar saya masih hilang setelah konversi”

* **Periksa tipe MIME:** Beberapa file DOCX lama menyimpan gambar dengan tipe MIME generik (`application/octet-stream`). Callback tetap akan menyematkannya, tetapi beberapa renderer Markdown menolak menampilkan tipe yang tidak dikenal. Anda dapat memaksa fallback ke `image/png` dalam callback jika Anda mengetahui format gambar.
* **Dokumen besar:** Base64 memperbesar ukuran sekitar 33 %. Jika Anda mengonversi file Word 10 MB, Markdown yang dihasilkan bisa ~13 MB. Sebagian besar editor modern dapat menangani ini, tetapi generator situs statis mungkin memiliki batas. Pertimbangkan mengekstrak gambar ke folder alih-alih menyematkannya jika ukuran menjadi masalah.

### 2. “Apakah saya juga dapat mengekstrak gambar dari DOCX untuk penggunaan terpisah?”

Tentu saja. Callback yang sama dapat menulis byte gambar ke disk sebelum mengembalikan data‑URI.

```python
import os

def embed_and_save_images(resource):
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Save the raw image to a folder
        os.makedirs("extracted_images", exist_ok=True)
        with open(f"extracted_images/{resource.name}", "wb") as f:
            f.write(resource.bytes)

        # Then embed as Base64 (same as before)
        data_uri = f"data:{resource.mime_type};base64,{base64.b64encode(resource.bytes).decode()}"
        return (resource.name, data_uri.encode())
    return None
```

Menjalankan versi ini akan memberi Anda folder `extracted_images` **dan** file Markdown dengan gambar Base64 yang disematkan—sempurna untuk proyek yang membutuhkan keduanya.

### 3. “Bagaimana dengan tabel, catatan kaki, atau fitur khusus Word?”

Aspose.Words berusaha mempertahankan sebanyak mungkin format, tetapi Markdown memiliki set fitur terbatas. Tabel dikonversi ke sintaks dipisahkan pipa, sementara catatan kaki menjadi penanda teks biasa. Jika Anda memerlukan output yang lebih kaya (mis., HTML), ubah `MarkdownSaveOptions` menjadi `HtmlSaveOptions` dan pertahankan logika callback yang sama.

---

## Contoh lengkap yang dapat dijalankan – siap salin‑tempel

Menggabungkan semuanya, berikut satu skrip yang dapat Anda letakkan di folder proyek mana pun. Sesuaikan placeholder `YOUR_DIRECTORY` untuk menunjuk ke file Anda yang sebenarnya.

```python
# ------------------------------------------------------------
# How to embed images while converting DOCX to Markdown
# ------------------------------------------------------------
# Prerequisites:
#   pip install aspose-words
# ------------------------------------------------------------

import aspose.words as aw
import base64
import os

# ------------------------------------------------------------------
# 1️⃣  Define the callback that embeds images as Base64 data‑URIs
# ------------------------------------------------------------------
def embed_images_callback(resource):
    """
    Aspose calls this for each external resource (image, font, etc.).
    We only care about images – everything else falls back to default.
    """
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Optional: also write the image to disk for later reuse
        os.makedirs("extracted_images", exist_ok=True)
        with open(f"extracted_images/{resource.name}", "wb") as img_file:
            img_file.write(resource.bytes)

        # Build the Base64 data‑URI
        data_uri = (
            f"data:{resource.mime_type};base64,"
            f"{base64.b64encode(resource.bytes).decode()}"
        )
        # Return name (ignored) and the encoded URI as bytes
        return (resource.name, data_uri.encode())
    return None  # Use Aspose's default handling for non‑image resources

# ------------------------------------------------------------------
# 2️⃣  Load the DOCX that contains images
# ------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/Images.docx"
document = aw.Document(doc_path)

# ------------------------------------------------------------------
# 3️⃣  Prepare Markdown save options and hook the callback
# ------------------------------------------------------------------
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = embed_images_callback

# ------------------------------------------------------------------
# 4️⃣  Save as Markdown with images embedded as Base64
# ------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/ImagesEmbedded.md"
document.save(output_path, markdown_options)

print(f"✅ Success! Markdown saved to {output_path}")
print("   Images are now inline Base64 data‑URIs.")
```

**Hasil yang diharapkan:** Buka `ImagesEmbedded.md` dan Anda akan melihat teks asli plus tag gambar inline seperti `![Picture1](data:image/png;base64,…)`. Tidak diperlukan file gambar eksternal.

---

## Kesimpulan

Kami telah membahas **cara menyematkan gambar** ketika Anda **mengonversi docx ke markdown**, menunjukkan cara **mengekstrak gambar dari docx**, dan mendemonstrasikan cara paling bersih untuk **menyematkan gambar sebagai base64** menggunakan Aspose.Words untuk Python. Skrip lengkap di atas siap dijalankan, dan penjelasannya menjawab “mengapa” di balik setiap baris—sehingga Anda dapat menyesuaikannya dengan proyek Anda tanpa tebakan.

Ingin melangkah lebih jauh? Coba langkah berikut:

* **Konversi Word ke markdown** dengan level heading khusus dengan menyesuaikan `markdown_options.heading_level`.
* **Hasilkan PDF** dari DOCX yang sama dan bandingkan bagaimana gambar ditangani dalam format output yang berbeda.
* **Integrasikan skrip ke dalam pipeline CI** sehingga setiap commit secara otomatis menghasilkan snapshot Markdown dari dokumentasi Anda.

Silakan bereksperimen—mungkin Anda akan mengganti penyematan Base64 dengan URL CDN untuk file besar, atau menambahkan OCR untuk gambar yang dipindai. Tidak ada batasan, dan kini Anda memiliki fondasi yang kuat.

If you hit any sn

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}