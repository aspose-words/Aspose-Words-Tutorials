---
category: general
date: 2026-06-08
description: Buka file Word yang rusak di C# menggunakan Aspose.Words. Pelajari cara
  mengatur mode pemulihan dan memulihkan dokumen yang rusak secara efisien.
draft: false
keywords:
- open corrupted word file
- set recovery mode
- recover corrupted document
- Aspose.Words recovery
- handling damaged docx
language: id
og_description: Buka file Word yang rusak di C# dengan Aspose.Words. Panduan ini menunjukkan
  cara mengatur mode pemulihan dan memulihkan dokumen yang rusak dengan aman.
og_title: Buka File Word Rusak di C# – Panduan Langkah demi Langkah
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  headline: Open Corrupted Word File in C# – Complete Guide
  type: TechArticle
- description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  name: Open Corrupted Word File in C# – Complete Guide
  steps:
  - name: '**Create `LoadOptions`** – decide how strict the loader should be.'
    text: '**Create `LoadOptions`** – decide how strict the loader should be.'
  - name: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
    text: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
  - name: '**Load the document** – give the path and the options you just built.'
    text: '**Load the document** – give the path and the options you just built.'
  - name: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
    text: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
  type: HowTo
tags:
- C#
- Aspose.Words
- Document Recovery
title: Membuka File Word yang Rusak di C# – Panduan Lengkap
url: /id/net/programming-with-loadoptions/open-corrupted-word-file-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buka File Word Rusak di C# – Panduan Lengkap

Pernahkah Anda perlu **membuka file word yang rusak** dalam proyek .NET dan bertanya-tanya apakah file tersebut tidak dapat diperbaiki? Anda bukan yang pertama—korupsi dokumen muncul lebih sering daripada yang Anda kira, terutama ketika file berpindah melalui jaringan yang tidak stabil atau diedit oleh versi Office yang lebih lama.  

Kabar baiknya? Dengan Aspose.Words Anda dapat **set recovery mode** untuk memberi tahu perpustakaan cara berperilaku yang tepat, dan bahkan dapat **recover corrupted document** tanpa menulis parser khusus. Dalam tutorial ini kami akan membahas setiap langkah, mulai dari mengonfigurasi opsi hingga memverifikasi bahwa file terbuka dengan benar.

> **Apa yang akan Anda dapatkan**  
> • Potongan kode C# yang berfungsi untuk membuka file .docx apa pun, bahkan yang rusak.  
> • Pemahaman tentang tiga nilai `RecoveryMode` dan kapan menggunakannya.  
> • Tips menangani pengecualian, menguji hasil, dan secara opsional menyimpan salinan bersih.

## Cara Membuka File Word Rusak dengan Aspose.Words

Berikut adalah gambaran tingkat tinggi dari alur.  
![Diagram yang menggambarkan proses membuka file word yang rusak](/images/open-corrupted-word-file-flow.png){: .center alt="diagram alur membuka file word yang rusak"}

1. **Buat `LoadOptions`** – tentukan seberapa ketat pemuat harusnya.  
2. **Pilih `RecoveryMode`** – *Passthrough* untuk pemuatan mentah, *Recover* untuk perbaikan otomatis, atau *Throw* untuk menangkap masalah lebih awal.  
3. **Muat dokumen** – berikan jalur dan opsi yang baru saja Anda buat.  
4. **Validasi** – periksa bahwa pohon dokumen tidak kosong, opsional menyimpan salinan yang diperbaiki.

Mari kita selami setiap bagian.

## Memahami Mode Pemulihan

Aspose.Words mendefinisikan tiga perilaku berbeda:

