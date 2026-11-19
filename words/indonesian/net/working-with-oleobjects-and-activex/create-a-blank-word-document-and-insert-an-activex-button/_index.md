---
category: general
date: 2026-11-18
description: Buat dokumen Word kosong dan sisipkan tombol ActiveX dengan C#. Pelajari
  cara menambahkan kontrol, mengatur caption tombol, dan menyimpan file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: id
lastmod: 2026-11-18
og_description: Buat dokumen Word kosong dan sisipkan tombol ActiveX menggunakan C#.
  Ikuti tutorial lengkap ini untuk menambahkan kontrol, mengatur caption tombol, dan
  menyimpan hasilnya.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Buat dokumen Word kosong dan sisipkan tombol ActiveX – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Buat dokumen Word kosong dan sisipkan tombol ActiveX
url: /id/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan sisipkan tombol ActiveX

Jika Anda perlu **membuat dokumen Word kosong** dan menempatkan tombol ActiveX interaktif di dalamnya, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Anda akan melihat kode lengkap, memahami mengapa setiap baris penting, dan belajar cara **mengatur caption tombol** sehingga kontrol terlihat siap untuk interaksi pengguna.

Selain tujuan utama, kami akan membahas **cara menyisipkan ActiveX**, langkah‑langkah **cara menambahkan kontrol** ke file Word, dan nuansa **menyisipkan tombol ActiveX** dengan caption khusus. Pada akhir tutorial Anda akan memiliki pola yang dapat digunakan kembali untuk skenario otomatisasi dokumen apa pun yang memerlukan elemen UI tersemat.

## Apa yang akan Anda pelajari

* Cara **membuat dokumen Word kosong** secara programatis.  
* Panggilan API yang tepat diperlukan untuk **menyisipkan tombol ActiveX** dan mengonfigurasi propertinya.  
* Cara **mengatur caption tombol** sehingga kontrol menampilkan teks yang diinginkan.  
* Tips untuk menyimpan file di lokasi pilihan Anda dan menangani jebakan umum.

### Prasyarat

* .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.6+).  
* Aspose.Words untuk .NET terpasang (`Install-Package Aspose.Words`).  
* Familiaritas dasar dengan C# dan Visual Studio atau IDE kompatibel .NET apa pun.

---

## Buat dokumen Word kosong dengan Aspose.Words

Langkah pertama adalah membuat instance objek `Document` yang kosong. Objek ini mewakili file Word yang tidak berisi konten apa pun hingga kita menambahkan sesuatu.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Mengapa ini penting*: `Document` yang kosong memberi Anda kanvas bersih. Anda dapat menambahkan paragraf, tabel, atau kontrol nanti tanpa khawatir tentang format yang sudah ada.

---

## Inisialisasi DocumentBuilder untuk bekerja dengan dokumen

`DocumentBuilder` adalah kelas pembantu yang memungkinkan Anda menyisipkan konten pada posisi kursor saat ini. Ia secara otomatis melacak posisi Anda dalam dokumen.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting*: Tanpa `DocumentBuilder` Anda harus memanipulasi pohon node tingkat rendah secara manual. Builder mempermudah penyisipan teks, gambar, dan kontrol ActiveX.

---

## Cara menyisipkan tombol ActiveX (insert activex button)

Sekarang kita menggunakan `InsertForms2OleControl` untuk menyematkan kontrol ActiveX. Metode ini memerlukan tiga argumen:

1. Jenis kontrol (`OleControlType.CommandButton`).  
2. Nama internal untuk kontrol (digunakan oleh VBA atau kode makro).  
3. `RectangleF` yang menentukan posisi dan ukuran pada halaman.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Mengapa ini penting*: Ini adalah inti dari **cara menyisipkan activex** ke dalam dokumen Word. Koordinat persegi panjang diungkapkan dalam poin (1 poin = 1/72 inci). Sesuaikan untuk menempatkan tombol di tempat yang Anda inginkan.

