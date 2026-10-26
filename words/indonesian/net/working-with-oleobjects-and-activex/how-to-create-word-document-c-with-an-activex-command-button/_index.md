---
category: general
date: 2026-10-26
description: Pelajari cara membuat dokumen Word dengan C# dan menambahkan tombol ActiveX
  secara programatis. Panduan langkah demi langkah ini mencakup penyisipan tombol
  perintah, menyembunyikannya saat desain, dan menyimpan file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: id
lastmod: 2026-10-26
og_description: Buat dokumen Word dengan C# dan tambahkan tombol ActiveX secara programatis.
  Ikuti tutorial lengkap ini untuk menyematkan tombol perintah yang hanya muncul saat
  runtime.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Buat dokumen Word C# dengan tombol perintah ActiveX – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Cara membuat dokumen Word C# dengan tombol perintah ActiveX
url: /id/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word C# dengan tombol perintah ActiveX

Jika Anda perlu **create Word document C#** yang berisi tombol interaktif, panduan ini menunjukkan cara melakukannya secara tepat. Pada akhir dua kalimat pertama Anda akan mengetahui pendekatan keseluruhan, dan langkah‑langkah berikut akan memandu Anda melalui setiap baris kode yang harus ditulis.

Anda akan belajar cara menambahkan tombol ActiveX, menyembunyikannya selama desain, dan membuatnya terlihat hanya ketika pengguna membuka file. Tutorial ini juga mencakup jebakan umum seperti peringatan keamanan dan kompatibilitas versi, sehingga Anda dapat mengirim dokumen yang dapat diandalkan.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 atau yang lebih baru terinstal  
* Salinan berlisensi **Aspose.Words for .NET** (versi percobaan gratis dapat digunakan untuk percobaan)  
* Familiaritas dasar dengan C# dan Visual Studio (IDE apa pun yang mendukung .NET dapat digunakan)  

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Langkah 1: Buat dokumen Word C# dan inisialisasi DocumentBuilder

Langkah pertama adalah menginstansiasi objek `Document` dan `DocumentBuilder`. `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` menyediakan metode fluently untuk menambahkan konten.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Mengapa ini penting:** Tanpa `DocumentBuilder` Anda harus memanipulasi DOM OpenXML secara manual, yang rawan kesalahan dan lebih sulit dibaca. Builder mengabstraksi detail tersebut dan menjamin file Word yang terbentuk dengan baik.

## Langkah 2: Cara menambahkan tombol ActiveX – sisipkan kontrol CommandButton

Sekarang kita menyisipkan **CommandButton ActiveX control** pada lokasi tertentu. Persegi panjang menentukan posisi tombol (X, Y) dan ukuran (lebar, tinggi) dalam poin.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Mengapa ini penting:** `InsertForms2OleControl` adalah satu‑satunya metode Aspose.Words yang membuat objek OLE ActiveX yang sesungguhnya. Nilai enum `Forms2OleControlType.CommandButton` memberi tahu Word untuk menyematkan tombol yang dapat diklik, bukan kontainer OLE generik.

## Langkah 3: Tambahkan tombol perintah secara programatis – sembunyikan hingga runtime

Word memperlakukan setiap bentuk yang disisipkan sebagai terlihat secara default. Untuk menjaga tombol tetap tidak terlihat saat Anda mendesain templat, set properti `Hidden` pada shape yang baru saja dibuat builder.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Mengapa ini penting:** Menetapkan `Hidden = true` mencegah tombol mengacaukan tampilan desain. Ketika dokumen dibuka di Word, lingkungan runtime secara otomatis menampilkan kontrol tersebut, mempertahankan pengalaman pengguna yang dimaksudkan.

## Langkah 4: Simpan file – buat dokumen Word dengan tombol perintah

Akhirnya, tulis dokumen ke disk. Pilih jalur yang dapat ditulis oleh aplikasi Anda, dan gunakan ekstensi `.docx` untuk memastikan kompatibilitas modern.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Mengapa ini penting:** Menyimpan sebagai `.docx` menjamin bahwa kontrol ActiveX yang disematkan mematuhi standar Office Open XML, yang didukung oleh Word 2007 dan versi selanjutnya. Jika Anda memerlukan dukungan legacy `.doc`, ganti ekstensi dan gunakan `SaveFormat.Doc`.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semuanya, berikut program lengkap yang dapat Anda salin, tempel, dan jalankan:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Output yang diharapkan:** Setelah menjalankan program, buka `C:\Temp\ActiveX.docx` di Microsoft Word. Anda akan melihat dokumen kosong; tombol tidak terlihat dalam mode desain. Tekan **Alt + F9** untuk mengalihkan kode bidang, lalu klik area tombol—Word akan menampilkan kontrol ActiveX, dan Anda dapat berinteraksi dengannya (mis., klik ganda untuk melihat properti).

