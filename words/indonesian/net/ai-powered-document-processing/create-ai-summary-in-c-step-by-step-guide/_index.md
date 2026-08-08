---
category: general
date: 2026-08-07
description: Buat ringkasan AI dalam C# untuk dengan cepat merangkum dokumen Word
  menggunakan OpenAI. Pelajari cara mengatur kunci API OpenAI dan mengotomatisasi
  peringkasan dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create AI summary
- summarize Word document
- set OpenAI API key
- generate summary OpenAI
- automate document summarization
language: id
lastmod: 2026-08-07
og_description: Buat ringkasan AI dalam C# untuk langsung merangkum dokumen Word.
  Ikuti tutorial ini untuk mengatur kunci API OpenAI, menghasilkan ringkasan dengan
  OpenAI, dan mengotomatiskan peringkasan dokumen.
og_image_alt: Console window displaying the generated AI summary of a Word document
og_title: Buat Ringkasan AI dalam C# – panduan lengkap untuk pengembang
schemas:
- author: GroupDocs
  dateModified: '2026-08-07'
  description: Create AI summary in C# to quickly summarize a Word document using
    OpenAI. Learn how to set OpenAI API key and automate document summarization.
  headline: Create AI summary in C# – step‑by‑step guide
  type: TechArticle
tags:
- AI
- C#
- Document processing
- OpenAI
- Automation
title: Buat Ringkasan AI di C# – panduan langkah demi langkah
url: /id/net/ai-powered-document-processing/create-ai-summary-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Ringkasan AI dalam C# – panduan langkah‑demi‑langkah

Jika Anda perlu **membuat ringkasan AI** dari file Word yang besar, tutorial ini menunjukkan secara tepat cara melakukannya dengan C# dan GroupDocs AI SDK. Anda akan belajar cara **menyimpulkan konten dokumen Word**, **menetapkan kunci API OpenAI**, dan **mengotomatisasi ringkasan dokumen** untuk alur kerja yang dapat diulang.

Kami akan membahas setiap langkah yang diperlukan, menjelaskan mengapa setiap bagian penting, dan menyediakan aplikasi konsol lengkap yang dapat dijalankan. Pada akhir tutorial, Anda akan memiliki solusi mandiri yang dapat Anda masukkan ke dalam proyek .NET mana pun.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terinstal  
* Kunci API OpenAI yang valid (atau kunci Google Gemini jika Anda lebih suka)  
* Akses ke paket NuGet GroupDocs AI untuk .NET  

Anda dapat menginstal paket dengan perintah berikut:

```bash
dotnet add package GroupDocs.AI.Summarizer
```

> **Tip pro:** Gunakan *user‑secret* atau variabel lingkungan untuk menyimpan kunci API daripada menuliskannya secara langsung.

## Buat Ringkasan AI dengan GroupDocs AI SDK

Inti dari solusi ini adalah kelas `DocumentSummarizer`, yang menerima objek `Document` dan instance `AiSummarizerOptions`. Opsi-opsi tersebut memberi tahu SDK penyedia mana yang akan digunakan dan di mana menemukan kredensial.

```csharp
using System;
using GroupDocs.AI.Summarizer;
using GroupDocs.AI.Summarizer.Options;
using GroupDocs.AI.Summarizer.Providers;

class Program
{
    static void Main()
    {
        // Step 1: Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/LongReport.docx");

        // Step 2: Configure the summarizer (choose provider and supply API key)
        AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
        {
            Provider = AiProvider.OpenAi,          // or AiProvider.Google
            ApiKey   = "YOUR_OPENAI_API_KEY"
        };

        // Step 3: Generate the summary using the configured options
        string reportSummary = DocumentSummarizer.Summarize(doc, summarizerOptions);

        // Step 4: Display the resulting summary
        Console.WriteLine("Summary:\n" + reportSummary);
    }
}
```

### Mengapa ini Berfungsi

