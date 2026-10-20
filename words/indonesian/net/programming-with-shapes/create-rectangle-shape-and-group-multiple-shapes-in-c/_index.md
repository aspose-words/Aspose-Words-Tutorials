---
category: general
date: 2026-09-18
description: Buat bentuk persegi panjang dalam dokumen Word menggunakan C#. Pelajari
  cara menambahkan beberapa bentuk, menambahkan bentuk ke dalam grup, dan menyisipkan
  bentuk grup dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: id
lastmod: 2026-09-18
og_description: Buat bentuk persegi panjang dalam file Word dengan C#. Panduan ini
  menunjukkan cara menambahkan beberapa bentuk, menambahkan bentuk ke dalam grup,
  dan menyisipkan bentuk grup menggunakan Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Buat bentuk persegi panjang dan grupkan bentuk‑bentuk di C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Buat bentuk persegi panjang dan grupkan beberapa bentuk dalam C#
url: /id/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang dan mengelompokkan beberapa bentuk di C#

Jika Anda perlu **membuat bentuk persegi panjang** dalam dokumen Word, tutorial ini menunjukkan solusi lengkap. Anda akan melihat cara **menambahkan beberapa bentuk**, **menambahkan bentuk ke dalam grup**, dan **menyisipkan grup bentuk** menggunakan Aspose.Words API untuk .NET.

Bekerja dengan bentuk adalah kebutuhan umum saat menghasilkan laporan, kontrak, atau materi pemasaran secara programatis. Pada akhir panduan ini Anda akan memiliki aplikasi konsol C# yang dapat dijalankan dan menghasilkan file `.docx` yang berisi sebuah persegi panjang, sebuah elips, serta sebuah grup yang memuat kedua bentuk tersebut.

Prasyarat satu‑satunya adalah .NET SDK terbaru (6.0 atau lebih baru) dan salinan berlisensi Aspose.Words untuk .NET. Tidak diperlukan alat tambahan.

## Prasyarat

- .NET 6.0 SDK atau yang lebih baru  
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)  
- Familiaritas dasar dengan sintaks C#  

Anda dapat menginstal paket dengan perintah berikut:

```bash
dotnet add package Aspose.Words
```

## Langkah 1: Membuat bentuk persegi panjang dengan Aspose.Words

Langkah pertama adalah membuat objek `Shape` dengan tipe `Rectangle`. Objek ini mewakili persegi panjang visual yang akan muncul di dokumen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Mengapa ini penting:** `ShapeType.Rectangle` memberi tahu Aspose.Words untuk merender sebuah persegi panjang geometris. Menetapkan `Width` dan `Height` menentukan ukuran dalam poin (1 poin = 1/72 inci). Menambahkan warna isi dan garis membuat bentuk terlihat tanpa memerlukan styling tambahan.

## Langkah 2: Menambahkan beberapa bentuk ke dokumen

Setelah persegi panjang, Anda dapat membuat sejumlah bentuk tambahan. Pada contoh ini kami menambahkan sebuah elips untuk mendemonstrasikan cara **menambahkan beberapa bentuk**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Mengapa ini penting:** Setiap pemanggilan `new Shape` membuat objek gambar yang independen. Dengan menyisipkannya secara berurutan Anda membangun koleksi bentuk yang kemudian dapat dikelompokkan atau diposisikan secara individual.

## Langkah 3: Menambahkan bentuk ke grup

Mengelompokkan bentuk menyederhanakan manajemen tata letak karena grup berperilaku sebagai satu node. Langkah ini menunjukkan cara **menambahkan bentuk ke grup** menggunakan `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Mengapa ini penting:** `GroupShape` berfungsi seperti sebuah kontainer. Ketika Anda memindahkan, memutar, atau mengubah ukuran grup, semua bentuk anak akan mengikuti secara otomatis. Kotak pembatas (200 × 200 poin) menentukan ruang koordinat untuk bentuk‑bentuk anak.

## Langkah 4: Menyisipkan grup bentuk ke dalam dokumen

Setelah grup berisi persegi panjang dan elips, Anda perlu **menyisipkan grup bentuk** pada lokasi yang diinginkan. Builder sudah menempatkan grup kosong, tetapi Anda juga dapat menyisipkannya di tempat lain bila diperlukan.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Mengapa ini penting:** Menyesuaikan `Left` dan `Top` memindahkan seluruh grup di dalam halaman. Menyimpan dokumen menuliskan hierarki bentuk ke file `.docx` yang dapat dibuka di Microsoft Word, LibreOffice, atau penampil kompatibel lainnya.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang menggabungkan semua langkah. Salin kode ke proyek konsol baru dan jalankan untuk menghasilkan `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Output yang diharapkan:**  
Membuka `GroupShapeExample.docx` menampilkan satu grup yang berisi persegi panjang berwarna biru‑muda dan elips berwarna merah‑karang muda, keduanya diposisikan di dalam kontainer 200 × 200 poin. Grup dapat dipilih sebagai satu objek di Word, menandakan bahwa **menambahkan bentuk ke grup** berhasil.

## Variasi umum dan kasus tepi

| Situasi | Penyesuaian yang disarankan |
|-----------|------------------------|
| Jenis bentuk berbeda (mis., `ShapeType.Line`) | Buat bentuk dengan `ShapeType` yang diinginkan dan atur geometri sesuai. |
| Perlu memutar sebuah bentuk | Gunakan `shape.Rotation = 45;` (derajat) sebelum menambahkannya ke grup. |
| Dokumen besar dengan banyak grup | Gunakan satu instance `DocumentBuilder`; hindari membuat builder baru untuk setiap grup guna mengurangi beban memori. |
| Menyimpan ke PDF alih‑alih DOCX | Panggil `doc.Save("output.pdf", SaveFormat.Pdf);` setelah grup disisipkan. |

**Tip pro:** Selalu tetapkan nilai `Left` dan `Top` yang eksplisit untuk grup ketika Anda memerlukan penempatan yang tepat. Jika Anda mengabaikannya, grup akan mewarisi posisi kursor builder saat ini, yang dapat menghasilkan tata letak yang tidak terduga.

## Kesimpulan

Anda kini tahu cara **membuat bentuk persegi panjang**, **menambahkan beberapa bentuk**, **menambahkan bentuk ke grup**, dan **menyisipkan grup bentuk** dalam dokumen Word menggunakan C#. Contoh lengkap memperlihatkan alur kerja penuh mulai dari pembuatan dokumen hingga penyimpanan file akhir.  

Selanjutnya, jelajahi topik terkait seperti **menempatkan bentuk relatif terhadap teks**, **menerapkan pembungkus teks**, dan **mengekspor bentuk yang dikelompokkan ke PDF**. Ekstensi‑ekstensi ini memungkinkan Anda membangun tata letak dokumen yang canggih dan programatis dengan Aspose.Words.

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}