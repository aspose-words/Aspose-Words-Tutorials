---
category: general
date: 2026-10-23
description: Buat dokumen Word kosong dengan C# dan pelajari cara menyisipkan kontrol
  ActiveX, termasuk tombol, menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: id
lastmod: 2026-10-23
og_description: Buat dokumen Word kosong dengan C# dan pelajari cara menyisipkan kontrol
  ActiveX, termasuk tombol, menggunakan Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Buat dokumen Word kosong dan tambahkan tombol ActiveX di C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Buat dokumen Word kosong dan tambahkan tombol ActiveX di C#
url: /id/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan tambahkan tombol ActiveX di C#

Jika Anda perlu **create blank Word document** secara programatis, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan melihat contoh lengkap yang dapat dijalankan yang membuat dokumen baru, menyisipkan ActiveX CommandButton, dan menyimpan file—semua dengan Aspose.Words untuk .NET.

Bekerja dengan file Word sering memerlukan lebih dari sekadar teks biasa. Menambahkan **ActiveX button** memungkinkan Anda menyematkan fungsionalitas interaktif yang dapat digunakan dalam templat yang mendukung makro atau solusi khusus Windows. Pada akhir tutorial ini Anda akan dapat menyisipkan kontrol ActiveX apa pun, tetapi kami fokus pada skenario paling umum: **word document activex button** yang mengirimkan formulir.

## Prasyarat

* .NET 6.0 atau lebih baru (kode juga bekerja dengan .NET Framework 4.7+)
* Visual Studio 2022 (atau IDE C# apa pun)
* **Aspose.Words for .NET** paket NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Familiaritas dasar dengan sintaks C#

> **Pro tip:** Aspose.Words adalah perpustakaan komersial, tetapi menyediakan lisensi sementara gratis untuk pengujian. Pasang lisensi lebih awal untuk menghindari watermark evaluasi.

## Langkah 1: Buat dokumen Word kosong dengan Aspose.Words

Langkah pertama adalah menginstansiasi objek `Document`. Ini mewakili file `.docx` kosong di memori.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` dimulai tanpa bagian, halaman, atau konten. Ini adalah kanvas bersih yang Anda butuhkan untuk skenario **create blank word document** seperti menghasilkan laporan dari awal.

## Langkah 2: Dapatkan DocumentBuilder untuk mengedit dokumen

`DocumentBuilder` menyediakan API yang nyaman untuk menambahkan teks, gambar, dan kontrol. Kami akan menggunakannya untuk menempatkan kontrol ActiveX.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder secara otomatis menambahkan bagian default dan halaman pertama, sehingga Anda dapat mulai menyisipkan objek langsung.

## Langkah 3: Cara menyisipkan kontrol ActiveX ke dalam dokumen

Aspose.Words menyediakan `InsertForms2OleControl` untuk menyematkan objek OLE/ActiveX. Metode ini memerlukan tipe kontrol, lebar, dan tinggi (dalam poin). Di bawah ini kami menyisipkan **CommandButton**—tombol formulir klasik yang Anda lihat di templat Word lama.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Mengapa ini berhasil:** `Forms2OleControlType.COMMANDBUTTON` memberi tahu Word untuk membuat tombol yang dapat merespons peristiwa klik ketika dokumen dibuka di lingkungan Windows yang mendukung ActiveX.

## Langkah 4: Buat kontrol ActiveX – atur propertinya

Sekarang kami memberi tombol nama programatik dan caption yang terlihat. Ini adalah bagian dari **create activex control** yang sering diabaikan oleh pengembang.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` adalah pengidentifikasi yang akan Anda referensikan dari makro VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` adalah label yang ditampilkan pada tombol itu sendiri.

## Langkah 5: Simpan dokumen Word dengan tombol ActiveX

Akhirnya, tulis dokumen ke disk. Ekstensi file harus `.docx` (atau `.docm` jika Anda berencana menambahkan makro nanti). Contoh menyimpan ke folder placeholder—ganti dengan jalur Anda sendiri.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Saat Anda membuka file hasil di Microsoft Word (hanya Windows), Anda akan melihat **word document activex button** yang berfungsi dan dapat dihubungkan ke kode VBA.

## Contoh lengkap yang berfungsi

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke proyek konsol baru.

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
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output yang diharapkan saat Anda menjalankan program**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Buka `ActiveXButton.docx` yang dihasilkan di Word, dan Anda akan melihat tombol berlabel **Submit** yang ditempatkan di bagian atas halaman pertama.

## Kasus tepi dan jebakan umum

| Situasi | Hal yang perlu diwaspadai | Rekomendasi |
|-----------|-------------------|----------------|
| Menjalankan di macOS atau Linux | ActiveX adalah teknologi khusus Windows, sehingga tombol akan muncul sebagai placeholder. | Gunakan tutorial ini hanya untuk templat yang ditargetkan Windows. |
| Dokumen dibuka di Word Online | Kontrol ActiveX tidak didukung dalam tampilan browser. | Sediakan UI cadangan atau beri instruksi kepada pengguna untuk membuka file di klien desktop. |
| Membutuhkan file yang mendukung makro | File `.docx` tidak dapat menyimpan kode VBA. | Simpan sebagai `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) dan tambahkan makro secara terpisah. |
| Ukuran kontrol tidak cocok | Nilai lebar/tinggi dalam poin (1 pt ≈ 1/72 in). | Sesuaikan nilai numerik untuk mencapai ukuran visual yang diinginkan. |

## Pertanyaan yang sering diajukan

**Bagaimana cara menyisipkan kontrol ActiveX selain tombol?**  
Gunakan metode `InsertForms2OleControl` yang sama tetapi berikan nilai enum `Forms2OleControlType` yang berbeda, seperti `COMBOBOX` atau `LISTBOX`.

**Apakah saya dapat mengubah font atau warna tombol?**  
Penampilan tombol ActiveX diatur oleh aplikasi host (Word) dan tema Windows yang mendasarinya. Anda dapat memodifikasi properti seperti `ForeColor` dan `BackColor` melalui VBA setelah dokumen dibuka.

**Apakah ada cara menambahkan penangan klik langsung dari C#?**  
Tidak. Peristiwa klik harus ditangani oleh VBA atau add‑in Word karena tombol berjalan di dalam proses Word, bukan aplikasi .NET Anda.

## Kesimpulan

Anda sekarang tahu cara **create blank Word document** secara programatis dan menyematkan **ActiveX button** menggunakan Aspose.Words untuk .NET. Langkah-langkah yang dibahas:

1. Instansiasi sebuah `Document`.
2. Gunakan `DocumentBuilder` untuk bekerja dengan file.
3. Panggil `InsertForms2OleControl` untuk **how to insert activex** kontrol.
4. Konfigurasikan properti kontrol (**create activex control**).
5. Simpan file, menghasilkan **word document activex button** yang siap untuk integrasi VBA.

Dari sini Anda dapat mengeksplorasi menambahkan tipe kontrol lain, menghubungkan makro VBA, atau mengonversi dokumen ke PDF sambil mempertahankan tombol (sebagai gambar statis). Bereksperimenlah dengan ukuran, caption, dan nama yang berbeda.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara menambahkan tombol ActiveX dalam dokumen Word dengan Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Buat Dokumen Word dengan Tombol ActiveX – Panduan C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}