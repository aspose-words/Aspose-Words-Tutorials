---
"description": "Pelajari cara mengekspor font sebagai Base64 menggunakan Aspose.Words untuk .NET dalam tutorial terperinci ini. Pastikan font tertanam dan ditampilkan dengan benar dalam file HTML."
"linktitle": "Ekspor Font Sebagai Basis 64"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Ekspor Font Sebagai Basis 64"
"url": "/id/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ekspor Font Sebagai Basis 64

## Perkenalan

Dalam hal memanipulasi dokumen Word secara terprogram, Aspose.Words for .NET adalah yang terbaik. Salah satu fiturnya yang bagus adalah mengekspor font sebagai Base64 dalam file HTML, memastikan font tertanam dan ditampilkan dengan benar di berbagai browser dan sistem. Dalam tutorial ini, kita akan membahas cara melakukannya. Siap membuat font dokumen Word Anda ramah web? Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke pengkodean, mari pastikan Anda memiliki semua yang dibutuhkan:

- Pustaka Aspose.Words untuk .NET: Anda dapat mengunduhnya dari [Rilis Aspose](https://releases.aspose.com/words/net/) halaman.
- Lingkungan Pengembangan .NET: IDE apa pun seperti Visual Studio akan bekerja dengan sempurna.
- Pengetahuan Dasar C#: Anda tidak perlu menjadi seorang profesional, tetapi pemahaman dasar akan membantu.

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words untuk .NET, Anda perlu mengimpor namespace yang diperlukan dalam kode C# Anda. Ini membuat semua kelas dan metode tersedia untuk digunakan.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Siapkan Proyek Anda

Hal pertama yang terpenting, mari kita siapkan proyek Anda dan instal pustaka Aspose.Words.

### 1.1 Buat Proyek Baru

Buka Visual Studio dan buat proyek Aplikasi Konsol baru. Beri nama yang bermakna seperti "ExportFontsBase64".

### 1.2 Instal Aspose.Words

Anda dapat menginstal Aspose.Words untuk .NET melalui NuGet Package Manager:

1. Klik kanan pada proyek Anda di Solution Explorer.
2. Pilih "Kelola Paket NuGet".
3. Cari "Aspose.Words" dan instal.

Sebagai alternatif, Anda dapat menjalankan perintah berikut di Konsol Manajer Paket:

```sh
Install-Package Aspose.Words
```

## Langkah 2: Muat Dokumen Word Anda

Sekarang proyek Anda sudah disiapkan, mari muat dokumen Word yang font-nya ingin Anda ekspor.

### 2.1 Menentukan Direktori Dokumen

Pertama, tentukan direktori tempat dokumen Word Anda berada:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke direktori dokumen Anda.

### 2.2 Memuat Dokumen

Selanjutnya, muat dokumen Anda menggunakan `Document` kelas:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Pastikan "Rendering.docx" ada di direktori yang Anda tentukan.

## Langkah 3: Konfigurasikan Opsi Penyimpanan HTML

Untuk mengekspor font sebagai Base64, kita perlu mengkonfigurasi `HtmlSaveOptions`.


Buat contoh dari `HtmlSaveOptions` dan mengatur `ExportFontsAsBase64` properti untuk `true`:

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## Langkah 4: Simpan Dokumen sebagai HTML

Terakhir, mari simpan dokumen dengan opsi yang dikonfigurasikan.


Gunakan `Save` metode dari `Document` kelas untuk menyimpan dokumen Anda:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

Baris ini akan menyimpan dokumen Anda sebagai berkas HTML dengan font yang diekspor sebagai Base64, memastikan font tersebut tertanam dalam HTML.

## Kesimpulan

Selamat! Anda telah berhasil mengekspor font sebagai Base64 dari dokumen Word menggunakan Aspose.Words untuk .NET. Ini memastikan bahwa font Anda dipertahankan dan ditampilkan dengan benar di berbagai platform. Baik Anda sedang mempersiapkan dokumen untuk tampilan web atau sekadar memastikan kompatibilitas, fitur ini sangat berguna.

## Pertanyaan yang Sering Diajukan

### Apa itu pengkodean Base64?
Base64 adalah metode pengkodean data biner (seperti font) ke dalam format teks. Ini memastikan kompatibilitas dengan format berbasis teks seperti HTML.

### Mengapa saya harus menggunakan Base64 untuk font dalam HTML?
Penggunaan Base64 memastikan bahwa font tertanam langsung dalam HTML, menghindari masalah dengan hilangnya file font dan memastikan tampilan yang konsisten.

### Dapatkah saya menggunakan metode ini untuk sumber daya lain seperti gambar?
Tentu saja! Aspose.Words untuk .NET memungkinkan Anda untuk menanamkan berbagai sumber daya, termasuk gambar, sebagai Base64 dalam berkas HTML Anda.

### Bagaimana jika dokumen saya memiliki banyak font?
Tidak masalah! Aspose.Words untuk .NET akan menyematkan semua font yang digunakan dalam dokumen Anda sebagai Base64 dalam file HTML yang dihasilkan.

### Apakah Aspose.Words untuk .NET gratis untuk digunakan?
Aspose.Words untuk .NET adalah pustaka komersial. Namun, Anda dapat mengunduh uji coba gratis dari [Rilis Aspose](https://releases.aspose.com/) halaman.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}