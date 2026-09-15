---
category: general
date: 2026-09-14
description: Pelajari cara menyisipkan tag, menambahkan bentuk, membuat grup, dan
  menyimpan dokumen sebagai DOCX menggunakan Aspose.Words dalam C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: id
lastmod: 2026-09-14
og_description: Cara menyisipkan tag, menambahkan bentuk, membuat grup, dan menyimpan
  dokumen sebagai DOCX menggunakan Aspose.Words. Ikuti panduan langkah demi langkah.
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: Cara menyisipkan tag dan membuat bentuk berkelompok dalam DOCX dengan C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to insert tag, add shapes, create a group, and save document
    as DOCX using Aspose.Words in C#.
  headline: How to insert tag and create a group shape in a DOCX
  type: TechArticle
tags:
- Aspose.Words
- C#
- DOCX manipulation
title: Cara menyisipkan tag dan membuat grup bentuk dalam DOCX
url: /id/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan tag dan membuat bentuk grup dalam DOCX

Jika Anda perlu mengetahui **cara menyisipkan tag** saat membangun tata letak yang kompleks, panduan ini menunjukkan solusi lengkap yang dapat dijalankan. Anda akan melihat cara menambahkan bentuk, membuat grup, dan akhirnya **menyimpan dokumen sebagai DOCX** dengan Aspose.Words untuk .NET.

Pembuatan dokumen sering memerlukan pencampuran tag teks dengan elemen grafis. Dalam tutorial ini Anda akan belajar secara tepat **cara menyisipkan tag**, cara **menambahkan bentuk**, cara **membuat grup**, dan cara yang benar untuk **menyimpan docx** sehingga file dapat dibuka di Word tanpa kehilangan kualitas.

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Framework 4.7+)
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)
- Pemahaman dasar tentang sintaks C#
- IDE seperti Visual Studio atau VS Code

Tidak ada pustaka tambahan yang diperlukan; seluruh contoh berjalan dengan satu referensi NuGet.

## Cara membuat grup dan menambahkan bentuk

Langkah logis pertama adalah membuat **grup** yang akan menampung beberapa bentuk. Pengelompokan menjaga bentuk tetap bersama ketika Anda memindahkan atau memutar mereka nanti.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

// 1️⃣ Create an empty document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// 2️⃣ Build a GroupShape (200 × 200 points) and set its bounds
GroupShape groupShape = new GroupShape(document, 200, 200);
groupShape.Bounds = new RectangleF(50, 50, 200, 200);

// 3️⃣ Add a rectangle shape
groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
{
    Width = 80,
    Height = 80,
    Left = 0,
    Top = 0
});

