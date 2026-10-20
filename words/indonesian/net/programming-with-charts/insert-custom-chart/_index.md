---
title: Masukkan Diagram Kolom Kustom ke Dokumen Word Menggunakan Aspose.Words for .NET
weight: 310
limit:
description: Buat file Word, sisipkan diagram kolom, ganti datanya dengan array khusus, tambahkan judul, dan simpan—semua dengan Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Buat file Word, sisipkan diagram kolom, ganti datanya dengan array
    khusus, tambahkan judul, dan simpan—semua dengan Aspose.Words for .NET.
  headline: Masukkan Diagram Kolom Kustom ke Dokumen Word Menggunakan Aspose.Words
    for .NET
  type: TechArticle
- description: Buat file Word, sisipkan diagram kolom, ganti datanya dengan array
    khusus, tambahkan judul, dan simpan—semua dengan Aspose.Words for .NET.
  name: Masukkan Diagram Kolom Kustom ke Dokumen Word Menggunakan Aspose.Words for
    .NET
  steps:
  - name: Buat Document baru dan DocumentBuilder yang terhubung padanya.
    text: Buat Document baru dan DocumentBuilder yang terhubung padanya.
  - name: Masukkan diagram kolom berukuran 432x252 poin ke dalam dokumen dan dapatkan
      objek Chart-nya.
    text: Masukkan diagram kolom berukuran 432x252 poin ke dalam dokumen dan dapatkan
      objek Chart-nya.
  - name: Hapus seri contoh yang dihasilkan secara otomatis dari diagram.
    text: Hapus seri contoh yang dihasilkan secara otomatis dari diagram.
  - name: Tetapkan label kategori sumbu X dan entri legenda untuk setiap seri.
    text: Tetapkan label kategori sumbu X dan entri legenda untuk setiap seri.
  - name: Buat array dua dimensi di mana setiap baris menyimpan nilai untuk satu seri.
    text: Buat array dua dimensi di mana setiap baris menyimpan nilai untuk satu seri.
  - name: Iterasi setiap seri, ekstrak nilai barisnya dari matriks, dan tambahkan
      seri ke diagram dengan entri legenda yang sesuai serta label sumbu X.
    text: Iterasi setiap seri, ekstrak nilai barisnya dari matriks, dan tambahkan
      seri ke diagram dengan entri legenda yang sesuai serta label sumbu X.
  - name: Setel teks judul diagram menjadi 'Half‑Yearly Revenue' dan buatnya terlihat.
    text: Setel teks judul diagram menjadi 'Half‑Yearly Revenue' dan buatnya terlihat.
  - name: Simpan dokumen yang berisi diagram khusus ke file .docx.
    text: Simpan dokumen yang berisi diagram khusus ke file .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` mengharapkan panjang array nilai sama dengan jumlah
      label sumbu X, dan Anda harus menambahkan tepat satu seri per entri legenda;
      ketidaksesuaian akan melempar `ArgumentException` pada runtime.'
    question: Bagaimana jika baris atau kolom dalam `dataMatrix` tidak sesuai dengan
      panjang `legendEntries` atau `xLabels`?
  - answer: Ya—ganti `ChartType.Column` dalam `docBuilder.InsertChart` dengan `ChartType`
      lain (mis., `ChartType.Line`) dan pemanggilan `Series.Add` berikutnya akan mengisi
      diagram baru dengan cara yang sama.
    question: Apakah saya dapat menggunakan tipe diagram lain, seperti diagram garis,
      dengan logika pengisian data yang sama?
  - answer: Sesuaikan properti `Width` dan `Height` dari `Shape` yang dikembalikan
      oleh `InsertChart` (mis., `chartContainer.Width = 500; chartContainer.Height
      = 300;`).
    question: Bagaimana cara mengubah ukuran diagram setelah dimasukkan?
  - answer: Setel `chartObj.Series[i].HasDataLabel = true;` untuk setiap seri setelah
      menambahkannya, atau lakukan loop melalui `chartObj.Series` dan aktifkan `HasDataLabel`
      untuk menampilkan nilai pada diagram.
    question: Apakah ada cara cepat untuk menampilkan label data pada setiap kolom
      diagram?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Tambahkan Diagram Kolom Kustom ke Dokumen Word
og_description: Ganti data default diagram dengan array Anda sendiri dan atur judul dalam hitungan detik.
og_image_alt: Tangkapan layar yang menampilkan dokumen Word dengan diagram kolom kustom yang dibuat menggunakan Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Diagram Kolom Kustom ke Dokumen Word Menggunakan Aspose.Words
Tutorial ini memandu Anda melalui pembuatan dokumen Word, penyisipan diagram kolom, penghapusan data defaultnya, dan pengisian diagram dengan nilai khusus dari array dua dimensi—memetakan setiap baris ke sebuah seri dan setiap kolom ke sebuah kategori. Anda juga akan melihat cara menambahkan judul diagram sebelum menyimpan file. Ikuti langkah-langkah untuk menghasilkan diagram yang sepenuhnya disesuaikan langsung di file Word Anda.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: Bagaimana jika baris atau kolom dalam `dataMatrix` tidak sesuai dengan panjang `legendEntries` atau `xLabels`?**  
A: `Chart.Series.Add` mengharapkan panjang array nilai sama dengan jumlah label sumbu X, dan Anda harus menambahkan tepat satu seri per entri legenda; ketidaksesuaian akan melempar `ArgumentException` pada runtime.

**Q: Apakah saya dapat menggunakan tipe diagram lain, seperti diagram garis, dengan logika pengisian data yang sama?**  
A: Ya—ganti `ChartType.Column` dalam `docBuilder.InsertChart` dengan `ChartType` lain (mis., `ChartType.Line`) dan pemanggilan `Series.Add` berikutnya akan mengisi diagram baru dengan cara yang sama.

**Q: Bagaimana cara mengubah ukuran diagram setelah dimasukkan?**  
A: Sesuaikan properti `Width` dan `Height` dari `Shape` yang dikembalikan oleh `InsertChart` (mis., `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Apakah ada cara cepat untuk menampilkan label data pada setiap kolom diagram?**  
A: Setel `chartObj.Series[i].HasDataLabel = true;` untuk setiap seri setelah menambahkannya, atau lakukan loop melalui `chartObj.Series` dan aktifkan `HasDataLabel` untuk menampilkan nilai pada diagram.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}