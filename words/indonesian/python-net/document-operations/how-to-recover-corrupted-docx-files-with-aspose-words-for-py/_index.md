---
category: general
date: 2026-10-16
description: Pelajari cara memulihkan docx yang rusak, mengaktifkan mode pemulihan,
  dan memeriksa jumlah halaman dalam satu skrip Python menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- enable recovery mode
- check page count
- recover word document
- how to open corrupted docx
language: id
lastmod: 2026-10-16
og_description: Pulihkan file docx yang rusak menggunakan Aspose.Words untuk Python.
  Panduan ini menunjukkan cara mengaktifkan mode pemulihan, membuka file yang rusak,
  dan memeriksa jumlah halaman.
og_image_alt: Screenshot of Python code that recovers a corrupted docx document using
  Aspose.Words
og_title: Pulihkan docx yang rusak dengan Aspose.Words – aktifkan mode pemulihan dan
  verifikasi jumlah halaman
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to recover corrupted docx, enable recovery mode, and check
    page count in a single Python script using Aspose.Words.
  headline: How to recover corrupted docx files with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
- DOCX
title: Cara memulihkan file docx yang rusak dengan Aspose.Words untuk Python
url: /id/python/document-operations/how-to-recover-corrupted-docx-files-with-aspose-words-for-py/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memulihkan file docx yang rusak dengan Aspose.Words untuk Python

Jika Anda perlu **memulihkan docx yang rusak**, Aspose.Words untuk Python mempermudahnya. Tutorial ini menunjukkan cara **mengaktifkan mode pemulihan**, memuat dokumen yang rusak, dan **memeriksa jumlah halaman** untuk mengonfirmasi operasi **memulihkan dokumen Word** berhasil.

File DOCX yang rusak sering muncul setelah penyimpanan terputus, konversi yang gagal, atau kesalahan disk. Daripada meminta pengguna mengirim ulang file, Anda dapat secara otomatis mencoba pemulihan di sisi server. Di bawah ini Anda akan mempelajari alur kerja lengkap, mulai dari menginstal SDK hingga memverifikasi bahwa dokumen terbuka dengan benar.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Python 3.8 atau lebih baru terinstal.
* Lisensi Aspose.Words untuk Python yang valid (versi percobaan gratis dapat digunakan untuk evaluasi).
* Paket `aspose-words` terinstal melalui `pip`:

```bash
pip install aspose-words
```

* File DOCX yang rusak tersedia di disk (misalnya, `corrupted.docx`).  
  Jika Anda tidak memilikinya, Anda dapat mensimulasikan kerusakan dengan membuka DOCX di editor teks dan menghapus beberapa byte.

## Langkah 1: Aktifkan mode pemulihan untuk memulihkan docx yang rusak

Mode pemulihan memberi tahu Aspose.Words untuk mengabaikan masalah struktural dan mencoba membangun kembali pohon dokumen. Tanpa mode ini, memuat file yang rusak akan menghasilkan pengecualian.

```python
import aspose.words as aw

# Create LoadOptions and turn on recovery mode
load_options = aw.LoadOptions()
load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER
```

**Mengapa ini penting:**  
`LoadOptions.RecoveryMode.RECOVER` memberi instruksi kepada parser untuk memperlakukan file seolah-olah sebagian valid, melewati bagian yang tidak dapat dibaca dan menyelamatkan sisanya. Ini adalah langkah inti yang memungkinkan Anda **memulihkan docx yang rusak** secara otomatis.

## Langkah 2: Muat dokumen menggunakan opsi pemulihan yang diaktifkan

Sekarang mode pemulihan aktif, muat file tersebut. Jika dokumen sangat rusak, Aspose.Words tetap akan mengembalikan objek `Document` yang berisi konten apa pun yang dapat diselamatkan.

```python
# Load the potentially corrupted DOCX using the recovery options
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Tip:** Ganti `YOUR_DIRECTORY` dengan jalur sebenarnya. Menggunakan jalur absolut menghindari kesalahan jalur relatif yang ambigu, terutama ketika skrip dijalankan sebagai layanan latar belakang.

## Langkah 3: Periksa jumlah halaman untuk memverifikasi operasi pemulihan dokumen Word

Cara cepat untuk memastikan file terbuka adalah dengan membaca `page_count`-nya. Jika jumlahnya lebih dari nol, pemulihan berhasil cukup untuk menampilkan setidaknya satu halaman.

```python
# Verify that the document was loaded by printing its page count
print("Document loaded, pages:", doc.page_count)
```

Jika output menunjukkan `pages: 0`, file mungkin tidak dapat diperbaiki, atau kerusakan menghapus semua konten yang dapat dicetak. Dalam kasus tersebut, pertimbangkan untuk memberi tahu pengguna dan meminta unggahan baru.

## Skrip lengkap – memulihkan docx yang rusak dalam satu kali jalan

Menggabungkan tiga langkah tersebut memberi Anda potongan kode yang ringkas dan siap produksi:

```python
import aspose.words as aw

