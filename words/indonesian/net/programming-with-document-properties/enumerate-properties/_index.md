---
title: Hitung Properti
linktitle: Hitung Properti
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menghitung properti dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah ini. Sempurna untuk pengembang dari semua tingkat keterampilan.
weight: 10
url: /id/net/programming-with-document-properties/enumerate-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hitung Properti

## Perkenalan

Ingin bekerja dengan dokumen Word secara terprogram? Aspose.Words for .NET adalah alat hebat yang dapat membantu Anda mencapai hal itu. Hari ini, saya akan memandu Anda melalui cara menghitung properti dokumen Word menggunakan Aspose.Words for .NET. Baik Anda seorang pemula atau sudah berpengalaman, panduan ini akan menguraikannya langkah demi langkah dengan cara yang mudah dipahami dan mudah dipahami.

## Prasyarat

Sebelum kita masuk ke tutorial, ada beberapa hal yang Anda perlukan untuk memulai:

-  Aspose.Words untuk .NET: Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Visual Studio direkomendasikan, tetapi Anda dapat menggunakan IDE C# apa pun.
- Pengetahuan Dasar C#: Pemahaman mendasar tentang C# akan membantu Anda mengikutinya.

Baiklah, mari kita langsung saja!

## Langkah 1: Menyiapkan Proyek Anda

Hal pertama yang terpenting, Anda perlu menyiapkan proyek Anda di Visual Studio.

1. Buat Proyek Baru: Buka Visual Studio dan buat proyek Aplikasi Konsol baru.
2. Instal Aspose.Words untuk .NET: Gunakan NuGet Package Manager untuk menginstal Aspose.Words untuk .NET. Klik kanan pada proyek Anda di Solution Explorer, pilih "Manage NuGet Packages," dan cari "Aspose.Words". Instal paket tersebut.

## Langkah 2: Impor Namespace

Untuk bekerja dengan Aspose.Words, Anda perlu mengimpor namespace yang diperlukan. Tambahkan yang berikut di bagian atas berkas Program.cs Anda:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Properties;
```

## Langkah 3: Muat Dokumen Anda

Selanjutnya, mari kita muat dokumen Word yang ingin Anda gunakan. Untuk contoh ini, kita akan menggunakan dokumen bernama "Properties.docx" yang ada di direktori proyek Anda.

1. Tentukan Jalur Dokumen: Tentukan jalur ke dokumen Anda.
2.  Memuat Dokumen: Gunakan Aspose.Words`Document` kelas untuk memuat dokumen.

Berikut kodenya:

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

## Langkah 4: Menampilkan Nama Dokumen

Setelah dokumen Anda dimuat, Anda mungkin ingin menampilkan namanya. Aspose.Words menyediakan properti untuk ini:

```csharp
Console.WriteLine("1. Document name: {0}", doc.OriginalFileName);
```

## Langkah 5: Hitung Properti Bawaan

Properti bawaan adalah properti metadata yang telah ditetapkan oleh Microsoft Word. Properti ini meliputi judul, penulis, dan lain-lain.

1.  Mengakses Properti Bawaan: Gunakan`BuiltInDocumentProperties` koleksi.
2. Ulangi Properti: Ulangi properti dan tampilkan nama dan nilainya.

Berikut kodenya:

```csharp
Console.WriteLine("2. Built-in Properties");

foreach (DocumentProperty prop in doc.BuiltInDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Langkah 6: Hitung Properti Kustom

Properti kustom adalah properti metadata yang ditentukan pengguna. Properti ini dapat berupa apa pun yang ingin Anda tambahkan ke dokumen Anda.

1.  Akses Properti Kustom: Gunakan`CustomDocumentProperties` koleksi.
2. Ulangi Properti: Ulangi properti dan tampilkan nama dan nilainya.

Berikut kodenya:

```csharp
Console.WriteLine("3. Custom Properties");

foreach (DocumentProperty prop in doc.CustomDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil menghitung properti bawaan dan kustom dokumen Word menggunakan Aspose.Words untuk .NET. Ini hanyalah sebagian kecil dari apa yang dapat Anda lakukan dengan Aspose.Words. Baik Anda mengotomatiskan pembuatan dokumen atau memanipulasi dokumen yang rumit, Aspose.Words menyediakan serangkaian fitur yang lengkap untuk memudahkan hidup Anda.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menambahkan properti baru ke dokumen?
 Ya, Anda dapat menambahkan properti kustom baru menggunakan`CustomDocumentProperties` koleksi.

### Apakah Aspose.Words gratis untuk digunakan?
 Aspose.Words menawarkan[uji coba gratis](https://releases.aspose.com/) dan berbeda[opsi pembelian](https://purchase.aspose.com/buy).

### Bagaimana cara mendapatkan dukungan untuk Aspose.Words?
 Anda bisa mendapatkan dukungan dari komunitas Aspose[Di Sini](https://forum.aspose.com/c/words/8).

### Bisakah saya menggunakan Aspose.Words dengan bahasa .NET lainnya?
Ya, Aspose.Words mendukung beberapa bahasa .NET termasuk VB.NET.

### Di mana saya dapat menemukan lebih banyak contoh?
 Lihat di sini[Dokumentasi Aspose.Words untuk .NET](https://reference.aspose.com/words/net/) untuk contoh lebih lanjut dan informasi lebih rinci.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