* **Loading the document** mengonversi file `.docx` ke dalam format yang dapat dibaca oleh mesin AI.  
* **AiSummarizerOptions** memberi tahu SDK penyedia LLM yang akan dipanggil dan menyediakan token otentikasi—di sinilah Anda **menetapkan kunci API OpenAI**.  
* **DocumentSummarizer.Summarize** mengirim teks dokumen ke penyedia yang dipilih dan mengembalikan ringkasan singkat.  
* **Console.WriteLine** mencetak hasilnya, yang kemudian dapat Anda alirkan ke file, email, atau basis data.

## Tetapkan Kunci API OpenAI untuk Ringkasan

Menuliskan kunci secara langsung berfungsi untuk demo cepat, tetapi kode produksi harus menyimpan rahasia di luar kontrol sumber. SDK membaca properti `ApiKey`, sehingga Anda dapat mengambil nilainya dari variabel lingkungan:

```csharp
AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
{
    Provider = AiProvider.OpenAi,
    ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
};
```

Tambahkan variabel ke sistem Anda:

```bash
# Windows PowerShell
$Env:OPENAI_API_KEY = "sk-xxxxxxxxxxxxxxxxxxxx"

# macOS / Linux
export OPENAI_API_KEY="sk-xxxxxxxxxxxxxxxxxxxx"
```

> **Mengapa ini penting:** Menyimpan kunci secara aman mencegah paparan tidak sengaja dan mematuhi kebanyakan kebijakan keamanan perusahaan.

## Ringkas Dokumen Word menggunakan Generate summary OpenAI

Kelas `DocumentSummarizer` secara internal memanggil endpoint **Generate summary OpenAI**. Jika Anda ingin menyesuaikan permintaan, Anda dapat mengirimkan parameter tambahan melalui `AiSummarizerOptions`:

```csharp
AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
{
    Provider = AiProvider.OpenAi,
    ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY"),
    Temperature = 0.3,          // Lower temperature for more deterministic output
    MaxTokens   = 250           // Limit the length of the summary
};
```

Pengaturan ini membantu Anda mengontrol tingkat detail dan kreativitas teks yang dikembalikan, yang berguna ketika Anda **mengotomatisasi ringkasan dokumen** pada banyak file.

## Otomatiskan Ringkasan Dokumen dalam Aplikasi Konsol

Untuk memproses banyak file tanpa intervensi manual, bungkus logika dalam sebuah loop dan baca jalur file dari sebuah folder:

```csharp
string inputFolder = @"YOUR_DIRECTORY";
foreach (var filePath in Directory.GetFiles(inputFolder, "*.docx"))
{
    Document doc = new Document(filePath);
    string summary = DocumentSummarizer.Summarize(doc, summarizerOptions);

    string outputPath = Path.ChangeExtension(filePath, ".summary.txt");
    File.WriteAllText(outputPath, summary);
    Console.WriteLine($"Summarized {Path.GetFileName(filePath)} → {Path.GetFileName(outputPath)}");
}
```

### Apa yang Ditambahkan

* **Batch processing** – Anda dapat menaruh sejumlah file Word ke dalam folder dan mendapatkan file `.summary.txt` untuk masing‑masing.  
* **Error handling** – Anda dapat membungkus loop dengan `try/catch` untuk melewati file yang rusak sambil mencatat masalah.  
* **Scalability** – Karena SDK melakukan permintaan HTTP per dokumen, Anda dapat memparalelkan loop dengan `Parallel.ForEach` jika kuota OpenAI Anda memungkinkan.

## Output yang Diharapkan

Saat Anda menjalankan program dengan contoh `LongReport.docx`, konsol akan mencetak sesuatu yang mirip dengan:

```
Summary:
The report outlines the quarterly performance of the sales department, highlighting a 12% increase in revenue driven by new product launches. Key challenges include supply‑chain constraints and rising operational costs. Recommendations focus on expanding the digital sales channel and optimizing inventory management.
```

