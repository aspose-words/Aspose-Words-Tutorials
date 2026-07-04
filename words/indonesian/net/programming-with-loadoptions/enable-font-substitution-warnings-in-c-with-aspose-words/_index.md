---
category: general
date: 2026-06-20
description: Aktifkan peringatan substitusi font di C# menggunakan Aspose.Words. Pelajari
  cara mengonfigurasi LoadOptions, menangkap peringatan, dan menangani font yang hilang
  secara efisien.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: id
og_description: Aktifkan peringatan substitusi font di C# dengan Aspose.Words. Panduan
  ini menunjukkan cara mengatur LoadOptions, membaca WarningInfo, dan menampilkan
  pesan font yang hilang.
og_title: Aktifkan Peringatan Substitusi Font di C# – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Aktifkan Peringatan Substitusi Font di C# dengan Aspose.Words
url: /id/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktifkan Peringatan Substitusi Font di C# dengan Aspose.Words

Pernah bertanya-tanya bagaimana **mengaktifkan peringatan substitusi font** ketika dokumen Word merujuk ke font yang tidak terpasang di server? Anda tidak sendirian. Font yang hilang dapat secara diam‑diam merusak tata letak PDF atau gambar yang dihasilkan, dan satu‑satunya cara untuk menangkapnya lebih awal adalah dengan mendengarkan peringatan yang dikeluarkan Aspose.Words.

Dalam tutorial ini kami akan menuntun Anda melalui contoh praktis yang menunjukkan secara tepat cara menyalakan peringatan tersebut, mengambilnya dari koleksi `WarningInfo`, dan mencetak pesan yang bermakna ke konsol. Pada akhir tutorial Anda akan tahu cara mengonfigurasi **Aspose.Words LoadOptions**, menangani **peringatan substitusi font C#**, dan membuat alur pemrosesan dokumen Anda tahan banting.

Kami juga akan menyentuh beberapa kasus tepi—apa yang terjadi jika Anda menekan peringatan, atau jika Anda perlu mencatatnya alih‑alih mencetak—serta memberikan contoh kode lengkap yang siap salin‑tempel dan bekerja dengan Aspose.Words for .NET versi terbaru (versi 24.10).

## Apa yang Anda Butuhkan

- .NET 6.0 atau lebih baru (kode juga berfungsi pada .NET Framework 4.7+)
- Referensi NuGet ke `Aspose.Words` (pasang via `dotnet add package Aspose.Words`)
- File Word yang merujuk ke font yang **tidak** Anda miliki (misalnya `DocumentWithMissingFont.docx`)
- IDE yang memadai (Visual Studio, Rider, atau VS Code)

Itu saja—tanpa layanan tambahan, tanpa alat proprietari. Siap? Mari kita mulai.

## Langkah 1: Aktifkan Peringatan Substitusi Font

Hal pertama yang harus Anda lakukan adalah memberi tahu Aspose.Words bahwa Anda ingin diberi tahu ketika ia menggantikan font yang hilang. Ini dilakukan melalui properti `FontSettings` dari objek `LoadOptions`. Secara default, peringatan **dinonaktifkan** agar API tetap tenang, jadi kita harus mengaktifkannya secara manual.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Mengapa ini berhasil:** Ketika `FontSettings` tidak `null`, perpustakaan secara otomatis mengisi `Document.WarningInfo` dengan entri `WarningType.FontSubstitution` yang ditemukannya saat memuat dokumen. Anggap saja ini seperti menyalakan “mode debug” untuk font.

## Langkah 2: Muat Dokumen dengan Opsi yang Dikonfigurasi

