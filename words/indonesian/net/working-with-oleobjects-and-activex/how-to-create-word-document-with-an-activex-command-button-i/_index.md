---
category: general
date: 2026-09-05
description: Buat dokumen Word menggunakan Aspose.Words C# dan pelajari cara menyisipkan
  tombol perintah ActiveX, mengatur ukuran tombol, serta menambahkan fungsionalitas
  tombol interaktif.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: id
lastmod: 2026-09-05
og_description: Buat dokumen Word dalam C# dan sisipkan tombol perintah ActiveX. Tutorial
  ini menunjukkan cara mengatur ukuran tombol dan menambahkan fitur tombol interaktif.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Membuat dokumen Word dengan tombol perintah ActiveX di C# – panduan langkah
  demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Cara membuat dokumen Word dengan tombol perintah ActiveX di C#
url: /id/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word dengan tombol perintah ActiveX di C#

Jika Anda perlu **membuat dokumen Word** secara programatis dan menyematkan elemen UI yang dapat diklik, panduan ini menunjukkan secara tepat caranya. Dengan menggunakan Aspose.Words untuk .NET Anda dapat **membuat dokumen Word**, **menambahkan tombol perintah**, dan mengontrol tampilannya—semua tanpa membuka Microsoft Word.

Anda akan belajar **cara menyisipkan kontrol ActiveX**, **mengatur ukuran tombol**, dan membuat tombol berperilaku seperti komponen UI interaktif. Tidak diperlukan pengalaman sebelumnya dengan COM atau VBA; cukup lingkungan pengembangan .NET dan pustaka Aspose.Words.

## Apa yang akan Anda capai

* **Membuat dokumen Word** dari awal dengan C#.
* **Menyisipkan tombol perintah ActiveX** (kontrol klasik “Click Me”).
* **Mengatur ukuran tombol** dan posisinya secara tepat.
* Secara opsional menambahkan logika **tombol interaktif** sederhana (mis., placeholder makro).
* Menyimpan file sebagai `.docx` yang dapat dibuka di Microsoft Word atau penampil kompatibel lainnya.

