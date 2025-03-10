---
title: Gunakan Karakter Spasi Per Level Untuk Indentasi Daftar
linktitle: Gunakan Karakter Spasi Per Level Untuk Indentasi Daftar
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat daftar bertingkat dengan indentasi karakter spasi di Aspose.Words untuk .NET. Panduan langkah demi langkah untuk pemformatan dokumen yang tepat.
weight: 10
url: /id/net/programming-with-txtsaveoptions/use-space-character-per-level-for-list-indentation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gunakan Karakter Spasi Per Level Untuk Indentasi Daftar

## Perkenalan

Dalam hal pemformatan dokumen, terutama saat bekerja dengan daftar, ketepatan adalah kuncinya. Dalam skenario saat Anda perlu membuat dokumen dengan berbagai tingkat indentasi, Aspose.Words untuk .NET menawarkan alat yang hebat untuk menangani tugas ini. Salah satu fitur khusus yang dapat berguna adalah mengonfigurasi indentasi daftar dalam file teks. Panduan ini akan memandu Anda tentang cara menggunakan karakter spasi untuk indentasi daftar, memastikan dokumen Anda mempertahankan struktur dan keterbacaan yang diinginkan.

## Prasyarat

Sebelum memulai tutorial, berikut ini yang Anda perlukan:

-  Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words. Jika Anda belum memilikinya, Anda dapat mengunduhnya dari[Situs web Aspose](https://releases.aspose.com/words/net/).
- Visual Studio: Lingkungan pengembangan untuk menulis dan menguji kode Anda.
- Pemahaman Dasar C#: Keakraban dengan C# dan kerangka .NET akan membantu Anda mengikutinya dengan lancar.

## Mengimpor Ruang Nama

Untuk mulai bekerja dengan Aspose.Words, Anda perlu mengimpor namespace yang diperlukan. Berikut ini cara memasukkannya ke dalam proyek Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Mari kita uraikan proses pembuatan dokumen dengan daftar bertingkat dan menentukan karakter spasi untuk indentasi. 

## Langkah 1: Siapkan Dokumen Anda

 Pertama, Anda perlu membuat dokumen baru dan menginisialisasi`DocumentBuilder` objek. Objek ini akan memudahkan Anda menambahkan konten dan memformatnya sesuai kebutuhan.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Buat dokumen dan tambahkan konten
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Dalam cuplikan ini, ganti`"YOUR DOCUMENTS DIRECTORY"` dengan jalur sebenarnya tempat Anda ingin menyimpan dokumen Anda.

## Langkah 2: Buat Daftar dengan Beberapa Tingkat Indentasi

 Dengan`DocumentBuilder` Misalnya, Anda sekarang dapat membuat daftar dengan berbagai tingkat indentasi. Gunakan`ListFormat` properti untuk menerapkan penomoran dan membuat indentasi item daftar sebagaimana diperlukan.

```csharp
// Buat daftar dengan tiga tingkat indentasi
builder.ListFormat.ApplyNumberDefault();
builder.Write("Element 1");
builder.ListFormat.ListIndent();
builder.Write("Element 2");
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

 Pada langkah ini,`ApplyNumberDefault` mengatur format daftar, dan`ListIndent` digunakan untuk meningkatkan tingkat indentasi untuk setiap item daftar berikutnya.

## Langkah 3: Konfigurasikan Karakter Spasi untuk Indentasi

Sekarang setelah Anda menyiapkan daftar Anda, langkah berikutnya adalah mengonfigurasi bagaimana indentasi daftar ditangani saat menyimpan dokumen ke file teks. Anda akan menggunakan`TxtSaveOptions` untuk menentukan bahwa karakter spasi harus digunakan untuk indentasi.

```csharp
// Gunakan satu karakter spasi per level untuk indentasi daftar
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 3;
saveOptions.ListIndentation.Character = ' ';
```

 Di Sini,`ListIndentation.Count` menentukan jumlah karakter spasi per tingkat indentasi, dan`ListIndentation.Character` Mengatur karakter sebenarnya yang digunakan untuk indentasi.

## Langkah 4: Simpan Dokumen dengan Opsi yang Ditentukan

Terakhir, simpan dokumen Anda menggunakan opsi yang dikonfigurasi. Ini akan menerapkan pengaturan indentasi dan menyimpan berkas Anda dalam format yang diinginkan.

```csharp
// Simpan dokumen dengan opsi yang ditentukan
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
```

 Potongan kode ini menyimpan dokumen ke jalur yang ditentukan di`dataDir` dengan nama file`"WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt"`File yang disimpan akan memiliki daftar yang diformat sesuai dengan pengaturan indentasi Anda.

## Kesimpulan

Dengan mengikuti langkah-langkah ini, Anda telah berhasil membuat dokumen dengan indentasi daftar multilevel menggunakan karakter spasi untuk pemformatan. Pendekatan ini memastikan bahwa daftar Anda terstruktur dengan baik dan mudah dibaca, bahkan saat disimpan sebagai file teks. Aspose.Words untuk .NET menyediakan alat yang tangguh untuk manipulasi dokumen, dan menguasai fitur-fitur ini dapat meningkatkan alur kerja pemrosesan dokumen Anda secara signifikan.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan karakter yang berbeda untuk indentasi daftar selain spasi?
 Ya, Anda dapat menentukan karakter yang berbeda untuk indentasi daftar dengan menyetel`Character` properti di`TxtSaveOptions`.

### Bagaimana cara menerapkan poin-poin sebagai ganti angka dalam daftar?
 Menggunakan`ListFormat.ApplyBulletDefault()` alih-alih`ApplyNumberDefault()` untuk membuat daftar berpoin.

### Dapatkah saya menyesuaikan jumlah spasi untuk indentasi secara dinamis?
 Ya, Anda dapat menyesuaikan`ListIndentation.Count` properti untuk mengatur jumlah spasi berdasarkan kebutuhan Anda.

### Apakah mungkin untuk mengubah indentasi daftar setelah dokumen dibuat?
Ya, Anda dapat mengubah format daftar dan pengaturan indentasi kapan saja sebelum menyimpan dokumen.

### Format dokumen lain apa yang mendukung pengaturan indentasi daftar?
Selain file teks, pengaturan indentasi daftar dapat diterapkan ke format lain seperti DOCX, PDF, dan HTML saat menggunakan Aspose.Words.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
