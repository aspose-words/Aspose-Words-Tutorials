---
title: Format Garis Horizontal Dalam Dokumen Word
linktitle: Format Garis Horizontal Dalam Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyisipkan garis horizontal yang dapat disesuaikan dalam dokumen Word menggunakan Aspose.Words untuk .NET. Tingkatkan otomatisasi dokumen Anda.
weight: 10
url: /id/net/add-content-using-documentbuilder/horizontal-rule-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Format Garis Horizontal Dalam Dokumen Word

## Perkenalan

Dalam bidang pengembangan .NET, memanipulasi dan memformat dokumen Word secara terprogram dapat menjadi tugas yang berat. Untungnya, Aspose.Words untuk .NET menyediakan solusi yang tangguh, yang memungkinkan pengembang untuk mengotomatiskan pembuatan, penyuntingan, dan pengelolaan dokumen dengan mudah. Artikel ini membahas salah satu fitur penting: memasukkan garis horizontal ke dalam dokumen Word. Baik Anda pengembang berpengalaman atau baru mulai menggunakan Aspose.Words, menguasai kemampuan ini akan meningkatkan proses pembuatan dokumen Anda.

## Prasyarat

Sebelum mulai menerapkan aturan horizontal menggunakan Aspose.Words untuk .NET, pastikan Anda memiliki prasyarat berikut:

- Visual Studio: Instal Visual Studio IDE untuk pengembangan .NET.
- Aspose.Words untuk .NET: Unduh dan instal Aspose.Words untuk .NET dari[Di Sini](https://releases.aspose.com/words/net/).
- Pengetahuan Dasar C#: Keakraban dengan dasar-dasar bahasa pemrograman C#.
-  Kelas DocumentBuilder: Pemahaman tentang`DocumentBuilder` kelas di Aspose.Words untuk manipulasi dokumen.

## Mengimpor Ruang Nama

Untuk memulai, impor namespace yang diperlukan dalam proyek C# Anda:

```csharp
using Aspose.Words;
using System.Drawing;
```

Ruang nama ini menyediakan akses ke kelas Aspose.Words untuk manipulasi dokumen dan kelas .NET standar untuk menangani warna.

Mari kita uraikan proses penambahan garis horizontal dalam dokumen Word menggunakan Aspose.Words untuk .NET menjadi beberapa langkah komprehensif:

## Langkah 1: Inisialisasi DocumentBuilder dan Atur Direktori

 Pertama, inisialisasikan`DocumentBuilder` objek dan mengatur jalur direktori tempat dokumen akan disimpan.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## Langkah 2: Masukkan Penggaris Horizontal

 Gunakan`InsertHorizontalRule()` metode dari`DocumentBuilder` kelas untuk menambahkan aturan horizontal.

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## Langkah 3: Sesuaikan Format Aturan Horizontal

 Akses`HorizontalRuleFormat` properti bentuk yang disisipkan untuk menyesuaikan tampilan aturan horizontal.

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- Penyelarasan: Menentukan penyelarasan aturan horizontal (`HorizontalRuleAlignment.Center` dalam contoh ini).
- WidthPercent: Mengatur lebar garis horizontal sebagai persentase lebar halaman (70% dalam contoh ini).
- Tinggi: Menentukan tinggi penggaris horizontal dalam poin (3 poin dalam contoh ini).
- Warna: Mengatur warna aturan horizontal (`Color.Blue` dalam contoh ini).
- NoShade: Menentukan apakah aturan horizontal harus memiliki bayangan (`true` dalam contoh ini).

## Langkah 4: Simpan Dokumen

 Terakhir, simpan dokumen yang dimodifikasi menggunakan`Save` metode dari`Document` obyek.

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## Kesimpulan

Menguasai penyisipan aturan horizontal dalam dokumen Word menggunakan Aspose.Words untuk .NET akan meningkatkan kemampuan otomatisasi dokumen Anda. Dengan memanfaatkan fleksibilitas dan kekuatan Aspose.Words, pengembang dapat menyederhanakan proses pembuatan dan pemformatan dokumen secara efisien.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka yang hebat untuk bekerja dengan dokumen Word secara terprogram dalam aplikasi .NET.

### Bagaimana cara mengunduh Aspose.Words untuk .NET?
 Anda dapat mengunduh Aspose.Words untuk .NET dari[Di Sini](https://releases.aspose.com/words/net/).

### Bisakah saya menyesuaikan tampilan aturan horizontal di Aspose.Words?
Ya, Anda dapat menyesuaikan berbagai aspek seperti perataan, lebar, tinggi, warna, dan bayangan aturan horizontal menggunakan Aspose.Words.

### Apakah Aspose.Words cocok untuk pemrosesan dokumen tingkat perusahaan?
Ya, Aspose.Words digunakan secara luas di lingkungan perusahaan karena kemampuan manipulasi dokumennya yang kuat.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Words untuk .NET?
 Untuk dukungan dan keterlibatan komunitas, kunjungi[Forum Aspose.Words](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
