---
category: general
date: 2026-10-10
description: Atur teks tombol dan tambahkan tombol ActiveX di C# menggunakan Aspose.Words.
  Pelajari cara menyisipkan tombol, membuat kontrol tombol, dan menyesuaikan caption
  di dokumen Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: id
lastmod: 2026-10-10
og_description: Atur teks tombol dan tambahkan tombol ActiveX di C# dengan Aspose.Words.
  Ikuti panduan langkah demi langkah ini untuk menyisipkan tombol, membuat kontrol
  tombol, dan menyesuaikan keterangan tombol.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Atur teks tombol dan tambahkan tombol ActiveX di C# – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Atur teks tombol dan tambahkan tombol ActiveX di C#
url: /id/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengatur teks tombol dan menambahkan tombol ActiveX di C#

Jika Anda perlu **mengatur teks tombol** pada tombol ActiveX di dalam dokumen Word, panduan ini menunjukkan cara melakukannya secara tepat. Pada akhir tutorial Anda akan dapat **menyisipkan tombol**, membuat **kontrol tombol**, dan menyesuaikan caption‑nya dengan hanya beberapa baris kode C#.

Bekerja dengan kontrol ActiveX umum dilakukan ketika Anda menginginkan formulir interaktif di Word—baik Anda sedang membuat templat kontrak, survei, atau alat internal. Contoh ini menggunakan Aspose.Words untuk .NET, sebuah pustaka yang memungkinkan Anda memanipulasi file Word tanpa harus menginstal Microsoft Office.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Visual Studio 2022 (atau IDE apa pun yang mendukung C#)  
* Lisensi Aspose.Words untuk .NET (lisensi evaluasi gratis cukup untuk belajar)  

Anda juga memerlukan referensi ke paket NuGet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## Cara menyisipkan tombol ke dalam dokumen Word

Langkah pertama adalah membuat `Document` baru dan `DocumentBuilder`. Builder adalah titik masuk untuk menambahkan konten, termasuk kontrol ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:** `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` menyediakan metode tingkat tinggi seperti `InsertParagraph` dan `InsertFormField`. Memulai dengan dokumen bersih memastikan tombol muncul tepat di tempat yang Anda inginkan.

## Membuat kontrol tombol dengan Forms2OleControl

Sekarang kita membuat kontrol tombol yang sebenarnya. `Forms2OleControl` adalah kelas yang digunakan Aspose.Words untuk semua objek ActiveX, dan tipe `COMMANDBUTTON` ditampilkan sebagai tombol yang dapat diklik di Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Penjelasan:**  
* `InsertForms2OleControl` menempatkan kontrol pada koordinat tepat yang Anda berikan.  
* Ukuran didefinisikan dalam poin (1 poin = 1/72 inci). Sesuaikan angka‑angka ini agar cocok dengan tata letak Anda.

## Menambahkan kontrol ActiveX dan memberi nama unik

Setiap objek ActiveX harus memiliki nama yang berbeda agar dapat direferensikan nanti (misalnya, saat menangani peristiwa di VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tip:** Hindari spasi atau karakter khusus dalam nama; Word memperlakukan nama sebagai pengidentifikasi dalam model formulir internalnya.

## Mengatur teks tombol (caption) pada tombol ActiveX

Inilah saat kata kunci utama **set button text** berperan. Properti `Caption` menentukan label yang dilihat pengguna pada tombol.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Anda dapat mengubah caption kapan saja sebelum menyimpan dokumen. Jika kemudian Anda perlu melokalisasi UI, cukup panggil `SetCaption` lagi dengan string yang berbeda.

## Menyimpan dokumen dan memverifikasi hasilnya

Akhirnya, tulis dokumen ke disk. Membuka file di Microsoft Word akan menampilkan tombol dengan caption yang telah disesuaikan.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Output yang diharapkan:** Saat Anda membuka *ActiveXButton.docx* di Word, Anda akan melihat tombol yang diposisikan pada koordinat yang ditentukan, berlabel **Click Me**. Mengklik tombol akan memicu perilaku default tombol perintah Word (yang dapat Anda sesuaikan nanti dengan VBA).

![Contoh mengatur teks tombol](https://example.com/activex-button.png){alt="Contoh mengatur teks tombol"}

## Menambahkan tombol ActiveX dan menangani peristiwa (opsional)

Jika Anda menginginkan tombol melakukan aksi khusus, Anda dapat menambahkan makro VBA yang merespons peristiwa `Click`. Makro dapat disuntikkan secara programatis, tetapi itu berada di luar cakupan tutorial ini. Bagian pentingnya adalah tombol sudah ada dan caption‑nya sudah diatur—siap untuk penanganan peristiwa apa pun yang Anda pilih.

## Kesalahan umum dan cara menghindarinya

| Masalah | Mengapa terjadi | Solusi |
|---------|----------------|--------|
| Tombol muncul tidak rata | Koordinat dalam poin, bukan piksel | Konversi nilai piksel ke poin (`points = pixels * 72 / DPI`) |
| Caption tidak berubah setelah disimpan | `SetCaption` dipanggil setelah `Save` | Selalu atur caption **sebelum** memanggil `doc.Save` |
| Kontrol tidak terlihat di versi Word lama | Beberapa versi Word lama tidak mendukung ActiveX sepenuhnya | Uji pada versi Word target; pertimbangkan menggunakan `CheckBox` atau `DropDownList` sebagai alternatif |
| Peringatan lisensi pada output | Lisensi evaluasi kedaluwarsa | Terapkan lisensi Aspose.Words yang valid melalui `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Program ini mencakup semua direktif `using` yang diperlukan dan mendemonstrasikan alur kerja lengkap mulai dari pembuatan dokumen hingga penyimpanan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Jalankan program dengan `dotnet run`. Setelah eksekusi selesai, buka *ActiveXButton.docx* untuk memastikan caption tombol berbunyi **Click Me**.

## Ringkasan apa yang telah Anda pelajari

* Anda belajar cara **set button text** pada tombol ActiveX menggunakan Aspose.Words.  
* Anda melihat langkah‑langkah tepat untuk **how to insert button**, **create button control**, dan **add activex control** ke dokumen Word.  
* Anda kini memiliki potongan kode yang dapat digunakan kembali dan dapat disesuaikan untuk proyek otomasi Word berbasis formulir apa pun.

## Langkah selanjutnya

* Jelajahi nilai `Forms2OleControlType` lainnya seperti `CHECKBOX` atau `LISTBOX` untuk membuat formulir yang lebih kaya.  
* Gabungkan tombol dengan makro VBA untuk melakukan perhitungan atau validasi data.  
* Gunakan API `FormField` Aspose.Words untuk membaca input pengguna setelah dokumen diisi.

Silakan bereksperimen dengan ukuran, posisi, dan caption agar sesuai dengan kebutuhan desain Anda. Jika Anda menemui masalah, dokumentasi Aspose.Words menyediakan referensi detail untuk setiap kelas yang digunakan dalam tutorial ini.

Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}