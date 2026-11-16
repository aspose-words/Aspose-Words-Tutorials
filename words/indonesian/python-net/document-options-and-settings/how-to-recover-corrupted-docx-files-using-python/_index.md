---
category: general
date: 2026-11-15
description: Pelajari cara memulihkan file docx yang rusak di Python dengan mengaktifkan
  mode pemulihan dan memverifikasi halaman dokumen menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- enable recovery mode
- open corrupted word file
- check page count
- verify document pages
language: id
lastmod: 2026-11-15
og_description: Pulihkan file docx yang rusak di Python dengan Aspose.Words. Aktifkan
  mode pemulihan, buka file Word yang rusak dengan aman, dan verifikasi halaman dokumen.
og_image_alt: Screenshot of Python code that recovers a corrupted docx file
og_title: Pulihkan file docx yang rusak di Python – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to recover corrupted docx files in Python by enabling recovery
    mode and verifying document pages with Aspose.Words.
  headline: How to recover corrupted docx files using Python
  type: TechArticle
- description: Learn how to recover corrupted docx files in Python by enabling recovery
    mode and verifying document pages with Aspose.Words.
  name: How to recover corrupted docx files using Python
  steps:
  - name: '**Enable recovery mode** – ensures the loader attempts to fix the file.'
    text: '**Enable recovery mode** – ensures the loader attempts to fix the file.'
  - name: '**Open corrupted word file** – loads the docx even when parts are broken.'
    text: '**Open corrupted word file** – loads the docx even when parts are broken.'
  - name: '**Check page count** – prints the number of pages, confirming the load.'
    text: '**Check page count** – prints the number of pages, confirming the load.'
  - name: '**Save a clean copy** – optional step to write a repaired file back to
      disk.'
    text: '**Save a clean copy** – optional step to write a repaired file back to
      disk.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document recovery
title: Cara memulihkan file docx yang rusak menggunakan Python
url: /id/python/document-options-and-settings/how-to-recover-corrupted-docx-files-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memulihkan file docx yang rusak menggunakan Python

Jika Anda perlu **memulihkan file docx yang rusak**, panduan ini menunjukkan cara yang dapat diandalkan untuk melakukannya dengan Python. Dengan mengaktifkan recovery mode Anda dapat membuka file Word yang rusak, lalu **memeriksa jumlah halaman** untuk memastikan dokumen dimuat dengan benar.

Kami akan membahas setiap langkah—dari mengkonfigurasi `LoadOptions` hingga memastikan bahwa halaman telah dibaca—sehingga Anda dapat mengintegrasikan solusi ini ke dalam pipeline otomatisasi apa pun. Tidak diperlukan alat eksternal selain pustaka Aspose.Words untuk Python.

## Apa yang akan Anda pelajari

* Cara **mengaktifkan recovery mode** di Aspose.Words.
* Kode tepat untuk **membuka file word yang rusak** dengan aman.
* Cara **memverifikasi halaman dokumen** dengan mencetak jumlah halaman.
* Kesulitan umum dan tips untuk menangani dokumen edge‑case.

### Prasyarat

* Python 3.8 atau yang lebih baru.
* Paket `aspose-words` terpasang (`pip install aspose-words`).
* File `.docx` yang gagal dibuka di Microsoft Word (file “rusak”).

---

## Memulihkan docx yang rusak dengan recovery mode

Mengaktifkan recovery mode memberi tahu Aspose.Words untuk mencoba memperbaiki masalah struktural saat memuat file. Baris tunggal ini adalah kunci untuk **memulihkan docx yang rusak**.

```python
import aspose.words as aw

# Create LoadOptions and turn on recovery mode
load_opts = aw.loading.LoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

**Mengapa ini penting:**  
Saat file Word rusak, loader default akan menghentikan proses dengan pengecualian. `RecoveryMode.RECOVER` memaksa parser mengabaikan kesalahan non‑fatal, membangun kembali bagian yang hilang, dan mengembalikan objek `Document` yang dapat digunakan.

---

## Mengaktifkan recovery mode di Aspose.Words (kata kunci sekunder)

Objek `LoadOptions` juga dapat mengontrol perilaku lain (misalnya, penanganan kata sandi). Di sini kami fokus pada flag **enable recovery mode**:

```python
# Explicitly enable recovery mode – this is the secondary keyword in action
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

> **Pro tip:** Jika Anda hanya perlu membaca dokumen tanpa modifikasi, pertahankan instance `LoadOptions` seminimal mungkin. Opsi tambahan dapat sedikit meningkatkan waktu pemuatan.

---

## Membuka file word yang rusak dengan aman

Dengan recovery mode aktif, muat file seperti dokumen biasa. Potongan kode berikut menunjukkan penanganan **open corrupted word file** dan menyertakan pelaporan kesalahan dasar.

```python
try:
    # Replace the path with the location of your corrupted .docx
    doc_path = "YOUR_DIRECTORY/corrupted.docx"
    doc = aw.Document(doc_path, load_opts)
except Exception as e:
    # If recovery fails, you still get a partially loaded document.
    # The exception provides details you can log for diagnostics.
    print(f"Failed to fully recover the file: {e}")
    raise
```

