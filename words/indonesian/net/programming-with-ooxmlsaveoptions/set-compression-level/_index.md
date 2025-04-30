---
"description": "Pelajari cara mengatur tingkat kompresi dalam dokumen Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk mengoptimalkan penyimpanan dan kinerja dokumen Anda."
"linktitle": "Atur Tingkat Kompresi"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Atur Tingkat Kompresi"
"url": "/id/net/programming-with-ooxmlsaveoptions/set-compression-level/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atur Tingkat Kompresi

## Perkenalan

Siap menyelami dunia kompresi dokumen dengan Aspose.Words untuk .NET? Baik Anda ingin mengoptimalkan penyimpanan dokumen atau mempercepat waktu pemrosesan, pengaturan tingkat kompresi dapat membuat perbedaan besar. Dalam tutorial ini, kami akan memandu Anda melalui proses pengaturan tingkat kompresi untuk dokumen Word menggunakan Aspose.Words untuk .NET. Di akhir panduan ini, Anda akan menjadi ahli dalam membuat dokumen Anda lebih ramping dan lebih ringkas.

## Prasyarat

Sebelum kita masuk ke inti pembahasan, mari pastikan Anda memiliki semua yang dibutuhkan untuk mengikuti tutorial ini:

1. Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words untuk .NET. Anda dapat mengunduhnya dari [Halaman Rilis Aspose](https://releases.aspose.com/words/net/).

2. Lingkungan Pengembangan: Anda harus menyiapkan lingkungan pengembangan, seperti Visual Studio.

3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# sangat penting untuk mengikuti panduan ini.

4. Contoh Dokumen: Siapkan dokumen Word (misalnya, "Document.docx") di direktori proyek Anda.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini penting untuk mengakses fungsi Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Baiklah, mari kita uraikan ini ke dalam langkah-langkah kecil agar mudah Anda ikuti.

## Langkah 1: Siapkan Proyek Anda

Sebelum kita masuk ke kode, pastikan proyek Anda telah disiapkan dengan benar.

### Langkah 1.1: Buat Proyek Baru

Buka Visual Studio dan buat proyek Aplikasi Konsol C# baru. Beri nama seperti "AsposeWordsCompressionDemo."

### Langkah 1.2: Instal Aspose.Words untuk .NET

Anda perlu menambahkan Aspose.Words for .NET ke proyek Anda. Anda dapat melakukannya melalui Pengelola Paket NuGet. Cari "Aspose.Words" dan instal. Atau, Anda dapat menggunakan Konsol Pengelola Paket:

```shell
Install-Package Aspose.Words
```

## Langkah 2: Muat Dokumen Anda

Sekarang proyek Anda sudah disiapkan, mari muat dokumen yang ingin Anda kerjakan.

### Langkah 2.1: Tentukan Direktori Dokumen

Pertama, tentukan jalur ke direktori dokumen Anda. Ganti "DIREKTORI DOKUMEN ANDA" dengan jalur sebenarnya.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

### Langkah 2.2: Muat Dokumen

Gunakan kode berikut untuk memuat dokumen Word Anda:

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

## Langkah 3: Atur Tingkat Kompresi

Di sinilah keajaiban terjadi. Kami akan mengatur tingkat kompresi untuk dokumen tersebut.

Buat contoh dari `OoxmlSaveOptions` dan mengatur tingkat kompresi. `CompressionLevel` properti dapat diatur ke berbagai level seperti `Normal`Bahasa Indonesia: `Maximum`Bahasa Indonesia: `Fast`, Dan `SuperFast`Untuk contoh ini, kita akan menggunakan `SuperFast`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    CompressionLevel = CompressionLevel.SuperFast
};
```

## Langkah 4: Simpan Dokumen

Terakhir, simpan dokumen dengan pengaturan kompresi baru.

Gunakan `Save` metode untuk menyimpan dokumen Anda dengan tingkat kompresi yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
```

## Langkah 5: Verifikasi Output

Setelah menjalankan aplikasi Anda, navigasikan ke direktori yang ditentukan dan periksa berkas baru. Anda akan melihat bahwa ukurannya berkurang dibandingkan dengan dokumen asli, berkat pengaturan kompresi yang kami terapkan.

## Kesimpulan

Nah, itu dia! Anda telah berhasil mengatur tingkat kompresi untuk dokumen Word menggunakan Aspose.Words for .NET. Ini dapat mengurangi ukuran file secara signifikan dan meningkatkan kinerja saat bekerja dengan dokumen berukuran besar. Jangan lupa untuk menjelajahi tingkat kompresi lainnya untuk menemukan keseimbangan terbaik antara ukuran file dan kinerja sesuai kebutuhan Anda.

Jika Anda memiliki pertanyaan atau mengalami masalah, lihat [Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/) atau hubungi mereka [Forum Dukungan](https://forum.aspose.com/c/words/8).

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?

Aspose.Words untuk .NET adalah pustaka manipulasi dokumen canggih yang memungkinkan pengembang untuk membuat, mengedit, mengonversi, dan mencetak dokumen Word secara terprogram menggunakan .NET.

### Bagaimana cara menginstal Aspose.Words untuk .NET?

Anda dapat menginstal Aspose.Words untuk .NET melalui NuGet Package Manager di Visual Studio. Cukup cari "Aspose.Words" dan instal.

### Apa saja tingkat kompresi yang tersedia?

Aspose.Words untuk .NET menyediakan beberapa tingkat kompresi termasuk Normal, Maksimum, Cepat, dan SuperCepat. Setiap tingkat menawarkan keseimbangan yang berbeda antara ukuran file dan kecepatan pemrosesan.

### Bisakah saya menerapkan kompresi ke format dokumen lain?

Ya, Aspose.Words untuk .NET mendukung kompresi untuk berbagai format dokumen termasuk DOCX, PDF, dan lainnya.

### Di mana saya bisa mendapatkan dukungan jika saya mengalami masalah?

Anda bisa mendapatkan dukungan dari komunitas Aspose dengan mengunjungi [Forum Dukungan](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}