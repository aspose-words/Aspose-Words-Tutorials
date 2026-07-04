---
category: general
date: 2026-04-28
description: Hubungkan ke LLM lokal dari C# dan minta model bahasa besar untuk memuat
  dokumen Word, panggil LLM lokal, serta menulis ulang teks secara otomatis. Kode
  langkah demi langkah disertakan.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: id
og_description: Hubungkan ke LLM lokal dari C# dan lihat cara memberi prompt pada
  model bahasa besar, memuat dokumen Word, memanggil LLM lokal, serta menulis ulang
  teks secara otomatis dalam hitungan menit.
og_title: Terhubung ke LLM Lokal di C# – Panduan Pemrograman Lengkap
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Terhubung ke LLM Lokal di C# – Panduan Pemrograman Lengkap
url: /id/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menghubungkan ke LLM Lokal di C# – Panduan Pemrograman Lengkap

Pernahkah Anda perlu **menghubungkan ke LLM lokal** dari aplikasi .NET dan bertanya-tanya bagaimana membuatnya berinteraksi dengan file Word? Anda tidak sendirian. Dalam panduan ini kami akan membahas seluruh proses—menghubungkan ke LLM lokal, **prompt large language model**, memuat dokumen Word, **call local llm**, dan akhirnya **rewrite text automatically**. Pada akhir tutorial Anda akan memiliki contoh yang dapat dijalankan yang mengubah setiap paragraf menjadi nada formal tanpa kunci API eksternal.

## Apa yang Dibahas dalam Tutorial Ini

Kami akan memulai dengan menginstal paket NuGet yang diperlukan, lalu menjalankan endpoint LLM lokal sederhana (bayangkan Ollama pada port 11434). Setelah itu kami akan memuat file `.docx` menggunakan Aspose.Words, mengirim sebuah paragraf ke LLM, menerima versi yang telah ditulis ulang, dan menuliskannya kembali ke dokumen yang sama. Anda juga akan melihat cara menangani jebakan umum—paragraf null, async disposal, dan keanehan encoding—sehingga kode berfungsi di produksi, bukan hanya demo.

### Prasyarat

- .NET 6.0 SDK atau yang lebih baru (Anda juga dapat menggunakan .NET 8 jika suka)
- Visual Studio 2022 atau VS Code dengan ekstensi C#
- **Aspose.Words for .NET** (versi trial gratis sudah cukup)
- LLM yang dihosting secara lokal dan mendukung kontrak `/api/generate` (misalnya Ollama, LMStudio)
- Familiaritas dasar dengan async/await di C#

> **Pro tip:** Jika Anda belum menginstal Ollama, jalankan `ollama serve` dan tarik model dengan `ollama pull llama3`. Endpoint HTTP default akan menjadi `http://localhost:11434/api/generate`.

---

## Langkah 1: Instal Paket yang Diperlukan

Pertama, tambahkan paket NuGet Aspose.Words dan Aspose.Words.AI ke proyek Anda.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Perpustakaan ini memberi kita kemampuan **load word document** dan wrapper tipis untuk **call local llm** tanpa harus membuat permintaan HTTP secara manual.

---

## Langkah 2: Hubungkan ke Endpoint LLM Lokal

Menghubungkan ke model yang dihosting secara lokal sesederhana menginstansiasi `LocalLargeLanguageModel`. Konstruktor mengharapkan URL lengkap dari endpoint generasi.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Mengapa kita membungkus endpoint dalam sebuah kelas? `LocalLargeLanguageModel` menangani serialisasi JSON, retry, dan streaming response untuk Anda—sehingga Anda dapat fokus pada logika prompt alih-alih mengutak‑atik `HttpClient`.

---

## Langkah 3: Muat Dokumen Word Sumber

Selanjutnya, kita membawa dokumen ke memori. Aspose.Words mendukung hampir semua format Word, jadi `Document` akan mem‑parse `input.docx` tanpa perlu Office terinstal.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Jika Anda perlu bekerja dengan stream (misalnya file yang di‑upload lewat ASP.NET), cukup ganti path file dengan `MemoryStream` dan berikan ke konstruktor `Document`.

---

## Langkah 4: Ekstrak Teks Paragraf Saat Ini

Kita akan menggunakan `DocumentBuilder` untuk menavigasi dokumen. Pada contoh ini kami menulis ulang **paragraf pertama**, tetapi Anda dapat mengiterasi `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` untuk memproses banyak paragraf.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

Operator `?.` mencegah `NullReferenceException` jika dokumen ternyata kosong. Ini adalah salah satu **edge cases** yang sering menjebak pemula.

