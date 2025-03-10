---
title: Terapkan Batas Garis Besar
linktitle: Terapkan Batas Garis Besar
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menerapkan garis tepi pada tabel di Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk pemformatan tabel yang sempurna.
weight: 10
url: /id/net/programming-with-table-styles-and-formatting/apply-outline-border/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Terapkan Batas Garis Besar

## Perkenalan

Dalam tutorial hari ini, kita akan menyelami dunia manipulasi dokumen menggunakan Aspose.Words untuk .NET. Secara khusus, kita akan mempelajari cara menerapkan batas garis luar ke tabel dalam dokumen Word. Ini adalah keterampilan yang fantastis untuk dimiliki dalam perangkat Anda jika Anda sering bekerja dengan pembuatan dan pemformatan dokumen otomatis. Jadi, mari kita mulai perjalanan ini untuk membuat tabel Anda tidak hanya fungsional tetapi juga menarik secara visual.

## Prasyarat

Sebelum kita masuk ke kode, ada beberapa hal yang Anda perlukan:

1.  Aspose.Words untuk .NET: Anda perlu menginstal Aspose.Words untuk .NET. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Lingkungan pengembangan yang cocok seperti Visual Studio.
3. Pengetahuan Dasar C#: Pemahaman mendasar tentang C# akan membantu Anda mengikuti tutorial.

## Mengimpor Ruang Nama

Pertama-tama, pastikan Anda telah mengimpor namespace yang diperlukan. Ini penting untuk mengakses fungsi Aspose.Words.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Mari kita uraikan prosesnya menjadi beberapa langkah yang sederhana dan mudah dikelola.

## Langkah 1: Muat Dokumen

Pertama, kita perlu memuat dokumen Word yang berisi tabel yang ingin kita format.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

 Pada langkah ini, kami menggunakan`Document` kelas dari Aspose.Words untuk memuat dokumen yang sudah ada. Ganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya tempat dokumen Anda disimpan.

## Langkah 2: Akses Tabel

Berikutnya, kita perlu mengakses tabel spesifik yang ingin kita format. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

 Di Sini,`GetChild` metode mengambil tabel pertama dalam dokumen. Parameter`NodeType.Table, 0, true` pastikan kita mendapatkan jenis node yang benar.

## Langkah 3: Sejajarkan Tabel

Sekarang, mari kita ratakan tabel di tengah halaman.

```csharp
table.Alignment = TableAlignment.Center;
```

Langkah ini memastikan tabel terpusat dengan rapi, memberikan tampilan profesional.

## Langkah 4: Hapus Batas yang Ada

Sebelum kita menerapkan batas baru, kita perlu menghapus batas yang sudah ada.

```csharp
table.ClearBorders();
```

Membersihkan batas memastikan bahwa batas baru kita diterapkan secara bersih tanpa ada gaya lama yang mengganggu.

## Langkah 5: Tetapkan Batas Garis Besar

Sekarang, mari terapkan garis tepi hijau pada tabel.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

 Setiap jenis batas (kiri, kanan, atas, bawah) diatur secara individual. Kami menggunakan`LineStyle.Single` untuk garis padat,`1.5` untuk lebar garis, dan`Color.Green` untuk warna batas.

## Langkah 6: Terapkan Cell Shading

Untuk membuat tabel lebih menarik secara visual, mari isi sel dengan warna hijau muda.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

 Di Sini,`SetShading` digunakan untuk menerapkan warna hijau muda pekat pada sel, sehingga tabel tampak menonjol.

## Langkah 7: Simpan Dokumen

Terakhir, simpan dokumen yang telah dimodifikasi.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Langkah ini menyimpan dokumen Anda dengan format yang diterapkan. Anda dapat membukanya untuk melihat tabel yang diformat dengan indah.

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda telah berhasil menerapkan border outline ke tabel dalam dokumen Word menggunakan Aspose.Words for .NET. Tutorial ini mencakup memuat dokumen, mengakses tabel, menyelaraskannya, menghapus border yang ada, menerapkan border baru, menambahkan cell shading, dan akhirnya menyimpan dokumen. 

Dengan keterampilan ini, Anda dapat menyempurnakan tampilan visual tabel Anda, membuat dokumen Anda lebih profesional dan menarik. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menerapkan gaya yang berbeda pada setiap batas tabel?  
 Ya, Anda dapat menerapkan gaya dan warna yang berbeda ke setiap perbatasan dengan menyesuaikan parameter di`SetBorder` metode.

### Bagaimana cara mengubah lebar perbatasan?  
 Anda dapat mengubah lebar dengan memodifikasi parameter ketiga di`SetBorder` metode. Misalnya,`1.5` menetapkan lebar 1,5 poin.

### Mungkinkah menerapkan bayangan pada sel individual?  
 Ya, Anda dapat menerapkan bayangan ke sel individual dengan mengakses setiap sel dan menggunakan`SetShading` metode.

### Bisakah saya menggunakan warna lain untuk batas dan bayangan?  
 Tentu saja! Anda dapat menggunakan warna apa pun yang tersedia di`System.Drawing.Color` kelas.

### Bagaimana cara menyelaraskan tabel secara horizontal dan berpusat?  
 Itu`table.Alignment = TableAlignment.Center;` Baris dalam kode memusatkan tabel secara horizontal pada halaman.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
