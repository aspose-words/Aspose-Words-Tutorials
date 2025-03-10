---
title: Konversi Metafile ke Emf atau Wmf
linktitle: Konversi Metafile ke Emf atau Wmf
second_title: API Pemrosesan Dokumen Aspose.Words
description: Panduan langkah demi langkah untuk mengonversi metafile ke format EMF atau WMF saat mengonversi dokumen ke HTML dengan Aspose.Words untuk .NET.
weight: 10
url: /id/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konversi Metafile ke Emf atau Wmf

## Perkenalan

Selamat datang di pembahasan mendalam lainnya tentang dunia Aspose.Words untuk .NET. Hari ini, kita akan membahas trik yang menarik: mengonversi gambar SVG ke format EMF atau WMF dalam dokumen Word Anda. Ini mungkin terdengar sedikit teknis, tetapi jangan khawatir. Di akhir tutorial ini, Anda akan menjadi ahli dalam hal ini. Baik Anda seorang pengembang berpengalaman atau baru saja memulai dengan Aspose.Words untuk .NET, panduan ini akan memandu Anda melalui semua hal yang perlu Anda ketahui, langkah demi langkah.

## Prasyarat

Sebelum kita mulai membuat kode, mari kita pastikan semuanya sudah disiapkan. Berikut ini yang Anda perlukan:

1.  Aspose.Words untuk Pustaka .NET: Pastikan Anda memiliki versi terbaru. Jika Anda belum memilikinya, Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/net/).
2. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
3. Lingkungan Pengembangan: IDE seperti Visual Studio akan membuat hidup Anda lebih mudah.
4. Pengetahuan Dasar C#: Anda tidak perlu menjadi ahli, tetapi pemahaman dasar akan membantu.

Sudah punya semuanya? Bagus! Mari kita mulai.

## Mengimpor Ruang Nama

Pertama-tama, kita perlu mengimpor namespace yang diperlukan. Ini penting karena memberi tahu program kita di mana menemukan kelas dan metode yang akan kita gunakan.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ruang nama ini mencakup semuanya dari fungsi sistem dasar hingga fungsionalitas Aspose.Words spesifik yang kita perlukan untuk tutorial ini.

## Langkah 1: Siapkan Direktori Dokumen Anda

Mari kita mulai dengan menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda akan disimpan setelah kita mengonversi metafile.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya tempat Anda ingin menyimpan dokumen Anda.

## Langkah 2: Buat String HTML dengan SVG

Selanjutnya, kita memerlukan string HTML yang berisi gambar SVG yang ingin kita ubah. Berikut contoh sederhananya:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' lebar='500' tinggi='40' kotak tampilan='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

Potongan HTML ini menyertakan SVG dasar yang bertuliskan "Halo dunia!".

## Langkah 3: Muat HTML dengan Opsi ConvertSvgToEmf

 Sekarang, kita menggunakan`HtmlLoadOptions` untuk menentukan bagaimana kita ingin menangani gambar SVG dalam HTML. Pengaturan`ConvertSvgToEmf` ke`true` memastikan bahwa gambar SVG diubah ke format EMF.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

 Potongan kode ini membuat yang baru`Document` objek dengan memuat string HTML ke dalamnya dengan opsi muat yang ditentukan.

## Langkah 4: Mengatur HtmlSaveOptions untuk Format Metafile

 Untuk menyimpan dokumen dengan format metafile yang benar, kita menggunakan`HtmlSaveOptions` Di sini, kami mengatur`MetafileFormat` ke`HtmlMetafileFormat.Png` , tapi Anda dapat mengubahnya menjadi`Emf` atau`Wmf` tergantung kebutuhan Anda.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Langkah 5: Simpan Dokumen

Terakhir, kami menyimpan dokumen menggunakan opsi penyimpanan yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

Ini menyimpan dokumen dalam direktori yang ditentukan dengan format metafile yang dikonversi seperti yang ditentukan.

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda telah berhasil mengonversi gambar SVG ke format EMF atau WMF dalam dokumen Word Anda menggunakan Aspose.Words for .NET. Metode ini berguna untuk memastikan kompatibilitas dan menjaga integritas visual dokumen Anda di berbagai platform. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengonversi format gambar lain menggunakan metode ini?
Ya, Anda dapat mengonversi berbagai format gambar dengan menyesuaikan opsi muat dan simpan.

### Apakah perlu menggunakan versi .NET Framework tertentu?
Aspose.Words untuk .NET mendukung beberapa versi .NET Framework, tetapi sebaiknya selalu menggunakan versi terbaru untuk kompatibilitas dan fitur terbaik.

### Apa keuntungan mengonversi SVG ke EMF atau WMF?
Mengonversi SVG ke EMF atau WMF memastikan bahwa grafik vektor dipertahankan dan ditampilkan dengan benar di lingkungan yang mungkin tidak sepenuhnya mendukung SVG.

### Bisakah saya mengotomatiskan proses ini untuk beberapa dokumen?
Tentu saja! Anda dapat mengulang beberapa file HTML, dengan menerapkan proses yang sama untuk mengotomatiskan konversi untuk pemrosesan batch.

### Di mana saya dapat menemukan lebih banyak sumber daya dan dukungan untuk Aspose.Words untuk .NET?
 Anda dapat menemukan dokumentasi yang lengkap[Di Sini](https://reference.aspose.com/words/net/) dan mendapatkan dukungan dari komunitas Aspose[Di Sini](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
