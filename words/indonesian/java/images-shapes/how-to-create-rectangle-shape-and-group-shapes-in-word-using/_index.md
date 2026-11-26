---
category: general
date: 2026-11-18
description: Pelajari cara membuat bentuk persegi panjang dalam dokumen Word dengan
  C#. Panduan ini juga mencakup cara mengatur ukuran bentuk, mengatur posisi bentuk,
  dan mengelompokkan bentuk di Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: id
lastmod: 2026-11-18
og_description: Buat bentuk persegi panjang dalam file Word menggunakan C# dan pelajari
  cara mengatur dimensi bentuk, mengatur posisi bentuk, serta mengelompokkan bentuk
  di Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Buat bentuk persegi panjang dan grupkan bentuk di Word dengan C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cara membuat bentuk persegi panjang dan mengelompokkan bentuk di Word menggunakan
  C#
url: /id/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat bentuk persegi panjang dan mengelompokkan bentuk di Word menggunakan C#

Jika Anda perlu **membuat bentuk persegi panjang** dalam dokumen Word, tutorial ini menunjukkan solusi lengkap yang siap dijalankan. Anda akan melihat cara mengatur ukuran bentuk, mengatur posisi bentuk, dan mengelompokkan bentuk di Word sehingga mereka berperilaku sebagai satu objek.

Bekerja dengan bentuk merupakan kebutuhan umum saat menghasilkan laporan, faktur, atau diagram secara programatis. Pada akhir panduan ini Anda akan dapat menghasilkan file `.docx` yang berisi persegi panjang, elips, dan sebuah kontainer yang dikelompokkan—semua dibuat dengan Aspose.Words untuk .NET.

## Prasyarat

- .NET 6.0 SDK atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)
- Editor kode atau IDE (Visual Studio, VS Code, Rider, dll.)

Tidak ada pustaka tambahan yang diperlukan.

## Cara membuat bentuk persegi panjang dan mengelompokkan bentuk di Word

Langkah‑langkah inti adalah:

1. **Buat dokumen kosong** dan sebuah `DocumentBuilder`.
2. **Sisipkan sebuah `GroupShape`** yang akan menampung bentuk‑bentuk individual.
3. **Buat bentuk persegi panjang**, atur dimensinya, dan tambahkan ke grup.
4. **Buat bentuk elips**, atur ukuran dan posisinya, lalu tambahkan ke grup.
5. **Simpan** dokumen.

Setiap langkah dijelaskan di bawah, dan kode sumber lengkap mengikuti penjelasan.

### Langkah 1: Inisialisasi dokumen dan builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` mewakili seluruh file Word, sementara `DocumentBuilder` menyediakan API fluens untuk menyisipkan konten. Menginisialisasinya wajib sebelum Anda dapat menambahkan bentuk apa pun.