| Mode | Apa yang dilakukannya | Kapan menggunakannya |
|------|-----------------------|----------------------|
| `RecoveryMode.Recover` | Mencoba memperbaiki masalah struktural, bagian yang hilang, atau XML yang tidak terbentuk dengan benar. Ini adalah **default** dan bekerja untuk sebagian besar korupsi kecil. | Anda menginginkan perbaikan sebaik mungkin tanpa intervensi manual. |
| `RecoveryMode.Passthrough` | Memuat file **tepat** sebagaimana adanya, bahkan jika mengandung bagian yang rusak. Tidak ada perbaikan otomatis yang diterapkan. | Anda perlu memeriksa konten mentah, atau Anda berencana menerapkan logika pemulihan khusus nanti. |
| `RecoveryMode.Throw` | Langsung melemparkan pengecualian jika ada masalah terdeteksi. | Anda lebih suka pendekatan gagal cepat untuk menolak file yang rusak secara langsung. |

Memilih mode yang tepat adalah inti dari **set recovery mode** dengan benar. Kebanyakan pengembang memulai dengan `Recover`, tetapi jika Anda sedang men-debug file yang membandel, `Passthrough` dapat memberi Anda visibilitas tentang apa yang salah.

## Langkah‑per‑Langkah: Atur Mode Pemulihan

Berikut adalah blok kode pertama yang akan Anda tempel ke aplikasi konsol baru atau proyek C# apa pun yang sudah merujuk `Aspose.Words`.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 1: Create LoadOptions and choose a recovery behavior
LoadOptions loadOptions = new LoadOptions
{
    // Choose the desired recovery behavior:
    //   RecoveryMode.Recover      – attempt to fix the file (default)
    //   RecoveryMode.Passthrough – load the file exactly as it is
    //   RecoveryMode.Throw       – throw an exception if the file is damaged
    RecoveryMode = RecoveryMode.Passthrough   // <-- we are explicitly setting it
};
```

**Mengapa ini penting:** Dengan secara eksplisit menetapkan `RecoveryMode.Passthrough`, kami memberi tahu Aspose.Words **set recovery mode** ke nilai non‑default. Ini menghilangkan tebakan dan membuat niat menjadi sangat jelas bagi pemelihara di masa depan.

> **Pro tip:** Jika Anda pernah perlu kembali ke jalur perbaikan otomatis, cukup ubah enum menjadi `RecoveryMode.Recover` dan jalankan kembali—tidak ada perubahan kode lain yang diperlukan.

## Memuat Dokumen dengan Aman

Sekarang opsi sudah siap, langkah berikutnya adalah benar‑benarnya **membuka file word yang rusak**. Potongan kode berikut menunjukkan proses pemuatan dan menyertakan pemeriksaan sederhana.

```csharp
// Step 2: Load the possibly‑corrupted document using the configured options
try
{
    // Replace the path with the location of your damaged DOCX
    Document doc = new Document(@"C:\Temp\Corrupted.docx", loadOptions);

    // Quick validation – make sure the document contains at least one section
    if (doc.Sections.Count == 0)
    {
        Console.WriteLine("The document appears empty after loading. It may be severely corrupted.");
    }
    else
    {
        Console.WriteLine($"Successfully opened the file. Sections found: {doc.Sections.Count}");
    }
}
catch (Exception ex)
{
    // If you used RecoveryMode.Throw, you'll land here for any problem.
    Console.WriteLine($"Failed to open the file: {ex.Message}");
}
```

**Penjelasan:**  
* Blok `try/catch` melindungi kita dari mode `Throw`, tetapi juga berfungsi sebagai jaring pengaman untuk kesalahan I/O yang tidak terduga.  
* Setelah memuat, kita memeriksa `doc.Sections.Count`. Jumlah nol merupakan indikator kuat bahwa file tidak berhasil memulihkan konten yang berarti—sempurna untuk mengonfirmasi apakah **recover corrupted document** benar‑benar berhasil.

## Menangani Pengecualian dan Memverifikasi Pemulihan

Bahkan dengan `Passthrough`, perpustakaan masih dapat melempar pengecualian jika paket ZIP yang mendasarinya tidak dapat dibaca. Berikut cara membedakan antara masalah *yang dapat dipulihkan* dan *yang fatal*:

```csharp
catch (CorruptedFileException cfe)
{
    // This exception means the file's internal structure is broken.
    Console.WriteLine("CorruptedFileException caught – the file cannot be read at all.");
}
catch (Exception ex)
{
    // Any other exception (e.g., FileNotFound, UnauthorizedAccess)
    Console.WriteLine($"General error: {ex.GetType().Name} – {ex.Message}");
}
```

Jika Anda melihat `CorruptedFileException`, Anda mungkin ingin beralih ke strategi pemulihan lain, seperti:

* Mencoba `RecoveryMode.Recover` alih‑alih `Passthrough`.  
* Menggunakan alat perbaikan ZIP pihak ketiga sebelum memberi file ke Aspose.Words.  
* Meminta pengguna mengunggah salinan baru.

## Bonus: Menyimpan Dokumen yang Diperbaiki

Setelah Anda **recover corrupted document** kontennya, Anda sering ingin menyimpan versi bersih. Kode berikut menulis file yang diperbaiki ke lokasi baru:

```csharp
// Assuming 'doc' was loaded successfully
string outputPath = @"C:\Temp\Repaired.docx";

