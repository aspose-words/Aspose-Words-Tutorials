---
category: general
date: 2026-10-13
description: Pelajari cara menyesuaikan label diagram secara programatis dalam dokumen
  Word menggunakan C#. Panduan ini mencakup manipulasi diagram Aspose.Words dan penyelarasan
  label.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: id
lastmod: 2026-10-13
og_description: Sesuaikan label diagram secara programatis dalam dokumen Word menggunakan
  C#. Ikuti tutorial lengkap ini untuk mengubah penempatan label, perataan, dan lainnya.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Sesuaikan label grafik secara programatik di Word – Panduan langkah demi
  langkah C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Menyesuaikan label grafik secara programatis dalam dokumen Word dengan C#
url: /id/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menyesuaikan label diagram secara programatis dalam dokumen Word dengan C#

Jika Anda perlu **menyesuaikan label diagram secara programatis** dalam dokumen Word, panduan ini menunjukkan secara tepat cara melakukannya dengan C#. Baik Anda menghasilkan laporan, mengotomatisasi dasbor, atau menyesuaikan templat, Anda akan melihat contoh lengkap yang dapat dijalankan yang mengubah penempatan dan perataan label diagram di dalam file .docx.

Anda juga akan belajar cara menggunakan teknik **manipulasi diagram Aspose.Words**, menangani beberapa seri, dan menghindari jebakan umum saat bekerja dengan objek **label data diagram C#**.

## Prasyarat

* .NET 6.0 (atau lebih baru) terpasang  
* Visual Studio 2022 (atau IDE C# apa pun)  
* Paket NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Dokumen Word (`input.docx`) yang berisi setidaknya satu diagram  

Item-item ini diperlukan untuk **contoh diagram dokumen Word** yang akan kami modifikasi.

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek konsol baru dan tambahkan direktif `using` yang diperlukan. Ini menyiapkan lingkungan untuk **menyesuaikan label diagram secara programatis**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Mengapa langkah ini?*  
Memuat dokumen memberi Anda akses ke pohon internal **contoh diagram dokumen Word**, di mana diagram disimpan sebagai node shape.

## Langkah 2: Temukan shape diagram pertama

Diagram disimpan sebagai node `Shape`. Kode berikut mengambil diagram pertama dalam dokumen, yang menjadi target untuk penyesuaian label kami.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Mengapa langkah ini?*  
Metode `GetChild` mencari secara rekursif (`true`) dan mengembalikan node pertama bertipe `Shape`. Meng-cast ke `Chart` memungkinkan kita bekerja dengan API khusus diagram.

## Langkah 3: Akses label data yang ingin Anda ubah

Setiap seri dalam diagram memiliki koleksi label data. Untuk diagram sederhana, label pertama biasanya sudah cukup. Kode di bawah menunjukkan cara mengaksesnya.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Mengapa langkah ini?*  
`ChartSeries` mewakili serangkaian titik. `DataLabelCollection` menyimpan label untuk seri tersebut, memungkinkan kontrol tepat atas penempatan dan perataan.

## Langkah 4: Ubah penempatan dan perataan label

Sekarang kita **menyesuaikan label diagram secara programatis** dengan mengatur posisi, perataan horizontal, dan perataan vertikal. Properti ini sesuai dengan opsi yang Anda lihat di UI Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Mengapa pengaturan ini?*  

* `OutsideEnd` menempatkan label tepat di luar ujung setiap batang atau kolom, meningkatkan keterbacaan.  
* `HorizontalAlignment.Center` menjaga teks tetap berada di tengah titik, sementara `VerticalAlignment.Top` menyelaraskan tepi atas label dengan titik data, mencegah tumpang tindih dengan elemen lain.

### Tips Pro
Jika sebuah diagram memiliki beberapa seri, lakukan perulangan melalui `chart.Series` dan terapkan pengaturan yang sama ke setiap `DataLabelCollection`. Ini memastikan tampilan konsisten di seluruh diagram.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Langkah 5: Simpan dokumen yang telah dimodifikasi

Setelah menyesuaikan label, simpan perubahan ke file baru. Ini menyelesaikan proses **mengubah posisi label diagram**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Saat Anda membuka `output.docx`, Anda akan melihat bahwa setiap label diagram telah dipindahkan ke luar ujung titik datanya, terpusat secara horizontal dan teralign ke atas secara vertikal.

## Kasus tepi dan variasi

| Situation | What to watch for | Recommended approach |
|-----------|-------------------|----------------------|
| **Beberapa diagram** dalam dokumen yang sama | `GetChild` hanya mengembalikan diagram pertama. | Gunakan `doc.GetChildNodes(NodeType.Shape, true)` untuk mengiterasi semua shape diagram. |
| **Seri tanpa label data** | `DataLabelCollection` mungkin kosong. | Periksa `series.HasDataLabels` sebelum mengakses koleksi. |
| **Berbagai tipe diagram** (pie, line, scatter) | Tidak semua nilai `DataLabelPosition` valid. | Gunakan `DataLabelPosition.Auto` untuk diagram yang menentukan penempatan terbaik secara otomatis. |
| **Lokalisasi** | Konstanta perataan bersifat netral bahasa, tetapi teks yang dirender mungkin memerlukan dukungan kanan‑ke‑kiri. | Setel `dataLabel.TextDirection` jika Anda memerlukan bahasa RTL. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Ganti `YOUR_DIRECTORY` dengan jalur folder yang sebenarnya.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Hasil yang diharapkan:** Membuka `output.docx` menunjukkan setiap label diagram diposisikan di luar titik data, terpusat secara horizontal, dan teralign ke atas—tepat efek **menyesuaikan label diagram secara programatis** yang Anda tulis.

## Kesimpulan

Anda sekarang tahu cara **menyesuaikan label diagram secara programatis** dalam dokumen Word menggunakan C#. Tutorial ini mencakup:

* Memuat dokumen dengan **manipulasi diagram Aspose.Words**  
* Mengakses **label data diagram C#**  
* Mengubah **posisi label diagram** dan perataan  
* Menyimpan file dan menangani kasus tepi umum  

Dari sini Anda dapat menjelajahi skenario yang lebih maju, seperti menyesuaikan font label, menambahkan pemformatan bersyarat, atau memperbarui beberapa diagram dalam proses batch. Bereksperimenlah dengan berbagai opsi `DataLabelPosition` untuk menemukan gaya yang paling cocok dengan laporan Anda.

---

*Siap meningkatkan pipeline pelaporan otomatis Anda? Coba tambahkan format angka khusus ke label atau ekspor diagram sebagai gambar untuk digunakan dalam PDF.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Atur Label Data Seragam dalam Diagram Kolom Menggunakan Aspose.Words untuk .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Atur Opsi Default untuk Label Data dalam Diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Perbarui Data Seri Diagram dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}