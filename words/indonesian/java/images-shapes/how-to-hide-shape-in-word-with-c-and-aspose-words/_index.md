---
category: general
date: 2026-09-11
description: Pelajari cara menyembunyikan bentuk di Word menggunakan C#. Panduan ini
  juga menunjukkan cara menyisipkan bentuk persegi panjang dan menyisipkan bentuk
  ke dalam dokumen Word dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: id
lastmod: 2026-09-11
og_description: Cara menyembunyikan bentuk di Word menggunakan C# dan Aspose.Words.
  Ikuti tutorial langkah demi langkah untuk menyisipkan bentuk persegi panjang dan
  mengelola bentuk-bentuk dalam dokumen Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Cara menyembunyikan bentuk di Word – panduan lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Cara menyembunyikan bentuk di Word dengan C# dan Aspose.Words
url: /id/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyembunyikan bentuk di Word dengan C# dan Aspose.Words

Jika Anda perlu menyembunyikan bentuk di Word sambil mempertahankan bentuk tersebut dalam struktur dokumen, tutorial ini menunjukkan cara melakukannya secara tepat. Dengan menggunakan Aspose.Words untuk .NET Anda dapat menyisipkan bentuk persegi panjang, menyembunyikannya, dan tetap mempertahankan posisinya untuk pemrosesan selanjutnya.

Automasi Word sering memerlukan kontrol detail atas bentuk—baik Anda membuat templat, menyiapkan laporan, atau membangun layanan penyuntingan dokumen. Pada akhir panduan ini Anda akan dapat:

* Menyisipkan bentuk persegi panjang ke dalam dokumen Word (`insert rectangle shape`).
* Menyembunyikan bentuk apa pun tanpa menghapusnya (`how to hide shape in word`).
* Menyimpan hasil dan memverifikasi bahwa bentuk tersembunyi tidak muncul dalam tampilan yang dirender (`insert shape into word document`).

Contoh ini bekerja dengan Aspose.Words 24.10 atau yang lebih baru dan menargetkan .NET 6.0+, tetapi konsepnya juga berlaku untuk versi sebelumnya.

## Prasyarat

* **Aspose.Words for .NET** ≥ 24.10. Anda dapat memperoleh lisensi sementara gratis dari situs web Aspose.
* **.NET SDK** 6.0 atau yang lebih baru terpasang di mesin Anda.
* Lingkungan pengembangan seperti Visual Studio 2022, VS Code, atau Rider.
* Familiaritas dasar dengan C# dan konsep Word Open XML (opsional tetapi membantu).

## Cara menyembunyikan bentuk di Word dengan Aspose.Words

Berikut adalah program lengkap yang dapat dijalankan yang menunjukkan seluruh alur kerja—dari membuat dokumen hingga menyisipkan bentuk persegi panjang dan akhirnya menyembunyikannya.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Penjelasan setiap langkah

1. **Buat dokumen baru** – `Document` mewakili file Word dalam memori. `DocumentBuilder` menyediakan API yang mudah digunakan untuk menyisipkan konten.
2. **Sisipkan bentuk persegi panjang** – `InsertShape` membuat objek gambar bertipe `Rectangle`. Dimensi dinyatakan dalam poin (1 pt ≈ 1/72 in). Ini memenuhi persyaratan `insert rectangle shape`.
3. **Sembunyikan bentuk** – Menetapkan `Shape.Hidden = true` menandai bentuk sebagai tersembunyi dalam markup Word (`<w:hidden/>`). Bentuk tetap menjadi bagian dari pohon dokumen, sehingga Anda dapat membuka sembunyinya nanti atau merujuknya secara programatis. Ini adalah inti dari `how to hide shape in word`.
4. **Simpan file** – Dokumen ditulis ke `output.docx`. Saat dibuka di Microsoft Word, persegi panjang tidak akan terlihat, tetapi masih ada dalam XML dan dapat diperiksa dengan penampil ZIP atau Open XML SDK.

### Hasil yang diharapkan

Buka `output.docx` di Microsoft Word:

* Dokumen tampak kosong—tidak ada bentuk yang terlihat.
* Jika Anda memeriksa XML dasar (`word/document.xml`) Anda akan menemukan elemen `<w:pict>` dengan atribut `<w:hidden/>`, mengonfirmasi bahwa bentuk tersebut ada tetapi tersembunyi.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Bentuk yang tersembunyi dapat dibuat terlihat kembali dengan mengatur `Hidden = false` dan menyimpan ulang dokumen.

## Menyisipkan bentuk persegi panjang ke dalam dokumen Word

