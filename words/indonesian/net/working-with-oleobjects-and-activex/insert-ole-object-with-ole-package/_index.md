---
title: Masukkan Objek Ole Di Word Dengan Paket Ole
linktitle: Masukkan Objek Ole Di Word Dengan Paket Ole
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyisipkan objek OLE dalam dokumen Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah terperinci kami untuk menyematkan file dengan mudah.
weight: 10
url: /id/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Objek Ole Di Word Dengan Paket Ole

## Perkenalan

Jika Anda pernah ingin menyematkan berkas ke dalam dokumen Word, Anda berada di tempat yang tepat. Baik itu berkas ZIP, lembar Excel, atau jenis berkas lainnya, menyematkannya langsung ke dalam dokumen Word Anda bisa sangat berguna. Anggap saja seperti memiliki kompartemen rahasia di dalam dokumen Anda tempat Anda dapat menyimpan berbagai harta karun. Dan hari ini, kita akan membahas cara melakukannya menggunakan Aspose.Words untuk .NET. Siap menjadi ahli Word? Mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Aspose.Words untuk .NET: Jika Anda belum melakukannya, unduh dari[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau lingkungan pengembangan .NET lainnya.
3. Pemahaman Dasar tentang C#: Anda tidak perlu menjadi seorang ahli, tetapi mengetahui cara menggunakan C# akan membantu.
4. Direktori Dokumen: Folder tempat Anda dapat menyimpan dan mengambil dokumen.

## Mengimpor Ruang Nama

Pertama-tama, mari kita atur namespace kita. Anda perlu menyertakan namespace berikut dalam proyek Anda:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Mari kita uraikan ini ke dalam langkah-langkah kecil, sehingga mudah diikuti.

## Langkah 1: Siapkan Dokumen Anda

Bayangkan Anda seorang seniman dengan kanvas kosong. Pertama, kita perlu kanvas kosong, yaitu dokumen Word. Berikut cara mengaturnya:

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Kode ini menginisialisasi dokumen Word baru dan menyiapkan DocumentBuilder, yang akan kita gunakan untuk memasukkan konten ke dalam dokumen kita.

## Langkah 2: Baca Objek Ole Anda

Selanjutnya, mari kita baca berkas yang ingin Anda sisipkan. Bayangkan ini seperti mengambil harta karun yang ingin Anda sembunyikan di kompartemen rahasia Anda:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Baris ini membaca semua byte dari berkas ZIP Anda dan menyimpannya dalam array byte.

## Langkah 3: Masukkan Objek Ole

Sekarang tibalah bagian ajaibnya. Kita akan menyematkan berkas tersebut ke dalam dokumen Word kita:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Di sini, kita membuat aliran memori dari array byte dan menggunakan`InsertOleObject` metode untuk menanamkannya ke dalam dokumen. Kami juga menetapkan nama file dan nama tampilan untuk objek yang disematkan.

## Langkah 4: Simpan Dokumen Anda

Terakhir, mari kita simpan karya agung kita:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Ini akan menyimpan dokumen dengan berkas yang tertanam dalam direktori yang ditentukan.

## Kesimpulan

Nah, itu dia! Anda telah berhasil menyematkan objek OLE ke dalam dokumen Word menggunakan Aspose.Words for .NET. Ini seperti menambahkan permata tersembunyi di dalam dokumen Anda yang dapat disingkapkan kapan saja. Teknik ini dapat sangat berguna untuk berbagai aplikasi, mulai dari dokumentasi teknis hingga laporan dinamis. 

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyematkan tipe berkas lain menggunakan metode ini?
Ya, Anda dapat menyematkan berbagai jenis file seperti lembar Excel, PDF, dan gambar.

### Apakah saya memerlukan lisensi untuk Aspose.Words?
 Ya, Anda memerlukan lisensi yang valid. Anda bisa mendapatkannya[lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk evaluasi.

### Bagaimana saya dapat menyesuaikan nama tampilan objek OLE?
 Anda dapat mengatur`DisplayName` milik`OlePackage` untuk menyesuaikannya.

### Apakah Aspose.Words kompatibel dengan .NET Core?
Ya, Aspose.Words mendukung .NET Framework dan .NET Core.

### Bisakah saya mengedit objek OLE yang tertanam dalam dokumen Word?
Tidak, Anda tidak dapat mengedit objek OLE secara langsung di Word. Anda perlu membukanya di aplikasi aslinya.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