---

## Langkah 5: Prompt LLM untuk Menulis Ulang Paragraf

Sekarang kita benar‑benar **prompt large language model**. Prompt ditulis dalam bahasa Inggris biasa; wrapper akan mengirimnya sebagai JSON ke endpoint lokal.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Mengapa permintaan diformulasikan seperti ini? LLM merespons paling baik pada instruksi yang jelas dan satu‑tugas. Menambahkan baris baru setelah titik dua memisahkan instruksi dari konten, mengurangi kemungkinan model meng‑echo prompt kembali.

**Output yang diharapkan** – Jika `originalParagraph` berisi `"Hey, what's up?"`, LLM mungkin mengembalikan:

> “Good day, how may I assist you?”

Anda dapat memverifikasi hasilnya dengan mencetaknya:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Langkah 6: Sisipkan Teks yang Telah Ditulis Ulang ke Dokumen

Dengan teks baru di tangan, kita mengganti paragraf lama. `DocumentBuilder.Writeln` menulis baris baru dan memindahkan kursor ke depan, cocok untuk menambahkan. Jika Anda perlu *mengganti* paragraf yang sama persis, Anda dapat menggunakan `docBuilder.CurrentParagraph.RemoveAllChildren()` sebelum menulis.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Kedua pendekatan ditampilkan sehingga Anda dapat memilih yang paling sesuai dengan alur kerja Anda.

---

## Langkah 7: Simpan Dokumen yang Telah Diperbarui

Akhirnya, kita menyimpan perubahan ke file baru. Aspose.Words secara otomatis memilih format berdasarkan ekstensi file.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Buka `output.docx` di Word, dan Anda akan melihat paragraf kini ditulis dengan nada formal.

---

## Contoh Program Lengkap yang Berfungsi

Berikut adalah **program lengkap yang berdiri sendiri**. Salin‑tempel ke proyek console, restore paket NuGet, dan jalankan—tidak ada konfigurasi tambahan yang diperlukan selain LLM lokal yang sedang berjalan.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Apa yang Diharapkan Saat Menjalankannya

1. Konsol mencetak paragraf asli dan paragraf yang telah ditulis ulang.  
2. `output.docx` muncul di samping `input.docx`.  
3. Membuka file menunjukkan paragraf formal baru disisipkan setelah yang asli (atau diganti, jika Anda menggunakan kode alternatif).

---

## Menangani Edge Cases yang Umum

| Situasi | Solusi |
|-----------|----------|
| **Paragraf kosong atau hanya spasi** | Periksa `string.IsNullOrWhiteSpace` sebelum melakukan prompt (lihat Langkah 3). |
| **LLM mengembalikan error atau string kosong** | Bungkus `PromptAsync` dalam `try/catch` dan gunakan teks asli sebagai fallback. |
| **Beberapa paragraf perlu ditulis ulang** | Loop melalui `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` dan terapkan logika prompt yang sama. |
| **Dokumen besar menyebabkan latensi** | Batch paragraf dan kirim dalam satu permintaan (prompt hingga 4 KB per panggilan). |
| **Karakter non‑ASCII menjadi rusak** | Pastikan endpoint LLM menggunakan UTF‑8 (sebagian besar model modern sudah melakukannya). |

---

## Langkah Selanjutnya & Topik Terkait

- **Prompt large language model** dengan instruksi yang lebih kaya (misalnya panduan gaya, batas panjang).  
- Gunakan **call local llm** dalam sebuah web API untuk mengekspos otomatisasi dokumen sebagai layanan.  
- Jelajahi **load word document** dalam aliran paralel untuk skenario throughput tinggi.  
- Gabungkan pendekatan ini dengan **rewrite text automatically** untuk pembuatan email massal atau standarisasi laporan.  

Jika Anda ingin menggali lebih dalam, lihat dokumentasi Aspose tentang **document merging** dan referensi API Ollama untuk parameter sampling khusus.

---

## Kesimpulan

Kami baru saja menunjukkan cara **menghubungkan ke LLM lokal** dari C#, **prompt large language model**, **load word document**, **call local llm**, dan **rewrite text automatically**—semuanya dalam satu aplikasi console yang dapat dijalankan. Pola ini dapat diskalakan: ganti prompt, iterasi paragraf, atau ekspos logika melalui endpoint ASP.NET. Inti utama adalah model AI lokal dapat diintegrasikan secara erat dengan perpustakaan pemrosesan dokumen klasik, memberi Anda otomasi kuat tanpa harus meninggalkan lingkungan on‑prem yang terpercaya.

Ada pertanyaan tentang threading,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}