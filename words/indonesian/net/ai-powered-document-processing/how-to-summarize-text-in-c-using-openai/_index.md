---
category: general
date: 2026-09-11
description: Pelajari cara merangkum teks dalam C# dengan membaca kunci API, memanggil
  OpenAI, dan menghasilkan ringkasan singkat dari dokumen Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: id
lastmod: 2026-09-11
og_description: Bagaimana cara merangkum teks di C#? Tutorial ini menunjukkan cara
  membaca kunci API, memanggil OpenAI, dan membuat ringkasan dokumen Word.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Cara meringkas teks di C# dengan OpenAI – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: Cara merangkum teks di C# menggunakan OpenAI
url: /id/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara merangkum teks dalam C# menggunakan OpenAI

Jika Anda perlu **cara merangkum teks** dalam file .docx, panduan ini menunjukkan solusi lengkap yang siap dijalankan. Anda akan belajar cara membaca kunci API dari lingkungan Anda, cara memanggil OpenAI (atau Google) dari C#, dan cara membuat ringkasan singkat dari dokumen Word.

Merangkum dokumen Word adalah kebutuhan umum untuk pembuatan laporan, rangkuman email, atau ekstraksi basis pengetahuan. Pada akhir tutorial ini Anda akan memiliki program baris perintah yang mencetak ringkasan lima kalimat dari file `.docx` apa pun yang Anda berikan.

## Prasyarat

- .NET 6.0 SDK atau lebih baru (unduh dari [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- Kunci API OpenAI yang valid disimpan dalam variabel lingkungan bernama `OPENAI_API_KEY` (Anda akan melihat **baca kunci api** dalam aksi)
- Paket NuGet `DocumentFormat.OpenXml` untuk membaca file `.docx`
- Paket NuGet `OpenAI` (atau `Google.AI` jika Anda lebih suka penyedia Google)

## Langkah 1: Siapkan proyek dan instal dependensi

Buat proyek konsol baru dan tambahkan paket yang diperlukan:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** Jaga agar `csproj` Anda rapi dengan mengelompokkan paket terkait di bawah `<ItemGroup>` jika Anda menambahkan lebih banyak dependensi nanti.

## Langkah 2: Baca kunci API dengan aman

Menulis rahasia secara hard‑coding tidak aman. Tutorial ini menunjukkan cara yang tepat untuk **baca kunci api** dari variabel lingkungan.

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## Langkah 3: Muat dokumen Word yang ingin Anda rangkum

Kode di bawah ini menunjukkan **cara merangkum dokumen word** dengan mengekstrak teks polos dari struktur OpenXML.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## Langkah 4: Bangun kelas summarizer yang dapat digunakan kembali

Kelas ini mengenkapsulasi **cara memanggil openai** (atau Google) dan mengimplementasikan logika **cara membuat ringkasan**. Kelas ini juga memungkinkan Anda beralih penyedia dengan satu nilai enum.

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### Mengapa struktur ini penting

- **Pemisahan kepedulian:** Memuat dokumen, membaca kunci API, dan memanggil layanan AI dipisahkan ke dalam metode masing‑masing. Ini membuat kode lebih mudah diuji dan diperluas.
- **Fleksibilitas penyedia:** Dengan menggunakan enum Anda dapat beralih antara OpenAI dan Google tanpa menyentuh kode pemanggil, yang secara langsung menjawab **cara memanggil openai** dan **cara membuat ringkasan** secara dapat digunakan kembali.
- **Penanganan error:** Kunci API yang hilang melemparkan pengecualian yang jelas, mencegah kegagalan diam.

## Langkah 5: Gabungkan semuanya dalam `Program.cs`

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### Output yang diharapkan

Menjalankan program dengan dokumen contoh:

```bash
dotnet run -- "sample/input.docx"
```

dapat menghasilkan:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Langkah 6: Variasi umum dan kasus tepi

| Situasi | Penyesuaian yang disarankan |
|-----------|------------------------|
| **Large documents** ( > 10 KB ) | Bagi teks menjadi potongan dan rangkum setiap potongan, lalu gabungkan hasilnya. |
| **Non‑English content** | Sertakan petunjuk bahasa dalam prompt, misalnya, “Summarize the following French text …”. |
| **Google provider** | Ganti pemanggilan `SummarizeWithOpenAIAsync` dengan klien API Google yang sesuai; pertahankan antarmuka enum yang sama. |
| **Custom summary length** | Ubah argumen `maxSentences` saat memanggil `SummarizeAsync`. |
| **Missing API key** | Metode `GetOpenAIApiKey` sudah melempar pengecualian yang jelas; tangkap di `Main` jika Anda menginginkan pesan yang lebih ramah. |

## Tips profesional untuk penggunaan produksi

1. **Cache kunci API** – membaca dari lingkungan setiap panggilan menambah overhead yang dapat diabaikan, tetapi Anda dapat menyimpannya dalam field static readonly jika Anda memanggil summarizer berkali‑kali dalam satu proses.  
2. **Rate‑limit permintaan** – OpenAI menerapkan batas permintaan; terapkan back‑off eksponensial jika Anda menerima `429 Too Many Requests`.  
3. **Sanitasi input** – hapus informasi pribadi yang dapat diidentifikasi sebelum mengirim teks ke layanan AI eksternal.  
4. **Uji unit logika ekstraksi** – mock `WordprocessingDocument` untuk memverifikasi bahwa `ExtractTextFromDocx` berfungsi dengan berbagai struktur dokumen.  

## Kesimpulan

Anda kini tahu **cara merangkum teks** dalam C# dengan membaca kunci API secara aman, memanggil OpenAI, dan menghasilkan ringkasan singkat dari dokumen Word. Pola yang sama memungkinkan Anda **cara memanggil openai** dengan penyedia lain, **cara membuat ringkasan** untuk berbagai tipe konten, dan dengan aman **baca kunci api** dari lingkungan. Bereksperimenlah dengan dokumen yang lebih panjang, penyedia yang berbeda, atau prompt khusus untuk menyesuaikan rangkuman dengan domain spesifik Anda.

---

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Ringkas Dokumen Word dalam C# dengan Aspose.Words API – Panduan Lengkap Berbasis AI](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [cara membuat pdf dari Word – Panduan Lengkap C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Dokumen Word - Cara Menghapus Konten](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}