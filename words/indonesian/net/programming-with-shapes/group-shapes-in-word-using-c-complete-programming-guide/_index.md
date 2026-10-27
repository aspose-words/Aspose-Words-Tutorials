---
category: general
date: 2026-10-13
description: Mengelompokkan bentuk di Word dengan C# – pelajari cara mengelompokkan
  bentuk dan menambahkan bentuk ke grup menggunakan Aspose.Words dalam beberapa langkah
  mudah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: id
lastmod: 2026-10-13
og_description: Kelompokkan bentuk di Word menggunakan C# dan Aspose.Words. Ikuti
  panduan ini untuk mempelajari cara mengelompokkan bentuk dan menambahkan bentuk
  ke dalam grup di dokumen Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Mengelompokkan bentuk di Word dengan C# – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Mengelompokkan bentuk di Word menggunakan C# – panduan pemrograman lengkap
url: /id/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengelompokkan bentuk di Word menggunakan C# – panduan pemrograman lengkap

Jika Anda perlu **mengelompokkan bentuk di Word** secara programatis, panduan ini menunjukkan secara tepat caranya. Pada akhir dua kalimat pertama Anda akan mengetahui kode yang diperlukan, alasan di balik setiap langkah, dan cara **menambahkan bentuk ke grup** tanpa kejutan.

Kami akan membahas semuanya mulai dari memuat file `.docx` hingga menyimpan dokumen yang telah diperbarui. Tutorial ini mengasumsikan Anda memiliki pengetahuan dasar C# dan referensi ke pustaka Aspose.Words untuk .NET. Tidak diperlukan dokumentasi eksternal—cukup salin, tempel, dan jalankan.

## Prasyarat

- .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)
- Dokumen Word (`input.docx`) yang sudah berisi setidaknya dua bentuk (mis., gambar, AutoShapes)

> **Pro tip:** Jika Anda sedang menguji, buat file Word sederhana dengan dua persegi panjang melalui UI Word. Simpan sebagai `input.docx` di folder yang Anda kontrol.

## Mengelompokkan bentuk di Word – panduan langkah demi langkah

Di bawah ini kami membagi proses menjadi lima langkah logis. Setiap langkah mencakup kode C# yang tepat, penjelasan tentang *mengapa* baris tersebut diperlukan, dan catatan singkat tentang jebakan umum.

### Langkah 1: Muat dokumen Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Mengapa:** `Document` adalah titik masuk untuk setiap manipulasi Word. Menyediakan jalur file lengkap memuat dokumen ke memori, memungkinkan kita untuk menanyakan dan memodifikasi pohon node-nya.

**Jebakan:** Menggunakan jalur relatif dapat gagal ketika direktori kerja berbeda. Gunakan jalur absolut atau `Path.Combine` dengan `AppContext.BaseDirectory`.

### Langkah 2: Ambil bentuk yang ingin Anda kelompokkan

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Mengapa:** `GetChild` menelusuri pohon dokumen dan mengembalikan node *ke‑n* dari tipe yang diminta. Menetapkan `isDeep` ke `true` mencari di seluruh dokumen, bukan hanya pada bagian saat ini.

**Kasus tepi:** Jika dokumen berisi kurang dari dua bentuk, `firstShape` atau `secondShape` akan menjadi `null` dan pengecualian akan dilempar ketika kita mencoba melakukan cast. Lindungi terhadap hal ini:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Langkah 3: Buat kontainer `GroupShape` baru

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Mengapa:** `GroupShape` berfungsi sebagai node induk yang dapat menampung beberapa objek `Shape`. Ia mewarisi dari `Shape`, sehingga dapat disisipkan di mana saja bentuk biasa diizinkan (mis., di dalam paragraf).

### Langkah 4: Tambahkan bentuk individual ke grup

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Mengapa:** `AppendChild` memindahkan bentuk dari lokasi aslinya ke dalam grup baru. Setelah pemanggilan ini, bentuk asli tidak lagi ada sebagai node independen; mereka menjadi bagian dari `groupShape`.

