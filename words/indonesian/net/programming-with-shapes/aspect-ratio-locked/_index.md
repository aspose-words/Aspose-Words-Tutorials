---
title: Rasio Aspek Terkunci
linktitle: Rasio Aspek Terkunci
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengunci rasio aspek bentuk dalam dokumen Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah ini untuk menjaga gambar dan bentuk Anda tetap proporsional.
weight: 10
url: /id/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rasio Aspek Terkunci

## Perkenalan

Pernahkah Anda bertanya-tanya bagaimana cara mempertahankan proporsi gambar dan bentuk yang sempurna dalam dokumen Word Anda? Terkadang, Anda perlu memastikan bahwa gambar dan bentuk Anda tidak terdistorsi saat diubah ukurannya. Di sinilah penguncian rasio aspek menjadi berguna. Dalam tutorial ini, kita akan membahas cara mengatur rasio aspek untuk bentuk dalam dokumen Word menggunakan Aspose.Words untuk .NET. Kami akan menguraikannya menjadi langkah-langkah yang mudah diikuti, memastikan Anda dapat menerapkan keterampilan ini ke proyek Anda dengan percaya diri.

## Prasyarat

Sebelum kita menyelami kodenya, mari kita bahas apa saja yang Anda perlukan untuk memulai:

- Pustaka Aspose.Words untuk .NET: Anda perlu menginstal Aspose.Words untuk .NET. Jika Anda belum menginstalnya, Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Pastikan Anda telah menyiapkan lingkungan pengembangan .NET. Visual Studio merupakan pilihan yang populer.
- Pengetahuan Dasar C#: Sedikit pengetahuan tentang pemrograman C# akan sangat membantu.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Namespace ini akan memberi kita akses ke kelas dan metode yang kita perlukan untuk bekerja dengan dokumen dan bentuk Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

 Sebelum kita mulai memanipulasi bentuk, kita perlu menyiapkan direktori tempat dokumen kita akan disimpan. Demi kesederhanaan, kita akan menggunakan placeholder`YOUR DOCUMENT DIRECTORY`Ganti ini dengan jalur sebenarnya ke direktori dokumen Anda.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Buat Dokumen Baru

Selanjutnya, kita akan membuat dokumen Word baru menggunakan Aspose.Words. Dokumen ini akan berfungsi sebagai kanvas untuk menambahkan bentuk dan gambar.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Di sini, kita membuat sebuah instance dari`Document` kelas dan menggunakan`DocumentBuilder` untuk membantu kami membangun konten dokumen.

## Langkah 3: Masukkan Gambar

 Sekarang, mari masukkan gambar ke dalam dokumen kita. Kita akan menggunakan`InsertImage` metode dari`DocumentBuilder`kelas. Pastikan Anda memiliki gambar di direktori yang ditentukan.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Mengganti`dataDir + "Transparent background logo.png"` dengan jalur ke berkas gambar Anda.

## Langkah 4: Kunci Rasio Aspek

Setelah gambar dimasukkan, kita dapat mengunci rasio aspeknya. Mengunci rasio aspek memastikan bahwa proporsi gambar tetap konstan saat diubah ukurannya.

```csharp
shape.AspectRatioLocked = true;
```

 Pengaturan`AspectRatioLocked` ke`true` memastikan gambar mempertahankan rasio aspek aslinya.

## Langkah 5: Simpan Dokumen

Terakhir, kita akan menyimpan dokumen ke direktori yang ditentukan. Langkah ini akan menuliskan semua perubahan yang telah kita buat pada berkas dokumen.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Kesimpulan

Selamat! Anda telah berhasil mempelajari cara mengatur rasio aspek untuk bentuk dalam dokumen Word menggunakan Aspose.Words for .NET. Dengan mengikuti langkah-langkah ini, Anda dapat memastikan bahwa gambar dan bentuk Anda mempertahankan proporsinya, membuat dokumen Anda terlihat profesional dan menawan. Jangan ragu untuk bereksperimen dengan gambar dan bentuk yang berbeda untuk melihat bagaimana fitur penguncian rasio aspek bekerja dalam berbagai skenario.

## Pertanyaan yang Sering Diajukan

### Bisakah saya membuka kunci rasio aspek setelah menguncinya?
Ya, Anda dapat membuka kunci rasio aspek dengan mengatur`shape.AspectRatioLocked = false`.

### Apa yang terjadi jika saya mengubah ukuran gambar dengan rasio aspek terkunci?
Gambar akan diubah ukurannya secara proporsional, mempertahankan rasio lebar dan tinggi aslinya.

### Bisakah saya menerapkan ini ke bentuk lain selain gambar?
Tentu saja! Fitur penguncian rasio aspek dapat diterapkan pada bentuk apa pun, termasuk persegi panjang, lingkaran, dan lainnya.

### Apakah Aspose.Words untuk .NET kompatibel dengan .NET Core?
Ya, Aspose.Words untuk .NET mendukung .NET Framework dan .NET Core.

### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang Aspose.Words untuk .NET?
 Anda dapat menemukan dokumentasi yang lengkap[Di Sini](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
