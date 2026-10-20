---
category: general
date: 2026-06-21
description: Ekspor Word ke Markdown dan simpan gambar dari Word menggunakan Python.
  Pelajari cara mengonversi docx ke markdown, menulis file biner dengan Python, dan
  mengekstrak gambar dari docx.
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- save images from word
- write binary file python
- how to extract images from docx
language: id
og_description: Ekspor Word ke Markdown dan secara otomatis menyimpan gambar dari
  Word. Panduan langkah demi langkah ini menunjukkan cara mengonversi docx ke markdown,
  menulis file biner dengan Python, dan mengekstrak gambar dari docx.
og_title: Ekspor Word ke Markdown – Tutorial Python Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  headline: Export Word to Markdown – Full Guide with Image Extraction in Python
  type: TechArticle
- description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  name: Export Word to Markdown – Full Guide with Image Extraction in Python
  steps:
  - name: Expected Output Example
    text: 'If `input.docx` contained a single picture named `image1.png`, the resulting
      `output.md` might look like:'
  - name: What if the document has duplicate image names?
    text: 'Aspose.Words will suggest the same name for identical images. Our callback
      uses the suggested name directly, which could cause overwrites. To avoid that,
      modify the callback to append a unique identifier:'
  - name: Can I change the image format during extraction?
    text: Absolutely. After writing the binary data, you could open it with Pillow
      (`PIL.Image`) and save it as a different format (e.g., JPEG). This is useful
      when you need to **convert docx to markdown** for a web‑optimized site.
  - name: Does this work on macOS/Linux as well as Windows?
    text: Yes. The code uses `os.path` and avoids hard‑coded path separators, so it’s
      cross‑platform. Just remember to grant the script write permissions to the target
      directory.
  - name: What if I need to export tables or footnotes too?
    text: '`MarkdownSaveOptions` supports a range of features—tables become markdown
      tables, footnotes become inline references. No extra code is required; just
      experiment with the generated markdown to see how it renders.'
  type: HowTo
tags:
- python
- docx
- markdown
- image-extraction
title: Ekspor Word ke Markdown – Panduan Lengkap dengan Ekstraksi Gambar di Python
url: /id/python/document-conversion/export-word-to-markdown-full-guide-with-image-extraction-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ekspor Word ke Markdown – Panduan Lengkap dengan Ekstraksi Gambar di Python

Pernah bertanya-tanya bagaimana cara **mengekspor Word ke markdown** tanpa kehilangan gambar yang tersemat dalam dokumen Anda? Anda bukan satu-satunya—para pengembang terus-menerus meminta cara yang mudah untuk beralih dari `.docx` ke markdown bersih sambil mempertahankan setiap gambar tetap utuh.  

Dalam tutorial ini kami akan membahas solusi lengkap yang tidak hanya **convert docx to markdown** tetapi juga **save images from word** file, semuanya dengan Python murni. Pada akhir tutorial Anda akan memiliki skrip siap‑jalankan yang menulis binary file python style dan mengekstrak setiap gambar yang Anda butuhkan.

## Apa yang Dibahas dalam Panduan Ini

- Menginstal pustaka yang tepat (Aspose.Words for Python)  
- Mendefinisikan callback yang menulis data biner ke disk  
- Mengonversi dokumen Word ke markdown dengan penanganan gambar  
- Memverifikasi output dan memecahkan masalah umum  

Tanpa layanan eksternal, tanpa menyalin‑tempel manual—hanya satu skrip mandiri yang dapat Anda masukkan ke dalam proyek apa pun.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

| Persyaratan | Mengapa penting |
|-------------|----------------|
| Python 3.8+ | Sintaks modern dan petunjuk tipe |
| `pip` access | Untuk menginstal paket Aspose.Words |
| Izin menulis ke folder | Callback akan **write binary file python** style |
| File `.docx` dengan gambar | Untuk melihat fitur **save images from word** beraksi |

Jika ada yang terdengar tidak familiar, jangan panik—saya akan menunjukkan cara menyiapkannya pada langkah berikutnya.

## Langkah 1: Instal Aspose.Words untuk Python via pip

