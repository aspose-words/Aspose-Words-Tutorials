---
category: general
date: 2026-09-11
description: Tutorial mengedit label diagram yang menunjukkan cara mengubah posisi
  label diagram, menyesuaikan label data diagram, menyembunyikan nama kategori diagram,
  dan menampilkan nilai label diagram dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: id
lastmod: 2026-09-11
og_description: Tutorial mengedit label grafik memandu Anda melalui mengubah posisi
  label grafik, menyesuaikan label data grafik, menyembunyikan nama kategori grafik,
  dan menampilkan nilai label grafik menggunakan Aspose.Words untuk .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Tutorial mengedit label grafik – sesuaikan label grafik Word di C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Tutorial mengedit label grafik – memodifikasi label grafik Word di C#
url: /id/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial mengedit label diagram – memodifikasi label diagram Word di C#

Jika Anda perlu **edit chart label tutorial** untuk dokumen Word, panduan ini menunjukkan secara tepat cara mengubah posisi label diagram, menyesuaikan label data diagram, menyembunyikan nama kategori diagram, dan menampilkan nilai label diagram menggunakan Aspose.Words for .NET. Anda akan melihat contoh lengkap yang dapat dijalankan yang dapat Anda masukkan ke dalam proyek C# apa pun.

Bekerja dengan label diagram adalah kebutuhan umum saat menghasilkan laporan, faktur, atau dasbor secara programatis. Tutorial ini mencakup setiap langkah—dari memuat dokumen hingga menyimpan perubahan—sehingga Anda dapat menghasilkan diagram yang rapi tanpa harus mengedit secara manual.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 atau yang lebih baru terpasang  
* Lisensi Aspose.Words for .NET yang valid (atau kunci evaluasi sementara)  
* Visual Studio 2022 atau IDE kompatibel C# lainnya  
* File Word (`Chart.docx`) yang berisi setidaknya satu diagram  

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Langkah 1: Siapkan proyek dan impor namespace

Buat aplikasi konsol baru dan tambahkan paket NuGet Aspose.Words:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Buka `Program.cs` dan impor namespace yang diperlukan:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Namespace ini memberi Anda akses ke kelas `Document` untuk menangani file Word dan kelas `Chart` untuk memanipulasi elemen diagram.

## Langkah 2: Muat dokumen Word yang berisi diagram

Baris pertama yang dapat dijalankan memuat dokumen sumber. Ganti `YOUR_DIRECTORY` dengan jalur sebenarnya tempat `Chart.docx` berada.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Memuat dokumen membuat representasi dalam memori yang dapat Anda telusuri dan ubah.

## Langkah 3: Dapatkan diagram pertama dalam dokumen

Diagram disimpan sebagai node anak dengan tipe `NodeType.Chart`. Metode `GetChild` menelusuri pohon dokumen dan mengembalikan diagram yang ingin Anda edit.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Jika dokumen berisi beberapa diagram, Anda dapat mengubah indeks untuk menargetkan diagram lain.

## Langkah 4: Akses dan sesuaikan label data dari seri pertama

Setiap seri diagram memiliki objek `DataLabel` yang mengontrol bagaimana label ditampilkan. Kode di bawah ini memperlihatkan empat penyesuaian utama yang diperlukan oleh kata kunci sekunder tutorial.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Mengapa pengaturan ini penting**

* `DataLabelPosition.Center` memindahkan label dari lokasi default di luar titik ke tengah titik data, sehingga diagram lebih mudah dibaca ketika titik-titik berdekatan.  
* Menetapkan `Separator` khusus memungkinkan Anda mengontrol cara nama seri, nilai, dan bagian lainnya digabungkan.  
* Menyembunyikan nama kategori (`ShowCategoryName = false`) mengurangi kekacauan visual ketika kategori sudah jelas dari sumbu.  
* Mengaktifkan `ShowValue` memastikan nilai data sebenarnya terlihat, yang sering diperlukan untuk laporan keuangan atau statistik.

## Langkah 5: Simpan dokumen yang telah dimodifikasi

Setelah menyesuaikan properti label, simpan perubahan ke file baru:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

File baru (`CustomLabelChart.docx`) berisi tata letak diagram yang sama tetapi dengan tampilan label yang Anda definisikan.

## Kode sumber lengkap

Berikut adalah program lengkap yang siap dijalankan. Salin ke `Program.cs`, sesuaikan jalur file, dan jalankan proyek.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Hasil yang diharapkan

Buka `CustomLabelChart.docx` di Microsoft Word. Anda akan melihat label seri pertama diagram berada di tengah setiap titik data, menampilkan hanya nilai numerik, dan menggunakan “; ” sebagai pemisah. Nama kategori tidak lagi muncul di samping nilai.

## Pertanyaan umum dan kasus tepi

| Question | Answer |
|----------|--------|
| **What if the document contains no chart?** | Contoh memeriksa apakah diagram `null` dan keluar dengan pesan konsol secara elegan. |
| **Can I edit labels for multiple series?** | Ya. Lakukan perulangan pada `chart.Series` dan terapkan pengaturan `DataLabel` yang sama ke setiap `Series[i].DataLabel`. |
| **How do I change the font style of the label?** | Gunakan `label.Font` (misalnya, `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **Is `DataLabelPosition.Center` supported for all chart types?** | Sebagian besar tipe diagram 2‑D mendukungnya. Untuk diagram 3‑D, beberapa posisi mungkin diabaikan oleh Word. |
| **Do I need a license for Aspose.Words?** | Mode evaluasi berfungsi tetapi menambahkan watermark. Lisensi menghilangkan watermark dan membuka semua fungsi. |

## Tips profesional

* **Batch processing:** Bungkus logika pemuatan dan penyimpanan dalam metode yang menerima jalur input dan output. Ini memudahkan pemrosesan puluhan dokumen dalam sebuah loop.  
* **Performance:** Gunakan satu instance `Document` saat memodifikasi beberapa diagram dalam file yang sama untuk menghindari I/O berulang.  
* **Testing:** Verifikasi perubahan label dengan mengotomatiskan perbandingan visual (misalnya, menggunakan penampil Word tanpa tampilan) jika Anda perlu memastikan output dalam pipeline CI.

## Langkah selanjutnya

Sekarang Anda sudah menguasai dasar **edit chart label tutorial**, pertimbangkan untuk mengeksplorasi:

* **Change chart label position** untuk seri lain atau tipe diagram yang berbeda  
* **Customize chart data label** format seperti format angka, warna font, atau isi latar belakang  
* **Hide chart category name** sambil tetap menampilkan nama seri untuk diagram multi‑seri  
* **Show chart label value** bersama nilai persentase untuk diagram pai  

Topik-topik ini memperdalam kontrol Anda atas estetika diagram Word dan mempersiapkan Anda untuk skenario pelaporan lanjutan.

---

*Selamat coding! Jika Anda menemukan tutorial ini bermanfaat, bagikan kepada rekan tim atau kontribusikan perbaikan di GitHub.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Sesuaikan Label Data Diagram](/words/english/net/programming-with-charts/chart-data-label/)
- [Label Data Diagram](/words/german/net/programming-with-charts/chart-data-label/)
- [Label Data Diagram](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}