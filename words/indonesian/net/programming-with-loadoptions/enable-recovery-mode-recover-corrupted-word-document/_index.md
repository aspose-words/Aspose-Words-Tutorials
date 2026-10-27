---
category: general
date: 2026-07-06
description: Aktifkan mode pemulihan untuk membuka file docx yang rusak dengan Aspose.Words.
  Pelajari cara memulihkan dokumen Word yang rusak dengan cepat.
draft: false
keywords:
- enable recovery mode
- recover corrupted word document
- recover damaged docx file
- how to open corrupted docx
language: id
og_description: Mengaktifkan mode pemulihan memungkinkan Anda membuka file docx yang
  rusak dan mencoba memulihkan dokumen Word yang rusak.
og_title: Aktifkan mode pemulihan – Pulihkan dokumen Word yang rusak
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Enable recovery mode to open a corrupted docx file with Aspose.Words.
    Learn how to recover corrupted Word document quickly.
  headline: Enable recovery mode – Recover corrupted Word document
  type: TechArticle
- questions:
  - answer: No. It only affects how the library reads the file in memory. The source
      remains untouched unless you explicitly call `Save`.
    question: Does enabling recovery mode modify the original file?
  - answer: Usually yes, as long as the underlying ZIP entry isn’t broken. If an image
      stream is missing, Aspose.Words will skip it and continue.
    question: Can I recover images that were embedded in the corrupted docx?
  - answer: Slightly, because the parser performs additional checks. The overhead
      is negligible for typical documents (<10 MB).
    question: Is recovery mode slower?
  - answer: '`RecoveryMode.Auto` (default) tries to recover only when an error occurs.
      `RecoveryMode.None` disables any recovery attempts. `RecoveryMode.Recover` forces
      the attempt every time. ## Full Working Example Below is a self‑contained console
      app you can copy‑paste into a new .NET project. It demonstrate'
    question: What other recovery options exist?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Document Recovery
- Word
title: Aktifkan mode pemulihan – Pulihkan dokumen Word yang rusak
url: /id/net/programming-with-loadoptions/enable-recovery-mode-recover-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktifkan mode pemulihan – Pulihkan dokumen Word yang rusak

Pernah mencoba membuka **docx yang rusak** dan melihat dialog error menatap kembali Anda? Itu menjengkelkan, terutama ketika file tersebut berisi minggu‑minggu kerja. Untungnya, Aspose.Words memberi Anda cara untuk *mengaktifkan mode pemulihan* sehingga Anda dapat mencoba menyelamatkan kontennya tanpa menyalin‑tempel secara manual.

Dalam panduan ini kami akan membahas langkah‑langkah tepat untuk **mengaktifkan mode pemulihan**, memuat file yang rusak, dan menyimpan salinan yang dapat digunakan. Pada akhir panduan Anda akan tahu cara *memulihkan dokumen Word yang rusak* secara programatis dan bahkan menangani skenario *memulihkan file docx yang rusak* dengan elegan.

## Apa yang Anda butuhkan

- .NET 6 (atau runtime .NET terbaru apa pun) – perpustakaan ini juga bekerja pada .NET Framework.  
- Visual Studio 2022 atau VS Code – IDE favorit Anda sudah cukup.  
- **Aspose.Words for .NET** paket NuGet (`Install-Package Aspose.Words`) – ini satu‑satunya ketergantungan eksternal.  
- Contoh file `docx` yang rusak (kami akan menyebutnya `corrupted.docx`).  

Itu saja. Tidak ada alat tambahan, tidak ada pengutak‑utakan XML manual. Hanya beberapa baris C#.

![aktifkan mode pemulihan di Aspose.Words](image-url-placeholder.png)

*​Teks alt gambar: aktifkan mode pemulihan di Aspose.Words*

## Langkah 1: Instal Aspose.Words dan siapkan proyek

Buka terminal Anda (atau Package Manager Console) dan jalankan:

```bash
dotnet add package Aspose.Words
```

Atau, di Visual Studio buka **Tools → NuGet Package Manager → Manage NuGet Packages** dan cari *Aspose.Words*. Setelah terpasang, tambahkan namespace di bagian atas file Anda:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **Tip Pro:** Jaga paket Anda tetap terbaru. Logika pemulihan meningkat pada setiap rilis.

## Langkah 2: Aktifkan mode pemulihan menggunakan `LoadOptions`

Inti dari solusi ini adalah kelas `LoadOptions`. Dengan mengatur properti `RecoveryMode`‑nya menjadi `RecoveryMode.Recover`, Anda memberi tahu Aspose.Words untuk *mengaktifkan mode pemulihan* saat mem‑parsing dokumen.

```csharp
// Step 2: Create LoadOptions and enable recovery mode
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover   // <-- this line turns on recovery
};
```

Mengapa ini penting? Tanpa mode pemulihan, Aspose.Words akan menghentikan proses pada tanda pertama kerusakan. Dengan mode ini, perpustakaan berusaha sebaik mungkin melewati bagian yang rusak dan tetap menghasilkan objek `Document` yang dapat digunakan.

## Langkah 3: Muat file yang berpotensi rusak

Sekarang kita benar‑benarnya memuat file tersebut. Jika dokumen tidak dapat diperbaiki, Aspose.Words tetap akan mengembalikan instance `Document`, namun beberapa elemen mungkin hilang.

```csharp
// Step 3: Load the potentially corrupted document using the recovery options
Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
```

