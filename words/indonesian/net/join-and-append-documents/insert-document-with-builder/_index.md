---
title: Masukkan Dokumen Dengan Builder
linktitle: Masukkan Dokumen Dengan Builder
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menggabungkan dua dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah untuk menyisipkan dokumen dengan DocumentBuilder dan mempertahankan formatnya.
weight: 10
url: /id/net/join-and-append-documents/insert-document-with-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Dokumen Dengan Builder

## Perkenalan

Jadi, Anda punya dua dokumen Word, dan Anda ingin menggabungkannya menjadi satu. Anda mungkin berpikir, "Apakah ada cara mudah untuk melakukan ini secara terprogram?" Tentu saja! Hari ini, saya akan memandu Anda melalui proses memasukkan satu dokumen ke dokumen lain menggunakan pustaka Aspose.Words for .NET. Metode ini sangat praktis, terutama saat Anda menangani dokumen besar atau perlu mengotomatiskan prosesnya. Mari kita langsung mulai!

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Aspose.Words untuk .NET: Jika Anda belum melakukannya, Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Pastikan Anda telah menginstal Visual Studio atau IDE lain yang sesuai.
3. Pengetahuan Dasar C#: Sedikit pengetahuan tentang C# akan sangat membantu.

## Mengimpor Ruang Nama

Pertama-tama, Anda perlu mengimpor namespace yang diperlukan untuk mengakses fungsi pustaka Aspose.Words. Berikut cara melakukannya:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Sekarang setelah prasyaratnya terpenuhi, mari kita uraikan prosesnya langkah demi langkah.

## Langkah 1: Menyiapkan Direktori Dokumen Anda

Sebelum kita mulai membuat kode, Anda perlu mengatur jalur ke direktori dokumen Anda. Di sinilah dokumen sumber dan tujuan Anda disimpan.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya tempat dokumen Anda berada. Ini akan membantu program menemukan berkas Anda dengan mudah.

## Langkah 2: Memuat Dokumen Sumber dan Tujuan

Selanjutnya, kita perlu memuat dokumen yang ingin kita gunakan. Dalam contoh ini, kita memiliki dokumen sumber dan dokumen tujuan.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

 Di sini, kami menggunakan`Document` kelas dari pustaka Aspose.Words untuk memuat dokumen kita. Pastikan nama berkas sesuai dengan nama di direktori Anda.

## Langkah 3: Membuat Objek DocumentBuilder

 Itu`DocumentBuilder` class adalah alat yang hebat dalam pustaka Aspose.Words. Class memungkinkan kita untuk menavigasi dan memanipulasi dokumen.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

 Pada langkah ini, kami telah membuat`DocumentBuilder` objek untuk dokumen tujuan kita. Ini akan membantu kita memasukkan konten ke dalam dokumen.

## Langkah 4: Berpindah ke Akhir Dokumen

Kita perlu memindahkan kursor pembangun ke akhir dokumen tujuan sebelum memasukkan dokumen sumber.

```csharp
builder.MoveToDocumentEnd();
```

Ini memastikan bahwa dokumen sumber dimasukkan di akhir dokumen tujuan.

## Langkah 5: Memasukkan Hentian Halaman

Agar semuanya tetap rapi, mari tambahkan pemisah halaman sebelum memasukkan dokumen sumber. Ini akan memulai konten dokumen sumber pada halaman baru.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Hentian halaman memastikan bahwa konten dokumen sumber dimulai pada halaman baru, membuat dokumen gabungan tampak profesional.

## Langkah 6: Memasukkan Dokumen Sumber

Sekarang tibalah bagian yang menarik—memasukkan dokumen sumber ke dalam dokumen tujuan.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

 Menggunakan`InsertDocument` metode ini, kita dapat memasukkan seluruh dokumen sumber ke dalam dokumen tujuan.`ImportFormatMode.KeepSourceFormatting` memastikan bahwa format dokumen sumber dipertahankan.

## Langkah 7: Menyimpan Dokumen yang Digabung

Terakhir, mari simpan dokumen yang telah digabungkan. Ini akan menggabungkan dokumen sumber dan tujuan menjadi satu berkas.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

Dengan menyimpan dokumen, kita telah menyelesaikan proses penggabungan kedua dokumen. Dokumen baru Anda kini telah siap dan tersimpan di direktori yang ditentukan.

## Kesimpulan

Nah, itu dia! Anda telah berhasil memasukkan satu dokumen ke dokumen lain menggunakan Aspose.Words untuk .NET. Metode ini tidak hanya efisien tetapi juga mempertahankan format kedua dokumen, sehingga memastikan penggabungan yang lancar. Baik Anda mengerjakan proyek satu kali atau perlu mengotomatiskan pemrosesan dokumen, Aspose.Words untuk .NET siap membantu Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?  
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, mengedit, mengonversi, dan memanipulasi dokumen Word secara terprogram.

### Bisakah saya mempertahankan format dokumen sumber?  
 Ya, dengan menggunakan`ImportFormatMode.KeepSourceFormatting`, format dokumen sumber dipertahankan saat dimasukkan ke dokumen tujuan.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Words untuk .NET?  
 Ya, Aspose.Words untuk .NET memerlukan lisensi untuk fungsionalitas penuh. Anda bisa mendapatkannya[lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk evaluasi.

### Bisakah saya mengotomatiskan proses ini?  
Tentu saja! Metode yang dijelaskan dapat dimasukkan ke dalam aplikasi yang lebih besar untuk mengotomatiskan tugas pemrosesan dokumen.

### Di mana saya dapat menemukan lebih banyak sumber daya dan dukungan?  
 Untuk informasi lebih lanjut, Anda dapat memeriksa[dokumentasi](https://reference.aspose.com/words/net/) , atau kunjungi[forum dukungan](https://forum.aspose.com/c/words/8) untuk bantuan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
