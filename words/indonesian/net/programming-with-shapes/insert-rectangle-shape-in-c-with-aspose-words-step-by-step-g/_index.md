---
category: general
date: 2026-08-07
description: Masukkan bentuk persegi panjang di C# menggunakan Aspose.Words dan pelajari
  cara menyembunyikan bentuk, mengatur warna isi, serta menambahkan bentuk persegi
  panjang ke dokumen Word secara efisien.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: id
lastmod: 2026-08-07
og_description: Masukkan bentuk persegi panjang dalam dokumen Word dengan C#. Pelajari
  cara menyembunyikan bentuk, mengatur warna isi, dan menambahkan bentuk persegi panjang
  menggunakan Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Menyisipkan bentuk persegi panjang di C# – tutorial lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Menyisipkan bentuk persegi panjang di C# dengan Aspose.Words – panduan langkah
  demi langkah
url: /id/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan bentuk persegi panjang di C# dengan Aspose.Words – panduan langkah‑demi‑langkah

Jika Anda perlu **menyisipkan bentuk persegi panjang** dalam dokumen Word dari C#, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan melihat cara mengatur warna isi, menyembunyikan bentuk agar tidak muncul dalam tata letak akhir, dan menyimpan file—semua dengan hanya beberapa baris kode.

Pada bagian berikut kami membahas semua yang perlu Anda ketahui: prasyarat, daftar kode lengkap, penjelasan untuk setiap langkah, dan tip untuk variasi umum seperti membuat bentuk terlihat kembali atau menggunakan warna yang berbeda. Pada akhir panduan Anda akan dapat **menambahkan bentuk persegi panjang** ke file .docx mana pun secara programatis.

## Prasyarat

* **Aspose.Words untuk .NET** (versi 23.10 atau lebih baru). Anda dapat menginstalnya melalui NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK atau yang lebih baru terpasang di mesin Anda.
* Pemahaman dasar tentang C# dan Visual Studio (atau IDE apa pun yang Anda sukai).

Tidak ada pustaka tambahan yang diperlukan—API terkait bentuk merupakan bagian dari paket inti Aspose.Words.

## Sisipkan bentuk persegi panjang dengan Aspose.Words

Inti solusi adalah program singkat yang berdiri sendiri yang membuat dokumen kosong, menyisipkan persegi panjang, memberi warna, menyembunyikannya, dan kemudian menyimpan file. Di bawah ini adalah kode sumber lengkap dengan komentar inline yang menjelaskan *alasan* di balik setiap baris.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Apa yang dilakukan setiap langkah

| Langkah | Alasan |
|------|--------|
| **Create a new document** | Menyediakan kanvas bersih; Anda juga dapat memuat .docx yang ada dengan memberikan jalur file ke `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` adalah pembantu tingkat tinggi yang memungkinkan Anda menyisipkan teks, tabel, dan bentuk tanpa harus berurusan dengan pohon node tingkat rendah. |
| **Insert rectangle shape** | Metode `InsertShape` mengembalikan objek `Shape` yang dapat Anda sesuaikan lebih lanjut (ukuran, posisi, batas, dll.). |
| **Set fill color** | Properti `FillColor` mengontrol warna interior; Anda dapat menggunakan nilai `Color` apa pun (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, dll.). |
| **Hide the shape** | `Hidden = true` memberi tahu Word untuk mengabaikan bentuk selama tata letak sambil tetap menyimpannya dalam XML dokumen. Ini adalah cara standar menyimpan objek tak terlihat. |
| **Save the document** | Menyimpan perubahan ke file .docx. File yang disimpan akan berisi bentuk persegi panjang yang disembunyikan. |

## Cara mengatur warna isi untuk sebuah bentuk

