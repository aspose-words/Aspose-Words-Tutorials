---
category: general
date: 2026-09-30
description: Aktifkan mode pemulihan untuk membuka dokumen Word yang rusak menggunakan
  Aspose.Words. Pelajari cara memulihkan file docx yang rusak dengan aman dan andal.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: id
lastmod: 2026-09-30
og_description: Aktifkan mode pemulihan untuk membuka dokumen Word yang rusak dengan
  Aspose.Words. Panduan ini menunjukkan langkah demi langkah cara memulihkan file
  docx yang rusak dan menjaga alur kerja Anda tetap stabil.
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: Aktifkan mode pemulihan untuk membuka dokumen Word yang rusak
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: Aktifkan mode pemulihan untuk membuka dokumen Word yang rusak
url: /id/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktifkan mode pemulihan untuk membuka dokumen Word yang rusak

Jika Anda perlu **mengaktifkan mode pemulihan** saat membuka dokumen Word yang rusak, tutorial ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk Python. Baik file rusak selama transfer maupun diedit oleh program yang tidak kompatibel, mengaktifkan mode pemulihan memungkinkan perpustakaan mencoba memperbaiki dokumen alih-alih melemparkan pengecualian.

Dalam panduan ini Anda akan belajar cara **membuka file dokumen word yang rusak**, **memulihkan konten docx yang rusak**, dan memahami opsi-opsi yang mengontrol proses **memuat dokumen dengan pemulihan**. Langkah‑langkah ini bekerja dengan Aspose.Words 23.10 (rilis terbaru pada saat penulisan) dan hanya memerlukan lingkungan Python standar.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Python 3.9 atau yang lebih baru terpasang.
* Aspose.Words untuk Python via .NET (`aspose-words`) terpasang (`pip install aspose-words`).
* File DOCX yang diketahui rusak (untuk pengujian Anda dapat mengganti nama file `.docx` yang valid menjadi `.zip` dan merusak XML secara manual).

> **Tips pro:** Simpan cadangan file asli. Mode pemulihan mengubah dokumen di memori tetapi tidak menulis kembali ke sumber kecuali Anda secara eksplisit menyimpannya.

## Langkah 1: Impor perpustakaan dan buat opsi pemuatan

Hal pertama yang harus Anda lakukan adalah mengimpor `aspose.words` dan membuat objek `LoadOptions`. Objek ini menyimpan semua pengaturan yang memengaruhi cara file dibaca.

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*Mengapa ini penting:* `LoadOptions` adalah gerbang untuk penyetelan detail parser. Tanpa ini, Aspose.Words menggunakan mode ketat default, yang menghentikan proses pada setiap kesalahan struktural.

## Langkah 2: Aktifkan mode pemulihan

Setel properti `recovery_mode` ke `RecoveryMode.RECOVER`. Ini memberi tahu pemuat untuk mencoba memperbaiki otomatis bagian‑bagian yang rusak seperti node XML yang hilang, hubungan yang rusak, atau aliran yang terpotong.

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

Mengaktifkan mode pemulihan **tidak** menjamin dokumen sempurna, tetapi secara signifikan meningkatkan peluang Anda masih dapat mengekstrak teks, gambar, atau tabel.

## Langkah 3: Muat DOCX yang kemungkinan rusak dengan opsi yang telah dikonfigurasi

Sekarang gunakan konstruktor `Document` yang menerima baik jalur file maupun instance `LoadOptions`.

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*Mengapa ini penting:* Blok `try/except` memperlihatkan **cara membuka docx yang rusak** dengan aman. Tanpa mode pemulihan, pemanggilan yang sama akan langsung melempar pengecualian, menghentikan program Anda.

## Langkah 4: Verifikasi konten yang dipulihkan (opsional namun disarankan)

Setelah memuat, Anda sebaiknya memeriksa apakah dokumen berisi konten yang bermakna. Cara cepatnya adalah mengekstrak teks polos dan mencetak beberapa karakter pertama.

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

Jika output menampilkan pratinjau yang masuk akal, Anda dapat melanjutkan memproses dokumen (misalnya, mengonversi ke PDF, mengekstrak tabel, dll.). Jika teks kosong, file mungkin sudah terlalu rusak dan Anda perlu meminta salinan baru.

## Langkah 5: Simpan dokumen yang telah diperbaiki (jika Anda menginginkan salinan bersih)

Setelah Anda puas dengan konten yang dipulihkan, Anda dapat menyimpan DOCX baru yang bersih. Langkah ini opsional tetapi sering berguna untuk alur kerja selanjutnya.

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Menyimpan menghasilkan file baru yang tidak lagi mengandung kerusakan yang memicu mode pemulihan.

## Kasus khusus dan tips tambahan

| Situasi                                 | Pendekatan yang disarankan |
|----------------------------------------|----------------------------|
| **File bukan DOCX** (misalnya `.doc`) | Gunakan `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC` sebelum memuat. |
| **Pemulihan parsial saja**             | Setelah memuat, periksa `document.get_text()` dan `document.get_page_count()`. Jika jumlah halaman 0, dokumen mungkin tidak dapat dipulihkan. |
| **Dokumen besar**                      | Aktifkan `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE` untuk mengurangi penggunaan RAM selama pemulihan. |
| **Perlu mencatat apa yang diperbaiki** | Setel `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER` lalu baca `document.get_last_save_options().recovery_log` (jika tersedia) untuk detail. |

> **Waspada:** Mode pemulihan dapat secara diam-diam menghapus elemen yang tidak didukung (misalnya, font yang hilang). Jika kesetiaan visual sangat penting, bandingkan file yang diperbaiki dengan versi yang diketahui baik.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua langkah, berikut skrip mandiri yang dapat Anda jalankan langsung:

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

Menjalankan skrip akan mencetak pesan sukses, kutipan teks singkat, dan membuat `repaired.docx` di folder yang sama.

## Kesimpulan

Anda kini tahu cara **mengaktifkan mode pemulihan** untuk **membuka dokumen word yang rusak**, **memulihkan konten docx yang rusak**, dan dengan aman **memuat dokumen dengan pemulihan** menggunakan Aspose.Words untuk Python. Langkah utama—membuat `LoadOptions`, mengaktifkan `RecoveryMode.RECOVER`, dan menangani pengecualian—merupakan pola andal yang dapat Anda gunakan kembali dalam pipeline otomatisasi apa pun.

Selanjutnya, pertimbangkan untuk menjelajahi topik terkait seperti **mengonversi dokumen yang dipulihkan ke PDF**, **mengekstrak tabel dengan `DocumentVisitor`**, atau **memproses batch folder berisi file rusak**. Semua itu dibangun di atas fondasi mode pemulihan yang ditunjukkan di sini.

Selamat coding, semoga dokumen Anda tetap sehat!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [how to recover docx – set recovery mode & open corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Recover corrupted DOCX with Aspose.Words LoadOptions – Complete C# Guide](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}