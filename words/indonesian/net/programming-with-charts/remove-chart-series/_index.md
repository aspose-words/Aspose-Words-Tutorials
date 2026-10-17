---
title: Hapus Seri Diagram dari Word Document Menggunakan Aspose.Words for .NET
weight: 510
limit:
description: Pelajari cara menghapus satu seri data tertentu dari diagram kolom dalam Word document menggunakan Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Pelajari cara menghapus satu seri data tertentu dari diagram kolom
    dalam Word document menggunakan Aspose.Words for .NET.
  headline: Hapus Seri Diagram dari Word Document Menggunakan Aspose.Words for .NET
  type: TechArticle
- description: Pelajari cara menghapus satu seri data tertentu dari diagram kolom
    dalam Word document menggunakan Aspose.Words for .NET.
  name: Hapus Seri Diagram dari Word Document Menggunakan Aspose.Words for .NET
  steps:
  - name: Buat sebuah Word Document baru dan DocumentBuilder yang terhubung ke dokumen
      tersebut.
    text: Buat sebuah Word Document baru dan DocumentBuilder yang terhubung ke dokumen
      tersebut.
  - name: Sisipkan diagram kolom dengan ukuran 432×252 poin dan dapatkan objek Chart
      untuk manipulasi lebih lanjut.
    text: Sisipkan diagram kolom dengan ukuran 432×252 poin dan dapatkan objek Chart
      untuk manipulasi lebih lanjut.
  - name: Tentukan indeks berbasis nol dari seri yang harus dihapus (seri kedua).
    text: Tentukan indeks berbasis nol dari seri yang harus dihapus (seri kedua).
  - name: Jika indeks valid, panggil RemoveAt pada koleksi Series diagram untuk menghapus
      seri tersebut.
    text: Jika indeks valid, panggil RemoveAt pada koleksi Series diagram untuk menghapus
      seri tersebut.
  - name: Simpan dokumen yang diperbarui ke file .docx.
    text: Simpan dokumen yang diperbarui ke file .docx.
  type: HowTo
- questions:
  - answer: Pemeriksaan `if` (`targetSeriesIdx < columnChart.Series.Count`) akan gagal,
      sehingga `RemoveAt` tidak pernah dipanggil dan diagram tetap tidak berubah.
    question: Apa yang terjadi jika saya memberikan indeks yang sama dengan jumlah
      seri dalam diagram?
  - answer: Ya, setelah `columnChart.Series.RemoveAt` legenda akan dibuat ulang untuk
      mencerminkan seri yang tersisa, sehingga entri yang dihapus menghilang dari
      legenda.
    question: Apakah menghapus sebuah seri secara otomatis memperbarui legenda diagram?
  - answer: Kode ini bekerja untuk tipe diagram apa pun yang mendukung koleksi `Series`;
      cukup ubah `ChartType.Column` ke tipe yang diinginkan saat menyisipkan diagram.
    question: Apakah saya dapat menggunakan kode yang sama untuk menghapus seri dari
      diagram garis atau pai?
  - answer: Diagram dengan nol seri masih merupakan `Shape` yang valid dan akan disimpan,
      tetapi akan muncul kosong dalam dokumen hasil.
    question: Jika saya menghapus satu-satunya seri dalam diagram, apakah diagram
      tetap akan disimpan dengan benar?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Hapus Seri Diagram dalam Word Document
og_description: Panduan langkah demi langkah untuk menghapus satu seri data dari diagram Word menggunakan Aspose.Words for .NET.
og_image_alt: Panduan yang menunjukkan cara menghapus satu seri data tertentu dari diagram kolom dalam Word document menggunakan Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hapus Seri Diagram dari Word Document Menggunakan Aspose.Words
Tutorial ini menunjukkan cara membuat Word document, menambahkan diagram kolom dengan DocumentBuilder, dan kemudian menghapus satu seri data tertentu dari diagram tersebut menggunakan metode ChartSeriesCollection.RemoveAt. Pada akhir tutorial, Anda akan memiliki dokumen yang tersimpan dengan seri yang tidak diinginkan dihapus, memberi Anda kontrol yang tepat atas konten diagram langsung dari kode .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Apa yang terjadi jika saya memberikan indeks yang sama dengan jumlah seri dalam diagram?**  
A: Pemeriksaan `if` (`targetSeriesIdx < columnChart.Series.Count`) akan gagal, sehingga `RemoveAt` tidak pernah dipanggil dan diagram tetap tidak berubah.

**Q: Apakah menghapus sebuah seri secara otomatis memperbarui legenda diagram?**  
A: Ya, setelah `columnChart.Series.RemoveAt` legenda akan dibuat ulang untuk mencerminkan seri yang tersisa, sehingga entri yang dihapus menghilang dari legenda.

**Q: Apakah saya dapat menggunakan kode yang sama untuk menghapus seri dari diagram garis atau pai?**  
A: Kode ini bekerja untuk tipe diagram apa pun yang mendukung koleksi `Series`; cukup ubah `ChartType.Column` ke tipe yang diinginkan saat menyisipkan diagram.

**Q: Jika saya menghapus satu-satunya seri dalam diagram, apakah diagram tetap akan disimpan dengan benar?**  
A: Diagram dengan nol seri masih merupakan `Shape` yang valid dan akan disimpan, tetapi akan muncul kosong dalam dokumen hasil.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}