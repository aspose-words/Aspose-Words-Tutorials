---
"description": "Pelajari cara mengekspor dokumen Word ke Markdown dengan tabel yang selaras menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk tabel Markdown yang sempurna."
"linktitle": "Ekspor ke Markdown dengan Penyelarasan Konten Tabel"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Ekspor ke Markdown dengan Penyelarasan Konten Tabel"
"url": "/id/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ekspor ke Markdown dengan Penyelarasan Konten Tabel

## Perkenalan

Hai! Pernahkah Anda bertanya-tanya bagaimana cara mengekspor dokumen Word Anda ke format Markdown dengan tabel yang selaras sempurna? Apakah Anda seorang pengembang yang mengerjakan dokumentasi atau hanya seseorang yang menyukai Markdown, panduan ini cocok untuk Anda. Kami akan membahas seluk-beluk penggunaan Aspose.Words untuk .NET untuk mencapainya. Siap mengubah tabel Word Anda menjadi tabel Markdown yang selaras rapi? Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke kode, ada beberapa hal yang perlu Anda siapkan:

1. Pustaka Aspose.Words untuk .NET: Pastikan Anda memiliki pustaka Aspose.Words untuk .NET. Anda dapat mengunduhnya dari [Halaman Rilis Aspose](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan Anda. Visual Studio merupakan pilihan populer untuk pengembangan .NET.
3. Pengetahuan Dasar C#: Memahami C# sangat penting karena kita akan menulis kode dalam bahasa ini.
4. Contoh Dokumen Word: Miliki dokumen Word yang dapat Anda gunakan untuk pengujian.

## Mengimpor Ruang Nama

Sebelum kita mulai membuat kode, mari impor namespace yang diperlukan. Namespace ini akan memberi kita akses ke kelas dan metode Aspose.Words yang akan kita gunakan.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

Hal pertama yang harus kita lakukan adalah membuat dokumen Word baru dan menginisialisasinya `DocumentBuilder` objek untuk mulai membangun dokumen kita.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Buat dokumen baru.
Document doc = new Document();

// Inisialisasi DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Masukkan Sel dan Sejajarkan Konten

Selanjutnya, kita akan memasukkan beberapa sel ke dalam dokumen kita dan mengatur perataannya. Ini penting untuk memastikan bahwa ekspor Markdown mempertahankan perataan yang benar.

```csharp
// Sisipkan sel dan atur perataan ke kanan.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Sisipkan sel lain dan atur perataan ke tengah.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Langkah 3: Mengatur Penyelarasan Konten Tabel untuk Ekspor Markdown

Sekarang saatnya untuk mengkonfigurasi `MarkdownSaveOptions` untuk mengontrol penyelarasan konten tabel dalam file Markdown yang diekspor. Kami akan menyimpan dokumen dengan pengaturan penyelarasan yang berbeda untuk melihat cara kerjanya.

```csharp
// Buat objek MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Simpan dokumen dengan perataan kiri.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Ubah perataan ke kanan dan simpan.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Ubah perataan ke tengah dan simpan.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Langkah 4: Gunakan Penyelarasan Konten Tabel Otomatis

Itu `Auto` Opsi penyelarasan mengambil penyelarasan dari paragraf pertama di kolom tabel terkait. Ini berguna saat Anda memiliki penyelarasan campuran dalam satu tabel.

```csharp
// Atur perataan ke Otomatis.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Simpan dokumen dengan penyelarasan otomatis.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Kesimpulan

Nah, itu dia! Mengekspor dokumen Word ke Markdown dengan tabel yang disejajarkan menggunakan Aspose.Words untuk .NET sangat mudah jika Anda tahu cara melakukannya. Pustaka canggih ini memudahkan Anda mengontrol pemformatan dan penyelarasan tabel, memastikan dokumen Markdown Anda terlihat seperti yang Anda inginkan. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memodifikasi, mengonversi, dan mengekspor dokumen Word secara terprogram.

### Dapatkah saya mengatur perataan yang berbeda untuk kolom yang berbeda dalam tabel yang sama?
Ya, dengan menggunakan `Auto` opsi perataan, Anda dapat memiliki perataan berbeda berdasarkan paragraf pertama di setiap kolom.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Words untuk .NET?
Ya, Aspose.Words untuk .NET memerlukan lisensi untuk fungsionalitas penuh. Anda bisa mendapatkannya [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk evaluasi.

### Apakah mungkin untuk mengekspor elemen dokumen lain ke Markdown menggunakan Aspose.Words?
Ya, Aspose.Words mendukung ekspor berbagai elemen seperti judul, daftar, dan gambar ke format Markdown.

### Di mana saya bisa mendapatkan dukungan jika saya mengalami masalah?
Anda bisa mendapatkan dukungan dari [Forum Dukungan Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}