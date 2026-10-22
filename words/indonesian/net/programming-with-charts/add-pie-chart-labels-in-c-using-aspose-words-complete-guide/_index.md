---
category: general
date: 2026-07-20
description: Tambahkan label diagram lingkaran dengan Aspose.Words untuk .NET. Pelajari
  cara mengubah label diagram lingkaran, menampilkan label persentase, dan memperbarui
  label seri diagram dengan cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: id
lastmod: 2026-07-20
og_description: Tambahkan label diagram lingkaran di C# dengan Aspose.Words. Kuasai
  mengubah label diagram lingkaran, menampilkan label persentase, dan memperbarui
  label seri diagram hanya dalam beberapa langkah.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Menambahkan label diagram lingkaran di C# – Tutorial Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Menambahkan label diagram lingkaran di C# menggunakan Aspose.Words – Panduan
  Lengkap
url: /id/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan label diagram lingkaran di C# menggunakan Aspose.Words – Panduan Lengkap

Perlu **menambahkan label diagram lingkaran** ke dokumen Word menggunakan C#? Dengan Aspose.Words Anda dapat dengan mudah **mengubah label diagram lingkaran** dan **menampilkan persentase diagram lingkaran** langsung di dalam file—tanpa harus mengutak-atik secara manual di Word.  

Dalam tutorial ini kami akan menjelaskan langkah‑langkah tepat untuk **menampilkan label persentase**, memposisikan ulangnya, dan bahkan **memperbarui label seri diagram** untuk data dinamis. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat dimasukkan ke proyek .NET mana pun.

> **Pratinjau cepat:** Setelah mengikuti panduan, membuka file `.docx` yang disimpan akan menampilkan diagram lingkaran di mana setiap irisan diberi label dengan persentasenya, diposisikan di luar irisan untuk keterbacaan maksimal.

---

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi terbaru per 2026). Anda dapat mengunduhnya dari NuGet: `Install-Package Aspose.Words`.
- Sebuah **dokumen Word** yang sudah berisi diagram lingkaran atau donat (kami sebut `Chart.docx`).
- Pengetahuan dasar tentang **C#** dan Visual Studio (atau IDE favorit Anda).

Itu saja—tanpa perpustakaan tambahan, tanpa interop COM, hanya kode terkelola murni.

---

## Tambahkan label diagram lingkaran – Implementasi Lengkap

Berikut adalah program konsol C# **lengkap dan dapat dijalankan** yang memuat dokumen, memodifikasi diagram lingkaran pertama, dan menyimpan hasilnya. Setiap baris diberi komentar sehingga Anda memahami **mengapa** kami melakukan apa yang kami lakukan, bukan hanya **apa**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Hasil yang Diharapkan

Buka `ChartWithCustomLabels.docx` di Microsoft Word. Anda akan melihat diagram lingkaran **dengan label persentase yang diposisikan di luar setiap irisan**. Labelnya terlihat seperti “35 %”, “20 %”, dll., sehingga diagram langsung dapat dipahami.

---

## Ubah label diagram lingkaran: posisi dan format

Jika Anda hanya perlu **mengubah label diagram lingkaran** tanpa menampilkan persentase, Anda dapat menyesuaikan properti `Position` ke salah satu berikut:

| Enum Posisi   | Efek Visual |
|---------------|-------------|
| `InsideEnd`   | Label berada di dalam irisan, tepat di tepi. |
| `Center`      | Label muncul di tengah irisan (bagus untuk diagram kecil). |
| `OutsideEnd`  | Label berada di luar irisan, terhubung dengan garis pemimpin (default kami). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Tips profesional:** `OutsideEnd` bekerja paling baik ketika diagram memiliki banyak irisan; ini mencegah teks saling tumpang tindih.

---

## Tampilkan label persentase pada diagram lingkaran

Properti `ShowPercentage` adalah **bendera boolean**. Menyetelnya ke `true` memberi tahu Aspose.Words untuk menghitung kontribusi masing‑masing irisan berdasarkan sumber data yang mendasarinya.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Anda juga dapat menggabungkannya dengan `ShowValue` jika Anda memerlukan angka mentah **dan** persentase:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Ketika kedua bendera diaktifkan, label akan terlihat seperti “45 % (120)”.

---

## Perbarui label seri diagram untuk data dinamis

Sering kali Anda akan menghasilkan diagram secara dinamis—misalnya penjualan bulanan atau hasil survei. Untuk **memperbarui label seri diagram** secara programatik, ubah koleksi `Series` sebelum Anda menyentuh label data:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Potongan kode ini menunjukkan cara **memperbarui label seri diagram** untuk seri apa pun, bukan hanya yang pertama. Ini berguna saat Anda membuat laporan yang menggabungkan data aktual vs. perkiraan.

---

## Kasus Tepi & Kesalahan Umum

| Situasi | Hal yang Perlu Diperhatikan | Perbaikan |
|-----------|-------------------|-----|
| **Diagram bukan pie/donut** | `Position` mungkin tidak memberikan efek visual. | Pastikan `chart.Type` adalah `ChartType.Pie` atau `ChartType.Doughnut`. |
| **No chart found** | `GetChild` mengembalikan `null`. | Tambahkan klausa penjaga (lihat kode) dan catat pesan yang membantu. |
| **Versi Word lama** | Beberapa fitur label diabaikan. | Simpan sebagai `.docx` (format modern) untuk memastikan dukungan penuh. |
| **Banyak irisan** | Label dapat tumpang tindih bahkan dengan `OutsideEnd`. | Pertimbangkan mengurangi jumlah irisan atau memperbesar ukuran diagram. |

---

## Contoh Lengkap yang Berfungsi (Salin‑Tempel)

Berikut adalah **seluruh program** yang dapat Anda salin ke proyek konsol baru. Cukup ganti `YOUR_DIRECTORY` dengan folder yang berisi `Chart.docx`.



## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Atur Opsi Default untuk Label Data dalam Diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Sesuaikan Seri Diagram Tunggal dalam Diagram](/words/english/net/programming-with-charts/single-chart-series/)
- [Sisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}