---
title: Dapatkan Rentang Halaman Jpeg
linktitle: Dapatkan Rentang Halaman Jpeg
second_title: API Pemrosesan Dokumen Aspose.Words
description: Ubah halaman tertentu dari dokumen Word menjadi JPEG dengan pengaturan khusus menggunakan Aspose.Words untuk .NET. Pelajari cara menyesuaikan kecerahan, kontras, dan resolusi langkah demi langkah.
weight: 10
url: /id/net/programming-with-imagesaveoptions/get-jpeg-page-range/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dapatkan Rentang Halaman Jpeg

## Perkenalan

Mengonversi dokumen Word ke gambar bisa sangat berguna, baik saat Anda membuat gambar mini, melihat pratinjau dokumen secara daring, atau berbagi konten dalam format yang lebih mudah diakses. Dengan Aspose.Words untuk .NET, Anda dapat dengan mudah mengonversi halaman tertentu dari dokumen Word Anda ke format JPEG sambil menyesuaikan berbagai pengaturan seperti kecerahan, kontras, dan resolusi. Mari kita bahas cara melakukannya langkah demi langkah!

## Prasyarat

Sebelum kita memulai, Anda memerlukan beberapa hal berikut:

-  Aspose.Words untuk .NET: Pastikan Anda telah menginstal Aspose.Words untuk .NET. Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Lingkungan pengembangan AC# seperti Visual Studio.
- Contoh Dokumen: Dokumen Word untuk digunakan. Anda dapat menggunakan file .docx apa pun untuk tutorial ini.
- Pengetahuan Dasar C#: Keakraban dengan pemrograman C#.

Setelah Anda siap, mari kita mulai!

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words untuk .NET, Anda perlu mengimpor namespace yang diperlukan di awal kode Anda. Ini memastikan Anda memiliki akses ke semua kelas dan metode yang diperlukan untuk manipulasi dokumen.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Muat Dokumen Anda

Pertama, kita perlu memuat dokumen Word yang ingin kita ubah. Mari kita asumsikan dokumen kita diberi nama`Rendering.docx` dan terletak di direktori yang ditentukan oleh placeholder`YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Kode ini menginisialisasi jalur ke dokumen Anda dan memuatnya ke Aspose.Words`Document` obyek.

## Langkah 2: Siapkan ImageSaveOptions

 Selanjutnya, kita akan mengatur`ImageSaveOptions` untuk menentukan bagaimana kita ingin JPEG dihasilkan. Ini termasuk pengaturan rentang halaman, kecerahan gambar, kontras, dan resolusi.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // Konversi hanya halaman pertama
options.ImageBrightness = 0.3f;   // Mengatur kecerahan
options.ImageContrast = 0.7f;     // Mengatur kontras
options.HorizontalResolution = 72f; // Atur resolusi
```

## Langkah 3: Simpan Dokumen sebagai JPEG

Terakhir, kami menyimpan dokumen sebagai berkas JPEG menggunakan pengaturan yang telah kami tetapkan.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

 Kode ini menyimpan halaman pertama`Rendering.docx` sebagai gambar JPEG dengan pengaturan kecerahan, kontras, dan resolusi yang ditentukan.

## Kesimpulan

Nah, itu dia! Anda telah berhasil mengonversi halaman tertentu dari dokumen Word ke gambar JPEG dengan pengaturan khusus menggunakan Aspose.Words untuk .NET. Proses ini dapat disesuaikan dengan berbagai kebutuhan, baik Anda sedang mempersiapkan gambar untuk situs web, membuat pratinjau dokumen, atau lainnya.

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengonversi beberapa halaman sekaligus?
 Ya, Anda dapat menentukan rentang halaman menggunakan`PageSet` properti di`ImageSaveOptions`.

### Bagaimana cara menyesuaikan kualitas gambar?
 Anda dapat menyesuaikan kualitas JPEG dengan menggunakan`JpegQuality` properti di`ImageSaveOptions`.

### Bisakah saya menyimpan dalam format gambar lain?
 Ya, Aspose.Words mendukung berbagai format gambar seperti PNG, BMP, dan TIFF. Ubah`SaveFormat` di dalam`ImageSaveOptions` demikian.

### Apakah ada cara untuk melihat pratinjau gambar sebelum menyimpan?
Anda perlu menerapkan mekanisme pratinjau secara terpisah, karena Aspose.Words tidak menyediakan fitur pratinjau bawaan.

### Bagaimana cara mendapatkan lisensi sementara untuk Aspose.Words?
 Anda dapat meminta[lisensi sementara di sini](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
