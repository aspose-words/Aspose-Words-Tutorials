---
category: general
date: 2026-03-30
description: Buat ringkasan dengan AI untuk file Word Anda menggunakan LLM lokal.
  Pelajari cara merangkum dokumen Word, menyiapkan server LLM lokal, dan menghasilkan
  ringkasan dokumen dalam hitungan menit.
draft: false
keywords:
- create summary with ai
- summarize word document
- use local llm
- generate document summary
- setup local llm server
language: id
og_description: Buat ringkasan dengan AI untuk file Word. Panduan ini menunjukkan
  cara merangkum dokumen Word menggunakan LLM lokal dan menghasilkan ringkasan dokumen
  dengan mudah.
og_title: Buat ringkasan dengan AI – Panduan Lengkap C#
tags:
- Aspose.Words
- C#
- AI
- Document Automation
title: Buat ringkasan dengan AI – Tutorial C# Aspose Words
url: /id/net/ai-powered-document-processing/create-summary-with-ai-c-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat ringkasan dengan AI – Tutorial C# Aspose Words

Pernah bertanya-tanya bagaimana **membuat ringkasan dengan AI** tanpa mengirim file rahasia Anda ke cloud? Anda tidak sendirian. Di banyak perusahaan, aturan privasi data membuat penggunaan layanan eksternal menjadi berisiko, sehingga pengembang beralih ke **LLM lokal** yang berjalan langsung di mesin mereka.

Dalam tutorial ini kita akan menelusuri contoh lengkap yang dapat dijalankan yang **meringkas dokumen Word** menggunakan Aspose.Words AI dan model bahasa yang di‑host secara mandiri. Pada akhir tutorial Anda akan tahu cara **menyiapkan server LLM lokal**, mengonfigurasi koneksi, dan **menghasilkan ringkasan dokumen** yang dapat ditampilkan atau disimpan di mana pun Anda perlukan.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (v24.10 atau lebih baru) – perpustakaan yang menyediakan kelas `Document` dan helper AI.  
- Sebuah **server LLM lokal** yang menyediakan endpoint OpenAI‑compatible `/v1/chat/completions` (misalnya Ollama, LM Studio, atau vLLM).  
- .NET 6+ SDK dan IDE pilihan Anda (Visual Studio, Rider, VS Code).  
- File `.docx` sederhana yang ingin Anda ringkas – letakkan di folder bernama `YOUR_DIRECTORY`.

> **Pro tip:** Jika Anda hanya melakukan percobaan, model “tiny‑llama” gratis sudah cukup untuk dokumen pendek dan menjaga latensi di bawah satu detik.

## Langkah 1: Muat Dokumen Word yang Ingin Dirangkum

Hal pertama yang harus kita lakukan adalah memuat file sumber ke dalam objek `Aspose.Words.Document`. Langkah ini penting karena mesin AI mengharapkan instance `Document`, bukan jalur file mentah.

```csharp
using Aspose.Words;

// Load the source .docx file
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of pages
Console.WriteLine($"Document loaded: {doc.PageCount} pages");
```

*Mengapa ini penting:* Memuat dokumen di awal memungkinkan Anda memverifikasi bahwa file ada dan dapat dibaca. Ini juga memberi Anda akses ke metadata (penulis, jumlah kata) yang mungkin ingin Anda sertakan dalam prompt nanti.

## Langkah 2: Konfigurasikan Koneksi ke Server LLM Lokal Anda

Selanjutnya kita memberi tahu Aspose Words ke mana mengirim prompt. Objek `LlmConfiguration` menyimpan URL endpoint dan kunci API opsional. Untuk kebanyakan server yang di‑host sendiri, kunci dapat berupa nilai dummy.

```csharp
using Aspose.Words.AI;

// Define connection settings for the local LLM
var llmConfig = new LlmConfiguration
{
    Endpoint = "http://localhost:8000/v1/chat/completions",
    ApiKey = "dummy" // not required for self‑hosted servers
};

// Verify the connection (optional but handy)
try
{
    var test = llmConfig.TestConnectionAsync().Result;
    Console.WriteLine("LLM server reachable ✅");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to reach LLM: {ex.Message}");
    // Exit early – no point continuing without a working server
    return;
}
```

*Mengapa ini penting:* Dengan menguji endpoint terlebih dahulu Anda menghindari error yang membingungkan ketika permintaan ringkasan gagal. Ini juga memperlihatkan **cara menggunakan LLM lokal** dengan aman.

## Langkah 3: Hasilkan Ringkasan Menggunakan Document AI

Sekarang bagian yang menyenangkan – kita meminta AI membaca dokumen dan menghasilkan ringkasan singkat. Aspose.Words.AI menyediakan satu baris kode `DocumentAi.Summarize` yang menangani pembuatan prompt, batas token, dan parsing hasil.

```csharp
// Ask the AI to summarize the document
string summary = DocumentAi.Summarize(doc, llmConfig);

// Show the raw JSON response for debugging (optional)
Console.WriteLine("=== AI Raw Response ===");
Console.WriteLine(summary);
```

*Mengapa ini penting:* Metode `Summarize` mengabstraksi boilerplate pembuatan permintaan chat‑completion, sehingga Anda dapat fokus pada logika bisnis. Metode ini juga menghormati batas token model, memotong dokumen bila diperlukan.

## Langkah 4: Tampilkan atau Simpan Ringkasan yang Dihasilkan

Akhirnya, kita menampilkan ringkasan ke konsol. Dalam aplikasi dunia nyata Anda mungkin menulisnya ke basis data, mengirimnya lewat email, atau menyisipkannya kembali ke file Word asli.

