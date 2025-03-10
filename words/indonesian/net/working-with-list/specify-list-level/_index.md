---
title: Tentukan Tingkat Daftar
linktitle: Tentukan Tingkat Daftar
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat daftar bertingkat dengan nomor dan poin dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah disertakan. Sempurna untuk pengembang .NET.
weight: 10
url: /id/net/working-with-list/specify-list-level/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tentukan Tingkat Daftar

## Perkenalan

Hai, rekan pembuat kode! Jika Anda pernah bergumul dengan pembuatan daftar yang dinamis dan canggih dalam dokumen Word menggunakan .NET, Anda akan dimanjakan. Hari ini, kita akan menyelami dunia Aspose.Words untuk .NET. Secara khusus, kita akan fokus pada penentuan level daftar. Anggap saja ini sebagai peningkatan level dokumen Anda, yang memungkinkan Anda membuat daftar yang profesional dan bagus dengan mudah. Di akhir panduan ini, Anda akan memiliki jalur yang jelas untuk membuat daftar bernomor dan berpoin dengan beberapa level. Siap? Mari langsung mulai!

## Prasyarat

Sebelum kita menyelami hal-hal yang lebih mendalam, mari kita pastikan kita memiliki semua yang kita butuhkan. Berikut ini daftar periksa singkatnya:

1.  Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words untuk .NET. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: IDE seperti Visual Studio akan membuat hidup Anda lebih mudah.
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
4. Pemahaman Dasar C#: Tutorial ini mengasumsikan Anda nyaman dengan pemrograman C# dasar.

Sudah dapat semuanya? Bagus! Mari kita mulai.

## Mengimpor Ruang Nama

Pertama-tama, kita perlu mengimpor namespace yang diperlukan. Buka proyek C# Anda dan tambahkan perintah berikut menggunakan perintah:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Ini menyiapkan tahap untuk bekerja dengan Aspose.Words dalam proyek Anda.

## Langkah 1: Menyiapkan Dokumen dan DocumentBuilder

 Mari kita mulai dengan membuat dokumen baru dan`DocumentBuilder` keberatan untuk bekerja dengannya.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Membuat Daftar Bernomor

 Sekarang, kita akan membuat daftar bernomor berdasarkan salah satu templat daftar Microsoft Word dan menerapkannya ke`DocumentBuilder`'paragraf saat ini.

```csharp
builder.ListFormat.List = doc.Lists.Add(ListTemplate.NumberArabicDot);
```

## Langkah 3: Menerapkan Beberapa Tingkat Daftar

Aspose.Words memungkinkan Anda menentukan hingga sembilan level untuk sebuah daftar. Mari terapkan semuanya untuk melihat cara kerjanya.

```csharp
for (int i = 0; i < 9; i++)
{
    builder.ListFormat.ListLevelNumber = i;
    builder.Writeln("Level " + i);
}
```

Dalam loop ini, kita menetapkan level daftar untuk setiap paragraf dan menulis baris teks yang menunjukkan level tersebut.

## Langkah 4: Membuat Daftar Berpoin

Selanjutnya, mari kita beralih ke topik lain dan membuat daftar berpoin. Kali ini, kita akan menggunakan templat daftar yang berbeda.

```csharp
builder.ListFormat.List = doc.Lists.Add(ListTemplate.BulletDiamonds);
```

## Langkah 5: Menerapkan Beberapa Level ke Daftar Berpoin

Sama halnya dengan daftar bernomor, kita akan menerapkan beberapa tingkatan pada daftar berpoin kita.

```csharp
for (int i = 0; i < 9; i++)
{
    builder.ListFormat.ListLevelNumber = i;
    builder.Writeln("Level " + i);
}
```

## Langkah 6: Menghentikan Pemformatan Daftar

Terakhir, mari kita lihat bagaimana kita dapat menghentikan pemformatan daftar untuk kembali ke teks normal.

```csharp
builder.ListFormat.List = null;
```

## Langkah 7: Menyimpan Dokumen

Setelah semua kerja keras itu, saatnya menyimpan dokumen kita. Mari kita simpan dengan nama yang bermakna.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.SpecifyListLevel.docx");
```

Selesai! Anda baru saja membuat dokumen dengan struktur daftar yang kompleks menggunakan Aspose.Words untuk .NET.

## Kesimpulan

Membuat daftar terstruktur dan bertingkat dalam dokumen Word dapat meningkatkan keterbacaan dan profesionalisme secara signifikan. Dengan Aspose.Words untuk .NET, Anda dapat mengotomatiskan proses ini, menghemat waktu, dan memastikan konsistensi. Kami harap panduan ini membantu Anda memahami cara menentukan tingkat daftar secara efektif. Teruslah bereksperimen dan lihat seberapa hebat alat ini untuk kebutuhan pemrosesan dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan Anda membuat, mengedit, mengonversi, dan mencetak dokumen Word secara terprogram dalam C#.

### Dapatkah saya menggunakan Aspose.Words secara gratis?
Aspose.Words menawarkan versi uji coba gratis yang dapat Anda unduh[Di Sini](https://releases.aspose.com/) Untuk versi lengkapnya, Anda dapat memeriksa opsi pembelian[Di Sini](https://purchase.aspose.com/buy).

### Berapa banyak level yang dapat saya tentukan dalam daftar menggunakan Aspose.Words?
Anda dapat menentukan hingga sembilan level dalam daftar menggunakan Aspose.Words.

### Apakah mungkin untuk mencampur daftar bernomor dan berpoin dalam satu dokumen?
Ya, Anda dapat mencampur berbagai jenis daftar dalam satu dokumen dengan mengganti templat daftar sesuai kebutuhan.

### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang Aspose.Words untuk .NET?
 Anda dapat menemukan dokumentasi terperinci[Di Sini](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
