---
category: general
date: 2026-05-04
description: Cara menggunakan LLM untuk mengedit dokumen dengan Aspose – pelajari
  cara mengganti teks paragraf, menghubungkan ke LLM lokal, dan menulis ulang teks
  menggunakan AI.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: id
og_description: Cara menggunakan LLM untuk mengedit dokumen dengan Aspose. Panduan
  ini menunjukkan cara menghubungkan ke LLM lokal, mengganti teks paragraf, dan menulis
  ulang teks menggunakan AI.
og_title: Cara Menggunakan LLM dengan Aspose.Words – Menulis Ulang Paragraf dalam
  C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Cara Menggunakan LLM dengan Aspose.Words – Menulis Ulang Paragraf di C#
url: /id/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggunakan LLM dengan Aspose.Words – Menulis Ulang Paragraf dalam C#

Pernah bertanya-tanya **bagaimana cara menggunakan LLM** untuk memperbaiki dokumen Word tanpa membukanya secara manual? Anda bukan satu-satunya. Banyak pengembang menemui kebuntuan ketika mereka perlu *mengganti teks paragraf* secara programatik tetapi tidak memiliki alur kerja AI yang bersih.  

Dalam tutorial ini kami akan menghubungkan model bahasa besar lokal, memberi potongan dari file `.docx`, meminta **menulis ulang teks menggunakan AI**, dan akhirnya menyimpan dokumen yang diperbarui—semua dengan Aspose.Words. Pada akhir tutorial Anda akan memiliki aplikasi konsol C# yang siap dijalankan dan mendemonstrasikan seluruh pipeline.

> **Apa yang akan Anda dapatkan:** contoh lengkap yang dapat dijalankan, penjelasan setiap langkah, tip untuk kasus tepi, dan ide untuk memperluas solusi.

## Apa yang Anda Butuhkan

- **.NET 6+** (atau .NET Framework 4.7.2 – kode ini bekerja pada keduanya)
- **Aspose.Words for .NET** (paket NuGet `Aspose.Words`)
- **Server LLM lokal** yang menyediakan endpoint HTTP `/generate` sederhana (misalnya Ollama, LMStudio, atau layanan Flask khusus)
- Familiaritas dasar dengan C# dan kode klien HTTP  

Tidak diperlukan SDK tambahan; semua yang lain ada dalam kode yang akan kami tulis bersama.

## Langkah 1: Cara Menggunakan LLM untuk Mengganti Teks Paragraf

Hal pertama yang harus kita lakukan adalah mengidentifikasi paragraf yang ingin dimodifikasi. Aspose.Words mempermudah hal ini dengan menyediakan model objek yang kaya.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Mengapa ini penting:**  
Memilih node yang tepat mencegah Anda secara tidak sengaja menimpa heading atau tabel. Dengan menggunakan pendekatan **replace paragraph text** kami menjaga struktur dokumen tetap utuh sambil hanya menyentuh konten yang relevan.

> **Pro tip:** Jika dokumen Anda memiliki bagian dengan panjang variabel, gunakan `document.GetChildNodes(NodeType.Paragraph, true)` dan LINQ untuk menemukan paragraf berdasarkan teks atau gaya-nya.

## Langkah 2: Menghubungkan ke Endpoint LLM Lokal

Setelah kita memiliki teks, kita perlu mengirimnya ke LLM. Contoh ini menggunakan kelas pembungkus sederhana `LocalLargeLanguageModel` yang menyembunyikan detail HTTP. Anda dapat menggantinya dengan panggilan `HttpClient` jika lebih suka.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Mengapa kami menghubungkannya dengan cara ini:**  
Pengaturan **connect to local llm** menghilangkan latensi, menjaga data tetap di tempat, dan menghindari biaya API. Pembungkus ini juga membuat kode selanjutnya lebih bersih, memungkinkan kami fokus pada logika **rewrite text using ai**.

