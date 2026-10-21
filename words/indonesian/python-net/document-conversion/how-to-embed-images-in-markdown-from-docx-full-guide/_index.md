---
category: general
date: 2026-05-04
description: Pelajari cara menyisipkan gambar dalam Markdown saat Anda mengonversi
  DOCX ke markdown, menggunakan Python dan Aspose.Words. Juga lihat cara memulihkan
  file DOCX yang rusak.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- recover corrupted docx
language: id
og_description: Pelajari cara menyisipkan gambar dalam Markdown saat mengonversi DOCX,
  dengan contoh Python langkah demi langkah dan tips untuk memulihkan file DOCX yang
  rusak.
og_title: cara menyisipkan gambar di Markdown dari DOCX – Panduan Lengkap
tags:
- Aspose.Words
- Python
- Markdown
- DOCX conversion
title: Cara Menyisipkan Gambar dalam Markdown dari DOCX – Panduan Lengkap
url: /id/python/document-conversion/how-to-embed-images-in-markdown-from-docx-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara menyisipkan gambar di Markdown dari DOCX – Panduan Lengkap

Pernah bertanya‑tanya **cara menyisipkan gambar** di Markdown saat mengonversi file DOCX? Panduan ini menunjukkan **cara menyisipkan gambar** menggunakan Python dan Aspose.Words, dan melakukannya dengan cara yang tetap berfungsi meskipun dokumen sumber sebagian rusak. Kami juga akan membahas **convert docx to markdown**, menjelaskan **how to convert docx**, mendemonstrasikan **embed images as base64**, serta menunjukkan cara **recover corrupted docx** tanpa kesulitan.

Dalam beberapa menit ke depan Anda akan memiliki skrip yang dapat dijalankan, pemahaman jelas mengapa setiap baris penting, dan beberapa tip praktis yang dapat Anda salin‑tempel ke proyek Anda sendiri. Tanpa ketergantungan tersembunyi, tanpa jalan pintas “lihat dokumen”—hanya solusi menyeluruh dari awal hingga akhir.

---

## Apa yang Akan Anda Bangun

Pada akhir tutorial ini Anda akan memiliki:

* Skrip Python yang memuat DOCX (bahkan yang rusak) dengan Aspose.Words.
* Callback khusus yang mengubah setiap gambar yang disematkan menjadi **Base64** data‑URI, secara efektif menjawab pertanyaan **how to embed images** langsung di dalam file Markdown.
* File Markdown di mana persamaan muncul sebagai LaTeX, bentuk mengambang menjadi tag inline, dan semua gambar ter‑inline dengan aman.
* Daftar periksa singkat untuk memecahkan masalah umum saat Anda **convert docx to markdown**.

---

## Prasyarat

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | Diperlukan untuk paket `aspose.words`. |
| paket pip `aspose-words` | Menyediakan namespace `aw` yang digunakan di seluruh kode. |
| File DOCX (ukuran berapa saja) | Sumber yang akan Anda konversi. |
| Opsional: DOCX yang rusak | Untuk menguji jalur **recover corrupted docx**. |

Pasang pustaka dengan:

```bash
pip install aspose-words
```

---

## Menyiapkan lingkungan

Sebelum kita masuk ke proses konversi, pastikan lingkungan Anda dapat menemukan assembly Aspose.Words. Jika Anda menggunakan virtual environment, aktifkan terlebih dahulu:

```bash
# Activate your venv (Linux/macOS)
source venv/bin/activate

# Or on Windows
venv\Scripts\activate
```

Sekarang impor modul‑modul yang diperlukan. Perhatikan impor `base64` – itu adalah inti dari **embed images as base64**.

```python
# Step 1: Import Aspose.Words and base64 for encoding image data
import aspose.words as aw
import base64
```

> **Pro tip:** Jika Anda mendapatkan `ModuleNotFoundError`, periksa kembali bahwa Anda telah menginstal `aspose-words` di dalam virtual environment yang sama dengan tempat Anda menjalankan skrip.

---

## Menulis callback penyisipan gambar

Aspose.Words memungkinkan Anda menyisipkan *resource‑saving callback* ke dalam proses penyimpanan. Di sinilah kita menjawab **how to embed images** dengan mengonversi payload biner menjadi string data‑URI.

