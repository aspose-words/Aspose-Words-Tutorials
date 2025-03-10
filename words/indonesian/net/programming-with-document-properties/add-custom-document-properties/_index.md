---
title: Tambahkan Properti Dokumen Kustom
linktitle: Tambahkan Properti Dokumen Kustom
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menambahkan properti dokumen kustom dalam file Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk menyempurnakan dokumen Anda dengan metadata tambahan.
weight: 10
url: /id/net/programming-with-document-properties/add-custom-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Properti Dokumen Kustom

## Perkenalan

Hai! Apakah Anda sedang mendalami dunia Aspose.Words untuk .NET dan ingin tahu cara menambahkan properti dokumen kustom ke file Word Anda? Nah, Anda telah datang ke tempat yang tepat! Properti kustom dapat sangat berguna untuk menyimpan metadata tambahan yang tidak tercakup oleh properti bawaan. Baik itu mengotorisasi dokumen, menambahkan nomor revisi, atau bahkan memasukkan tanggal tertentu, properti kustom telah mencakup semuanya. Dalam tutorial ini, kami akan memandu Anda melalui langkah-langkah untuk menambahkan properti ini dengan mudah menggunakan Aspose.Words untuk .NET. Siap untuk memulai? Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda sudah memiliki semua yang dibutuhkan:

1.  Pustaka Aspose.Words untuk .NET: Pastikan Anda memiliki pustaka Aspose.Words untuk .NET. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: IDE seperti Visual Studio.
3. Pengetahuan Dasar C#: Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang C# dan .NET.
4.  Contoh Dokumen: Siapkan contoh dokumen Word yang diberi nama`Properties.docx`, yang akan Anda modifikasi.

## Mengimpor Ruang Nama

Sebelum kita dapat memulai pengkodean, kita perlu mengimpor namespace yang diperlukan. Ini adalah langkah penting untuk memastikan bahwa kode Anda memiliki akses ke semua fungsi yang disediakan oleh Aspose.Words.

```csharp
using System;
using Aspose.Words;
```

## Langkah 1: Menyiapkan Jalur Dokumen

 Pertama-tama, kita perlu mengatur jalur ke dokumen kita. Di sinilah kita akan menentukan lokasi dokumen kita.`Properties.docx` mengajukan.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 Dalam cuplikan ini, ganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke dokumen Anda. Langkah ini penting karena memungkinkan program untuk menemukan dan membuka berkas Word Anda.

## Langkah 2: Mengakses Properti Dokumen Kustom

Selanjutnya, mari kita akses properti dokumen kustom dari dokumen Word. Di sinilah semua metadata kustom Anda akan disimpan.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

Dengan melakukan hal ini, kita dapat menangani koleksi properti kustom, yang akan kita kerjakan dalam langkah berikutnya.

## Langkah 3: Memeriksa Properti yang Ada

Sebelum menambahkan properti baru, ada baiknya untuk memeriksa apakah properti tertentu sudah ada. Ini menghindari duplikasi yang tidak perlu.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

Baris ini memeriksa apakah properti "Authorized" sudah ada. Jika sudah ada, program akan keluar dari metode lebih awal untuk mencegah penambahan properti duplikat.

## Langkah 4: Menambahkan Properti Boolean

Sekarang, mari tambahkan properti kustom pertama kita—nilai boolean untuk menunjukkan apakah dokumen tersebut diotorisasi.

```csharp
customDocumentProperties.Add("Authorized", true);
```

 Baris ini menambahkan properti kustom bernama "Diotorisasi" dengan nilai`true`Sederhana dan mudah!

## Langkah 5: Menambahkan Properti String

Berikutnya, kita akan menambahkan properti kustom lain untuk menentukan siapa yang mengesahkan dokumen tersebut.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Di sini, kami menambahkan properti bernama "Diizinkan Oleh" dengan nilai "John Smith". Jangan ragu untuk mengganti "John Smith" dengan nama lain yang Anda inginkan.

## Langkah 6: Menambahkan Properti Tanggal

Mari tambahkan properti untuk menyimpan tanggal otorisasi. Ini membantu melacak kapan dokumen tersebut diotorisasi.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 Potongan kode ini menambahkan properti bernama "Tanggal Resmi" dengan tanggal saat ini sebagai nilainya.`DateTime.Today`properti secara otomatis mengambil tanggal hari ini.

## Langkah 7: Menambahkan Nomor Revisi

Kita juga dapat menambahkan properti untuk melacak nomor revisi dokumen. Ini sangat berguna untuk kontrol versi.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Di sini, kami menambahkan properti bernama "Revisi Resmi" dan menetapkan nomor revisi dokumen saat ini.

## Langkah 8: Menambahkan Properti Numerik

Terakhir, mari tambahkan properti numerik untuk menyimpan jumlah yang diizinkan. Ini bisa berupa angka anggaran atau jumlah transaksi.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 Baris ini menambahkan properti bernama "Jumlah Resmi" dengan nilai`123.45`Sekali lagi, jangan ragu untuk menggantinya dengan angka apa pun yang sesuai dengan kebutuhan Anda.

## Kesimpulan

Nah, itu dia! Anda telah berhasil menambahkan properti dokumen kustom ke dokumen Word menggunakan Aspose.Words for .NET. Properti ini dapat sangat berguna untuk menyimpan metadata tambahan yang sesuai dengan kebutuhan Anda. Baik Anda melacak detail otorisasi, nomor revisi, atau jumlah tertentu, properti kustom menyediakan solusi yang fleksibel.

Ingat, kunci untuk menguasai Aspose.Words untuk .NET adalah latihan. Jadi, teruslah bereksperimen dengan berbagai properti dan lihat bagaimana properti tersebut dapat menyempurnakan dokumen Anda. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu properti dokumen kustom?
Properti dokumen kustom adalah metadata yang dapat Anda tambahkan ke dokumen Word untuk menyimpan informasi tambahan yang tidak tercakup oleh properti bawaan.

### Bisakah saya menambahkan properti selain string dan angka?
Ya, Anda dapat menambahkan berbagai jenis properti, termasuk boolean, tanggal, dan bahkan objek kustom.

### Bagaimana cara mengakses properti ini dalam dokumen Word?
Properti kustom dapat diakses secara terprogram menggunakan Aspose.Words atau dilihat langsung di Word melalui properti dokumen.

### Apakah mungkin untuk mengedit atau menghapus properti khusus?
Ya, Anda dapat dengan mudah mengedit atau menghapus properti kustom menggunakan metode serupa yang disediakan oleh Aspose.Words.

### Bisakah properti khusus digunakan untuk memfilter dokumen?
Tentu saja! Properti kustom sangat bagus untuk mengkategorikan dan memfilter dokumen berdasarkan metadata tertentu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
