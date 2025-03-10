---
title: Escape URI dalam Dokumen PDF
linktitle: Escape URI dalam Dokumen PDF
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara meloloskan URI dalam PDF menggunakan Aspose.Words untuk .NET. Panduan terperinci ini memandu Anda melalui proses tersebut langkah demi langkah.
weight: 10
url: /id/net/programming-with-pdfsaveoptions/escape-uri/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Escape URI dalam Dokumen PDF

## Perkenalan

Hai! Pernahkah Anda bertanya-tanya bagaimana cara menangani URI saat menyimpan dokumen Word sebagai PDF menggunakan Aspose.Words untuk .NET? Anda berada di tempat yang tepat! Hari ini, kita akan membahas secara mendalam tentang escape URI dalam dokumen PDF untuk memastikannya berfungsi dengan benar saat dokumen Anda dikonversi. Mari kita mulai perjalanan ini bersama-sama, selangkah demi selangkah, memastikan Anda memahami setiap konsep di sepanjang jalan.

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Aspose.Words untuk .NET: Pastikan Anda memiliki versi terbaru. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau lingkungan pengembangan .NET lainnya.
3. Pengetahuan Dasar C#: Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang pemrograman C#.

## Mengimpor Ruang Nama

Pertama-tama, Anda perlu mengimpor namespace yang diperlukan. Ini penting untuk mengakses fungsi Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Baiklah, mari kita uraikan prosesnya menjadi beberapa langkah yang mudah dipahami. Ikuti langkah-langkahnya dan Anda akan menjadi ahli dalam meloloskan URI dalam waktu singkat!

## Langkah 1: Siapkan Direktori Dokumen Anda

Sebelum mulai menulis kode, tentukan jalur ke direktori dokumen Anda. Di sinilah berkas Anda akan disimpan.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya tempat Anda ingin menyimpan dokumen PDF Anda.

## Langkah 2: Buat Dokumen Baru

Selanjutnya, kita akan membuat dokumen baru menggunakan Aspose.Words. Dokumen ini akan berfungsi sebagai kanvas untuk menyisipkan hyperlink.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Di Sini,`Document` adalah dokumen Word baru Anda, dan`DocumentBuilder` adalah kelas pembantu yang menyederhanakan proses pembuatan dokumen.

## Langkah 3: Masukkan Hyperlink

Sekarang, mari masukkan hyperlink ke dalam dokumen. Hyperlink ini akan menjadi fokus proses escape URI kita.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose", salah);
```

 Pada baris ini,`"Testlink"` adalah teks tampilan untuk hyperlink, dan`"https://www.google.com/search?q= aspose"` adalah URL.`false` parameter menunjukkan bahwa tautan tidak boleh diformat sebagai hyperlink (yakni, tidak akan digarisbawahi dan berwarna biru).

## Langkah 4: Simpan Dokumen sebagai PDF

Terakhir, simpan dokumen sebagai PDF. Di sinilah Aspose.Words menangani proses escape URI dalam output PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

 Baris ini menyimpan dokumen ke direktori yang ditentukan dengan nama file`WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## Kesimpulan

Nah, itu dia! Anda baru saja mempelajari cara meloloskan URI saat menyimpan dokumen Word sebagai PDF menggunakan Aspose.Words untuk .NET. Proses ini memastikan bahwa hyperlink Anda tetap berfungsi dan diformat dengan benar dalam PDF yang dihasilkan. 

Ingat, menguasai teknik-teknik kecil namun penting ini dapat meningkatkan kualitas dan fungsionalitas dokumen Anda. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?

Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi dokumen Word dalam aplikasi .NET.

### Mengapa escape URI penting dalam PDF?

Pelarian URI memastikan karakter khusus pada URL ditafsirkan dengan benar, mencegah tautan rusak, dan memastikannya berfungsi sebagaimana mestinya.

### Dapatkah saya menggunakan jenis tautan lain di Aspose.Words untuk .NET?

Tentu saja! Aspose.Words mendukung berbagai jenis tautan, termasuk tautan dokumen internal, bookmark, dan URL eksternal.

### Bagaimana saya bisa mendapatkan uji coba gratis Aspose.Words untuk .NET?

 Anda bisa mendapatkan uji coba gratis[Di Sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dokumentasi yang lebih rinci tentang Aspose.Words untuk .NET?

 Anda dapat menemukan dokumentasi terperinci[Di Sini](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
