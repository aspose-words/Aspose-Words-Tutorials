---
category: general
date: 2026-09-21
description: Buat dokumen Word secara programatis dan pelajari cara menyimpan tombol
  dokumen Word, menyisipkan tombol perintah Word, serta mengatur caption tombol perintah
  menggunakan DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: id
lastmod: 2026-09-21
og_description: Buat dokumen Word secara programatis dengan Aspose.Words. Pelajari
  cara menyimpan dokumen Word dengan tombol, menyisipkan tombol perintah Word, mengatur
  caption tombol perintah, dan menggunakan DocumentBuilder untuk formulir interaktif.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Buat dokumen Word secara programatis dan tambahkan tombol
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Buat dokumen Word secara programatis dan sisipkan tombol
url: /id/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat dokumen Word secara programatis dan menyisipkan tombol

Jika Anda perlu **membuat dokumen Word secara programatis**, Aspose.Words menyediakan API yang fluida yang memungkinkan Anda menambahkan kontrol interaktif seperti CommandButton. Tutorial ini juga menjelaskan **cara menggunakan DocumentBuilder**, cara **menyimpan tombol dokumen Word**, dan cara **mengatur caption tombol perintah** sehingga tombol muncul persis seperti yang Anda harapkan di dalam file .docx.

Anda akan belajar cara:

* Menginisialisasi dokumen kosong dengan `Document`.
* Bekerja dengan `DocumentBuilder` untuk mengedit dokumen.
* Menyisipkan **CommandButton** (`insert command button word`).
* Mengatur nama tombol dan caption yang terlihat (`set command button caption`).
* Menyimpan hasilnya ke disk (`save word document button`).

Langkah‑langkah ini ditulis untuk pengembang .NET menggunakan C# dan Aspose.Words for .NET terbaru (v24.10). Tidak ada paket NuGet tambahan yang diperlukan selain Aspose.Words.

---

## Apa yang Anda butuhkan sebelum memulai

| Prasyarat | Alasan |
|--------------|--------|
| Visual Studio 2022 (atau IDE C# apa saja) | Untuk mengompilasi dan menjalankan contoh kode. |
| .NET 6.0 SDK atau yang lebih baru | Menyediakan runtime untuk contoh. |
| Aspose.Words for .NET (v24.10 atau lebih baru) | Perpustakaan yang memungkinkan Anda **membuat dokumen Word secara programatis** dan memanipulasi kontrol formulir. |
| Familiaritas dasar dengan C# dan konsep OOP | Diperlukan untuk memahami alur kode. |

Anda dapat menginstal Aspose.Words melalui NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Membuat dokumen Word secara programatis

Langkah pertama adalah menginstansiasi `Document` kosong. Objek ini mewakili seluruh file Word di memori.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Membuat dokumen secara programatis memberi Anda kanvas bersih di mana Anda dapat menambahkan paragraf, tabel, atau kontrol interaktif.  

---

## Cara menggunakan DocumentBuilder

`DocumentBuilder` adalah kelas utama untuk mengedit sebuah `Document`. Ia menyediakan metode untuk menyisipkan teks, gambar, dan bidang formulir. Dalam tutorial ini kami menggunakannya untuk menempatkan CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder mempertahankan kursor internal yang menunjuk ke lokasi penyisipan saat ini. Secara default kursor dimulai di awal bagian pertama, yang ideal untuk contoh kami.

---

## Menyisipkan command button word

Aspose.Words memperlakukan CommandButton sebagai kontrol ActiveX. Metode `InsertForms2OleControl` membuat kontrol OLE generik yang kemudian kami konfigurasikan sebagai tombol.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Pada titik ini kontrol sudah ada di dokumen tetapi belum memiliki representasi visual sampai kami menentukan tipenya.

---

## Mengatur caption command button

Sekarang kami memberi tahu kontrol OLE bahwa ia harus berperilaku seperti CommandButton dan memberikan label yang ramah.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Mengatur **caption tombol perintah** sangat penting karena Word menampilkan teks ini pada permukaan tombol. Jika Anda melewatkan `SetCaption`, tombol akan muncul dengan label generik.

---

## Menyimpan tombol dokumen Word

Akhirnya, simpan dokumen ke disk. Metode `Save` menulis seluruh paket Word, termasuk tombol yang baru disisipkan, ke file .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

File `CommandButton.docx` kini berisi tombol yang berfungsi penuh dengan label **Submit**. Ketika pengguna membuka file di Microsoft Word dan mengklik tombol, aksi default (yang nanti dapat Anda hubungkan melalui VBA) akan dipicu.

---

## Contoh lengkap yang berfungsi

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Program ini mendemonstrasikan seluruh alur kerja mulai dari pembuatan dokumen hingga penyimpanan tombol.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Hasil yang diharapkan**

* Sebuah file bernama `CommandButton.docx` berada di jalur yang Anda tentukan.
* Membuka file di Microsoft Word menampilkan satu tombol **Submit** pada halaman pertama.
* Tombol dapat dipilih, diubah ukurannya, atau dihubungkan ke makro melalui tab **Developer** di Word.

---

## Pertanyaan umum dan penanganan kasus tepi

| Pertanyaan | Jawaban |
|----------|--------|
| *Bagaimana jika saya membutuhkan lebih dari satu tombol?* | Ulangi langkah 3–6 dengan nama dan caption yang berbeda. Setiap tombol harus memiliki nilai `SetName` yang unik. |
| *Apakah saya dapat mengatur ukuran tombol?* | Ya. Setelah menyisipkan kontrol, Anda dapat memodifikasi properti `Width` dan `Height` melalui objek `OleFormat`. |
| *Apakah tombol akan berfungsi di semua versi Word?* | Kontrol ActiveX didukung di versi desktop Word (Windows). Mereka tidak ditampilkan di Word Online atau di macOS. |
| *Bagaimana cara menambahkan handler klik?* | Anda perlu menulis kode VBA yang merujuk ke nama tombol (`btnSubmit`). Makro VBA dapat disematkan menggunakan `doc.VbaProject`. |
| *Bagaimana jika saya perlu menyisipkan tombol di dalam sel tabel?* | Pindahkan kursor builder ke sel yang diinginkan (`builder.MoveTo(cell.FirstParagraph)`) sebelum memanggil `InsertForms2OleControl`. |

---

## Tips profesional

* **Tips pro:** Selalu atur nama yang bermakna dengan `SetName`. Ini menyederhanakan otomasi VBA dan memudahkan debugging.
* **Waspadai:** Lupa memanggil `SetControlType`. Tanpa pemanggilan ini objek OLE muncul sebagai placeholder generik, bukan tombol yang dapat diklik.
* **Tips performa:** Jika Anda menghasilkan banyak dokumen dalam sebuah loop, gunakan kembali satu instance `DocumentBuilder` dan panggil `builder.MoveToDocumentEnd()` sebelum setiap penyisipan untuk menghindari reset kursor yang tidak perlu.

---

## Langkah selanjutnya

Sekarang Anda sudah tahu cara **membuat dokumen Word secara programatis**, **menyisipkan command button word**, **mengatur caption command button**, dan **menyimpan tombol dokumen Word**, Anda dapat menjelajahi skenario yang lebih maju:

* Tambahkan kontrol **TextFormField** untuk input pengguna.
* Gabungkan tombol dengan bidang **MacroButton** untuk mengeksekusi VBA secara langsung.
* Gunakan **DocumentBuilder.InsertImage** untuk menempatkan ikon pada tombol Anda.
* Integrasikan dengan ASP.NET untuk menghasilkan formulir Word pada

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}