Perhatikan bahwa path adalah string absolut; sesuaikan dengan lokasi file uji Anda. Konstruktor `Document` membaca file **dengan mode pemulihan diaktifkan**, memberi Anda kesempatan untuk *memulihkan konten dokumen Word yang rusak*.

## Langkah 4: Verifikasi apa yang telah dipulihkan (opsional namun berguna)

Sebaiknya periksa dokumen yang dimuat sebelum Anda memutuskan menimpa apa pun. Untuk pemeriksaan cepat, Anda dapat mencetak beberapa paragraf pertama ke konsol:

```csharp
// Optional: Print first 3 paragraphs to verify recovery
for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
{
    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
}
```

Jika Anda melihat teks berantakan atau banyak string kosong, file mungkin **terlalu rusak**. Namun, Anda kini memiliki objek `Document` yang dapat dimanipulasi—menambah header, mengganti gambar yang hilang, dll.

## Langkah 5: Simpan dokumen yang dipulihkan

Dengan asumsi pemeriksaan cepat terlihat baik, tulis versi yang dipulihkan ke file baru. Langkah ini secara efektif *memulihkan file docx yang rusak* dan memberi Anda salinan bersih yang dapat dibuka di Word.

```csharp
// Step 5: Save the recovered document
string outputPath = @"C:\Temp\recovered.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Recovered document saved to: {outputPath}");
```

Jika file asli berupa `.doc` atau format lain, Anda dapat mengubah `SaveFormat` sesuai (misalnya, `SaveFormat.Pdf` untuk output PDF).

## Langkah 6: Menangani pengecualian dan kasus tepi

Bahkan dengan mode pemulihan, beberapa bencana tidak dapat dipulihkan (mis., struktur zip yang terpotong sepenuhnya). Bungkus proses pemuatan dalam blok try‑catch untuk menampilkan masalah tersebut:

```csharp
try
{
    Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
    // proceed with saving...
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to recover the document: {ex.Message}");
    // You might log the stack trace or notify the user.
}
```

Pertanyaan umum adalah **“bagaimana membuka docx yang rusak”** ketika file dilindungi kata sandi. Mode pemulihan **tidak** melewati enkripsi; Anda tetap memerlukan kata sandi. Dalam kasus tersebut, atur `LoadOptions.Password` sebelum memuat.

## Pertanyaan yang Sering Diajukan (FAQ)

**Q: Apakah mengaktifkan mode pemulihan mengubah file asli?**  
A: Tidak. Itu hanya memengaruhi cara perpustakaan membaca file di memori. Sumber tetap tidak tersentuh kecuali Anda secara eksplisit memanggil `Save`.

**Q: Bisakah saya memulihkan gambar yang tertanam dalam docx yang rusak?**  
A: Biasanya ya, selama entri ZIP yang mendasarinya tidak rusak. Jika aliran gambar hilang, Aspose.Words akan melewatinya dan melanjutkan.

**Q: Apakah mode pemulihan lebih lambat?**  
A: Sedikit, karena parser melakukan pemeriksaan tambahan. Beban tambahan tidak signifikan untuk dokumen tipikal (<10 MB).

**Q: Opsi pemulihan lain apa yang tersedia?**  
A: `RecoveryMode.Auto` (default) mencoba memulihkan hanya ketika terjadi error. `RecoveryMode.None` menonaktifkan semua upaya pemulihan. `RecoveryMode.Recover` memaksa upaya pemulihan setiap kali.

## Contoh Kerja Lengkap

Berikut adalah aplikasi konsol mandiri yang dapat Anda salin‑tempel ke proyek .NET baru. Aplikasi ini menunjukkan alur lengkap—dari instalasi paket hingga penyimpanan file yang dipulihkan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace RecoverCorruptedDocx
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the corrupted document
            string inputPath = @"C:\Temp\corrupted.docx";
            // Where the recovered file will be written
            string outputPath = @"C:\Temp\recovered.docx";

            // Step 1: Create LoadOptions and enable recovery mode
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Recover
            };

            try
            {
                // Step 2: Load the document with recovery enabled
                Document doc = new Document(inputPath, loadOptions);

                // Optional sanity check – print first three paragraphs
                Console.WriteLine("=== First three paragraphs after recovery ===");
                for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
                {
                    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
                }

                // Step 3: Save the recovered document
                doc.Save(outputPath, SaveFormat.Docx);
                Console.WriteLine($"\nRecovered document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to open or recover the document: {ex.Message}");
            }
        }
    }
}
```

**Output yang diharapkan (asumsi pemulihan berhasil):**

```
=== First three paragraphs after recovery ===
Paragraph 1: Project Overview
Paragraph 2: This document outlines...
Paragraph 3: ...

Recovered document saved to: C:\Temp\recovered.docx
```

Jika file tidak dapat diselamatkan, Anda akan melihat pesan error alih‑alih dump paragraf.

## Kesimpulan

Kami baru saja menunjukkan cara **mengaktifkan mode pemulihan** di Aspose.Words, memuat `docx` yang rusak, dan **memulihkan data dokumen Word yang rusak** ke dalam file baru. Pola yang sama memungkinkan Anda *memulihkan file docx yang rusak* dalam pekerjaan batch, lampiran email otomatis, atau

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [cara memulihkan docx – atur mode pemulihan & buka file Word yang rusak](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [cara memulihkan docx dengan Aspose.Words – langkah demi langkah](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Pulihkan File Word Rusak – Panduan Lengkap Membuka DOCX yang Rusak & Mendapatkan Halaman](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}