---
category: general
date: 2026-10-04
description: Pelajari cara mengelompokkan bentuk di Word menggunakan C#. Panduan ini
  menunjukkan cara menyisipkan bentuk persegi panjang, mengelompokkan beberapa bentuk,
  dan membuat file Word kosong secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: id
lastmod: 2026-10-04
og_description: Kelompokkan bentuk di Word menggunakan C#. Ikuti panduan langkah demi
  langkah ini untuk menyisipkan bentuk persegi panjang, mengelompokkan beberapa bentuk,
  dan membuat file Word kosong dengan DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Mengelompokkan bentuk di Word dengan C# – tutorial lengkap DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Cara mengelompokkan bentuk di Word dengan C# dan DocumentBuilder
url: /id/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di Word dengan C# dan DocumentBuilder

Jika Anda perlu **mengelompokkan bentuk di Word** dari aplikasi C#, tutorial ini menunjukkan secara tepat cara melakukannya. Anda akan melihat cara *menyisipkan bentuk persegi panjang*, menggabungkan beberapa gambar menjadi satu grup, dan akhirnya **membuat file Word kosong** yang berisi objek-objek yang dikelompokkan.

Bekerja dengan bentuk merupakan kebutuhan umum saat menghasilkan laporan, faktur, atau templat khusus secara programatis. Pada akhir panduan ini Anda akan memiliki potongan kode yang dapat digunakan kembali yang dapat Anda sisipkan ke dalam proyek .NET mana pun yang merujuk pada Aspose.Words.

## Apa yang akan Anda pelajari

- Membuat dokumen Word kosong dari awal.  
- Menyisipkan bentuk persegi panjang dan elips menggunakan `DocumentBuilder`.  
- **Mengelompokkan beberapa bentuk** ke dalam `GroupShape`.  
- Gunakan **append child to group** untuk membangun hierarki.  
- Menyimpan file ke disk dan memverifikasi hasilnya.

Tidak diperlukan pengalaman sebelumnya dengan Aspose.Words, tetapi Anda sebaiknya memiliki pemahaman dasar tentang pengembangan C# dan .NET.

## Prasyarat

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 or later | Menyediakan runtime untuk kode C#. |
| Aspose.Words for .NET (latest version) | Menyediakan `Document`, `DocumentBuilder`, dan kelas shape. |
| An IDE such as Visual Studio 2022 (or VS Code) | Memudahkan kompilasi dan menjalankan contoh. |
| Write permission to a folder on your machine | Diperlukan untuk pemanggilan `doc.save`. |

Instal Aspose.Words melalui NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Mengelompokkan bentuk di Word – panduan langkah demi langkah

Berikut adalah program lengkap yang dapat dijalankan. Setiap bagian dijelaskan secara detail sehingga Anda memahami **mengapa** kode ditulis seperti ini, bukan hanya **apa** yang dilakukannya.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Mengapa setiap langkah penting

1. **Buat file Word kosong** – Memulai dengan dokumen bersih menjamin tidak ada format tersembunyi yang mengganggu penempatan bentuk.  
2. **Inisialisasi DocumentBuilder** – `DocumentBuilder` mengabstraksi manipulasi node tingkat rendah, memungkinkan Anda fokus pada tata letak.  
3. **Sisipkan bentuk individual** – Anda terlebih dahulu memerlukan objek terpisah (`insert rectangle shape` dan sebuah elips) sebelum dapat mengelompokkannya. Menyesuaikan `Left` dan `Top` memastikan mereka muncul berdampingan.  
4. **Kelompokkan beberapa bentuk** – Dengan membuat `GroupShape` dan menggunakan **append child to group**, Anda mengubah dua gambar independen menjadi satu unit logis. Memindahkan atau mengubah ukuran grup akan memengaruhi kedua anak secara bersamaan.  
5. **Simpan dokumen** – File akhir, `GroupedShapes.docx`, dapat dibuka di Microsoft Word untuk memverifikasi bahwa persegi panjang dan elips memang dikelompokkan (pilih satu, dan keduanya bergerak bersama).

### Output yang diharapkan

Buka `GroupedShapes.docx` di Microsoft Word:

- Anda akan melihat sebuah persegi panjang dan sebuah elips yang ditempatkan berdampingan.  
- Memilih salah satu bentuk menyorot keduanya, mengonfirmasi bahwa mereka berada dalam grup yang sama.  
- Grup tersebut dapat dipindahkan, diubah ukurannya, atau diformat sebagai satu objek.

![Diagram persegi panjang dan elips yang dikelompokkan di dalam dokumen Word](https://example.com/grouped-shapes.png){: .center-image alt="Diagram persegi panjang dan elips yang dikelompokkan di dalam dokumen Word"}

*Tangkapan layar ini menggambarkan bentuk yang dikelompokkan akhir.*

---

## Menyisipkan bentuk persegi panjang – menyesuaikan ukuran dan gaya

Jika Anda memerlukan persegi panjang dengan warna isi atau border tertentu, ubah objek `Shape` setelah penyisipan:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Properti ini merupakan bagian dari kelas `Shape`, dan berfungsi untuk semua tipe bentuk, tidak hanya persegi panjang. Menyesuaikan gaya sebelum Anda **append child to group** memastikan grup mewarisi properti visual yang Anda tetapkan.

---

## Mengelompokkan beberapa bentuk – menangani lebih dari dua objek

Contoh ini mengelompokkan sebuah persegi panjang dan sebuah elips, tetapi Anda dapat menambahkan sejumlah bentuk apa pun:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Tips pro:** Setelah Anda membangun grup yang kompleks, Anda dapat mengunci tata letaknya untuk mencegah perubahan tidak sengaja:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – urutan penting

Urutan pemanggilan `AppendChild` menentukan Z‑order (bentuk mana yang muncul di atas). Dalam contoh, persegi panjang ditambahkan pertama, kemudian elips, sehingga elips menutupi persegi panjang jika mereka berpotongan. Mengubah urutan semudah memanggil `RemoveChild` dan menambahkan kembali:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Membuat file Word kosong – metode pembantu yang dapat digunakan kembali

Jika aplikasi Anda sering membutuhkan dokumen baru, enkapsulasi logika pembuatan:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Anda kemudian dapat mengganti baris `new Document()` dalam program utama dengan `CreateBlankWordFile()`. Ini mendemonstrasikan konsep **create blank word file** secara dapat digunakan kembali.

---

## Kesalahan umum dan cara menghindarinya

| Masalah | Mengapa terjadi | Solusi |
|---------|----------------|--------|
| Bentuk muncul di luar halaman | Nilai default `Left`/`Top` adalah 0, yang menempatkan bentuk di margin. | Setel secara eksplisit `Left` dan `Top` setelah penyisipan. |
| Grup kehilangan format | Mengubah bentuk anak setelah ditambahkan ke grup dapat merusak tata letak grup. | Terapkan semua properti visual **sebelum** memanggil `AppendChild`. |
| File yang disimpan kosong | `DocumentBuilder` tidak pernah digunakan untuk menambahkan node, atau `doc.Save` dipanggil pada instance `Document` yang berbeda. | Pastikan Anda menyimpan `Document` yang sama dengan yang Anda buat. |
| Peringatan kompatibilitas di Word | Menggunakan fitur bentuk baru yang tidak didukung |  |

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Sisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}