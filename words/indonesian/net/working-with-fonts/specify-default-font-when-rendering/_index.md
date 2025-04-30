---
"description": "Pelajari cara menentukan font default saat merender dokumen Word menggunakan Aspose.Words untuk .NET. Pastikan tampilan dokumen konsisten di semua platform."
"linktitle": "Tentukan Font Default Saat Rendering"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Tentukan Font Default Saat Rendering"
"url": "/id/net/working-with-fonts/specify-default-font-when-rendering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tentukan Font Default Saat Rendering

## Perkenalan

Memastikan dokumen Word Anda ditampilkan dengan benar di berbagai platform bisa menjadi tantangan, terutama saat menangani kompatibilitas font. Salah satu cara untuk mempertahankan tampilan yang konsisten adalah dengan menentukan font default saat menampilkan dokumen Anda dalam format PDF atau format lainnya. Dalam tutorial ini, kita akan membahas cara mengatur font default menggunakan Aspose.Words untuk .NET, sehingga dokumen Anda tampak hebat di mana pun dokumen tersebut dilihat.

## Prasyarat

Sebelum menyelami kodenya, mari kita bahas apa saja yang perlu Anda ikuti dalam tutorial ini:

- Aspose.Words untuk .NET: Pastikan Anda telah menginstal versi terbaru. Anda dapat mengunduhnya [Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Visual Studio atau lingkungan pengembangan .NET lainnya.
- Pengetahuan Dasar C#: Tutorial ini mengasumsikan Anda nyaman dengan pemrograman C#.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan. Ini akan memungkinkan Anda mengakses kelas dan metode yang diperlukan untuk bekerja dengan Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Sekarang, mari kita uraikan proses menentukan font default ke dalam langkah-langkah yang mudah diikuti.

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama, tentukan jalur ke direktori dokumen Anda. Di sinilah berkas masukan dan keluaran Anda akan disimpan.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Muat Dokumen Anda

Selanjutnya, muat dokumen yang ingin Anda render. Dalam contoh ini, kita akan menggunakan file bernama "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Langkah 3: Konfigurasikan Pengaturan Font

Buat contoh dari `FontSettings` dan tentukan font default. Jika font yang ditentukan tidak dapat ditemukan selama rendering, Aspose.Words akan menggunakan font terdekat yang tersedia di komputer.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Langkah 4: Terapkan Pengaturan Font ke Dokumen

Tetapkan pengaturan font yang dikonfigurasikan ke dokumen Anda.

```csharp
doc.FontSettings = fontSettings;
```

## Langkah 5: Simpan Dokumen

Terakhir, simpan dokumen dalam format yang diinginkan. Dalam hal ini, kita akan menyimpannya sebagai PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Kesimpulan

Dengan mengikuti langkah-langkah ini, Anda dapat memastikan bahwa dokumen Word Anda ditampilkan dengan fon default yang ditentukan, sehingga tetap konsisten di berbagai platform. Hal ini dapat sangat berguna untuk dokumen yang dibagikan secara luas atau dilihat pada sistem dengan ketersediaan fon yang bervariasi.


## Pertanyaan yang Sering Diajukan

### Mengapa menentukan font default di Aspose.Words?
Menentukan font default memastikan dokumen Anda tampak konsisten di berbagai platform, bahkan jika font asli tidak tersedia.

### Apa yang terjadi jika font default tidak ditemukan selama rendering?
Aspose.Words akan menggunakan font paling dekat yang tersedia pada mesin untuk mempertahankan tampilan dokumen semirip mungkin.

### Bisakah saya menentukan beberapa font default?
Tidak, Anda hanya dapat menentukan satu font default. Namun, Anda dapat menangani penggantian font untuk kasus tertentu menggunakan `FontSettings` kelas.

### Apakah Aspose.Words untuk .NET kompatibel dengan semua versi dokumen Word?
Ya, Aspose.Words untuk .NET mendukung berbagai format dokumen Word, termasuk DOC, DOCX, RTF, dan banyak lagi.

### Di mana saya bisa mendapatkan dukungan jika saya mengalami masalah?
Anda bisa mendapatkan dukungan dari komunitas dan pengembang Aspose di [Forum Dukungan Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}