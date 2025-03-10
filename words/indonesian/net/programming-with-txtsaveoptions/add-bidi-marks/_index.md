---
title: Tambahkan Tanda Bidi di Dokumen Word
linktitle: Tambahkan Tanda Bidi di Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menambahkan tanda dua arah (Bidi) dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan ini. Pastikan arah teks yang tepat untuk konten multibahasa.
weight: 10
url: /id/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Tanda Bidi di Dokumen Word

## Perkenalan

Dalam dunia pemrosesan dokumen, teks dua arah (Bidi) sering kali agak sulit dikelola. Hal ini terutama berlaku saat menangani bahasa yang memiliki arah teks berbeda, seperti bahasa Arab atau Ibrani. Untungnya, Aspose.Words for .NET memudahkan penanganan skenario semacam itu. Dalam tutorial ini, kami akan membahas cara menambahkan tanda Bidi ke dokumen Word menggunakan Aspose.Words for .NET.

## Prasyarat

Sebelum kita masuk ke kode, pastikan Anda memiliki yang berikut ini:

1. Aspose.Words untuk .NET: Anda perlu menginstal Aspose.Words untuk .NET. Anda dapat mengunduhnya dari[Halaman Unduhan Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework atau .NET Core: Pastikan Anda telah menyiapkan lingkungan .NET yang kompatibel untuk menjalankan contoh tersebut.
3. Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C# dan operasi dasar di .NET.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan. Berikut cara memasukkannya ke dalam proyek Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Mari kita uraikan proses penambahan tanda Bidi dalam dokumen Word menjadi beberapa langkah yang jelas. Setiap langkah akan memandu Anda memahami kode dan tujuannya.

## Langkah 1: Siapkan Dokumen Anda

 Mulailah dengan membuat contoh baru dari`Document` kelas dan a`DocumentBuilder` untuk menambahkan konten ke dokumen.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Buat dokumen dan tambahkan konten
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Pada langkah ini, Anda menginisialisasi dokumen Word baru dan menyiapkan`DocumentBuilder` untuk memfasilitasi penyisipan konten.

## Langkah 2: Tambahkan Konten ke Dokumen Anda

Selanjutnya, tambahkan beberapa teks ke dokumen Anda. Di sini, kami akan menambahkan teks dalam berbagai bahasa untuk mengilustrasikan penanganan teks Bidi.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Di sini, pertama-tama kita tambahkan frasa bahasa Inggris standar. Kemudian, kita aktifkan format teks Bidi untuk teks berikutnya, yang ditulis dalam bahasa Ibrani dan Arab. Ini menunjukkan cara menggabungkan teks dua arah.

## Langkah 3: Konfigurasikan Opsi Penyimpanan untuk Tanda Bidi

 Untuk memastikan tanda Bidi tersimpan dengan benar dalam dokumen, Anda perlu mengonfigurasi`TxtSaveOptions` dan mengaktifkan`AddBidiMarks` pilihan.

```csharp
// Tambahkan tanda Bidi
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 Pada langkah ini, kita membuat sebuah instance dari`TxtSaveOptions` dan mengatur`AddBidiMarks`properti untuk`true`Ini memastikan tanda Bidi disertakan saat menyimpan dokumen sebagai berkas teks.

## Kesimpulan

Menambahkan tanda Bidi ke dokumen Word Anda dapat menjadi langkah penting saat menangani konten multibahasa yang mencakup bahasa dengan arah teks yang berbeda. Dengan Aspose.Words untuk .NET, proses ini mudah dan efisien. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat memastikan bahwa dokumen Anda benar-benar mewakili teks Bidi, sehingga meningkatkan keterbacaan dan akurasi.

## Pertanyaan yang Sering Diajukan

### Apa itu tanda Bidi dan mengapa itu penting?
Tanda bidi adalah karakter khusus yang digunakan untuk mengontrol arah teks dalam dokumen. Karakter ini penting untuk menampilkan bahasa yang dibaca dari kanan ke kiri, seperti bahasa Arab dan Ibrani.

### Dapatkah saya menggunakan Aspose.Words untuk .NET untuk menangani jenis masalah arah teks lainnya?
Ya, Aspose.Words untuk .NET menyediakan dukungan komprehensif untuk berbagai arah teks dan kebutuhan pemformatan, termasuk bahasa kanan-ke-kiri dan kiri-ke-kanan.

### Apakah mungkin untuk menerapkan format Bidi ke bagian tertentu saja dari suatu dokumen?
Ya, Anda dapat menerapkan format Bidi ke paragraf atau bagian tertentu dari dokumen Anda sesuai kebutuhan.

### Dalam format apa saya dapat menyimpan dokumen dengan tanda Bidi?
Dalam contoh yang diberikan, dokumen disimpan sebagai berkas teks. Namun, Aspose.Words juga mendukung penyimpanan dokumen dalam berbagai format sambil mempertahankan tanda Bidi.

### Di mana saya dapat menemukan informasi lebih lanjut tentang Aspose.Words untuk .NET?
 Anda dapat menjelajahi lebih lanjut tentang Aspose.Words untuk .NET melalui[Dokumentasi Aspose](https://reference.aspose.com/words/net/) dan mengakses[Forum Dukungan](https://forum.aspose.com/c/words/8) untuk bantuan tambahan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
