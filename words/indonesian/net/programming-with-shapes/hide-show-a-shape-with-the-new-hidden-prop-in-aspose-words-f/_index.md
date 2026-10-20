---
category: general
date: 2026-10-20
description: Sembunyikan/Tampilkan Bentuk dengan properti `Hidden` baru menggunakan
  Aspose.Words untuk C#. Pelajari cara mengubah visibilitas bentuk, menangani kasus
  tepi, dan menyimpan hasilnya.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: id
lastmod: 2026-10-20
og_description: Sembunyikan/Tampilkan Bentuk dengan properti `Hidden` baru menggunakan
  Aspose.Words untuk C#. Kuasai pengaturan visibilitas bentuk dan hindari jebakan
  umum.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Sembunyikan/Tampilkan Bentuk dengan properti `Hidden` baru di Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Sembunyikan/Tampilkan Bentuk dengan Properti `Hidden` Baru di Aspose.Words
  untuk C#
url: /id/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sembunyikan/Tampilkan Bentuk dengan properti `Hidden` baru di Aspose.Words untuk C#

Jika Anda perlu **menyembunyikan/menampilkan sebuah Bentuk dengan properti `Hidden` baru** dalam dokumen Word, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Baik Anda menghasilkan laporan, membangun templat, atau membersihkan dokumen yang diimpor, mengendalikan visibilitas bentuk secara programatik menghemat waktu dibandingkan penyuntingan manual.

Dalam tutorial ini Anda akan belajar cara memuat dokumen, menemukan sebuah bentuk, mengubah properti `Hidden`, dan menyimpan file yang telah dimodifikasi. Langkah‑langkahnya juga mencakup variasi umum seperti menangani beberapa bentuk serta perbedaan antara grafik inline dan mengambang.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 (atau lebih baru) terpasang – Aspose.Words mendukung .NET Standard 2.0 dan .NET Core.  
* Salinan berlisensi **Aspose.Words untuk .NET** (versi percobaan gratis dapat digunakan untuk eksplorasi).  
* IDE seperti Visual Studio 2022 atau Visual Studio Code.  
* Dokumen Word (`input.docx`) yang berisi setidaknya satu bentuk (misalnya gambar, SmartArt, atau kanvas gambar).

## Langkah 1: Muat dokumen Word

Operasi pertama adalah membuat objek `Document` yang mewakili file .docx di disk.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Mengapa langkah ini penting*: `Document` adalah titik masuk untuk semua operasi Aspose.Words. Memuat file ke memori memberi Anda akses penuh ke pohon node‑nya, termasuk bentuk‑bentuk.

## Langkah 2: Dapatkan bentuk target

Untuk mengubah visibilitas, Anda harus memperoleh referensi ke node bentuk. Contoh di bawah mengambil bentuk pertama dalam dokumen, namun Anda dapat menyesuaikan logika untuk menemukan bentuk berdasarkan nama, tipe, atau indeks.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Mengapa langkah ini penting*: `GetChild` dengan argumen `true` melakukan pencarian mendalam, memastikan Anda menemukan bentuk meskipun berada di dalam tabel atau header. Memeriksa `null` mencegah `NullReferenceException` bila dokumen tidak memiliki bentuk.

## Langkah 3: Sembunyikan bentuk dengan properti `Hidden`

