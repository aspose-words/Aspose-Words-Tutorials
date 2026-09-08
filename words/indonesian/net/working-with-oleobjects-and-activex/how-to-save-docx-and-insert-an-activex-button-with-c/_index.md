---
category: general
date: 2026-09-08
description: Cara menyimpan docx saat menyisipkan kontrol ActiveX di C#. Ikuti panduan
  langkah demi langkah ini untuk menambahkan tombol perintah secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: id
lastmod: 2026-09-08
og_description: Cara menyimpan docx saat menyisipkan kontrol ActiveX di C#. Tutorial
  ini memandu Anda melalui pembuatan dokumen Word secara programatis, menambahkan
  tombol perintah, dan menyimpan file.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Cara menyimpan docx dan menyematkan tombol ActiveX di C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Cara menyimpan docx dan menyisipkan tombol ActiveX dengan C#
url: /id/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyimpan docx dan menyisipkan tombol ActiveX dengan C#

Jika Anda perlu membuat dokumen Word secara programatis dan kemudian menyimpan docx dengan tombol interaktif, panduan ini menunjukkan cara melakukannya. Anda akan belajar menyisipkan kontrol ActiveX, menambahkan tombol ActiveX, dan menyimpan file .docx yang dihasilkan menggunakan C# dan pustaka Aspose.Words.

Tutorial ini mencakup setiap langkah yang diperlukan untuk **membuat dokumen Word secara programatis**, menyematkan **tombol perintah**, dan menyimpan file ke disk. Tidak diperlukan pengalaman sebelumnya dengan objek COM, tetapi Anda harus memiliki pengetahuan dasar C# dan Visual Studio terinstal.

## Prasyarat

