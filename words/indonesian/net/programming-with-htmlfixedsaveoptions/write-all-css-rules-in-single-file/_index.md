---
title: Tulis Semua Aturan CSS Dalam Satu File
linktitle: Tulis Semua Aturan CSS Dalam Satu File
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengonversi dokumen Word ke HTML menggunakan Aspose.Words untuk .NET dengan semua aturan CSS dalam satu berkas untuk kode yang lebih bersih dan pemeliharaan yang lebih mudah.
weight: 10
url: /id/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tulis Semua Aturan CSS Dalam Satu File

## Perkenalan

Pernahkah Anda merasa terjerat dalam jalinan aturan CSS yang tersebar di mana-mana saat mengonversi dokumen Word ke HTML? Jangan khawatir! Hari ini, kita akan membahas fitur menarik Aspose.Words untuk .NET yang memungkinkan Anda menulis semua aturan CSS dalam satu berkas. Fitur ini tidak hanya merapikan kode Anda, tetapi juga membuat hidup Anda jauh lebih mudah. Bersiaplah, dan mari kita mulai perjalanan menuju keluaran HTML yang lebih bersih dan efisien!

## Prasyarat

Sebelum kita menyelami inti permasalahannya, mari kita persiapkan segala sesuatunya. Berikut ini hal-hal yang Anda perlukan untuk memulai:

1.  Aspose.Words untuk .NET: Pastikan Anda memiliki pustaka Aspose.Words untuk .NET. Jika Anda belum memilikinya, Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan .NET: Anda memerlukan lingkungan pengembangan .NET yang sudah disiapkan di komputer Anda. Visual Studio adalah pilihan yang populer.
3. Pengetahuan Dasar C#: Pemahaman dasar tentang pemrograman C# akan sangat membantu.
4. Dokumen Word: Siapkan dokumen Word (.docx) yang ingin Anda konversi.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan ke dalam proyek C# Anda. Ini akan memudahkan kita mengakses fungsi Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Baiklah, mari kita uraikan prosesnya menjadi beberapa langkah yang mudah diikuti. Setiap langkah akan memandu Anda melalui bagian tertentu dari proses tersebut untuk memastikan semuanya berjalan lancar.

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama, kita perlu menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda disimpan dan tempat HTML yang dikonversi akan disimpan.

```csharp
// Jalur akses ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Langkah 2: Muat Dokumen Word

 Selanjutnya, kita memuat dokumen Word yang ingin Anda ubah menjadi HTML. Ini dilakukan dengan menggunakan`Document` kelas dari pustaka Aspose.Words.

```csharp
// Memuat dokumen Word
Document doc = new Document(dataDir + "Document.docx");
```

## Langkah 3: Konfigurasikan Opsi Penyimpanan HTML

 Sekarang, kita perlu mengonfigurasi opsi penyimpanan HTML. Secara khusus, kita ingin mengaktifkan fitur yang menulis semua aturan CSS ke dalam satu berkas. Hal ini dicapai dengan menyetel`SaveFontFaceCssSeparately`properti untuk`false`.

```csharp
// Konfigurasikan opsi cadangan dengan fitur "Tulis semua aturan CSS dalam satu file"
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## Langkah 4: Ubah Dokumen menjadi HTML Tetap

Terakhir, kami menyimpan dokumen sebagai file HTML menggunakan opsi penyimpanan yang dikonfigurasi. Langkah ini memastikan bahwa semua aturan CSS ditulis dalam satu file.

```csharp
// Konversi dokumen ke HTML tetap
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## Kesimpulan

Nah, itu dia! Hanya dengan beberapa baris kode, Anda telah berhasil mengonversi dokumen Word ke HTML dengan semua aturan CSS yang tertata rapi dalam satu berkas. Metode ini tidak hanya menyederhanakan pengelolaan CSS, tetapi juga meningkatkan kemudahan perawatan dokumen HTML. Jadi, lain kali Anda ditugaskan mengonversi dokumen Word, Anda tahu persis cara menjaga kerapiannya!

## Pertanyaan yang Sering Diajukan

### Mengapa saya harus menggunakan satu berkas CSS untuk keluaran HTML saya?
Menggunakan satu berkas CSS menyederhanakan pengelolaan dan pemeliharaan gaya Anda. Ini membuat HTML Anda lebih bersih dan lebih efisien.

### Dapatkah saya memisahkan aturan CSS tampilan font jika diperlukan?
 Ya, dengan pengaturan`SaveFontFaceCssSeparately` ke`true`, Anda dapat memisahkan aturan CSS tampilan font ke dalam file yang berbeda.

### Apakah Aspose.Words untuk .NET gratis untuk digunakan?
 Aspose.Words menawarkan uji coba gratis yang dapat Anda[unduh disini](https://releases.aspose.com/) Untuk penggunaan berkelanjutan, pertimbangkan untuk membeli lisensi[Di Sini](https://purchase.aspose.com/buy).

### Format apa lagi yang dapat dikonversi oleh Aspose.Words untuk .NET?
Aspose.Words untuk .NET mendukung berbagai format termasuk PDF, TXT, dan format gambar seperti JPEG dan PNG.

### Di mana saya dapat menemukan lebih banyak sumber daya tentang Aspose.Words untuk .NET?
 Lihat di sini[dokumentasi](https://reference.aspose.com/words/net/) untuk panduan lengkap dan referensi API.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