Aspose.Words adalah pustaka kuat yang memahami format dokumen Word secara lengkap, termasuk media yang tersemat. Instal dengan satu perintah:

```bash
pip install aspose-words
```

> **Pro tip:** Gunakan lingkungan virtual (`python -m venv venv`) untuk menjaga ketergantungan tetap rapi. Ini juga mencegah bentrok versi dengan proyek lain.

## Langkah 2: Buat Callback Penyimpanan Sumber Daya (Write Binary File Python)

Inti dari solusi ini adalah callback yang menerima setiap sumber daya biner (seperti gambar) dan memutuskan di mana menyimpannya. Di sinilah kita **write binary file python** style.

```python
def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save a binary resource (e.g., an image) to a custom folder and
    return the relative path for markdown linking.

    :param resource: Raw binary data of the resource.
    :param suggested_name: A filename suggested by Aspose.Words.
    :return: Relative path to be used in the markdown file.
    """
    # Build a relative path inside a custom folder.
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)          # Ensure the folder exists.
    file_path = os.path.join(folder, suggested_name)

    # Write the binary data to disk – classic write binary file python.
    with open(file_path, "wb") as f:
        f.write(resource)

    # Return the path so the Markdown writer can reference it.
    return file_path
```

**Mengapa callback?**  
Aspose.Words tidak tahu di mana Anda ingin menyimpan gambar. Dengan memberikan `my_resource_saver`, Anda memperoleh kontrol penuh atas penamaan, struktur folder, dan bahkan pemrosesan lanjutan (seperti kompresi gambar) jika diinginkan.

## Langkah 3: Muat Dokumen Word Sumber

Sekarang kami mengarahkan pustaka ke file `.docx` yang ingin Anda ubah.

```python
import aspose.words as aw
import os

# Adjust the path to your actual file location.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

Jika file tidak ditemukan, periksa kembali jalurnya dan pastikan skrip memiliki izin membaca. Kesalahan umum adalah mencampur slash maju dan mundur pada Windows; `os.path.join` menangani hal itu untuk Anda.

## Langkah 4: Konfigurasikan Opsi Penyimpanan Markdown dan Lampirkan Callback

Langkah ini menggabungkan semuanya. Kami memberi tahu Aspose.Words untuk menggunakan markdown sebagai format output dan memanggil `my_resource_saver` setiap kali menemukan gambar.

```python
# Create Markdown save options.
md_save = aw.saving.MarkdownSaveOptions()

# Attach the resource‑saving callback.
md_save.resource_saving_callback = my_resource_saver
```

Anda dapat menyesuaikan output markdown di sini (mis., set `md_save.export_images_as_base64 = False` jika Anda lebih suka gambar tersemat). Untuk tujuan **how to extract images from docx**, menyimpannya sebagai file terpisah biasanya lebih bersih.

## Langkah 5: Ekspor Dokumen – Panggilan Akhir Export Word ke Markdown

Yang tersisa hanyalah satu baris kode yang melakukan pekerjaan berat.

```python
output_md = "YOUR_DIRECTORY/output.md"
doc.save(output_md, md_save)
print(f"✅ Markdown saved to {output_md}")
print(f"🖼️ Images stored in ./custom_images/")
```

Saat Anda menjalankan skrip, Anda akan melihat file `output.md` baru di samping folder `custom_images` yang berisi setiap gambar dari file Word asli. Markdown akan merujuk gambar dengan jalur relatif, sehingga siap untuk generator situs statis atau rendering GitHub.

### Contoh Output yang Diharapkan

Jika `input.docx` berisi satu gambar bernama `image1.png`, `output.md` yang dihasilkan mungkin terlihat seperti:

```markdown
# Sample Document

Here is an illustration:

![image1.png](custom_images/image1.png)

More text follows...
```

Dan struktur foldernya:

```
/YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ custom_images/
   └─ image1.png
```

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika dokumen memiliki nama gambar duplikat?

Aspose.Words akan menyarankan nama yang sama untuk gambar identik. Callback kami menggunakan nama yang disarankan secara langsung, yang dapat menyebabkan penimpaan. Untuk menghindarinya, ubah callback untuk menambahkan pengidentifikasi unik:

```python
import uuid

