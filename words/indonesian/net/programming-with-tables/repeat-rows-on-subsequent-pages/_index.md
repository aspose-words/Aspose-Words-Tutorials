---
"description": "Pelajari cara membuat dokumen Word dengan baris tajuk tabel berulang menggunakan Aspose.Words untuk .NET. Ikuti panduan ini untuk memastikan dokumen yang profesional dan bermutu."
"linktitle": "Ulangi Baris Pada Halaman Berikutnya"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Ulangi Baris Pada Halaman Berikutnya"
"url": "/id/net/programming-with-tables/repeat-rows-on-subsequent-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ulangi Baris Pada Halaman Berikutnya

## Perkenalan

Membuat dokumen Word secara terprogram bisa menjadi tugas yang berat, terutama saat Anda perlu mempertahankan format di beberapa halaman. Pernahkah Anda mencoba membuat tabel di Word, hanya untuk menyadari bahwa baris tajuk Anda tidak berulang di halaman berikutnya? Jangan khawatir! Dengan Aspose.Words untuk .NET, Anda dapat dengan mudah memastikan bahwa tajuk tabel Anda berulang di setiap halaman, memberikan tampilan yang profesional dan apik pada dokumen Anda. Dalam tutorial ini, kami akan memandu Anda melalui langkah-langkah untuk mencapainya menggunakan contoh kode sederhana dan penjelasan terperinci. Mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Aspose.Words untuk .NET: Anda dapat mengunduhnya [Di Sini](https://releases.aspose.com/words/net/).
2. .NET Framework terinstal di komputer Anda.
3. Visual Studio atau IDE lain yang mendukung pengembangan .NET.
4. Pemahaman dasar tentang pemrograman C#.

Pastikan Anda telah menginstal Aspose.Words untuk .NET dan menyiapkan lingkungan pengembangan Anda sebelum melanjutkan.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan dalam proyek Anda. Tambahkan perintah berikut di bagian atas file C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ruang nama ini menyertakan kelas dan metode yang diperlukan untuk memanipulasi dokumen dan tabel Word.

## Langkah 1: Inisialisasi Dokumen

Pertama, mari kita membuat dokumen Word baru dan `DocumentBuilder` untuk membuat tabel kita.

```csharp
// Jalur ke direktori dokumen Anda 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Kode ini menginisialisasi dokumen baru dan `DocumentBuilder` objek, yang membantu dalam membangun struktur dokumen.

## Langkah 2: Mulai Tabel dan Tentukan Baris Header

Berikutnya, kita akan memulai tabel dan menentukan baris tajuk yang ingin kita ulangi pada halaman berikutnya.

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

Di sini, kita memulai tabel baru, mengatur `HeadingFormat` properti untuk `true` untuk menunjukkan bahwa baris adalah tajuk, dan menentukan perataan dan lebar sel.

## Langkah 3: Tambahkan Baris Data ke Tabel

Sekarang, kita akan menambahkan beberapa baris data ke tabel kita. Baris-baris ini tidak akan diulang di halaman berikutnya.

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

Loop ini memasukkan 50 baris data ke dalam tabel, dengan dua kolom di setiap baris. `HeadingFormat` diatur untuk `false` untuk baris-baris ini, karena baris-baris tersebut bukan baris tajuk.

## Langkah 4: Simpan Dokumen

Terakhir, kami menyimpan dokumen ke direktori yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Ini akan menyimpan dokumen dengan nama yang ditentukan dalam direktori dokumen Anda.

## Kesimpulan

Nah, itu dia! Hanya dengan beberapa baris kode, Anda dapat membuat dokumen Word dengan tabel yang memiliki baris tajuk berulang pada halaman berikutnya menggunakan Aspose.Words untuk .NET. Ini tidak hanya meningkatkan keterbacaan dokumen Anda, tetapi juga memastikan tampilan yang konsisten dan profesional. Sekarang, lanjutkan dan coba ini di proyek Anda!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan baris header lebih lanjut?
Ya, Anda dapat menerapkan pemformatan tambahan ke baris header dengan mengubah properti `ParagraphFormat`Bahasa Indonesia: `RowFormat`, Dan `CellFormat`.

### Apakah mungkin untuk menambahkan lebih banyak kolom pada tabel?
Tentu saja! Anda dapat menambahkan kolom sebanyak yang diperlukan dengan memasukkan lebih banyak sel di dalam `InsertCell` metode.

### Bagaimana cara membuat baris lainnya berulang pada halaman berikutnya?
Untuk membuat baris apa pun berulang, atur `RowFormat.HeadingFormat` properti untuk `true` untuk baris spesifik tersebut.

### Bisakah saya menggunakan metode ini untuk tabel yang ada dalam dokumen?
Ya, Anda dapat mengubah tabel yang ada dengan mengaksesnya melalui `Document` objek dan menerapkan pemformatan yang serupa.

### Apa saja pilihan pemformatan tabel lain yang tersedia di Aspose.Words untuk .NET?
Aspose.Words untuk .NET menawarkan berbagai pilihan pemformatan tabel, termasuk penggabungan sel, pengaturan batas, dan perataan tabel. Lihat [dokumentasi](https://reference.aspose.com/words/net/) untuk lebih jelasnya.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}