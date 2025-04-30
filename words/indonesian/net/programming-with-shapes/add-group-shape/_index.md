---
"description": "Pelajari cara menambahkan bentuk grup ke dokumen Word menggunakan Aspose.Words untuk .NET dengan tutorial langkah demi langkah yang komprehensif ini."
"linktitle": "Tambahkan Bentuk Grup"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Tambahkan Bentuk Grup"
"url": "/id/net/programming-with-shapes/add-group-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Bentuk Grup

## Perkenalan

Membuat dokumen yang rumit dengan elemen visual yang kaya terkadang bisa menjadi tugas yang berat, terutama saat berhadapan dengan bentuk grup. Namun, jangan khawatir! Aspose.Words untuk .NET menyederhanakan proses ini, membuatnya semudah membuat pai. Dalam tutorial ini, kami akan memandu Anda melalui langkah-langkah untuk menambahkan bentuk grup ke dokumen Word Anda. Siap untuk mencobanya? Mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Aspose.Words untuk .NET: Anda dapat mengunduhnya dari [Aspose merilis halaman](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau IDE lain yang kompatibel dengan .NET.
3. Pemahaman Dasar tentang C#: Kemampuan dengan pemrograman C# merupakan nilai tambah.

## Mengimpor Ruang Nama

Untuk memulai, kita perlu mengimpor namespace yang diperlukan dalam proyek kita. Namespace ini menyediakan akses ke kelas dan metode yang diperlukan untuk memanipulasi dokumen Word dengan Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Langkah 1: Inisialisasi Dokumen

Pertama-tama, mari kita inisialisasi dokumen Word baru. Anggap saja ini seperti membuat kanvas kosong tempat kita akan menambahkan bentuk grup.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

Di Sini, `EnsureMinimum()` menambahkan serangkaian node minimal yang diperlukan untuk dokumen.

## Langkah 2: Buat Objek GroupShape

Selanjutnya, kita perlu membuat `GroupShape` objek. Objek ini akan berfungsi sebagai wadah bagi bentuk-bentuk lain, sehingga kita dapat mengelompokkannya bersama-sama.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Langkah 3: Tambahkan Bentuk ke GroupShape

Sekarang, mari tambahkan bentuk individual ke `GroupShape` wadah. Kita akan mulai dengan bentuk batas aksen lalu menambahkan bentuk tombol tindakan.

### Menambahkan Bentuk Batas Aksen

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

Potongan kode ini membuat bentuk batas aksen dengan lebar dan tinggi 100 unit dan menambahkannya ke `GroupShape`.

### Menambahkan Bentuk Tombol Tindakan

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

Di sini, kita membuat bentuk tombol tindakan, memposisikannya, dan menambahkannya ke `GroupShape`.

## Langkah 4: Tentukan Dimensi GroupShape

Untuk memastikan bentuk kita sesuai dengan grup, kita perlu mengatur dimensi `GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

Ini menentukan lebar dan tinggi `GroupShape` sebagai 200 unit dan menetapkan ukuran koordinat yang sesuai.

## Langkah 5: Masukkan GroupShape ke dalam Dokumen

Sekarang, mari kita masukkan `GroupShape` ke dalam dokumen menggunakan `DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` menyediakan cara mudah untuk menambahkan simpul, termasuk bentuk, ke dokumen.

## Langkah 6: Simpan Dokumen

Terakhir, simpan dokumen ke direktori yang Anda tentukan.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

Nah, itu dia! Dokumen Anda dengan bentuk grup sudah siap.

## Kesimpulan

Menambahkan bentuk grup ke dokumen Word Anda tidak harus menjadi proses yang rumit. Dengan Aspose.Words untuk .NET, Anda dapat membuat dan memanipulasi bentuk dengan mudah, membuat dokumen Anda lebih menarik secara visual dan fungsional. Ikuti langkah-langkah yang diuraikan dalam tutorial ini, dan Anda akan menjadi seorang profesional dalam waktu singkat!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menambahkan lebih dari dua bentuk ke GroupShape?
Ya, Anda dapat menambahkan bentuk sebanyak yang Anda butuhkan ke dalam `GroupShape`Cukup gunakan `AppendChild` metode untuk setiap bentuk.

### Apakah mungkin untuk memberi gaya pada bentuk dalam GroupShape?
Tentu saja! Setiap bentuk dapat ditata secara individual menggunakan properti yang tersedia di `Shape` kelas.

### Bagaimana cara memposisikan GroupShape dalam dokumen?
Anda dapat memposisikan `GroupShape` dengan mengaturnya `Left` Dan `Top` properti.

### Bisakah saya menambahkan teks ke bentuk dalam GroupShape?
Ya, Anda dapat menambahkan teks ke bentuk menggunakan `AppendChild` metode untuk menambahkan `Paragraph` mengandung `Run` simpul dengan teks.

### Apakah mungkin untuk mengelompokkan bentuk secara dinamis berdasarkan masukan pengguna?
Ya, Anda dapat membuat dan mengelompokkan bentuk secara dinamis berdasarkan masukan pengguna dengan menyesuaikan properti dan metode sebagaimana mestinya.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}