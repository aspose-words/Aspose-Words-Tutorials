---
category: general
date: 2026-08-10
description: Buat dokumen Word secara programatis dengan Aspose.Words, kemudian tambahkan
  tombol kontrol ActiveX. Sisipkan tombol perintah ActiveX dalam hitungan menit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: id
lastmod: 2026-08-10
og_description: Buat dokumen Word secara programatis menggunakan Aspose.Words, lalu
  tambahkan tombol kontrol ActiveX. Pelajari cara menyisipkan tombol perintah ActiveX
  dengan cepat.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Buat dokumen Word secara programatis – tambahkan tombol ActiveX di C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Buat dokumen Word secara programatis dan tambahkan tombol ActiveX
url: /id/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word secara programatis dan tambahkan tombol ActiveX

Jika Anda perlu **membuat dokumen Word secara programatis**, panduan ini akan memandu Anda melalui seluruh proses dengan Aspose.Words untuk .NET. Anda juga akan belajar cara **menambahkan elemen kontrol activex word** dan **menyisipkan objek tombol perintah activex** dalam satu contoh yang berdiri sendiri.

Membuat file Word dari kode menghilangkan langkah manual membuka Microsoft Word, memungkinkan Anda membuat laporan, faktur, atau kontrak berbasis data secara otomatis. Pada akhir tutorial ini Anda akan memiliki aplikasi konsol C# yang siap dijalankan yang menghasilkan file `.docx` berisi ActiveX CommandButton interaktif.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau lebih baru (kode juga bekerja dengan .NET Framework 4.6+)
* Visual Studio 2022 atau IDE apa pun yang mendukung pengembangan .NET
* Lisensi Aspose.Words untuk .NET yang valid (Anda dapat menggunakan kunci evaluasi gratis untuk pengujian)
* Pemahaman dasar tentang sintaks C# dan konsep kontrol COM/ActiveX

> **Tips pro:** Jika Anda berencana mendistribusikan dokumen yang dihasilkan kepada pengguna yang tidak memiliki Word terpasang, sematkan file runtime kontrol ActiveX bersama `.docx` atau sediakan templat yang mendukung macro.

## Buat dokumen Word secara programatis – pengaturan awal

Pertama, tambahkan paket NuGet Aspose.Words ke proyek Anda:

```bash
dotnet add package Aspose.Words
```

Kemudian buat proyek konsol baru (jika Anda belum memilikinya):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Buka file `Program.cs` yang dihasilkan – kami akan mengganti isinya dengan solusi lengkap di bawah ini.

## Langkah 1: Impor namespace dan konfigurasikan lisensi

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Mengapa ini penting*: Mengimpor `Aspose.Words.Drawing` memberi Anda akses ke `Forms2OleControl`, kelas yang mewakili kontrol ActiveX di dalam dokumen Word. Menetapkan lisensi sejak awal mencegah peringatan runtime di produksi.

## Langkah 2: Buat dokumen kosong dan DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Objek `Document` adalah representasi dalam memori dari file `.docx`. `DocumentBuilder` berfungsi seperti kursor yang Anda gerakkan di sekitar dokumen untuk menyisipkan elemen.

## Langkah 3: Sisipkan kontrol ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` membuat objek OLE yang diperlakukan Word sebagai kontrol ActiveX. Sistem koordinat menggunakan poin (1 poin = 1/72 inci), yang sesuai dengan mesin tata letak Word.

## Langkah 4: Atur caption tombol dan properti opsional

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Mengatur properti `Caption` adalah cara paling umum untuk memberi label pada tombol. Jika Anda perlu tombol mengeksekusi macro VBA, tetapkan nama macro ke `OnAction`. Tutorial ini fokus pada bagian visual; integrasi macro dibahas di bagian “Langkah selanjutnya”.

## Langkah 5: Simpan dokumen

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Saat Anda menjalankan program, Anda akan melihat pesan konsol yang mengonfirmasi bahwa `ActiveX_CommandButton.docx` telah ditulis ke disk.

### Kode sumber lengkap (siap salin‑tempel)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Menjalankan potongan kode menghasilkan file Word yang berisi **tombol perintah ActiveX** yang dapat diklik. Buka file di Microsoft Word, beralih ke **Design Mode** (tab Developer → Design Mode), dan Anda akan melihat tombol ditampilkan tepat di tempat Anda menaruhnya.

## Langkah 6: Verifikasi hasil

1. Buka `ActiveX_CommandButton.docx` di Microsoft Word.
2. Aktifkan tab **Developer** jika tidak terlihat (`File → Options → Customize Ribbon → centang Developer`).
3. Klik **Design Mode**. Tombol harus muncul dengan label “Submit”.
4. Jika Anda menambahkan macro `OnAction`, klik tombol saat Design Mode dimatikan untuk memicu macro.

Jika tombol tidak muncul, pastikan pengaturan keamanan Word mengizinkan kontrol ActiveX (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Pertanyaan umum dan kasus tepi

| Question | Answer |
|----------|--------|
| **Apakah saya dapat menyisipkan tipe ActiveX lain?** | Ya. Enum `Forms2OleControlType` mencakup `CheckBox`, `OptionButton`, `ComboBox`, dll. Ganti `CommandButton` dengan nilai enum yang diinginkan |

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat Dokumen Word dengan Header dan Footer Menggunakan Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Sisipkan Gambar Inline dalam Dokumen Word menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}