## Kasus tepi dan tips praktik terbaik

| Situasi | Hal yang perlu diwaspadai | Perbaikan yang disarankan |
|-----------|-------------------|-----------------|
| **Pengguna menonaktifkan ActiveX** | Word mungkin menampilkan peringatan keamanan atau memblokir kontrol. | Instruksikan pengguna akhir untuk mengaktifkan “ActiveX controls” di Trust Center, atau sediakan alternatif yang ditandatangani macro. |
| **Dokumen dibuka di Word Online** | Word Online tidak mendukung ActiveX; tombol akan dihilangkan. | Gunakan hyperlink cadangan atau content control jika Anda memerlukan kompatibilitas cloud. |
| **Pengaturan DPI yang berbeda** | Ukuran persegi panjang mungkin terlihat lebih besar atau lebih kecil pada tampilan DPI tinggi. | Gunakan `GraphicsUnit.Point` (default) dan uji pada pengaturan DPI umum (96 dpi, 120 dpi). |
| **Beberapa tombol** | Pemanggilan `GetChildNodes(NodeType.Shape, true)[0]` hanya mengambil shape pertama. | Lakukan loop melalui `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` dan set `Hidden` untuk setiap shape yang Anda tambahkan. |
| **Format .doc lama** | Beberapa properti ActiveX hilang saat menyimpan sebagai `.doc`. | Lebih baik gunakan `.docx` kecuali Anda memiliki kebutuhan legacy yang ketat. |

**Tip pro:** Setelah menyisipkan tombol, Anda dapat menetapkan macro ke properti `OnAction`‑nya melalui UI Word. Ini memungkinkan Anda mendefinisikan perilaku klik khusus tanpa menulis kode C# tambahan.

## Pertanyaan yang sering diajukan

* **Apakah ini bekerja dengan .NET Core?**  
  Ya. Aspose.Words for .NET sepenuhnya kompatibel dengan .NET 5, .NET 6, dan versi selanjutnya. Cukup referensikan paket NuGet yang sama.

* **Bisakah saya mengubah caption tombol setelah dokumen dihasilkan?**  
  Caption yang ditetapkan di `InsertForms2OleControl` menjadi teks desain‑time default. Pengguna dapat mengeditnya di Word, tetapi Anda juga dapat memperbarui caption secara programatis dengan mengakses properti objek OLE melalui API `Shape.OleFormat`.

* **Bagaimana jika saya membutuhkan ukuran tombol yang berbeda?**  
  Sesuaikan nilai `RectangleF`. Dua parameter pertama adalah koordinat X dan Y; dua parameter terakhir adalah lebar dan tinggi dalam poin (1 pt = 1/72 inci).

## Kesimpulan

Anda kini tahu cara **create Word document C#** dan **menambahkan tombol perintah secara programatis** menggunakan Aspose.Words. Tutorial ini mencakup inisialisasi dokumen, penyisipan tombol ActiveX, menyembunyikannya hingga runtime, dan menyimpan file akhir. Dengan blok‑blok bangunan ini Anda dapat menyematkan kontrol interaktif dalam templat Word apa pun yang Anda hasilkan.

Selanjutnya, jelajahi topik terkait seperti **cara menambahkan tombol ActiveX** penanganan acara, **buat tombol perintah Word** styling dengan VBA, dan **menambahkan tombol perintah secara programatis** ke dokumen yang sudah ada. Memperluas pola ini ke checkbox, combo box, atau objek OLE khusus mengikuti langkah yang sama—hanya ubah nilai enum `Forms2OleControlType`.

Mulailah bereksperimen: ganti caption, sesuaikan posisi, atau rangkaikan beberapa kontrol bersama. Semakin sering Anda berlatih, semakin lancar Anda akan menjadi dalam menyajikan dokumen Word yang kaya dan interaktif dari C#. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara menambahkan tombol perintah secara programatis dalam dokumen Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Cara menambahkan tombol ActiveX dalam dokumen Word dengan Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Buat Dokumen Word dengan Tombol ActiveX – Panduan C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}