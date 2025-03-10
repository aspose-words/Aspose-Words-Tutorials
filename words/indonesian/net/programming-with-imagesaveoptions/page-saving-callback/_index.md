---
title: Panggilan Balik Penyimpanan Halaman
linktitle: Panggilan Balik Penyimpanan Halaman
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyimpan setiap halaman dokumen Word sebagai gambar PNG terpisah menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah terperinci kami.
weight: 10
url: /id/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Panggilan Balik Penyimpanan Halaman

## Perkenalan

Hai! Pernahkah Anda merasa perlu menyimpan setiap halaman dokumen Word sebagai gambar terpisah? Mungkin Anda ingin membagi laporan besar menjadi visual yang mudah dipahami, atau mungkin Anda perlu membuat gambar mini untuk pratinjau. Apa pun alasan Anda, menggunakan Aspose.Words untuk .NET membuat tugas ini mudah. Dalam panduan ini, kami akan memandu Anda melalui proses pengaturan panggilan balik penyimpanan halaman untuk menyimpan setiap halaman dokumen sebagai gambar PNG individual. Mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  Aspose.Words untuk .NET: Jika Anda belum melakukannya, unduh dan instal dari[Di Sini](https://releases.aspose.com/words/net/).
2. Visual Studio: Versi mana pun seharusnya berfungsi, tetapi saya akan menggunakan Visual Studio 2019 untuk panduan ini.
3. Pengetahuan Dasar C#: Anda memerlukan pemahaman dasar tentang C# untuk mengikutinya.

## Mengimpor Ruang Nama

Pertama, kita perlu mengimpor namespace yang diperlukan. Ini membantu kita mengakses kelas dan metode yang diperlukan tanpa mengetik namespace lengkap setiap saat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Baiklah, mari kita mulai dengan menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Word masukan Anda berada dan di mana gambar keluaran akan disimpan.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Muat Dokumen Anda

Selanjutnya, kita akan memuat dokumen yang ingin Anda proses. Pastikan dokumen Anda ("Rendering.docx") berada di direktori yang ditentukan.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Langkah 3: Konfigurasikan Opsi Penyimpanan Gambar

Kita perlu mengonfigurasi opsi untuk menyimpan gambar. Dalam kasus ini, kita menyimpan halaman sebagai file PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Di Sini,`PageSet` menentukan rentang halaman untuk disimpan, dan`PageSavingCallback` menunjuk ke kelas panggilan balik kustom kita.

## Langkah 4: Terapkan Panggilan Balik Penyimpanan Halaman

Sekarang, mari kita terapkan kelas panggilan balik yang menangani bagaimana setiap halaman disimpan.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Kelas ini mengimplementasikan`IPageSavingCallback` antarmuka, dan dalam`PageSaving` metode ini, kami mendefinisikan pola penamaan untuk setiap halaman yang disimpan.

## Langkah 5: Simpan Dokumen sebagai Gambar

Terakhir, kami menyimpan dokumen menggunakan opsi yang dikonfigurasi.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil menyiapkan panggilan balik penyimpanan halaman untuk menyimpan setiap halaman dokumen Word sebagai gambar PNG terpisah menggunakan Aspose.Words untuk .NET. Teknik ini sangat berguna untuk berbagai aplikasi, mulai dari membuat pratinjau halaman hingga membuat gambar halaman individual untuk laporan. 

Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyimpan halaman dalam format selain PNG?  
 Ya, Anda dapat menyimpan halaman dalam format berbeda seperti JPEG, BMP, dan TIFF dengan mengubah`SaveFormat` di dalam`ImageSaveOptions`.

### Bagaimana jika saya hanya ingin menyimpan halaman tertentu?  
 Anda dapat menentukan halaman yang ingin Anda simpan dengan menyesuaikan`PageSet` parameter dalam`ImageSaveOptions`.

### Apakah mungkin untuk menyesuaikan kualitas gambar?  
 Tentu saja! Anda dapat mengatur properti seperti`ImageSaveOptions.JpegQuality` untuk mengontrol kualitas gambar keluaran.

### Bagaimana saya dapat menangani dokumen besar secara efisien?  
Untuk dokumen besar, pertimbangkan untuk memproses halaman secara bertahap untuk mengelola penggunaan memori secara efektif.

### Di mana saya dapat menemukan informasi lebih lanjut tentang Aspose.Words untuk .NET?  
 Lihat di sini[dokumentasi](https://reference.aspose.com/words/net/) untuk panduan dan contoh yang lengkap.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