Meskipun tujuan utama adalah menyembunyikan bentuk, banyak skenario dimulai dengan menyisipkan bentuk terlebih dahulu. Metode `InsertShape` mendukung banyak nilai `ShapeType`, termasuk `Rectangle`, `Ellipse`, `Line`, dan gambar khusus.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Mengapa menggunakan persegi panjang?**  
Persegi panjang menyediakan wadah bersih yang sejajar sumbu yang dapat menampung teks, gambar, atau bentuk bersarang lainnya. Itu sering digunakan sebagai placeholder untuk konten dinamis seperti tabel atau grafik. Dengan menyisipkan persegi panjang terlebih dahulu, Anda menjaga konsistensi tata letak bahkan setelah menyembunyikannya nanti.

## Menyisipkan bentuk ke dokumen Word – praktik terbaik

Saat Anda `insert shape into word document`, pertimbangkan hal berikut:

* **Tetapkan dimensi eksplisit** – Hindari bergantung pada ukuran otomatis; tentukan lebar dan tinggi dalam poin untuk memastikan tata letak konsisten di semua platform.
* **Tentukan posisi** – Secara default bentuk diikat ke paragraf saat ini. Gunakan `builder.MoveTo` atau `builder.StartBookmark` untuk menempatkannya secara tepat.
* **Terapkan gaya lebih awal** – Warna isi, gaya garis, dan pembungkus teks memengaruhi tampilan akhir. Bahkan bentuk tersembunyi mendapat manfaat dari gaya yang tepat karena markup tetap tidak berubah.
* **Kompatibilitas versi** – Properti `Hidden` hanya tersedia mulai Aspose.Words 24.10 ke atas. Jika Anda menargetkan versi yang lebih lama, Anda dapat menambahkan atribut `<w:hidden/>` secara manual menggunakan API `Node`.

### Menambahkan atribut tersembunyi secara manual (cadangan)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Contoh lengkap end‑to‑end

Menggabungkan semuanya, berikut adalah satu program yang:

1. Menyisipkan bentuk persegi panjang.
2. Menyembunyikan bentuk.
3. Menyisipkan elips yang terlihat untuk kontras.
4. Menyimpan dokumen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Menjalankan program menghasilkan `demo_output.docx`. Saat dibuka, Anda hanya akan melihat elips coral; persegi panjang hijau ada dalam XML tetapi tersembunyi dari tampilan.

## Pertanyaan umum dan kasus tepi

**Q: Apakah menyembunyikan bentuk memengaruhi pagination?**  
A: Tidak. Bentuk yang tersembunyi diabaikan oleh mesin tata letak, sehingga tidak mengonsumsi ruang. Ini berguna untuk konten placeholder yang tidak boleh memengaruhi pemisahan halaman.

**Q: Bisakah saya menyembunyikan bentuk yang merupakan bagian dari header atau footer?**  
A: Ya. Properti `Hidden` yang sama berfungsi pada bentuk yang berada di mana saja dalam pohon dokumen, termasuk header, footer, dan bahkan di dalam tabel.

**Q: Bagaimana jika saya perlu menyembunyikan beberapa bentuk sekaligus?**  
A: Iterasi koleksi `Document.GetChildNodes(NodeType.Shape, true)` dan atur `Hidden = true` untuk setiap bentuk target.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: Apakah atribut tersembunyi dipertahankan saat mengonversi ke PDF?**  
A: Saat mengonversi ke PDF, bentuk tersembunyi secara default diabaikan, sesuai dengan perilaku render Word. Jika Anda membutuhkannya dalam PDF, Anda harus membuka sembunyinya sebelum konversi.

## Tips dan jebakan

* **Pro tip:** Atur `shape.WrapType = WrapType.None` sebelum menyembunyikan jika Anda berencana membuka kembali bentuk nanti tanpa mengganggu teks di sekitarnya.
* **Waspadai versi Aspose.Words yang lebih lama:** Properti `Hidden` melempar `NotSupportedException` sebelum 24.10. Gunakan pendekatan XML manual dalam kasus tersebut.
* **Pengujian:** Selalu buka `.docx` yang dihasilkan di Word dan gunakan “Show XML markup” (tab Developer) untuk memverifikasi bahwa atribut `<w:hidden/>` ada.

## Kesimpulan

Anda sekarang tahu cara menyembunyikan bentuk di Word menggunakan C# dan Aspose.Words, serta cara menyisipkan bentuk persegi panjang dan menyisipkan bentuk ke dokumen Word dengan kontrol penuh atas visibilitas. Dengan memanfaatkan properti `Hidden` Anda dapat mempertahankan bentuk dalam model dokumen untuk pemrosesan selanjutnya sambil menyajikan tampilan bersih kepada pengguna akhir.

Selanjutnya, jelajahi topik terkait seperti **memperbarui properti bentuk pada runtime**, **mengonversi bentuk tersembunyi menjadi gambar**, atau **menggunakan Open XML SDK untuk memanipulasi elemen tersembunyi secara langsung**. Ekstensi ini akan memperdalam

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menyisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Membuat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Membuat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}