Mengubah warna isi semudah menetapkan `System.Drawing.Color` ke properti `FillColor`. Jika Anda memerlukan nuansa khusus, gunakan `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Mengapa ini penting*: Warna isi disimpan dalam XML bentuk (`<w:fill>` attribute). Ketika bentuk disembunyikan, warna tetap ada, yang dapat berguna untuk pemrosesan lanjutan (mis., mengekstrak metadata berdasarkan kode warna).

## Cara menyembunyikan bentuk dalam dokumen akhir

Flag `Hidden` adalah properti boolean pada kelas `Shape`. Menetapkannya ke `true` memastikan bentuk diabaikan oleh mesin tata letak Word.

```csharp
rectangleShape.Hidden = true;
```

**Kesalahan umum**

* **Hidden vs. Visible** – Jika Anda kemudian membutuhkan bentuk muncul, cukup setel `Hidden = false`.
* **Compatibility** – Versi Word yang lebih lama (sebelum‑2007) mungkin memperlakukan objek gambar tersembunyi secara berbeda. Aspose.Words menjaga kompatibilitas dengan menyimpan flag di elemen OOXML yang tepat.

## Cara menyisipkan bentuk secara programatis

Meskipun contoh menggunakan persegi panjang, metode `InsertShape` yang sama bekerja untuk banyak bentuk lain (elips, segitiga, garis, dll.). Argumen pertama adalah nilai enum `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tip**: Jika Anda perlu menempatkan bentuk pada lokasi tertentu di halaman, gunakan `builder.MoveTo` untuk mengatur titik sisipan sebelum memanggil `InsertShape`.

## Tambahkan bentuk persegi panjang ke dokumen yang sudah ada

Seringkali Anda akan meningkatkan sebuah templat alih-alih memulai dari awal. Ganti langkah 1 dengan:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Semua langkah berikutnya tetap sama, dan persegi panjang akan ditambahkan di mana pun kursor builder berada (biasanya di akhir dokumen secara default).

## Menangani kasus tepi dan variasi

### 1. Membuat bentuk terlihat kembali

Jika bagian selanjutnya dari alur kerja Anda perlu menampilkan persegi panjang yang tersembunyi, Anda dapat mengubah flag tersebut:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Menambahkan batas (stroke)

Bentuk tersembunyi masih dapat memiliki batas yang terlihat ketika Anda memutuskan untuk menampilkannya. Atur properti `LineColor` dan `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Memposisikan persegi panjang secara absolut

Untuk kontrol tata letak yang tepat, ubah `WrapType` bentuk menjadi `WrapType.Inline` (default) atau `WrapType.TopBottom` dan sesuaikan properti `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Menggunakan satuan ukuran yang berbeda

Aspose.Words bekerja dalam poin (1 pt = 1/72 inci). Jika Anda lebih suka sentimeter, konversikan terlebih dahulu:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Contoh lengkap yang dapat dijalankan

Di bawah ini adalah program *lengkap* yang dapat Anda salin, tempel, dan jalankan. Program ini mencakup semua direktif `using` yang diperlukan dan menggunakan jalur absolut yang harus Anda sesuaikan dengan lingkungan Anda.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Hasil yang diharapkan**: File `HiddenRectangleShape.docx` terbuka di Microsoft Word dengan *tidak ada bentuk yang terlihat*, tetapi persegi panjang tersembunyi ada dalam XML dokumen. Anda dapat memverifikasi keberadaannya dengan membuka .docx sebagai arsip zip dan memeriksa `word/document.xml` untuk elemen `<w:shape>` dengan atribut `w:fill="yellow"` dan `w:hidden="true"`.

## Kesimpulan

Anda kini tahu cara **menyisipkan bentuk persegi panjang** dalam dokumen Word menggunakan C# dan Aspose.Words, cara **mengatur warna isi**, dan cara **menyembunyikan bentuk** sehingga tetap tak terlihat dalam tata letak akhir. Pola yang sama berlaku untuk tipe bentuk lain, warna khusus, dan templat yang sudah ada. Bereksperimenlah dengan batas, posisi absolut, dan satuan ukuran yang berbeda untuk menyesuaikan bentuk dengan kebutuhan Anda secara tepat.

### Langkah selanjutnya

* Jelajahi **cara menyisipkan bentuk** di dalam tabel atau header/footer untuk watermark.
* Gabungkan **menambahkan bentuk persegi panjang** dengan kontrol konten untuk membuat placeholder dinamis.
* Tinjau API **manipulasi bentuk** Aspose.Words untuk fitur lanjutan seperti rotasi, isian gradien, dan impor SVG.

Silakan sesuaikan kode dengan proyek Anda sendiri, dan beri tahu kami di komentar tantangan terkait bentuk apa yang Anda selesaikan selanjutnya!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑demi‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat Bentuk Grup di Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}