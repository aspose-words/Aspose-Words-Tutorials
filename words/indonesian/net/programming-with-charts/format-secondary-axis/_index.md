---
title: Format Sumbu Y Sekunder sebagai Mata Uang dalam Diagram Word Menggunakan Aspose.Words for .NET
weight: 710
limit:
description: Pelajari cara menambahkan dan memformat sumbu Y sekunder sebagai mata uang dalam diagram garis Word dengan Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Pelajari cara menambahkan dan memformat sumbu Y sekunder sebagai mata
    uang dalam diagram garis Word dengan Aspose.Words for .NET.
  headline: Format Sumbu Y Sekunder sebagai Mata Uang dalam Diagram Word Menggunakan
    Aspose.Words for .NET
  type: TechArticle
- description: Pelajari cara menambahkan dan memformat sumbu Y sekunder sebagai mata
    uang dalam diagram garis Word dengan Aspose.Words for .NET.
  name: Format Sumbu Y Sekunder sebagai Mata Uang dalam Diagram Word Menggunakan Aspose.Words
    for .NET
  steps:
  - name: Buat dokumen Word kosong baru dan DocumentBuilder untuk mengeditnya.
    text: Buat dokumen Word kosong baru dan DocumentBuilder untuk mengeditnya.
  - name: Sisipkan diagram garis berukuran 450×250 poin ke dalam dokumen dan dapatkan
      objek Chart-nya.
    text: Sisipkan diagram garis berukuran 450×250 poin ke dalam dokumen dan dapatkan
      objek Chart-nya.
  - name: Hapus seri placeholder default yang ditambahkan Aspose ke diagram baru.
    text: Hapus seri placeholder default yang ditambahkan Aspose ke diagram baru.
  - name: Tetapkan label kuartal dan tambahkan seri data utama dengan nilai contoh
      ke diagram.
    text: Tetapkan label kuartal dan tambahkan seri data utama dengan nilai contoh
      ke diagram.
  - name: Buat grup seri sekunder bertipe Line dan tetapkan ke grup sumbu sekunder.
    text: Buat grup seri sekunder bertipe Line dan tetapkan ke grup sumbu sekunder.
  - name: Sembunyikan sumbu X sekunder sehingga hanya sumbu Y sekunder yang terlihat.
    text: Sembunyikan sumbu X sekunder sehingga hanya sumbu Y sekunder yang terlihat.
  - name: Tampilkan judul sumbu Y sekunder dan atur teksnya menjadi \"Sales (USD)\".
    text: Tampilkan judul sumbu Y sekunder dan atur teksnya menjadi \"Sales (USD)\".
  - name: Atur format angka sumbu Y sekunder menjadi pola mata uang dengan dua tempat
      desimal dan lepaskan tautannya dari format sumber.
    text: Atur format angka sumbu Y sekunder menjadi pola mata uang dengan dua tempat
      desimal dan lepaskan tautannya dari format sumber.
  - name: Tambahkan seri tambahan ke grup sekunder, menyediakan data yang akan dipetakan
      terhadap sumbu Y sekunder.
    text: Tambahkan seri tambahan ke grup sekunder, menyediakan data yang akan dipetakan
      terhadap sumbu Y sekunder.
  - name: Simpan dokumen selesai ke file bernama ProfitChart.docx di direktori saat
      ini.
    text: Simpan dokumen selesai ke file bernama ProfitChart.docx di direktori saat
      ini.
  type: HowTo
- questions:
  - answer: Diagram akan mempertahankan seri placeholder default yang disisipkan Aspose.Words,
      sehingga \"Main Series\" khusus Anda akan muncul bersama titik data yang tidak
      diinginkan.
    question: Apa yang terjadi jika saya menghilangkan pemanggilan `lineChart.Series.Clear()`?
  - answer: Atur `secondarySeriesGroup.AxisX.Hidden = false;` (atau cukup hilangkan
      baris yang mengaturnya ke `true`).
    question: Bagaimana saya dapat menampilkan sumbu X sekunder alih-alih menyembunyikannya?
  - answer: Ya – ubah string format, misalnya `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"\\\"€\\\"#,##0.00\";` untuk euro atau sesuaikan pola agar cocok dengan locale
      Anda.
    question: Apakah saya dapat menggunakan simbol mata uang atau format yang berbeda
      untuk sumbu Y sekunder?
  - answer: Ketika `IsLinkedToSource` bernilai true, sumbu mewarisi format angka dari
      sumber data yang mendasarinya, menimpa `FormatCode` khusus apa pun; mengaturnya
      ke false memaksa diagram menggunakan format yang Anda tentukan.
    question: Mengapa saya perlu mengatur `IsLinkedToSource = false` saat menerapkan
      format angka khusus?
  - answer: Ya, tetapkan `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (atau `Right` untuk default) untuk mengontrol sisi mana sumbu digambar.
    question: Apakah memungkinkan memindahkan sumbu Y sekunder ke sisi kiri diagram?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Format Sumbu Sekunder Chart sebagai Mata Uang
og_description: Pelajari cara menambahkan sumbu Y sekunder ke diagram garis Word dan menataannya sebagai mata uang dengan dua desimal.
og_image_alt: Tangkapan layar yang menunjukkan diagram garis Word dengan sumbu Y sekunder yang diformat sebagai mata uang menggunakan Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format Sumbu Y Sekunder sebagai Mata Uang dalam Diagram Word Menggunakan Aspose.Words
Pada tutorial ini Anda akan melihat cara membuat dokumen Word, menyisipkan diagram garis, menambahkan sumbu Y sekunder, memformat sumbu tersebut sebagai mata uang dengan dua tempat desimal, dan mengikat seri data sekunder kepadanya menggunakan Aspose.Words for .NET. Memformat sumbu sekunder sebagai mata uang memungkinkan Anda menyajikan data keuangan dengan jelas bersama seri utama. Ikuti kode langkah demi langkah untuk melihat diagram yang dirender langsung dalam dokumen yang dihasilkan.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Apa yang terjadi jika saya menghilangkan pemanggilan `lineChart.Series.Clear()`?**  
A: Diagram akan mempertahankan seri placeholder default yang disisipkan Aspose.Words, sehingga \"Main Series\" khusus Anda akan muncul bersama titik data yang tidak diinginkan.

**Q: Bagaimana saya dapat menampilkan sumbu X sekunder alih-alih menyembunyikannya?**  
A: Atur `secondarySeriesGroup.AxisX.Hidden = false;` (atau cukup hilangkan baris yang mengaturnya ke `true`).

**Q: Apakah saya dapat menggunakan simbol mata uang atau format yang berbeda untuk sumbu Y sekunder?**  
A: Ya – ubah string format, misalnya `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` untuk euro atau sesuaikan pola agar cocok dengan locale Anda.

**Q: Mengapa saya perlu mengatur `IsLinkedToSource = false` saat menerapkan format angka khusus?**  
A: Ketika `IsLinkedToSource` bernilai true, sumbu mewarisi format angka dari sumber data yang mendasarinya, menimpa `FormatCode` khusus apa pun; mengaturnya ke false memaksa diagram menggunakan format yang Anda tentukan.

**Q: Apakah memungkinkan memindahkan sumbu Y sekunder ke sisi kiri diagram?**  
A: Ya, tetapkan `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (atau `Right` untuk default) untuk mengontrol sisi mana sumbu digambar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}