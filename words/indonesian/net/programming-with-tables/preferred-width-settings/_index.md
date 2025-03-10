---
title: Pengaturan Lebar Pilihan
linktitle: Pengaturan Lebar Pilihan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat tabel dengan pengaturan lebar absolut, relatif, dan otomatis di Aspose.Words untuk .NET dengan panduan langkah demi langkah ini.
weight: 10
url: /id/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pengaturan Lebar Pilihan

## Perkenalan

Tabel merupakan cara yang ampuh untuk mengatur dan menyajikan informasi dalam dokumen Word Anda. Saat bekerja dengan tabel di Aspose.Words for .NET, Anda memiliki beberapa opsi untuk mengatur lebar sel tabel guna memastikan tabel tersebut sesuai dengan tata letak dokumen Anda dengan sempurna. Panduan ini akan memandu Anda melalui proses pembuatan tabel dengan pengaturan lebar yang diinginkan menggunakan Aspose.Words for .NET, dengan fokus pada opsi ukuran absolut, relatif, dan otomatis. 

## Prasyarat

Sebelum memulai tutorial, pastikan Anda memiliki hal berikut:

1.  Aspose.Words untuk .NET: Pastikan Anda telah menginstal Aspose.Words untuk .NET di lingkungan pengembangan Anda. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).

2. Lingkungan Pengembangan .NET: Siapkan lingkungan pengembangan .NET, seperti Visual Studio.

3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membantu Anda memahami potongan kode dan contoh dengan lebih baik.

4.  Dokumentasi Aspose.Words: Lihat[Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/) untuk informasi API terperinci dan bacaan lebih lanjut.

## Mengimpor Ruang Nama

Sebelum Anda mulai membuat kode, Anda perlu mengimpor namespace yang diperlukan ke dalam proyek C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ruang nama ini menyediakan akses ke fungsionalitas inti Aspose.Words dan objek Tabel, yang memungkinkan Anda memanipulasi tabel dokumen.

Mari kita uraikan proses pembuatan tabel dengan pengaturan lebar berbeda yang disukai menjadi langkah-langkah yang jelas dan mudah dikelola.

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

Judul: Membuat Dokumen Baru dan DocumentBuilder

 Penjelasan: Mulailah dengan membuat dokumen Word baru dan`DocumentBuilder` contoh.`DocumentBuilder` kelas menyediakan cara sederhana untuk menambahkan konten ke dokumen Anda.

```csharp
// Tentukan jalur untuk menyimpan dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Buat Dokumen baru.
Document doc = new Document();

// Buat DocumentBuilder untuk Dokumen ini.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Di sini, Anda menentukan direktori tempat dokumen akan disimpan dan menginisialisasi`Document` Dan`DocumentBuilder` objek.

## Langkah 2: Masukkan Sel Tabel Pertama dengan Lebar Absolut

Masukkan sel pertama ke dalam tabel dengan lebar tetap 40 poin. Ini akan memastikan bahwa sel ini selalu mempertahankan lebar 40 poin, berapa pun ukuran tabelnya.

```csharp
// Masukkan sel berukuran absolut.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

Pada langkah ini, Anda mulai membuat tabel dan memasukkan sel dengan lebar absolut.`PreferredWidth.FromPoints(40)` metode mengatur lebar sel menjadi 40 poin, dan`Shading.BackgroundPatternColor` menerapkan warna latar belakang kuning muda.

## Langkah 3: Masukkan Sel Berukuran Relatif

Sisipkan sel lain dengan lebar 20% dari total lebar tabel. Ukuran relatif ini memastikan sel menyesuaikan secara proporsional dengan lebar tabel.

```csharp
// Masukkan sel berukuran relatif (persen).
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Lebar sel ini akan menjadi 20% dari lebar total tabel, membuatnya dapat disesuaikan dengan berbagai ukuran layar atau tata letak dokumen.

### Langkah 4: Masukkan Sel Berukuran Otomatis

Terakhir, masukkan sel yang ukurannya secara otomatis berdasarkan sisa ruang yang tersedia dalam tabel.

```csharp
// Masukkan sel berukuran otomatis.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 Itu`PreferredWidth.Auto` pengaturan ini memungkinkan sel ini mengembang atau mengecil berdasarkan ruang yang tersisa setelah sel lainnya diperhitungkan. Ini memastikan tata letak tabel terlihat seimbang dan profesional.

## Langkah 5: Selesaikan dan Simpan Dokumen

Setelah Anda memasukkan semua sel, lengkapi tabel dan simpan dokumen ke jalur yang Anda tentukan.

```csharp
// Simpan dokumen.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Langkah ini menyelesaikan tabel dan menyimpan dokumen dengan nama file "WorkingWithTables.PreferredWidthSettings.docx" di direktori yang Anda tentukan.

## Kesimpulan

Membuat tabel dengan pengaturan lebar yang diinginkan di Aspose.Words untuk .NET mudah dilakukan setelah Anda memahami berbagai opsi ukuran yang tersedia. Apakah Anda memerlukan lebar sel tetap, relatif, atau otomatis, Aspose.Words menyediakan fleksibilitas untuk menangani berbagai skenario tata letak tabel secara efisien. Dengan mengikuti langkah-langkah yang diuraikan dalam panduan ini, Anda dapat memastikan tabel Anda terstruktur dengan baik dan menarik secara visual dalam dokumen Word Anda.

## Pertanyaan yang Sering Diajukan

### Apa perbedaan antara lebar sel absolut dan relatif?
Lebar sel absolut bersifat tetap dan tidak berubah, sedangkan lebar relatif disesuaikan berdasarkan lebar total tabel.

### Dapatkah saya menggunakan persentase negatif untuk lebar relatif?
Tidak, persentase negatif tidak berlaku untuk lebar sel. Hanya persentase positif yang diizinkan.

### Bagaimana cara kerja fitur pengaturan ukuran otomatis?
Ukuran otomatis menyesuaikan lebar sel untuk mengisi ruang yang tersisa dalam tabel setelah sel lain diubah ukurannya.

### Dapatkah saya menerapkan gaya yang berbeda pada sel dengan pengaturan lebar yang berbeda?
Ya, Anda dapat menerapkan berbagai gaya dan pemformatan ke sel terlepas dari pengaturan lebarnya.

### Apa yang terjadi jika lebar total tabel kurang dari jumlah semua lebar sel?
Tabel akan secara otomatis menyesuaikan lebar sel agar sesuai dengan ruang yang tersedia, yang dapat menyebabkan beberapa sel menyusut.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
