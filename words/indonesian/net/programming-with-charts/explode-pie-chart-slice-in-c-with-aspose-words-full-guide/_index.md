---
category: general
date: 2026-07-19
description: Memisahkan irisan diagram lingkaran menggunakan Aspose.Words untuk C#.
  Pelajari cara memisahkan irisan diagram lingkaran, menyesuaikan ukuran lubang donat,
  dan mengubah titik data diagram dengan cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: id
lastmod: 2026-07-19
og_description: Memisahkan irisan diagram lingkaran dengan Aspose.Words untuk C#.
  Panduan ini menunjukkan cara memisahkan irisan diagram lingkaran, menyesuaikan ukuran
  lubang donat, dan mengubah titik data diagram secara efisien.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Mengekspansi Irisan Diagram Lingkaran di C# – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Memisahkan Irisan Diagram Lingkaran di C# dengan Aspose.Words – Panduan Lengkap
url: /id/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengekspansi Irisan Diagram Pai di C# dengan Aspose.Words – Panduan Lengkap

Pernah bertanya-tanya bagaimana cara **explode pie chart slice** dalam dokumen Word menggunakan C#? Anda tidak sendirian. Baik Anda menyiapkan presentasi penjualan maupun memvisualisasikan hasil survei, irisan yang diekspansi dapat menarik perhatian tepat di tempat yang Anda inginkan. Pada tutorial ini kami akan membahas seluruh proses—memuat dokumen, mengambil diagram, mengekspansi irisan pertama, menyesuaikan lubang donat, dan bahkan mengubah titik data diagram.

Kami juga akan menyisipkan konsep sekunder yang mungkin Anda cari: **how to explode pie slice**, **adjust doughnut hole size**, dan **change chart data points**. Tanpa basa‑basi, hanya solusi lengkap yang siap disalin‑tempel.

---

## Apa yang Anda Butuhkan

Sebelum kita mulai, pastikan Anda memiliki:

- **Aspose.Words for .NET** (versi terbaru per 2026‑07‑19). Anda dapat mengunduhnya dari NuGet dengan `Install-Package Aspose.Words`.
- Proyek **.NET 6+** (atau .NET Framework 4.7.2+ jika masih menggunakan versi lama).
- File Word (`Chart.docx`) yang sudah berisi diagram pai atau donat. Jika belum ada, buat diagram cepat di Word dan simpan.

Itu saja—tanpa pustaka tambahan, tanpa interop COM, hanya kode terkelola murni.

---

## Mengekspansi Irisan Diagram Pai – Implementasi Langkah‑per‑Langkah

Di bawah ini kami membagi tugas menjadi langkah‑langkah kecil. Setiap bagian memiliki judul yang jelas, cuplikan kode, dan penjelasan singkat tentang *mengapa* kami melakukan hal tersebut.

### Langkah 1: Instal dan Referensikan Aspose.Words

Hal pertama yang harus dilakukan, tambahkan paket Aspose.Words ke proyek Anda. Di Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Pro tip:** Jika Anda menggunakan UI NuGet bawaan Visual Studio, cari “Aspose.Words” dan klik Install. Ini memastikan Anda mendapatkan perbaikan bug terbaru serta kemampuan bekerja dengan diagram secara langsung.

### Langkah 2: Muat Dokumen Word yang Memuat Diagram

Kita memerlukan objek `Document` yang menunjuk ke file `.docx` berisi diagram yang ingin dimodifikasi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Mengapa ini penting:** `Document` adalah titik masuk untuk setiap operasi di Aspose.Words. Dengan memeriksa keberadaan diagram di awal, kita menghindari referensi null saat mencoba mengekspansi irisan.

### Langkah 3: Ambil Node Diagram Pertama

Sebagian besar contoh mengasumsikan hanya ada satu diagram, jadi kami akan mengambil yang pertama. Jika Anda memiliki banyak diagram, sesuaikan indeksnya.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Catatan:** Casting ke `Chart` aman setelah kami memastikan diagram ada. Objek ini memberi akses ke seri, titik data, dan pengaturan khusus tipe diagram.

### Langkah 4: Mengekspansi Irisan Pertama pada Diagram Pai

Inilah bintang utama—**how to explode pie slice**. Kami akan mengatur properti `Exploded` pada titik data pertama.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Mengapa ini berhasil:** `Exploded` memberi tahu Word untuk menarik irisan tersebut menjauh dari pusat, menciptakan efek “pie chart exploded” klasik. Properti ini bertipe boolean, jadi mengaturnya ke `true` sudah cukup.