```python
# Step 2: Define a callback that converts embedded images to Base64 data URIs
def embed_images(resource):
    # We only care about images; other resources (like CSS) are ignored.
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Build a data URI: data:<mime_type>;base64,<encoded_bytes>
        data_uri = f"data:{resource.mime_type};base64,{base64.b64encode(resource.bytes).decode()}"
        # Return a tuple (name, bytes) – the name is used as the image reference.
        return (resource.name, data_uri.encode())
    # Returning None tells Aspose to skip this resource.
    return None
```

**Mengapa ini berhasil:** Properti `resource.bytes` berisi byte gambar mentah. `base64.b64encode` mengubah byte tersebut menjadi string ASCII, dan kami menambahkan tipe MIME sehingga browser tahu cara merender gambar. Hasilnya adalah file Markdown yang berdiri sendiri tanpa file gambar eksternal – tepat seperti yang dijanjikan oleh **embed images as base64**.

---

## Memuat DOCX dengan mode pemulihan

Masalah umum adalah berhadapan dengan file Word yang sebagian rusak. Aspose.Words menyediakan *recovery mode* yang berusaha menyelamatkan apa yang bisa. Ini memenuhi kebutuhan **recover corrupted docx**.

```python
# Step 3: Load the source DOCX document with recovery mode enabled
load_options = aw.LoadOptions()
load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER  # Attempts to fix broken parts
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_options)
```

Jika file dalam kondisi baik, mode pemulihan hampir tidak menambah beban. Jika file rusak, Aspose akan melewati bagian yang tidak dapat dibaca sambil tetap memberikan objek dokumen yang dapat digunakan.

---

## Mengonfigurasi opsi ekspor Markdown

Sekarang kita memberi tahu Aspose secara tepat bagaimana output Markdown harus terlihat. Dua pengaturan penting untuk hasil yang bersih:

* `office_math_export_mode = LATEX` – mengonversi persamaan Word ke LaTeX, yang dipahami oleh kebanyakan renderer Markdown.
* `export_floating_shapes_as_inline_tag = True` – memaksa gambar mengambang berperilaku seperti gambar inline, sehingga file akhir lebih mirip tampilan PDF.

```python
# Step 4: Configure Markdown export options
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX
markdown_options.resource_saving_callback = embed_images      # Hook we defined earlier
markdown_options.export_floating_shapes_as_inline_tag = True
```

---

## Menyimpan file Markdown

Setelah semua terhubung, langkah terakhir adalah satu baris kode yang menulis Markdown ke disk. Callback yang kami sediakan akan dipanggil untuk setiap gambar, menjadikan **how to embed images** bagian mulus dari pipeline penyimpanan.

```python
# Step 5: Save the document as a Markdown file with the configured options
doc.save("YOUR_DIRECTORY/output.md", markdown_options)
print("✅ Conversion complete! Find your Markdown at YOUR_DIRECTORY/output.md")
```

Saat Anda membuka `output.md`, Anda akan melihat sesuatu seperti:

```markdown
![image1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Baris itu adalah hasil dari **embed images as base64** – gambar berada sepenuhnya di dalam file Markdown, sehingga Anda dapat mengirim satu file `.md` ke mana saja tanpa khawatir aset yang hilang.

---

## Memverifikasi output dan pemecahan masalah

### Pemeriksaan cepat

1. Buka `output.md` di penampil Markdown (VS Code, Typora, pratinjau GitHub, dll.).
2. Pastikan semua gambar muncul dengan benar.
3. Cari blok LaTeX untuk persamaan, misalnya:

   ```latex
   $$\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}$$
   ```

Jika gambar tidak muncul, periksa kembali:

* DOCX sumber memang berisi gambar.
* `resource.mime_type` terdeteksi (jarang bisa menjadi `image/svg+xml`; Aspose tetap dapat menanganinya).

### Kasus tepi umum

| Situation | What to do |
|-----------|------------|
| **Corrupted DOCX still throws errors** | Set `load_options.password` jika file dilindungi kata sandi, atau coba buka file di Word dan simpan kembali. |
| **Very large images cause huge Markdown files** | Ubah ukuran gambar sebelum konversi atau modifikasi callback untuk memperkecil menggunakan Pillow (`PIL.Image`). |
| **You need external image files instead of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}