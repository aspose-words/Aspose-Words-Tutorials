---
category: general
date: 2026-10-07
description: Pelajari cara menyisipkan tombol perintah OLE dalam dokumen Word dengan
  Aspose.Words C#. Panduan langkah demi langkah yang mencakup DocumentBuilder, properti,
  dan penyimpanan file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: id
lastmod: 2026-10-07
og_description: Masukkan tombol perintah OLE dalam dokumen Word menggunakan C#. Ikuti
  tutorial singkat ini untuk menambahkan, mengkonfigurasi, dan menyimpan CommandButton
  yang berfungsi dengan Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Menyisipkan tombol perintah OLE di Word dengan C# – panduan lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Cara memasukkan tombol perintah OLE ke dalam dokumen Word menggunakan C#
url: /id/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan tombol perintah OLE dalam dokumen Word menggunakan C#

Jika Anda perlu **menyisipkan tombol perintah OLE** ke dalam file Word secara programatis, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Baik Anda membuat laporan berisi formulir maupun mengotomatiskan templat yang memerlukan interaksi pengguna, langkah‑langkah di bawah ini memberikan solusi lengkap yang dapat dijalankan.

Anda akan belajar cara membuat dokumen kosong, menggunakan `DocumentBuilder` untuk menempatkan `Forms2OleControl`, mengatur caption dan nama tombol, serta akhirnya menyimpan file `.docx`. Tidak ada alat eksternal yang diperlukan selain pustaka Aspose.Words.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
* Lisensi Aspose.Words untuk .NET yang valid atau kunci evaluasi gratis
* Visual Studio 2022 (atau IDE C# lain yang Anda sukai)
* Familiaritas dasar dengan sintaks C# dan konsep OLE di Word

> **Pro tip:** Jika Anda menggunakan versi evaluasi gratis, dokumen yang dihasilkan akan berisi watermark kecil. Versi berlisensi akan menghapusnya secara otomatis.

## Langkah 1: Instal Aspose.Words

Tambahkan paket Aspose.Words ke proyek Anda melalui NuGet:

```bash
dotnet add package Aspose.Words
```

Paket ini mencakup namespace `Aspose.Words.Drawing` dan `Aspose.Words.Drawing.Ole` yang diperlukan untuk kontrol OLE.

## Langkah 2: Sisipkan tombol perintah OLE dengan DocumentBuilder

Inti tutorial adalah metode `InsertForms2OleControl`. Metode ini membuat **Forms2 OLE CommandButton** pada lokasi dan ukuran tertentu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Mengapa ini berhasil

* `DocumentBuilder` adalah API utama untuk membangun dokumen Word secara programatis.  
* `InsertForms2OleControl` memberi tahu Aspose.Words untuk menyematkan **kontrol Forms2 OLE**, yaitu teknologi formulir Word lama yang mendukung tombol perintah, kotak centang, dll.  
* Nilai enum `OleControlType.CommandButton` menentukan bahwa kontrol yang disisipkan adalah **tombol perintah**—tipe tepat yang Anda minta ketika ingin **menyisipkan tombol perintah OLE**.  
* `Rectangle` menentukan penempatan visual. Sesuaikan koordinat X/Y atau lebar/tinggi agar cocok dengan tata letak Anda.

## Langkah 3: Simpan dokumen

Setelah mengonfigurasi tombol, tulis dokumen ke disk. Anda dapat memilih format apa pun yang didukung oleh Aspose.Words (`.docx`, `.pdf`, `.odt`, …). Untuk tutorial ini kita akan menyimpan sebagai dokumen Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Saat Anda membuka `CommandButton.docx` di Microsoft Word, Anda akan melihat tombol yang dapat diklik dengan label **Click Me**. Menekannya di Word memicu dialog “Run Macro” default karena tombol tersebut adalah kontrol formulir OLE; Anda dapat menambahkan makro atau kode VBA nanti jika diperlukan.

## Langkah 4: Verifikasi hasil (output yang diharapkan)

Buka file yang dihasilkan:

1. Tombol muncul pada koordinat yang Anda tentukan (sekitar 1,4 in dari kiri dan atas halaman).  
2. Caption menampilkan **Click Me**.  
3. Properti nama (`cmdSubmit`) terlihat di panel **Developer → Properties** Word, yang berguna ketika Anda perlu merujuk kontrol tersebut dari VBA.

![Insert OLE command button example in Word document](insert-ole-button.png)

*Teks alt gambar*: **Contoh menyisipkan tombol perintah OLE dalam dokumen Word** (menyertakan kata kunci utama untuk aksesibilitas dan SEO).

## Kasus Khusus & Pertanyaan Umum

### 1. Bagaimana jika tombol tidak muncul di lokasi yang saya harapkan?

* Word menggunakan poin, bukan piksel. Konversi piksel layar ke poin (`points = pixels * 72 / DPI`).  
* Pastikan rectangle tidak bersinggungan dengan margin halaman; jika tidak, Word dapat memindahkan kontrol.

### 2. Bisakah saya menyisipkan tombol ke dalam dokumen yang sudah ada?

Ya. Muat dokumen dengan `new Document("Existing.docx")` dan gunakan alur kerja `DocumentBuilder` yang sama. Ingat untuk memindahkan kursor builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, dll.) sebelum memanggil `InsertForms2OleControl`.

