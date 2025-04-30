---
"description": "Panduan langkah demi langkah untuk mengurangi ukuran pdf dengan skala font wmf ke ukuran metafile saat mengonversi ke PDF dengan Aspose.Words untuk .NET."
"linktitle": "Kurangi Ukuran PDF dengan Mengubah Font Wmf Menjadi Ukuran Metafile"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Kurangi Ukuran PDF dengan Mengubah Font Wmf Menjadi Ukuran Metafile"
"url": "/id/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kurangi Ukuran PDF dengan Mengubah Font Wmf Menjadi Ukuran Metafile

## Perkenalan

Saat bekerja dengan file PDF, terutama yang dibuat dari dokumen Word yang berisi grafik WMF (Windows Metafile), manajemen ukuran dapat menjadi aspek penting dalam penanganan dokumen. Salah satu cara untuk mengontrol ukuran PDF adalah dengan menyesuaikan cara font WMF ditampilkan dalam dokumen. Dalam tutorial ini, kita akan membahas cara mengurangi ukuran PDF dengan mengubah skala font WMF ke ukuran metafile menggunakan Aspose.Words untuk .NET.

## Prasyarat

Sebelum memulai langkah-langkahnya, pastikan Anda memiliki hal berikut:

1. Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words. Jika belum, Anda dapat [unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Tutorial ini mengasumsikan Anda telah menyiapkan lingkungan pengembangan .NET (seperti Visual Studio) tempat Anda dapat menulis dan mengeksekusi kode C#.
3. Pemahaman Dasar Pemrograman .NET: Kemampuan memahami konsep dasar pemrograman .NET dan sintaksis C# akan sangat membantu.
4. Dokumen Word dengan Grafik WMF: Anda memerlukan dokumen Word yang berisi grafik WMF. Anda dapat menggunakan dokumen Anda sendiri atau membuatnya sendiri untuk pengujian.

## Mengimpor Ruang Nama

Pertama, Anda perlu mengimpor namespace yang diperlukan dalam proyek C# Anda. Ini akan memberi Anda akses ke kelas dan metode yang diperlukan untuk bekerja dengan Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Muat Dokumen Word

Untuk memulai, muat dokumen Word yang berisi grafik WMF. Ini dilakukan dengan menggunakan `Document` kelas dari Aspose.Words.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Muat dokumen
Document doc = new Document(dataDir + "WMF with text.docx");
```

Di Sini, `dataDir` adalah tempat penampung untuk jalur direktori dokumen Anda. Kami membuat contoh `Document` kelas dengan meneruskan jalur ke berkas Word. Ini memuat dokumen ke dalam memori, siap untuk diproses lebih lanjut.

## Langkah 2: Konfigurasikan Opsi Rendering Metafile

Selanjutnya, Anda perlu mengonfigurasi opsi rendering metafile. Secara khusus, atur `ScaleWmfFontsToMetafileSize` properti untuk `false`Ini mengontrol apakah font WMF diskalakan agar sesuai dengan ukuran metafile.

```csharp
// Buat contoh baru MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

Itu `MetafileRenderingOptions` kelas menyediakan opsi untuk bagaimana metafile (seperti WMF) ditampilkan. Dengan mengatur `ScaleWmfFontsToMetafileSize` ke `false`, Anda menginstruksikan Aspose.Words untuk tidak mengubah skala font sesuai dengan ukuran metafile, yang dapat membantu mengurangi ukuran PDF keseluruhan.

## Langkah 3: Atur Opsi Penyimpanan PDF

Sekarang, konfigurasikan opsi penyimpanan PDF untuk menggunakan opsi perenderan metafile yang baru saja Anda atur. Ini memberi tahu Aspose.Words cara menangani metafile saat menyimpan dokumen sebagai PDF.

```csharp
// Buat contoh baru PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

Itu `PdfSaveOptions` kelas memungkinkan Anda menentukan berbagai pengaturan untuk menyimpan dokumen sebagai PDF. Dengan menetapkan pengaturan yang dikonfigurasi sebelumnya `MetafileRenderingOptions` ke `MetafileRenderingOptions` milik `PdfSaveOptions`, Anda memastikan bahwa dokumen disimpan sesuai dengan pengaturan rendering metafile yang Anda inginkan.

## Langkah 4: Simpan Dokumen sebagai PDF

Terakhir, simpan dokumen Word sebagai PDF menggunakan opsi penyimpanan yang dikonfigurasi. Ini akan menerapkan semua pengaturan, termasuk opsi rendering metafile, ke PDF keluaran.


```csharp
// Simpan dokumen sebagai PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

Pada langkah ini, `Save` metode dari `Document` kelas digunakan untuk mengekspor dokumen ke file PDF. Jalur tempat PDF akan disimpan ditentukan, bersama dengan `PdfSaveOptions` yang menyertakan pengaturan rendering metafile.

## Kesimpulan

Dengan menskalakan font WMF ke ukuran metafile, Anda dapat mengurangi ukuran file PDF yang dihasilkan dari dokumen Word secara signifikan. Teknik ini membantu mengoptimalkan penyimpanan dan distribusi dokumen tanpa mengurangi kualitas konten visual. Mengikuti langkah-langkah yang diuraikan di atas memastikan bahwa file PDF Anda lebih mudah dikelola dan ukurannya lebih efisien.

## Pertanyaan yang Sering Diajukan

### Apa itu WMF dan mengapa penting untuk ukuran PDF?

WMF (Windows Metafile) adalah format grafis yang digunakan dalam Microsoft Windows. Format ini dapat memuat data vektor dan bitmap. Karena data vektor dapat diskalakan dan dimanipulasi, penting untuk menanganinya dengan benar guna menghindari file PDF yang terlalu besar.

### Bagaimana penskalaan font WMF ke ukuran metafile memengaruhi PDF?

Penskalaan font WMF ke ukuran metafile dapat membantu mengurangi ukuran PDF keseluruhan dengan menghindari rendering font beresolusi tinggi yang dapat meningkatkan ukuran file.

### Bisakah saya menggunakan format metafile lain dengan Aspose.Words?

Ya, Aspose.Words mendukung berbagai format metafile, termasuk EMF (Enhanced Metafile) dan WMF.

### Apakah teknik ini berlaku untuk semua jenis dokumen Word?

Ya, teknik ini dapat diterapkan pada dokumen Word apa pun yang berisi grafik WMF, membantu mengoptimalkan ukuran PDF yang dihasilkan.

### Di mana saya dapat menemukan informasi lebih lanjut tentang Aspose.Words?

Anda dapat menjelajahi lebih lanjut tentang Aspose.Words di [Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/)Untuk unduhan, uji coba, dan dukungan, kunjungi [Halaman Unduh Aspose.Words](https://releases.aspose.com/words/net/)Bahasa Indonesia: [Beli Aspose.Words](https://purchase.aspose.com/buy)Bahasa Indonesia: [Uji Coba Gratis](https://releases.aspose.com/)Bahasa Indonesia: [Lisensi Sementara](https://purchase.aspose.com/temporary-license/), Dan [Mendukung](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}