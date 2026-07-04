---
category: general
date: 2026-06-24
description: Tutorial LLM lokal yang menunjukkan cara memanggil LLM lokal, memuat
  dokumen Word, dan menjalankan pemeriksaan tata bahasa AI di C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: id
og_description: Tutorial LLM lokal menjelaskan langkah demi langkah cara memanggil
  LLM lokal, memuat dokumen Word, dan menjalankan pemeriksaan tata bahasa AI di C#.
og_title: Tutorial LLM Lokal – Panggil LLM Lokal dan Jalankan Pemeriksaan Tata Bahasa
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: Tutorial LLM Lokal – Cara Memanggil LLM Lokal dan Menjalankan Pemeriksaan Tata
  Bahasa
url: /id/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial LLM Lokal – Memanggil LLM Lokal dan Menjalankan Pemeriksaan Tata Bahasa

Pernah bertanya-tanya bagaimana cara **menjalankan pemeriksaan tata bahasa** pada file Word tanpa mengirim apa pun ke cloud? Dalam **tutorial llm lokal** ini kami akan menghubungkan model bahasa besar yang di‑host sendiri, memuat file `.docx`, dan membiarkan AI merapikan prosa. Tanpa kunci API, tanpa lalu lintas eksternal—hanya mesin Anda sendiri yang melakukan pekerjaan berat.

Kami akan menelusuri setiap baris kode, menjelaskan mengapa setiap bagian penting, dan bahkan menunjukkan cara menangani jebakan umum (seperti file yang hilang atau endpoint yang tidak dapat dijangkau). Pada akhir tutorial Anda akan memiliki aplikasi konsol C# yang siap dijalankan yang melakukan **pemeriksaan tata bahasa AI** menggunakan model yang di‑host secara lokal.

> **Apa yang akan Anda dapatkan:** program lengkap yang dapat dijalankan, penjelasan jelas setiap langkah, dan tip untuk menskalakan solusi ke dokumen yang lebih besar atau penyedia LLM yang berbeda.

