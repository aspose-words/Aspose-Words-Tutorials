---
"description": "Pelajari cara menguasai pemformatan daftar bertingkat dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah kami. Sempurnakan struktur dokumen dengan mudah."
"linktitle": "Pemformatan Daftar Multilevel Dalam Dokumen Word"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Pemformatan Daftar Multilevel Dalam Dokumen Word"
"url": "/id/net/document-formatting/multilevel-list-formatting/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Pemformatan Daftar Multilevel Dalam Dokumen Word

## Perkenalan

Jika Anda seorang pengembang yang ingin mengotomatiskan pembuatan dan pemformatan dokumen Word, Aspose.Words untuk .NET adalah pengubah permainan. Hari ini, kita akan membahas cara menguasai pemformatan daftar bertingkat menggunakan pustaka yang canggih ini. Baik Anda membuat dokumen terstruktur, menguraikan laporan, atau membuat dokumentasi teknis, daftar bertingkat dapat meningkatkan keterbacaan dan pengaturan konten Anda.

## Prasyarat

Sebelum kita masuk ke detail yang lebih mendalam, mari pastikan Anda memiliki semua yang dibutuhkan untuk mengikuti tutorial ini.

1. Lingkungan Pengembangan: Pastikan Anda telah menyiapkan lingkungan pengembangan. Visual Studio adalah pilihan yang tepat.
2. Aspose.Words untuk .NET: Unduh dan instal pustaka Aspose.Words untuk .NET. Anda bisa mendapatkannya [Di Sini](https://releases.aspose.com/words/net/).
3. Lisensi: Dapatkan lisensi sementara jika Anda tidak memiliki lisensi lengkap. Dapatkan lisensi tersebut [Di Sini](https://purchase.aspose.com/temporary-license/).
4. Pengetahuan Dasar C#: Keakraban dengan C# dan kerangka kerja .NET akan bermanfaat.

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words for .NET dalam proyek Anda, Anda perlu mengimpor namespace yang diperlukan. Berikut cara melakukannya:

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

## Langkah 1: Inisialisasi Dokumen dan Pembuat Anda

Pertama-tama, mari kita buat dokumen Word baru dan inisialisasi DocumentBuilder. Kelas DocumentBuilder menyediakan metode untuk memasukkan konten ke dalam dokumen.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Terapkan Penomoran Default

Untuk memulai dengan daftar bernomor, Anda menggunakan `ApplyNumberDefault` metode. Ini mengatur format daftar bernomor default.

```csharp
builder.ListFormat.ApplyNumberDefault();
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

Pada baris-baris ini, `ApplyNumberDefault` memulai daftar bernomor, dan `Writeln` menambahkan item ke daftar.

## Langkah 3: Indentasi untuk Sublevel

Selanjutnya, untuk membuat sublevel dalam daftar Anda, Anda menggunakan `ListIndent` metode. Metode ini membuat indentasi item daftar, menjadikannya sublevel dari item sebelumnya.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.1");
builder.Writeln("Item 2.2");
```

Potongan kode ini membuat indentasi item, sehingga menciptakan daftar tingkat kedua.

## Langkah 4: Indentasi Lebih Lanjut untuk Tingkat yang Lebih Dalam

Anda dapat terus membuat indentasi untuk membuat level yang lebih dalam dalam daftar Anda. Di sini, kita akan membuat level ketiga.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.2.1");
builder.Writeln("Item 2.2.2");
```

Sekarang Anda memiliki daftar tingkat ketiga di bawah "Item 2.2".

## Langkah 5: Outdent untuk Kembali ke Tingkat yang Lebih Tinggi

Untuk kembali ke level yang lebih tinggi, gunakan `ListOutdent` metode. Ini akan memindahkan item kembali ke level daftar sebelumnya.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 2.3");
```

Ini membawa "Item 2.3" kembali ke tingkat kedua.

## Langkah 6: Hapus Penomoran

Setelah selesai dengan daftar Anda, Anda dapat menghapus penomoran untuk melanjutkan dengan teks biasa atau jenis pemformatan lainnya.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 3");
builder.ListFormat.RemoveNumbers();
```

Potongan kode ini melengkapi daftar dan menghentikan penomoran.

## Langkah 7: Simpan Dokumen Anda

Terakhir, simpan dokumen ke direktori yang Anda inginkan.

```csharp
doc.Save(dataDir + "DocumentFormatting.MultilevelListFormatting.docx");
```

Ini menyimpan dokumen Anda yang diformat indah dengan daftar bertingkat.

## Kesimpulan

Nah, itu dia! Anda telah berhasil membuat daftar bertingkat dalam dokumen Word menggunakan Aspose.Words for .NET. Pustaka canggih ini memungkinkan Anda mengotomatiskan tugas pemformatan dokumen yang rumit dengan mudah. Ingat, menguasai alat-alat ini tidak hanya menghemat waktu tetapi juga memastikan konsistensi dan profesionalisme dalam proses pembuatan dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan gaya penomoran daftar?
Ya, Aspose.Words untuk .NET memungkinkan Anda menyesuaikan gaya penomoran daftar menggunakan `ListTemplate` kelas.

### Bagaimana cara menambahkan poin-poin sebagai ganti angka?
Anda dapat menerapkan poin-poin dengan menggunakan `ApplyBulletDefault` metode sebagai pengganti `ApplyNumberDefault`.

### Apakah mungkin untuk melanjutkan penomoran dari daftar sebelumnya?
Ya, Anda dapat melanjutkan penomoran dengan menggunakan `ListFormat.List` properti untuk menautkan ke daftar yang ada.

### Bagaimana cara mengubah level indentasi secara dinamis?
Anda dapat mengubah tingkat indentasi secara dinamis dengan menggunakan `ListIndent` Dan `ListOutdent` metode sesuai kebutuhan.

### Bisakah saya membuat daftar bertingkat dalam format dokumen lain seperti PDF?
Ya, Aspose.Words mendukung penyimpanan dokumen dalam berbagai format termasuk PDF dengan tetap mempertahankan formatnya.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}