---
category: general
date: 2026-07-16
description: Ringkas teks dengan AI menggunakan C#. Pelajari cara menghasilkan ringkasan
  dari Word dan memuat dokumen Word C# dalam beberapa langkah saja.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize text with ai
- generate summary from word
- load word document c#
- ai summarizer c#
- word document processing c#
- text summarization api
language: id
lastmod: 2026-07-16
og_description: Ringkas teks dengan AI di C#. Ikuti panduan ini untuk menghasilkan
  ringkasan dari file Word dan pelajari cara memuat dokumen Word di C# dengan cepat.
og_image_alt: Screenshot of C# code that loads a Word document and produces an AI‑generated
  summary
og_title: Ringkas Teks dengan AI di C# – Panduan Langkah demi Langkah
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Summarize text with AI using C#. Learn how to generate summary from
    Word and load Word document C# in just a few steps.
  headline: Summarize Text with AI in C# – Complete Programming Guide
  type: TechArticle
tags:
- C#
- AI
- Word
title: Meringkas Teks dengan AI di C# – Panduan Pemrograman Lengkap
url: /id/net/ai-powered-document-processing/summarize-text-with-ai-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ringkas Teks dengan AI di C# – Panduan Pemrograman Lengkap

Pernah bertanya-tanya bagaimana cara **meringkas teks dengan AI** tanpa meninggalkan IDE Anda? Mungkin Anda memiliki tumpukan laporan dalam *.docx* dan membutuhkan ringkasan eksekutif yang cepat. Kabar baiknya, Anda dapat melakukannya semua di C#—memuat dokumen Word, memanggil AI summarizer, dan mencetak ikhtisar lima kalimat yang rapi.

Dalam tutorial ini kami akan menelusuri contoh dunia nyata yang menunjukkan cara **menghasilkan ringkasan dari file Word** dan **memuat dokumen Word C#** dengan kode yang bekerja pada model OpenAI maupun Google. Pada akhir tutorial Anda akan memiliki aplikasi konsol mandiri yang dapat Anda masukkan ke proyek .NET mana pun.

> **Apa yang akan Anda dapatkan**  
> • Program C# yang dapat dijalankan sepenuhnya dan membaca file *.docx*.  
> • Metode `Summarize` yang dapat digunakan kembali dan berkomunikasi dengan layanan AI.  
> • Tips menangani file yang hilang, pemilihan model, dan batas token.

---

## Prerequisites — What You Need Before You Start

| Persyaratan | Mengapa penting |
|-------------|-----------------|
| .NET 6 atau lebih baru | Fitur bahasa modern dan dukungan `async`. |
| Paket NuGet: `Aspose.Words` (atau `DocumentFormat.OpenXml`), `System.Net.Http.Json` | `Aspose.Words` memberikan kelas `Document` yang ditunjukkan dalam cuplikan; `HttpClient` menangani panggilan API. |
| Kunci API untuk OpenAI atau Google Vertex AI | Summarizer memerlukan endpoint model; Anda akan menyematkan kunci ke dalam kode. |
| File Word contoh (`report.docx`) di folder yang dapat direferensikan | Tutorial menggunakan `load word document c#` untuk mendemonstrasikan I/O file. |

Jika Anda belum memiliki salah satu dari itu, instal sekarang—tidak sulit, langkah-langkahnya langsung.

---

## Langkah 1 – Muat Dokumen Word di C#  

Hal pertama yang harus Anda lakukan adalah **memuat dokumen Word C#**. Dengan Aspose.Words cukup dengan membuat instance `Document` yang menunjuk ke file di disk.

```csharp
using Aspose.Words;
using System;
using System.IO;

// Ensure the file exists before we try to open it.
string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
if (!File.Exists(filePath))
{
    Console.Error.WriteLine($"❌ File not found: {filePath}");
    return;
}

// Step 1: Load the source document
Document doc = new Document(filePath);
Console.WriteLine("✅ Document loaded successfully.");
```

