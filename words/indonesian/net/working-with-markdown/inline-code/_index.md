---
title: Kode Sebaris
linktitle: Kode Sebaris
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menerapkan gaya kode sebaris dalam dokumen Word menggunakan Aspose.Words untuk .NET. Tutorial ini mencakup tanda petik tunggal dan ganda untuk pemformatan kode.
weight: 10
url: /id/net/working-with-markdown/inline-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kode Sebaris

## Perkenalan

Jika Anda sedang membuat atau memanipulasi dokumen Word secara terprogram, Anda mungkin perlu memformat teks agar menyerupai kode. Baik untuk dokumentasi atau cuplikan kode dalam laporan, Aspose.Words for .NET menyediakan cara yang kuat untuk menangani gaya teks. Dalam tutorial ini, kita akan fokus pada cara menerapkan gaya kode sebaris ke teks menggunakan Aspose.Words. Kita akan menjelajahi cara menentukan dan menggunakan gaya khusus untuk satu dan beberapa backtick, membuat segmen kode Anda menonjol dengan jelas dalam dokumen Anda.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  Pustaka Aspose.Words untuk .NET: Pastikan Anda telah menginstal Aspose.Words di lingkungan .NET Anda. Anda dapat mengunduhnya dari[Halaman rilis Aspose.Words untuk .NET](https://releases.aspose.com/words/net/).

2. Pengetahuan Dasar Pemrograman .NET: Panduan ini mengasumsikan Anda memiliki pemahaman dasar tentang pemrograman C# dan .NET.

3. Lingkungan Pengembangan: Anda harus menyiapkan lingkungan pengembangan .NET, seperti Visual Studio, tempat Anda dapat menulis dan mengeksekusi kode C#.

## Mengimpor Ruang Nama

Untuk mulai menggunakan Aspose.Words di proyek Anda, Anda perlu mengimpor namespace yang diperlukan. Berikut cara melakukannya:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Mari kita uraikan prosesnya menjadi beberapa langkah yang jelas:

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

 Pertama, Anda perlu membuat dokumen baru dan`DocumentBuilder` contoh.`DocumentBuilder`Kelas membantu Anda menambahkan konten dan memformatnya dalam dokumen Word.

```csharp
// Inisialisasi DocumentBuilder dengan Dokumen baru.
DocumentBuilder builder = new DocumentBuilder();
```

## Langkah 2: Tambahkan Gaya Kode Sebaris dengan Satu Backtick

Pada langkah ini, kita akan menentukan gaya untuk kode sebaris dengan satu tanda hubung terbalik. Gaya ini akan memformat teks agar tampak seperti kode sebaris.

### Tentukan Gaya

```csharp
// Tentukan gaya karakter baru untuk kode sebaris dengan satu tanda centang terbalik.
Style inlineCode1BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode");
inlineCode1BackTicks.Font.Name = "Courier New"; // Font khas untuk kode.
inlineCode1BackTicks.Font.Size = 10.5; // Ukuran font untuk kode sebaris.
inlineCode1BackTicks.Font.Color = System.Drawing.Color.Blue; // Kode warna teks.
inlineCode1BackTicks.Font.Bold = true; // Buat teks kode menjadi tebal.
```

### Terapkan Gaya

Sekarang, Anda dapat menerapkan gaya ini pada teks dalam dokumen Anda.

```csharp
// Gunakan DocumentBuilder untuk menyisipkan teks dengan gaya kode sebaris.
builder.Font.Style = inlineCode1BackTicks;
builder.Writeln("Text with InlineCode style with 1 backtick");
```

## Langkah 3: Tambahkan Gaya Kode Sebaris dengan Tiga Backticks

Berikutnya, kita akan mendefinisikan gaya untuk kode sebaris dengan tiga tanda centang terbalik, yang biasanya digunakan untuk blok kode multi-baris.

### Tentukan Gaya

```csharp
// Tentukan gaya karakter baru untuk kode sebaris dengan tiga tanda centang terbalik.
Style inlineCode3BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode.3");
inlineCode3BackTicks.Font.Name = "Courier New"; // Font yang konsisten untuk kode.
inlineCode3BackTicks.Font.Size = 10.5; // Ukuran font untuk blok kode.
inlineCode3BackTicks.Font.Color = System.Drawing.Color.Green; //Warna berbeda untuk visibilitas.
inlineCode3BackTicks.Font.Bold = true; // Cetak tebal untuk penekanan.
```

### Terapkan Gaya

Terapkan gaya ini ke teks untuk memformatnya sebagai blok kode multi-baris.

```csharp
// Terapkan gaya untuk blok kode.
builder.Font.Style = inlineCode3BackTicks;
builder.Writeln("Text with InlineCode style with 3 backticks");
```

## Kesimpulan

Memformat teks sebagai kode sebaris dalam dokumen Word menggunakan Aspose.Words untuk .NET mudah dilakukan setelah Anda mengetahui langkah-langkahnya. Dengan menentukan dan menerapkan gaya khusus dengan satu atau beberapa tanda petik terbalik, Anda dapat membuat cuplikan kode Anda menonjol dengan jelas. Metode ini sangat berguna untuk dokumentasi teknis atau dokumen apa pun yang sangat penting untuk keterbacaan kode.

Jangan ragu untuk bereksperimen dengan berbagai gaya dan opsi pemformatan agar sesuai dengan kebutuhan Anda. Aspose.Words menawarkan fleksibilitas yang luas, yang memungkinkan Anda untuk menyesuaikan tampilan dokumen Anda secara maksimal.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan font yang berbeda untuk gaya kode sebaris?
Ya, Anda dapat menggunakan font apa pun yang sesuai dengan kebutuhan Anda. Font seperti "Courier New" biasanya digunakan untuk kode karena sifatnya yang monospaced.

### Bagaimana cara mengubah warna teks kode sebaris?
 Anda dapat mengubah warna dengan mengatur`Font.Color` properti gaya untuk apa pun`System.Drawing.Color`.

### Bisakah saya menerapkan beberapa gaya pada teks yang sama?
Di Aspose.Words, Anda hanya dapat menerapkan satu gaya dalam satu waktu. Jika Anda perlu menggabungkan gaya, pertimbangkan untuk membuat gaya baru yang menggabungkan semua format yang diinginkan.

### Bagaimana cara menerapkan gaya ke teks yang ada dalam dokumen?
 Untuk menerapkan gaya pada teks yang ada, Anda perlu memilih teks terlebih dahulu lalu menerapkan gaya yang diinginkan menggunakan`Font.Style` milik.

### Dapatkah saya menggunakan Aspose.Words untuk format dokumen lain?
Aspose.Words dirancang khusus untuk dokumen Word. Untuk format lain, Anda mungkin perlu menggunakan pustaka yang berbeda atau mengonversi dokumen ke format yang kompatibel.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
