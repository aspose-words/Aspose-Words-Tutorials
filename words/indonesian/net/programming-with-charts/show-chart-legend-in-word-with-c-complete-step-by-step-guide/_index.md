---
category: general
date: 2026-06-02
description: Tampilkan legenda diagram dalam dokumen Word menggunakan C#. Pelajari
  cara menambahkan legenda, menerapkan gaya diagram bawaan, dan menyesuaikan tampilan
  diagram Word dalam hitungan menit.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: id
og_description: Tampilkan legenda diagram di dokumen Word secara instan. Panduan ini
  memandu Anda menambahkan legenda, menerapkan gaya diagram bawaan, dan menangani
  kasus tepi.
og_title: Tampilkan Legenda Grafik di Word – Tutorial Lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Menampilkan Legenda Diagram di Word dengan C# – Panduan Lengkap Langkah demi
  Langkah
url: /id/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tampilkan Legenda Diagram di Word dengan C# – Panduan Lengkap Langkah‑per‑Langkah

Pernah bertanya-tanya **bagaimana cara menambahkan legenda** ke diagram yang berada di dalam dokumen Word? Anda bukan satu-satunya. Dalam banyak laporan, legenda yang hilang membuat data terlihat misterius, dan memperbaikinya tidak seharusnya menjadi beban.  

Dalam tutorial ini kami akan **menampilkan legenda diagram** dalam file Word menggunakan Aspose.Words for .NET, menerapkan gaya diagram preset, dan memastikan legenda muncul tepat di tempat yang Anda inginkan. Pada akhir tutorial Anda akan memiliki contoh siap‑jalankan yang dapat Anda masukkan ke proyek C# mana pun.

## Apa yang Dibahas dalam Panduan Ini

Kami akan membahas seluruh alur kerja:

1. Memuat file *.docx* yang sudah ada dan sudah berisi diagram.  
2. Mengambil diagram pertama (atau diagram mana pun yang Anda targetkan).  
3. **Menerapkan gaya diagram preset** untuk memberikan tampilan yang profesional.  
4. **Menampilkan legenda diagram**, menempatkannya di sisi kanan, dan menangani kasus khusus seperti diagram Waterfall.  
5. Menyimpan dokumen yang telah dimodifikasi.

Tidak ada alat eksternal, tidak ada pengaturan manual melalui UI—hanya kode murni. Prasyarat satu-satunya adalah referensi ke paket NuGet Aspose.Words (versi 23.10 atau lebih baru) dan pemahaman dasar tentang C#.

---

## Prasyarat

- .NET 6.0 atau lebih baru (contoh ini juga bekerja dengan .NET Framework 4.7.2).  
- Perpustakaan Aspose.Words for .NET terpasang (`Install-Package Aspose.Words`).  
- File Word (`input.docx`) yang sudah berisi setidaknya satu diagram.  
- Visual Studio, Rider, atau IDE apa pun yang Anda sukai.

---

## Langkah 1: Siapkan Proyek dan Muat Dokumen

Pertama, buat aplikasi console (atau integrasikan kode ke dalam proyek yang sudah ada). Tambahkan pernyataan `using` dan muat file `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Mengapa ini penting:** Memuat dokumen adalah dasar. Tanpa instance `Document` Anda tidak dapat mengakses objek diagram yang disediakan oleh Aspose.Words.

---

## Langkah 2: Ambil Diagram Target

Diagram disimpan sebagai node di dalam pohon dokumen. Metode `GetChild` melakukan pencarian mendalam, memungkinkan kami mengambil diagram pertama terlepas dari letaknya (header, badan, footer, dll.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Tip:** Jika Anda memiliki beberapa diagram, ubah indeks `0` menjadi `1`, `2`, … atau iterasi melalui `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Langkah 3: Terapkan Gaya Visual Preset

Diagram yang menarik biasanya dimulai dengan sebuah gaya. Aspose.Words menyediakan puluhan gaya bawaan; `ChartStyle.Style12` adalah pilihan yang bersih dan modern.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Cara kerjanya:** Properti `Style` memetakan ke gaya diagram Word bawaan yang Anda lihat di UI. Memilih preset menghemat Anda dari mengatur warna, font, dan penanda secara manual.

---

## Langkah 4: Aktifkan Legenda dan Tempatkan

Sekarang untuk bintang utama—**menampilkan legenda diagram**. Kami mengaktifkan legenda, lalu menempelkannya di sisi kanan diagram.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Mengapa kanan?** Menempatkan legenda di kanan menjaga area data tetap lebar, yang sangat membantu untuk diagram batang atau kolom.

