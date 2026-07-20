---
category: general
date: 2026-07-19
description: Buat Dokumen Word menggunakan Aspose.Words C# dan pelajari cara menambahkan
  tombol perintah ActiveX, mengatur ukuran tombol, serta menyisipkan tombol secara
  programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: id
lastmod: 2026-07-19
og_description: Buat Dokumen Word dengan Aspose.Words C# dan sematkan tombol perintah
  ActiveX dalam hitungan detik. Ikuti panduan langkah demi langkah untuk mengatur
  ukuran tombol dan menyisipkan tombol dengan mudah.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Buat Dokumen Word dengan Tombol ActiveX – Tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Buat Dokumen Word dengan Tombol ActiveX – Panduan C#
url: /id/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Dokumen Word dengan Tombol ActiveX – Panduan Lengkap C#

Pernah bertanya-tanya bagaimana **membuat dokumen word** yang berisi tombol ActiveX yang berfungsi? Mungkin Anda sedang mengotomatiskan laporan dan membutuhkan kontrol “Setujui” yang dapat diklik langsung di dalam file. Dalam tutorial ini kita akan membahas langkah demi langkah—menggunakan Aspose.Words untuk .NET untuk menambahkan tombol perintah ActiveX, mengatur ukurannya, dan menyisipkannya di tempat yang Anda inginkan.  

Jika Anda pernah bertanya pada diri sendiri *bagaimana menambahkan activex* tanpa membuka Word secara manual, Anda berada di tempat yang tepat. Pada akhir tutorial Anda akan memiliki contoh yang dapat dijalankan, penjelasan jelas setiap langkah, dan tips untuk menangani jebakan umum.

## Apa yang Akan Anda Pelajari

- Cara menyiapkan Aspose.Words dalam proyek C#  
- Kode tepat untuk **membuat dokumen word** dan menyematkan tombol perintah ActiveX  
- Cara **mengatur ukuran tombol** serta menyesuaikan caption dan namanya  
- Metode yang tepat untuk **menyisipkan tombol perintah** dan **cara menyisipkan tombol** di lokasi manapun dalam dokumen  
- Pertimbangan kasus tepi (versi Word, batasan platform, peringatan keamanan)

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi pada .NET Framework 4.7+).  
- Lisensi Aspose.Words untuk .NET yang sah (atau kunci evaluasi gratis).  
- Visual Studio 2022 (atau IDE lain pilihan Anda).  
- Familiaritas dasar dengan C# dan pemrograman berorientasi objek.

Tidak ada pustaka pihak ketiga lain yang diperlukan.

---

## Langkah 1: Membuat Dokumen Word – Penyiapan Proyek

Sebelum kita dapat **menyisipkan tombol perintah**, kita memerlukan file Word kosong untuk dikerjakan. Langkah ini juga menunjukkan pola klasik “membuat dokumen word” menggunakan Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Mengapa ini penting:** `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` melacak posisi kursor saat ini. Semua penyisipan selanjutnya (termasuk kontrol ActiveX kita) terjadi relatif terhadap builder ini.

---

## Langkah 2: Cara Menambahkan ActiveX – Membuat Kontrol CommandButton

Sekarang dokumen sudah ada, mari kita selesaikan bagian **cara menambahkan activex**. Aspose.Words menyediakan kelas `Forms2OleControl` untuk objek ActiveX. Di sini kita akan membuat tombol perintah dan mengonfigurasi propertinya, termasuk kebutuhan **mengatur ukuran tombol**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Tip pro:** Ukuran diukur dalam poin (1 poin = 1/72 inci). Sesuaikan nilai agar cocok dengan tata letak Anda; untuk tombol toolbar tipikal, 120 × 30 bekerja dengan baik.

---

## Langkah 3: Menyisipkan Tombol Perintah – Inti dari **Menyisipkan Tombol Perintah**

Dengan kontrol yang siap, kini kita **menyisipkan tombol perintah** ke dalam dokumen pada lokasi builder saat ini. Anda dapat memindahkan builder ke mana saja (misalnya, setelah sebuah paragraf) sebelum memanggil metode ini.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Jika Anda perlu **cara menyisipkan tombol** pada bookmark tertentu, cukup pindahkan builder terlebih dahulu:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Apa yang terjadi di balik layar?** Aspose.Words menulis aliran objek OLE yang diperlukan ke dalam paket .docx, sehingga Word dapat menampilkan tombol tanpa makro tambahan.

