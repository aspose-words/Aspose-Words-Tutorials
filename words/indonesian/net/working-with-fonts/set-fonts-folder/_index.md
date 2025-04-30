---
"description": "Pelajari cara mengatur folder font kustom di Aspose.Words untuk .NET untuk memastikan dokumen Word Anda ditampilkan dengan benar tanpa font yang hilang."
"linktitle": "Atur Folder Font"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Atur Folder Font"
"url": "/id/net/working-with-fonts/set-fonts-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atur Folder Font

## Perkenalan

Pernahkah Anda menghadapi masalah dengan font yang hilang saat bekerja dengan dokumen Word di aplikasi .NET Anda? Nah, Anda tidak sendirian. Menetapkan folder font yang benar dapat menyelesaikan masalah ini dengan mudah. Dalam panduan ini, kami akan memandu Anda melalui cara menetapkan folder font menggunakan Aspose.Words untuk .NET. Mari kita bahas!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

- Visual Studio terinstal di komputer Anda
- Pengaturan .NET Framework
- Pustaka Aspose.Words untuk .NET. Jika Anda belum memilikinya, Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/net/).

## Mengimpor Ruang Nama

Pertama, Anda perlu mengimpor namespace yang diperlukan untuk bekerja dengan Aspose.Words. Tambahkan baris berikut di bagian atas berkas kode Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Menyiapkan folder font mudah dilakukan jika Anda mengikuti langkah-langkah ini dengan cermat.

## Langkah 1: Tentukan Direktori Dokumen

Sebelum melakukan hal lain, tentukan jalur ke direktori dokumen Anda. Direktori ini akan berisi dokumen Word dan font yang ingin Anda gunakan.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Pastikan untuk mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke direktori Anda.

## Langkah 2: Inisialisasi FontSettings

Sekarang, Anda perlu menginisialisasi `FontSettings` objek. Objek ini memungkinkan Anda menentukan folder font khusus.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Langkah 3: Atur Folder Font

Menggunakan `SetFontsFolder` metode dari `FontSettings` objek, tentukan folder tempat font kustom Anda disimpan.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

Di Sini, `dataDir + "Fonts"` menunjuk ke folder bernama "Font" dalam direktori dokumen Anda. Parameter kedua, `false`, menunjukkan bahwa folder tersebut tidak rekursif.

## Langkah 4: Buat LoadOptions

Selanjutnya, buatlah sebuah instance dari `LoadOptions` Kelas ini akan membantu Anda memuat dokumen dengan pengaturan font yang ditentukan.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## Langkah 5: Muat Dokumen

Terakhir, muat dokumen Word menggunakan `Document` kelas dan `LoadOptions` obyek.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

Pastikan bahwa `"Rendering.docx"` adalah nama dokumen Word Anda. Anda dapat menggantinya dengan nama file Anda.

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengatur folder font khusus di Aspose.Words untuk .NET, memastikan bahwa semua font Anda ditampilkan dengan benar. Pengaturan sederhana ini dapat menghemat banyak masalah dan membuat dokumen Anda terlihat persis seperti yang Anda inginkan.

## Pertanyaan yang Sering Diajukan

### Mengapa saya perlu mengatur folder font khusus?
Menetapkan folder font khusus memastikan semua font yang digunakan dalam dokumen Word Anda ditampilkan dengan benar, sehingga menghindari masalah font yang hilang.

### Bisakah saya mengatur beberapa folder font?
Ya, Anda bisa menggunakan `SetFontsFolders` metode untuk menentukan beberapa folder.

### Apa yang terjadi jika font tidak ditemukan?
Aspose.Words akan mencoba mengganti font yang hilang dengan font serupa dari font sistem.

### Apakah Aspose.Words kompatibel dengan .NET Core?
Ya, Aspose.Words mendukung .NET Core dan .NET Framework.

### Di mana saya bisa mendapatkan dukungan jika saya menghadapi masalah?
Anda bisa mendapatkan dukungan dari [Forum dukungan Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}