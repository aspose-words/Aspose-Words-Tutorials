---
category: general
date: 2026-10-13
description: Cara memformat grafik di Word dengan C# dengan menerapkan format angka
  khusus, seperti mata uang, pada sumbu grafik. Contoh kode langkah demi langkah disertakan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: id
lastmod: 2026-10-13
og_description: Cara memformat diagram di Word dengan C# memungkinkan Anda menerapkan
  format angka khusus pada sumbu diagram, memastikan nilai muncul sebagai mata uang,
  persentase, atau pola apa pun yang Anda butuhkan. Ikuti panduan langkah demi langkah.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Cara memformat grafik di Word dengan C# – format angka khusus
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Cara memformat diagram di Word dengan C# dan format angka khusus
url: /id/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memformat chart di Word dengan C# dan format angka khusus

Memformat chart di Word dengan C# adalah kebutuhan umum ketika Anda perlu menyajikan data secara profesional. Panduan ini menunjukkan cara menerapkan format angka khusus pada sumbu chart menggunakan **Aspose.Words for .NET**, sehingga nilai-nilai muncul persis seperti yang Anda harapkan.

Anda akan belajar cara memuat file DOCX, menemukan chart pertama, membaca format saat ini, dan kemudian menetapkan pola baru seperti mata uang dengan dua desimal. Tutorial ini juga mencakup cara mengubah format sumbu chart untuk seri tambahan dan cara mengatur ulang format jika diperlukan.

## Prasyarat

* .NET 6.0 atau yang lebih baru terinstal  
* Proyek Visual Studio 2022 (atau IDE apa pun yang mendukung .NET)  
* Paket NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Dokumen Word (`input.docx`) yang berisi setidaknya satu chart

Anda dapat menambahkan paket dengan perintah berikut:

```bash
dotnet add package Aspose.Words
```

## Cara memformat chart di Word menggunakan Aspose.Words

Program lengkap berikut menunjukkan setiap langkah yang diperlukan untuk **memformat chart** nilai sumbu. Simpan file sebagai `Program.cs` dan jalankan dari command line atau IDE Anda.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Penjelasan setiap langkah

| Langkah | Mengapa penting | Kode utama |
|------|----------------|----------|
| **Muat dokumen** | Anda memerlukan objek `Document` untuk bekerja dengan file Word. | `new Document("input.docx")` |
| **Ambil chart** | Objek `Chart` disimpan sebagai node `Shape`; casting memungkinkan Anda menggunakan API khusus chart. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Akses X‑values** | Pemformatan sumbu diterapkan pada koleksi nilai dari sebuah seri data. | `chart.ChartData.Series[0].XValues` |
| **Baca format saat ini** | Mengetahui `FormatCode` yang ada membantu Anda memutuskan apakah akan mengganti atau menambahkannya. | `xValues.FormatCode` |
| **Tetapkan format khusus** | Properti `FormatCode` menerima pola apa pun yang kompatibel dengan Excel, memungkinkan mata uang, persentase, tanggal, dll. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Simpan dokumen** | Menyimpan perubahan menuliskan format sumbu baru kembali ke file DOCX. | `doc.Save("output_formatted.docx")` |

Menjalankan program menghasilkan `output_formatted.docx`. Buka file tersebut di Word dan Anda akan melihat nilai sumbu X chart ditampilkan sebagai **$1,234.00**, **$2,345.00**, … bukan angka biasa.

## Terapkan format angka khusus pada sumbu chart

Jika Anda perlu **menerapkan format angka khusus** pada sumbu Y atau pada seri tambahan, prosesnya identik—cukup targetkan koleksi yang berbeda:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Pro tip:** Gunakan tanda kutip ganda di dalam string format untuk menyisipkan karakter literal (misalnya, `"$"` untuk mata uang). Escape tanda kutip seperti yang ditunjukkan di atas.

## Kata format angka khusus – menangani locale Word

Word menghormati locale dokumen saat menafsirkan format angka. Jika dokumen menggunakan locale non‑AS, Anda mungkin perlu menyesuaikan string format:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Menguji format pada dokumen dengan pengaturan bahasa Jerman mengonfirmasi bahwa nilai muncul sebagai **€ 1.234,00**.

## Cara mengatur properti chart secara programatis

Selain pemformatan sumbu, Anda sering ingin **mengatur chart** judul, legenda, atau label data. Berikut cuplikan singkat yang menunjukkan cara mengatur judul chart setelah Anda memformat sumbu:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Menggabungkan ini dengan format angka khusus memberi Anda chart yang sepenuhnya dipoles dan siap untuk pelaporan.

## Ubah format sumbu chart secara dinamis berdasarkan input pengguna

Dalam aplikasi dunia nyata Anda mungkin membiarkan pengguna memilih format pada saat runtime. Metode berikut mengenkapsulasi logika pemformatan:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Anda dapat memanggil `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` untuk mata uang atau `SetAxisFormat(chart, 0, "0%")` untuk persentase. Pendekatan ini menjaga kode utama Anda tetap bersih dan mendukung ekstensi di masa depan.

## Kasus tepi dan jebakan umum

| Situasi | Hal yang harus diwaspadai | Perbaikan yang disarankan |
|-----------|-------------------|---------------|
| Dokumen berisi **tidak ada chart** | `GetChild` mengembalikan `null`, menyebabkan pengecualian cast. | Periksa `null` sebelum casting (lihat contoh). |
| Beberapa chart dalam dokumen yang sama | Kode selalu mengambil chart pertama (`indeks 0`). | Lakukan loop melalui `doc.GetChildNodes(NodeType.Shape, true)` dan filter berdasarkan `ShapeType.Chart`. |
| Seri **tanpa X‑values** (misalnya, chart pai) | Mengakses `XValues` dapat melempar `ArgumentOutOfRangeException`. | Pastikan `Series[i].XValues` tidak kosong sebelum memformat. |
| Ketidaksesuaian locale | Simbol mata uang mungkin muncul tidak tepat. | Secara eksplisit set `xValues.FormatCode` dengan simbol locale yang sesuai. |

## Output yang diharapkan

Setelah menjalankan program contoh, buka **output_formatted.docx**. Sumbu X chart harus menampilkan angka dalam format khusus yang dipilih. Untuk contoh mata uang, label sumbu terlihat seperti:

```
$1,000.00
$2,000.00
$3,000.00
```

Jika Anda menerapkan format persentase pada nilai Y, label sumbu Y muncul sebagai:

```
10%
20%
30%
```

## Kesimpulan

Tutorial ini menunjukkan **cara memformat chart** di Word dengan C# dengan **menerapkan format angka khusus** pada nilai sumbu. Anda kini memiliki pola yang dapat digunakan kembali untuk mengatur mata uang, persentase, atau pola numerik lainnya, serta panduan untuk menangani locale, banyak seri, dan input pengguna yang dinamis.

Selanjutnya, Anda mungkin ingin menjelajahi **cara mengatur chart** judul, label data, atau bahkan mengekspor chart sebagai gambar menggunakan `ChartRenderer`. Topik tersebut dibangun langsung dari konsep yang dibahas di sini dan akan membantu Anda membuat solusi pelaporan yang sepenuhnya otomatis.

---

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Format Angka untuk Sumbu dalam Chart](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Format Angka pada Label Data dalam Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Format Sumbu X Sekunder dan Atur Unit Tampilan ke Ribuan dalam Chart Garis Word Menggunakan Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}