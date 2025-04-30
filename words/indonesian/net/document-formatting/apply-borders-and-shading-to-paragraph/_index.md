---
"description": "Terapkan batas dan bayangan pada paragraf dalam dokumen Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk menyempurnakan format dokumen Anda."
"linktitle": "Terapkan Batas dan Bayangan ke Paragraf di Dokumen Word"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Terapkan Batas dan Bayangan ke Paragraf di Dokumen Word"
"url": "/id/net/document-formatting/apply-borders-and-shading-to-paragraph/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Terapkan Batas dan Bayangan ke Paragraf di Dokumen Word

## Perkenalan

Hai, pernahkah Anda bertanya-tanya bagaimana cara membuat dokumen Word Anda menonjol dengan beberapa bingkai dan bayangan yang cantik? Nah, Anda berada di tempat yang tepat! Hari ini, kita akan menyelami dunia Aspose.Words untuk .NET untuk mempercantik paragraf kita. Bayangkan dokumen Anda tampak ramping seperti karya desainer profesional hanya dengan beberapa baris kode. Siap untuk memulai? Ayo!

## Prasyarat

Sebelum kita mulai dan mulai membuat kode, mari kita pastikan kita memiliki semua yang kita butuhkan. Berikut daftar periksa singkatnya:

- Aspose.Words untuk .NET: Anda perlu menginstal pustaka ini. Anda dapat mengunduhnya dari [Situs web Aspose](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Visual Studio atau IDE lain yang mendukung .NET.
- Pengetahuan Dasar C#: Cukup untuk memahami dan mengubah cuplikan kode.
- Lisensi yang Sah: Baik [lisensi sementara](https://purchase.aspose.com/temporary-license/) atau yang dibeli dari [Asumsikan](https://purchase.aspose.com/buy).

## Mengimpor Ruang Nama

Sebelum memulai kode, kita perlu memastikan bahwa kita telah mengimpor namespace yang diperlukan ke dalam proyek kita. Ini membuat semua fitur menarik Aspose.Words dapat diakses oleh kita.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

Sekarang, mari kita uraikan prosesnya menjadi beberapa langkah kecil. Setiap langkah akan memiliki judul dan penjelasan terperinci. Siap? Ayo mulai!

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama-tama, kita perlu tempat untuk menyimpan dokumen yang diformat dengan indah. Mari kita atur jalur ke direktori dokumen Anda.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Direktori ini adalah tempat dokumen akhir Anda akan disimpan. Ganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya di mesin Anda.

## Langkah 2: Buat Dokumen Baru dan DocumentBuilder

Selanjutnya, kita perlu membuat dokumen baru dan `DocumentBuilder` objek. Itu `DocumentBuilder` adalah tongkat ajaib yang memungkinkan kita memanipulasi dokumen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Itu `Document` objek mewakili seluruh dokumen Word kita, dan `DocumentBuilder` membantu kami menambahkan dan memformat konten.

## Langkah 3: Tentukan Batas Paragraf

Sekarang, mari tambahkan beberapa bingkai bergaya ke paragraf kita. Kita akan menentukan jarak dari teks dan mengatur gaya bingkai yang berbeda.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

Di sini, kami menetapkan jarak 20 poin antara teks dan batas. Batas di semua sisi (kiri, kanan, atas, bawah) ditetapkan menjadi garis ganda. Menarik, bukan?

## Langkah 4: Terapkan Bayangan pada Paragraf

Batasan itu bagus, tetapi mari kita tingkatkan dengan beberapa bayangan. Kita akan menggunakan pola silang diagonal dengan campuran warna untuk membuat paragraf kita menonjol.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

Pada langkah ini, kami menerapkan tekstur silang diagonal dengan warna koral muda sebagai warna latar belakang dan salmon muda sebagai warna latar depan. Ini seperti mendandani paragraf Anda dengan pakaian desainer!

## Langkah 5: Tambahkan Teks ke Paragraf

Apa gunanya paragraf tanpa teks? Mari tambahkan contoh kalimat untuk melihat formatnya.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

Baris ini menyisipkan teks kita ke dalam dokumen. Sederhana, tetapi sekarang dibungkus dalam bingkai bergaya dan latar belakang berbayang.

## Langkah 6: Simpan Dokumen

Akhirnya, saatnya menyimpan pekerjaan kita. Mari kita simpan dokumen ke direktori yang ditentukan dengan nama yang deskriptif.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

Ini menyimpan dokumen kita dengan nama `DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` di direktori yang kita tentukan sebelumnya.

## Kesimpulan

Nah, itu dia! Hanya dengan beberapa baris kode, kami telah mengubah paragraf biasa menjadi konten yang menarik secara visual. Aspose.Words untuk .NET memudahkan Anda untuk menambahkan format yang tampak profesional ke dokumen Anda. Baik Anda sedang mempersiapkan laporan, surat, atau dokumen apa pun, trik ini akan membantu Anda memberikan kesan yang baik. Jadi, silakan, cobalah, dan lihat dokumen Anda menjadi lebih hidup!

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan gaya garis yang berbeda untuk setiap batas?  
Tentu saja! Aspose.Words untuk .NET memungkinkan Anda untuk menyesuaikan setiap border secara individual. Cukup atur `LineStyle` untuk setiap jenis perbatasan seperti yang ditunjukkan dalam panduan.

### Tekstur bayangan apa lagi yang tersedia?  
Ada beberapa tekstur yang dapat Anda gunakan, seperti solid, garis horizontal, garis vertikal, dan banyak lagi. Periksa [Dokumentasi Aspose](https://reference.aspose.com/words/net/) untuk daftar lengkap.

### Bagaimana cara mengubah warna batas?  
Anda dapat mengatur warna batas menggunakan `Color` properti untuk setiap perbatasan. Misalnya, `borders[BorderType.Left].Color = Color.Red;`.

### Apakah mungkin untuk menerapkan batas dan bayangan pada bagian teks tertentu?  
Ya, Anda dapat menerapkan batas dan bayangan ke rangkaian teks tertentu menggunakan `Run` objek dalam `DocumentBuilder`.

### Bisakah saya mengotomatiskan proses ini untuk beberapa paragraf?  
Tentu saja! Anda dapat mengulang paragraf dan menerapkan pengaturan batas dan bayangan yang sama secara terprogram.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}