---
"description": "Pelajari cara mengaktifkan atau menonaktifkan substitusi font dalam dokumen Word menggunakan Aspose.Words untuk .NET. Pastikan dokumen Anda terlihat konsisten di semua platform."
"linktitle": "Aktifkan Nonaktifkan Substitusi Font"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Aktifkan Nonaktifkan Substitusi Font"
"url": "/id/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aktifkan Nonaktifkan Substitusi Font

## Perkenalan

Pernahkah Anda menemukan diri Anda dalam situasi di mana font yang Anda pilih dengan cermat dalam dokumen Word terganti saat dilihat di komputer lain? Menyebalkan, bukan? Hal ini terjadi karena substitusi font, sebuah proses di mana sistem mengganti font yang hilang dengan font yang tersedia. Namun, jangan khawatir! Dengan Aspose.Words untuk .NET, Anda dapat mengelola dan mengontrol substitusi font dengan mudah. Dalam tutorial ini, kami akan memandu Anda melalui langkah-langkah untuk mengaktifkan atau menonaktifkan substitusi font dalam dokumen Word Anda, memastikan dokumen Anda selalu terlihat seperti yang Anda inginkan.

## Prasyarat

Sebelum masuk ke langkah-langkahnya, mari pastikan Anda memiliki semua yang dibutuhkan:

- Aspose.Words untuk .NET: Unduh versi terbaru [Di Sini](https://releases.aspose.com/words/net/).
- Visual Studio: Versi apa pun yang mendukung .NET.
- Pengetahuan dasar C#: Ini akan membantu Anda mengikuti contoh pengkodean.

## Mengimpor Ruang Nama

Untuk memulai, pastikan Anda telah mengimpor namespace yang diperlukan ke dalam proyek Anda. Tambahkan namespace ini di bagian atas file C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Sekarang, mari kita uraikan prosesnya menjadi beberapa langkah yang sederhana dan mudah dikelola.

## Langkah 1: Siapkan Proyek Anda

Pertama, buat proyek baru di Visual Studio dan tambahkan referensi ke pustaka Aspose.Words for .NET. Jika Anda belum melakukannya, unduh dari [Situs web Aspose](https://releases.aspose.com/words/net/).

## Langkah 2: Muat Dokumen Anda

Selanjutnya, muat dokumen yang ingin Anda kerjakan. Berikut cara melakukannya:

```csharp
// Jalur ke direktori dokumen Anda 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke direktori dokumen Anda. Kode ini memuat dokumen ke dalam memori sehingga Anda dapat memanipulasinya.

## Langkah 3: Konfigurasikan Pengaturan Font

Sekarang, mari kita membuat `FontSettings` objek untuk mengelola pengaturan substitusi font:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Langkah 4: Mengatur Substitusi Font Default

Tetapkan substitusi font default ke font pilihan Anda. Font ini akan digunakan jika font asli tidak tersedia:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

Dalam contoh ini, kami menggunakan Arial sebagai font default.

## Langkah 5: Nonaktifkan Substitusi Info Font

Untuk menonaktifkan substitusi info font, yang menghentikan sistem mengganti font yang hilang dengan font yang tersedia, gunakan kode berikut:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Langkah 6: Terapkan Pengaturan Font ke Dokumen

Sekarang, terapkan pengaturan ini ke dokumen Anda:

```csharp
doc.FontSettings = fontSettings;
```

## Langkah 7: Simpan Dokumen Anda

Terakhir, simpan dokumen yang telah dimodifikasi. Anda dapat menyimpannya dalam format apa pun yang Anda suka. Untuk tutorial ini, kami akan menyimpannya sebagai PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengontrol penggantian font di dokumen Word Anda menggunakan Aspose.Words for .NET. Ini memastikan dokumen Anda tetap terlihat dan terasa seperti yang diinginkan, di mana pun dokumen tersebut dilihat.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan font selain Arial untuk substitusi?

Tentu saja! Anda dapat menentukan font apa pun yang tersedia di sistem Anda dengan mengubah nama font di `DefaultFontName` milik.

### Apa yang terjadi jika font default yang ditentukan tidak tersedia?

Jika font default tidak tersedia, Aspose.Words akan menggunakan mekanisme cadangan sistem untuk menemukan pengganti yang sesuai.

### Bisakah saya mengaktifkan kembali substitusi font setelah menonaktifkannya?

Ya, Anda dapat mengaktifkan `Enabled` milik `FontInfoSubstitution` kembali ke `true` jika Anda ingin mengaktifkan kembali substitusi font.

### Apakah ada cara untuk memeriksa font mana yang diganti?

Ya, Aspose.Words menyediakan metode untuk mencatat dan melacak penggantian font, sehingga Anda dapat melihat font mana yang sedang diganti.

### Bisakah saya menggunakan metode ini untuk format dokumen lain selain DOCX?

Tentu saja! Aspose.Words mendukung berbagai format, dan Anda dapat menerapkan pengaturan font ini ke format apa pun yang didukung.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}