**Tip:** Pengelompokan secara otomatis menyesuaikan posisi relatif dari bentuk anak. Jika Anda memerlukan tata letak tertentu, atur properti `GroupShape.Bounds` *sebelum* menambahkan anak.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Langkah 5: Sisipkan bentuk grup ke dalam badan dokumen

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Mengapa:** `GroupShape` harus ditempatkan di dalam paragraf (atau sel tabel) agar dapat ditampilkan. Dengan menambahkannya ke paragraf pertama kami menjamin penempatan yang terlihat tanpa mengganggu tata letak yang ada.

### Langkah 6: Simpan dokumen yang telah dimodifikasi

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Mengapa:** `Save` menulis perubahan dalam memori kembali ke file `.docx`. Anda juga dapat menyimpan ke stream atau ke PDF dengan mengubah overload.

**Verifikasi hasil:** Buka `output.docx` di Microsoft Word. Anda harus melihat dua bentuk asli kini digabung menjadi satu objek yang dikelompokkan. Memilih grup akan menampilkan pegangan pengelompokan standar Word.

## Cara mengelompokkan bentuk secara programatis – wawasan mendalam

- **Kepemilikan node:** Saat Anda memanggil `AppendChild`, referensi `ParentNode` dari bentuk berubah secara otomatis. Ini mencegah node “yatim” yang dapat merusak dokumen.
- **Mempertahankan format:** Pengelompokan **tidak** kehilangan format bentuk apa pun (warna isi, gaya garis, dll.). Semua bentuk anak mempertahankan properti aslinya.
- **Grup bersarang:** `GroupShape` dapat berisi objek `GroupShape` lain, memungkinkan hierarki multi‑tingkat. Perlakukan grup dalam sebagai bentuk lain apa pun.

## Tambahkan bentuk ke grup dan kelola nanti

Jika Anda perlu menambahkan lebih banyak bentuk setelah grup awal dibuat, Anda dapat menggunakan kembali instance `GroupShape` yang sama:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Ketika Anda nanti perlu memisahkan grup, iterasi melalui `groupShape.GetChildNodes(NodeType.Shape, true)` dan sisipkan kembali setiap anak ke tempat yang Anda inginkan.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Mengapa ini penting:** Beberapa alur kerja memerlukan pengelompokan sementara (mis., menyelaraskan beberapa objek) diikuti dengan pemisahan grup untuk penyuntingan individual lebih lanjut.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program mandiri yang dapat Anda kompilasi dan jalankan apa adanya. Ganti `YOUR_DIRECTORY` dengan jalur folder yang sebenarnya di mesin Anda.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Output yang diharapkan:** Saat Anda membuka `output.docx`, dua bentuk asli muncul sebagai satu objek yang dikelompokkan. Memilih grup menampilkan pegangan pengelompokan Word yang familiar, memungkinkan Anda memindahkan, mengubah ukuran, atau memutar seluruh set sekaligus.

## Kesimpulan

Anda kini tahu cara **mengelompokkan bentuk di Word** menggunakan C# dan Aspose.Words, dan Anda telah melihat langkah‑langkah tepat untuk **menambahkan bentuk ke grup** serta kemudian memanipulasi atau memisahkannya. Teknik ini ideal untuk mengotomatisasi tata letak laporan, membuat diagram komposit, atau menyiapkan templat Word yang memerlukan penempatan presisi dari beberapa objek.

Selanjutnya, jelajahi topik terkait seperti **cara mengelompokkan bentuk** dengan tipe jangkar berbeda, menerapkan **format lanjutan** pada objek yang dikelompokkan, atau mengekspor hasil grup ke PDF. Bereksperimenlah dengan grup bersarang untuk membangun grafik kompleks secara programatis.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Menyisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Membuat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Menambahkan Efek Bayangan ke Bentuk Word – Panduan C# Lengkap](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}