---
title: Sisipkan Gambar Mengambang Dalam Dokumen Word
linktitle: Sisipkan Gambar Mengambang Dalam Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyisipkan gambar mengambang dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah yang terperinci ini. Sempurna untuk menyempurnakan dokumen Anda.
weight: 10
url: /id/net/add-content-using-documentbuilder/insert-floating-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Gambar Mengambang Dalam Dokumen Word

## Perkenalan

Bayangkan membuat laporan atau proposal yang memukau dengan gambar yang diposisikan dengan sempurna untuk melengkapi teks Anda. Dengan Aspose.Words untuk .NET, Anda dapat melakukannya dengan mudah. Pustaka ini menyediakan fitur canggih untuk manipulasi dokumen, menjadikannya solusi yang tepat bagi para pengembang. Dalam tutorial ini, kita akan fokus pada penyisipan gambar mengambang menggunakan kelas DocumentBuilder. Baik Anda pengembang berpengalaman atau baru memulai, panduan ini akan memandu Anda melalui setiap langkah.

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang dibutuhkan untuk memulai:

1.  Aspose.Words untuk .NET: Anda dapat mengunduh pustaka dari[Aspose merilis halaman](https://releases.aspose.com/words/net/).
2. Visual Studio: Versi apa pun yang mendukung pengembangan .NET.
3. Pengetahuan Dasar C#: Memahami dasar-dasar pemrograman C# akan sangat membantu.
4. Berkas Gambar: Berkas gambar yang ingin Anda sisipkan, seperti logo atau gambar.

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words dalam proyek Anda, Anda perlu mengimpor namespace yang diperlukan. Hal ini dilakukan dengan menambahkan baris berikut di bagian atas berkas C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Dengan prasyarat dan namespace yang tersedia, kita siap memulai tutorial kita.

Mari kita uraikan proses penyisipan gambar mengambang ke dalam dokumen Word menjadi beberapa langkah yang mudah dilakukan. Setiap langkah akan dijelaskan secara terperinci untuk memastikan Anda dapat mengikutinya tanpa hambatan apa pun.

## Langkah 1: Siapkan Proyek Anda

Pertama, buat proyek C# baru di Visual Studio. Anda dapat memilih Aplikasi Konsol untuk mempermudah.

1. Buka Visual Studio dan buat proyek baru.
2. Pilih "Aplikasi Konsol (.NET Core)" dan klik "Berikutnya."
3. Beri nama proyek Anda dan pilih lokasi untuk menyimpannya. Klik "Buat".
4. Instal Aspose.Words untuk .NET melalui NuGet Package Manager. Klik kanan pada proyek Anda di Solution Explorer, pilih "Manage NuGet Packages," dan cari "Aspose.Words." Instal versi terbaru.

## Langkah 2: Inisialisasi Dokumen dan DocumentBuilder

Sekarang proyek Anda sudah disiapkan, mari inisialisasi objek Document dan DocumentBuilder.

1.  Buat contoh baru dari`Document` kelas:

```csharp
Document doc = new Document();
```

2. Inisialisasi objek DocumentBuilder:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Itu`Document` objek mewakili dokumen Word, dan`DocumentBuilder` membantu dalam menambahkan konten ke dalamnya.

## Langkah 3: Tentukan Jalur Gambar

Selanjutnya, tentukan jalur ke berkas gambar Anda. Pastikan gambar Anda dapat diakses dari direktori proyek Anda.

Tentukan direktori gambar dan nama berkas gambar:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya tempat gambar Anda disimpan.

## Langkah 4: Masukkan Gambar Mengambang

Setelah semuanya siap, mari masukkan gambar mengambang ke dalam dokumen.

 Gunakan`InsertImage` metode dari`DocumentBuilder` kelas untuk menyisipkan gambar:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Berikut ini arti setiap parameter:
- `imagePath`: Jalur ke berkas gambar Anda.
- `RelativeHorizontalPosition.Margin`: Posisi horizontal relatif terhadap margin.
- `100`: Jarak horizontal dari margin (dalam poin).
- `RelativeVerticalPosition.Margin`: Posisi vertikal relatif terhadap margin.
- `100`: Jarak vertikal dari margin (dalam poin).
- `200`: Lebar gambar (dalam poin).
- `100`: Tinggi gambar (dalam poin).
- `WrapType.Square`: Gaya pembungkusan teks di sekitar gambar.

## Langkah 5: Simpan Dokumen

Terakhir, simpan dokumen ke lokasi yang Anda inginkan.

1. Tentukan jalur berkas keluaran:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Simpan dokumen:

```csharp
doc.Save(outputPath);
```

Dokumen Word Anda dengan gambar mengambang sekarang sudah siap!

## Kesimpulan

Memasukkan gambar mengambang ke dalam dokumen Word menggunakan Aspose.Words untuk .NET merupakan proses yang mudah jika dipecah menjadi beberapa langkah yang mudah dikelola. Dengan mengikuti panduan ini, Anda dapat menambahkan gambar yang tampak profesional ke dokumen Anda, sehingga meningkatkan daya tarik visualnya. Aspose.Words menyediakan API yang tangguh yang memudahkan manipulasi dokumen, baik saat Anda mengerjakan laporan, proposal, atau jenis dokumen lainnya.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyisipkan beberapa gambar menggunakan Aspose.Words untuk .NET?

 Ya, Anda dapat memasukkan beberapa gambar dengan mengulangi`InsertImage` metode untuk setiap gambar dengan parameter yang diinginkan.

### Bagaimana cara mengubah posisi gambar?

 Anda dapat menyesuaikan`RelativeHorizontalPosition`, `RelativeVerticalPosition`, dan parameter offset untuk memposisikan gambar sesuai kebutuhan.

### Jenis bungkus apa lagi yang tersedia untuk gambar?

 Aspose.Words mendukung berbagai jenis pembungkus seperti`Inline`, `TopBottom`, `Tight`, `Through`, dan banyak lagi. Anda dapat memilih salah satu yang paling sesuai dengan tata letak dokumen Anda.

### Bisakah saya menggunakan format gambar yang berbeda?

Ya, Aspose.Words mendukung berbagai format gambar termasuk JPEG, PNG, BMP, dan GIF.

### Bagaimana cara mendapatkan uji coba gratis Aspose.Words untuk .NET?

 Anda bisa mendapatkan uji coba gratis dari[Halaman uji coba gratis Aspose](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
