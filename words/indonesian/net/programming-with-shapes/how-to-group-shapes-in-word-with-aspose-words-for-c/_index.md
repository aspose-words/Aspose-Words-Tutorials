---
category: general
date: 2026-09-21
description: Pelajari cara mengelompokkan bentuk di Word menggunakan Aspose.Words
  untuk C#. Panduan langkah demi langkah ini mencakup pembuatan, penempatan, dan penyimpanan
  bentuk yang dikelompokkan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: id
lastmod: 2026-09-21
og_description: Kelompokkan bentuk di Word menggunakan Aspose.Words untuk C#. Ikuti
  tutorial singkat ini untuk membuat, menempatkan, dan menyimpan bentuk yang dikelompokkan
  secara programatis.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Mengelompokkan bentuk di Word dengan Aspose.Words – panduan lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cara mengelompokkan bentuk di Word dengan Aspose.Words untuk C#
url: /id/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di Word dengan Aspose.Words untuk C#

Jika Anda perlu **mengelompokkan bentuk di Word** secara programatis, Aspose.Words mempermudahnya. Tutorial ini menunjukkan cara membuat dua bentuk persegi panjang, menempatkannya berdampingan, menggabungkannya menjadi `GroupShape`, dan menyimpan hasilnya sebagai file DOCX.

Anda akan melihat contoh lengkap yang dapat dijalankan, penjelasan mengapa setiap langkah penting, dan tips untuk menangani kasus tepi umum seperti bentuk yang saling tumpang tindih atau ukuran dinamis. Pada akhir panduan ini Anda dapat mengintegrasikan pengelompokan bentuk ke dalam proyek otomatisasi Word apa pun.

## Prasyarat

* .NET 6.0 (atau lebih baru) terinstal – Aspose.Words mendukung .NET Standard 2.0+, .NET Core, dan .NET Framework.
* Lisensi Aspose.Words for .NET yang valid (atau kunci evaluasi sementara) – perpustakaan dapat berfungsi tanpa lisensi tetapi menambahkan watermark.
* Visual Studio 2022 (atau IDE C# apa pun) untuk mengompilasi dan menjalankan contoh.

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Cara mengelompokkan bentuk di Word menggunakan Aspose.Words

Inti solusi adalah objek **`GroupShape`** yang berfungsi sebagai wadah untuk bentuk‑bentuk individual. Di bawah ini kami memecah proses menjadi langkah‑langkah yang jelas.

### Langkah 1: Buat dokumen kosong dan `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa langkah ini?*  
`Document` mewakili seluruh file DOCX, sedangkan `DocumentBuilder` menyediakan metode fluently (misalnya, `InsertShape`) yang secara otomatis menempatkan elemen baru pada posisi kursor saat ini.

### Langkah 2: Sisipkan bentuk persegi panjang pertama

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Pemanggilan `InsertShape` menambahkan bentuk ke dokumen dan mengembalikan objek `Shape` yang dapat Anda konfigurasikan lebih lanjut (warna, border, dll.). Ukuran dinyatakan dalam poin (1 pt ≈ 1/72 in).

### Langkah 3: Sisipkan persegi panjang kedua dan offset-kan

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Menetapkan `Left` memposisikan bentuk relatif terhadap margin halaman. Offset harus lebih besar dari lebar bentuk pertama (100 pt) untuk menghindari tumpang tindih; kami menggunakan 120 pt untuk memberi celah kecil.

### Langkah 4: Buat `GroupShape` yang cukup besar untuk kedua persegi panjang

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` menerima `Document` pemilik dan dimensi kontainer. Lebar kontainer harus melebihi tepi kanan bentuk yang paling jauh; jika tidak, bentuk kedua akan terpotong.

### Langkah 5: Tambahkan bentuk individual ke grup

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Menambahkan (append) memindahkan bentuk ke dalam koleksi internal grup. Setelah pemanggilan ini, bentuk tidak lagi menjadi objek independen dalam pohon dokumen—mereka menjadi bagian dari grup.

### Langkah 6: Sisipkan bentuk yang telah dikelompokkan kembali ke dalam dokumen

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` menempatkan seluruh `GroupShape` di lokasi kursor saat ini. Jika Anda membutuhkan grup di paragraf tertentu, pindahkan builder ke paragraf tersebut terlebih dahulu.

### Langkah 7: Simpan dokumen

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

File yang dihasilkan berisi dua persegi panjang yang berperilaku sebagai satu objek—Anda dapat memindahkan, mengubah ukuran, atau menghapusnya bersama-sama di Microsoft Word.

## Kode sumber lengkap

Menggabungkan semua langkah menghasilkan program yang berdiri sendiri:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Output yang diharapkan:** Membuka *GroupedShapes.docx* di Microsoft Word menampilkan dua persegi panjang berdampingan, diperlakukan sebagai satu objek yang dapat dipilih. Menyeret grup memindahkan kedua persegi panjang secara bersamaan.

## Variasi umum dan kasus tepi

| Situasi | Penyesuaian yang disarankan |
|-----------|------------------------|
| **Lebih dari dua bentuk** | Buat objek `Shape` tambahan, posisikan sesuai, dan tambahkan masing‑masing ke `GroupShape` yang sama. |
| **Ukuran dinamis** | Hitung lebar/tinggi grup berdasarkan nilai maksimum `Right` dan `Bottom` dari bentuk anak. |
| **Berbagai jenis bentuk** | `ShapeType.Ellipse`, `ShapeType.Triangle`, dll., dapat disisipkan dengan cara yang sama; kontainer grup tidak peduli dengan jenisnya. |
| **Bentuk berputar** | Setel `shape.Rotation = 45;` sebelum menambahkan; rotasi akan dipertahankan di dalam grup. |
| **Menyimpan sebagai PDF** | Panggil `doc.Save("GroupedShapes.pdf");` – grup tetap dipertahankan dalam rendering PDF. |

**Tips pro:** Setelah mengelompokkan, Anda masih dapat memodifikasi bentuk individual dengan mengakses `group.GetChildNodes(NodeType.Shape, true)`. Ini berguna ketika Anda perlu mengubah warna isi satu persegi panjang tanpa memutuskan grup.

## Cara memverifikasi pengelompokan secara programatis

Jika Anda perlu memastikan bahwa bentuk‑bentuk telah dikelompokkan dengan benar (mis., dalam unit test), periksa hierarki node dokumen:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Outputnya harus:

```
Number of groups: 1
Children in first group: 2
```

Ini mengonfirmasi bahwa **group shapes in Word** telah dibuat seperti yang diharapkan.

## Kesimpulan

Anda sekarang tahu cara **mengelompokkan bentuk di Word** dengan Aspose.Words untuk C#. Prosesnya melibatkan pembuatan bentuk individual, memposisikannya, membungkusnya dalam `GroupShape`, dan menyisipkan grup kembali ke dalam dokumen. Dengan contoh lengkap di atas Anda dapat memperluas teknik ini ke jumlah bentuk apa pun, jenis yang berbeda, atau bahkan menggabungkannya dengan kotak teks dan gambar.

Selanjutnya, jelajahi topik terkait seperti **Aspose.Words shape grouping**, **C# Word shape manipulation**, dan **DocumentBuilder insert shape** untuk skenario otomatisasi dokumen yang lebih maju. Bereksperimenlah dengan ukuran dinamis, pengelompokan bersyarat, dan mengekspor ke PDF untuk memanfaatkan sepenuhnya kekuatan Aspose.Words.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}