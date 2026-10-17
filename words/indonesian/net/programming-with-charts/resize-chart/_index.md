---
title: Ubah Ukuran Chart Secara Proporsional Saat Mengubah Ukuran Halaman di Word Menggunakan Aspose.Words for .NET
weight: 210
limit:
description: Pelajari cara otomatis mengubah ukuran diagram kolom Word saat mengubah dokumen menjadi A4 menggunakan Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Pelajari cara otomatis mengubah ukuran diagram kolom Word saat mengubah
    dokumen menjadi A4 menggunakan Aspose.Words for .NET.
  headline: Ubah Ukuran Chart Secara Proporsional Saat Mengubah Ukuran Halaman di
    Word Menggunakan Aspose.Words for .NET
  type: TechArticle
- description: Pelajari cara otomatis mengubah ukuran diagram kolom Word saat mengubah
    dokumen menjadi A4 menggunakan Aspose.Words for .NET.
  name: Ubah Ukuran Chart Secara Proporsional Saat Mengubah Ukuran Halaman di Word
    Menggunakan Aspose.Words for .NET
  steps:
  - name: Buat objek Document baru dan DocumentBuilder untuk mengeditnya.
    text: Buat objek Document baru dan DocumentBuilder untuk mengeditnya.
  - name: Sisipkan diagram kolom berukuran 432×252 poin dan dapatkan objek Chart-nya.
    text: Sisipkan diagram kolom berukuran 432×252 poin dan dapatkan objek Chart-nya.
  - name: Setel teks judul diagram menjadi "Quarterly Revenue" dan buat terlihat.
    text: Setel teks judul diagram menjadi "Quarterly Revenue" dan buat terlihat.
  - name: Simpan dokumen ke file yang menampilkan ukuran diagram asli.
    text: Simpan dokumen ke file yang menampilkan ukuran diagram asli.
  - name: Ubah ukuran kertas dokumen menjadi A4 dan segarkan tata letak.
    text: Ubah ukuran kertas dokumen menjadi A4 dan segarkan tata letak.
  - name: Hitung lebar diagram baru yang sama dengan 80 % lebar halaman sambil mempertahankan
      rasio aspek asli.
    text: Hitung lebar diagram baru yang sama dengan 80 % lebar halaman sambil mempertahankan
      rasio aspek asli.
  - name: Jika shape berisi chart, terapkan lebar dan tinggi yang dihitung untuk mengubah
      ukurannya.
    text: Jika shape berisi chart, terapkan lebar dan tinggi yang dihitung untuk mengubah
      ukurannya.
  - name: Simpan dokumen setelah chart diubah ukurannya untuk mencerminkan ukuran
      halaman baru.
    text: Simpan dokumen setelah chart diubah ukurannya untuk mencerminkan ukuran
      halaman baru.
  type: HowTo
- questions:
  - answer: Ya. Mengubah `docBuilder.PageSetup.PaperSize` tidak secara otomatis menyesuaikan
      shape yang ada, jadi Anda harus menghitung ulang dan menetapkan `chartContainer.Width`
      dan `Height` secara manual seperti yang ditunjukkan.
    question: Apakah saya perlu mengubah ukuran chart secara manual setelah mengubah
      ukuran kertas dokumen?
  - answer: Itu menyimpan `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      dan kemudian menghitung `newChartHeight = newChartWidth * originalAspectRatio`
      setelah menentukan lebar baru.
    question: Bagaimana kode menjaga rasio lebar‑ke‑tinggi chart asli saat mengubah
      ukuran?
  - answer: '`UpdatePageLayout()` memaksa mesin tata letak untuk mengevaluasi kembali
      dimensi halaman, memastikan `docBuilder.PageSetup.PageWidth` mencerminkan lebar
      A4 baru sebelum ukuran chart dihitung ulang.'
    question: Mengapa `myDoc.UpdatePageLayout()` dipanggil setelah mengatur ukuran
      kertas menjadi A4?
  - answer: Guard `if (chartContainer.HasChart)` mencegah kode menetapkan `Width`
      dan `Height` ketika tidak ada chart, menghindari pengecualian runtime.
    question: Apa yang terjadi jika shape yang disisipkan sebenarnya tidak berisi
      chart?
  - answer: Tentu—ganti pengali `0.8` dengan proporsi apa pun yang Anda inginkan;
      sisa logika pengubahan ukuran tetap akan mempertahankan rasio aspek asli.
    question: Apakah saya dapat mengubah faktor skala 80 % ke nilai lain?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Ubah Ukuran Chart Word Saat Beralih ke A4
og_description: Jaga chart Anda tetap proporsional dengan otomatis mengubah ukurannya setelah mengubah dokumen menjadi A4.
og_image_alt: Tangkapan layar yang menunjukkan diagram kolom secara otomatis diubah ukurannya untuk menyesuaikan dokumen Word berukuran A4 menggunakan Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ubah Ukuran Chart Secara Proporsional Saat Mengubah Ukuran Halaman di Word Menggunakan Aspose.Words
Tutorial ini menunjukkan cara menyisipkan diagram kolom ke dalam dokumen Word, mengubah ukuran halaman dokumen menjadi A4, dan membuat diagram secara otomatis mengubah ukuran sehingga tetap proporsional dengan lebar halaman baru. Dengan mengikuti langkah-langkah, Anda akan melihat diagram menyesuaikan dimensinya tanpa skala manual, memastikan tata letak yang konsisten di berbagai format halaman.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Apakah saya perlu mengubah ukuran chart secara manual setelah mengubah ukuran kertas dokumen?**  
A: Ya. Mengubah `docBuilder.PageSetup.PaperSize` tidak secara otomatis menyesuaikan shape yang ada, jadi Anda harus menghitung ulang dan menetapkan `chartContainer.Width` dan `Height` secara manual seperti yang ditunjukkan.

**Q: Bagaimana kode menjaga rasio lebar‑ke‑tinggi chart asli saat mengubah ukuran?**  
A: Itu menyimpan `originalAspectRatio = chartContainer.Height / chartContainer.Width` dan kemudian menghitung `newChartHeight = newChartWidth * originalAspectRatio` setelah menentukan lebar baru.

**Q: Mengapa `myDoc.UpdatePageLayout()` dipanggil setelah mengatur ukuran kertas menjadi A4?**  
A: `UpdatePageLayout()` memaksa mesin tata letak untuk mengevaluasi kembali dimensi halaman, memastikan `docBuilder.PageSetup.PageWidth` mencerminkan lebar A4 baru sebelum ukuran chart dihitung ulang.

**Q: Apa yang terjadi jika shape yang disisipkan sebenarnya tidak berisi chart?**  
A: Guard `if (chartContainer.HasChart)` mencegah kode menetapkan `Width` dan `Height` ketika tidak ada chart, menghindari pengecualian runtime.

**Q: Apakah saya dapat mengubah faktor skala 80 % ke nilai lain?**  
A: Tentu—ganti pengali `0.8` dengan proporsi apa pun yang Anda inginkan; sisa logika pengubahan ukuran tetap akan mempertahankan rasio aspek asli.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}