### Tips

Jika Anda membutuhkan tombol muncul pada halaman tertentu, pindahkan kursor builder terlebih dahulu:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Cara mengatur caption tombol (set button caption)

Setelah kontrol ditempatkan, Anda dapat memodifikasi propertinya. Properti yang paling terlihat adalah `Caption`, yang menentukan teks yang ditampilkan pada tombol.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Mengapa ini penting*: Pengguna melihat caption, bukan nama internal. Mengubahnya membuat tombol menjadi bermakna dalam dokumen akhir.

---

## Simpan dokumen yang berisi tombol

Akhirnya, tulis dokumen ke disk. Anda dapat memilih format yang didukung (`.docx`, `.pdf`, dll.). Di sini kami menyimpan sebagai dokumen Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Mengapa ini penting*: Menyimpan file memungkinkan Anda membukanya di Microsoft Word dan menguji tombol. Saat dokumen dibuka, tombol akan muncul dengan caption “Press”.

### Hasil yang diharapkan

Membuka `with_button.docx` di Word menampilkan halaman kosong dengan tombol berbentuk persegi panjang berlabel **Press**. Mengklik tombol tidak melakukan apa‑apa secara default karena tidak ada makro VBA yang terlampir, tetapi kontrol berfungsi penuh dan dapat dihubungkan ke kode nanti.

---

## Cara menambahkan kontrol ke paragraf tertentu (how to add control)

Terkadang Anda ingin tombol berada di dalam paragraf tertentu, misalnya setelah beberapa teks instruksional. Gunakan `MoveTo` untuk memposisikan builder sebelum menyisipkan kontrol.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Mengapa ini penting*: Pola ini menunjukkan **cara menambahkan kontrol** dalam konteks, memastikan tata letak dokumen tetap logis.

---

## Kesulitan umum dan cara menghindarinya

| Masalah | Mengapa terjadi | Solusi |
|-------|----------------|-----|
| Tombol muncul di luar halaman | Koordinat persegi panjang berada di luar margin halaman | Gunakan `builder.PageSetup` untuk mendapatkan dimensi halaman dan menghitung `RectangleF` yang aman. |
| Caption tidak muncul | `Caption` diatur sebelum kontrol sepenuhnya diinisialisasi | Atur `Caption` **setelah** pemanggilan `InsertForms2OleControl`, seperti yang ditunjukkan pada Langkah 4. |
| Dokumen disimpan tanpa tombol | Kursor builder dipindahkan setelah penyisipan tanpa mengkomit perubahan | Pertahankan builder pada halaman yang sama atau panggil `builder.Document.UpdatePageLayout()` sebelum menyimpan. |

---

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Program ini membuat file Word kosong, menyisipkan tombol ActiveX, mengatur caption-nya, dan menyimpan hasilnya.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output**: Setelah menjalankan program, buka `C:\Temp\with_button.docx` di Microsoft Word. Anda akan melihat satu halaman dengan teks “Below is an ActiveX button created programmatically:” diikuti oleh tombol berlabel **Press**.

---

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong**, **menyisipkan tombol ActiveX**, **mengatur caption tombol**, dan **menyimpan** hasilnya menggunakan Aspose.Words untuk .NET. Pola yang sama dapat diperluas ke kontrol ActiveX lainnya (checkbox, list box, dll.) dengan mengubah `OleControlType`.  

Selanjutnya, Anda dapat menjelajahi **cara menyisipkan tombol ActiveX** dengan event VBA, atau **cara menambahkan kontrol** ke dokumen yang sudah ada dan sudah berisi konten. Kedua topik tersebut dibangun langsung dari konsep yang dibahas di sini.

Selamat coding, dan silakan bereksperimen dengan ukuran, posisi, dan caption yang berbeda untuk memenuhi kebutuhan UI aplikasi Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat dokumen Word C# dengan tombol perintah ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Cara menambahkan tombol ActiveX dalam dokumen Word dengan Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}