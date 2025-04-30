---
"description": "Pelajari cara mengubah sumber budaya pembaruan bidang di Aspose.Words untuk .NET dengan panduan ini. Kontrol pemformatan tanggal berdasarkan budaya yang berbeda dengan mudah."
"linktitle": "Ubah Bidang Perbarui Budaya Sumber"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Ubah Bidang Perbarui Budaya Sumber"
"url": "/id/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ubah Bidang Perbarui Budaya Sumber

## Perkenalan

Dalam tutorial ini, kita akan menyelami dunia Aspose.Words untuk .NET dan menjelajahi cara mengubah sumber budaya pembaruan bidang. Jika Anda berurusan dengan dokumen Word yang menyertakan bidang tanggal dan Anda perlu mengontrol bagaimana tanggal-tanggal ini diformat berdasarkan budaya yang berbeda, panduan ini cocok untuk Anda. Mari kita bahas prosesnya langkah demi langkah, memastikan Anda memahami setiap konsep dan dapat menerapkannya secara efektif dalam proyek Anda.

## Prasyarat

Sebelum kita masuk ke kode, pastikan Anda memiliki yang berikut ini:

- Aspose.Words untuk .NET: Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Setiap IDE yang kompatibel dengan .NET (misalnya, Visual Studio).
- Pengetahuan Dasar C#: Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang pemrograman C#.

## Mengimpor Ruang Nama

Pertama, mari impor namespace yang diperlukan untuk proyek kita. Ini akan memastikan bahwa kita memiliki akses ke semua kelas dan metode yang diperlukan yang disediakan oleh Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Sekarang, mari kita uraikan contoh tersebut menjadi beberapa langkah untuk membantu Anda memahami cara mengubah sumber budaya pembaruan bidang di Aspose.Words untuk .NET.

## Langkah 1: Inisialisasi Dokumen

Langkah pertama adalah membuat instance baru dari `Document` kelas dan a `DocumentBuilder`Ini menjadi dasar untuk membangun dan memanipulasi dokumen Word kita.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Masukkan Kolom dengan Lokal Tertentu

Selanjutnya, kita perlu memasukkan kolom ke dalam dokumen. Untuk contoh ini, kita akan memasukkan dua kolom tanggal. Kita akan menetapkan lokal font ke Jerman (LocaleId = 1031) untuk menunjukkan bagaimana budaya memengaruhi format tanggal.

```csharp
builder.Font.LocaleId = 1031; // Jerman
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Langkah 3: Tetapkan Sumber Budaya Pembaruan Lapangan

Untuk mengontrol budaya yang digunakan saat memperbarui bidang, kami mengatur `FieldUpdateCultureSource` milik `FieldOptions` class. Properti ini menentukan apakah kultur diambil dari kode bidang atau dokumen.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Langkah 4: Jalankan Mail Merge

Sekarang kita perlu menjalankan gabungan surat untuk mengisi kolom dengan data aktual. Dalam contoh ini, kita akan mengatur kolom tanggal kedua (`Date2`) hingga 1 Januari 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Langkah 5: Simpan Dokumen

Terakhir, kami menyimpan dokumen ke direktori yang ditentukan. Langkah ini melengkapi proses perubahan sumber kultur pembaruan lapangan.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil mengubah sumber budaya pembaruan bidang di Aspose.Words untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat memastikan bahwa dokumen Word Anda menampilkan tanggal dan nilai bidang lainnya sesuai dengan pengaturan budaya yang ditentukan. Ini dapat sangat berguna saat membuat dokumen untuk audiens internasional.

## Pertanyaan yang Sering Diajukan

### Apa tujuan pengaturan `LocaleId`....
Itu `LocaleId` menentukan pengaturan budaya untuk teks, yang memengaruhi bagaimana tanggal dan data sensitif lokal lainnya diformat.

### Bisakah saya menggunakan bahasa lain selain bahasa Jerman?
Ya, Anda dapat mengaturnya `LocaleId` ke pengenal lokal yang valid. Misalnya, 1033 untuk Bahasa Inggris (Amerika Serikat).

### Apa yang terjadi jika saya tidak mengatur `FieldUpdateCultureSource` milik?
Jika properti ini tidak disetel, pengaturan budaya default dokumen akan digunakan saat memperbarui bidang.

### Apakah mungkin untuk memperbarui bidang berdasarkan budaya dokumen, bukan kode bidang?
Ya, Anda dapat mengaturnya `FieldUpdateCultureSource` ke `FieldUpdateCultureSource.Document` untuk menggunakan pengaturan budaya dokumen.

### Bagaimana cara memformat tanggal dalam pola yang berbeda?
Anda dapat mengubah pola format tanggal di `InsertField` metode dengan memodifikasi `\\@` nilai saklar.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}