### Langkah 2: Sisipkan grup bentuk

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` berfungsi seperti kontainer; semua bentuk anak bergerak bersama. Ini adalah cara yang direkomendasikan untuk **mengelompokkan bentuk di Word** ketika Anda memerlukan transformasi kolektif (misalnya, memindahkan, memutar, atau menghapus).

### Langkah 3: Buat persegi panjang dan atur ukurannya

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Di sini kita **membuat bentuk persegi panjang** dan **mengatur ukuran bentuk** dengan menetapkan `Width` dan `Height`. Pada Aspose.Words, ukuran dinyatakan dalam poin (1 pt ≈ 1/72 in). Menetapkan dimensi secara eksplisit memastikan persegi panjang muncul persis seperti yang diinginkan.

### Langkah 4: Buat elips, atur dimensi, dan posisikan

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

**Mengatur dimensi bentuk** untuk elips identik untuk lebar dan tinggi, menghasilkan lingkaran sempurna. Properti `Left` memperlihatkan **mengatur posisi bentuk**: elips dimulai 120 pt ke kanan dari asal grup, sehingga tidak tumpang tindih dengan persegi panjang.

### Langkah 5: Simpan dokumen

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Menyimpan menuliskan file Word ke disk. Anda dapat membuka `GroupShape.docx` di Microsoft Word untuk memverifikasi bahwa persegi panjang dan elips telah dikelompokkan serta diposisikan dengan benar.

## Mengatur dimensi dan ukuran bentuk – penjelasan lebih dalam

- **Poin vs. inci**: 72 pt = 1 in. Jika Anda lebih suka inci, kalikan dengan 72 (misalnya, `2.5 * 72` untuk 2,5 in).
- **Skala otomatis**: Jika Anda mengabaikan `Width` atau `Height`, bentuk akan menggunakan ukuran defaultnya. **Atur ukuran bentuk** secara eksplisit untuk menghindari kejutan tata letak.
- **Rasio aspek**: Untuk bentuk seperti `Ellipse`, menjaga `Width` dan `Height` sama mempertahankan tampilan melingkar.

## Memposisikan bentuk di Word

Properti `Left` dan `Top` mengontrol offset bentuk di dalam kontainernya (grup atau halaman). Nilai positif memindahkan bentuk ke kanan/bawah; nilai negatif menggeser ke kiri/atas. Saat dikelompokkan, posisi bersifat relatif terhadap asal grup, yang menyederhanakan perhitungan tata letak.

## Mengelompokkan bentuk di Word menggunakan Aspose.Words

Pengelompokan penting ketika Anda ingin beberapa bentuk berperilaku sebagai satu unit. Objek `GroupShape`:

- Mendukung `AppendChild` untuk menambahkan bentuk apa pun (`Shape`) (persegi panjang, elips, gambar, dll.).
- Memungkinkan Anda memindahkan, memutar, atau menghapus seluruh grup dengan satu panggilan.
- Menjaga posisi bentuk anak relatif terhadap grup, memudahkan pengelolaan diagram kompleks.

**Tips profesional:** Setelah menambahkan semua bentuk anak, Anda dapat menyesuaikan `Width`, `Height`, `Left`, dan `Top` grup untuk memindahkan seluruh koleksi dalam satu langkah.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Program ini mencakup semua direktif `using`, metode `Main`, serta komentar yang menjelaskan setiap baris.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Output yang diharapkan:** Setelah menjalankan program, `GroupShape.docx` muncul di folder eksekusi. Membukanya di Word menampilkan persegi panjang (100 pt × 50 pt) di sebelah kiri dan elips (80 pt × 80 pt) diposisikan 120 pt ke kanan, keduanya berada dalam satu objek yang dikelompokkan.

![Dokumen Word dengan persegi panjang dan elips yang dikelompokkan](grouped_shapes.png){: .center alt="Tangkapan layar dokumen Word yang menampilkan persegi panjang dan elips yang dikelompokkan yang dibuat dengan C#" }

*Gambar di atas menggambarkan hasil akhir; persegi panjang dan elips dapat dipilih sebagai satu grup.*

## Pertanyaan umum dan kasus khusus

| Pertanyaan | Jawaban |
|------------|---------|
| **Apakah saya dapat menambahkan lebih dari dua bentuk?** | Ya. Panggil `group.AppendChild(yourShape)` untuk setiap bentuk tambahan. |
| **Bagaimana jika saya perlu memutar grup?** | Gunakan `group.RotationAngle = 45;` (derajat) setelah menambahkan semua anak. |
| **Bagaimana cara mengubah warna latar belakang grup?** | Setel `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Apakah ini akan bekerja dengan file .doc?** | Aspose.Words mendukung `.doc` dan `.docx`. Kode yang sama berfungsi; cukup ubah ekstensi file pada `Save`. |
| **Apakah ada dampak memori saat mengelompokkan banyak bentuk?** | Pengelompokan sendiri menambah overhead minimal. Kekhawatiran utama adalah total jumlah bentuk; jaga agar tetap wajar untuk dokumen besar. |

## Kesimpulan

Dalam tutorial ini Anda belajar cara **membuat bentuk persegi panjang** dalam file Word menggunakan C#, cara **mengatur ukuran bentuk**, **mengatur dimensi bentuk**, **mengatur posisi bentuk**, dan akhirnya cara **mengelompokkan bentuk di Word** dengan Aspose.Words. Contoh lengkap menunjukkan pendekatan yang bersih dan dapat dipelihara yang dapat Anda kembangkan menjadi diagram, grafik, atau grafis khusus yang lebih kompleks.

Selanjutnya, Anda dapat menjelajahi:

- Menambahkan teks di dalam bentuk (`Shape.TextPath.Text = "Hello"`).
- Menyisipkan gambar ke dalam `GroupShape`.
- Mengekspor bentuk yang dikelompokkan ke PDF dengan `doc.Save("output.pdf")`.

Silakan bereksperimen dengan ukuran, posisi, dan tipe bentuk tambahan untuk menyesuaikan kebutuhan proyek Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}