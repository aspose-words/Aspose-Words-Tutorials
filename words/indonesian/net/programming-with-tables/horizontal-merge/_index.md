---
title: Penggabungan Horisontal
linktitle: Penggabungan Horisontal
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menggabungkan sel secara horizontal dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan tutorial langkah demi langkah terperinci ini.
weight: 10
url: /id/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Penggabungan Horisontal

## Perkenalan

Hai! Siap menyelami dunia Aspose.Words untuk .NET? Hari ini, kita akan membahas fitur yang sangat berguna: penggabungan horizontal dalam tabel. Ini mungkin terdengar agak teknis, tetapi jangan khawatir, saya siap membantu Anda. Di akhir tutorial ini, Anda akan menjadi ahli dalam menggabungkan sel dalam dokumen Word secara terprogram. Jadi, mari kita mulai!

## Prasyarat

Sebelum kita masuk ke inti permasalahan, ada beberapa hal yang perlu Anda siapkan:

1. Pustaka Aspose.Words untuk .NET: Jika Anda belum mengunduhnya, unduh pustaka Aspose.Words untuk .NET. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Pastikan Anda telah menyiapkan lingkungan pengembangan yang sesuai, seperti Visual Studio.
3. Pengetahuan Dasar C#: Pemahaman dasar tentang pemrograman C# akan bermanfaat.

Setelah Anda menyelesaikannya, Anda siap berangkat!

## Mengimpor Ruang Nama

Sebelum menyelami kode, mari pastikan kita telah mengimpor namespace yang diperlukan. Dalam proyek C# Anda, pastikan untuk menyertakan:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Baiklah, mari kita uraikan proses penggabungan sel tabel secara horizontal dalam dokumen Word menggunakan Aspose.Words untuk .NET.

## Langkah 1: Menyiapkan Dokumen Anda

 Hal pertama yang harus kita lakukan adalah membuat dokumen Word baru dan menginisialisasi`DocumentBuilder`:

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Potongan kode ini menyiapkan dokumen baru dan mempersiapkan`DocumentBuilder` untuk bertindak.

## Langkah 2: Memasukkan Sel Pertama

Selanjutnya, kita mulai dengan memasukkan sel pertama dan menandainya untuk penggabungan horizontal:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Di sini, kita memasukkan sel baru dan mengaturnya`HorizontalMerge`properti untuk`CellMerge.First`, yang menunjukkan bahwa sel ini adalah awal dari rangkaian sel yang digabungkan.

## Langkah 3: Memasukkan Sel yang Digabung

Sekarang, kita masukkan sel yang akan digabungkan dengan sel sebelumnya:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Sel ini diatur untuk bergabung dengan sel sebelumnya dengan menggunakan`CellMerge.Previous` Perhatikan bagaimana kita mengakhiri baris dengan`builder.EndRow()`.

## Langkah 4: Memasukkan Sel yang Tidak Digabungkan

Untuk mengilustrasikan perbedaannya, mari masukkan beberapa sel yang tidak digabungkan:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Di sini, kita menyisipkan dua sel tanpa penggabungan horizontal. Ini menunjukkan bagaimana sel berperilaku saat mereka bukan bagian dari rangkaian yang digabungkan.

## Langkah 5: Menyelesaikan Tabel

Terakhir, kita akhiri tabel dan simpan dokumennya:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Potongan kode ini melengkapi tabel dan menyimpan dokumen ke direktori yang ditentukan.

## Kesimpulan

Nah, itu dia! Anda baru saja menguasai seni menggabungkan sel secara horizontal dalam dokumen Word menggunakan Aspose.Words untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat membuat struktur tabel yang rumit dengan mudah. Teruslah bereksperimen dan jelajahi kemampuan Aspose.Words untuk membuat dokumen Anda sedinamis dan sefleksibel yang Anda butuhkan. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, mengedit, dan memanipulasi dokumen Word secara terprogram dalam aplikasi .NET.

### Bisakah saya menggabungkan sel secara vertikal dengan Aspose.Words untuk .NET?
 Ya, Anda juga dapat menggabungkan sel secara vertikal dengan menggunakan`CellFormat.VerticalMerge` milik.

### Apakah Aspose.Words untuk .NET gratis untuk digunakan?
 Aspose.Words untuk .NET menawarkan uji coba gratis, tetapi untuk fungsionalitas penuh, Anda perlu membeli lisensi. Anda bisa mendapatkan lisensi sementara[Di Sini](https://purchase.aspose.com/temporary-license/).

### Bagaimana saya dapat mempelajari lebih lanjut tentang Aspose.Words untuk .NET?
 Anda dapat menjelajahi dokumentasi terperinci[Di Sini](https://reference.aspose.com/words/net/).

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Words untuk .NET?
 Untuk pertanyaan atau masalah apa pun, Anda dapat mengunjungi forum dukungan Aspose[Di Sini](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