doc.Save(outputPath, SaveFormat.Docx);
Console.WriteLine($"Repaired document saved to: {outputPath}");
```

Menyimpan juga berfungsi sebagai langkah verifikasi implisit—jika `doc.Save` melempar, masih ada yang tidak beres dengan pohon node internal.

## Tips untuk Skenario Pemulihan Dokumen Rusak

| Situasi | Tindakan yang Disarankan |
|-----------|--------------------------|
| Kesalahan kecil XML (misalnya, tag penutup yang hilang) | Pertahankan `RecoveryMode.Recover`; Aspose.Words akan memperbaikinya secara otomatis. |
| Arsip ZIP yang sepenuhnya rusak | Gunakan perbaikan ZIP eksternal, lalu muat dengan `Passthrough`. |
| Mode campuran (beberapa bagian baik, lainnya rusak) | Muat dengan `Passthrough`, periksa node yang bermasalah, lalu secara manual menghapus atau menggantinya. |
| Korupsi sering dari sumber tertentu | Otomatiskan pemeriksaan pra‑proses yang menjalankan `RecoveryMode.Recover` dan mencatat setiap `CorruptedFileException`. |

Ingat, **set recovery mode** bukan tongkat sihir—memahami sifat korupsi membantu Anda memilih strategi yang tepat.

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut adalah aplikasi konsol mandiri yang dapat Anda tempel ke `Program.cs` dan jalankan langsung (setelah menambahkan paket NuGet Aspose.Words).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace OpenCorruptedWordFileDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure load options – we explicitly set the recovery mode.
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Passthrough // change to Recover if you prefer auto‑fix
            };

            // 2️⃣ Attempt to load the possibly damaged DOCX.
            string sourcePath = @"C:\Temp\Corrupted.docx";
            Document doc = null;

            try
            {
                doc = new Document(sourcePath, loadOptions);
                Console.WriteLine($"File loaded. Sections: {doc.Sections.Count}");
            }
            catch (CorruptedFileException)
            {
                Console.WriteLine("The file is too damaged to be opened even in Passthrough mode.");
                return;
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.Message}");
                return;
            }

            // 3️⃣ Simple verification – ensure we have at least one paragraph.
            if (doc.GetChildNodes(NodeType.Paragraph, true).Count == 0)
            {
                Console.WriteLine("No paragraphs were recovered – the document may be empty.");
            }
            else
            {
                Console.WriteLine("Paragraphs recovered – the document appears usable.");
            }

            // 4️⃣ Optionally save a clean copy.
            string cleanPath = @"C:\Temp\Repaired.docx";
            doc.Save(cleanPath, SaveFormat.Docx);
            Console.WriteLine($"Clean copy saved to: {cleanPath}");
        }
    }
}
```

**Output yang diharapkan (ketika file dapat dibuka):**



## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [cara memulihkan docx – atur mode pemulihan & buka file Word yang rusak](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Pulihkan File Word Rusak – Panduan Lengkap Membuka DOCX Rusak & Mendapatkan Halaman](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)
- [Pulihkan Dokumen Word dengan Aspose.Words di C#](/words/english/net/programming-with-loadoptions/recover-word-document-with-aspose-words-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}