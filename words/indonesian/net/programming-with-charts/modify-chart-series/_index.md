---
title: Perbarui Data Seri Diagram dalam Dokumen Word Menggunakan Aspose.Words for .NET
weight: 610
limit:
description: Pelajari cara mengubah titik data seri diagram dalam dokumen Word dan menyegarkan diagram menggunakan Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Pelajari cara mengubah titik data seri diagram dalam dokumen Word dan
    menyegarkan diagram menggunakan Aspose.Words for .NET.
  headline: Perbarui Data Seri Diagram dalam Dokumen Word Menggunakan Aspose.Words
    for .NET
  type: TechArticle
- description: Pelajari cara mengubah titik data seri diagram dalam dokumen Word dan
    menyegarkan diagram menggunakan Aspose.Words for .NET.
  name: Perbarui Data Seri Diagram dalam Dokumen Word Menggunakan Aspose.Words for
    .NET
  steps:
  - name: Buat Document baru, sisipkan diagram kolom dengan DocumentBuilder, dan simpan
      sebagai file awal.
    text: Buat Document baru, sisipkan diagram kolom dengan DocumentBuilder, dan simpan
      sebagai file awal.
  - name: Buka file yang disimpan dan temukan shape diagram untuk memperoleh objek
      Chart yang ada.
    text: Buka file yang disimpan dan temukan shape diagram untuk memperoleh objek
      Chart yang ada.
  - name: Bersihkan nilai seri pertama dan tambahkan titik baru, lalu sesuaikan seri
      kedua dengan menghapus titik pertamanya dan menambahkan titik baru.
    text: Bersihkan nilai seri pertama dan tambahkan titik baru, lalu sesuaikan seri
      kedua dengan menghapus titik pertamanya dan menambahkan titik baru.
  - name: Simpan dokumen yang telah dimodifikasi ke file baru yang berisi diagram
      yang diperbarui.
    text: Simpan dokumen yang telah dimodifikasi ke file baru yang berisi diagram
      yang diperbarui.
  type: HowTo
- questions:
  - answer: Gunakan `document.GetChildNodes(NodeType.Shape, true)` untuk mendapatkan
      semua shape, lalu saring dengan `s.HasChart` dan pilih yang pertama (atau yang
      Anda butuhkan) – ini mencegah pemilihan gambar atau kotak teks yang tidak terkait.
    question: Bagaimana cara saya dapat menemukan shape diagram secara andal dalam
      dokumen yang mungkin berisi shape lain?
  - answer: '`ClearValues()` menghapus titik data yang ada; tanpa itu titik baru akan
      ditambahkan ke yang lama, yang dapat menghasilkan kategori duplikat atau total
      yang tidak tepat.'
    question: Mengapa saya perlu memanggil `ClearValues()` sebelum menambahkan titik
      baru ke sebuah seri?
  - answer: Gunakan `FromString` ketika kategori sumbu X diagram berupa teks (misalnya,
      "Group A"), dan `FromDouble` ketika sumbu mengharapkan nilai numerik seperti
      tanggal atau ukuran.
    question: Kapan saya harus menggunakan `ChartXValue.FromString` dibandingkan `ChartXValue.FromDouble`
      untuk nilai sumbu X?
  - answer: Mencoba mengakses seri yang tidak ada akan melempar `ArgumentOutOfRangeException`;
      selalu periksa `existingChart.Series.Count` sebelum merujuk ke indeks tertentu.
    question: Apa yang terjadi jika diagram hanya memiliki satu seri dan saya mencoba
      mengakses `existingChart.Series[1]`?
  - answer: Menyimpan `openedDoc` sudah cukup karena itu adalah instance dokumen yang
      berisi diagram yang telah dimodifikasi; `document` asli hanya digunakan untuk
      membuat file awal.
    question: Apakah saya perlu menyimpan kembali `document` asli setelah memodifikasi
      diagram, atau menyimpan `openedDoc` saja sudah cukup?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Edit Data Seri Diagram di Word
og_description: Panduan langkah demi langkah untuk mengubah nilai seri diagram dalam file Word dengan Aspose.Words for .NET.
og_image_alt: Panduan yang menampilkan dokumen Word dengan diagram kolom sebelum dan sesudah memperbarui data serinya menggunakan Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Perbarui Data Seri Diagram dalam Dokumen Word Menggunakan Aspose.Words
Tutorial ini menunjukkan cara membuat dokumen Word yang berisi diagram kolom, kemudian membuka kembali file, mengambil seri diagram yang ada, mengubah titik data mereka, dan menyimpan dokumen sehingga diagram menampilkan nilai baru. Ikuti kode langkah demi langkah untuk melihat betapa mudahnya menyesuaikan data diagram secara programatis dengan Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: Bagaimana cara saya dapat menemukan shape diagram secara andal dalam dokumen yang mungkin berisi shape lain?**  
A: Gunakan `document.GetChildNodes(NodeType.Shape, true)` untuk mendapatkan semua shape, lalu saring dengan `s.HasChart` dan pilih yang pertama (atau yang Anda butuhkan) – ini mencegah pemilihan gambar atau kotak teks yang tidak terkait.

**Q: Mengapa saya perlu memanggil `ClearValues()` sebelum menambahkan titik baru ke sebuah seri?**  
A: `ClearValues()` menghapus titik data yang ada; tanpa itu titik baru akan ditambahkan ke yang lama, yang dapat menghasilkan kategori duplikat atau total yang tidak tepat.

**Q: Kapan saya harus menggunakan `ChartXValue.FromString` dibandingkan `ChartXValue.FromDouble` untuk nilai sumbu X?**  
A: Gunakan `FromString` ketika kategori sumbu X diagram berupa teks (misalnya, "Group A"), dan `FromDouble` ketika sumbu mengharapkan nilai numerik seperti tanggal atau ukuran.

**Q: Apa yang terjadi jika diagram hanya memiliki satu seri dan saya mencoba mengakses `existingChart.Series[1]`?**  
A: Mencoba mengakses seri yang tidak ada akan melempar `ArgumentOutOfRangeException`; selalu periksa `existingChart.Series.Count` sebelum merujuk ke indeks tertentu.

**Q: Apakah saya perlu menyimpan kembali `document` asli setelah memodifikasi diagram, atau menyimpan `openedDoc` saja sudah cukup?**  
A: Menyimpan `openedDoc` sudah cukup karena itu adalah instance dokumen yang berisi diagram yang telah dimodifikasi; `document` asli hanya digunakan untuk membuat file awal.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}