def recover_docx(file_path: str) -> int:
    """
    Attempts to recover a corrupted DOCX file and returns the page count.
    Returns -1 if the file cannot be opened at all.
    """
    # Step 1: Enable recovery mode
    load_options = aw.LoadOptions()
    load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER

    try:
        # Step 2: Load the document with recovery enabled
        doc = aw.Document(file_path, load_options)

        # Step 3: Check page count – this also confirms the file was recovered
        page_count = doc.page_count
        print(f"Recovered document page count: {page_count}")
        return page_count
    except Exception as e:
        # If loading fails even with recovery mode, report the error
        print(f"Failed to recover '{file_path}': {e}")
        return -1

if __name__ == "__main__":
    # Example usage – replace with your actual file location
    recover_docx("YOUR_DIRECTORY/corrupted.docx")
```

**Penjelasan fungsi:**

* **Parameter** – `file_path` menunjuk ke DOCX yang ingin Anda buka.  
* **Nilai kembali** – Jumlah halaman setelah pemulihan, atau `-1` jika file tidak dapat dibuka.  
* **Penanganan error** – Bahkan dengan mode pemulihan, beberapa file tidak dapat dipulihkan; blok `except` memastikan skrip gagal dengan elegan.

## Cara membuka docx yang rusak dalam layanan web (opsional)

Jika Anda mengekspos logika ini melalui endpoint Flask atau FastAPI, Anda dapat memungkinkan klien mengunggah file dan menerima respons JSON dengan jumlah halaman.

```python
from fastapi import FastAPI, File, UploadFile
import shutil, os

app = FastAPI()

@app.post("/recover")
async def recover_endpoint(file: UploadFile = File(...)):
    temp_path = f"/tmp/{file.filename}"
    with open(temp_path, "wb") as buffer:
        shutil.copyfileobj(file.file, buffer)

    pages = recover_docx(temp_path)
    os.remove(temp_path)  # Clean up temporary file

    return {"filename": file.filename, "page_count": pages}
```

**Mengapa Anda mungkin memerlukan ini:**  
Dalam pipeline pemrosesan dokumen perusahaan, secara otomatis mencoba pemulihan mengurangi tiket dukungan manual dan meningkatkan pengalaman pengguna.

## Kesalahan umum dan pemecahan masalah

| Gejala | Penyebab yang mungkin | Solusi |
|---|---|---|
| `Exception: File not found` | Jalur salah atau file tidak ada | Verifikasi jalur absolut dan pastikan file ada. |
| `pages: 0` bahkan setelah pemulihan | File hanya berisi data non‑visual (misalnya, hanya metadata) | Periksa apakah dokumen asli memang memiliki halaman; jika tidak, minta file baru. |
| `LicenseException` | Tidak ada lisensi Aspose.Words yang valid | Terapkan lisensi percobaan atau komersial menggunakan `aw.License().set_license("path/to/license.xml")`. |
| Memuat lambat pada file sangat besar | Mode pemulihan memproses banyak bagian yang rusak | Pertimbangkan streaming file atau meningkatkan batas memori. |

**Pro tip:** Selalu catat pesan pengecualian asli ketika pemulihan gagal. Pesan tersebut sering berisi node XML tepat yang menyebabkan masalah, yang dapat membantu Anda memperbaiki proses pembuatan dokumen di hulu.

## Output yang diharapkan

Menjalankan skrip terhadap `corrupted.docx` yang dapat dipulihkan mencetak sesuatu yang mirip dengan:

```
Recovered document page count: 5
```

Jika file tidak dapat diselamatkan, Anda akan melihat:

```
Failed to recover 'YOUR_DIRECTORY/corrupted.docx': The file is corrupted and cannot be opened.
```

Melihat jumlah halaman yang positif mengonfirmasi bahwa Anda telah berhasil **memulihkan docx yang rusak** dan kini dapat melanjutkan pemrosesan dokumen (mis., mengonversi ke PDF, mengekstrak teks, dll.).

## Langkah selanjutnya

Sekarang Anda tahu **cara membuka docx yang rusak**, Anda dapat memperluas alur kerja:

* **Konversi dokumen yang dipulihkan ke PDF** – panggil `doc.save("output.pdf")`.
* **Ekstrak teks untuk pengindeksan** – iterasi melalui `doc.get_child_nodes(aw.NodeType.PARAGRAPH, True)`.
* **Proses batch folder berisi file rusak** – loop melalui file dan simpan hasilnya ke basis data.

Setiap ekstensi ini menggunakan objek `Document` yang sama yang Anda peroleh setelah **mengaktifkan mode pemulihan**, sehingga langkah pemulihan tetap menjadi fondasi dari pipeline penanganan dokumen yang kuat.

---

*Anda telah belajar cara memulihkan file DOCX yang rusak, mengaktifkan mode pemulihan, dan memverifikasi keberhasilan dengan memeriksa jumlah halaman. Terapkan pola ini untuk menjaga layanan pemrosesan dokumen Anda tetap tangguh dan ramah pengguna.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Memulihkan DOCX Rusak – Panduan Lengkap Mengaktifkan Mode Pemulihan & Mendapatkan Halaman](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [cara memulihkan docx – mengatur mode pemulihan & membuka file Word yang rusak](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Cara memulihkan docx – Aktifkan Mode Pemulihan & Baca Peringatan](/words/english/java/document-loading-and-saving/how-to-recover-docx-enable-recovery-mode-read-warnings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}