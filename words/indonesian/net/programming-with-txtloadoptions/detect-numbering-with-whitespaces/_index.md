---
"description": "Temukan cara menggunakan Aspose.Words untuk .NET untuk mendeteksi penomoran dengan spasi dalam dokumen teks biasa dan memastikan daftar Anda dikenali dengan benar."
"linktitle": "Mendeteksi Penomoran Dengan Spasi Putih"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Mendeteksi Penomoran Dengan Spasi Putih"
"url": "/id/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mendeteksi Penomoran Dengan Spasi Putih

## Perkenalan

Aspose.Words untuk penggemar .NET! Hari ini, kita akan menyelami fitur menarik yang dapat mempermudah penanganan daftar dalam dokumen teks biasa. Pernahkah Anda menangani berkas teks yang beberapa barisnya seharusnya berupa daftar, tetapi tidak terlihat benar saat dimuat ke dalam dokumen Word? Nah, kami punya trik yang bagus: mendeteksi penomoran dengan spasi. Tutorial ini akan memandu Anda tentang cara menggunakan `DetectNumberingWithWhitespaces` opsi di Aspose.Words untuk .NET untuk memastikan daftar Anda dikenali dengan benar, bahkan saat ada spasi di antara angka dan teks.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

- Aspose.Words untuk .NET: Anda dapat mengunduhnya dari [Rilis Aspose](https://releases.aspose.com/words/net/) halaman.
- Lingkungan Pengembangan: Visual Studio atau IDE C# lainnya.
- .NET Framework terinstal di komputer Anda.
- Pengetahuan Dasar C#: Memahami dasar-dasarnya akan membantu Anda mengikuti contoh-contohnya.

## Mengimpor Ruang Nama

Sebelum memulai kode, pastikan Anda telah mengimpor namespace yang diperlukan ke dalam proyek Anda. Berikut cuplikan singkat untuk membantu Anda memulai:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Mari kita uraikan prosesnya menjadi beberapa langkah yang sederhana dan mudah dikelola. Setiap langkah akan memandu Anda melalui kode yang diperlukan dan menjelaskan apa yang terjadi.

## Langkah 1: Tentukan Direktori Dokumen Anda

Pertama-tama, mari kita atur jalur ke direktori dokumen Anda. Di sinilah berkas masukan dan keluaran Anda akan disimpan.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Buat Dokumen Plaintext

Selanjutnya, kita akan membuat dokumen teks biasa sebagai string. Dokumen ini akan berisi bagian-bagian yang dapat diartikan sebagai daftar.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Langkah 3: Konfigurasikan LoadOptions

Untuk mendeteksi penomoran dengan spasi, kita perlu mengatur `DetectNumberingWithWhitespaces` pilihan untuk `true` di sebuah `TxtLoadOptions` obyek.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Langkah 4: Muat Dokumen

Sekarang, mari kita memuat dokumen menggunakan `TxtLoadOptions` sebagai parameter. Ini memastikan bahwa daftar keempat (dengan spasi) terdeteksi dengan benar.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Langkah 5: Simpan Dokumen

Terakhir, simpan dokumen ke direktori yang Anda tentukan. Ini akan menghasilkan dokumen Word dengan daftar yang terdeteksi dengan benar.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Kesimpulan

Nah, itu dia! Hanya dengan beberapa baris kode, Anda telah menguasai seni mendeteksi penomoran dengan spasi dalam dokumen teks biasa menggunakan Aspose.Words untuk .NET. Fitur ini dapat sangat berguna saat menangani berbagai format teks dan memastikan daftar Anda terwakili secara akurat dalam dokumen Word Anda. Jadi, lain kali Anda menghadapi daftar yang rumit itu, Anda akan tahu persis apa yang harus dilakukan.

## Pertanyaan yang Sering Diajukan

### Apa `DetectNumberingWithWhitespaces` di Aspose.Words untuk .NET?
`DetectNumberingWithWhitespaces` adalah sebuah pilihan di `TxtLoadOptions` yang memungkinkan Aspose.Words mengenali daftar bahkan ketika ada spasi antara penomoran dan teks item daftar.

### Dapatkah saya menggunakan fitur ini untuk pemisah lain seperti poin dan tanda kurung?
Ya, Aspose.Words secara otomatis mendeteksi daftar dengan pembatas umum seperti poin dan tanda kurung. `DetectNumberingWithWhitespaces` khususnya membantu dengan daftar yang memiliki spasi.

### Apa yang terjadi jika saya tidak menggunakannya.... `DetectNumberingWithWhitespaces`?
Tanpa opsi ini, daftar dengan spasi antara penomoran dan teks mungkin tidak dikenali sebagai daftar, dan item dapat muncul sebagai paragraf biasa.

### Apakah fitur ini tersedia di produk Aspose lainnya?
Fitur khusus ini dirancang untuk Aspose.Words untuk .NET, yang dirancang untuk menangani pemrosesan dokumen Word.

### Bagaimana cara mendapatkan lisensi sementara untuk Aspose.Words untuk .NET?
Anda dapat memperoleh lisensi sementara dari [Aspose Lisensi Sementara](https://purchase.aspose.com/temporary-license/) halaman.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}