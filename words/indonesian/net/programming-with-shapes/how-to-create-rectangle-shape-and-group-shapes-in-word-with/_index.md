---
category: general
date: 2026-09-05
description: Buat bentuk persegi panjang dalam dokumen Word menggunakan Aspose.Words,
  kemudian pelajari cara menyisipkan elips dan mengelompokkan bentuk di Word untuk
  tata letak yang lebih kaya.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: id
lastmod: 2026-09-05
og_description: Buat bentuk persegi panjang dalam dokumen Word dengan Aspose.Words,
  kemudian lihat cara menyisipkan bentuk elips dan mengelompokkan bentuk‑bentuk di
  Word untuk tata letak yang kompleks.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Buat bentuk persegi panjang dan grupkan bentuk di Word – Panduan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cara membuat bentuk persegi panjang dan mengelompokkan bentuk di Word dengan
  Aspose.Words
url: /id/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat bentuk persegi panjang dan mengelompokkan bentuk di Word dengan Aspose.Words

Jika Anda perlu **membuat bentuk persegi panjang** dalam dokumen Word, panduan ini menunjukkan langkah‑langkah tepat dengan Aspose.Words untuk .NET. Anda juga akan melihat cara menyisipkan kata ellipse, mengelompokkan bentuk di Word, dan menyimpan hasilnya sebagai file DOCX. Solusi ini bekerja di proyek .NET 6+ apa pun dan tidak memerlukan Microsoft Office terpasang di server.

Tutorial ini mencakup semua hal mulai dari penyiapan proyek hingga penanganan jebakan tata letak umum, sehingga Anda dapat menyalin kode dan menjalankannya segera.

## Prasyarat

* .NET 6 SDK atau yang lebih baru terpasang  
* IDE yang kompatibel dengan NuGet (Visual Studio, Rider, atau VS Code)  
* Lisensi Aspose.Words untuk .NET (atau kunci evaluasi sementara)  
* Pengetahuan dasar tentang C# dan struktur dokumen Word  

Item‑item ini memungkinkan kode dikompilasi dan bentuk ditampilkan dengan benar.

## Langkah 1: Siapkan proyek dan tambahkan Aspose.Words

Buat proyek konsol baru dan tambahkan paket Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Paket ini menyediakan kelas `Document`, `DocumentBuilder`, `Shape`, dan `GroupShape` yang digunakan sepanjang tutorial ini.

## Langkah 2: Inisialisasi dokumen kosong dan builder

Objek `Document` mewakili seluruh file Word, sementara `DocumentBuilder` memungkinkan Anda menyisipkan konten secara programatis.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Membuat dokumen terlebih dahulu memastikan semua operasi bentuk berikutnya memiliki kontainer yang valid.

## Langkah 3: **Buat bentuk persegi panjang** dan atur dimensinya

Persegi panjang adalah kontainer paling umum untuk teks atau gambar. Anda menentukan ukurannya dalam poin (1 pt ≈ 1/72 inci).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Mengapa langkah ini penting: kelas `Shape` mengenkapsulasi geometri, properti isi, dan garis. Menetapkan `Width` dan `Height` sebelum penyisipan menjamin bentuk muncul dengan ukuran yang diharapkan.

## Langkah 4: **Cara menyisipkan kata ellipse** – tambahkan bentuk elips

Elips dapat digunakan untuk ikon, penanda, atau elemen dekoratif. Kode ini mencerminkan pembuatan persegi panjang, hanya `ShapeType` yang berubah.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Properti `FillColor` dan `Line.Color` menggambarkan cara menyesuaikan tampilan tanpa gambar eksternal.

## Langkah 5: **Kelompokkan bentuk di Word** – gabungkan persegi panjang dan elips

Pengelompokan memungkinkan Anda memindahkan, mengubah ukuran, atau memutar beberapa bentuk sebagai satu unit. Ini penting ketika Anda memerlukan grafik komposit (misalnya, ikon berlabel).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Saat Anda memanggil `AppendChild`, bentuk asli dihapus dari alur dokumen utama dan menjadi anak dari `GroupShape`. Grup berperilaku seperti satu bentuk, yang menyederhanakan penyesuaian tata letak selanjutnya.

