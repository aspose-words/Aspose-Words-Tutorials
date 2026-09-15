---
category: general
date: 2026-09-14
description: Buat kontrol ActiveX dalam dokumen Word dengan C#. Pelajari cara menyisipkan
  ActiveX, menambahkan tombol interaktif, dan menghasilkan file .docx secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: id
lastmod: 2026-09-14
og_description: Buat kontrol ActiveX dalam dokumen Word dengan C#. Ikuti contoh lengkap
  ini untuk menyisipkan ActiveX, menambahkan tombol interaktif, dan menyimpan file.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Buat kontrol ActiveX di Word menggunakan C# – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Cara membuat kontrol ActiveX dalam dokumen Word dengan C#
url: /id/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat kontrol ActiveX dalam dokumen Word dengan C#

Jika Anda perlu **membuat kontrol ActiveX** di dalam file Microsoft Word, panduan ini menunjukkan solusi lengkap yang siap dijalankan. Anda akan melihat secara tepat cara menyisipkan ActiveX CommandButton, mengatur propertinya, dan menyimpan file `.docx` yang dihasilkan hanya dengan kode C#.

Menambahkan tombol interaktif ke dokumen Word adalah kebutuhan umum ketika Anda ingin pengguna akhir memicu makro atau logika khusus langsung dari UI dokumen. Contoh di bawah ini menunjukkan **cara menyisipkan ActiveX** tanpa bergantung pada alat pihak ketiga, dan juga mencakup **cara membuat dokumen Word** secara programatis.

Pada akhir tutorial ini Anda akan dapat **membuat tombol dengan kode**, menyesuaikan caption‑nya, dan menghasilkan file Word yang dapat dipindahkan yang mempertahankan kontrol ActiveX.

## Prerequisites

