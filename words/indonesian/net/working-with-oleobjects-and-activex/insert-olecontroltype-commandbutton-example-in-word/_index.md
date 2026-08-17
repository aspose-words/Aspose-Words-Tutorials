---
category: general
date: 2026-08-17
description: Masukkan contoh OleControlType.CommandButton di Word menggunakan Aspose.Words.
  Pelajari cara menambahkan kontrol formulir ke dokumen Word secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: id
lastmod: 2026-08-17
og_description: Masukkan contoh OleControlType.CommandButton di Word dengan Aspose.Words.
  Ikuti panduan ini untuk menambahkan kontrol formulir ke dokumen Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Sisipkan contoh OleControlType.CommandButton di Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Sisipkan contoh OleControlType.CommandButton di Word
url: /id/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan contoh OleControlType.CommandButton di Word

Jika Anda perlu **insert OleControlType.CommandButton example** ke dalam file Word, panduan ini menunjukkan cara melakukannya. Anda akan belajar **how to add form controls to a Word document** menggunakan Aspose.Words, dengan program C# lengkap yang dapat dijalankan.

Kontrol formulir seperti tombol ActiveX memungkinkan Anda membuat templat Word interaktif—berguna untuk kontrak, kuesioner, atau alat internal. Langkah-langkah di bawah ini mencakup semua hal mulai dari penyiapan proyek hingga memverifikasi tombol muncul dengan benar dalam file `.docx` yang disimpan.

## Prasyarat

- .NET 6.0 SDK atau yang lebih baru terpasang  
- Visual Studio 2022 (atau IDE C# apa pun)  
- Lisensi Aspose.Words untuk .NET atau lisensi sementara gratis  
- Pemahaman dasar tentang C# dan konsep file Word  

> **Pro tip:** Jika Anda menggunakan versi percobaan gratis, letakkan file lisensi di folder yang sama dengan executable dan muat di awal `Main`.

## Langkah 1: Buat proyek konsol baru dan tambahkan Aspose.Words

Buka terminal dan jalankan:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Ini membuat proyek bersih dan mengunduh paket Aspose.Words terbaru, yang menyediakan API `Document`, `DocumentBuilder`, dan `InsertForms2OleControl` yang diperlukan untuk **insert OleControlType.CommandButton example**.

## Langkah 2: Tulis program lengkap

Buat atau ganti `Program.cs` dengan kode berikut. Kode ini berisi semua direktif `using` yang diperlukan, pemuatan lisensi, dan alur kerja empat langkah yang ditunjukkan dalam cuplikan asli.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Mengapa setiap baris penting

* **License loading** – memastikan Anda tidak dibatasi oleh pembatasan evaluasi.  
* **`Document doc = new Document();`** – membuat wadah untuk semua konten Word; ini adalah dasar dari **insert OleControlType.CommandButton example**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – menyediakan API fluently untuk menambahkan teks, gambar, dan kontrol.  
* **`InsertForms2OleControl`** – metode inti yang mengimplementasikan **how to add form controls to a Word document**. Nilai enum `OleControlType.CommandButton` memberi tahu Aspose.Words untuk membuat tombol ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – menempatkan tombol 100 pt dari margin kiri dan atas, dengan lebar 80 pt dan tinggi 30 pt. Sesuaikan angka-angka ini agar cocok dengan tata letak Anda.  
* **`doc.Save`** – menulis file .docx ke disk; file kini berisi tombol yang disematkan.

## Langkah 3: Bangun dan jalankan program

Dari folder proyek, jalankan:

```bash
dotnet run
```

Anda akan melihat pesan konsol:

```
Document saved to ActiveXButton.docx
```

Buka `ActiveXButton.docx` di Microsoft Word. Anda akan melihat tombol berlabel **ClickMe** yang ditempatkan kira-kira di tengah halaman. Mengklik tombol akan memicu perilaku default ActiveX (yang biasanya tidak melakukan apa‑apa kecuali Anda melampirkan makro).

![contoh insert olecontroltype.commandbutton](/images/activex-button.png "ActiveX CommandButton disisipkan ke dalam dokumen Word")

*Teks alt gambar:* contoh insert olecontroltype.commandbutton – sebuah ActiveX CommandButton yang ditampilkan dalam dokumen Word.

## Langkah 4: Menyesuaikan tombol (opsional)

Contoh **insert OleControlType.CommandButton example** dasar membuat tombol default. Anda dapat mengubah caption, font, atau bahkan melampirkan makro dengan mengedit objek OLE yang mendasarinya. Berikut adalah cara singkat untuk mengubah caption tombol setelah penyisipan:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Catatan:** Manipulasi langsung properti OLE memerlukan pemahaman tentang antarmuka COM yang mendasarinya. Untuk kebanyakan skenario, caption default sudah cukup.

## Langkah 5: Kesalahan umum dan cara menghindarinya

| Masalah | Mengapa terjadi | Solusi |
|---------|----------------|--------|
| Tombol tidak muncul di Word | Dokumen disimpan sebagai `.docx` tetapi dibuka di penampil yang menghapus kontrol OLE (mis., Google Docs). | Buka file di Microsoft Word atau Word Online dengan hak edit. |
| Runtime error `ArgumentOutOfRangeException` | Koordinat `Rectangle` berada di luar margin halaman. | Gunakan nilai dalam ukuran halaman (mis., 0‑500 untuk A4). |
| Pengecualian lisensi | Lisensi percobaan kedaluwarsa setelah 30 hari. | Muat file lisensi yang valid atau minta percobaan diperpanjang dari Aspose. |

## Langkah 6: Bagaimana contoh ini cocok dalam proyek otomasi yang lebih besar

Ketika Anda perlu **how to add form controls to Word document** secara skala besar—seperti menghasilkan ratusan templat kontrak—bungkus logika penyisipan dalam metode yang dapat digunakan kembali:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Anda kemudian dapat memanggil `AddCommandButton` di dalam loop yang memproses baris data, memastikan setiap dokumen yang dihasilkan berisi tombol dengan nama unik (mis., `Approve_001`, `Approve_002`).

## Kesimpulan

Anda kini memiliki **insert OleControlType.CommandButton example** lengkap yang menunjukkan **how to add form controls to a Word document** menggunakan Aspose.Words untuk .NET. Tutorial ini mencakup penyiapan proyek, kode sumber lengkap, tips kustomisasi, dan langkah-langkah pemecahan masalah umum.

Dari sini Anda dapat menjelajahi:

- Menambahkan tipe kontrol lain seperti **CheckBox** atau **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Mengaitkan tombol ke makro VBA untuk interaktivitas yang lebih kaya.  
- Menghasilkan PDF dari dokumen yang sama sambil mempertahankan bidang formulir.

Bereksperimenlah dengan ukuran, posisi, dan nama kontrol yang berbeda untuk menyesuaikan kebutuhan spesifik Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Sisipkan Form Field Kotak Kombinasi di Dokumen Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Sisipkan Form Field Kotak Centang di Dokumen Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Sisipkan Form Field Input Teks di Dokumen Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}