File `.summary.txt` yang dihasilkan berisi teks yang sama, siap untuk konsumsi selanjutnya (mis., notifikasi email, ingest basis pengetahuan, atau tampilan UI).

## Kesalahan Umum dan Cara Menghindarinya

| Gejala | Penyebab | Solusi |
|---------|----------|--------|
| *Ringkasan kosong* | Dokumen hanya berisi gambar atau tabel tanpa teks yang dapat diekstrak. | Gunakan `doc.ExtractText()` sebelum merangkum atau konversi gambar menjadi teks dengan OCR. |
| *Kesalahan otentikasi* | Kunci API salah atau tidak ada. | Verifikasi variabel lingkungan `OPENAI_API_KEY` dan pastikan kunci memiliki izin yang diperlukan. |
| *Respons batas kecepatan* | Melebihi kuota permintaan OpenAI. | Tambahkan jeda (`Task.Delay(1000)`) antar permintaan atau minta kuota lebih tinggi dari OpenAI. |
| *Bahasa tidak terduga* | Penyedia default ke bahasa Inggris tetapi dokumen sumber dalam bahasa lain. | Setel `summarizerOptions.Language = "es"` (atau kode ISO yang sesuai) untuk memaksa bahasa target. |

## Kode sumber lengkap untuk disalin‑tempel

```csharp
using System;
using System.IO;
using GroupDocs.AI.Summarizer;
using GroupDocs.AI.Summarizer.Options;
using GroupDocs.AI.Summarizer.Providers;

class Program
{
    static void Main()
    {
        // Configure summarizer options (set OpenAI API key)
        AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
        {
            Provider = AiProvider.OpenAi,
            ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY"),
            Temperature = 0.3,
            MaxTokens   = 250
        };

        // Folder containing Word documents to summarize
        string inputFolder = @"YOUR_DIRECTORY";

        foreach (var filePath in Directory.GetFiles(inputFolder, "*.docx"))
        {
            try
            {
                Document doc = new Document(filePath);
                string summary = DocumentSummarizer.Summarize(doc, summarizerOptions);

                string outputPath = Path.ChangeExtension(filePath, ".summary.txt");
                File.WriteAllText(outputPath, summary);

                Console.WriteLine($"Summarized {Path.GetFileName(filePath)} → {Path.GetFileName(outputPath)}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Failed to process {Path.GetFileName(filePath)}: {ex.Message}");
            }
        }
    }
}
```

> **Catatan:** Ganti `YOUR_DIRECTORY` dengan jalur absolut ke folder yang berisi file `.docx` Anda.

![Console output showing the generated AI summary of a Word document](console-output.png)

## Kesimpulan

Anda sekarang tahu cara **membuat ringkasan AI** dari file Word dalam C# menggunakan GroupDocs AI SDK, cara **menetapkan kunci API OpenAI**, dan cara **mengotomatisasi ringkasan dokumen** untuk sejumlah file apa pun. Pendekatan ini bekerja dengan penyedia OpenAI maupun Google, memungkinkan Anda menyesuaikan parameter generasi, dan terintegrasi dengan bersih ke dalam solusi .NET yang ada.

**Langkah Selanjutnya**

* Jelajahi fitur **summarize Word document** dengan prompt khusus untuk nada atau panjang.  
* Gabungkan ringkasan dengan **Azure Functions** atau **AWS Lambda** untuk membangun layanan ringkasan tanpa server.  
* Ganti output konsol dengan REST API menggunakan ASP.NET Core untuk ringkasan on‑demand.

Selamat coding, dan nikmati peningkatan produktivitas yang dibawa oleh ringkasan berbasis AI ke alur kerja dokumen Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create a Word Document with Table of Contents in .NET](/words/english/net/add-content-using-document-builder/insert-table-contents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}