![diagram tutorial llm lokal](https://example.com/local-llm-tutorial-diagram.png "Diagram yang menggambarkan alur tutorial llm lokal")

## Prasyarat

- .NET 6.0 SDK atau lebih baru (Anda dapat mengunduhnya dari situs Microsoft)
- Server LLM yang berjalan secara lokal dengan endpoint yang kompatibel dengan OpenAI (mis., Ollama, LM Studio, atau pembungkus FastAPI khusus)
- Paket NuGet `AiGrammar` (atau pustaka apa pun yang menyediakan kelas `LocalLargeLanguageModel`, `Document`, dan `AiModelType`)
- Dokumen Word contoh (`input.docx`) yang ditempatkan di folder yang akan Anda referensikan nanti

Itu saja—tidak diperlukan kredensial cloud tambahan.

## Langkah 1: Tutorial LLM Lokal – Menyiapkan Endpoint

Hal pertama yang kita butuhkan adalah objek **call local llm** yang mengetahui ke mana mengirim permintaannya. Anggap saja seperti nomor telepon yang Anda hubungi sebelum dapat berbicara.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Mengapa ini penting:**  
Sebagian besar SDK LLM mengharapkan endpoint HTTP yang mengikuti kontrak API OpenAI. Dengan mengarahkan `Endpoint` ke `http://localhost:8000/v1` kami memberi tahu pustaka untuk **call local llm** alih-alih menghubungi server OpenAI. Kunci API dummy hanyalah placeholder—beberapa klien menolak nilai null, jadi kami memberikan sesuatu yang tidak berbahaya.

> **Pro tip:** Jika Anda menjalankan LLM di belakang reverse proxy, setel `Endpoint` ke URL proxy dan biarkan proxy menangani terminasi TLS. Ini membuat aplikasi konsol Anda tetap sederhana dan aman.

## Langkah 2: Memuat Dokumen Word untuk Pemeriksaan Tata Bahasa

Setelah model dapat dijangkau, kita perlu **load word document** kontennya ke memori. Kelas `Document` mengabstraksi parsing `.docx` untuk kami.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Mengapa ini penting:**  
Memberikan file `.docx` biner secara langsung ke LLM akan membingungkannya. Pembantu `Document` mengekstrak teks mentah sambil mempertahankan jeda paragraf, yang memberikan **ai grammar check** input bersih untuk diproses. Pemeriksaan keberadaan mencegah `FileNotFoundException` yang tidak menyenangkan yang sebaliknya akan membuat aplikasi crash.

## Langkah 3: Menjalankan Pemeriksaan Tata Bahasa Menggunakan LLM

Inilah inti tutorial: kami meminta model lokal untuk memeriksa teks. Metode `CheckGrammar` menyembunyikan plumbing HTTP dan mengembalikan objek hasil.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Mengapa ini penting:**  
`AiModelType.Gpt4` hanyalah label yang memberi tahu layanan remote template prompt mana yang digunakan. Jika Anda memiliki model yang lebih kecil (mis., `Llama2`), ganti sesuai. Pustaka men-serialisasi teks dokumen, mengirimnya ke `http://localhost:8000/v1/completions`, dan mengurai output yang telah diperbaiki.

> **Kasus tepi:** Jika LLM mengalami timeout, `CheckGrammar` melempar `TimeoutException`. Bungkus pemanggilan dalam blok `try/catch` jika Anda mengharapkan dokumen besar atau server yang sibuk.

## Langkah 4: Mengoutput Teks yang Diperbaiki

Akhirnya, kami menampilkan versi yang telah dibersihkan. Dalam aplikasi nyata Anda mungkin menulisnya kembali ke file `.docx` baru, tetapi untuk tutorial ini dump konsol sudah cukup.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Output yang diharapkan**  

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Jika LLM tidak menemukan kesalahan apa pun, output akan identik dengan input, yang tetap merupakan sinyal berguna.

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut program lengkap yang dapat Anda salin‑tempel ke proyek konsol baru:

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### Cara Menjalankan

1. Buka terminal di folder proyek.  
2. Jalankan `dotnet run`.  
3. Amati konsol mencetak teks yang telah diperbaiki.

Itu adalah seluruh **tutorial llm lokal** dalam kurang dari 100 baris kode.

## Pertanyaan yang Sering Diajukan (FAQ)

### Bisakah saya menggunakan merek LLM yang berbeda?

Tentu saja. Selama server menghormati skema API OpenAI v1, cukup ubah `Endpoint` dan pilih nilai enum `AiModelType` yang sesuai (mis., `AiModelType.Llama2`). Sisanya tetap identik.

### Bagaimana jika dokumen saya sangat besar (10 MB+)?

Payload besar dapat melampaui ukuran permintaan default banyak server. Bagi dokumen menjadi bagian‑bagian dan panggil `CheckGrammar` per bagian, lalu gabungkan hasilnya. Ini juga mengurangi peluang timeout.

### Bagaimana cara menulis output yang diperbaiki kembali ke file `.docx`?

Kelas `Document` biasanya menyediakan metode `Save(string path, string content)`. Setelah Anda mendapatkan `result.CorrectedText`, panggil:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Periksa dokumentasi pustaka untuk tanda tangan yang tepat.

### Apakah kunci API dummy merupakan risiko keamanan?

Tidak. Kunci tersebut diabaikan oleh endpoint yang di‑host sendiri, tetapi beberapa SDK menuntut string yang tidak null. Menggunakan placeholder seperti `"dummy"` memenuhi persyaratan SDK tanpa mengekspos rahasia apa pun.

## Langkah Selanjutnya dan Topik Terkait

- **Fine‑tune LLM lokal Anda** untuk tata bahasa khusus domain (mis., penulisan hukum atau medis).  
- **Jalankan pekerjaan batch** yang memproses seluruh folder file Word—bagus untuk pipeline penerbitan.  
- Jelajahi **streaming responses** jika Anda menginginkan saran waktu nyata saat pengguna mengetik.  
- Gabungkan ini dengan **perpustakaan spell‑checking** untuk gerbang kualitas berlapis ganda.

Setiap ide tersebut dibangun di atas konsep inti yang dibahas dalam **tutorial llm lokal** ini, sehingga Anda akan menemukan pola yang sama—**call local llm**, **load word document**, **run grammar check**, dan **handle results**—berulang di seluruh tutorial.

---

*Selamat coding! Jika Anda mengalami kendala, tinggalkan komentar di bawah dan kami akan membantu memecahkan masalah bersama.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Muat dengan Encoding di Dokumen Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Muat Enkripsi di Dokumen Word](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Pulihkan DOCX Rusak – Buka & Muat Dokumen Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}