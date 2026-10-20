---
category: general
date: 2026-08-14
description: Cara menambahkan tombol ActiveX dalam dokumen Word menggunakan Aspose.Words
  – pelajari cara membuat dokumen Word kosong dan menyisipkan tombol ActiveX secara
  programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: id
lastmod: 2026-08-14
og_description: Cara menambahkan tombol ActiveX dalam dokumen Word dengan Aspose.Words.
  Tutorial ini menunjukkan cara membuat dokumen Word kosong, menyisipkan tombol ActiveX,
  dan menyimpan hasilnya.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Cara menambahkan tombol ActiveX di Word – Panduan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Cara menambahkan tombol ActiveX dalam dokumen Word dengan Aspose.Words
url: /id/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan tombol ActiveX dalam dokumen Word dengan Aspose.Words

Jika Anda perlu **menambahkan ActiveX** ke kontrol dalam file Word yang dihasilkan, panduan ini menunjukkan langkah‑langkah tepatnya. Anda akan belajar cara **menyisipkan tombol ActiveX** secara programatis, mulai dari **membuat dokumen Word kosong** hingga file yang disimpan yang dapat dibuka di Microsoft Word.

Menambahkan tombol yang menjalankan kode VBA atau memicu makro merupakan kebutuhan umum untuk generator laporan otomatis, templat formulir, atau kontrak interaktif. Menggunakan Aspose.Words untuk .NET memungkinkan Anda membangun dokumen tanpa meluncurkan Office, sehingga proses menjadi cepat dan ramah server.

## Prerequisites

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 (atau lebih baru) SDK terpasang.
* Visual Studio 2022 atau IDE kompatibel C# lainnya.
* Paket NuGet Aspose.Words untuk .NET (`Aspose.Words` versi 24.9 atau lebih baru).  
  Instal dengan:
  ```bash
  dotnet add package Aspose.Words
  ```
* Lingkungan Windows jika Anda berencana menguji tombol ActiveX, karena kontrol ActiveX memerlukan versi Windows dari Microsoft Word.

## Step 1: Create an empty Word document

Tugas pertama adalah **membuat dokumen Word kosong** di memori. Aspose.Words menyediakan kelas `Document` untuk tujuan ini.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` mewakili seluruh file .docx. Pada titik ini dokumen belum memiliki halaman, tetapi Anda dapat mulai menambahkan konten secara langsung.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder` adalah pembantu yang memungkinkan Anda menyisipkan teks, gambar, dan objek lain ke dalam dokumen. Ia bekerja pada instance `Document` yang baru saja Anda buat.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder mempertahankan posisi kursor; apa pun yang Anda sisipkan setelah baris ini akan muncul di awal halaman pertama.

## Step 3: Insert an ActiveX CommandButton control

Aspose.Words menyediakan metode `InsertForms2OleControl` untuk menambahkan kontrol formulir warisan, termasuk ActiveX. Metode ini memerlukan tipe kontrol dan ukurannya dalam poin.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Objek `Forms2OleControl` yang dikembalikan memungkinkan Anda mengonfigurasi properti seperti nama kontrol dan caption.

## Step 4: Configure the button’s properties

Menetapkan `Name` yang bermakna memungkinkan Anda merujuk kontrol tersebut dari kode VBA nanti. `Caption` adalah teks yang dilihat pengguna pada tombol.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** Jaga nama tetap pendek dan alfanumerik; Word akan menolak nama yang mengandung spasi atau karakter khusus.

## Step 5: Save the document

Akhirnya, tulis dokumen ke disk. Gunakan ekstensi `.docx` untuk file Word modern; tombol ActiveX berfungsi dengan cara yang sama pada file `.doc`, tetapi `.docx` adalah format yang disarankan untuk proyek baru.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Saat Anda membuka `ActiveXButton.docx` di Microsoft Word, Anda akan melihat tombol **Submit** yang dapat diklik. Jika Anda mengaktifkan makro, Anda dapat melampirkan kode VBA ke `btnSubmit_Click` dan membuatnya dijalankan ketika pengguna mengklik tombol.

## Full, runnable example

Menggabungkan semua bagian memberikan Anda program mandiri yang dapat Anda salin, tempel, dan jalankan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output** – Setelah menjalankan program, konsol mencetak lokasi penyimpanan, dan membuka file yang dihasilkan di Word menampilkan tombol berlabel **Submit** yang ditempatkan di bagian atas halaman pertama.

## Handling common questions and edge cases

### Does the button work in all Word versions?

Kontrol ActiveX didukung di versi desktop Word pada Windows. Mereka tidak ditampilkan di Word Online, Word untuk macOS, atau klien seluler. Jika Anda memerlukan interaktivitas lintas‑platform, pertimbangkan menggunakan kontrol konten atau solusi berbasis HTML sebagai gantinya.

### What if I need a different size or position?

`InsertForms2OleControl` menempatkan kontrol pada posisi kursor builder saat ini. Untuk memindahkannya, sesuaikan kursor dengan `builder.MoveTo` sebelum penyisipan, atau ubah properti `Left` dan `Top` kontrol setelah dibuat:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Can I add other ActiveX types?

Ya. Enumerasi `Forms2OleControlType` mencakup `CheckBox`, `OptionButton`, `ListBox`, dan lainnya. Ganti `CommandButton` dengan nilai enum yang diinginkan dan sesuaikan properti sesuai kebutuhan.

### Is a macro required for the button to do something?

Tombol itu sendiri tidak melakukan apa‑apa sampai Anda melampirkan kode VBA. Di Word, tekan **Alt+F11** untuk membuka editor VBA, temukan `btnSubmit_Click`, dan tulis logika yang diinginkan. Dokumen yang dihasilkan akan mempertahankan proyek VBA jika Anda menyimpan dengan format **SaveFormat.Doc** (legacy `.doc`), tetapi file `.docx` tidak dapat menyimpan makro VBA. Gunakan format `.doc` jika Anda memerlukan VBA yang tersemat.

## Conclusion

Anda kini tahu **cara menambahkan ActiveX** ke file Word menggunakan Aspose.Words. Dengan mengikuti langkah‑langkah untuk **membuat dokumen Word kosong**, menginisialisasi `DocumentBuilder`, **menyisipkan tombol ActiveX**, mengonfigurasi propertinya, dan menyimpan file, Anda dapat menghasilkan templat Word interaktif langsung dari kode .NET Anda.

Selanjutnya, jelajahi topik terkait seperti penanganan acara **insert ActiveX button**, menambahkan **create word document aspose** untuk tabel atau gambar, serta mengamankan dokumen yang mendukung makro untuk penyebaran perusahaan. Bereksperimenlah dengan berbagai tipe kontrol dan opsi tata letak untuk menyesuaikan pengalaman pengguna dengan kebutuhan aplikasi Anda.

Happy coding!

## What Should You Learn Next?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}