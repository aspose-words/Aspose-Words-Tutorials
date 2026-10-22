---
title: Atur Label Data Seragam dalam Diagram Kolom Menggunakan Aspose.Words untuk .NET
weight: 110
limit:
description: Pelajari cara membuat diagram kolom Word dan menerapkan ukuran font serta warna label data yang seragam pada semua seri dengan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Pelajari cara membuat diagram kolom Word dan menerapkan ukuran font
    serta warna label data yang seragam pada semua seri dengan Aspose.Words untuk
    .NET.
  headline: Atur Label Data Seragam dalam Diagram Kolom Menggunakan Aspose.Words untuk
    .NET
  type: TechArticle
- description: Pelajari cara membuat diagram kolom Word dan menerapkan ukuran font
    serta warna label data yang seragam pada semua seri dengan Aspose.Words untuk
    .NET.
  name: Atur Label Data Seragam dalam Diagram Kolom Menggunakan Aspose.Words untuk
    .NET
  steps:
  - name: Buat dokumen Word kosong baru dan DocumentBuilder untuk mengeditnya.
    text: Buat dokumen Word kosong baru dan DocumentBuilder untuk mengeditnya.
  - name: Sisipkan diagram kolom berukuran 500×300 ke dalam dokumen dan dapatkan objek
      Chart-nya.
    text: Sisipkan diagram kolom berukuran 500×300 ke dalam dokumen dan dapatkan objek
      Chart-nya.
  - name: Hapus seri contoh default yang ditambahkan Aspose.Words ke diagram baru.
    text: Hapus seri contoh default yang ditambahkan Aspose.Words ke diagram baru.
  - name: Tetapkan label kategori dan tambahkan dua seri data (Item Alpha dan Item
      Beta) beserta nilainya ke diagram.
    text: Tetapkan label kategori dan tambahkan dua seri data (Item Alpha dan Item
      Beta) beserta nilainya ke diagram.
  - name: Tetapkan ukuran font dan warna dasar yang akan diterapkan pada semua label
      data.
    text: Tetapkan ukuran font dan warna dasar yang akan diterapkan pada semua label
      data.
  - name: Aktifkan label data untuk setiap seri, tampilkan nilai numerik, dan terapkan
      ukuran font serta warna yang telah ditentukan.
    text: Aktifkan label data untuk setiap seri, tampilkan nilai numerik, dan terapkan
      ukuran font serta warna yang telah ditentukan.
  - name: Simpan dokumen ke file .docx.
    text: Simpan dokumen ke file .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` membuat diagram dengan seri contoh default; menghapusnya
      menghilangkan placeholder tersebut sehingga diagram hanya menampilkan seri yang
      Anda tambahkan (`Item Alpha` dan `Item Beta`).'
    question: Mengapa saya perlu memanggil `chart.Series.Clear()` sebelum menambahkan
      seri saya sendiri?
  - answer: Ganti `Color.White` dengan nilai `System.Drawing.Color` apa pun, misalnya
      `Color.Black` atau `Color.FromArgb(255, 30, 144, 255)`; warna baru diterapkan
      melalui `series.DataLabels.Font.Color` di dalam loop.
    question: Bagaimana saya dapat mengubah warna label data menjadi selain putih?
  - answer: Label data akan disembunyikan, sehingga pengaturan font yang Anda terapkan
      menjadi tidak terlihat; Anda harus tetap mengatur `HasDataLabels` ke `true`
      agar label (dan gaya mereka) muncul.
    question: Apa yang terjadi jika saya mengatur `series.HasDataLabels = false` setelah
      mengonfigurasi ukuran font dan warna?
  - answer: Ya—setiap `ChartSeries` memiliki objek `DataLabels` masing-masing, sehingga
      setiap seri yang ditambahkan setelah loop awal juga harus memiliki `HasDataLabels`,
      `ShowValue`, dan properti font yang diatur, baik dengan melakukan loop lagi
      atau dengan mengekstrak gaya ke dalam metode bantu.
    question: Apakah saya perlu melakukan loop melalui seri lagi jika saya menambahkan
      seri lain nanti dalam kode?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Terapkan Label Data Seragam ke Diagram Word
og_description: Berikan setiap label diagram ukuran font dan warna yang sama secara cepat dengan Aspose.Words untuk .NET.
og_image_alt: Panduan yang menampilkan dokumen Word dengan diagram kolom di mana semua label data berbagi ukuran font dan warna yang sama, dibuat menggunakan Aspose.Words untuk .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atur Label Data Seragam dalam Diagram Kolom Menggunakan Aspose.Words untuk .NET
Tutorial ini menunjukkan cara menghasilkan dokumen Word, menyisipkan diagram kolom, dan menambahkan seri data khusus dengan Aspose.Words untuk .NET. Selanjutnya, tutorial ini mendemonstrasikan cara mendefinisikan ukuran font dan warna label data default sehingga setiap seri dalam diagram menampilkan label yang identik. Dengan menerapkan satu gaya, Anda memastikan tampilan visual yang konsisten di seluruh diagram.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: Mengapa saya perlu memanggil `chart.Series.Clear()` sebelum menambahkan seri saya sendiri?**  
A: `InsertChart` membuat diagram dengan seri contoh default; menghapusnya menghilangkan placeholder tersebut sehingga diagram hanya menampilkan seri yang Anda tambahkan (`Item Alpha` dan `Item Beta`).

**Q: Bagaimana saya dapat mengubah warna label data menjadi selain putih?**  
A: Ganti `Color.White` dengan nilai `System.Drawing.Color` apa pun, misalnya `Color.Black` atau `Color.FromArgb(255, 30, 144, 255)`; warna baru diterapkan melalui `series.DataLabels.Font.Color` di dalam loop.

**Q: Apa yang terjadi jika saya mengatur `series.HasDataLabels = false` setelah mengonfigurasi ukuran font dan warna?**  
A: Label data akan disembunyikan, sehingga pengaturan font yang Anda terapkan menjadi tidak terlihat; Anda harus tetap mengatur `HasDataLabels` ke `true` agar label (dan gaya mereka) muncul.

**Q: Apakah saya perlu melakukan loop melalui seri lagi jika saya menambahkan seri lain nanti dalam kode?**  
A: Ya—setiap `ChartSeries` memiliki objek `DataLabels` masing-masing, sehingga setiap seri yang ditambahkan setelah loop awal juga harus memiliki `HasDataLabels`, `ShowValue`, dan properti font yang diatur, baik dengan melakukan loop lagi atau dengan mengekstrak gaya ke dalam metode bantu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}