**Mengapa ini penting:**  
* Objek `Document` menyembunyikan XML di balik file *.docx*, memungkinkan kita memperlakukan kontennya sebagai teks biasa nanti.  
* Memeriksa keberadaan file mencegah `FileNotFoundException`, masalah umum saat **memuat dokumen word c#** dalam skrip produksi.

---

## Langkah 2 – Ekstrak Teks Biasa untuk Ringkasan  

Model AI tidak memahami markup internal Word; mereka memerlukan teks bersih. Aspose menyediakan `Document.GetText()` yang mengembalikan seluruh dokumen sebagai string.

```csharp
// Extract raw text – this strips out tables, images, and formatting.
string rawText = doc.GetText();
if (string.IsNullOrWhiteSpace(rawText))
{
    Console.Error.WriteLine("⚠️ Document appears empty after extraction.");
    return;
}
Console.WriteLine($"📝 Extracted {rawText.Length:N0} characters of text.");
```

**Tips pro:** Jika Anda perlu mempertahankan heading, Anda dapat mengiterasi `doc.GetChildNodes(NodeType.Paragraph, true)` dan menggabungkan hanya yang memiliki style “Heading”. Dengan begitu ringkasan menghormati struktur dokumen.

---

## Langkah 3 – Definisikan Opsi Ringkasan  

Sekarang kita masuk ke inti tutorial: **meringkas teks dengan AI**. Kami akan membungkus opsi dalam POCO kecil sehingga Anda dapat menyesuaikan model, maksimal kalimat, dan temperature tanpa menyelam ke panggilan HTTP.

```csharp
public enum SummarizationModel
{
    OpenAI,
    Google
}

public class SummarizationOptions
{
    public int MaxSentences { get; set; } = 5;
    public SummarizationModel Model { get; set; } = SummarizationModel.OpenAI;
    public double Temperature { get; set; } = 0.7; // Controls creativity
}
```

Anda kini dapat membuat instance opsi yang memberi tahu AI persis apa yang Anda inginkan:

```csharp
// Step 2: Define summarization options (e.g., limit to 5 sentences, choose a model)
SummarizationOptions options = new SummarizationOptions
{
    MaxSentences = 5,
    Model = SummarizationModel.OpenAI   // switch to Google if you prefer
};
```

**Mengapa kami mengekspose pengaturan ini:**  
* Proyek berbeda memiliki kebutuhan singkat yang berbeda—ada yang membutuhkan TL;DR dua kalimat, ada yang membutuhkan ringkasan eksekutif lima kalimat.  
* Beralih antara model `OpenAI` dan `Google` semudah mengubah satu nilai enum, yang sangat cocok untuk A/B testing.

---

## Langkah 4 – Implementasikan Metode `Summarize`  

Berikut adalah implementasi **lengkap dan dapat dijalankan** yang berkomunikasi dengan endpoint `chat/completions` OpenAI atau model `text-bison` Google Vertex AI. Ia menggunakan `HttpClient` dengan `System.Net.Http.Json` untuk kepraktisan.

```csharp
using System.Net.Http;
using System.Net.Http.Json;
using System.Threading.Tasks;

public static class AiSummarizer
{
    private static readonly HttpClient http = new HttpClient();

    public static async Task<string> SummarizeAsync(string text, SummarizationOptions opts)
    {
        // Choose endpoint and payload based on the selected model.
        if (opts.Model == SummarizationModel.OpenAI)
        {
            // OpenAI expects a messages array; we use a system prompt to enforce sentence limit.
            var request = new
            {
                model = "gpt-4o-mini",
                temperature = opts.Temperature,
                messages = new[]
                {
                    new { role = "system", content = $"Summarize the following text in no more than {opts.MaxSentences} sentences." },
                    new { role = "user", content = text }
                },
                max_tokens = 500
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("OPENAI_API_KEY"));

            var response = await http.PostAsJsonAsync("https://api.openai.com/v1/chat/completions", request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            return (string)json.choices[0].message.content;
        }
        else // Google Vertex AI
        {
            var request = new
            {
                instances = new[] { new { content = text } },
                parameters = new
                {
                    temperature = opts.Temperature,
                    maxOutputTokens = 500,
                    topK = 40,
                    topP = 0.95,
                    // Vertex AI doesn’t have a built‑in sentence limit, so we post‑process later.
                }
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("GOOGLE_API_KEY"));

            var response = await http.PostAsJsonAsync(
                "https://us-central1-aiplatform.googleapis.com/v1/projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison-001:predict",
                request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            string raw = (string)json.predictions[0].content;
            // Simple post‑processing: keep only the first N sentences.
            return string.Join(' ', raw.Split('.').Take(opts.MaxSentences)).Trim() + ".";
        }
    }
}
```

