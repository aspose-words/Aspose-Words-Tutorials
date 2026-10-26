---
category: general
date: 2026-10-23
description: Pelajari cara menyisipkan elips dan menambahkan bentuk persegi panjang
  di Word menggunakan Aspose.Words. Termasuk memindahkan kursor ke bentuk dan cara
  membuat grup bentuk.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: id
lastmod: 2026-10-23
og_description: Cara menyisipkan elips dan cara menambahkan bentuk persegi panjang
  di Word dengan Aspose.Words. Ikuti panduan langkah demi langkah untuk memindahkan
  kursor ke bentuk dan membuat grup bentuk.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Cara menyisipkan bentuk elips dan persegi panjang dalam grup bentuk Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cara menyisipkan bentuk elips dan persegi panjang di dalam grup bentuk dengan
  Aspose.Words
url: /id/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan bentuk elips dan persegi panjang di dalam bentuk grup dengan Aspose.Words

Jika Anda perlu mengetahui **how to insert ellipse** dalam dokumen Word secara programatis, panduan ini menunjukkan proses lengkapnya. Anda juga akan melihat **how to add rectangle** shape, belajar **move cursor to shape**, dan menemukan **how to create group shape** yang menampung beberapa objek gambar.

Otomasi Word sering memerlukan penempatan yang tepat dari objek gambar. Pada akhir tutorial ini Anda dapat menghasilkan file `.docx` yang berisi persegi panjang dan elips yang dikelompokkan, siap untuk penataan lebih lanjut atau ekspor. Tidak diperlukan alat eksternal selain pustaka Aspose.Words untuk .NET dan lingkungan pengembangan .NET.

## Prasyarat

* .NET 6.0 atau yang lebih baru terpasang.
* Aspose.Words untuk .NET (paket NuGet `Aspose.Words`) ditambahkan ke proyek Anda.
* Pengetahuan dasar tentang sintaks C# dan Visual Studio (atau IDE apa pun).

Persyaratan ini memastikan kode dapat dikompilasi tanpa konfigurasi tambahan.

## Cara membuat group shape di Word

Group shape berfungsi sebagai kontainer yang memungkinkan Anda memindahkan, memutar, atau memformat beberapa bentuk sebagai satu unit. Kode berikut membuat grup dengan ukuran tertentu (300 × 200 poin) dan menyiapkan dokumen untuk operasi gambar lebih lanjut.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Mengapa langkah ini penting*: Group shape mendefinisikan sistem koordinat lokal. Semua bentuk yang ditambahkan setelah memindahkan kursor ke dalam grup akan diposisikan relatif terhadap asal grup, membuat perhitungan tata letak menjadi sederhana.

## Cara menambahkan bentuk persegi panjang di Word

Sekarang grup sudah ada, Anda dapat **insert rectangle shape** di dalamnya. Persegi panjang akan berfungsi sebagai latar belakang atau placeholder visual untuk konten lain.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Penjelasan*: `MoveTo(group)` memberi tahu builder bahwa titik sisipan aktif adalah group shape. Tanpa memindahkan kursor, `InsertShape` akan menambahkan persegi panjang ke badan dokumen utama alih-alih ke grup.

## Cara menyisipkan elips

Dengan persegi panjang sudah ditempatkan, Anda sekarang dapat mendemonstrasikan **how to insert ellipse**. Elips akan berada di tengah grup yang sama, menindih persegi panjang jika diinginkan.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Mengapa kursor harus dipindahkan*: Setiap pemanggilan `InsertShape` menghormati lokasi kursor saat ini. Memanggil kembali `MoveTo(group)` menjamin bahwa elips juga menjadi anak grup, mempertahankan hierarki yang dimaksud.

## Pindahkan kursor ke shape sebelum menyisipkan objek tambahan

Jika Anda perlu menambahkan lebih banyak bentuk nanti, selalu **move cursor to shape** sebelum setiap penyisipan. Pola ini menghindari penempatan tidak sengaja di luar grup.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tip*: Menggunakan kembali `MoveTo(group)` murah dan meningkatkan keterbacaan kode. Ini juga mempermudah pemeliharaan di masa depan karena konteks penyisipan menjadi eksplisit.

## Simpan dokumen

Akhirnya, simpan dokumen ke disk. Contoh ini menyimpan file sebagai `GroupShape.docx` di folder yang Anda tentukan.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Saat Anda membuka file yang disimpan di Microsoft Word, Anda akan melihat satu grup yang berisi persegi panjang dan elips, keduanya diposisikan dengan benar.

### Output yang Diharapkan

* File `.docx` bernama `GroupShape.docx`.
* Di dalam dokumen, objek gambar yang dikelompokkan berukuran 300 × 200 poin.
* Di dalam grup:
  * Sebuah persegi panjang (100 × 50 poin) terletak pada asal grup.
  * Sebuah elips (80 × 80 poin) menindih persegi panjang.
  * Setiap bentuk tambahan yang Anda tambahkan setelah memindahkan kursor.

## Variasi umum dan kasus tepi

| Situation | Recommended approach |
|-----------|----------------------|
| **Berbagai ukuran unit** | Aspose.Words menggunakan poin (1 pt = 1/72 in). Konversikan sentimeter atau inci ke poin sebelum memanggil `InsertShape`. |
| **Memutar bentuk di dalam grup** | Setelah menyisipkan sebuah shape, ambil objek `ShapeBase`-nya dan atur `ShapeBase.RotationAngle`. |
| **Menambahkan teks di dalam shape** | Gunakan `ShapeBase.AppendChild(new Paragraph(document))` lalu tambahkan `Run` dengan teks yang diinginkan. |
| **Menyimpan ke PDF alih-alih DOCX** | Panggil `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – hierarki grup dipertahankan dalam output PDF. |

Variasi ini menunjukkan bahwa logika **how to insert ellipse** yang sama dapat disesuaikan untuk banyak skenario dunia nyata.

## Tips profesional

* **Gunakan kembali instance `DocumentBuilder` yang sama** – ini mengurangi beban memori dan menjaga konsistensi status dokumen.
* **Validasi dimensi shape** – lebar atau tinggi yang sangat besar dapat menyebabkan masalah rendering pada versi Word yang lebih lama.
* **Group sebelum styling** – menerapkan warna isi atau gaya garis ke grup setelah semua anak ditambahkan memastikan tampilan yang seragam.

## Kesimpulan

Anda sekarang memahami **how to insert ellipse** dan **how to add rectangle** shape di dalam kontainer yang dikelompokkan dalam dokumen Word menggunakan Aspose.Words. Dengan secara konsisten **move cursor to shape** sebelum setiap penyisipan, Anda menjaga hierarki yang bersih dan menghindari penempatan tidak sengaja. Contoh lengkap ini dapat dikompilasi, dijalankan, dan menghasilkan shape yang dikelompokkan yang dapat disesuaikan lebih lanjut atau diekspor.

Siap untuk menjelajahi lebih lanjut? Cobalah menggabungkan teknik ini dengan **how to create group shape** untuk diagram kompleks, atau bereksperimen dengan **insert rectangle shape word** bersama kotak teks untuk pembuatan laporan yang kaya. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat bentuk persegi panjang dan grup shape di Word dengan Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Cara membuat dokumen Word kosong dan menambahkan bentuk elips tersembunyi dalam C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Cara membuat group shape docx dan menambahkan kontrol interaktif dalam C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}