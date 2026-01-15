---
category: general
date: 2026-01-14
description: Pelajari cara memeriksa tata bahasa dalam file DOCX menggunakan Aspose.Words
  dan model gpt‑4 turbo. Panduan ini juga menunjukkan cara memuat docx dan menampilkan
  kesalahan tata bahasa.
draft: false
keywords:
- how to check grammar
- how to load docx
- load word document
- use gpt-4 turbo
- list grammar errors
language: id
og_description: Panduan langkah demi langkah tentang cara memeriksa tata bahasa dalam
  file DOCX menggunakan Aspose.Words dan model AI gpt-4 turbo. Termasuk kode, tips,
  dan output yang diharapkan.
og_title: Cara Memeriksa Tata Bahasa di DOCX – Aspose.Words & gpt-4 turbo
tags:
- Aspose.Words
- C#
- AI grammar checking
title: Cara Memeriksa Tata Bahasa di DOCX dengan Aspose.Words – gunakan gpt-4 turbo
url: /id/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Memeriksa Tata Bahasa dalam DOCX dengan Aspose.Words – gunakan gpt-4 turbo

Pernah bertanya-tanya **bagaimana cara memeriksa tata bahasa** dalam dokumen Word tanpa membuka Microsoft Word? Anda tidak sendirian. Banyak pengembang perlu memvalidasi teks secara programatis, terutama saat membangun pipeline konten, back‑end CMS, atau alat proofreading otomatis. Dalam tutorial ini kami akan membahas solusi lengkap yang siap dijalankan yang memuat file *.docx*, mengirimkan isinya ke model **gpt‑4 turbo**, dan mencetak setiap masalah tata bahasa yang ditemukan.

Kami juga akan membahas **cara memuat docx**, nuansa langkah **load word document**, dan cara **mendaftar kesalahan tata bahasa** dalam format yang jelas dan mudah dipahami. Pada akhir tutorial, Anda akan memiliki satu file C# yang dapat Anda masukkan ke proyek .NET apa pun dan mulai menangkap kesalahan secara instan.

> **Pro tip:** Jika Anda sudah menggunakan Aspose.Words di tempat lain (misalnya, untuk konversi PDF), pendekatan ini hampir tidak menambah beban.

![Diagram yang menunjukkan alur memuat DOCX, mengirimkannya ke gpt‑4 turbo, dan menerima masalah tata bahasa. Teks alternatif: diagram cara memeriksa tata bahasa](/images/grammar-check-flow.png)

## Apa yang Anda Butuhkan

- **.NET 6+** (kode ini dapat dikompilasi dengan .NET Framework 4.6 juga, tetapi .NET 6 adalah LTS saat ini)
- **Aspose.Words for .NET** – versi 23.9 atau lebih baru (Anda dapat mengunduhnya dari NuGet)
- **Aspose.Words.AI** package – paket ini berisi enum `AiModelType` dan helper `GrammarChecker`
- Kunci **Aspose Cloud API** yang valid (atau file lisensi lokal) – diperlukan untuk panggilan AI
- Contoh **input.docx** yang ditempatkan di folder yang Anda kontrol (kami akan menyebutnya `YOUR_DIRECTORY`)

Tidak ada klien REST eksternal atau penanganan HTTP manual—Aspose melakukan pekerjaan berat.

## Cara Memeriksa Tata Bahasa dalam File DOCX

Berikut adalah **program lengkap yang dapat dijalankan**. Silakan salin‑tempel ke proyek konsol dan tekan **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;