Sebelum Anda mulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru  
* Visual Studio 2022 (atau IDE C# apa pun)  
* Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
* Pemahaman tentang struktur proyek C#  

Item-item ini menjamin bahwa kode dapat dikompilasi dan dijalankan tanpa konfigurasi tambahan.

## Langkah 1: Siapkan proyek konsol C# baru

Buat aplikasi konsol yang akan menampung logika otomatisasi Word.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Perintah di atas membuat folder bernama **WordActiveXDemo**, menambahkan referensi Aspose.Words, dan menyiapkan proyek untuk kompilasi.

## Langkah 2: Buat dokumen Word secara programatis

Buka file `Program.cs` yang dihasilkan dan tambahkan direktif `using` yang diperlukan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Sekarang buat instance `Document` kosong. Objek ini mewakili seluruh file Word dalam memori.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

`Document` class adalah titik masuk untuk semua operasi pengolahan Word. Pada tahap ini dokumen tidak memiliki halaman, tetapi Aspose.Words akan secara otomatis membuat bagian default ketika Anda menambahkan konten.

## Langkah 3: Sisipkan kontrol ActiveX – tambahkan tombol activex

Sebuah objek **Forms2OleControl** memungkinkan Anda menyematkan kontrol ActiveX di dalam paragraf Word. Kode berikut menyisipkan **CommandButton** dengan lebar 150 pt dan tinggi 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` membuat kontrol dan mengembalikan instance `Forms2OleControl` yang kuat‑tipe, yang dapat Anda konfigurasikan lebih lanjut. Metode ini secara otomatis menambahkan paragraf baru untuk menampung kontrol, sehingga Anda tidak perlu mengelola objek paragraf secara manual.

## Langkah 4: Konfigurasikan tombol perintah – cara menambahkan properti tombol perintah

Atur properti **Name** dan **Caption** tombol agar dapat diidentifikasi pada runtime dan ramah pengguna di UI.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

Atribut `Name` berguna ketika Anda nanti menangani peristiwa klik tombol melalui VBA atau makro Word. `Caption` adalah teks yang dilihat pengguna akhir pada permukaan tombol.

### Tips Pro
Jika Anda berencana mengotomatisasi penanganan klik dari C#, sisipkan makro VBA yang merujuk ke `cmdSubmit`. Word akan meminta pengguna untuk mengaktifkan makro saat dokumen dibuka, yang merupakan perilaku keamanan standar untuk kontrol ActiveX.

## Langkah 5: Cara menyimpan docx

Setelah kontrol berada di tempatnya, simpan dokumen ke file .docx. Metode `Save` secara otomatis memilih format yang tepat berdasarkan ekstensi file.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Menyimpan file menyelesaikan alur kerja **cara menyimpan docx**. File yang dihasilkan dapat dibuka di Microsoft Word, di mana tombol ActiveX akan muncul di halaman pertama. Saat Anda mengklik tombol, Word akan menampilkan pesan placeholder kecuali ada makro yang terlampir.

## Langkah 6: Jalankan program dan verifikasi hasil

Kompilasi dan jalankan aplikasi konsol:

```bash
dotnet run
```

Setelah program selesai, buka `C:\Temp\CommandButton.docx` di Microsoft Word:

* Dokumen berisi satu halaman dengan tombol **Submit** di bagian atas.  
* Mengarahkan kursor ke tombol menampilkan tooltip dengan nama `cmdSubmit`.  
* Tidak ada konten yang hilang, dan ukuran file sebanding dengan .docx kosong standar.

Jika tombol tidak muncul, pastikan bahwa:

1. Pengaturan **Trust Center** Word mengizinkan kontrol ActiveX.  
2. File disimpan dengan ekstensi `.docx` (bukan `.doc`).  

## Kasus tepi dan variasi umum

| Situasi | Penyesuaian yang disarankan |
|-----------|------------------------|
| Anda membutuhkan ukuran tombol yang berbeda | Ubah argumen lebar dan tinggi pada `InsertForms2OleControl`. |
| Anda menginginkan tombol pada halaman tertentu | Gunakan `builder.MoveToDocumentEnd();` setelah menambahkan halaman, atau sisipkan pemisah halaman sebelum kontrol. |
| Anda harus mendukung lingkungan tanpa Aspose.Words | Gunakan Open XML SDK untuk menyisipkan elemen `w:object`, tetapi kode menjadi jauh lebih kompleks. |
| Dokumen yang mendukung makro diperlukan | Simpan dengan ekstensi `.docm` (`document.Save("MyDoc.docm");`) dan sisipkan modul VBA yang menangani `cmdSubmit_Click`. |

## Kode sumber lengkap

Berikut adalah program lengkap yang berdiri sendiri yang dapat Anda salin ke `Program.cs` dan jalankan tanpa modifikasi (kecuali jalur output).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Output yang diharapkan di konsol

```
Document saved to C:\Temp\CommandButton.docx
```

Membuka file di Word menampilkan tombol berlabel **Submit**. Mengklik tombol memicu perilaku default ActiveX (kotak pesan yang menunjukkan bahwa tidak ada makro yang terlampir).

## Kesimpulan

Tutorial ini menunjukkan **cara menyimpan docx** sambil menyematkan **kontrol ActiveX**, khususnya **menambahkan tombol activex** yang berfungsi sebagai tombol perintah. Anda kini tahu cara **membuat dokumen Word secara programatis**, mengonfigurasi properti tombol, dan menyimpan file untuk interaksi pengguna akhir.

Dari sini Anda dapat mengeksplorasi:

* Menambahkan makro VBA untuk menangani `cmdSubmit_Click`.  
* Menyisipkan kontrol ActiveX lain seperti kotak centang atau kotak kombo.  
* Menghasilkan dokumen multi‑halaman dengan banyak elemen interaktif.  

Bereksperimenlah dengan berbagai jenis kontrol dan opsi tata letak untuk membangun templat Word yang kaya dan interaktif yang menyederhanakan proses bisnis Anda.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [how to recover docx – C# guide for corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [How to Save Word as Markdown – Complete C# Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}