### 3. Bagaimana cara menambahkan makro ke tombol?

Aspose.Words tidak membuat kode VBA, tetapi Anda dapat menyematkan makro setelah dokumen dihasilkan:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Apakah ini bekerja dengan .NET Core di Linux?

Kontrol OLE adalah fitur khusus Windows karena bergantung pada COM. Di Linux tombol akan disisipkan, tetapi akan muncul sebagai gambar statis tanpa perilaku interaktif. Untuk formulir interaktif lintas‑platform, pertimbangkan menggunakan kontrol konten (`StructuredDocumentTag`) sebagai gantinya.

### 5. Bagaimana jika saya membutuhkan ukuran berbeda atau beberapa tombol?

Buat objek `Rectangle` tambahan dengan koordinat unik dan ulangi pemanggilan `InsertForms2OleControl`. Setiap tombol dapat memiliki `Caption` dan `Name` masing‑masing.

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup semua direktif `using` yang diperlukan, penanganan error, dan komentar.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Jalankan program, buka `CommandButton.docx` yang dihasilkan, dan Anda akan melihat tombol **Click Me** siap untuk kustomisasi lebih lanjut.

## Kesimpulan

Sekarang Anda tahu cara **menyisipkan tombol perintah OLE** ke dalam dokumen Word menggunakan C# dan Aspose.Words. Tutorial ini mencakup:

* Instalasi paket Aspose.Words  
* Penggunaan `DocumentBuilder.InsertForms2OleControl` dengan `OleControlType.CommandButton`  
* Pengaturan properti tombol (`Caption`, `Name`)  
* Menyimpan dan memverifikasi output  

Selanjutnya Anda dapat menjelajahi topik terkait seperti **Aspose.Words OLE control** untuk kotak centang, kotak kombo, atau menyematkan lembar kerja Excel secara keseluruhan. Anda juga dapat bereksperimen dengan otomatisasi **Word OLE command button** dalam templat yang lebih besar, atau mengganti kontrol OLE dengan **content controls** modern untuk dukungan lintas‑platform yang lebih baik.

Silakan sesuaikan nilai rectangle, tambahkan beberapa tombol, atau lampirkan makro VBA untuk memenuhi kebutuhan aplikasi Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menyisipkan Objek Ole dalam Dokumen Word](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Menyisipkan Objek Ole dalam Dokumen Word sebagai Ikon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Menyisipkan Objek Ole dalam Word dengan Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}