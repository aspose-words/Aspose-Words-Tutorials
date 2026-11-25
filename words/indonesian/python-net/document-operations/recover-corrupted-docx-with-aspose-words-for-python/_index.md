---
category: general
date: 2026-11-25
description: Pulihkan file docx yang rusak secara otomatis menggunakan Aspose.Words
  untuk Python. Pelajari cara membuka file Word yang rusak, mengaktifkan mode pemulihan,
  dan memperbaiki docx yang rusak dalam hitungan menit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- open corrupted word file
- automatically repair word document
- fix corrupted docx
- open docx with recovery
language: id
lastmod: 2026-11-25
og_description: Pulihkan file docx yang rusak secara instan dengan Aspose.Words untuk
  Python. Tutorial ini menunjukkan cara membuka file Word yang rusak dan secara otomatis
  memperbaiki dokumen Word menggunakan mode pemulihan.
og_image_alt: Screenshot showing Aspose.Words Python code that recovers corrupted
  docx
og_title: Pulihkan file docx yang rusak dengan Aspose.Words – Panduan Python
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Recover corrupted docx files automatically using Aspose.Words for Python.
    Learn to open corrupted word file, enable recovery mode, and fix corrupted docx
    in minutes.
  headline: Recover corrupted docx with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- docx recovery
- file handling
title: Pulihkan docx yang rusak dengan Aspose.Words untuk Python
url: /id/python/document-operations/recover-corrupted-docx-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pulihkan docx yang rusak dengan Aspose.Words untuk Python

Jika Anda perlu **memulihkan docx yang rusak**, panduan ini menunjukkan cara yang dapat diandalkan untuk melakukannya di Python. Dengan mengkonfigurasi Aspose.Words for Python Anda dapat *membuka file word yang rusak* dengan aman, mengaktifkan mode pemulihan, dan **memperbaiki dokumen word secara otomatis** tanpa intervensi manual.

Tutorial ini membahas setiap langkah—dari menginstal pustaka hingga menangani kasus tepi di mana sebuah file tidak dapat diselamatkan. Pada akhir tutorial Anda akan dapat **memperbaiki docx yang rusak** secara programatis dan menyimpan versi yang diperbaiki untuk pemrosesan lanjutan.

## Apa yang Anda butuhkan

* Python 3.8 atau lebih baru
* Lisensi aktif Aspose.Words untuk Python (versi percobaan gratis dapat digunakan untuk pengujian)
* `pip` untuk menginstal paket
* Sebuah file `.docx` yang gagal dibuka di Microsoft Word (the *corrupted docx* yang akan kami perbaiki)

> **Tip profesional:** Simpan cadangan file asli; mode pemulihan dapat mengubah struktur file saat mencoba memperbaikinya.

## Langkah 1: Instal Aspose.Words untuk Python

Tugas pertama adalah menambahkan paket Aspose.Words ke lingkungan Anda.

```bash
pip install aspose-words
```

Paket ini menyertakan namespace `aw` yang digunakan dalam contoh kode di bawah. Setelah instalasi, verifikasi bahwa impor berhasil:

```python
import aspose.words as aw
print("Aspose.Words version:", aw.__version__)
```

Menjalankan skrip akan mencetak versi pustaka, mengonfirmasi bahwa SDK siap.

## Langkah 2: Buat load options untuk mengontrol cara dokumen dibuka

Saat Anda **membuka file word yang rusak**, Anda harus memberi tahu Aspose.Words bagaimana berperilaku. Kelas `LoadOptions` memungkinkan Anda menentukan strategi pemulihan.

```python
# Step 2: Create load options
load_options = aw.loading.LoadOptions()
```

`LoadOptions` adalah objek ringan; Anda dapat menggunakannya kembali untuk beberapa dokumen jika diperlukan.

## Langkah 3: Aktifkan mode pemulihan untuk secara otomatis memperbaiki file yang rusak

Aspose.Words menyediakan dua mode pemulihan:

* `RecoveryMode.RECOVER` – mencoba memperbaiki dokumen dan mengembalikan objek yang sebagian diperbaiki.
* `RecoveryMode.THROW_EXCEPTION` – melemparkan pengecualian jika terdeteksi korupsi apa pun.

Untuk kebanyakan skenario Anda menginginkan perilaku *memperbaiki dokumen word secara otomatis*, jadi aktifkan `RECOVER`.

```python
# Step 3: Enable recovery mode
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # or .THROW_EXCEPTION
```

Memilih `RECOVER` memastikan API berusaha menyelamatkan sebanyak mungkin konten, yang ideal ketika Anda hanya ingin **memperbaiki docx yang rusak** tanpa inspeksi manual.

## Langkah 4: Muat dokumen yang mungkin rusak menggunakan opsi yang dikonfigurasi

Sekarang Anda dapat **membuka docx dengan mode pemulihan**. Berikan path ke file yang rusak dan `load_options` yang baru saja Anda konfigurasikan.

```python
# Step 4: Load the corrupted document
doc_path = "YOUR_DIRECTORY/corrupted.docx"
document = aw.Document(doc_path, load_options)

print("Document loaded. Sections:", document.sections.count)
```