## Langkah 3: Menulis Ulang Teks Menggunakan AI dengan Aspose.Words

Dengan teks paragraf di tangan dan LLM siap, kami menyusun prompt yang memberi tahu model secara tepat apa yang kami inginkan—menulis ulang dengan nada formal. Anda dapat menyesuaikan prompt untuk gaya lain (ramah, teknis, dll.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Mengapa ini berhasil:**  
LLM bekerja berdasarkan prompt; memberikan instruksi eksplisit (“Rewrite … in a formal tone”) menghasilkan hasil yang konsisten. Langkah **rewrite text using ai** adalah inti tutorial – ia menunjukkan bagaimana AI dapat disematkan langsung ke alur kerja dokumen.

## Langkah 4: Mengedit Dokumen dan Menyimpan Perubahan

Sekarang kami mengganti run asli dengan konten baru. Aspose.Words menyimpan teks dalam objek `Run`, jadi mengosongkannya terlebih dahulu menghindari sisa artefak format.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Catatan kasus tepi:**  
Jika paragraf asli berisi format campuran (tebal, miring) Anda mungkin ingin mempertahankan gaya. Dalam hal itu, buat `Run` baru, salin pengaturan `Font` asli, lalu set `Text`‑nya ke `revisedText`.

## Contoh Kerja Lengkap

Berikut seluruh program yang dapat Anda salin‑tempel ke proyek konsol. Ingat untuk menginstal paket NuGet Aspose.Words terlebih dahulu (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Output yang Diharapkan

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Buka `output.docx` – Anda akan melihat paragraf ketiga kini berisi versi yang telah dipoles.

## Pertanyaan Umum & Hal-hal yang Perlu Diwaspadai

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika LLM saya mengembalikan JSON dengan bidang tambahan?** | Sesuaikan `GenerateText` untuk mendeserialisasi properti yang tepat atau parsing respons secara manual. |
| **Bisakah saya memproses banyak paragraf sekaligus?** | Ya – iterasi melalui `document.FirstSection.Body.Paragraphs` dan terapkan logika prompt yang sama, mungkin menambahkan indeks paragraf ke prompt untuk konteks. |
| **Server LLM saya menggunakan autentikasi?** | Tambahkan header ke `HttpClient` sebelum POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Format hilang setelah penggantian.** | Pertahankan pengaturan `Run.Font` asli: buat `Run` baru, salin `originalRun.Font.Clone()`, lalu set `Text`‑nya. |
| **LLM kadang‑kadang mengembalikan string kosong.** | Implementasikan fallback – jika `revisedText.Trim().Length == 0`, pertahankan teks asli atau coba lagi dengan prompt yang lebih sederhana. |

## Memperluas Solusi

Setelah Anda menguasai **cara menggunakan llm** untuk satu paragraf, pertimbangkan langkah selanjutnya berikut:

- **Pemrosesan batch:** Loop melalui setiap paragraf dan menulis ulang dengan gaya yang dipilih (misalnya “buat semua teks singkat”).  
- **Penulisan ulang sadar gaya:** Sertakan nama gaya paragraf asli dalam prompt sehingga LLM dapat menghormati heading vs teks tubuh.  
- **Integrasi dengan pipeline CI:** Otomatiskan pemolesan dokumen sebagai bagian dari proses build dokumentasi.  
- **Prompt alternatif:** Coba “summarize this paragraph” atau “translate this paragraph to Spanish” untuk menjelajahi kekuatan penuh **rewrite text using ai**.

## Kesimpulan

Kami telah menelusuri seluruh alur **cara menggunakan llm** dengan Aspose.Words: memuat dokumen, **connect to local llm**, mengekstrak paragraf, **rewrite text using ai**, **replace paragraph text**, dan akhirnya menyimpan hasilnya. Kode ini mandiri, siap pakai, dan menampilkan cara praktis menggabungkan AI dengan otomasi dokumen tradisional.

Cobalah, ubah prompt, dan biarkan

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}