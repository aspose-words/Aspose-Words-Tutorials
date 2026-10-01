---
category: general
date: 2026-09-30
description: Tambahkan kontrol ActiveX ke dokumen Word menggunakan C#. Pelajari cara
  menyisipkan tombol ActiveX, menambahkan tombol perintah, dan membuatnya dapat diklik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: id
lastmod: 2026-09-30
og_description: Tambahkan kontrol ActiveX ke dokumen Word dengan C#. Ikuti panduan
  lengkap ini untuk menyisipkan tombol ActiveX, menambahkan tombol perintah, dan membuatnya
  dapat diklik.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Menambahkan kata kontrol ActiveX ke dokumen Word – panduan C# langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Cara menambahkan kontrol ActiveX di Word dengan C#
url: /id/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan kata kontrol ActiveX di Word dengan C#

Jika Anda perlu menyematkan **kata kontrol ActiveX** di dalam file Microsoft Word, panduan ini menunjukkan langkah‑langkahnya secara tepat. Anda akan melihat contoh lengkap yang dapat dijalankan, yang menyisipkan tombol yang dapat diklik, menyimpan dokumen, dan bekerja dengan Aspose.Words for .NET versi terbaru.

Menambahkan kata kontrol ActiveX memungkinkan Anda membuat formulir interaktif, dialog khusus, atau elemen UI sederhana yang berperilaku seperti kontrol Word asli. Baik Anda sedang membangun templat kontrak yang memerlukan interaksi pengguna atau laporan yang membutuhkan tombol “Run”, langkah‑langkah di bawah ini mencakup semua yang Anda perlukan.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau lebih baru (kode juga berfungsi dengan .NET Framework 4.8)
* Visual Studio 2022 (atau IDE apa pun yang mendukung C#)
* Aspose.Words for .NET terpasang (`dotnet add package Aspose.Words`)
* Pemahaman dasar tentang C# dan struktur dokumen Word

> **Tips pro:** Metode `InsertForms2OleControl` hanya bekerja dengan kontrol “Forms 2.0” warisan, yaitu kontrol ActiveX yang Word gunakan untuk bidang formulir. Jika Anda menargetkan versi Office yang lebih baru, kontrol tetap ditampilkan dengan benar di klien desktop.

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek konsol baru dan tambahkan pernyataan `using` yang diperlukan. Ini memastikan kompiler dapat menemukan kelas `Document`, `DocumentBuilder`, dan `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Namespace `Aspose.Words` menyediakan API tingkat tinggi untuk pemrosesan Word, sementara `Aspose.Words.Drawing` berisi enumerasi `OleControlType` yang diperlukan untuk menentukan jenis kontrol ActiveX.

## Langkah 2: Muat dokumen Word sumber

Anda harus memulai dengan file Word yang ingin dimodifikasi. Kode berikut memuat `input.docx` dari folder yang Anda tentukan.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Jika file tidak ada, Aspose.Words akan melempar `FileNotFoundException`. Bungkus pemanggilan dalam blok `try/catch` jika Anda memerlukan penanganan error yang lebih halus.

## Langkah 3: Buat DocumentBuilder untuk mengedit dokumen

`DocumentBuilder` adalah mesin utama untuk menyisipkan teks, gambar, dan kontrol. Ia menjaga kursor yang menunjuk ke lokasi di mana elemen berikutnya akan ditempatkan.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Secara default, kursor builder berada di awal bagian pertama. Anda dapat memindahkannya dengan metode seperti `MoveToDocumentEnd()` atau `MoveToParagraph(index)` jika ingin menempatkan tombol di tempat lain.

## Langkah 4: Sisipkan kontrol ActiveX CommandButton

Sekarang masuk ke inti tutorial: menyisipkan **kata kontrol ActiveX** yang muncul sebagai tombol yang dapat diklik. Metode `InsertForms2OleControl` menerima dua argumen—jenis kontrol dan caption (atau nama) untuk kontrol tersebut.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Mengapa menggunakan `OleControlType.CommandButton`?**  
  Ini memberi tahu Word untuk membuat tombol command Forms 2.0 klasik, yang menampilkan caption dan dapat dihubungkan ke makro atau skrip VBA nanti.

* **Apa fungsi caption?**  
  String `"ClickMe"` menjadi teks yang terlihat pada tombol. Anda dapat mengubahnya menjadi apa saja yang sesuai dengan UI Anda.

### Menyisipkan tombol pada lokasi tertentu

Jika Anda memerlukan tombol setelah paragraf tertentu, pindahkan builder terlebih dahulu:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Langkah 5: Simpan dokumen yang telah dimodifikasi

Setelah menyisipkan kontrol, persistensikan perubahan ke file baru (atau timpa file asli).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Saat Anda membuka `output.docx` di versi desktop Word, Anda akan melihat tombol berlabel **ClickMe** (atau **Submit**, tergantung caption yang Anda gunakan). Mengklik tombol dalam mode desain tidak melakukan apa‑apa secara default; Anda dapat menugaskan makro nanti melalui tab “Developer” di Word.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program mandiri yang mendemonstrasikan seluruh alur kerja. Salin ke `Program.cs` pada aplikasi konsol baru dan jalankan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Output yang diharapkan

* Konsol mencetak pesan keberhasilan beserta jalur output.
* Membuka `output.docx` menampilkan tombol **ClickMe** di lokasi di mana builder menyisipkannya.
* Tombol dapat dipilih, diubah ukuran, atau diberikan makro melalui **Developer → Design Mode** di Word.

## Pertanyaan umum dan penanganan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana cara menyisipkan tombol ActiveX di header/footer?** | Pindahkan builder ke header/footer dengan `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` sebelum memanggil `InsertForms2OleControl`. |
| **Bagaimana jika saya membutuhkan kotak centang alih-alih tombol?** | Gunakan `OleControlType.CheckBox` dan berikan caption seperti `"Agree"`. |
| **Apakah tombol akan berfungsi di Word Online?** | Tidak. Word Online tidak mendukung kontrol Forms 2.0 ActiveX warisan. Tombol hanya ditampilkan di klien desktop. |
| **Bisakah saya mengatur ukuran tombol secara programatis?** | Setelah penyisipan, dapatkan objek `Shape` melalui `builder.CurrentParagraph.Runs[0].GetShape()` dan sesuaikan `Width`/`Height`. |
| **Apakah ada cara menugaskan makro dari kode?** | Aspose.Words tidak menyediakan akses pengeditan makro. Anda harus membuka dokumen di Word dan menempelkan makro secara manual atau menggunakan Office Interop API. |

## Tips untuk penggunaan produksi

* **Hindari jalur hard‑coded** – gunakan `Path.Combine` dan file konfigurasi.
* **Dispose `Document`** – bungkus dalam pernyataan `using` jika Anda bekerja dengan file besar untuk membebaskan memori dengan cepat.
* **Validasi output** – secara programatis periksa bahwa dokumen berisi shape bertipe `OleControl` dengan mengiterasi `doc.GetChildNodes(NodeType.Shape, true)`.
* **Catatan keamanan** – kontrol ActiveX dapat menjalankan kode di mesin klien. Distribusikan dokumen hanya kepada pengguna tepercaya dan pertimbangkan tanda tangan digital.

## Kesimpulan

Anda kini tahu cara menambahkan **kata kontrol ActiveX** ke dokumen Word menggunakan C#. Dengan memuat dokumen, membuat `DocumentBuilder`, menyisipkan tombol perintah menggunakan `InsertForms2OleControl`, dan menyimpan file, Anda dapat mengotomatisasi pembuatan formulir Word interaktif. Bereksperimenlah dengan nilai `OleControlType` lainnya, tempatkan kontrol di header atau tabel, dan gabungkan dengan makro untuk pengalaman pengguna yang lebih kaya.

---

*Langkah selanjutnya*: jelajahi **cara menyisipkan kontrol ActiveX** tipe lain, pelajari **cara menambahkan event handler tombol perintah** melalui VBA, dan baca tentang praktik terbaik **menyisipkan tombol ActiveX** untuk kompatibilitas lintas platform.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}