- .NET 6.0 atau lebih baru (perpustakaan Aspose.Words untuk .NET bekerja dengan .NET Core dan .NET Framework)
- Referensi ke paket NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Pengetahuan dasar tentang C# dan pemrograman berorientasi objek

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek konsol baru (atau integrasikan kode ke dalam aplikasi C# yang sudah ada). Impor namespace yang diperlukan agar kompilator dapat menemukan kelas pemrosesan Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Mengapa langkah ini penting** – API `Aspose.Words` menyediakan kelas `Document`, `DocumentBuilder`, dan `Forms2OleControl` yang memungkinkan Anda memanipulasi file Word pada tingkat objek. Tanpa referensi ini sisa kode tidak akan dapat dikompilasi.

## Langkah 2: Buat dokumen Word baru dan DocumentBuilder

Objek `Document` mewakili seluruh paket `.docx`, sementara `DocumentBuilder` menyediakan API yang fluently untuk menyisipkan konten.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Penjelasan** – Membuat instance `Document` baru memberi Anda kanvas bersih. Kursor builder dimulai di awal bagian pertama, siap untuk penyisipan berikutnya.

## Langkah 3: Sisipkan ActiveX CommandButton

Gunakan `InsertForms2OleControl` untuk menempatkan kontrol ActiveX pada lokasi tertentu. Metode ini memerlukan tipe kontrol, dan sebuah `RectangleF` yang mendefinisikan koordinat X/Y serta ukuran (dalam poin).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Mengapa ini berhasil** – `OleControlType.CommandButton` memberi tahu API untuk membuat CommandButton Windows standar. Rectangle menempatkan tombol relatif terhadap sudut kiri‑atas halaman, memungkinkan Anda **menambahkan tombol interaktif** tepat di tempat yang Anda butuhkan.

## Langkah 4: Konfigurasikan properti tombol

Sekarang atur teks yang terlihat pada tombol (`Caption`) dan nama internalnya (`Name`). Properti ini adalah apa yang dilihat pengguna dan apa yang dapat direferensikan kode VBA nanti.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Tip praktis** – `Name` harus unik dalam dokumen; jika tidak, makro VBA dapat merujuk ke kontrol yang salah.

## Langkah 5: Simpan dokumen

Terakhir, tulis file ke disk. Kontrol ActiveX disimpan di dalam paket Word, sehingga file yang disimpan akan mempertahankan fungsionalitas penuh saat dibuka di Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Hasil** – Membuka `CommandButton.docx` di Word menampilkan CommandButton yang dapat diklik dengan label “Click Me”. Kontrol dapat dihubungkan ke makro melalui UI Word (`Developer → Design Mode → Properties`).

## Daftar sumber lengkap

Menggabungkan semua langkah menghasilkan satu program mandiri yang dapat Anda salin, tempel, dan jalankan.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Output yang diharapkan

Menjalankan program mencetak baris konfirmasi:

```
Document saved to C:\Temp\CommandButton.docx
```

Ketika Anda membuka file yang dihasilkan di Microsoft Word, Anda akan melihat **CommandButton** yang ditempatkan pada koordinat yang ditentukan. Mengklik tombol dalam mode desain menyorotnya; dalam mode jalankan tombol berperilaku seperti tombol ActiveX standar mana pun.

## Variasi umum dan kasus tepi

| Skenario | Penyesuaian |
|----------|------------|
| **Jenis kontrol berbeda** | Ganti `OleControlType.CommandButton` dengan `OleControlType.CheckBox`, `OleControlType.OptionButton`, dll. |
| **Beberapa tombol** | Panggil `InsertForms2OleControl` berulang kali, memperbarui koordinat `RectangleF` untuk setiap tombol baru. |
| **Ukuran dinamis** | Hitung dimensi rectangle berdasarkan ukuran halaman (`builder.PageSetup.PageWidth`). |
| **Menyimpan ke stream** | Gunakan `document.Save(stream, SaveFormat.Docx)` ketika Anda perlu mengembalikan file dari API web. |
| **Format Word 97‑2003** | Ubah format penyimpanan menjadi `SaveFormat.Doc` untuk menghasilkan file `.doc` yang masih menyertakan kontrol ActiveX. |

> **Pro tip:** Selalu uji dokumen yang dihasilkan pada versi Word target, karena versi lama mungkin menerapkan pengaturan keamanan yang menonaktifkan kontrol ActiveX secara default.

## Pertanyaan yang sering diajukan

**Apakah ini bekerja dengan .NET Core?**  
Ya. Perpustakaan Aspose.Words bersifat lintas‑platform dan sepenuhnya kompatibel dengan .NET Core serta .NET 5/6+.

**Bisakah saya menetapkan makro ke tombol secara programatis?**  
API tidak menyematkan kode VBA secara langsung. Setelah dokumen dihasilkan, buka di Word, aktifkan tab Developer, dan rekam atau tulis makro yang merujuk ke `btnClick`.

**Bagaimana jika tombol tidak muncul?**  
Pastikan tab `Developer` diaktifkan di Word dan dokumen tidak dibuka dalam **Protected View**. Juga verifikasi bahwa koordinat rectangle berada dalam margin halaman.

## Kesimpulan

Anda kini tahu cara **membuat kontrol ActiveX** di dalam file Word menggunakan C#. Tutorial ini mencakup **cara menyisipkan ActiveX**, mendemonstrasikan **menambahkan tombol interaktif**, menunjukkan **cara membuat dokumen Word** dari awal, dan mengilustrasikan **membuat tombol dengan kode** yang tetap ada setelah disimpan.

Dari sini Anda dapat menjelajahi tipe ActiveX tambahan, menghubungkan tombol ke makro VBA, atau menyematkan logika dalam layanan pembuatan dokumen yang lebih besar. Bereksperimenlah dengan ukuran, posisi, dan properti kontrol yang berbeda untuk menyesuaikan pengalaman pengguna yang tepat.

---

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Baru](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Buat Proyek VBA di Dokumen Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Buat dan Gaya Dokumen Word di Aspose.Words untuk .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}