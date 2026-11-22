---
category: general
date: 2026-11-22
description: Pelajari cara menyisipkan kontrol Forms2Ole di Word dengan C#. Panduan
  langkah demi langkah ini mencakup DocumentBuilder, penempatan tombol perintah, dan
  penyimpanan file .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: id
lastmod: 2026-11-22
og_description: Masukkan kontrol Forms2Ole ke dalam Word dengan C#. Ikuti panduan
  ini untuk menambahkan tombol perintah menggunakan Aspose.Words dan DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Menyisipkan kontrol Forms2Ole di Word dengan C# – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cara menyisipkan kontrol Forms2Ole di Word menggunakan C# dan Aspose.Words
url: /id/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan kontrol Forms2Ole di Word menggunakan C# dan Aspose.Words

Jika Anda perlu **menyisipkan kontrol Forms2Ole di Word**, tutorial ini menunjukkan secara tepat cara melakukannya dengan C#. Baik Anda sedang membuat templat yang dapat diisi atau mengotomatisasi pembuatan formulir, solusi di bawah ini memungkinkan Anda menambahkan tombol perintah secara programatis.

Anda akan belajar cara membuat dokumen kosong, menggunakan `DocumentBuilder` untuk menempatkan kontrol, dan menyimpan hasilnya sebagai `.docx`. Panduan ini juga mencakup jebakan umum, seperti sistem koordinat dan kompatibilitas dengan versi Word yang lebih lama.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 atau lebih baru (kode juga bekerja dengan .NET Framework 4.6+)
* Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)
* Pemahaman dasar tentang C# dan model objek Word
* IDE seperti Visual Studio atau VS Code

## Langkah 1: Siapkan proyek dan impor namespace

Buat aplikasi konsol baru dan tambahkan paket Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

Di `Program.cs` impor namespace yang diperlukan:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Tips profesional:** Gunakan versi Aspose.Words terbaru untuk mendapatkan dukungan penuh untuk API `Forms2OleControl`.

## Langkah 2: Buat dokumen kosong dan inisialisasi DocumentBuilder

`Kelas `Document` mewakili file Word, sementara `DocumentBuilder` menyediakan metode untuk menyisipkan konten.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` berfungsi seperti kursor; setelah baris ini Anda dapat mulai menempatkan elemen di mana saja dalam dokumen.

## Langkah 3: Tentukan posisi dan ukuran tombol

Word mengukur koordinat dalam poin (1 pt ≈ 1/72 in). Struct `Rectangle` dari `System.Drawing` menggambarkan batas kontrol.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` menempatkan kontrol di sudut kiri‑atas halaman saat ini.
* Sesuaikan `x` dan `y` untuk memindahkan tombol ke tempat lain (misalnya, `new Rectangle(150, 200, 100, 30)`).

## Langkah 4: Sisipkan tombol perintah Forms2Ole

Sekarang gunakan `InsertForms2OleControl` untuk menambahkan kontrol. Metode ini memerlukan tipe kontrol, sebuah nama, dan batas yang didefinisikan di atas.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Objek `Forms2OleControl` yang dikembalikan memungkinkan Anda mengubah properti seperti `Enabled`, `Visible`, atau bahkan menempelkan nama macro kemudian.

### Mengapa menggunakan Forms2Ole?

* **Kompatibilitas warisan** – Kontrol Forms2Ole bekerja di Word 97‑2003 (`.doc`) dan file `.docx` yang lebih baru.
* **Dukungan macro** – Mereka dapat memicu macro VBA, menjadikannya ideal untuk templat interaktif.
* **Penempatan presisi** – Tidak seperti kontrol konten, Anda mengontrol koordinat yang tepat.

## Langkah 5: Simpan dokumen

Akhirnya, tulis file ke disk. Pilih folder yang Anda miliki akses menulis.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Buka `output.docx` di Microsoft Word. Anda akan melihat tombol berlabel **ClickMe** di sudut kiri‑atas halaman pertama. Mengkliknya di Word tidak akan melakukan apa‑apa sampai Anda menetapkan macro, tetapi kontrol tersebut berfungsi penuh.

## Menangani kasus tepi umum

| Situasi | Cara mengatasinya |
|-----------|-------------------|
| **Tombol muncul di luar halaman** | Verifikasi koordinat `Rectangle` berada dalam margin halaman. Gunakan `builder.PageSetup.PageWidth` dan `PageHeight` untuk menghitung batas aman. |
| **Kontrol tidak terlihat di versi Word yang lebih lama** | Simpan dokumen sebagai `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) untuk menjamin kompatibilitas Forms2Ole dengan Word 97‑2003. |
| **Perlu mengubah caption** | Setelah penyisipan, atur `commandButton.Caption = "Submit";`. |
| **Tetapkan macro** | Atur `commandButton.MacroName = "MyMacro"`; macro harus ada dalam proyek VBA dokumen. |
| **Beberapa tombol** | Ulangi Langkah 4 dengan nilai `Rectangle` yang berbeda dan nama unik. |

## Contoh lengkap yang dapat dijalankan

Menggabungkan semuanya, berikut adalah program mandiri yang dapat Anda salin, tempel, dan jalankan:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output yang diharapkan:** Setelah menjalankan program, `output.docx` terbuka di Word dengan tombol yang dapat diklik berlabel *Click Me!* yang ditempatkan di sudut kiri‑atas halaman pertama.

## Kesimpulan

Anda sekarang tahu cara **menyisipkan kontrol Forms2Ole di Word** menggunakan C# dan Aspose.Words. Prosesnya melibatkan pembuatan `Document`, penempatan `Rectangle`, dan pemanggilan `InsertForms2OleControl` melalui `DocumentBuilder`. Dengan contoh kode lengkap dan panduan kasus tepi, Anda dapat mengintegrasikan tombol perintah ke dalam alur kerja Word otomatis apa pun.

### Langkah selanjutnya

* Jelajahi nilai `ControlType` lain seperti `CheckBox` atau `OptionButton`.
* Gabungkan kontrol Forms2Ole dengan macro VBA untuk formulir interaktif.
* Gunakan `DocumentBuilder.MoveTo` untuk menempatkan tombol pada paragraf atau tabel tertentu.
* Tinjau dokumentasi **Forms2Ole** Aspose.Words untuk pengaturan properti lanjutan.

Selamat coding, dan nikmati membangun dokumen Word yang lebih kaya dengan C# dan Aspose.Words!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara menyisipkan tombol perintah OLE dalam dokumen Word menggunakan C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [cara menambahkan kontrol activex di Word dengan Aspose.Words – panduan langkah demi langkah](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Tambahkan Tombol Perintah ke Dokumen Word dengan Aspose.Words – Panduan Lengkap](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}