namespace GrammarCheckDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Load the Word document you want to analyze.
            // -------------------------------------------------
            // The path can be absolute or relative; here we assume a folder called
            // YOUR_DIRECTORY sits next to the executable.
            string docPath = @"YOUR_DIRECTORY/input.docx";

            // The Document constructor reads the file into memory.
            // If the file doesn't exist, an exception is thrown – we catch it later.
            Document document;
            try
            {
                document = new Document(docPath);
                Console.WriteLine($"✅ Loaded document: {docPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"❌ Failed to load document. {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 2: Choose the AI model that will perform the grammar check.
            // -------------------------------------------------
            // Aspose.Words.AI currently supports several models.
            // For best accuracy and speed, we pick gpt‑4 turbo.
            AiModelType grammarModel = AiModelType.Gpt4Turbo;

            // -------------------------------------------------
            // Step 3: Run the grammar checker and collect any issues.
            // -------------------------------------------------
            // GrammarChecker.CheckGrammar returns a collection of Issue objects.
            // Each Issue contains Severity, Message, and Location (page/paragraph).
            var grammarIssues = GrammarChecker.CheckGrammar(document, grammarModel);

            // -------------------------------------------------
            // Step 4: Output each issue with its severity, message, and location.
            // -------------------------------------------------
            if (grammarIssues.Count == 0)
            {
                Console.WriteLine("🎉 No grammar issues found! Your document looks good.");
            }
            else
            {
                Console.WriteLine($"🔎 Found {grammarIssues.Count} grammar issue(s):");
                foreach (var issue in grammarIssues)
                {
                    // Example output: "Warning: Use of passive voice at Paragraph 3, Run 5"
                    Console.WriteLine($"{issue.Severity}: {issue.Message} at {issue.Location}");
                }
            }

            // Keep the console window open when debugging.
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Penjelasan Setiap Bagian

| Bagian | Mengapa Penting | Apa yang Mungkin Anda Ubah |
|--------|----------------|----------------------------|
| **Load the document** | Ini adalah langkah **cara memuat docx**. Aspose mem-parsing file menjadi objek `Document`, memberi Anda akses ke paragraf, run, tabel, dll. | Jika Anda menerima stream (misalnya, dari unggahan web), gunakan `new Document(stream)` alih-alih jalur file. |
| **Select AI model** | Konstanta `AiModelType.Gpt4Turbo` memberi tahu Aspose untuk meneruskan teks ke endpoint GPT‑4 Turbo milik OpenAI. Ini menyeimbangkan biaya dan kecepatan. | Untuk kepatuhan yang lebih ketat, Anda dapat beralih ke `AiModelType.Gpt4` (lebih lambat, lebih mahal) atau model masa depan apa pun yang didukung Aspose. |
| **Run the grammar checker** | `GrammarChecker.CheckGrammar` menangani tokenisasi, mengirim teks ke AI, dan mem-parsing respons JSON menjadi objek `Issue` yang bertipe kuat. | Anda dapat menyesuaikan overload `CheckGrammar` untuk mengirim `GrammarCheckOptions` khusus (mis., mengabaikan kategori aturan tertentu). |
| **Print results** | Bagian ini **menampilkan kesalahan tata bahasa** dalam format yang mudah dibaca manusia. Anda juga dapat menuliskannya ke file log atau basis data. | Jika Anda memerlukan output yang dapat dibaca mesin, serialisasikan `grammarIssues` ke JSON dengan `JsonSerializer.Serialize`. |

## Cara Memuat DOCX Secara Efisien (Kata Kunci Sekunder: **cara memuat docx**)

Saat menangani file besar (10 MB+), memuat seluruh dokumen ke memori dapat menjadi pemborosan. Aspose menawarkan kelas **LoadOptions** yang memungkinkan Anda:

- **Membaca hanya teks utama** (lewatkan gambar, objek tersemat)
- **Mendeteksi format file** secara otomatis, yang berguna jika Anda menerima unggahan `.docx` dan `.doc`.

```csharp
using Aspose.Words.Loading;

// Example: load only the text, ignore images.
LoadOptions options = new LoadOptions
{
    LoadFormat = LoadFormat.Docx,
    // Prevent loading of non‑text elements for speed.
    LoadImages = false,
    LoadHeadersFooters = false
};

Document lightweightDoc = new Document(docPath, options);
Console.WriteLine($"Loaded docx with {lightweightDoc.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**Kapan menggunakan ini?**  
Jika Anda membangun API berkecepatan tinggi yang memeriksa puluhan dokumen per detik, mengaktifkan `LoadImages = false` dapat mengurangi penggunaan CPU dan memori hingga 30 %.

## Menggunakan gpt‑4 Turbo dengan Aspose.Words.AI (Kata Kunci Sekunder: **gunakan gpt-4 turbo**)

Aspose menyederhanakan panggilan REST OpenAI di balik enum sederhana, tetapi di balik layar ia:

1. Mengekstrak teks polos dari `Document`.
2. Mengirim prompt seperti “Identify grammatical errors in the following text” ke endpoint **gpt‑4 turbo**.
3. Menerima daftar isu dalam format JSON dan memetakan kembali ke posisi Word asli.

Jika Anda memerlukan kontrol lebih atas prompt (mis., menegakkan British English), Anda dapat menyediakan `AiPrompt` khusus:

```csharp
var customPrompt = new AiPrompt
{
    SystemMessage = "You are a professional proofreader using British English conventions.",
    UserMessage = "Find all grammatical errors in the supplied text."
};

var grammarIssues = GrammarChecker.CheckGrammar(document, grammarModel, customPrompt);
```

**Pertimbangan biaya:**  
`gpt‑4 turbo` ditagih per token. Dokumen 5 halaman biasanya mengonsumsi < 2 K token, yang setara dengan beberapa sen per pemeriksaan. Selalu pantau penggunaan Anda di konsol Aspose Cloud.

## Menampilkan Kesalahan Tata Bahasa dengan Cara yang Ramah (Kata Kunci Sekunder: **daftar kesalahan tata bahasa**)

String mentah `Issue.Location` terlihat seperti `"Paragraph 4, Run 2"`. Untuk konsumsi UI Anda mungkin

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}