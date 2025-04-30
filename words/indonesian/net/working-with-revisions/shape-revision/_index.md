---
"description": "Pelajari cara menangani revisi bentuk dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan lengkap ini. Kuasai pelacakan perubahan, penyisipan bentuk, dan banyak lagi."
"linktitle": "Revisi Bentuk"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Revisi Bentuk"
"url": "/id/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Revisi Bentuk

## Perkenalan

Mengedit dokumen Word secara terprogram dapat menjadi tugas yang berat, terutama saat menangani bentuk. Baik Anda membuat laporan, mendesain templat, atau sekadar mengotomatiskan pembuatan dokumen, kemampuan untuk melacak dan mengelola revisi bentuk sangatlah penting. Aspose.Words untuk .NET menawarkan API yang canggih untuk membuat proses ini lancar dan efisien. Dalam tutorial ini, kita akan membahas secara mendalam tentang revisi bentuk dalam dokumen Word, memastikan Anda memiliki alat dan pengetahuan untuk mengelola dokumen Anda dengan mudah.

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda memiliki semua yang Anda butuhkan:

- Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words. Anda dapat [unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Anda harus menyiapkan lingkungan pengembangan, seperti Visual Studio.
- Pemahaman Dasar C#: Keakraban dengan bahasa pemrograman C# dan konsep dasar pemrograman berorientasi objek.
- Dokumen Word: Dokumen Word untuk digunakan, atau Anda dapat membuatnya selama tutorial.

## Mengimpor Ruang Nama

Pertama, mari impor namespace yang diperlukan. Namespace ini akan memberi kita akses ke kelas dan metode yang diperlukan untuk menangani dokumen dan bentuk Word.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Langkah 1: Menyiapkan Direktori Dokumen Anda

Sebelum kita mulai bekerja dengan bentuk, kita perlu menentukan jalur ke direktori dokumen kita. Di sinilah kita akan menyimpan dokumen yang telah dimodifikasi.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Membuat Dokumen Baru

Mari membuat dokumen Word baru tempat kita akan menyisipkan dan merevisi bentuk.

```csharp
Document doc = new Document();
```

## Langkah 3: Memasukkan Bentuk Inline

Kita akan mulai dengan memasukkan bentuk sebaris ke dalam dokumen kita tanpa melacak revisi. Bentuk sebaris adalah bentuk yang mengalir bersama teks.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Langkah 4: Mulai Melacak Revisi

Untuk melacak perubahan dalam dokumen, kita perlu mengaktifkan pelacakan revisi. Hal ini penting untuk mengidentifikasi modifikasi yang dilakukan pada bentuk.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Langkah 5: Memasukkan Bentuk Lain dengan Revisi

Sekarang pelacakan revisi telah diaktifkan, mari masukkan bentuk lain. Kali ini, setiap perubahan akan dilacak.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Langkah 6: Mengambil dan Memodifikasi Bentuk

Kita dapat mengambil semua bentuk dalam dokumen dan memodifikasinya sesuai kebutuhan. Di sini, kita akan mengambil bentuk dan menghapus yang pertama.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Langkah 7: Menyimpan Dokumen

Setelah melakukan perubahan, kita perlu menyimpan dokumen. Ini memastikan semua revisi dan modifikasi tersimpan.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Langkah 8: Menangani Revisi Perpindahan Bentuk

Saat bentuk dipindahkan, Aspose.Words melacaknya sebagai revisi. Ini berarti akan ada dua contoh bentuk: satu di lokasi aslinya dan satu di lokasi barunya.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil mempelajari cara menangani revisi bentuk dalam dokumen Word menggunakan Aspose.Words untuk .NET. Baik Anda mengelola templat dokumen, mengotomatiskan laporan, atau sekadar melacak perubahan, keterampilan ini sangat berharga. Dengan mengikuti panduan langkah demi langkah ini, Anda tidak hanya menguasai dasar-dasarnya tetapi juga memperoleh wawasan tentang teknik penanganan dokumen yang lebih canggih.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memodifikasi, dan mengonversi dokumen Word secara terprogram menggunakan C#.

### Bisakah saya melacak perubahan yang dibuat pada elemen lain dalam dokumen Word?
Ya, Aspose.Words untuk .NET mendukung pelacakan perubahan pada berbagai elemen, termasuk teks, tabel, dan lainnya.

### Bagaimana saya bisa mendapatkan uji coba gratis Aspose.Words untuk .NET?
Anda bisa mendapatkan uji coba gratis Aspose.Words untuk .NET [Di Sini](https://releases.aspose.com/).

### Apakah mungkin untuk menerima atau menolak revisi secara terprogram?
Ya, Aspose.Words untuk .NET menyediakan metode untuk menerima atau menolak revisi secara terprogram.

### Dapatkah saya menggunakan Aspose.Words untuk .NET dengan bahasa .NET lain selain C#?
Tentu saja! Aspose.Words untuk .NET dapat digunakan dengan bahasa .NET apa pun, termasuk VB.NET dan F#.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}