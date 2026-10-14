---
title: Format Sumbu X Sekunder dan Atur Unit Tampilan ke Ribuan dalam Diagram Garis Word Menggunakan Aspose.Words untuk .NET
weight: 710
limit:
description: Buat diagram garis Word, tambahkan sumbu X sekunder, atur unit tampilan menjadi ribuan, dan terapkan format numerik khusus dengan Aspose.Words untuk .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Buat diagram garis Word, tambahkan sumbu X sekunder, atur unit tampilan
    menjadi ribuan, dan terapkan format numerik khusus dengan Aspose.Words untuk .NET.
  headline: Format Sumbu X Sekunder dan Atur Unit Tampilan ke Ribuan dalam Diagram
    Garis Word Menggunakan Aspose.Words untuk .NET
  type: TechArticle
- description: Buat diagram garis Word, tambahkan sumbu X sekunder, atur unit tampilan
    menjadi ribuan, dan terapkan format numerik khusus dengan Aspose.Words untuk .NET.
  name: Format Sumbu X Sekunder dan Atur Unit Tampilan ke Ribuan dalam Diagram Garis
    Word Menggunakan Aspose.Words untuk .NET
  steps:
  - name: Buat Document baru dan DocumentBuilder untuk mulai membangun file Word.
    text: Buat Document baru dan DocumentBuilder untuk mulai membangun file Word.
  - name: Sisipkan diagram garis berukuran 500×300 ke dalam dokumen dan dapatkan objek
      Chart.
    text: Sisipkan diagram garis berukuran 500×300 ke dalam dokumen dan dapatkan objek
      Chart.
  - name: Hapus seri demo default yang ditambahkan secara otomatis oleh Aspose.Words.
    text: Hapus seri demo default yang ditambahkan secara otomatis oleh Aspose.Words.
  - name: Definisikan array label kategori yang akan digunakan untuk sumbu X.
    text: Definisikan array label kategori yang akan digunakan untuk sumbu X.
  - name: Tambahkan seri data utama bernama "Main Data" menggunakan label dan nilai.
    text: Tambahkan seri data utama bernama "Main Data" menggunakan label dan nilai.
  - name: Buat grup seri sekunder bertipe Line dan tetapkan ke grup sumbu sekunder.
    text: Buat grup seri sekunder bertipe Line dan tetapkan ke grup sumbu sekunder.
  - name: Atur unit tampilan sumbu X sekunder menjadi ribuan sehingga nilai ditampilkan
      dalam K.
    text: Atur unit tampilan sumbu X sekunder menjadi ribuan sehingga nilai ditampilkan
      dalam K.
  - name: Terapkan format numerik khusus "#,##0.0" pada label tick sumbu X sekunder.
    text: Terapkan format numerik khusus "#,##0.0" pada label tick sumbu X sekunder.
  - name: Opsional, tambahkan seri data tambahan ke grup sekunder.
    text: Opsional, tambahkan seri data tambahan ke grup sekunder.
  - name: Simpan dokumen ke file .docx.
    text: Simpan dokumen ke file .docx.
  type: HowTo
- questions:
  - answer: Tidak – pengaturan `AxisX` milik `ChartSeriesGroup`, sehingga Anda dapat
      mengatur `secondaryGroup.AxisX.DisplayUnit.Unit` dan `secondaryGroup.AxisX.NumberFormat.FormatCode`
      sebelum atau sesudah menambahkan seri; konfigurasi akan diterapkan pada sumbu
      grup tersebut dalam kedua kasus.
    question: Apakah saya harus menambahkan seri sekunder sebelum mengatur unit tampilan
      dan format angka pada sumbu X sekunder?
  - answer: Ya – tetapkan nilai `AxisBuiltInUnit` apa pun, misalnya `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` untuk menampilkan nilai sumbu dalam jutaan alih-alih
      ribuan.
    question: Apakah saya dapat menggunakan unit bawaan lain, seperti jutaan, untuk
      sumbu X sekunder?
  - answer: Tidak – kode format hanya diterapkan pada sumbu yang Anda ubah (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      sehingga sumbu X utama tetap menggunakan format default.
    question: Apakah format khusus "#,##0.0" akan memengaruhi label sumbu X utama?
  - answer: Diagram akan berisi seri demo default selain seri yang Anda tambahkan,
      yang dapat menyebabkan garis tambahan dan kategori yang tidak cocok; membersihkan
      koleksi memastikan hanya data yang Anda inginkan yang muncul.
    question: Apa yang terjadi jika saya lupa membersihkan seri demo dengan `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Format Sumbu X Sekunder dan Atur Unit ke Ribuan
og_description: Tambahkan sumbu X sekunder ke diagram garis Word dan format labelnya dalam ribuan dengan pola khusus.
og_image_alt: Panduan yang menunjukkan cara menambahkan sumbu X sekunder ke diagram garis Word dan memformat labelnya untuk menampilkan unit dalam ribuan menggunakan Aspose.Words untuk .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format Sumbu X Sekunder dan Atur Unit Tampilan ke Ribuan dalam Diagram Garis Word Menggunakan Aspose.Words untuk .NET
Tutorial ini memandu Anda membuat dokumen Word yang berisi diagram garis, menambahkan sumbu X sekunder, dan mengkonfigurasi sumbu tersebut agar menampilkan nilai dalam ribuan. Anda juga akan belajar cara menerapkan format numerik khusus pada label sumbu sekunder, memberikan kontrol yang tepat atas cara data ditampilkan. Ikuti langkah‑langkahnya untuk meningkatkan keterbacaan diagram multi‑sumbu dalam laporan Word Anda.

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

**Q: Apakah saya harus menambahkan seri sekunder sebelum mengatur unit tampilan dan format angka pada sumbu X sekunder?**  
A: Tidak – pengaturan `AxisX` milik `ChartSeriesGroup`, sehingga Anda dapat mengatur `secondaryGroup.AxisX.DisplayUnit.Unit` dan `secondaryGroup.AxisX.NumberFormat.FormatCode` sebelum atau sesudah menambahkan seri; konfigurasi akan diterapkan pada sumbu grup tersebut dalam kedua kasus.

**Q: Apakah saya dapat menggunakan unit bawaan lain, seperti jutaan, untuk sumbu X sekunder?**  
A: Ya – tetapkan nilai `AxisBuiltInUnit` apa pun, misalnya `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` untuk menampilkan nilai sumbu dalam jutaan alih-alih ribuan.

**Q: Apakah format khusus "#,##0.0" akan memengaruhi label sumbu X utama?**  
A: Tidak – kode format hanya diterapkan pada sumbu yang Anda ubah (`secondaryGroup.AxisX.NumberFormat.FormatCode`), sehingga sumbu X utama tetap menggunakan format default.

**Q: Apa yang terjadi jika saya lupa membersihkan seri demo dengan `lineChart.Series.Clear();`?**  
A: Diagram akan berisi seri demo default selain seri yang Anda tambahkan, yang dapat menyebabkan garis tambahan dan kategori yang tidak cocok; membersihkan koleksi memastikan hanya data yang Anda inginkan yang muncul.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}