---
category: general
date: 2026-10-20
description: Pelajari cara membuat dokumen Word kosong, mengelompokkan bentuk di Word,
  mengatur warna isi bentuk, dan menggunakan jenis pembungkus inline dengan contoh
  lengkap C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: id
lastmod: 2026-10-20
og_description: Buat dokumen Word kosong, kelompokkan bentuk di Word, dan atur warna
  isi bentuk dengan jenis pembungkus inline menggunakan Aspose.Words dan C#. Ikuti
  tutorial lengkap.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Buat dokumen Word kosong dan grupkan bentuk di Word – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cara membuat dokumen Word kosong dan mengelompokkan bentuk di Word menggunakan
  Aspose.Words
url: /id/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dan mengelompokkan bentuk di Word

Jika Anda perlu **membuat dokumen Word kosong** yang berisi beberapa bentuk yang berfungsi sebagai satu unit, panduan ini menunjukkan cara melakukannya secara tepat. Anda akan melihat cara **mengelompokkan bentuk di Word**, mengatur warna isi bentuk, dan menerapkan **wrap type inline**—semua dengan program C# yang singkat dan dapat dijalankan.

Tutorial ini membimbing Anda melalui setiap baris kode, menjelaskan mengapa setiap langkah penting, dan menyoroti jebakan umum. Pada akhir tutorial Anda akan memiliki file .docx yang menampilkan sebuah persegi panjang dan kotak teks yang dikelompokkan bersama, siap untuk otomatisasi lebih lanjut.

## Apa yang akan Anda pelajari

* Cara menginisialisasi file Word kosong dengan Aspose.Words.
* Cara yang benar untuk membuat **GroupShape** dan menambahkan bentuk anak.
* Teknik untuk **set shape fill color** dan mengontrol posisi.
* Menggunakan **wrap type inline** sehingga grup berperilaku seperti satu objek inline.
* Cara menyimpan dan memverifikasi hasilnya.

Tidak diperlukan pengalaman sebelumnya dengan Aspose.Words, tetapi Anda sebaiknya nyaman dengan sintaks dasar C# dan memiliki Visual Studio (atau IDE lain) terpasang.

## Prasyarat

| Persyaratan | Alasan |
|-------------|--------|
| .NET 6.0 atau lebih baru | Menyediakan runtime untuk proyek C#. |
| Aspose.Words untuk .NET (versi terbaru) | Menyediakan kelas `Document`, `DocumentBuilder`, dan kelas bentuk yang digunakan dalam contoh. |
| Jalur folder yang dapat ditulisi | Panggilan `doc.Save` memerlukan direktori yang valid untuk menulis file output. |
| Pengetahuan dasar C# | Memungkinkan Anda mengikuti kode dan memodifikasinya untuk skenario Anda sendiri. |

Instal Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Langkah 1: Buat dokumen Word kosong

Operasi pertama adalah **membuat dokumen Word kosong**. Kelas `Document` milik Aspose.Words mewakili file Word dalam memori, dan `DocumentBuilder` menyediakan API yang nyaman untuk mengeditnya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting*: Memulai dengan dokumen bersih menjamin bahwa bentuk grup yang Anda tambahkan akan menjadi satu‑satunya konten, sehingga verifikasi menjadi sederhana.

## Langkah 2: Definisikan grup bentuk dengan wrap type inline

Sebuah **GroupShape** berfungsi sebagai wadah untuk bentuk‑bentuk lain. Menetapkan `WrapType`‑nya ke `Inline` memastikan grup berperilaku seperti satu objek inline dalam alur paragraf.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Mengapa ini penting*: Menggunakan **wrap type inline** mencegah grup mengapung menjauh dari teks di sekitarnya, yang penting ketika Anda ingin grup bergerak sebagai satu unit.

## Langkah 3: Tambahkan persegi panjang dan atur warna isi bentuk

Persegi panjang adalah elemen visual yang umum. Konstruktor `Shape` menerima `ShapeType`; kemudian kita menentukan dimensi dan warna isi.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Mengapa ini penting*: Properti `FillColor` memperlihatkan **set shape fill color** secara praktis, memberikan persegi panjang latar belakang biru‑muda yang menonjol di dokumen akhir.

## Langkah 4: Tambahkan kotak teks – cara mengelompokkan bentuk secara efektif

