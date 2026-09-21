---
category: general
date: 2026-09-21
description: Pelajari cara membuat tombol perintah ActiveX dalam dokumen Word dengan
  Aspose.Words dan C#. Panduan langkah demi langkah mencakup penyisipan, penempatan,
  dan penyimpanan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: id
lastmod: 2026-09-21
og_description: Buat tombol perintah ActiveX dalam dokumen Word menggunakan C# dan
  Aspose.Words. Ikuti tutorial lengkap ini untuk menyisipkan, memposisikan, dan menyimpan
  tombol secara programatis.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Buat tombol perintah ActiveX di Word dengan C# – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Cara membuat tombol perintah ActiveX di Word menggunakan C#
url: /id/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat tombol perintah ActiveX di Word menggunakan C#

Jika Anda perlu **membuat tombol perintah ActiveX** di dalam file Word, panduan ini menunjukkan langkah‑langkah tepatnya. Dengan menggunakan Aspose.Words untuk .NET Anda dapat menambahkan, memposisikan, dan mengonfigurasi tombol sepenuhnya dari kode C#.

Penyisipan tombol ActiveX secara programatik menghilangkan pekerjaan UI manual dan memungkinkan pembuatan dokumen otomatis untuk formulir, laporan, atau templat interaktif. Dalam tutorial ini Anda akan belajar cara menggunakan **DocumentBuilder**, metode **InsertForms2OleControl**, dan properti terkait untuk menghasilkan tombol yang berfungsi penuh.

## Apa yang Anda perlukan

* .NET 6.0 SDK atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
* Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)
* IDE seperti Visual Studio 2022 atau VS Code
* Pengetahuan dasar tentang C# dan konsep dokumen Word

Tidak diperlukan instalasi Office tambahan karena Aspose.Words bekerja secara independen dari Microsoft Word.

## Langkah 1: Siapkan proyek C#

Buat proyek konsol baru dan tambahkan paket Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Pustaka `Aspose.Words` menyediakan kelas **DocumentBuilder** yang akan kita gunakan untuk memanipulasi dokumen.

## Langkah 2: Inisialisasi dokumen dan builder

Blok kode pertama membuat dokumen kosong dan sebuah instance `DocumentBuilder`. Objek ini merupakan titik masuk untuk semua operasi pemrosesan Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:** `DocumentBuilder` mempertahankan posisi kursor saat ini, sehingga setiap penyisipan berikutnya akan muncul tepat di tempat Anda menempatkan kursor.

## Langkah 3: Sisipkan tombol perintah ActiveX

Metode **InsertForms2OleControl** membuat kontrol ActiveX dengan tipe yang diminta. Di sini kami meminta `CommandButton` dan menentukan ukurannya dalam poin (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Penjelasan:**  
* `OleControlType.CommandButton` memberi tahu Aspose.Words untuk membuat tombol bukan tipe kontrol lain.  
* Metode ini mengembalikan objek `Forms2OleControl`, yang menyediakan bidang penempatan dan properti.

## Langkah 4: Posisi tombol dan atur propertinya

Setelah disisipkan Anda dapat memindahkan tombol ke lokasi mana pun di halaman dan memberikan nama programatik serta caption yang terlihat.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Tip pro:** Sistem koordinat dimulai dari sudut kiri‑atas halaman. Sesuaikan `Left` dan `Top` untuk menyelaraskan tombol dengan bidang formulir lainnya.

## Langkah 5: Simpan dokumen

Akhirnya, tulis dokumen ke disk. File akan berisi tombol ActiveX, siap dibuka di Microsoft Word di mana tombol menjadi interaktif.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Saat Anda membuka `ActiveXCommandButton.docx` di Word, Anda akan melihat tombol berlabel **Submit** pada lokasi yang ditentukan. Mengkliknya di Word akan memicu perilaku tombol perintah default (yang kemudian dapat Anda sesuaikan dengan VBA atau add‑in Word).

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian menghasilkan program mandiri yang dapat Anda salin, tempel, dan jalankan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Output yang diharapkan:** Konsol mencetak *“Document created successfully.”* dan folder kini berisi `ActiveXCommandButton.docx`. Membuka file di Microsoft Word menampilkan tombol **Submit** yang dapat diklik, diposisikan 100 pt dari margin kiri dan 150 pt dari atas halaman.

## Kesalahan umum dan cara menghindarinya

| Masalah | Mengapa terjadi | Solusi |
|-------|----------------|-----|
| Tombol muncul di luar halaman | Nilai `Left`/`Top` melebihi dimensi halaman | Gunakan `doc.FirstSection.PageSetup.PageWidth` dan `PageHeight` untuk menghitung koordinat yang aman |
| Tombol tidak terlihat di Word | Dokumen disimpan dalam format yang menghapus kontrol ActiveX (misalnya `.txt`) | Selalu simpan sebagai `.docx` atau `.doc` |
| Kesalahan runtime `ArgumentOutOfRangeException` | Lebar atau tinggi diatur ke nol atau negatif | Pastikan argumen ukuran yang diberikan ke `InsertForms2OleControl` adalah angka positif |

## Memperluas solusi

Anda dapat menyesuaikan tombol lebih lanjut dengan mengatur properti tambahan seperti `Enabled`, `Visible`, atau melampirkan makro melalui VBA. Kelas **Forms2OleControl** juga memungkinkan Anda menyisipkan kontrol ActiveX lain seperti kotak centang (`OleControlType.CheckBox`) atau kotak kombo (`OleControlType.ComboBox`).

Jika Anda perlu menghasilkan beberapa tombol dalam loop, enkapsulasi logika penyisipan dalam metode bantu:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Kesimpulan

Anda sekarang tahu cara **membuat tombol perintah ActiveX** dalam dokumen Word menggunakan C# dan Aspose.Words. Tutorial ini mencakup penyiapan proyek, penyisipan tombol dengan `InsertForms2OleControl`, penempatannya, dan menyimpan file akhir. Dengan dasar ini Anda dapat mengotomatisasi formulir kompleks, menyematkan kontrol interaktif, dan mengintegrasikan dokumen Word ke dalam solusi .NET yang lebih besar.

Selanjutnya, jelajahi topik terkait seperti bidang formulir **Aspose.Words ActiveX**, styling lanjutan **C# DocumentBuilder**, atau menambahkan secara programatik **kontrol ActiveX di Word** untuk kotak centang dan daftar drop‑down. Bereksperimenlah dengan koordinat dan ukuran yang berbeda untuk menyesuaikan kebutuhan tata letak spesifik Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Buat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Buat Dokumen Word dengan Tabel Menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}