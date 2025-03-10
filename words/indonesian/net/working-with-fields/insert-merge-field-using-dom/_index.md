---
title: Sisipkan Bidang Gabungan Menggunakan DOM
linktitle: Sisipkan Bidang Gabungan Menggunakan DOM
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyisipkan dan mengonfigurasi bidang gabungan dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan tutorial langkah demi langkah yang komprehensif ini.
weight: 10
url: /id/net/working-with-fields/insert-merge-field-using-dom/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Bidang Gabungan Menggunakan DOM

## Perkenalan

Jika Anda bekerja dengan pemrosesan dokumen di .NET, Anda mungkin pernah menemukan Aspose.Words. Pustaka canggih ini menawarkan beragam fitur untuk memanipulasi dokumen Word secara terprogram. Dalam tutorial ini, kami akan fokus pada satu fitur khusus: memasukkan kolom gabungan menggunakan Document Object Model (DOM) di Aspose.Words untuk .NET. Panduan ini akan memandu Anda melalui setiap langkah, mulai dari menyiapkan lingkungan hingga memasukkan dan memperbarui kolom gabungan dalam dokumen Word.

## Prasyarat

Sebelum masuk ke kode, mari pastikan Anda memiliki semua yang dibutuhkan untuk mengikuti tutorial ini.

1. Pengetahuan Dasar C#: Anda harus merasa nyaman dengan pemrograman C#.
2. Visual Studio Terpasang: Pastikan Anda telah menginstal Visual Studio atau IDE C# lainnya di komputer Anda.
3.  Aspose.Words untuk .NET: Unduh dan instal versi terbaru Aspose.Words untuk .NET dari[Rilis](https://releases.aspose.com/words/net/).
4.  Lisensi yang Valid: Jika Anda tidak memiliki lisensi, Anda bisa mendapatkannya[lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk evaluasi.

## Langkah 1: Siapkan Proyek Anda

Hal pertama yang terpenting, mari kita buat proyek baru di Visual Studio.

1. Buka Visual Studio.
2. Buat Proyek Baru: Buka File > Baru > Proyek. Pilih Aplikasi Konsol C#.
3. Beri Nama Proyek Anda: Berikan proyek Anda nama yang bermakna dan klik Buat.

## Langkah 2: Instal Aspose.Words

Untuk menggunakan Aspose.Words, Anda perlu menambahkannya ke proyek Anda. Hal ini dapat dilakukan melalui NuGet Package Manager.

1. Buka NuGet Package Manager: Klik kanan proyek Anda di Solution Explorer, lalu pilih Kelola Paket NuGet.
2. Cari Aspose.Words: Di Pengelola Paket NuGet, cari "Aspose.Words".
3. Instal Paket: Klik Instal untuk menambahkan Aspose.Words ke proyek Anda.

## Langkah 3: Impor Namespace

Untuk mulai menggunakan Aspose.Words, Anda perlu mengimpor namespace yang diperlukan ke dalam proyek Anda. Berikut cara melakukannya:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## Langkah 4: Inisialisasi Dokumen Anda

Sekarang semuanya sudah disiapkan, mari buat dokumen Word baru dan inisialisasi DocumentBuilder.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Buat dokumen dan DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 5: Pindahkan Kursor ke Paragraf Tertentu

Berikutnya, kita perlu memindahkan kursor ke paragraf tertentu dalam dokumen di mana kita ingin menyisipkan bidang gabungan.

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## Langkah 6: Masukkan Bidang Gabungan

 Memasukkan bidang gabungan sangatlah mudah. Kita akan menggunakan`InsertField` metode dari`DocumentBuilder` kelas.

```csharp
// Sisipkan bidang gabungkan bidang.
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## Langkah 7: Konfigurasikan Bidang Gabungan

Setelah memasukkan bidang gabungan, Anda dapat mengatur berbagai properti untuk mengonfigurasinya sesuai kebutuhan Anda.

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## Langkah 8: Perbarui dan Simpan Dokumen

Terakhir, perbarui bidang untuk memastikan semua pengaturan telah diterapkan, lalu simpan dokumen.

```csharp
// Perbarui bidang.
field.Update();

// Simpan dokumen.
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## Kesimpulan

Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah memasukkan dan mengonfigurasi kolom gabungan dalam dokumen Word menggunakan Aspose.Words untuk .NET. Tutorial ini membahas langkah-langkah penting mulai dari menyiapkan lingkungan hingga menyimpan dokumen akhir. Dengan Aspose.Words, Anda dapat mengotomatiskan tugas pemrosesan dokumen yang rumit, menjadikan aplikasi .NET Anda lebih canggih dan efisien.

## Pertanyaan yang Sering Diajukan

###  Apa itu bidang gabungan?
Bidang gabungan merupakan tempat penampung dalam dokumen yang dapat diganti secara dinamis dengan data dari sumber data, seperti basis data atau berkas CSV.

###  Dapatkah saya menggunakan Aspose.Words secara gratis?
 Aspose.Words menawarkan uji coba gratis yang dapat Anda unduh[Di Sini](https://releases.aspose.com/)Untuk penggunaan jangka panjang, Anda perlu membeli lisensi.

###  Bagaimana cara mendapatkan lisensi sementara untuk Aspose.Words?
 Anda dapat memperoleh lisensi sementara dari situs web Aspose[Di Sini](https://purchase.aspose.com/temporary-license/).

### Versi .NET apa yang didukung oleh Aspose.Words?
Aspose.Words mendukung beberapa versi .NET, termasuk .NET Framework, .NET Core, dan .NET Standard.

###  Di mana saya dapat menemukan dokumentasi API untuk Aspose.Words?
 Dokumentasi API tersedia[Di Sini](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