## Langkah 6: Simpan dokumen

Akhirnya, tulis dokumen ke disk. Anda dapat memilih format apa pun yang didukung (`.docx`, `.pdf`, `.html`, dll.). Untuk tutorial ini kami tetap menggunakan format Word asli.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Setelah menjalankan program, buka *GroupShape.docx* di Microsoft Word. Anda akan melihat persegi panjang dan elips yang dikelompokkan bersama, ditempatkan pada koordinat yang Anda tentukan.

## Variasi umum dan kasus tepi

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Unit ukuran berbeda** | Gunakan `ConvertUtil.InchToPoint(2.5)` untuk inci atau `ConvertUtil.MillimeterToPoint(30)` untuk milimeter. | Menjaga kode tetap mudah dibaca ketika Anda bekerja dengan ukuran selain poin. |
| **Menambahkan teks di dalam persegi panjang** | Buat node `Paragraph`, atur properti `Text`‑nya, dan tambahkan ke `rectangleShape` melalui `AppendChild`. | Memungkinkan Anda memberi label pada bentuk tanpa kotak teks terpisah. |
| **Memutar grup** | Setel `groupShape.Rotation = 45;` (derajat). | Berguna untuk membuat lencana diagonal atau watermark. |
| **Menyimpan sebagai PDF** | Panggil `doc.Save("GroupShape.pdf");`. | Aspose.Words secara otomatis merasterisasi bentuk vektor untuk output PDF. |
| **Beberapa grup** | Buat instance `GroupShape` tambahan dan ulangi langkah append/insert. | Memungkinkan tata letak halaman kompleks dengan beberapa komposit independen. |

### Tips profesional

Selalu tambahkan bentuk **sebelum** Anda mengelompokkannya. Jika Anda mencoba mengelompokkan bentuk yang sudah menjadi bagian dari grup lain, Aspose.Words akan melempar `ArgumentException`. Membuat grup dalam satu metode mencegah kesalahan runtime ini.

### Hal yang perlu diwaspadai

* **Sistem koordinat** – `Left` dan `Top` diukur dari margin kiri dan atas halaman, bukan dari tepi dokumen. Salah paham tentang ini dapat menempatkan bentuk di luar halaman.  
* **Lisensi** – Tanpa lisensi yang valid, dokumen yang disimpan akan berisi watermark yang mengatakan “Aspose.Words for .NET Evaluation”. Terapkan lisensi Anda lebih awal dalam kode (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) untuk menghindarinya.

## Kode sumber lengkap (dapat dijalankan)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Menjalankan program ini menghasilkan *GroupShape.docx* dengan bentuk yang dikelompokkan persis seperti yang dijelaskan.

## Kesimpulan

Anda kini tahu cara **membuat bentuk persegi panjang**, **menyisipkan kata ellipse**, dan **mengelompokkan bentuk di Word** menggunakan Aspose.Words. Contoh lengkap ini menunjukkan alur kerja penuh—dari inisialisasi dokumen hingga menyimpan file akhir—sehingga Anda dapat mengintegrasikan penanganan bentuk ke dalam solusi pelaporan otomatis atau pembuatan dokumen apa pun.

### Selanjutnya?

* Jelajahi **aspose.words create shapes** untuk geometri yang lebih kompleks seperti `Polygon` atau `Freeform`.  
* Gabungkan bentuk yang dikelompokkan dengan **content controls** untuk membangun templat dinamis.  
* Konversi DOCX ke PDF atau HTML untuk melihat bagaimana bentuk vektor dirender di berbagai format.  

Silakan bereksperimen dengan ukuran, warna, dan rotasi yang berbeda. Ketika Anda menguasai pengelompokan bentuk, Anda dapat membuat diagram, lencana, dan elemen UI khusus yang canggih langsung di dalam dokumen Word.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Sisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}