Aspose.Words memperkenalkan properti `Hidden` untuk mengontrol apakah sebuah bentuk dirender atau dicetak. Menetapkannya ke `true` menyembunyikan bentuk; menetapkannya ke `false` membuat bentuk kembali terlihat.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Jika Anda perlu **menampilkan** kembali bentuk yang sebelumnya disembunyikan, cukup beri nilai `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Mengapa langkah ini penting*: Properti `Hidden` berlaku untuk bentuk mengambang maupun inline, dan terintegrasi dengan format “Hidden” bawaan Word. Pendekatan ini lebih dapat diandalkan daripada menghapus bentuk karena node tetap berada dalam pohon dokumen, menjaga tata letak dan referensi.

## Langkah 4: Simpan dokumen yang telah dimodifikasi

Setelah mengatur visibilitas, tuliskan perubahan ke file baru (atau timpa file asli bila diinginkan).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Mengapa langkah ini penting*: `Save` menyerialkan pohon node dalam memori menjadi paket .docx yang dapat dibuka oleh Word. Flag tersembunyi dipertahankan, sehingga membuka file di Microsoft Word akan menampilkan bentuk sesuai pengaturan `Hidden`.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua langkah menghasilkan program mandiri yang dapat Anda salin, kompilasi, dan jalankan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Output yang diharapkan** saat Anda menjalankan program:

```
Document saved. Shape hidden = True
```

Membuka `ShapeHidden.docx` di Microsoft Word menampilkan dokumen tanpa bentuk yang ditargetkan. Jika Anda menetapkan `shape.Hidden = false;` sebelum menyimpan, bentuk akan muncul kembali.

## Menangani banyak bentuk

Contoh di atas bekerja untuk satu bentuk. Dokumen dunia nyata sering berisi banyak grafik. Gunakan loop untuk menyembunyikan atau menampilkan semua bentuk yang memenuhi kondisi (misalnya, nama atau tipe tertentu).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Tip*: Menyaring berdasarkan `ShapeType` menghindari penyembunyian tidak sengaja pada elemen dekoratif seperti kotak teks atau SmartArt.

## Kasus khusus dan praktik terbaik

| Situasi | Penanganan yang disarankan |
|-----------|----------------------|
| **Bentuk berada di dalam header/footer** | Ambil node header/footer terlebih dahulu, lalu panggil `GetChild(NodeType.Shape, …)` pada sub‑dokumen tersebut. |
| **Dokumen tidak mengandung bentuk** | Selalu periksa `null` setelah `GetChild` atau verifikasi `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Anda perlu mempertahankan flag tersembunyi di berbagai versi Word** | Properti `Hidden` disimpan dalam XML bentuk sebagai `<w:hidden/>`, yang didukung oleh Word 2007 dan versi selanjutnya. |
| **Kinerja pada dokumen besar** | Gunakan `doc.GetChildNodes(NodeType.Shape, true)` sekali dan pakai koleksi tersebut alih‑alih memanggil `GetChild` berulang kali. |

## Pro tip: Kombinasikan `Hidden` dengan `WrapType`

Saat sebuah bentuk disembunyikan, Word tetap menyisakan ruang yang biasanya ditempati kecuali Anda juga mengubah perilaku pembungkusnya. Menetapkan `WrapType = WrapType.None` menghapus area placeholder.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Ini memastikan tata letak runtuh seolah‑olah bentuk tidak pernah ada, yang berguna untuk menghasilkan laporan yang bersih.

## Kesimpulan

Anda kini mengetahui cara **menyembunyikan/menampilkan sebuah Bentuk dengan properti `Hidden` baru** menggunakan Aspose.Words untuk C#. Solusi ini mencakup memuat dokumen, menemukan bentuk, mengubah properti `Hidden`, dan menyimpan perubahan. Dengan mengikuti tip praktik terbaik—memeriksa `null`, menangani banyak bentuk, dan menyesuaikan pengaturan pembungkus—Anda dapat mengendalikan visibilitas bentuk secara andal dalam skenario otomatisasi Word apa pun.

Siap menjelajah lebih jauh? Pertimbangkan langkah selanjutnya berikut:

* **Sembunyikan/Tampilkan banyak bentuk** berdasarkan metadata khusus (menggunakan teknik “programmatically hide shape”).  
* **Kombinasikan `Hidden` dengan konten bersyarat** menggunakan field Aspose.Words untuk pembuatan laporan dinamis.  
* **Jelajahi properti node lainnya**, seperti `Visible` untuk objek diagram atau `IsDeleted` untuk kontrol tingkat paragraf.

Selamat coding, dan nikmati kontrol halus yang diberikan Aspose.Words untuk visibilitas bentuk dalam dokumen Word!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}