### Langkah 5: Sesuaikan Ukuran Lubang Donat (Jika Diagram Donat)

Jika diagram Anda berupa donat, Anda mungkin ingin **adjust doughnut hole size**. Ukuran lubang merupakan persentase dari radius diagram.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Apa arti angkanya:** Nilai `30` berarti lingkaran dalam akan menempati 30 % dari total radius, meninggalkan cincin luar yang lebih tebal.

### Langkah 6: Ubah Titik Data Diagram (Opsional)

Kadang‑kadang Anda perlu **change chart data points**—misalnya Anda telah memperbarui angka dasar dan ingin visualnya mencerminkan perubahan tersebut.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Mengapa Anda melakukannya:** Mengubah nilai titik data secara otomatis menghitung ulang persentase irisan, menjaga diagram tetap akurat tanpa harus mengedit manual di Word.

### Langkah 7: Simpan Dokumen yang Telah Dimodifikasi

Akhirnya, tuliskan perubahan ke disk. Anda dapat menimpa file asli atau membuat file baru—sesuai kebutuhan.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Tip:** Gunakan `SaveFormat.Docx` jika Anda ingin menentukannya secara eksplisit, namun `Save(string)` otomatis mendeteksi format dari ekstensi file.

---

## Hasil yang Diharapkan

Saat Anda membuka `FormattedChart.docx` di Microsoft Word, Anda akan melihat:

- Irisan pertama pada diagram pai **dieksplasi** ke luar.
- Jika diagramnya donat, lubang tengah kini menempati **30 %** dari radius.
- Setiap titik data yang diubah menampilkan nilai baru yang Anda tetapkan.

Berikut contoh tampilan irisan yang diekspansi (gambar hanya untuk ilustrasi).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Alt text:* **exploded pie chart slice** menunjukkan segmen yang ditarik menjauh dalam dokumen Word.

---

## Pertanyaan Umum & Kasus Pojok

**Bagaimana jika diagram bukan pai atau donat?**  
Kode memeriksa `ChartType` sebelum menerapkan `Exploded` atau `HoleSize`. Untuk diagram batang, garis, atau area properti tersebut tidak ada, sehingga logika secara aman melewatinya.

**Bisakah saya mengekspansi beberapa irisan?**  
Tentu saja. Loop melalui `chart.PieChartData.Series[0].DataPoints` dan set `Exploded = true` pada indeks mana pun yang Anda inginkan.

**Apakah saya perlu khawatir tentang format angka spesifik budaya?**  
Aspose.Words menyimpan nilai numerik sebagai double, terlepas dari locale, sehingga Anda tidak akan mengalami masalah koma vs titik.

**Bagaimana dengan diagram yang tertanam di header/footer?**  
Gunakan `doc.GetChildNodes(NodeType.Chart, true)` untuk mengambil semua diagram, lalu periksa `ParentNode` masing‑masing untuk mengetahui lokasinya. Logika eksplorasi yang sama tetap berlaku.

---

## Kesimpulan

Anda kini memiliki solusi lengkap yang siap disalin‑tempel untuk **explode pie chart slice** menggunakan Aspose.Words di C#. Kami telah membahas seluruh alur kerja—dari memuat dokumen, mengambil diagram, mengekspansi irisan, **menyesuaikan ukuran lubang donat**, hingga **mengubah titik data diagram** dan akhirnya menyimpan file.

Silakan bereksperimen: coba ekpansi irisan lain, ubah ukuran lubang menjadi 45 %, atau perbarui beberapa titik data sekaligus. API Aspose.Words membuat penyesuaian ini mudah, dan perubahan langsung terlihat saat Anda membuka file Word.

---

### Apa Selanjutnya?

- **Gaya pada irisan yang diekspansi** (ubah warna isi, border, atau tambahkan label data). Cari “Aspose.Words chart formatting”.
- **Otomatisasi pemrosesan batch** untuk banyak dokumen—loop melalui folder, ekpansi irisan, dan simpan versi baru.
- **Gabungkan dengan Aspose.Slides** jika Anda memerlukan diagram yang sama dalam presentasi PowerPoint.

Punya pertanyaan lebih lanjut tentang manipulasi diagram, atau ingin mendalami tipe diagram lain? Tinggalkan komentar di bawah, dan selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}