---

## Langkah 5: Tangani Diagram Waterfall (Kasus Khusus)

Diagram Waterfall berperilaku sedikit berbeda; legenda dapat tersembunyi secara default. Klausa penjaga berikut memastikan legenda terlihat ketika tipe diagram adalah Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Catatan kasus tepi:** Beberapa versi Word lama mengabaikan `HasLegend` untuk diagram Waterfall, sehingga secara eksplisit mengatur `Legend.Show` menjamin keterlihatan.

---

## Langkah 6: Simpan Dokumen yang Dimodifikasi

Akhirnya, tulis perubahan kembali ke disk. Anda dapat menimpa file asli atau membuat file baru.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Menjalankan program akan menghasilkan `output.docx` dengan legenda yang terlihat di kanan, bergaya `Style12`. Buka file tersebut di Word untuk memverifikasi hasilnya.

---

## Contoh Lengkap yang Berfungsi (Semua Langkah Digabungkan)

Berikut adalah kode lengkap yang siap dijalankan. Salin‑tempel ke `Program.cs` (atau file C# apa pun) dan sesuaikan jalur file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Output yang diharapkan:** Membuka `output.docx` menampilkan diagram asli dengan legenda yang rata kanan, bergaya `Style12` modern. Semua seri data diberi label jelas, membuat diagram langsung dapat dipahami.

---

## Pertanyaan yang Sering Diajukan (FAQ)

### Bagaimana menambahkan legenda ke diagram tertentu (bukan yang pertama)?

Ganti indeks `0` pada `GetChild(NodeType.Chart, 0, true)` dengan posisi berbasis nol dari diagram target Anda, atau lakukan loop melalui semua node diagram:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Bisakah saya menempatkan legenda di bagian bawah alih-alih di kanan?

Tentu saja. Cukup ubah enum `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Bagaimana jika diagram sudah memiliki legenda tetapi saya ingin menyembunyikannya?

Setel `HasLegend` menjadi `false`:

```csharp
chart.HasLegend = false;
```

### Apakah ini bekerja dengan Word 2010, 2016, dan versi selanjutnya?

Ya. Aspose.Words mengabstraksi versi Word yang mendasarinya, sehingga kode yang sama bekerja di semua file .docx modern.

---

## Tips Pro & Kesalahan Umum

- **Tips pro:** Setelah menerapkan gaya, Anda masih dapat menyesuaikan elemen individual (warna, label data) melalui koleksi `Chart.Series`. Gaya memberikan dasar yang kuat.  
- **Waspadai:** Jika diagram berada di dalam sel tabel, legenda mungkin terlihat sempit. Pertimbangkan meningkatkan ukuran diagram (`chart.Width`, `chart.Height`) sebelum menempatkan legenda.  
- **Catatan kinerja:** Memuat dokumen besar (ratusan MB) dapat memakan banyak memori. Gunakan `LoadOptions` dengan `LoadFormat.Docx` untuk mengurangi beban jika Anda hanya membutuhkan manipulasi diagram.

---

## Langkah Selanjutnya

Sekarang Anda tahu **cara menambahkan legenda** dan **menerapkan gaya diagram preset** di Word, Anda dapat menjelajahi:

- **Warna diagram khusus** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Pemformatan label data** (`chart.Series[i].HasDataLabel = true`).  
- **Mengekspor diagram sebagai gambar** (`chart.ToImage()`), berguna untuk disisipkan di tempat lain.  

Setiap topik ini dibangun di atas model objek yang sama, sehingga kurva pembelajarannya akan terasa ringan.

---

## Kesimpulan

Kami baru saja menunjukkan solusi bersih end‑to‑end untuk **menampilkan legenda diagram** dalam dokumen Word menggunakan C#. Dengan memuat dokumen, mengambil diagram, menerapkan gaya preset, mengaktifkan legenda, dan menangani keanehan Waterfall, Anda mendapatkan diagram yang dipoles siap untuk laporan bisnis apa pun.  

Jangan ragu bereksperimen dengan nilai `ChartStyle` lain atau posisi legenda—visualisasi data Anda pantas mendapatkan presentasi terbaik. Jika Anda mengalami kendala, tinggalkan komentar di bawah; selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Menyisipkan Diagram Kolom dalam Dokumen Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Menyembunyikan Sumbu Diagram dalam Dokumen Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Menggunakan API Diagram Word](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}