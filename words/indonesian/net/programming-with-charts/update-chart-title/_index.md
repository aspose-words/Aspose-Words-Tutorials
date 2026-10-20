---
title: Perbarui Judul Diagram dan Alihkan Visibilitas Legenda di Word Menggunakan Aspose.Words for .NET
weight: 810
limit:
description: Pelajari cara mengubah judul diagram dan mengontrol visibilitas legenda dalam dokumen Word dengan Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Pelajari cara mengubah judul diagram dan mengontrol visibilitas legenda
    dalam dokumen Word dengan Aspose.Words for .NET.
  headline: Perbarui Judul Diagram dan Alihkan Visibilitas Legenda di Word Menggunakan
    Aspose.Words for .NET
  type: TechArticle
- description: Pelajari cara mengubah judul diagram dan mengontrol visibilitas legenda
    dalam dokumen Word dengan Aspose.Words for .NET.
  name: Perbarui Judul Diagram dan Alihkan Visibilitas Legenda di Word Menggunakan
    Aspose.Words for .NET
  steps:
  - name: Tentukan judul diagram yang diberikan pengguna dan apakah legenda harus
      ditampilkan.
    text: Tentukan judul diagram yang diberikan pengguna dan apakah legenda harus
      ditampilkan.
  - name: Buat dokumen Word baru dan DocumentBuilder untuk menambahkan konten.
    text: Buat dokumen Word baru dan DocumentBuilder untuk menambahkan konten.
  - name: Sisipkan diagram kolom berukuran 432 × 252 pt ke dalam dokumen dan verifikasi
      bahwa shape tersebut memang berisi diagram.
    text: Sisipkan diagram kolom berukuran 432 × 252 pt ke dalam dokumen dan verifikasi
      bahwa shape tersebut memang berisi diagram.
  - name: Ambil objek chart, atur teks judulnya ke nilai yang diberikan pengguna,
      dan pastikan judul ditampilkan.
    text: Ambil objek chart, atur teks judulnya ke nilai yang diberikan pengguna,
      dan pastikan judul ditampilkan.
  - name: 'Konfigurasikan legenda: tampilkan di sebelah kanan jika diminta, jika tidak
      sembunyikan, dan izinkan legenda menutupi area plot.'
    text: 'Konfigurasikan legenda: tampilkan di sebelah kanan jika diminta, jika tidak
      sembunyikan, dan izinkan legenda menutupi area plot.'
  - name: Simpan dokumen yang telah dimodifikasi ke disk dengan nama CustomChart.docx.
    text: Simpan dokumen yang telah dimodifikasi ke disk dengan nama CustomChart.docx.
  type: HowTo
- questions:
  - answer: Ketika `displayLegend` bernilai `true`, kode mengatur `chartLegend.Position`
      menjadi `LegendPosition.Right`, sehingga legenda terlihat di sisi kanan area
      plot; properti `Overlay` tetap `true`, sehingga legenda dapat menutupi diagram
      untuk menghemat ruang.
    question: Apa yang berubah pada diagram yang dihasilkan ketika `displayLegend`
      diatur ke `true`?
  - answer: Atur `chartTitle.Show = false` (atau cukup tidak mengatur `Show` menjadi
      `true`) setelah menetapkan `chartTitle.Text`; judul tidak akan ditampilkan dalam
      dokumen Word.
    question: Bagaimana cara menyembunyikan judul diagram jika pengguna tidak menyediakan
      satu pun?
  - answer: Ya—`InsertChart` mengembalikan `Shape` yang seharusnya berisi diagram,
      tetapi memverifikasi `HasChart` memastikan shape tersebut benar‑benar memiliki
      objek `Chart`; jika tidak, kode akan melempar `InvalidOperationException`.
    question: Apakah perlu memeriksa `chartContainer.HasChart` setelah memanggil `InsertChart`?
  - answer: Tentu saja; tetapkan nilai apa pun dari enum `LegendPosition` (misalnya,
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) ke `chartLegend.Position`
      untuk memindahkan posisi legenda sesuai kebutuhan.
    question: Apakah saya dapat menempatkan legenda di tempat selain sisi kanan?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Ubah Judul Diagram & Legenda di Word
og_description: Pelajari cara menetapkan judul diagram khusus dan mengontrol tampilan legenda dalam dokumen Word dengan Aspose.Words for .NET.
og_image_alt: Panduan yang menampilkan kode untuk memperbarui judul diagram dan mengalihkan legenda dalam dokumen Word menggunakan Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Perbarui Judul Diagram dan Alihkan Visibilitas Legenda di Word Menggunakan Aspose.Words
Tutorial ini menunjukkan cara memodifikasi diagram secara programatis di dalam dokumen Word dengan Aspose.Words for .NET. Anda akan belajar menyisipkan diagram kolom, mengganti judulnya dengan teks yang diberikan pengguna, dan mengontrol visibilitas serta overlay legenda berdasarkan preferensi pengguna. Langkah‑langkah ini memungkinkan Anda menyesuaikan tampilan diagram secara dinamis tanpa penyuntingan manual.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Apa yang berubah pada diagram yang dihasilkan ketika `displayLegend` diatur ke `true`?**  
A: Ketika `displayLegend` bernilai `true`, kode mengatur `chartLegend.Position` menjadi `LegendPosition.Right`, sehingga legenda terlihat di sisi kanan area plot; properti `Overlay` tetap `true`, sehingga legenda dapat menutupi diagram untuk menghemat ruang.

**Q: Bagaimana cara menyembunyikan judul diagram jika pengguna tidak menyediakan satu pun?**  
A: Atur `chartTitle.Show = false` (atau cukup tidak mengatur `Show` menjadi `true`) setelah menetapkan `chartTitle.Text`; judul tidak akan ditampilkan dalam dokumen Word.

**Q: Apakah perlu memeriksa `chartContainer.HasChart` setelah memanggil `InsertChart`?**  
A: Ya—`InsertChart` mengembalikan `Shape` yang seharusnya berisi diagram, tetapi memverifikasi `HasChart` memastikan shape tersebut benar‑benar memiliki objek `Chart`; jika tidak, kode akan melempar `InvalidOperationException`.

**Q: Apakah saya dapat menempatkan legenda di tempat selain sisi kanan?**  
A: Tentu saja; tetapkan nilai apa pun dari enum `LegendPosition` (misalnya, `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) ke `chartLegend.Position` untuk memindahkan posisi legenda sesuai kebutuhan.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}