```csharp
// Print the clean summary to the console
Console.WriteLine("\n--- Document Summary ---");
Console.WriteLine(summary);

// Optional: Save the summary to a text file
File.WriteAllText("YOUR_DIRECTORY/summary.txt", summary);
Console.WriteLine("\nSummary saved to summary.txt");
```

*Mengapa ini penting:* Menyimpan hasil memungkinkan Anda mengauditnya nanti, atau menggunakannya dalam alur kerja downstream (misalnya, pengindeksan untuk pencarian).

## Contoh Lengkap yang Dapat Dijalankan

Berikut adalah program lengkap yang dapat Anda masukkan ke proyek konsol dan jalankan langsung. Pastikan paket NuGet `Aspose.Words` dan `Aspose.Words.AI` sudah terpasang.

```csharp
// ----------------------------------------------------------
// Complete C# console app – Create summary with AI
// ----------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.AI;

namespace DocumentSummaryDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            var docPath = "YOUR_DIRECTORY/input.docx";
            if (!File.Exists(docPath))
            {
                Console.WriteLine($"File not found: {docPath}");
                return;
            }

            Document doc = new Document(docPath);
            Console.WriteLine($"Loaded document ({doc.PageCount} pages).");

            // 2️⃣ Set up local LLM configuration
            var llmConfig = new LlmConfiguration
            {
                Endpoint = "http://localhost:8000/v1/chat/completions",
                ApiKey = "dummy"
            };

            // Quick connectivity test
            try
            {
                llmConfig.TestConnectionAsync().Wait();
                Console.WriteLine("✅ Connected to local LLM.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"❌ Unable to reach LLM: {ex.Message}");
                return;
            }

            // 3️⃣ Generate the summary
            Console.WriteLine("\nGenerating summary…");
            string summary = DocumentAi.Summarize(doc, llmConfig);

            // 4️⃣ Show and save the result
            Console.WriteLine("\n--- Document Summary ---");
            Console.WriteLine(summary);

            var outPath = "YOUR_DIRECTORY/summary.txt";
            File.WriteAllText(outPath, summary);
            Console.WriteLine($"\n✅ Summary written to {outPath}");
        }
    }
}
```

### Output yang Diharapkan

```
Loaded document (3 pages).
✅ Connected to local LLM.

Generating summary…

--- Document Summary ---
This report outlines the quarterly sales performance, highlighting a 12% increase in revenue driven by the new product line. Key challenges include supply‑chain delays, which are mitigated by renegotiated contracts. Recommendations focus on expanding into emerging markets and investing in automation.

✅ Summary written to YOUR_DIRECTORY/summary.txt
```

Kalimat persisnya akan berbeda tergantung pada konten dokumen Anda dan model yang Anda gunakan, tetapi struktur (paragraf singkat, poin‑poin bullet) biasanya serupa.

## Kesalahan Umum & Cara Menghindarinya

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| **Model kehabisan panjang konteks** | File Word besar melebihi jendela token LLM. | Gunakan overload `DocumentAi.Summarize` yang menerima `maxTokens` atau bagi dokumen menjadi bagian‑bagian dan ringkas masing‑masing. |
| **Error CORS atau SSL** | Server LLM lokal Anda mungkin menggunakan `https` dengan sertifikat self‑signed. | Nonaktifkan verifikasi SSL untuk pengembangan (`HttpClientHandler.ServerCertificateCustomValidationCallback = HttpClientHandler.DangerousAcceptAnyServerCertificateValidator`). |
| **Ringkasan kosong** | Prompt terlalu umum atau model tidak diarahkan untuk merangkum. | Berikan prompt khusus lewat `DocumentAi.Summarize(doc, llmConfig, new SummarizeOptions { Prompt = "Berikan ringkasan eksekutif 3 kalimat." })`. |
| **Penurunan performa** | LLM berjalan hanya di CPU. | Beralih ke instance dengan GPU atau gunakan model yang lebih kecil untuk prototipe cepat. |

## Kasus Khusus & Variasi

- **Merangkum PDF** – Konversi PDF ke `Document` terlebih dahulu (`Document pdfDoc = new Document("file.pdf");`) lalu jalankan langkah yang sama.  
- **Dokumen multibahasa** – Sertakan `CultureInfo` dalam `SummarizeOptions` untuk mengarahkan tokenisasi khusus bahasa.  
- **Pemrosesan batch** – Loop melalui folder berisi file `.docx`, gunakan kembali `llmConfig` yang sama untuk menghindari overhead koneksi ulang.  

## Langkah Selanjutnya

Setelah Anda menguasai cara **merangkum dokumen Word** dengan **LLM lokal**, Anda mungkin ingin:

1. **Mengintegrasikan dengan API web** – expose endpoint yang menerima upload file dan mengembalikan ringkasan dalam format JSON.  
2. **Menyimpan ringkasan ke indeks pencarian** – gunakan Azure Cognitive Search atau Elasticsearch agar dokumen Anda dapat dicari melalui abstrak yang dihasilkan AI.  
3. **Mencoba fitur AI lainnya** – Aspose.Words.AI juga menawarkan `Translate`, `ExtractKeyPhrases`, dan `ClassifyDocument`.  

Masing‑masing langkah ini dibangun di atas fondasi **menggunakan LLM lokal** dan **menghasilkan ringkasan dokumen** yang baru saja Anda siapkan.

---

*Selamat coding! Jika Anda mengalami kendala saat **menyiapkan server LLM lokal** atau menjalankan contoh, tinggalkan komentar di bawah – saya akan membantu Anda memecahkan masalahnya.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}