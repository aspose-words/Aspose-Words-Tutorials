---
category: general
date: 2026-09-14
description: Pelajari cara menyembunyikan bentuk di Word menggunakan C#—termasuk kode
  membuat dokumen Word, menyisipkan bentuk persegi panjang di Word, dan menyembunyikan
  bentuk di Word secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: id
lastmod: 2026-09-14
og_description: Cara menyembunyikan bentuk di Word menggunakan C#—panduan langkah
  demi langkah yang juga menunjukkan cara membuat kode dokumen Word dan menyisipkan
  bentuk persegi panjang di Word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Cara menyembunyikan bentuk dalam dokumen Word dengan kode C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cara menyembunyikan bentuk dalam dokumen Word dengan kode C#
url: /id/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyembunyikan bentuk di dokumen Word dengan kode C#

Jika Anda perlu **how to hide shape** dalam file Word, tutorial ini menunjukkan solusi lengkap. Anda akan melihat cara membuat dokumen Word, menyisipkan bentuk persegi panjang, menambahkan elips, dan menyembunyikan elips tersebut sehingga hanya persegi panjang yang muncul saat file dibuka.

Panduan ini mencakup semua yang Anda butuhkan—tanpa referensi eksternal, hanya kode dan penjelasannya. Pada akhir tutorial Anda akan dapat menyematkan grafik tersembunyi dalam dokumen Word apa pun yang Anda hasilkan secara programatis.

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Framework 4.7+)
- Aspose.Words untuk .NET (versi percobaan gratis atau berlisensi)  
  Instal melalui NuGet: `dotnet add package Aspose.Words`
- Pemahaman dasar tentang C# dan Visual Studio atau IDE apa pun yang Anda sukai

## Langkah 1: Siapkan proyek dan impor namespace

Mulailah aplikasi konsol baru dan tambahkan pernyataan `using` yang diperlukan. Impor ini memberi Anda akses ke kelas `Document`, `DocumentBuilder`, dan drawing yang dibutuhkan untuk memanipulasi bentuk.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Why this matters** – Mengimpor namespace yang tepat mencegah kesalahan kompilasi dan membuat API tersedia untuk pembuatan bentuk serta kontrol visibilitas.

## Langkah 2: Buat dokumen Word baru dan builder

`Document` mewakili file, sementara `DocumentBuilder` menyediakan API fluent untuk menambahkan konten. Ini adalah tempat pertama Anda menerapkan logika **how to hide shape**: Anda memerlukan konteks dokumen sebelum bentuk apa pun dapat ada.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explanation** – Objek `Document` dimulai kosong. `DocumentBuilder` ditempatkan di awal paragraf pertama, siap menyisipkan bentuk atau teks.

## Langkah 3: Sisipkan bentuk persegi panjang yang terlihat

Persegi panjang akan menjadi bentuk yang tetap terlihat saat dokumen dibuka. Anda dapat mengontrol ukuran, posisi, dan formatnya langsung melalui objek shape.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Why this step** – Menambahkan persegi panjang menunjukkan kebutuhan **insert rectangle shape word**. Menetapkan `FillColor` dan `LineColor` membuat bentuk mudah terlihat dalam dokumen akhir.

## Langkah 4: Sisipkan bentuk elips dan sembunyikan

Sekarang Anda menambahkan bentuk yang ingin disembunyikan. Properti `Hidden` memberi tahu Word untuk tidak menampilkan bentuk di UI, meskipun tetap menjadi bagian dari struktur dokumen.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explanation** – Menetapkan `Hidden = true` adalah inti dari **hide shape in word**. Word menghormati flag ini selama tampilan dan pencetakan normal, tetapi bentuk tetap dapat diakses secara programatis jika diperlukan.

## Langkah 5: Simpan dokumen

Akhirnya, tulis dokumen ke disk. Pilih folder yang Anda memiliki akses menulis, dan beri file nama yang jelas yang mencerminkan tujuan tutorial.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Result** – Membuka `ShapeVisibility.docx` di Microsoft Word menampilkan hanya persegi panjang berwarna biru muda. Elips yang disembunyikan tidak muncul, mengonfirmasi bahwa Anda telah berhasil menguasai **how to hide shape** dalam file Word.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua potongan kode memberikan Anda satu program yang dapat dijalankan:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Output yang diharapkan

- **Visual**: Saat Anda membuka `ShapeVisibility.docx`, Anda melihat persegi panjang berwarna biru muda yang terletak dekat margin kiri. Tidak ada elips yang terlihat.
- **Programmatic**: Elips yang disembunyikan tetap ada dalam XML dokumen (`<w:drawing>` element) dengan atribut `w:hidden` yang disetel, yang dapat Anda verifikasi dengan membuka file sebagai zip dan memeriksa `document.xml`.

## Pertanyaan umum dan kasus tepi

| Question | Answer |
|----------|--------|
| *Apakah saya dapat menyembunyikan beberapa bentuk?* | Ya. Set `Hidden = true` pada setiap bentuk yang ingin Anda sembunyikan. |
| *Apakah bentuk tersembunyi akan dicetak?* | Secara default Word tidak mencetak objek tersembunyi. Jika Anda memerlukan pencetakan, hapus flag `Hidden` sebelum mencetak. |
| *Apakah properti hidden didukung di versi Word yang lebih lama?* | Atribut `Hidden` merupakan bagian dari standar Office Open XML dan berfungsi di Word 2007 dan yang lebih baru. |
| *Bagaimana jika saya perlu mengubah visibilitas saat runtime?* | Ambil bentuk melalui `document.GetChildNodes(NodeType.Shape, true)` dan ubah properti `Hidden` berdasarkan logika Anda. |

## Tips profesional

- **Performance**: Jika Anda menghasilkan banyak dokumen, gunakan kembali satu instance `DocumentBuilder` alih-alih membuat yang baru untuk setiap file.
- **Version control**: Simpan file `.docx` yang dihasilkan dalam folder yang dikontrol versi; bentuk tersembunyi dapat berfungsi sebagai penanda metadata untuk pemrosesan selanjutnya.
- **Testing**: Otomatiskan tes visual cepat dengan mengonversi DOCX ke PDF menggunakan Aspose.Words (`document.Save("out.pdf")`). PDF juga akan menyembunyikan elips, mengonfirmasi bahwa flag hidden menyebar melalui konversi format.

## Kesimpulan

Anda sekarang tahu **how to hide shape** dalam dokumen Word menggunakan C#. Tutorial ini menjelaskan cara membuat dokumen, **insert rectangle shape word**, menambahkan elips, dan menerapkan flag `Hidden` untuk mencapai perilaku **hide shape in word**. Dengan kode lengkap yang dapat dijalankan, Anda dapat mengintegrasikan grafik tersembunyi ke dalam alur kerja pelaporan atau templating otomatis apa pun.

### Langkah selanjutnya

- Jelajahi properti shape lainnya seperti rotasi, bayangan, dan pembungkus teks.  
- Gabungkan shape tersembunyi dengan properti dokumen khusus untuk menyematkan data yang dapat dibaca mesin.  
- Pelajari pola **create word document code** untuk tabel, diagram, dan kontrol konten guna memperluas toolkit otomatisasi Anda.

Silakan bereksperimen dengan berbagai jenis shape dan pengaturan visibilitas—proyek otomatisasi Word Anda berikutnya hanya beberapa baris kode lagi!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayang – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}