**Penjelasan “mengapa”**  
* **Desain model‑agnostik** – Metode yang sama bekerja untuk OpenAI maupun Google, sehingga basis kode tetap rapi.  
* **Variabel lingkungan untuk kunci** – Menyimpan rahasia API secara hard‑code merupakan risiko keamanan; menggunakan `Environment.GetEnvironmentVariable` mengikuti praktik terbaik.  
* **Penegakan batas kalimat** – OpenAI dapat diberi batas langsung di prompt sistem; Google memerlukan proses pasca‑proses cepat karena API‑nya tidak mendukung batas kalimat secara bawaan.  

---

## Langkah 5 – Sambungkan Semua dan Tampilkan Ringkasan  

Sekarang kita gabungkan semua bagian: baca dokumen, kirim teks ke `SummarizeAsync`, dan cetak hasilnya.

```csharp
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // Load the document (Step 1)
        string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
        if (!File.Exists(filePath))
        {
            Console.Error.WriteLine($"❌ Cannot find {filePath}");
            return;
        }
        Document doc = new Document(filePath);

        // Extract raw text (Step 2)
        string rawText = doc.GetText();

        // Define options (Step 3)
        SummarizationOptions options = new SummarizationOptions
        {
            MaxSentences = 5,
            Model = SummarizationModel.OpenAI   // Change to Google if you prefer
        };

        // Generate the summary (Step 4)
        string summary = await AiSummarizer.SummarizeAsync(rawText, options);

        // Step 5: Output the generated summary
        Console.WriteLine("\n=== AI‑Generated Summary ===\n");
        Console.WriteLine(summary);
    }
}
```

### Output yang Diharapkan

Dengan asumsi `report.docx` berisi analisis bisnis 2 halaman, konsol mungkin menampilkan:

```
=== AI‑Generated Summary ===

The quarterly sales increased by 12% YoY, driven primarily by the new product line. Customer churn fell to 3%, the lowest in five years. Marketing spend rose 8% but delivered a 15% lift in brand awareness. Operational efficiencies saved $1.2M, mainly through supply‑chain automation. The outlook for Q3 remains positive, with projected growth of 10‑15%.
```

Jika Anda mengubah `options.Model` menjadi `SummarizationModel.Google`, Anda akan melihat paragraf ringkas serupa—hanya dengan gaya frase yang berbeda.

---

## Menangani Kasus Edge & Kesalahan Umum  

| Situasi | Hal yang Perlu Diperhatikan | Perbaikan Cepat |
|---------|----------------------------|-----------------|
| **Dokumen besar (>10 k token)** | API mungkin menolak permintaan atau memotong output. | Bagi teks menjadi bagian logis (misalnya per heading) dan ringkas setiap bagian, lalu gabungkan. |
| **Kunci API hilang atau tidak valid** | Kesalahan 401 Unauthorized. | Verifikasi `OPENAI_API_KEY` / `GOOGLE_API_KEY` sudah diset di lingkungan Anda atau gunakan file `appsettings.json` untuk pengembangan lokal. |
| **File Word non‑Inggris** | Ringkasan | Ringkasan |

---

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Dokumen Word - Temukan dan Ganti Teks](/words/english/net/find-and-replace-text/)
- [Rentang Dapatkan Teks dalam Dokumen Word](/words/english/net/programming-with-ranges/ranges-get-text/)
- [Salin Teks yang Ditandai dalam Dokumen Word](/words/english/net/programming-with-bookmarks/copy-bookmarked-text/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}