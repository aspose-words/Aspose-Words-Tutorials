---
title: Nomor Daftar Mulai Ulang
linktitle: Nomor Daftar Mulai Ulang
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara memulai ulang nomor daftar dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan terperinci berisi 2000 kata ini mencakup semua hal yang perlu Anda ketahui, mulai dari pengaturan hingga penyesuaian tingkat lanjut.
weight: 10
url: /id/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nomor Daftar Mulai Ulang

## Perkenalan

Apakah Anda ingin menguasai seni manipulasi daftar dalam dokumen Word Anda menggunakan Aspose.Words untuk .NET? Nah, Anda berada di tempat yang tepat! Dalam tutorial ini, kita akan menyelami lebih dalam cara memulai ulang nomor daftar, fitur praktis yang akan membawa keterampilan otomatisasi dokumen Anda ke tingkat berikutnya. Kencangkan sabuk pengaman, dan mari kita mulai!

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Aspose.Words untuk .NET: Anda perlu menginstal Aspose.Words untuk .NET. Jika Anda belum menginstalnya, Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Pastikan Anda memiliki lingkungan pengembangan yang sesuai seperti Visual Studio.
3. Pengetahuan Dasar C#: Pemahaman dasar tentang C# akan membantu Anda mengikuti tutorial.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Namespace ini penting untuk mengakses fitur Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Sekarang, mari kita uraikan prosesnya menjadi beberapa langkah yang mudah diikuti. Kita akan membahas semuanya mulai dari membuat daftar hingga memulai kembali penomorannya.

## Langkah 1: Siapkan Dokumen dan Pembuatnya

Sebelum Anda dapat mulai memanipulasi daftar, Anda memerlukan dokumen dan DocumentBuilder. DocumentBuilder adalah alat yang tepat untuk menambahkan konten ke dokumen Anda.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Buat dan Sesuaikan Daftar Pertama Anda

Selanjutnya, kita akan membuat daftar berdasarkan templat dan menyesuaikan tampilannya. Dalam contoh ini, kita menggunakan format angka Arab dengan tanda kurung.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Di sini, kami mengatur warna font menjadi merah dan menyelaraskan teks ke kanan.

## Langkah 3: Tambahkan Item ke Daftar Pertama Anda

 Setelah daftar Anda siap, saatnya menambahkan beberapa item. DocumentBuilder`ListFormat.List` Properti membantu dalam menerapkan format daftar ke teks.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Langkah 4: Mulai Ulang Penomoran Daftar

Untuk menggunakan kembali daftar tersebut dan memulai kembali penomorannya, Anda perlu membuat salinan dari daftar asli. Ini memungkinkan Anda untuk mengubah daftar baru secara independen.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

Dalam contoh ini, daftar baru dimulai pada nomor 10.

## Langkah 5: Tambahkan Item ke Daftar Baru

Sama seperti sebelumnya, tambahkan item ke daftar baru Anda. Ini menunjukkan daftar dimulai ulang pada nomor yang ditentukan.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Langkah 6: Simpan Dokumen Anda

Terakhir, simpan dokumen Anda ke direktori yang Anda tentukan.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Kesimpulan

Memulai ulang nomor daftar dalam dokumen Word menggunakan Aspose.Words untuk .NET mudah dan sangat berguna. Baik Anda membuat laporan, membuat dokumen terstruktur, atau hanya membutuhkan kontrol yang lebih baik atas daftar Anda, teknik ini dapat membantu Anda.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan templat daftar lain selain NumberArabicParenthesis?

Tentu saja! Aspose.Words menawarkan berbagai templat daftar seperti poin, huruf, angka Romawi, dan banyak lagi. Anda dapat memilih salah satu yang paling sesuai dengan kebutuhan Anda.

### Bagaimana cara mengubah level daftar?

 Anda dapat mengubah level daftar dengan memodifikasi`ListLevels` properti. Misalnya,`list1.ListLevels[1]` akan merujuk pada tingkat kedua dari daftar tersebut.

### Bisakah saya memulai ulang penomoran pada nomor berapa pun?

 Ya, Anda dapat mengatur nomor awal ke nilai integer apa pun menggunakan`StartAt` properti tingkat daftar.

### Apakah mungkin untuk memiliki format yang berbeda untuk tingkat daftar yang berbeda?

Tentu saja! Setiap level daftar dapat memiliki pengaturan formatnya sendiri, seperti jenis huruf, perataan, dan gaya penomoran.

### Bagaimana jika saya ingin meneruskan penomoran dari daftar sebelumnya alih-alih memulai ulang?

Jika Anda ingin melanjutkan penomoran, Anda tidak perlu membuat salinan daftar. Cukup lanjutkan menambahkan item ke daftar asli.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
