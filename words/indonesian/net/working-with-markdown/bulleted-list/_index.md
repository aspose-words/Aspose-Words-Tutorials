---
"description": "Pelajari cara membuat dan menyesuaikan daftar berpoin dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah ini."
"linktitle": "Daftar Poin"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Daftar Poin"
"url": "/id/net/working-with-markdown/bulleted-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Daftar Poin

## Perkenalan

Siap untuk menyelami dunia Aspose.Words untuk .NET? Hari ini, kita akan membahas cara membuat daftar berpoin dalam dokumen Word Anda. Baik Anda sedang menyusun ide, membuat daftar item, atau sekadar menambahkan sedikit struktur ke dokumen Anda, daftar berpoin sangatlah berguna. Jadi, mari kita mulai!

## Prasyarat

Sebelum kita mulai bersenang-senang dalam coding, mari pastikan Anda memiliki semua yang dibutuhkan:

1. Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words. Jika Anda belum memilikinya, Anda dapat [unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Lingkungan pengembangan AC# seperti Visual Studio.
3. Pengetahuan Dasar C#: Pemahaman dasar tentang pemrograman C# akan membantu Anda mengikutinya.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini seperti menyiapkan panggung agar kode kita berjalan lancar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Sekarang, mari kita uraikan prosesnya menjadi beberapa langkah yang mudah dan dapat dikelola.

## Langkah 1: Buat Dokumen Baru

Baiklah, mari kita mulai dengan membuat dokumen baru. Di sinilah semua keajaiban akan terjadi.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Langkah 2: Terapkan Format Daftar Poin

Berikutnya, kita akan menerapkan format daftar poin. Format ini memberi tahu dokumen bahwa kita akan memulai daftar poin.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## Langkah 3: Sesuaikan Daftar Poin

Di sini, kita akan menyesuaikan daftar poin sesuai keinginan kita. Untuk contoh ini, kita akan menggunakan tanda hubung (-) sebagai poin.

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## Langkah 4: Tambahkan Item Daftar

Sekarang, mari tambahkan beberapa item ke daftar poin kita. Di sinilah Anda dapat berkreasi dan menambahkan konten apa pun yang Anda perlukan.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## Langkah 5: Tambahkan Sub-Item

Untuk membuat hal-hal lebih menarik, mari tambahkan beberapa sub-item di bawah "Item 2". Ini membantu dalam mengatur subpoin.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // Kembali ke level daftar utama
```

## Kesimpulan

Nah, itu dia! Anda baru saja membuat daftar berpoin dalam dokumen Word menggunakan Aspose.Words untuk .NET. Prosesnya mudah, tetapi sangat ampuh untuk mengatur dokumen Anda. Baik Anda membuat daftar sederhana atau daftar bertingkat yang rumit, Aspose.Words siap membantu Anda.

Jangan ragu untuk bereksperimen dengan berbagai gaya dan format daftar yang sesuai dengan kebutuhan Anda. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan simbol poin yang berbeda dalam daftar?
   Ya, Anda dapat menyesuaikan simbol peluru dengan mengubah `NumberFormat` milik.

### Bagaimana cara menambahkan lebih banyak tingkat indentasi?
   Gunakan `ListIndent` metode untuk menambahkan lebih banyak level dan `ListOutdent` untuk kembali ke tingkat yang lebih tinggi.

### Apakah mungkin untuk mencampur daftar poin dan nomor?
   Tentu saja! Anda dapat beralih antara format poin dan angka menggunakan `ApplyNumberDefault` Dan `ApplyBulletDefault` metode.

### Bisakah saya memberi gaya pada teks dalam item daftar?
   Ya, Anda dapat menerapkan gaya, font, dan format yang berbeda ke teks dalam item daftar menggunakan `Font` milik `DocumentBuilder`.

### Bagaimana cara membuat daftar berpoin multi-kolom?
   Anda dapat menggunakan pemformatan tabel untuk membuat daftar multikolom, yang mana setiap sel berisi daftar berpoin terpisah.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}