def my_resource_saver(resource, suggested_name):
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    # rest of the code unchanged...
```

### Bisakah saya mengubah format gambar saat ekstraksi?

Tentu saja. Setelah menulis data biner, Anda dapat membukanya dengan Pillow (`PIL.Image`) dan menyimpannya dalam format berbeda (mis., JPEG). Ini berguna ketika Anda perlu **convert docx to markdown** untuk situs yang dioptimalkan web.

### Apakah ini bekerja di macOS/Linux serta Windows?

Ya. Kode menggunakan `os.path` dan menghindari pemisah jalur yang ditulis keras, sehingga lintas‑platform. Cukup ingat untuk memberikan skrip izin menulis ke direktori target.

### Bagaimana jika saya perlu mengekspor tabel atau catatan kaki juga?

`MarkdownSaveOptions` mendukung berbagai fitur—tabel menjadi tabel markdown, catatan kaki menjadi referensi inline. Tidak diperlukan kode tambahan; cukup bereksperimen dengan markdown yang dihasilkan untuk melihat bagaimana tampilannya.

## Skrip Lengkap – Siap Salin & Tempel

Berikut contoh lengkap yang dapat dijalankan yang menggabungkan semua yang telah dibahas. Simpan sebagai `export_word_to_md.py` dan jalankan `python export_word_to_md.py`.

```python
import os
import uuid
import aspose.words as aw

def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save binary resources (images) to a custom folder and return
    the relative path for markdown references.
    """
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)

    # Ensure unique filenames to avoid collisions.
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    file_path = os.path.join(folder, unique_name)

    with open(file_path, "wb") as f:
        f.write(resource)

    return file_path

def main():
    # ------------------------------------------------------------------
    # 1️⃣ Load the Word document you want to convert.
    # ------------------------------------------------------------------
    doc_path = "YOUR_DIRECTORY/input.docx"
    if not os.path.isfile(doc_path):
        raise FileNotFoundError(f"❌ {doc_path} does not exist.")
    doc = aw.Document(doc_path)

    # ------------------------------------------------------------------
    # 2️⃣ Set up markdown options and plug in the image callback.
    # ------------------------------------------------------------------
    md_save = aw.saving.MarkdownSaveOptions()
    md_save.resource_saving_callback = my_resource_saver

    # ------------------------------------------------------------------
    # 3️⃣ Perform the export – this is the core **export word to markdown** step.
    # ------------------------------------------------------------------
    output_md = "YOUR_DIRECTORY/output.md"
    doc.save(output_md, md_save)

    print(f"✅ Markdown exported to: {output_md}")
    print(f"🖼️ Extracted images are in the folder: ./custom_images/")

if __name__ == "__main__":
    main()
```

Jalankan, buka `output.md` di penampil markdown apa pun, dan Anda akan melihat konten Word asli Anda—teks, judul, **save images from word**, dan semua hal lainnya—terduplikasi dengan setia.

## Kesimpulan

Kami baru saja menunjukkan cara yang kuat untuk **export word to markdown** sambil mempertahankan setiap gambar yang tersemat. Dengan memanfaatkan Aspose.Words dan **resource‑saving callback** khusus, Anda dapat **convert docx to markdown**, **write binary file python**, dan menjawab pertanyaan klasik **how to extract images from docx** dalam satu skrip yang dapat digunakan kembali.

Apa selanjutnya? Coba tambahkan langkah yang mengompres gambar dengan Pillow, atau integrasikan skrip ke dalam pipeline CI yang secara otomatis mengonversi dokumentasi untuk situs statis Anda. Kemungkinannya tak terbatas, dan Anda kini memiliki fondasi yang kuat untuk dibangun.

Ada masukan atau mengalami masalah? Tinggalkan komentar di bawah—selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara Menyimpan Markdown dari Word – Panduan Python Lengkap](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Pulihkan DOCX Rusak & Konversi Word ke Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)
- [Simpan Gambar Word – Konversi Word ke Markdown dengan Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}