### Prasyarat

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 atau lebih baru | Menyediakan runtime untuk kode C#. |
| Aspose.Words for .NET (versi terbaru) | Menyediakan API `Document`, `DocumentBuilder`, dan `Forms2OleControl` yang digunakan dalam contoh. |
| Visual Studio 2022 (atau IDE C# apa pun) | Memudahkan kompilasi dan menjalankan contoh. |
| Pengetahuan dasar C# | Diperlukan untuk memahami alur kode. |

> **Pro tip:** Jika Anda menggunakan versi percobaan Aspose.Words, pastikan untuk mengatur lisensi sebelum menjalankan kode agar tidak muncul watermark evaluasi.

## Cara membuat dokumen Word – alur kerja keseluruhan

Proses ini terdiri dari empat langkah logis:

1. **Inisialisasi dokumen baru** dan `DocumentBuilder` untuk mengeditnya.  
2. **Sisipkan tombol perintah ActiveX** menggunakan `InsertForms2OleControl`.  
3. **Konfigurasikan tombol** – caption, ukuran, dan posisi.  
4. **Simpan** dokumen ke disk.

Setiap langkah dijelaskan di bagian masing‑masing di bawah ini.

![Dokumen Word dengan tombol ActiveX](/images/activex-button.png "Tangkapan layar dokumen Word yang berisi tombol perintah ActiveX yang dibuat dengan C#")

## Cara menyisipkan tombol perintah ActiveX

Bagian **cara menyisipkan activex** dimulai dengan metode `InsertForms2OleControl`. Metode ini membuat kontrol berbasis COM yang diperlakukan Word sebagai objek ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Mengapa ini berhasil:** `OleControlType.CommandButton` memberi tahu Aspose.Words untuk membuat tombol bergaya VB klasik. Ukuran dan lokasi dinyatakan dalam poin (1 poin = 1/72 inci), yang memberikan kontrol presisi atas tata letak.

## Cara menambahkan tombol perintah dan mengatur ukuran tombol

Setelah kontrol disisipkan Anda dapat menyesuaikan properti visualnya. Langkah **menambahkan tombol perintah** juga mencakup **mengatur ukuran tombol**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Penjelasan:**  

* `Caption` adalah label yang ditampilkan pada tombol.  
* `Width` dan `Height` memungkinkan Anda **mengatur ukuran tombol** setelah penyisipan awal—berguna ketika ukuran bergantung pada data runtime.  
* `Left` dan `Top` memindahkan posisi kontrol tanpa harus membuat ulang dokumen.

> **Common pitfall:** Lupa menggunakan poin alih‑alih piksel akan menyebabkan tombol muncul terlalu kecil atau terlalu besar. Selalu konversi nilai piksel (`px * 72 / DPI`) jika Anda memulai dari ukuran layar.

## Cara menambahkan tombol interaktif (opsional)

Tombol ActiveX dapat mengeksekusi makro saat diklik, tetapi menyematkan kode VBA dari C# berada di luar lingkup alur kerja Aspose.Words murni. Sebagai gantinya, Anda dapat menambahkan properti placeholder yang akan dikenali Word sebagai nama makro.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Ketika pengguna membuka `.docx` yang dihasilkan di Word, mengklik tombol akan mencoba menjalankan `MyMacroName`. Jika makro tidak ada, Word akan meminta pengguna untuk membuatnya.

**Mengapa Anda mungkin menggunakan ini:** Untuk formulir korporat di mana makro mengisi bidang, kode C# hanya perlu menempatkan tombol; logika makro berada di proyek VBA dokumen.

## Simpan dokumen dan verifikasi hasil

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Output yang diharapkan:** Membuka `CommandButton.docx` di Microsoft Word menampilkan tombol berlabel **Click Me** yang ditempatkan 100 pts dari margin kiri dan 120 pts dari atas. Dimensi tombol adalah **200 pts × 80 pts**. Mengklik tombol memicu placeholder makro (jika ada).

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat dijalankan yang menggabungkan semua langkah. Salin ke proyek Console App baru, tambahkan paket NuGet Aspose.Words, dan jalankan.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Jalankan program, lalu buka file yang dihasilkan. Anda akan melihat **tombol interaktif** siap untuk penyesuaian lebih lanjut.

## Pertanyaan yang sering diajukan

| Question | Answer |
|----------|--------|
| **Apakah ini bekerja dengan .NET Core?** | Ya. Aspose.Words mendukung .NET Standard, sehingga kode yang sama dapat dijalankan pada .NET 5/6/7. |
| **Bisakah saya menggunakan kontrol ActiveX lain (mis., CheckBox)?** | Tentu saja. Ganti `OleControlType.CommandButton` dengan `OleControlType.CheckBox`, `OleControlType.OptionButton`, dll. |
| **Bagaimana jika saya membutuhkan tombol yang lebih besar pada halaman lanskap?** | Sesuaikan properti `Width`, `Height`, `Left`, dan `Top` secara proporsional. Ingat bahwa poin tetap sama terlepas dari orientasi halaman. |
| **Apakah makro diperlukan agar tombol dapat diklik?** | Tidak. Tombol berfungsi penuh sebagai elemen UI; makro hanya menambahkan perilaku khusus saat diklik. |

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word** dengan Aspose.Words, **menambahkan tombol perintah**, **mengatur ukuran tombol**, dan secara opsional menautkan tombol ke makro untuk perilaku **menambahkan tombol interaktif**. Pendekatan ini memungkinkan Anda mengotomatisasi pembuatan formulir, menghasilkan laporan dinamis, atau membangun prototipe UI berbasis Word langsung dari C#.

Selanjutnya, Anda dapat menjelajahi:

* **Cara menyisipkan kotak centang ActiveX** untuk formulir survei.  
* **Cara menambahkan konten teks kaya** di sekitar tombol menggunakan `DocumentBuilder`.  
* **Cara melindungi dokumen** sambil menjaga tombol tetap berfungsi.  

Silakan bereksperimen dengan berbagai jenis kontrol, ukuran, dan nama makro untuk menyesuaikan dengan skenario spesifik Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Sisipkan Gambar Inline dalam Dokumen Word menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Buat Dokumen Word dengan Tabel Menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}