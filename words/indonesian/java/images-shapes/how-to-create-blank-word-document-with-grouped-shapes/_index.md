---
category: general
date: 2026-09-08
description: Pelajari cara membuat dokumen Word kosong, menyisipkan bentuk persegi
  panjang, dan mengelompokkan beberapa bentuk menggunakan C#. Ikuti panduan langkah
  demi langkah ini.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: id
lastmod: 2026-09-08
og_description: Buat dokumen Word kosong, sisipkan bentuk persegi panjang, dan grupkan
  beberapa bentuk dalam C#. Tutorial ini memandu Anda melalui proses lengkap.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Buat dokumen Word kosong dengan bentuk yang dikelompokkan di C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cara membuat dokumen Word kosong dengan bentuk yang dikelompokkan
url: /id/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dengan bentuk yang dikelompokkan

Jika Anda perlu **membuat dokumen Word kosong** yang berisi grafik khusus, panduan ini menunjukkan cara melakukannya secara tepat. Anda akan belajar **menyisipkan bentuk persegi panjang**, **mengelompokkan beberapa bentuk**, dan **menambahkan bentuk ke dalam grup** menggunakan Aspose.Words untuk .NET.

Dokumen kosong memberi Anda kanvas bersih, dan mengelompokkan bentuk memungkinkan Anda memindahkan, mengubah ukuran, atau memutar mereka sebagai satu unit. Tutorial ini mencakup setiap langkah—dari menginisialisasi dokumen hingga menyimpan file akhir—sehingga Anda dapat menyalin kode ke dalam proyek Anda sendiri dan melihat hasilnya secara langsung.

## Apa yang Anda perlukan

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 atau yang lebih baru (kode ini juga berfungsi dengan .NET Framework 4.6+)
* Lisensi Aspose.Words untuk .NET yang valid (evaluasi gratis dapat digunakan untuk pengujian)
* IDE seperti Visual Studio 2022 atau Visual Studio Code
* Familiaritas dasar dengan sintaks C#

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Cara membuat dokumen Word kosong

Langkah pertama adalah menginstansiasi objek `Document`. Objek ini mewakili file `.docx` kosong yang dapat Anda edit dengan `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Konstruktor `Document` membuat **dokumen Word kosong** di memori. `DocumentBuilder` menyediakan API yang fluently untuk menyisipkan teks, gambar, dan objek gambar.

## Menyisipkan bentuk persegi panjang ke dalam dokumen

Selanjutnya, tambahkan bentuk persegi panjang. Persegi panjang akan menjadi anak pertama dari grup yang akan kita buat nanti.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Pemanggilan `InsertShape` dengan `ShapeType.Rectangle` **menyisipkan bentuk persegi panjang** pada posisi kursor saat ini. Lebar dan tinggi dinyatakan dalam poin (1 pt ≈ 1/72 in).

## Mengelompokkan beberapa bentuk bersama-sama

`GroupShape` berfungsi seperti sebuah wadah. Semua bentuk anak di dalam grup bergerak dan bertransformasi bersama. Pertama, buat grupnya, lalu tambahkan persegi panjang yang baru saja kita buat.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Metode `InsertGroupShape` menempatkan grup kosong pada kursor builder. Dengan menambahkan persegi panjang, kita **mengelompokkan beberapa bentuk**—persegi panjang menjadi bagian dari koleksi node internal grup.

## Menambahkan bentuk ke grup dan menyimpan file

Sekarang tambahkan bentuk kedua—sebuah elips—untuk mendemonstrasikan bagaimana beberapa objek berbagi wadah yang sama. Setelah itu, simpan dokumen.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Pemanggilan `InsertShape` **menambahkan bentuk ke grup** ketika Anda menambahkan `Shape` yang dikembalikan ke `GroupShape`. Menyimpan `Document` menulis file `.docx` yang dapat Anda buka di Microsoft Word, LibreOffice, atau penampil kompatibel lainnya.

### Hasil yang diharapkan

Saat Anda membuka *GroupShapeDemo.docx*, Anda akan melihat halaman kosong dengan objek yang dikelompokkan yang berisi persegi panjang biru muda dan elips merah muda. Memilih grup memungkinkan Anda memindahkan kedua bentuk sekaligus, menegaskan bahwa **mengelompokkan beberapa bentuk** berhasil seperti yang diharapkan.

## Mengapa menggunakan GroupShape?

* **Transformasi atomik** – Menskalakan, memutar, atau memindahkan grup memengaruhi semua anak secara seragam.
* **Organisasi logis** – Menjaga grafik yang terkait bersama, membuat struktur dokumen lebih mudah dipelihara.
* **Kinerja** – Merender satu wadah seringkali lebih cepat daripada menangani banyak bentuk independen.

Jika Anda perlu memodifikasi satu anak nanti, Anda dapat mengambilnya dari `group.ChildNodes` berdasarkan indeks atau properti `Name`‑nya.

## Variasi umum dan kasus tepi

| Skenario                                 | Cara menyesuaikan kode                                                            |
|------------------------------------------|-----------------------------------------------------------------------------------|
| **Berbagai jenis bentuk**                | Ganti `ShapeType.Rectangle` atau `ShapeType.Ellipse` dengan `ShapeType` lain apa pun |
| **Menambahkan teks di dalam bentuk**     | Gunakan `Shape.TextPath.Text = "Hello"` setelah menyisipkan bentuk                |
| **Mengatur sudut rotasi**                | `group.Rotation = 45;` (derajat)                                                  |
| **Menyimpan sebagai PDF bukan DOCX**    | `doc.Save("GroupShapeDemo.pdf");`                                                 |
| **Menerapkan border pada grup**          | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`                |

## Tips profesional

* **Berikan nama pada bentuk Anda** – `rectangle.Name = "MyRect";` memudahkan pencarian nanti.
* **Gunakan posisi relatif** – Atur `group.RelativeHorizontalPosition` ke `RelativeHorizontalPosition.Page` jika Anda ingin grup tetap terikat pada margin halaman.
* **Bebaskan sumber daya** – Bungkus `Document` dalam blok `using` saat bekerja pada aplikasi yang lebih besar untuk membebaskan memori tak terkelola dengan cepat.

## Kode sumber lengkap untuk salin‑tempel cepat

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Salin kode ke dalam proyek konsol baru, pulihkan paket NuGet `Aspose.Words`, dan jalankan. File output akan muncul di folder `bin/Debug/net6.0` (atau setara) proyek Anda.

## Langkah selanjutnya

Sekarang Anda dapat **membuat dokumen Word kosong**, **menyisipkan bentuk persegi panjang**, dan **mengelompokkan beberapa bentuk**, Anda mungkin ingin mengeksplorasi:

* Menambahkan **kotak teks** di dalam grup untuk membuat diagram berlabel.
* Mengekspor grafik yang dikelompokkan ke gambar dengan `doc.Save("image.png", SaveFormat.Png)`.
* Menggabungkan grup dengan tabel untuk laporan yang diformat kaya.

Bereksperimenlah dengan properti bentuk yang berbeda, hierarki grup, dan format ekspor untuk memanfaatkan sepenuhnya kemampuan menggambar Aspose.Words.

--- 

*Ingat*: mengelompokkan bentuk adalah cara yang kuat untuk menjaga dokumen Word Anda tetap rapi dan kode Anda dapat dipelihara. Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}