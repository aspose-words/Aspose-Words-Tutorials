---
category: general
date: 2026-10-04
description: Aktifkan mode pemulihan di Aspose.Words untuk memulihkan dokumen Word
  yang rusak dengan aman. Ikuti panduan langkah demi langkah dengan kode Python lengkap
  dan penjelasan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: id
lastmod: 2026-10-04
og_description: Aktifkan mode pemulihan untuk memulihkan dokumen Word yang rusak menggunakan
  Aspose.Words. Tutorial ini menunjukkan kode Python yang tepat, mengapa kode tersebut
  berhasil, dan cara menangani kasus tepi.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: Aktifkan mode pemulihan untuk memulihkan dokumen Word yang rusak – panduan
  lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: Aktifkan mode pemulihan untuk memulihkan dokumen Word yang rusak
url: /id/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktifkan mode pemulihan untuk memulihkan dokumen Word yang rusak

Jika Anda perlu **mengaktifkan mode pemulihan** saat memuat file Word, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk Python. Dengan mengaktifkan mode pemulihan Anda dapat **memulihkan dokumen Word yang rusak** yang sebaliknya akan menghasilkan pengecualian.

Pada bagian berikut Anda akan mempelajari:

* Kelas dan properti mana yang mengontrol perilaku pemulihan.  
* Cara memuat file `.docx` yang berpotensi rusak tanpa membuat aplikasi Anda crash.  
* Tips untuk memecahkan masalah pemuatan umum dan menyesuaikan strategi pemulihan.

> **Prasyarat** – Anda telah menginstal Aspose.Words untuk Python (`pip install aspose-words`) dan memiliki pemahaman dasar tentang I/O file Python.

## Apa yang dilakukan mode pemulihan dan mengapa Anda harus mengaktifkannya

Aspose.Words mengurai struktur internal file Word sebelum menampilkannya sebagai objek `Document`. Ketika file rusak—bagian yang hilang, XML yang rusak, atau hubungan yang tidak valid—parser dapat:

| Mode | Perilaku |
|------|----------|
| `STRICT` | Melempar pengecualian pada tanda pertama kerusakan. |
| `IGNORE_ERRORS` | Melewatkan bagian yang tidak dapat dibaca tetapi mungkin kehilangan konten secara diam‑diam. |
| `RECOVER` (opsi **aktifkan mode pemulihan**) | Mencoba membangun kembali dokumen, mempertahankan sebanyak mungkin konten dan menampilkan mode yang dipilih melalui `load_options.recovery_mode`. |

`RECOVER` adalah pilihan yang direkomendasikan ketika Anda harus **memulihkan file dokumen word yang rusak** untuk pemrosesan lanjutan, seperti mengekstrak teks atau mengonversi ke PDF.

## Langkah 1: Buat LoadOptions dan aktifkan mode pemulihan

Langkah pertama adalah menginstansiasi `LoadOptions` dan mengatur properti `recovery_mode` ke `RecoveryMode.RECOVER`. Ini memberi tahu perpustakaan untuk masuk ke jalur pemulihan selama penguraian.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**Mengapa ini penting:**  
Jika Anda melewatkan langkah ini dan dokumen rusak, konstruktor `aw.Document(...)` akan mengeluarkan `InvalidOperationException`. Mengaktifkan mode pemulihan mencegah crash dan memberikan objek `Document` yang sebagian‑terbaiki yang masih dapat Anda gunakan.

## Langkah 2: Muat dokumen yang berpotensi rusak menggunakan opsi yang ditentukan

Berikan instance `load_options` ke konstruktor `Document`. Loader kini akan secara otomatis menerapkan algoritma pemulihan.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**Tips:** Ganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif yang dapat diakses runtime Anda. Jika file tidak ada, Aspose.Words akan mengeluarkan `FileNotFoundError` sebelum mencapai logika pemulihan.

## Langkah 3: Verifikasi bahwa mode pemulihan telah diterapkan

Anda dapat memastikan mode yang aktif dengan memeriksa `load_options.recovery_mode`. Ini berguna untuk pencatatan atau penanganan kondisional di kemudian hari dalam pipeline.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**Output yang diharapkan**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

Jika output menampilkan `RECOVER`, Anda telah berhasil **mengaktifkan mode pemulihan** dan dokumen kini siap untuk diproses lebih lanjut (misalnya, ekstraksi teks, konversi ke PDF, atau menyimpan salinan yang telah diperbaiki).

## Langkah 4 (opsional): Simpan salinan yang telah diperbaiki untuk penggunaan di masa depan

Setelah memuat, Anda mungkin ingin menyimpan dokumen yang telah dipulihkan sehingga tidak perlu mengulangi langkah pemulihan.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Menyimpan menghasilkan file `.docx` baru yang dianggap valid oleh Aspose.Words, yang dapat dibuka di Microsoft Word tanpa peringatan.

## Pertanyaan umum dan penanganan kasus‑tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika dokumen benar‑benar tidak dapat dibaca?** | Bahkan dalam mode `RECOVER`, beberapa file berada di luar perbaikan. Objek `Document` akan dibuat tetapi mungkin hanya berisi satu halaman kosong. Periksa `doc.get_page_count()` untuk memastikan konten. |
| **Apakah saya dapat beralih ke `IGNORE_ERRORS` setelah memuat?** | Tidak. Mode pemulihan harus diatur **sebelum** konstruktor `Document` dijalankan. Buat instance `LoadOptions` baru jika Anda memerlukan strategi berbeda. |
| **Apakah mode pemulihan memengaruhi kinerja?** | Ya, menambahkan sedikit overhead karena perpustakaan berusaha merekonstruksi bagian yang rusak. Dampaknya dapat diabaikan untuk kebanyakan file (< 2 MB). |
| **Apakah pendekatan ini bersifat bahasa‑agnostik?** | Konsep yang sama ada di API .NET, Java, dan Node.js (`LoadOptions.RecoveryMode`). Sintaks kode berubah, tetapi logikanya identik. |

## Pro tip: Catat informasi pemulihan secara detail

Aspose.Words menyediakan `LoadOptions.recovery_callback` yang menerima pesan terperinci tentang setiap langkah pemulihan. Menautkannya dapat membantu Anda mendiagnosis mengapa dokumen tertentu gagal.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

Sekarang setiap perbaikan internal (misalnya, “Removed duplicate relationship”) akan dicetak ke konsol.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut adalah skrip mandiri yang dapat Anda salin‑tempel dan jalankan langsung:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

Menjalankan skrip akan mencetak mode pemulihan, jumlah halaman, dan daftar kata yang diekstrak dari dokumen yang telah diperbaiki. Jika Anda mengatur `save_repaired=True`, file bersih baru akan muncul di samping file asli.

## Kesimpulan

Anda kini tahu cara **mengaktifkan mode pemulihan** di Aspose.Words untuk Python dan secara andal **memulihkan dokumen Word yang rusak**. Langkah‑langkah kunci adalah:

1. Buat `LoadOptions` dan atur `recovery_mode` ke `RECOVER`.  
2. Muat file `.docx` menggunakan opsi tersebut.  
3. Verifikasi mode dan, bila perlu, simpan salinan yang telah diperbaiki.

Dari sini Anda dapat menjelajahi topik lanjutan seperti **mengekstrak teks dari dokumen yang dipulihkan**, **mengonversinya ke PDF**, atau **mengotomatiskan pemulihan batch** untuk perpustakaan dokumen besar.

---


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Recover Corrupted DOCX – Complete Guide to Enable Recovery Mode & Get Page](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}