**Penjelasan:**  
* `aw.Document` menerima jalur file dan `load_opts` yang telah dikonfigurasi sebelumnya.  
* Bahkan jika file berisi bagian yang tidak dapat dipulihkan, Aspose.Words mengembalikan instance `Document` yang dapat Anda periksa.

---

## Memeriksa jumlah halaman untuk memverifikasi halaman dokumen

Setelah memuat, cara paling sederhana untuk memastikan dokumen dapat digunakan adalah dengan **memeriksa jumlah halaman**. Ini juga memenuhi persyaratan **verify document pages**.

```python
# Output the number of pages – a quick sanity check
print("Document loaded, pages:", doc.page_count)
```

Jika output menunjukkan jumlah halaman yang tidak nol, pemulihan berhasil. Misalnya:

```
Document loaded, pages: 12
```

**Kasus tepi:**  
Beberapa file yang rusak mungkin kehilangan pemisah bagian, menyebabkan jumlah halaman lebih rendah dari yang diharapkan. Dalam kasus seperti itu, Anda dapat mengiterasi koleksi `sections` untuk memeriksa elemen individual.

```python
for i, section in enumerate(doc.sections, start=1):
    print(f"Section {i} contains {section.body.paragraphs.count} paragraphs")
```

---

## Contoh lengkap yang dapat dijalankan

Menggabungkan semuanya, berikut adalah skrip mandiri yang dapat Anda jalankan langsung.

```python
import aspose.words as aw

def recover_docx(path: str) -> aw.Document:
    """
    Loads a potentially corrupted DOCX file with recovery mode enabled.
    Returns the Document object for further processing.
    """
    # Step 1: Create load options and enable recovery mode
    load_opts = aw.loading.LoadOptions()
    load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Step 2: Load the file using the configured options
    try:
        doc = aw.Document(path, load_opts)
    except Exception as err:
        # Even if recovery fails, Aspose.Words may still give a partial document.
        # Raising the exception makes the failure explicit for callers.
        raise RuntimeError(f"Unable to recover '{path}': {err}") from err

    # Step 3: Verify the document by checking the page count
    print("Document loaded, pages:", doc.page_count)

    return doc

if __name__ == "__main__":
    # Replace with your actual file location
    corrupted_path = "YOUR_DIRECTORY/corrupted.docx"
    recovered_doc = recover_docx(corrupted_path)

    # Optional: further processing, e.g., save as a clean file
    recovered_doc.save("recovered_output.docx")
    print("Recovered document saved as 'recovered_output.docx'")
```

**Apa yang dilakukan skrip:**

1. **Enable recovery mode** – memastikan loader berusaha memperbaiki file.
2. **Open corrupted word file** – memuat docx meskipun ada bagian yang rusak.
3. **Check page count** – mencetak jumlah halaman, mengonfirmasi pemuatan.
4. **Save a clean copy** – langkah opsional untuk menulis file yang diperbaiki kembali ke disk.

---

## Kesulitan umum dan cara menghindarinya

| Symptom | Likely cause | Fix |
|---------|--------------|-----|
| `RuntimeError` with “Unable to recover” | File tidak dapat diperbaiki (misalnya, bagian inti hilang) | Gunakan cadangan atau minta penulis menyediakan salinan baru. |
| Page count is `0` | Pemulihan berhasil tetapi dokumen tidak memiliki konten yang dapat dicetak (misalnya, hanya tabel tersembunyi) | Iterasi melalui `doc.sections` dan periksa `section.body` untuk menemukan elemen tersembunyi. |
| `ImportError: No module named aspose.words` | Aspose.Words tidak terpasang atau lingkungan Python salah | Jalankan `pip install aspose-words` di lingkungan yang sama tempat Anda mengeksekusi skrip. |

---

## Langkah selanjutnya

Sekarang Anda dapat **memulihkan docx yang rusak** dan **memverifikasi halaman dokumen**, Anda mungkin ingin:

* **Ekstrak teks** dari dokumen yang dipulihkan (`doc.get_text()`).
* **Konversi** file bersih ke PDF (`doc.save("output.pdf")`).
* **Otomatisasi** pemrosesan batch banyak file rusak dengan loop dan logging.

Semua tugas ini menggunakan kembali pola `LoadOptions` yang sama, jadi Anda hanya perlu menyesuaikan logika setelah pemuatan.

---

## Kesimpulan

Anda kini memiliki metode lengkap dan siap produksi untuk **memulihkan docx yang rusak** dengan Python. Dengan **mengaktifkan recovery mode**, **membuka file word yang rusak** secara aman, dan **memeriksa jumlah halaman**, Anda dapat secara programatis memastikan bahwa dokumen telah diperbaiki dan siap untuk diproses lebih lanjut.

Silakan sesuaikan skrip untuk operasi massal, integrasikan ke dalam sistem manajemen dokumen, atau kembangkan dengan langkah validasi tambahan. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Aktifkan recovery mode untuk memulihkan dokumen Word yang rusak](/words/english/python-net/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/)
- [Cara Memulihkan File DOCX di Python – Memuat Dokumen dengan Recovery Menggunakan Aspose.Words](/words/english/python-net/document-operations/how-to-recover-docx-files-in-python-load-document-with-recov/)
- [Pulihkan DOCX Rusak dan Konversi ke PDF dengan Aspose.Words (Python)](/words/english/python-net/document-conversion/recover-corrupted-docx-and-convert-to-pdf-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}