---

## Langkah 4: Menyimpan Dokumen – Menyelesaikan Siklus **Membuat Dokumen Word**

Langkah terakhir sangat sederhana: menyimpan file ke disk. Ini menyelesaikan siklus **membuat dokumen word**, menyematkan ActiveX, dan menyimpannya.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Buka file yang dihasilkan di Microsoft Word (hanya Windows). Anda akan melihat tombol yang dapat diklik dengan label “Click Me”. Mengkliknya akan memicu Action default untuk CommandButton—tidak ada yang terjadi kecuali Anda menambahkan kode VBA, tetapi kontrol tersebut sepenuhnya berfungsi.

> **Output yang diharapkan:** File .docx dengan satu halaman, tombol terpusat pada titik penyisipan, berukuran 120 × 30 pt, bercaption “Click Me”.  
> ![Tombol ActiveX yang disisipkan ke dalam dokumen Word](placeholder-image.png)  
> *Teks alt gambar:* **Tombol ActiveX yang disisipkan ke dalam dokumen Word menggunakan C#** (matches `og_image_alt`).

---

## Langkah 5: Kasus Tepi, Keamanan, dan Praktik Terbaik

### Batasan Platform
- Kontrol ActiveX hanya berjalan pada versi Word untuk Windows. Jika audiens Anda termasuk pengguna macOS atau Word Online, tombol akan muncul sebagai gambar statis.
- Beberapa lingkungan korporat menonaktifkan ActiveX demi keamanan; Anda mungkin perlu menandatangani dokumen atau memberi tahu pengguna untuk mengaktifkan konten.

### Interaksi VBA (Opsional)
Jika Anda ingin tombol mengeksekusi makro, Anda harus menambahkan proyek VBA ke dokumen setelah disimpan. Aspose.Words tidak menghasilkan kode VBA secara otomatis, tetapi Anda dapat menggunakan API `Document.VbaProject` untuk menyuntikkannya.

### Benturan Nama
Selalu berikan setiap kontrol `Name` yang unik. Menggunakan nama yang sama dapat menyebabkan error runtime ketika Word mencoba menyelesaikan kontrol tersebut.

### Tip Kinerja
Saat menyisipkan banyak kontrol, gunakan kembali satu instance `DocumentBuilder` dan hindari memanggil `doc.Save` di dalam loop. Kumpulkan semua penyisipan dan simpan sekali di akhir.

---

## Contoh Lengkap yang Siap Pakai

Menggabungkan semuanya, berikut program lengkap yang siap disalin‑tempel:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Jalankan program, buka file yang disimpan, dan Anda akan melihat tombol tepat di posisi builder.

---

## Kesimpulan

Kita baru saja **membuat dokumen word** dari awal, mempelajari **cara menambahkan activex** dengan mengonfigurasi `Forms2OleControl`, menguasai properti **mengatur ukuran tombol**, dan mendemonstrasikan cara yang tepat untuk **menyisipkan tombol perintah** serta **cara menyisipkan tombol** di sembarang tempat dalam file.  

Dari satu contoh kode, Anda kini memiliki fondasi kuat untuk otomatisasi Word yang lebih kaya—baik Anda membangun templat dengan formulir interaktif, menghasilkan kontrak yang memerlukan pengakuan pengguna, atau sekadar menambahkan beberapa kontrol berguna di laporan.

### Apa Selanjutnya?

- **Gaya tombol** – ubah font, warna, atau tambahkan latar belakang gambar.  
- **Lampirkan makro VBA** – buat tombol melakukan perhitungan atau meluncurkan program eksternal.  
- **Kombinasikan dengan kontrol lain** – checkbox, list box, atau bahkan lembar Excel yang disematkan.  

Silakan bereksperimen, dan jika Anda menemui kendala, tinggalkan komentar di bawah. Selamat coding, dan nikmati otomatisasi Word dengan Aspose.Words!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}