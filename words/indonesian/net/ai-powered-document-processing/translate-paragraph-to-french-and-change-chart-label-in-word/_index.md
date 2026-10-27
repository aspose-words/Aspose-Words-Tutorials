---
category: general
date: 2026-10-10
description: Terjemahkan paragraf ke dalam bahasa Prancis dan pelajari cara mengubah
  label data diagram, menyesuaikan label data diagram, serta menyimpan file docx yang
  telah diedit menggunakan Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: id
lastmod: 2026-10-10
og_description: Terjemahkan paragraf ke bahasa Prancis dan pelajari cara mengubah
  label data grafik, menyesuaikan label data grafik, serta menyimpan file docx yang
  telah diedit menggunakan Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Terjemahkan paragraf ke bahasa Prancis dan ubah label grafik di Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Terjemahkan paragraf ke bahasa Prancis dan ubah label diagram di Word
url: /id/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Terjemahkan paragraf ke Bahasa Prancis dan ubah label diagram di Word

Jika Anda perlu **menerjemahkan paragraf ke Bahasa Prancis** sambil memperbarui diagram di dalam dokumen Word yang sama, panduan ini menunjukkan cara melakukannya secara tepat. Menggunakan Aspose.Words AI Anda dapat menerjemahkan teks secara otomatis, kemudian mengubah label data diagram, dan akhirnya menyimpan file `.docx` yang telah diedit—semua dalam beberapa langkah sederhana.

Tutorial ini mencakup semua hal mulai dari memuat file sumber hingga menyimpan perubahan. Pada akhir tutorial Anda akan dapat menerjemahkan paragraf apa pun, menyesuaikan label data diagram, dan menghasilkan file Word baru yang siap didistribusikan. Tidak diperlukan skrip eksternal; seluruh alur kerja berada dalam satu program C#.

## Prasyarat

- .NET 6.0 atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
- Lisensi Aspose.Words untuk .NET (atau kunci evaluasi gratis)
- Akses internet untuk penerjemah Google AI (kelas `Translator` menggunakan API Google di balik layar)
- Dokumen Word (`input.docx`) yang berisi setidaknya satu paragraf dan satu diagram

## Langkah 1: Siapkan proyek dan impor namespace

Buat aplikasi konsol baru dan tambahkan paket NuGet Aspose.Words:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Sekarang sertakan namespace yang diperlukan di bagian atas `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Impor ini memberi Anda akses ke pemuatan dokumen, penerjemahan AI, dan fungsi pengeditan diagram.

## Langkah 2: Muat dokumen Word sumber

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Memuat file membuat representasi dalam memori yang dapat Anda query dan modifikasi tanpa menyentuh file asli di disk.

## Langkah 3: Terjemahkan paragraf pertama ke Bahasa Prancis

Paragraf pertama biasanya merupakan judul atau kalimat pengantar, sehingga menjadi kandidat yang baik untuk diterjemahkan. Kelas `Translator` mengabstraksi panggilan ke model AI Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Mengapa ini berhasil:**  
`paragraph.Runs.Clear()` menghapus semua run teks yang ada, memastikan terjemahan baru tidak digabungkan dengan konten lama. `new Run(document, translatedText)` membuat run baru yang mewarisi format paragraf.

## Langkah 4: Temukan diagram pertama dan sesuaikan label datanya

Diagram disimpan sebagai node `Shape` dengan tipe `NodeType.Shape`. Diagram pertama dapat diambil dengan `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Penjelasan langkah‑kunci:**

- `GetChild(NodeType.Shape, 0, true)` melakukan pencarian depth‑first dan mengembalikan shape pertama, yang dalam kasus ini adalah diagram.
- `ChartSeries` mewakili kumpulan titik data; seri pertama (`Series[0]`) biasanya berhubungan dengan set data utama.
- `ChartDataLabelPosition.OutsideEnd` memindahkan label ke luar ujung batang, meningkatkan keterbacaan.
- Menetapkan `dataLabel.Text` ke string Bahasa Prancis menyelaraskan label dengan paragraf yang telah diterjemahkan.

## Langkah 5: Simpan dokumen dengan paragraf yang diterjemahkan

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

Pada titik ini dokumen berisi paragraf Bahasa Prancis tetapi masih menyimpan konfigurasi diagram asli.

## Langkah 6: Simpan dokumen dengan diagram yang diperbarui

Anda dapat menggunakan kembali instance `Document` yang sama—tidak perlu memuat ulang—karena modifikasi diagram sudah berada di memori.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Kedua file kini siap untuk didistribusikan:

- **`translated.docx`** – berisi paragraf Bahasa Prancis.
- **`chart-updated.docx`** – berisi paragraf Bahasa Prancis *dan* label diagram yang disesuaikan.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke dalam `Program.cs`. Program ini dapat dikompilasi dan dijalankan apa adanya, dengan asumsi Anda telah mengganti `YOUR_DIRECTORY` dengan jalur folder yang sebenarnya.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Sesuaikan Label Data Diagram](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Jumlah Label Data dalam Diagram](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Label Data Diagram](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}