Jika file tidak dapat diperbaiki, Aspose.Words tetap mengembalikan objek `Document` tetapi mungkin berisi lebih sedikit bagian atau elemen yang hilang. Output `sections.count` membantu Anda memverifikasi bahwa sesuatu telah dimuat.

### Menangani file yang tidak dapat dipulihkan

Jika Anda lebih suka kegagalan eksplisit, ubah mode pemulihan menjadi `THROW_EXCEPTION` dan bungkus pemanggilan load dalam blok `try/except`:

```python
load_options.recovery_mode = aw.loading.RecoveryMode.THROW_EXCEPTION

try:
    document = aw.Document(doc_path, load_options)
except aw.core.exceptions.InvalidOperationException as e:
    print("Recovery failed:", e)
    # Optionally, log the error or move the file to a quarantine folder
```

Menggunakan `THROW_EXCEPTION` berguna dalam pipeline otomatis di mana Anda perlu menghentikan proses pada input yang tidak dapat dipulihkan.

## Langkah 5: Verifikasi dokumen dan simpan versi yang diperbaiki

Setelah memuat, Anda harus memeriksa bahwa bagian penting (mis., paragraf, tabel) ada. Pemeriksaan cepat dapat dilakukan dengan iterasi melalui beberapa paragraf pertama:

```python
# Step 5: Verify content
for i, para in enumerate(document.get_child_nodes(aw.NodeType.PARAGRAPH, True)[:5], start=1):
    print(f"Paragraph {i}: {para.to_txt().strip()[:60]}")

# Save the repaired file
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Jika file asli sangat rusak, beberapa elemen mungkin hilang, tetapi file yang disimpan akan menjadi `.docx` *valid* yang dapat dibuka oleh Microsoft Word.

## Kasus tepi dan praktik terbaik

| Situation | Recommended approach |
|-----------|----------------------|
| **File terenkripsi** | Gunakan `LoadOptions.password` untuk menyediakan kata sandi sebelum memuat. |
| **Dokumen besar (>100 MB)** | Tingkatkan `LoadOptions.memory_optimization` untuk mengurangi tekanan memori. |
| **Beberapa file yang rusak** | Lakukan loop pada daftar path, gunakan kembali instance `LoadOptions` yang sama, dan catat setiap hasil. |
| **Perlu mempertahankan metadata asli** | Setelah memuat, salin `document.built_in_properties` ke `Document` baru sebelum menyimpan. |

### Kesalahan umum

* **Lupa mengatur `recovery_mode`** – nilai default adalah `THROW_EXCEPTION`, yang akan menghentikan proses pada setiap korupsi.
* **Menggunakan path relatif tanpa direktori kerja yang tepat** – selalu selesaikan path lengkap dengan `os.path.abspath`.
* **Tidak membuang objek `Document`** – dalam layanan yang berjalan lama, panggil `document.dispose()` untuk membebaskan sumber daya native.

## Contoh lengkap yang berfungsi

Berikut adalah skrip mandiri yang mencakup semua langkah, menangani pengecualian, dan menunjukkan cara **memulihkan docx yang rusak** secara siap produksi.

```python
import os
import aspose.words as aw

def recover_docx(input_path: str, output_path: str) -> bool:
    """
    Attempts to recover a corrupted .docx file.
    Returns True if the file was saved successfully, False otherwise.
    """
    # Ensure the input exists
    if not os.path.isfile(input_path):
        print(f"File not found: {input_path}")
        return False

    # Configure load options for automatic repair
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # auto‑repair

    try:
        # Load the document with recovery
        doc = aw.Document(input_path, load_options)
        print(f"Loaded document. Sections: {doc.sections.count}")

        # Optional sanity check – print first three paragraphs
        paras = doc.get_child_nodes(aw.NodeType.PARAGRAPH, True)[:3]
        for idx, p in enumerate(paras, start=1):
            print(f"Paragraph {idx}: {p.to_txt().strip()[:80]}")

        # Save the repaired document
        doc.save(output_path)
        print(f"Repaired document saved to: {output_path}")
        return True

    except aw.core.exceptions.InvalidOperationException as exc:
        # This branch runs only if you switch to THROW_EXCEPTION mode
        print(f"Recovery failed: {exc}")
        return False

if __name__ == "__main__":
    src = "YOUR_DIRECTORY/corrupted.docx"
    dst = "YOUR_DIRECTORY/repaired.docx"
    success = recover_docx(src, dst)
    if success:
        print("Recovery completed successfully.")
    else:
        print("Recovery could not be performed.")
```

**Output yang diharapkan** (ketika pemulihan berhasil):



## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Pulihkan DOCX Rusak – Panduan Lengkap Menggunakan Aspose.Words untuk Python](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-using-aspose-words-for/)
- [Pulihkan DOCX Rusak – Panduan Lengkap untuk Mengaktifkan Mode Pemulihan & Mendapatkan Halaman](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Pulihkan DOCX Rusak dan Konversi ke PDF dengan Aspose.Words (Python)](/words/english/python-net/document-conversion/recover-corrupted-docx-and-convert-to-pdf-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}