// 4️⃣ Add an ellipse shape next to the rectangle
groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
{
    Width = 80,
    Height = 80,
    Left = 100,
    Top = 0
});
```

**Mengapa ini penting:**  
`GroupShape` berfungsi seperti wadah. Ketika Anda kemudian memindahkan grup, baik persegi panjang maupun elips bergerak bersama, mempertahankan posisi relatif mereka. Ini adalah cara yang direkomendasikan untuk mengelola beberapa grafik yang termasuk dalam blok logis yang sama.

## Cara menyisipkan tag di dalam dokumen

Sekarang grup sudah siap, Anda dapat **menyisipkan tag** (StructuredDocumentTag, juga dikenal sebagai SDT) tepat setelah grup. Tag dapat menampung teks biasa, teks kaya, atau bahkan konten yang berulang.

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**Mengapa Anda harus menggunakan StructuredDocumentTag:**  
SDT menyediakan penanda semantik yang dapat dikenali Word untuk kontrol konten, binding data, atau skenario pengisian formulir. Dengan menggunakan `InsertStructuredDocumentTag` Anda secara eksplisit **menyisipkan tag** dengan cara yang tetap bertahan pada penyuntingan selanjutnya di Microsoft Word.

## Cara menyimpan docx dan memverifikasi hasilnya

Langkah akhir adalah menyimpan dokumen. Kode di bawah ini menunjukkan cara yang tepat untuk **menyimpan dokumen sebagai docx** dan di mana menemukan file output.

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Saat Anda membuka *GroupAndSDT.docx* di Word, Anda akan melihat grafik persegi‑panjang‑elips yang dikelompokkan diikuti oleh kontrol konten teks biasa berjudul **MyTag** yang berisi baris “Content inside the SDT”.

### Output yang diharapkan

- Grup berukuran 200 × 200 poin yang ditempatkan pada (50, 50) di halaman.
- Di dalam grup: persegi panjang biru di sebelah kiri dan elips di sebelah kanan (warna default).
- Langsung di bawah grup: kontrol konten berlabel **MyTag** dengan teks “Content inside the SDT”.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup semua direktif `using` yang diperlukan, penanganan error, dan komentar yang menjelaskan setiap langkah.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeWordsGroupAndTag
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document and a DocumentBuilder to work with it
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Build a GroupShape (200x200) and define its bounds
            GroupShape groupShape = new GroupShape(document, 200, 200);
            groupShape.Bounds = new RectangleF(50, 50, 200, 200);

            // Add a rectangle to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
            {
                Width = 80,
                Height = 80,
                Left = 0,
                Top = 0
            });

            // Add an ellipse to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
            {
                Width = 80,
                Height = 80,
                Left = 100,
                Top = 0
            });

            // Insert the group into the document at the current builder position
            builder.InsertNode(groupShape);

            // Insert a plain‑text StructuredDocumentTag (SDT) and write some content inside it
            builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
            builder.Writeln("Content inside the SDT");

            // Save the resulting document
            string outputPath = Path.Combine(
                Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
                "GroupAndSDT.docx");

            document.Save(outputPath);
            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

Jalankan program, buka Desktop Anda, dan klik ganda *GroupAndSDT.docx* untuk memverifikasi bahwa grup dan tag muncul seperti yang dijelaskan.

## Pertanyaan umum dan kasus tepi

| Question | Answer |
|----------|--------|
| **Apakah saya dapat menambahkan lebih dari dua bentuk ke grup?** | Ya. Panggil `groupShape.AppendChild(new Shape(...))` untuk setiap bentuk tambahan sebelum menyisipkan grup. |
| **Bagaimana jika saya membutuhkan tag rich‑text alih-alih plain‑text?** | Gunakan `StructuredDocumentTagType.RichText` dalam `InsertStructuredDocumentTag`. |
| **Bagaimana cara mengubah warna persegi panjang atau elips?** | Set properti `FillColor` pada setiap instance `Shape`, misalnya `shape.FillColor = Color.LightBlue;`. |
| **Apakah memungkinkan memutar seluruh grup?** | Set `groupShape.Rotation = 45;` (derajat) sebelum menyisipkan node. |
| **Apakah saya perlu memanggil `Dispose()` pada objek apa pun?** | Aspose.Words mengelola sebagian besar sumber daya secara internal; membuang `Document` bersifat opsional dalam aplikasi console yang berumur pendek. |

## Praktik terbaik untuk menyimpan file DOCX

- **Selalu gunakan jalur absolut** (atau jalur relatif yang terdefinisi dengan baik) saat memanggil `document.Save`. Ini menghindari error “file not found” yang dapat terjadi dengan direktori kerja yang ambigu.
- **Lebih pilih overload `Save` yang menerima stream** jika Anda perlu mengirim dokumen melalui HTTP atau menyimpannya di basis data.
- **Setel `CompatibilityOptions`** jika Anda harus menargetkan versi Word yang lebih lama (mis., Word 2003). Untuk kebanyakan skenario modern, pengaturan default sudah cukup.

## Langkah selanjutnya

Sekarang Anda tahu **cara menyisipkan tag**, cara **menambahkan bentuk**, cara **membuat grup**, dan cara **menyimpan docx**, Anda dapat mengeksplorasi skenario yang lebih maju:

- Gabungkan beberapa grup untuk membangun diagram yang kompleks.
- Gunakan `StructuredDocumentTag` untuk binding data dalam templat Word.
- Ekspor dokumen yang sama ke PDF (`document.Save("output.pdf")`) sambil mempertahankan grafik yang dikelompokkan.
- Otomatisasi pengisian formulir dengan secara programatis mengatur konten SDT (`builder.MoveToDocumentEnd(); builder.Write("New value");`).

Bereksperimenlah dengan nilai `ShapeType` yang berbeda (mis., `ShapeType.Polygon`, `ShapeType.Line`) untuk melihat bagaimana mereka berperilaku di dalam `GroupShape`. Pola yang sama berlaku untuk tabel, gambar, atau node lain apa pun yang ingin Anda jaga bersama.

---

**Ringkasan:** Tutorial ini menunjukkan **cara menyisipkan tag** di dalam bentuk yang dikelompokkan, cara **menambahkan bentuk**, cara **membuat grup**, dan metode yang benar untuk **menyimpan dokumen sebagai docx** menggunakan Aspose.Words untuk .NET. Anda kini memiliki fondasi yang kuat untuk membangun file DOCX yang kaya dan interaktif secara programatis.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara Menyimpan Markdown dari DOCX – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Cara Memulihkan DOCX – Panduan Lengkap Menggunakan Aspose.Words](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [Cara Memeriksa Tata Bahasa dalam DOCX dengan Aspose.Words – gunakan gpt-4 turbo](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}