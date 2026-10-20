---
category: general
date: 2026-06-27
description: Konversi docx ke markdown menggunakan Python. Pelajari cara mengekstrak
  gambar dari Word dan menyimpan output markdown dengan callback khusus.
draft: false
keywords:
- convert docx to markdown
- extract images from word
- convert word to markdown
- python docx to markdown
- save markdown output
language: id
og_description: Konversi docx ke markdown dengan Python, ekstrak gambar dari Word,
  dan simpan output markdown menggunakan callback sumber daya khusus.
og_title: Konversi docx ke markdown – Panduan Python dengan Ekstraksi Gambar
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  headline: Convert docx to markdown – Complete Python Guide with Image Extraction
  type: TechArticle
- description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  name: Convert docx to markdown – Complete Python Guide with Image Extraction
  steps:
  - name: Expected Output
    text: '```markdown # Sample Document'
  - name: Quick sanity check
    text: '```bash # On Unix/macOS cat YOUR_DIRECTORY/output.md ls YOUR_DIRECTORY/images/
      ```'
  - name: Dealing with duplicate image names
    text: 'Word sometimes reuses the same internal name for different pictures. To
      avoid overwriting, you can tweak `image_saver`:'
  - name: Converting large documents
    text: 'For multi‑megabyte documents, consider streaming the output to avoid memory
      spikes:'
  type: HowTo
tags:
- Python
- Aspose.Words
- Document Conversion
title: Konversi docx ke markdown – Panduan Python Lengkap dengan Ekstraksi Gambar
url: /id/python/document-conversion/convert-docx-to-markdown-complete-python-guide-with-image-ex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengonversi docx ke markdown – Panduan Python Lengkap dengan Ekstraksi Gambar

Pernah bertanya-tanya bagaimana cara **convert docx to markdown** tanpa kehilangan gambar yang tertanam dalam file Word Anda? Anda bukan satu-satunya. Banyak pengembang mengalami kendala ketika konversi menghilangkan gambar, meninggalkan markdown dengan tautan rusak atau, lebih buruk lagi, tanpa gambar sama sekali.  

Kabar baik? Dengan beberapa baris Python dan Aspose.Words Anda dapat dengan mulus mengubah `.docx` menjadi markdown bersih **dan** mengekstrak setiap gambar ke dalam folder pilihan Anda. Dalam tutorial ini kami akan membahas seluruh proses, mulai dari menginstal pustaka hingga menyiapkan callback yang menyimpan setiap gambar di tempat yang Anda inginkan.

Pada akhir panduan ini Anda akan dapat **convert word to markdown**, mengekstrak setiap grafik, dan **save markdown output** siap untuk generator situs statis, pipeline dokumentasi, atau alur kerja markdown‑first lainnya.

## Apa yang Anda Butuhkan

- Python 3.8 atau lebih baru (kode juga berfungsi pada 3.9+)  
- Akses `pip` untuk menginstal paket pihak ketiga  
- Lisensi Aspose.Words for Python yang valid (versi percobaan gratis dapat digunakan untuk evaluasi)  
- Contoh `input.docx` yang berisi teks dan setidaknya satu gambar  

Itu saja—tanpa instalasi Office yang berat, tanpa interop COM, hanya Python murni.

## Langkah 1: Instal Aspose.Words untuk Python

Pertama-tama, mari dapatkan pustaka tersebut. Buka terminal dan jalankan:

```bash
pip install aspose-words
```

Jika Anda mendapatkan error izin, tambahkan `--user` atau gunakan lingkungan virtual. Setelah instalasi selesai, Anda akan memiliki akses ke paket `aspose.words` (diimpor sebagai `aw` dalam contoh).

> **Pro tip:** Jaga `requirements.txt` Anda tetap rapi; tambahkan `aspose-words==<latest-version>` agar kolaborator dapat mereproduksi lingkungan secara tepat.

## Langkah 2: Siapkan Callback Penyimpanan Gambar Kustom

Aspose.Words memungkinkan Anda menyisipkan ke dalam pipeline penyimpanan dengan *resource‑saving callback*. Anggaplah ini sebagai perantara yang menerima aliran byte setiap gambar dan memberi tahu pustaka di mana merujuknya dalam file markdown yang dihasilkan.

Here’s the core of the callback:

```python
# Step 1: Define a callback to store extracted images in a custom folder
def image_saver(image_bytes, image_name):
    """
    Saves an image to YOUR_DIRECTORY/images/ and returns the relative path
    that will be placed in the markdown file.
    """
    # Ensure the target folder exists
    import os
    target_dir = os.path.join("YOUR_DIRECTORY", "images")
    os.makedirs(target_dir, exist_ok=True)

    # Build the full path on disk
    file_path = os.path.join(target_dir, image_name)

    # Write the raw image bytes to disk
    with open(file_path, "wb") as f:
        f.write(image_bytes)

    # Return the path that markdown will use (relative to the .md file)
    return os.path.join("images", image_name)
