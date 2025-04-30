---
"description": "Pelajari cara mengatur folder font untuk contoh default di Aspose.Words untuk .NET dengan tutorial langkah demi langkah ini. Sesuaikan dokumen Word Anda dengan mudah."
"linktitle": "Atur Font Folder Default Instance"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Atur Font Folder Default Instance"
"url": "/id/net/working-with-fonts/set-fonts-folders-default-instance/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atur Font Folder Default Instance

## Perkenalan

Hai, rekan pembuat kode! Jika Anda bekerja dengan dokumen Word dalam .NET, Anda mungkin tahu pentingnya memiliki font yang tepat. Hari ini, kita akan membahas cara mengatur folder font untuk contoh default menggunakan Aspose.Words untuk .NET. Bayangkan memiliki semua font kustom di ujung jari Anda, membuat dokumen Anda terlihat persis seperti yang Anda bayangkan. Kedengarannya hebat, bukan? Mari kita mulai!

## Prasyarat

Sebelum kita menyelami detailnya, mari pastikan Anda memiliki semua yang dibutuhkan:
- Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka tersebut. Jika belum, Anda dapat [unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Visual Studio atau IDE lain yang kompatibel dengan .NET.
- Pengetahuan Dasar C#: Anda harus merasa nyaman dengan pemrograman C#.
- Folder Font: Direktori yang berisi font khusus Anda.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini membantu dalam mengakses kelas dan metode yang diperlukan untuk mengatur folder font.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Mari kita uraikan prosesnya menjadi beberapa langkah yang sederhana dan mudah dicerna.

## Langkah 1: Tentukan Direktori Data

Setiap perjalanan hebat dimulai dengan satu langkah, dan perjalanan kami dimulai dengan menentukan direktori tempat dokumen Anda disimpan. Di sinilah Aspose.Words akan mencari dokumen Word Anda.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Di sini, ganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke direktori dokumen Anda. Di sinilah dokumen sumber Anda berada dan di mana output akan disimpan.

## Langkah 2: Atur Folder Font

Sekarang, mari kita beri tahu Aspose.Words di mana menemukan font kustom Anda. Ini dilakukan dengan mengatur folder font menggunakan `FontSettings.DefaultInstance.SetFontsFolder` metode.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

Pada baris ini, `"C:\\MyFonts\\"` adalah jalur ke folder font kustom Anda. Parameter kedua, `true`, menunjukkan bahwa font dalam folder ini harus dipindai secara rekursif.

## Langkah 3: Muat Dokumen Anda

Setelah folder font diatur, langkah selanjutnya adalah memuat dokumen Word Anda ke Aspose.Words. Ini dilakukan dengan menggunakan `Document` kelas.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Di Sini, `dataDir + "Rendering.docx"` merujuk ke jalur lengkap dokumen Word Anda. Pastikan dokumen Anda berada di direktori yang ditentukan.

## Langkah 4: Simpan Dokumen

Langkah terakhir adalah menyimpan dokumen Anda setelah mengatur folder font. Ini memastikan bahwa font kustom Anda diterapkan dengan benar dalam output.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Baris ini menyimpan dokumen Anda sebagai PDF dengan font khusus yang diterapkan. File output akan ditempatkan di direktori yang sama dengan dokumen sumber Anda.

## Kesimpulan

Nah, itu dia! Menetapkan folder font untuk instance default di Aspose.Words untuk .NET mudah dilakukan jika Anda membaginya menjadi beberapa langkah sederhana. Dengan mengikuti panduan ini, Anda dapat memastikan bahwa dokumen Word Anda terlihat persis seperti yang Anda inginkan, dengan semua font kustom yang sudah tersedia. Jadi, silakan, cobalah, dan buat dokumen Anda bersinar!

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengatur beberapa folder font?
Ya, Anda dapat mengatur beberapa folder font dengan menggunakan `SetFontsFolders` metode yang menerima serangkaian jalur folder.

### Format file apa yang didukung Aspose.Words untuk menyimpan dokumen?
Aspose.Words mendukung berbagai format termasuk DOCX, PDF, HTML, EPUB, dan banyak lagi.

### Bisakah saya menggunakan font daring di Aspose.Words?
Tidak, Aspose.Words saat ini hanya mendukung berkas font lokal.

### Bagaimana saya dapat memastikan font khusus saya tertanam dalam PDF yang tersimpan?
Dengan mengatur `FontSettings` dengan benar dan memastikan font tersedia, Aspose.Words akan menanamkannya dalam keluaran PDF.

### Apa yang terjadi jika font tidak ditemukan dalam folder yang ditentukan?
Aspose.Words akan menggunakan font cadangan jika font yang ditentukan tidak ditemukan.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}