---
"description": "Pelajari cara menambahkan bentuk potongan sudut ke dokumen Word Anda menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah ini memastikan Anda dapat menyempurnakan dokumen Anda dengan mudah."
"linktitle": "Tambahkan Sudut yang Dipotong"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Tambahkan Sudut yang Dipotong"
"url": "/id/net/programming-with-shapes/add-corners-snipped/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Sudut yang Dipotong

## Perkenalan

Menambahkan bentuk khusus ke dokumen Word Anda dapat menjadi cara yang menyenangkan dan menarik secara visual untuk menyorot informasi penting atau menambahkan sedikit gaya pada konten Anda. Dalam tutorial ini, kita akan membahas cara menyisipkan bentuk "Corners Snipped" ke dalam dokumen Word Anda menggunakan Aspose.Words for .NET. Panduan ini akan memandu Anda melalui setiap langkah, memastikan Anda dapat dengan mudah menambahkan bentuk-bentuk ini dan menyesuaikan dokumen Anda seperti seorang profesional.

## Prasyarat

Sebelum kita masuk ke kode, mari pastikan Anda memiliki semua yang dibutuhkan untuk memulai:

1. Aspose.Words untuk .NET: Jika Anda belum melakukannya, unduh versi terbaru dari [Aspose merilis halaman](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Siapkan lingkungan pengembangan Anda. Visual Studio adalah pilihan yang populer, tetapi Anda dapat menggunakan IDE apa pun yang mendukung .NET.
3. Lisensi: Jika Anda hanya bereksperimen, Anda dapat menggunakan [uji coba gratis](https://releases.aspose.com/) atau dapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk membuka fungsionalitas penuh.
4. Pemahaman Dasar C#: Keakraban dengan pemrograman C# akan membantu Anda mengikuti contoh-contohnya.

## Mengimpor Ruang Nama

Sebelum kita dapat mulai bekerja dengan Aspose.Words untuk .NET, kita perlu mengimpor namespace yang diperlukan. Tambahkan namespace ini di bagian atas file C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Sekarang, mari kita uraikan proses penambahan bentuk "Corners Snipped" ke dalam beberapa langkah. Ikuti langkah-langkah ini dengan saksama untuk memastikan semuanya berjalan lancar.

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

Hal pertama yang perlu kita lakukan adalah membuat dokumen baru dan menginisialisasi `DocumentBuilder` objek. Pembuat ini akan membantu kita menambahkan konten ke dokumen kita.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Pada langkah ini, kita telah menyiapkan dokumen dan pembangun kita. Pikirkan `DocumentBuilder` sebagai pena digital Anda, siap untuk menulis dan menggambar di dokumen Word Anda.

## Langkah 2: Masukkan Bentuk Sudut yang Dipotong

Selanjutnya kita akan menggunakan `DocumentBuilder` untuk menyisipkan bentuk "Corners Snipped". Jenis bentuk ini telah ditetapkan sebelumnya di Aspose.Words dan dapat dengan mudah disisipkan dengan satu baris kode.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Di sini, kami menentukan jenis bentuk dan dimensinya (50x50). Bayangkan Anda menempelkan stiker sudut kecil yang dipotong sempurna pada dokumen Anda. 

## Langkah 3: Tentukan Opsi Penyimpanan dengan Kepatuhan

Sebelum menyimpan dokumen kita, kita perlu menentukan pilihan penyimpanan untuk memastikan dokumen kita mematuhi standar tertentu. Kita akan menggunakan `OoxmlSaveOptions` kelas untuk ini.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Pilihan penyimpanan ini memastikan bahwa dokumen kita mematuhi standar ISO/IEC 29500:2008, yang sangat penting untuk kompatibilitas dan keawetan dokumen.

## Langkah 4: Simpan Dokumen

Terakhir, kita simpan dokumen kita ke direktori yang ditentukan menggunakan opsi penyimpanan yang kita tentukan sebelumnya.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

Dan begitu saja, dokumen Anda kini berisi bentuk "Corners Snipped" khusus, yang disimpan dengan opsi kepatuhan yang diperlukan.

## Kesimpulan

Nah, itu dia! Menambahkan bentuk khusus ke dokumen Word Anda menggunakan Aspose.Words for .NET mudah dan dapat meningkatkan daya tarik visual dokumen Anda. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah menyisipkan bentuk "Corners Snipped" dan memastikan dokumen Anda memenuhi standar yang diperlukan. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan ukuran bentuk "Corners Snipped"?
Ya, Anda dapat menyesuaikan ukuran dengan mengubah dimensi di `InsertShape` metode.

### Apakah mungkin untuk menambahkan jenis bentuk lainnya?
Tentu saja! Aspose.Words mendukung berbagai bentuk. Ubah saja `ShapeType` sesuai bentuk yang Anda inginkan.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Words?
Meskipun Anda dapat menggunakan uji coba gratis atau lisensi sementara, lisensi penuh diperlukan untuk penggunaan tanpa batas.

### Bagaimana saya dapat menata bentuknya lebih lanjut?
Anda dapat menggunakan properti dan metode tambahan yang disediakan oleh Aspose.Words untuk menyesuaikan tampilan dan perilaku bentuk.

### Apakah Aspose.Words kompatibel dengan format lain?
Ya, Aspose.Words mendukung berbagai format dokumen termasuk DOCX, PDF, HTML, dan banyak lagi.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}