Kotak teks menyediakan teks yang dapat diedit di dalam grup. Posisionkan relatif terhadap sistem koordinat grup dengan menyesuaikan properti `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Mengapa ini penting*: Langkah ini menjawab **how to group shapes**—dengan menambahkan setiap bentuk anak ke instance `GroupShape` yang sama. Offset `Top` memastikan kotak teks muncul di bawah persegi panjang, memperlihatkan kontrol tata letak yang tepat.

## Langkah 5: Sisipkan grup bentuk yang selesai ke dalam dokumen

Setelah grup berisi kedua bentuk anak, sisipkan pada posisi builder saat ini.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Mengapa ini penting*: Menyisipkan grup sebagai satu node menjamin Word memperlakukan persegi panjang dan kotak teks sebagai satu objek logis, mempertahankan posisi relatif mereka saat penyuntingan.

## Langkah 6: Simpan dokumen dan verifikasi output

Akhirnya, tulis dokumen ke disk. Ganti `YOUR_DIRECTORY` dengan jalur nyata di mesin Anda.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Saat Anda membuka `GroupShape.docx` di Microsoft Word, Anda harus melihat persegi panjang biru‑muda dengan kotak teks berlabel “Grouped text” yang ditempatkan tepat di bawahnya. Memilih salah satu bentuk akan memilih seluruh grup, mengonfirmasi bahwa **group shapes in Word** berfungsi sebagaimana mestinya.

### Hasil yang diharapkan

* Sebuah file .docx yang berisi satu paragraf.
* Di dalam paragraf, sebuah grup inline yang tampak seperti satu objek komposit.
* Persegi panjang terisi biru‑muda, dan kotak teks menampilkan “Grouped text”.

![Screenshot of the generated Word document](grouped_shapes.png){.center width=600 alt="Tangkapan layar dokumen Word kosong dengan persegi panjang yang dikelompokkan dan kotak teks yang dibuat menggunakan Aspose.Words"}

## Pertanyaan umum dan penanganan kasus tepi

### Bagaimana jika saya ingin grup mengapung daripada menjadi inline?

Ganti `WrapType.Inline` dengan `WrapType.TopBottom` (atau nilai enum `WrapType` lainnya). Grup yang mengapung dapat diposisikan secara independen dari alur paragraf, tetapi mereka kehilangan penyelarasan otomatis inline.

### Bisakah saya menambahkan lebih banyak bentuk, seperti lingkaran atau gambar?

Ya. Buat objek `Shape` tambahan dengan `ShapeType.Ellipse` atau `ShapeType.Image`, konfigurasikan propertinya, dan panggil `group.AppendChild(newShape)`. Grup akan secara otomatis memperluas batasnya untuk menampung bentuk baru jika Anda memperbarui `group.Bounds` sesuai.

### Bagaimana cara mengubah ukuran keseluruhan grup setelah menambahkan anak?

Sesuaikan `group.Bounds` setelah semua anak ditambahkan, atau hitung union dari batas anak secara programatis. Ini memastikan area hit‑test grup cocok dengan konten visual.

### Bagaimana jika folder output tidak ada?

Aspose.Words akan melempar `DirectoryNotFoundException`. Buat direktori terlebih dahulu:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Apakah ini bekerja dengan .NET Framework alih‑alih .NET Core?

Semua API yang digunakan (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) tersedia dalam versi .NET Framework dari Aspose.Words, sehingga kode yang sama dapat dijalankan tanpa perubahan.

## Tips profesional

* **Tips performa** – Gunakan satu instance `DocumentBuilder` saat menyisipkan banyak grup; membuat builder baru per grup menambah beban.
* **Konsistensi visual** – Setel `rectangle.StrokeColor` agar cocok dengan `FillColor` untuk tampilan mulus, atau setel `rectangle.LineWidth = 0` untuk menyembunyikan batas.
* **Debugging** – Panggil `doc.UpdatePageLayout()` sebelum menyimpan jika Anda memodifikasi banyak bentuk; ini memaksa Word menghitung ulang tata letak dan dapat mencegah pemotongan yang tidak terduga.

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong**, **mengelompokkan bentuk di Word**, **set shape fill color**, dan menerapkan **wrap type inline** menggunakan Aspose.Words untuk .NET. Contoh lengkap ini menunjukkan pendekatan standar untuk membangun grafik komposit yang berperilaku sebagai satu objek di Word.

Dari sini Anda dapat mengeksplorasi:

* Menambahkan bentuk tambahan seperti gambar atau diagram.
* Bereksperimen dengan nilai `WrapType` yang berbeda untuk grup mengapung.
* Mengotomatisasi pembuatan batch diagram yang dikelompokkan di banyak dokumen.

Silakan sesuaikan kode dengan skenario otomatisasi Anda sendiri, dan bagikan hasilnya di kolom komentar!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}