```

**Mengapa ini penting:**  
- **Control** – Anda menentukan tata letak folder, skema penamaan, atau bahkan konversi format gambar jika diperlukan.  
- **Portability** – Jalur relatif yang dikembalikan membuat markdown dapat dipindahkan antar mesin selama folder `images` ikut bersama.  
- **Performance** – Callback dijalankan pada setiap gambar hanya sekali, menghindari penulisan duplikat.

## Langkah 3: Konfigurasikan Opsi Penyimpanan Markdown

Sekarang kami menghubungkan callback ke objek `MarkdownSaveOptions`. Ini memberi tahu Aspose.Words untuk menggunakan `image_saver` kami setiap kali menemukan sumber gambar.

```python
# Step 2: Create Markdown save options and attach the callback
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = image_saver
```

Anda juga dapat menyesuaikan beberapa pengaturan opsional di sini, seperti `export_images_as_base64` (diatur ke `False` karena kami menginginkan file terpisah) atau `add_table_of_contents` jika Anda memerlukan TOC. Untuk tujuan panduan ini kami akan tetap menggunakan nilai default.

## Langkah 4: Muat Dokumen Word Sumber

Loading a `.docx` is straightforward. Just point Aspose.Words at the file path:

```python
# Step 3: Load the source Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

Jika dokumen besar, Anda dapat mempertimbangkan streaming dengan `aw.LoadOptions`, tetapi untuk kebanyakan kasus konstruktor sederhana sudah cukup.

## Langkah 5: Simpan sebagai Markdown – Biarkan Callback Menangani Beban Berat

Akhirnya, kami meminta Aspose.Words menulis file markdown. Pustaka akan memanggil `image_saver` untuk setiap gambar yang tertanam, menyimpan file, dan menyisipkan tautan gambar markdown yang tepat.

```python
# Step 4: Save the document as Markdown, letting the callback handle image resources
doc.save("YOUR_DIRECTORY/output.md", md_options)
```

Setelah proses selesai Anda akan melihat dua hal:

1. `output.md` yang berisi teks markdown dengan baris seperti `![](images/image1.png)`  
2. Sub‑folder `images` yang berisi setiap gambar yang diekstrak.

### Output yang Diharapkan

```markdown
# Sample Document

This is a paragraph from the Word file.

![](images/image1.png)

Another paragraph follows the picture.
```

Buka `output.md` di penampil markdown apa pun (VS Code, GitHub, MkDocs) dan Anda akan melihat gambar ditampilkan persis seperti pada file Word asli.

## Langkah 6: Verifikasi Hasil dan Tangani Kasus Pojok

### Pemeriksaan cepat

```bash
# On Unix/macOS
cat YOUR_DIRECTORY/output.md
ls YOUR_DIRECTORY/images/
```

Pastikan nama file gambar cocok dengan jalur di markdown. Jika Anda menemukan gambar yang hilang, periksa kembali bahwa callback mengembalikan jalur **relatif** (bukan absolut) dan folder `images` direferensikan dengan benar.

### Menangani Nama Gambar Duplikat

Word sometimes reuses the same internal name for different pictures. To avoid overwriting, you can tweak `image_saver`:

```python
import uuid

def image_saver(image_bytes, image_name):
    unique_name = f"{uuid.uuid4().hex}_{image_name}"
    # rest of the code uses unique_name instead of image_name
    ...
    return os.path.join("images", unique_name)
```

### Mengonversi Dokumen Besar

For multi‑megabyte documents, consider streaming the output to avoid memory spikes:

```python
with open("YOUR_DIRECTORY/output.md", "w", encoding="utf-8") as out_file:
    doc.save(out_file, md_options)
```

Aspose.Words handles the streaming internally, so you don’t have to load the whole markdown into RAM.

## Langkah 7: Otomatiskan Alur Kerja (Opsional)

If you need to batch‑process a folder of Word files, wrap the logic in a loop:

```python
import glob

for doc_path in glob.glob("YOUR_DIRECTORY/*.docx"):
    doc = aw.Document(doc_path)
    base_name = os.path.splitext(os.path.basename(doc_path))[0]
    md_path = f"YOUR_DIRECTORY/{base_name}.md"
    doc.save(md_path, md_options)
    print(f"Converted {doc_path} → {md_path}")
```

Sekarang Anda dapat menaruh seratus file `.docx` ke dalam direktori dan membiarkan skrip memprosesnya, masing‑masing dengan sub‑folder `images`nya sendiri.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **convert docx to markdown** sambil mempertahankan setiap gambar, menggunakan skrip Python bersih dan mekanisme callback kuat dari Aspose.Words. Sekarang Anda tahu cara:

- **Ekstrak gambar dari Word** via a custom `resource_saving_callback`  
- **Convert word to markdown** dengan konfigurasi minimal  
- **Save markdown output** bersama folder gambar yang terorganisir rapi  

Dari sini Anda dapat bereksperimen dengan ekstensi markdown tambahan (tabel, catatan kaki) atau mengintegrasikan skrip ke dalam pipeline CI yang membangun dokumentasi secara otomatis. Tidak ada batasan—ingatlah untuk menjaga logika penyimpanan gambar tetap fleksibel, dan markdown Anda akan tetap rapi.

Ada pertanyaan tentang kasus pojok atau lisensi? Tinggalkan komentar di bawah, dan selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara Menyimpan Markdown dari Word – Panduan Python Lengkap](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Mengonversi File Docx ke Markdown](/words/english/net/basic-conversions/docx-to-markdown/)
- [Mengonversi Word ke Markdown – Menyematkan Gambar sebagai Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}