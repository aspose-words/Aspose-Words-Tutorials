---
category: general
date: 2026-09-21
description: Buat dokumen Word kosong menggunakan Aspose.Words, atur ukuran bentuk,
  atur posisi bentuk, atur warna bentuk, dan simpan file docx dalam satu langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: id
lastmod: 2026-09-21
og_description: Buat dokumen Word kosong, atur ukuran bentuk, atur posisi bentuk,
  atur warna bentuk, dan simpan file docx dengan Aspose.Words dalam hitungan menit.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Buat dokumen Word kosong dan tambahkan bentuk berwarna – Panduan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Buat dokumen Word kosong dan tambahkan bentuk berwarna dengan Aspose.Words
url: /id/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan tambahkan bentuk berwarna dengan Aspose.Words

Jika Anda perlu **membuat dokumen Word kosong** secara programatis, panduan ini menunjukkan cara melakukannya dengan Aspose.Words. Anda akan belajar cara **mengatur ukuran bentuk**, **mengatur posisi bentuk**, **mengatur warna bentuk**, dan akhirnya **menyimpan file docx** tanpa meninggalkan IDE Anda.

Bekerja dengan file Word di C# sering berarti harus menangani panggilan OpenXML tingkat rendah, tetapi Aspose.Words menyederhanakan kompleksitasnya. Pada akhir tutorial ini Anda akan memiliki `.docx` yang berfungsi penuh yang berisi bentuk grup yang terdiri dari dua persegi panjang berwarna—sempurna untuk laporan, sertifikat, atau templat khusus.

## Prasyarat

- .NET 6.0 atau lebih baru (kode juga bekerja dengan .NET Framework 4.7+)
- Aspose.Words untuk .NET 23.9 atau lebih baru (pasang via NuGet: `Install-Package Aspose.Words`)
- Familiaritas dasar dengan C# dan Visual Studio (atau editor C# apa pun)

Tidak diperlukan file Word yang sudah ada; tutorial dimulai dengan **membuat dokumen Word kosong** dari awal.

## Buat dokumen Word kosong dengan Aspose.Words

Langkah pertama adalah menginstansiasi objek `Document`. Objek ini mewakili file Word kosong di memori.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` dimulai dalam keadaan kosong, yang persis apa yang Anda butuhkan ketika **membuat dokumen Word kosong**. `builder` nanti akan digunakan untuk menyisipkan grup bentuk pada lokasi kursor saat ini.

## Atur ukuran bentuk dan buat GroupShape

`GroupShape` berfungsi seperti kontainer yang dapat menampung banyak bentuk individual. Pertama, tentukan dimensi keseluruhan kontainer.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Di sini kita **mengatur ukuran bentuk** untuk grup itu sendiri (300 × 200). Nama properti yang sama (`Width`, `Height`) digunakan untuk setiap bentuk anak, memberi Anda kontrol detail atas setiap elemen.

## Tambahkan persegi panjang pertama dan atur warna bentuk

Sekarang tambahkan persegi panjang ke grup dan beri warna latar belakang.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

Properti `FillColor` **mengatur warna bentuk**. Menggunakan `System.Drawing.Color` memungkinkan Anda memilih nilai ARGB yang telah ditentukan atau kustom.

## Tambahkan persegi panjang kedua, atur ukurannya, posisinya, dan warnanya

Persegi panjang kedua menunjukkan cara **mengatur posisi bentuk** relatif terhadap grup dan cara mengubah warnanya.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Karena lebar grup adalah 300 poin, dua persegi panjang 120‑poin muat dengan nyaman dengan celah 30 poin. Sesuaikan `Left` dan `Top` jika Anda memerlukan tata letak yang berbeda.

## Sisipkan GroupShape ke dalam dokumen

Dengan grup yang sudah sepenuhnya dikonfigurasi, letakkan pada posisi kursor saat ini.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` menulis bentuk langsung ke dalam badan dokumen, mempertahankan **posisi bentuk** yang tepat yang Anda definisikan sebelumnya.

## Simpan file docx

Langkah akhir adalah menyimpan dokumen ke disk. Ini mendemonstrasikan operasi **save docx file**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Setelah menjalankan program, buka `GroupShape.docx` di Microsoft Word. Anda akan melihat halaman kosong dengan bentuk grup yang berisi dua persegi panjang berwarna yang ditempatkan berdampingan.

### Output yang diharapkan

- File `.docx` satu halaman.
- Halaman berisi grup bentuk yang terletak 100 pts dari margin kiri dan atas.
- Di dalam grup, persegi panjang biru muda berada di kiri, dan persegi panjang koral muda berada di kanan, masing‑masing berukuran 120 × 80 pts.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Tidak diperlukan file tambahan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Menjalankan program ini membuat dokumen persis seperti yang dijelaskan sebelumnya, memenuhi semua empat tujuan: **membuat dokumen word kosong**, **mengatur ukuran bentuk**, **mengatur posisi bentuk**, **mengatur warna bentuk**, dan **menyimpan file docx**.

## Variasi umum dan kasus tepi

| Skenario | Apa yang diubah | Mengapa penting |
|----------|----------------|-----------------|
| **Berbagai jenis bentuk** | Ganti `ShapeType.Rectangle` dengan `ShapeType.Ellipse`, `ShapeType.Triangle`, dll. | Memungkinkan Anda membuat grafik yang lebih kompleks tanpa gambar eksternal. |
| **Dimensi dinamis** | Hitung `Width` dan `Height` dari input pengguna atau file konfigurasi. | Membuat solusi dapat digunakan kembali pada banyak templat dokumen. |
| **Menyimpan sebagai PDF** | Panggil `document.Save("output.pdf", SaveFormat.Pdf);` | Jika penerima membutuhkan format yang tidak dapat diedit, PDF adalah pilihan aman. |
| **Menambahkan teks di dalam bentuk** | Buat bentuk `TextBox` dan atur `TextBox.Text`. | Berguna untuk membuat lencana berlabel atau callout. |
| **Beberapa grup pada satu halaman** | Ulangi langkah 2‑5 dengan nilai `Left`/`Top` yang berbeda. | Memungkinkan Anda membangun dasbor atau tata letak multi‑bagian. |

### Pro tip

Ketika Anda perlu menyelaraskan bentuk secara tepat, gunakan properti `ShapeBase.WrapType = WrapType.Inline` sebelum menyisipkan grup. Ini memaksa grup berperilaku seperti paragraf, mencegah aliran teks tak terduga di sekitarnya.

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong** dengan Aspose.Words, **mengatur ukuran bentuk**, **mengatur posisi bentuk**, **mengatur warna bentuk**, dan **menyimpan file docx**. Contoh lengkap menunjukkan pola bersih dan dapat digunakan kembali untuk menambahkan grafik grup ke proyek otomatisasi Word apa pun.

Dari sini Anda dapat menjelajahi:

- Menambahkan lebih banyak bentuk atau gambar ke `GroupShape` yang sama (variasi **set shape size**, **set shape color**).
- Menggunakan `ShapeBase.Rotation` untuk memutar persegi panjang untuk efek dekoratif.
- Mengekspor dokumen yang sama sebagai PDF atau HTML untuk memperluas distribusi (alternatif **save docx file**).

Silakan bereksperimen dengan warna, ukuran, dan logika tata letak yang berbeda untuk menyesuaikan kebutuhan pelaporan atau templat spesifik Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}