Setelah koleksi peringatan aktif, muat dokumen Anda menggunakan `LoadOptions` yang baru saja kita siapkan. Jika dokumen berisi font yang hilang, Aspose.Words akan menggantinya dengan fallback dan menambahkan peringatan ke daftar `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Tips pro:** Jika Anda memproses banyak file dalam sebuah loop, gunakan kembali instance `LoadOptions` yang sama—membuatnya sekali dapat menghemat beberapa milidetik per iterasi.

## Langkah 3: Iterasi `WarningInfo` dan Tampilkan Pesan Substitusi Font

Setelah dokumen dimuat, koleksi `WarningInfo` berisi setiap peringatan yang terjadi selama pemuatan. Kita hanya tertarik pada `WarningType.FontSubstitution`, jadi kita menyaringnya sesuai kebutuhan.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Menjalankan potongan kode di atas pada dokumen yang merujuk ke font “Papyrus” yang tidak ada mungkin menghasilkan output seperti:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Itulah **pesan substitusi font** yang Anda cari—jelas, dapat ditindaklanjuti, dan siap dicatat atau dikirim ke sistem peringatan.

## Contoh Lengkap yang Berfungsi

Berikut adalah program konsol mandiri yang menggabungkan semuanya. Salin‑tempel ke proyek `.csproj` baru dan jalankan **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Output yang Diharapkan

Jika dokumen merujuk ke font yang tidak terpasang, Anda akan melihat sesuatu yang mirip dengan:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Jika semua font tersedia di mesin, program hanya akan mencetak:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Kesalahan Umum & Tips Pro

| Masalah | Mengapa Terjadi | Cara Memperbaiki / Menghindari |
|---------|-----------------|--------------------------------|
| **Peringatan menghilang** | Anda menghapus `FontSettings` atau menggunakan `LoadOptions` tanpa itu. | Selalu buat instance `FontSettings` meskipun tidak mengubah properti apa pun. |
| **Terlalu banyak peringatan** | Dokumen menggunakan banyak font eksotis. | Pertimbangkan menambahkan folder font khusus ke `FontSettings` lewat `SetFontsFolder` untuk mengurangi substitusi. |
| **Penurunan performa dalam loop ketat** | Membuat ulang `LoadOptions` setiap iterasi menambah beban. | Gunakan kembali satu instance `LoadOptions` untuk semua dokumen. |
| **Tidak ada output di konsol** | Menjalankan dalam aplikasi GUI dimana `Console.WriteLine` diabaikan. | Alihkan peringatan ke logger (`ILogger`) atau tulis ke file. |

### Menangani Peringatan dalam Layanan Dunia Nyata

Di API web Anda mungkin tidak ingin menulis ke konsol. Sebagai gantinya, alirkan peringatan ke log terstruktur:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Dengan cara ini Anda tetap **menangani peringatan dokumen** sambil menjaga layanan tetap bersih.

## Memperluas Contoh

- **Tangkap tipe peringatan lain** (misalnya `WarningType.UnknownFileFormat`) dengan menghapus filter `if`.
- **Simpan laporan** semua peringatan ke JSON untuk analitik downstream.
- **Paksa font fallback tertentu** dengan mengatur `FontSettings.SubstitutionSettings.DefaultFontName`.

Semua ini merupakan ekstensi alami setelah Anda menguasai **mengaktifkan peringatan substitusi font**.

## Kesimpulan

Kami telah menunjukkan cara **mengaktifkan peringatan substitusi font** di C# menggunakan Aspose.Words, mulai dari mengonfigurasi `LoadOptions` hingga iterasi `WarningInfo` dan mencetak pesan yang ramah. Dengan mengikuti langkah‑langkah di atas Anda dapat melindungi alur pemrosesan dokumen dari perubahan tata letak diam‑diam yang disebabkan oleh font yang hilang.

Selanjutnya, coba tambahkan folder font khusus, catat peringatan ke file, atau bahkan kirimkan ke dasbor pemantauan. Pola yang sama berlaku untuk skenario **penanganan peringatan dokumen** apa pun, baik Anda mengonversi ke PDF, merender gambar, atau melakukan mail‑merge.

Punya pertanyaan tentang **peringatan substitusi font C#** atau ingin berbagi solusi cerdas? Tinggalkan komentar di bawah—selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}