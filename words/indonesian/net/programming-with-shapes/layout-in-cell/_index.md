---
title: Tata Letak Dalam Sel
linktitle: Tata Letak Dalam Sel
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengatur tata letak dalam sel menggunakan Aspose.Words untuk .NET dengan panduan lengkap ini. Sempurna bagi pengembang yang ingin menyesuaikan dokumen Word.
weight: 10
url: /id/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tata Letak Dalam Sel

## Perkenalan

Jika Anda pernah ingin menyempurnakan tata letak sel tabel dalam dokumen Word secara terprogram, Anda berada di tempat yang tepat. Hari ini, kita akan membahas cara mengatur tata letak dalam sel menggunakan Aspose.Words untuk .NET. Kami akan membahas contoh praktis, menguraikannya langkah demi langkah sehingga Anda dapat mengikutinya dengan mudah.

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words untuk .NET. Jika belum, Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Anda memerlukan lingkungan pengembangan yang disiapkan dengan .NET. Visual Studio merupakan pilihan yang tepat jika Anda mencari rekomendasi.
3. Pengetahuan Dasar C#: Meskipun saya akan menjelaskan setiap langkah, pemahaman dasar tentang C# akan membantu Anda mengikutinya dengan lebih mudah.
4.  Direktori Dokumen: Siapkan jalur direktori tempat Anda akan menyimpan dokumen Anda. Kita akan menyebutnya sebagai`YOUR DOCUMENT DIRECTORY`.

## Mengimpor Ruang Nama

Untuk memulai, pastikan Anda mengimpor namespace yang diperlukan dalam proyek Anda:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Mari kita uraikan proses ini menjadi beberapa langkah yang dapat dikelola.

## Langkah 1: Buat Dokumen Baru

 Pertama, kita akan membuat dokumen Word baru dan menginisialisasi`DocumentBuilder` objek untuk membantu kami menyusun konten kami.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Mulai Tabel dan Atur Format Baris

Kita akan mulai membuat tabel dan menentukan tinggi dan aturan tinggi untuk baris.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Langkah 3: Masukkan Sel dan Isi dengan Konten

Selanjutnya, kita melakukan perulangan untuk menyisipkan sel ke dalam tabel. Untuk setiap 7 sel, kita akan mengakhiri baris untuk membuat sel baru.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Langkah 4: Tambahkan Bentuk Tanda Air

 Sekarang, mari tambahkan tanda air ke dokumen kita. Kita akan membuat`Shape` objek dan mengatur propertinya.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Menampilkan bentuk di luar sel tabel jika akan ditempatkan ke dalam sel.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Langkah 5: Sesuaikan Tampilan Tanda Air

Kami akan menyesuaikan lebih lanjut tampilan tanda air dengan mengatur warna dan properti teksnya.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Langkah 6: Masukkan Tanda Air ke dalam Dokumen

Kita akan menemukan bagian terakhir pada dokumen dan menyisipkan tanda air pada posisi tersebut.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Langkah 7: Optimalkan Dokumen untuk Word 2010

Untuk memastikan kompatibilitas, kami akan mengoptimalkan dokumen untuk Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Langkah 8: Simpan Dokumen

Terakhir, kita akan menyimpan dokumen kita ke direktori yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil membuat dokumen Word dengan tata letak tabel yang disesuaikan dan menambahkan tanda air menggunakan Aspose.Words untuk .NET. Tutorial ini bertujuan untuk memberikan panduan langkah demi langkah yang jelas untuk membantu Anda memahami setiap bagian dari proses tersebut. Dengan keterampilan ini, kini Anda dapat membuat dokumen Word yang lebih canggih dan disesuaikan secara terprogram.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan font yang berbeda untuk teks tanda air?
 Ya, Anda dapat mengubah font dengan mengatur`watermark.TextPath.FontFamily` properti ke font yang Anda inginkan.

### Bagaimana cara menyesuaikan posisi tanda air?
 Anda dapat mengubah`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , Dan`VerticalAlignment` properti untuk menyesuaikan posisi tanda air.

### Apakah mungkin menggunakan gambar sebagai pengganti teks untuk tanda air?
 Tentu saja! Anda dapat membuat`Shape` dengan tipe`ShapeType.Image` dan mengatur gambarnya menggunakan`ImageData.SetImage` metode.

### Bisakah saya membuat tabel dengan tinggi baris yang bervariasi?
Ya, Anda dapat mengatur ketinggian yang berbeda untuk setiap baris dengan mengubah`RowFormat.Height` properti sebelum memasukkan sel ke baris tersebut.

### Bagaimana cara menghapus tanda air dari dokumen?
 Anda dapat menghapus tanda air dengan menemukannya di koleksi bentuk dokumen dan memanggil perintah`Remove` metode.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
