---
category: general
date: 2026-09-11
description: Pelajari cara membuat dokumen Word, menambahkan bentuk persegi panjang,
  dan mengatur dimensi bentuk dengan Aspose.Words. Panduan C# langkah demi langkah
  untuk penentuan ukuran bentuk yang tepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: id
lastmod: 2026-09-11
og_description: Buat dokumen Word dengan Aspose.Words di C#. Panduan ini menunjukkan
  cara menambahkan bentuk persegi panjang, mengatur ukuran bentuk, dan mengelola dimensi
  bentuk secara programatis.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Buat dokumen Word dengan bentuk – tutorial Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cara membuat dokumen Word dengan bentuk menggunakan Aspose.Words di C#
url: /id/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen word dengan bentuk menggunakan Aspose.Words di C#

Jika Anda perlu **create word document** yang berisi grafik khusus, Anda dapat melakukannya sepenuhnya dengan kode. Tutorial ini memandu Anda membuat file Word, menambahkan bentuk persegi panjang, dan mengontrol setiap dimensi bentuk tersebut. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat dimasukkan ke dalam proyek .NET apa pun.

Anda akan belajar cara **add rectangle shape**, **set shape size**, dan **set shape dimensions** di dalam kontainer yang dikelompokkan. Contoh ini menggunakan Aspose.Words 13.9, tetapi konsepnya juga berlaku untuk versi yang lebih baru. Tidak diperlukan pengalaman sebelumnya dengan API menggambar Aspose—hanya pengetahuan dasar C#.

## Prasyarat

- .NET 6.0 atau yang lebih baru terinstal  
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)  
- Sebuah IDE seperti Visual Studio 2022 (editor apa pun yang mendukung C# dapat digunakan)  

Menyiapkan alat‑alat ini memungkinkan Anda menjalankan kode secara langsung tanpa konfigurasi tambahan.

## Langkah 1: Inisialisasi dokumen dan builder – dasar pembuatan dokumen word

Operasi pertama adalah membuat objek `Document` dan `DocumentBuilder`. `Document` mewakili file itu sendiri, sedangkan `DocumentBuilder` menyediakan API yang fluently untuk menyisipkan konten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:**  
Membuat dokumen di awal memberi Anda kanvas yang bersih. Kursor builder dimulai pada paragraf pertama, yang merupakan tempat kita nanti akan **create shapes in word**.

## Langkah 2: Bangun GroupShape untuk menampung beberapa grafik

`GroupShape` berfungsi sebagai kontainer; Anda dapat memindahkan, memutar, atau mengubah ukuran seluruh grup sebagai satu unit. Di sini kami mendefinisikan lebar dan tinggi kontainer dalam poin (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Mengapa ini penting:**  
Pengelompokan bentuk menyederhanakan manajemen tata letak. Jika nanti Anda perlu menambahkan lebih banyak bentuk (misalnya, lingkaran atau kotak teks), mereka akan mewarisi posisi dan skala grup.

## Langkah 3: Buat bentuk persegi panjang dan konfigurasikan dimensinya

Sekarang kami menambahkan persegi panjang yang sebenarnya. Konstruktor `Shape` memerlukan referensi dokumen dan tipe bentuk. Setelah dibuat kami secara eksplisit **set shape size** dan **set shape dimensions**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Mengapa ini penting:**  
Menentukan lebar, tinggi, kiri, dan atas memberi Anda kontrol pixel‑perfect atas bentuk. Ini penting ketika dokumen harus sesuai dengan spesifikasi desain atau formulir tercetak.

## Langkah 4: Susun grup dengan menambahkan persegi panjang

Menambahkan persegi panjang ke `GroupShape` menjadikannya node anak. Anda dapat menambahkan sebanyak mungkin anak yang diperlukan sebelum menyisipkan grup ke dalam dokumen.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tip:** Jika Anda berencana menambahkan bentuk kedua, buatlah dengan cara yang sama dan panggil `group.AppendChild(secondShape)`. Semua anak akan berbagi sistem koordinat grup.

## Langkah 5: Sisipkan bentuk yang dikelompokkan ke dalam dokumen dan simpan

Setelah grup selesai dibangun, kami menempatkannya ke dalam paragraf saat ini. Properti `CurrentParagraph` pada builder memberikan akses langsung ke pohon node yang mendasarinya.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Mengapa ini penting:**  
Menambahkan grup ke paragraf memastikan bentuk muncul inline dengan aliran teks. Menyimpan dokumen menyelesaikan operasi **create word document**.

## Variasi umum dan kasus tepi

| Scenario | Adjustment |
|----------|------------|
| **Orientasi halaman yang berbeda** | Set `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` sebelum membuat grup. |
| **Beberapa persegi panjang** | Buat objek `Shape` tambahan dan panggil `group.AppendChild(newRect)` untuk masing‑masing. |
| **Ukuran dinamis berdasarkan konten** | Hitung lebar/tinggi dari dimensi gambar atau metrik teks, lalu tetapkan ke `rectangle.Width` / `rectangle.Height`. |
| **Ekspor ke PDF** | Setelah `doc.Save`, panggil `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Kompatibilitas dengan versi Word lama** | Simpan menggunakan `SaveFormat.Doc` alih‑alih `Docx` untuk kompatibilitas Word 97‑2003. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Program ini mencakup semua direktif `using`, titik masuk `Main`, dan komentar yang menjelaskan setiap baris.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Output yang diharapkan:**  
Saat Anda membuka *GroupShape.docx*, halaman pertama menampilkan persegi panjang berbingkai abu‑abu yang ditempatkan 50 pt dari margin kiri/atas, dengan persegi panjang itu sendiri memiliki offset 10 pt di dalam grup. Dimensi tersebut cocok dengan nilai yang ditetapkan dalam kode.

## Kesimpulan

Anda sekarang tahu cara **create word document**, **add rectangle shape**, dan secara tepat **set shape size** serta **set shape dimensions** menggunakan Aspose.Words. Pendekatan bentuk‑dikelompokkan menjaga tata letak Anda tetap fleksibel dan siap untuk ekstensi di masa depan seperti grafik tambahan atau kotak teks.

Selanjutnya, jelajahi topik terkait seperti **create shapes in word** untuk lingkaran, panah, atau jalur SVG khusus, dan pelajari cara **set shape fill color** atau **apply rotation**. Bereksperimenlah dengan ukuran yang berbeda untuk melihat bagaimana Word merender poin versus sentimeter, dan integrasikan kode ke dalam pipeline pembuatan dokumen yang lebih besar.

Selamat coding, dan silakan sesuaikan pola ini untuk skenario pelaporan otomatis atau pengisian formulir apa pun yang Anda temui!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayang – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}