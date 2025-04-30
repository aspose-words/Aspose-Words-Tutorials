---
"description": "Pelajari cara mengonfigurasi fitur unit pengukuran di Aspose.Words untuk .NET untuk mempertahankan format dokumen selama konversi ODT."
"linktitle": "Satuan Ukuran"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Satuan Ukuran"
"url": "/id/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Satuan Ukuran

## Perkenalan

Pernahkah Anda harus mengonversi dokumen Word ke berbagai format tetapi memerlukan satuan ukuran tertentu untuk tata letak Anda? Baik Anda menggunakan inci, sentimeter, atau poin, memastikan dokumen Anda tetap utuh selama proses konversi sangatlah penting. Dalam tutorial ini, kami akan memandu Anda tentang cara mengonfigurasi fitur satuan ukuran di Aspose.Words untuk .NET. Fitur canggih ini memastikan bahwa format dokumen Anda dipertahankan persis seperti yang Anda butuhkan saat mengonversi ke format ODT (Open Document Text).

## Prasyarat

Sebelum menyelami kode, ada beberapa hal yang perlu Anda ketahui untuk memulai:

1. Aspose.Words untuk .NET: Pastikan Anda telah menginstal Aspose.Words versi terbaru untuk .NET. Jika Anda belum memilikinya, Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: IDE seperti Visual Studio untuk menulis dan mengeksekusi kode C# Anda.
3. Pengetahuan Dasar C#: Memahami dasar-dasar C# akan membantu Anda mengikuti tutorial.
4. Dokumen Word: Siapkan contoh dokumen Word yang dapat Anda gunakan untuk konversi.

## Mengimpor Ruang Nama

Sebelum kita mulai membuat kode, mari pastikan kita telah mengimpor namespace yang diperlukan. Tambahkan perintah menggunakan ini di bagian atas berkas kode Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama, Anda perlu menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda berada dan tempat penyimpanan berkas hasil konversi.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Mengganti `"YOUR DOCUMENTS DIRECTORY"` dengan jalur sebenarnya ke direktori Anda. Ini memastikan kode Anda mengetahui tempat menemukan dokumen Word Anda.

## Langkah 2: Muat Dokumen Word

Selanjutnya, Anda perlu memuat dokumen Word yang ingin Anda konversi. Ini dilakukan dengan menggunakan `Document` kelas dari Aspose.Words.

```csharp
// Memuat dokumen Word
Document doc = new Document(dataDir + "Document.docx");
```

Pastikan dokumen Word Anda, bernama "Document.docx", ada di direktori yang ditentukan.

## Langkah 3: Konfigurasikan Unit Pengukuran

Sekarang, mari kita konfigurasikan satuan pengukuran untuk konversi ODT. Di sinilah keajaiban terjadi. Kita akan mengatur `OdtSaveOptions` menggunakan inci sebagai satuan pengukuran.

```csharp
// Konfigurasi opsi cadangan dengan fitur "Unit pengukuran"
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

Dalam contoh ini, kami menyetel satuan pengukuran ke inci. Anda juga dapat memilih satuan lain seperti `OdtSaveMeasureUnit.Centimeters` atau `OdtSaveMeasureUnit.Points` Tergantung pada kebutuhan Anda.

## Langkah 4: Konversi Dokumen ke ODT

Terakhir, kita akan mengonversi dokumen Word ke format ODT menggunakan konfigurasi `OdtSaveOptions`.

```csharp
// Konversi dokumen ke ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Baris kode ini menyimpan dokumen yang dikonversi dalam direktori yang ditentukan dengan unit pengukuran baru yang diterapkan.

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengonfigurasi fitur satuan ukuran di Aspose.Words untuk .NET guna memastikan tata letak dokumen Anda dipertahankan selama konversi. Baik Anda bekerja dengan inci, sentimeter, atau poin, tutorial ini telah menunjukkan kepada Anda cara mengendalikan pemformatan dokumen dengan mudah.

## Tanya Jawab Umum

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka yang hebat untuk bekerja dengan dokumen Word secara terprogram. Pustaka ini memungkinkan pengembang untuk membuat, memodifikasi, mengonversi, dan memproses dokumen Word tanpa memerlukan Microsoft Word.

### Bisakah saya menggunakan satuan pengukuran lain selain inci?
Ya, Aspose.Words untuk .NET mendukung satuan pengukuran lain seperti sentimeter dan poin. Anda dapat menentukan satuan yang diinginkan menggunakan `OdtSaveMeasureUnit` enumerasi.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?
Ya, Anda dapat mengunduh uji coba gratis Aspose.Words untuk .NET dari [Di Sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dokumentasi untuk Aspose.Words untuk .NET?
Anda dapat mengakses dokumentasi lengkap untuk Aspose.Words untuk .NET di [tautan ini](https://reference.aspose.com/words/net/).

### Bagaimana saya bisa mendapatkan dukungan untuk Aspose.Words untuk .NET?
Untuk dukungan, Anda dapat mengunjungi forum Aspose.Words di [tautan ini](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}