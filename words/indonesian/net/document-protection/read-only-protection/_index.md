---
"description": "Pelajari cara melindungi dokumen Word Anda dengan menerapkan perlindungan baca-saja menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami."
"linktitle": "Perlindungan Hanya Baca Dalam Dokumen Word"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Perlindungan Hanya Baca Dalam Dokumen Word"
"url": "/id/net/document-protection/read-only-protection/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Perlindungan Hanya Baca Dalam Dokumen Word

## Perkenalan

Dalam mengelola dokumen Word, ada kalanya Anda perlu membuatnya hanya-baca untuk melindungi isinya. Baik untuk berbagi informasi penting tanpa risiko penyuntingan yang tidak disengaja atau memastikan integritas dokumen hukum, perlindungan hanya-baca merupakan fitur yang berharga. Dalam tutorial ini, kita akan membahas cara menerapkan perlindungan hanya-baca dalam dokumen Word menggunakan Aspose.Words untuk .NET. Kami akan memandu Anda melalui setiap langkah secara terperinci dan menarik, memastikan Anda dapat mengikutinya dengan mudah.

## Prasyarat

Sebelum kita menyelami kodenya, ada beberapa prasyarat yang perlu Anda penuhi:

1. Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words untuk .NET. Anda dapat mengunduhnya dari [Aspose merilis halaman](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan dengan .NET yang terinstal. Visual Studio adalah pilihan yang tepat.
3. Pemahaman Dasar C#: Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang pemrograman C#.

## Mengimpor Ruang Nama

Pertama, mari kita pastikan namespace yang diperlukan telah diimpor. Ini penting karena memungkinkan kita mengakses kelas dan metode yang kita perlukan dari Aspose.Words untuk .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Siapkan Dokumen

Pada langkah ini, kita akan membuat dokumen baru dan pembuat dokumen. Ini menjadi dasar bagi operasi kita.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Tulis beberapa teks ke dokumen.
builder.Write("Open document as read-only");
```

Penjelasan:

- Kita mulai dengan menentukan jalur direktori tempat dokumen akan disimpan.
- Sebuah baru `Document` objek dibuat, dan `DocumentBuilder` dikaitkan dengannya.
- Dengan menggunakan pembangun, kami menambahkan baris teks sederhana ke dalam dokumen.

## Langkah 2: Tetapkan Kata Sandi Perlindungan Penulisan

Selanjutnya, kita perlu mengatur kata sandi untuk proteksi penulisan. Kata sandi ini dapat terdiri dari 15 karakter.

```csharp
// Masukkan kata sandi yang panjangnya hingga 15 karakter.
doc.WriteProtection.SetPassword("MyPassword");
```

Penjelasan:

- Itu `SetPassword` metode dipanggil pada `WriteProtection` milik dokumen.
- Kami menyediakan kata sandi ("MyPassword" dalam kasus ini) yang akan diperlukan untuk menghapus perlindungan.

## Langkah 3: Aktifkan Rekomendasi Hanya Baca

Pada langkah ini, kami menjadikan dokumen tersebut sebagai dokumen yang direkomendasikan untuk dibaca saja. Ini berarti saat dokumen dibuka, dokumen tersebut akan meminta pengguna untuk membukanya dalam mode baca saja.

```csharp
// Jadikan dokumen sebagai baca-saja yang direkomendasikan.
doc.WriteProtection.ReadOnlyRecommended = true;
```

Penjelasan:

- Itu `ReadOnlyRecommended` properti diatur ke `true`.
- Ini akan meminta pengguna untuk membuka dokumen dalam mode baca-saja, meskipun mereka dapat memilih untuk mengabaikan rekomendasi tersebut.

## Langkah 4: Terapkan Perlindungan Hanya Baca

Terakhir, kami menerapkan perlindungan hanya-baca pada dokumen. Langkah ini memberlakukan perlindungan.

```csharp
// Terapkan proteksi penulisan sebagai hanya-baca.
doc.Protect(ProtectionType.ReadOnly);
```

Penjelasan:

- Itu `Protect` metode dipanggil pada dokumen dengan `ProtectionType.ReadOnly` sebagai argumen.
- Metode ini menegakkan perlindungan baca-saja, mencegah modifikasi apa pun pada dokumen tanpa kata sandi.

## Langkah 5: Simpan Dokumen

Langkah terakhir adalah menyimpan dokumen dengan pengaturan perlindungan yang diterapkan.

```csharp
// Simpan dokumen yang dilindungi.
doc.Save(dataDir + "DocumentProtection.ReadOnlyProtection.docx");
```

Penjelasan:

- Itu `Save` Metode ini dipanggil pada dokumen, yang menentukan jalur dan nama file.
- Dokumen disimpan dengan perlindungan baca-saja.

## Kesimpulan

Nah, itu dia! Anda telah berhasil membuat dokumen Word yang dilindungi hak baca-saja menggunakan Aspose.Words untuk .NET. Fitur ini memastikan bahwa konten dokumen Anda tetap utuh dan tidak berubah, sehingga memberikan lapisan keamanan ekstra. Baik Anda berbagi informasi sensitif atau dokumen hukum, perlindungan hak baca-saja adalah alat yang wajib dimiliki dalam gudang manajemen dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memodifikasi, mengonversi, dan melindungi dokumen Word secara terprogram menggunakan C# atau bahasa .NET lainnya.

### Bisakah saya menghapus proteksi baca-saja dari sebuah dokumen?
Ya, Anda dapat menghapus perlindungan baca-saja dengan menggunakan `Unprotect` metode dan memberikan kata sandi yang benar.

### Apakah kata sandi yang ditetapkan dalam dokumen dienkripsi?
Ya, Aspose.Words mengenkripsi kata sandi untuk memastikan keamanan dokumen yang dilindungi.

### Dapatkah saya menerapkan jenis perlindungan lain menggunakan Aspose.Words untuk .NET?
Ya, Aspose.Words untuk .NET mendukung berbagai jenis perlindungan, termasuk hanya mengizinkan komentar, pengisian formulir, atau pelacakan perubahan.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?
Ya, Anda dapat mengunduh uji coba gratis dari [Aspose merilis halaman](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}