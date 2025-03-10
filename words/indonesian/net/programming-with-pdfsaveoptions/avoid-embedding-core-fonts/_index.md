---
title: Kurangi Ukuran File PDF dengan Tidak Menyertakan Font Inti
linktitle: Kurangi Ukuran File PDF dengan Tidak Menyertakan Font Inti
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengurangi ukuran file PDF dengan tidak menyematkan font inti menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk mengoptimalkan PDF Anda.
weight: 10
url: /id/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kurangi Ukuran File PDF dengan Tidak Menyertakan Font Inti

## Perkenalan

Pernahkah Anda merasa bingung, bertanya-tanya mengapa file PDF Anda begitu besar? Anda tidak sendirian. Salah satu penyebab umum adalah penyematan font inti seperti Arial dan Times New Roman. Untungnya, Aspose.Words untuk .NET memiliki cara yang bagus untuk mengatasi masalah ini. Dalam tutorial ini, saya akan menunjukkan kepada Anda cara mengurangi ukuran file PDF dengan menghindari penyematan font inti ini. Mari kita bahas lebih lanjut!

## Prasyarat

Sebelum memulai perjalanan yang mengasyikkan ini, mari pastikan Anda memiliki semua yang Anda butuhkan. Berikut daftar periksa singkatnya:

-  Aspose.Words untuk .NET: Pastikan Anda telah menginstal Aspose.Words untuk .NET. Jika Anda belum memilikinya, Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Anda memerlukan lingkungan pengembangan seperti Visual Studio.
- Dokumen Word: Kami akan menggunakan dokumen Word (misalnya, "Rendering.docx") untuk tutorial ini.
- Pengetahuan Dasar C#: Pemahaman dasar tentang C# akan membantu Anda mengikutinya.

Baiklah, sekarang kita sudah siap, mari kita masuk ke inti permasalahan!

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Langkah ini memastikan kita memiliki akses ke semua fungsi Aspose.Words yang kita perlukan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Inisialisasi Direktori Dokumen Anda

Sebelum kita mulai memanipulasi dokumen kita, kita perlu menentukan direktori tempat dokumen kita disimpan. Ini penting untuk mengakses berkas-berkas tersebut.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya tempat dokumen Word Anda berada.

## Langkah 2: Muat Dokumen Word

Selanjutnya, kita perlu memuat dokumen Word yang ingin kita ubah ke PDF. Dalam contoh ini, kita menggunakan dokumen bernama "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Baris kode ini memuat dokumen ke dalam memori, siap untuk diproses lebih lanjut.

## Langkah 3: Konfigurasikan Opsi Penyimpanan PDF

Sekarang tibalah bagian ajaibnya! Kita akan mengonfigurasi opsi penyimpanan PDF untuk menghindari penyematan font inti. Ini adalah langkah kunci yang membantu mengurangi ukuran file PDF.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

 Pengaturan`UseCoreFonts` ke`true` memastikan bahwa font inti seperti Arial dan Times New Roman tidak tertanam dalam PDF, yang secara signifikan mengurangi ukuran file.

## Langkah 4: Simpan Dokumen sebagai PDF

Terakhir, kami menyimpan dokumen Word sebagai PDF menggunakan opsi penyimpanan yang telah dikonfigurasi. Langkah ini menghasilkan file PDF tanpa menyertakan font inti.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

Nah, itu dia! File PDF Anda sekarang tersimpan di direktori yang ditentukan tanpa font inti yang besar.

## Kesimpulan

Mengurangi ukuran file PDF dapat dilakukan dengan mudah menggunakan Aspose.Words untuk .NET. Dengan menghindari penyematan font inti, Anda dapat mengurangi ukuran file secara signifikan, sehingga memudahkan Anda untuk berbagi dan menyimpan dokumen. Saya harap tutorial ini bermanfaat dan memberi Anda pemahaman yang jelas tentang prosesnya. Ingat, perubahan kecil dapat membuat perbedaan besar!

## Pertanyaan yang Sering Diajukan

### Mengapa saya harus menghindari menanamkan font inti dalam PDF?
Menghindari penyematan font inti akan mengurangi ukuran berkas, membuatnya lebih mudah untuk dibagikan dan disimpan.

### Apakah saya masih dapat melihat PDF dengan benar tanpa font inti yang tertanam?
Ya, font inti seperti Arial dan Times New Roman umumnya tersedia di sebagian besar sistem.

### Bagaimana jika saya perlu menanamkan font khusus?
 Anda dapat menyesuaikan`PdfSaveOptions`untuk menanamkan font tertentu sesuai kebutuhan.

### Apakah Aspose.Words untuk .NET gratis untuk digunakan?
 Aspose.Words untuk .NET memerlukan lisensi. Anda bisa mendapatkan uji coba gratis[Di Sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang Aspose.Words untuk .NET?
 Anda dapat menemukan dokumentasi terperinci[Di Sini](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
