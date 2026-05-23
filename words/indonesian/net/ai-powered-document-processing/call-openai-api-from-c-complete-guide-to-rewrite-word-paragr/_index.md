---
category: general
date: 2026-05-23
description: Panggil API OpenAI di C# untuk menulis ulang kalimat dengan gaya formal.
  Pelajari cara memuat dokumen Word, memanggil LLM lokal, dan menulis ulang paragraf
  secara formal dengan Aspose.Words.
draft: false
keywords:
- call openai api
- call local llm
- rewrite sentence formal
- rewrite paragraph formal
- load word document
language: id
og_description: Panggil API OpenAI di C# untuk menulis ulang kalimat dengan gaya formal.
  Tutorial lengkap langkah demi langkah dengan kode, penjelasan, dan tips.
og_title: Panggil API OpenAI dari C# – Menulis Ulang Paragraf Word
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  headline: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  type: TechArticle
- description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  name: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  steps:
  - name: Why This Works
    text: '- **LocalLargeLanguageModel** abstracts the HTTP details, letting you **call
      local llm** exactly the same way you would a cloud OpenAI endpoint. - The prompt
      we send (`Rewrite the following sentence in formal tone:`) is concise, which
      helps the model focus on a **rewrite sentence formal** transforma'
  - name: Expected Output Example
    text: '| Original (informal) | Rewritten (formal) | |---------------------|--------------------|
      | *Hey team, can we get the results ASAP?* | *Dear team, could you please provide
      the results at your earliest convenience?* |'
  - name: Empty Paragraphs
    text: 'Sometimes a Word file contains empty paragraphs that throw off the LLM.
      Guard against this:'
  - name: Large Documents
    text: 'Processing a 100‑page report paragraph‑by‑paragraph can be slow. Batch
      the calls:'
  type: HowTo
tags:
- Aspose.Words
- C#
- LLM
- OpenAI
- Word Automation
title: Panggil API OpenAI dari C# – Panduan Lengkap untuk Menulis Ulang Paragraf Word
url: /id/net/ai-powered-document-processing/call-openai-api-from-c-complete-guide-to-rewrite-word-paragr/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Panggil OpenAI API dari C# – Panduan Lengkap untuk Menulis Ulang Paragraf Word

Pernah bertanya-tanya bagaimana cara **call OpenAI API** dari aplikasi .NET dan langsung memperbaiki sebuah teks? Mungkin Anda memiliki file Word yang membutuhkan nada lebih formal untuk laporan klien, dan Anda tidak ingin mengetik ulang semuanya sendiri. Dalam tutorial ini kami akan membahas hal tersebut: memuat dokumen Word, mengirim sebuah paragraf ke LLM yang dihosting secara lokal yang meniru API kompatibel OpenAI, dan mendapatkan kembali versi **rewrite paragraph formal**. Pada akhir tutorial Anda akan memiliki aplikasi console C# yang dapat dijalankan dan melakukan seluruh pekerjaan dalam beberapa baris.

Kami akan membahas semua yang Anda perlukan: paket NuGet yang diperlukan, cara **load word document** dengan Aspose.Words, keunikan **call local llm**, dan mengapa prompt “Rewrite the following sentence in formal tone” secara konsisten menghasilkan hasil **rewrite sentence formal**. Tanpa dokumen eksternal, hanya panduan mandiri yang dapat Anda salin‑tempel dan jalankan.

## Apa yang Akan Anda Capai

- Muat file *.docx* menggunakan Aspose.Words.  
- Buat klien yang dapat **call OpenAI API**‑compatible endpoints, bahkan jika dijalankan secara lokal.  
- Kirim sebuah paragraf ke LLM dan terima respons **rewrite paragraph formal**.  
- Ganti teks asli dalam file Word dan simpan dokumen yang telah diperbarui.  

Prasyaratnya minimal: .NET 6+ SDK, Visual Studio atau VS Code, dan sebuah instance LLM lokal yang menyediakan endpoint HTTP kompatibel OpenAI (misalnya, Ollama, LM Studio). Jika Anda sudah memiliki kunci cloud, Anda dapat mengganti endpoint dan API key – kode tetap sama.

## Langkah 1: Siapkan Proyek dan Instal Paket

Untuk memulai, buat proyek console baru:

```bash
dotnet new console -n WordLlmRewrite
cd WordLlmRewrite
```

Sekarang tambahkan dua paket NuGet yang kami perlukan:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tip:** Aspose.Words.AI dilengkapi dengan wrapper tipis yang mengetahui cara **call OpenAI API**‑style services, sehingga Anda tidak perlu membuat permintaan HTTP secara manual.

## Langkah 2: Tulis Kode yang **Call OpenAI API** (atau LLM Lokal)

Buka `Program.cs` dan ganti isinya dengan yang berikut. Setiap baris dijelaskan di bawah, sehingga Anda tidak akan kebingungan.

```csharp
using Aspose.Words;
using Aspose.Words.AI;
using System;

// ------------------------------------------------------------
// 1️⃣ Create a client for the local LLM that follows the
//    OpenAI‑compatible API. This is the heart of the
//    “call openai api” step.
// ------------------------------------------------------------
var localLlm = new LocalLargeLanguageModel(
    endpoint: "http://localhost:8000/v1", // change if your server runs elsewhere
    apiKey: "dummy",                      // dummy because the local server usually skips auth
    model: "my-llm");                     // name of the model you want to use

// ------------------------------------------------------------
// 2️⃣ Load the source Word document.
// ------------------------------------------------------------
Document doc = new Document("YOUR_DIRECTORY/source.docx");

// ------------------------------------------------------------
// 3️⃣ Grab the first paragraph that we want to rewrite.
// ------------------------------------------------------------
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;

// ------------------------------------------------------------
// 4️⃣ Ask the LLM to rewrite the paragraph in a formal tone.
//    This is where we “rewrite paragraph formal”.
// ------------------------------------------------------------
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in formal tone:\n{paragraph.GetText()}");

// ------------------------------------------------------------
// 5️⃣ Replace the original paragraph text with the revised version.
// ------------------------------------------------------------
paragraph.Runs.Clear();                     // remove old runs
paragraph.AppendChild(new Run(doc, revisedText));

// ------------------------------------------------------------
// 6️⃣ Save the updated document.
// ------------------------------------------------------------
doc.Save("YOUR_DIRECTORY/rewritten.docx");

// ------------------------------------------------------------
// 7️⃣ Confirmation output.
// ------------------------------------------------------------
Console.WriteLine("✅ Document rewritten and saved as rewritten.docx");
```

### Mengapa Ini Berfungsi

- **LocalLargeLanguageModel** mengabstraksi detail HTTP, memungkinkan Anda **call local llm** dengan cara yang sama seperti Anda akan menggunakan endpoint cloud OpenAI.  
- Prompt yang kami kirim (`Rewrite the following sentence in formal tone:`) singkat, yang membantu model fokus pada transformasi **rewrite sentence formal** daripada menambahkan konten yang tidak relevan.  
- Dengan mengosongkan `paragraph.Runs` dan menambahkan `Run` baru, kami menjamin file Word hanya berisi teks formal yang baru.

## Langkah 3: Jalankan Aplikasi

Pastikan server LLM lokal Anda sudah berjalan dan mendengarkan pada `http://localhost:8000/v1`. Kemudian jalankan:

```bash
dotnet run
```

Jika semuanya terhubung dengan benar, Anda akan melihat:

```
✅ Document rewritten and saved as rewritten.docx
```

Buka `rewritten.docx` – paragraf pertama kini harus terbaca dengan gaya yang halus dan formal.

### Contoh Output yang Diharapkan

| Asli (informal) | Ditulis Ulang (formal) |
|---------------------|--------------------|
| *Hey team, can we get the results ASAP?* | *Dear team, could you please provide the results at your earliest convenience?* |

Transformasi ini menunjukkan konversi **rewrite sentence formal** yang bersih, sempurna untuk komunikasi bisnis.

## Langkah 4: Menyesuaikan Prompt untuk Nada Berbeda

Jika Anda membutuhkan penulisan ulang yang lebih santai, cukup ubah prompt:

```csharp
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in a casual tone:\n{paragraph.GetText()}");
```

Demikian pula, Anda dapat meminta model untuk **rewrite paragraph formal** pada bagian yang lebih panjang, atau bahkan untuk merangkum seluruh dokumen. Pola **call openai api** yang sama berlaku – ganti prompt, pertahankan kode klien tetap tidak berubah.

## Langkah 5: Menangani Kasus Edge

### Paragraf Kosong

Terkadang file Word berisi paragraf kosong yang mengacaukan LLM. Lindungi dari hal ini:

```csharp
if (string.IsNullOrWhiteSpace(paragraph.GetText()))
{
    Console.WriteLine("Skipped empty paragraph.");
}
else
{
    // generate and replace as before
}
```

### Dokumen Besar

Memproses laporan 100‑halaman paragraf‑per‑paragraf dapat menjadi lambat. Lakukan pemanggilan secara batch:

```csharp
foreach (Paragraph p in doc.GetChildNodes(NodeType.Paragraph, true))
{
    // same rewrite logic for each paragraph
}
```

Sadari batas laju pada server lokal Anda; Anda mungkin perlu menambahkan `Thread.Sleep(200)` kecil di antara pemanggilan.

## Langkah 6: Menyebarkan ke Produksi

1. Ganti API key dummy dengan yang nyata jika Anda beralih ke Azure OpenAI atau OpenAI SaaS.  
2. Simpan endpoint dan key dalam variabel lingkungan (`OPENAI_ENDPOINT`, `OPENAI_KEY`) dan baca mereka melalui `Environment.GetEnvironmentVariable`.  
3. Tambahkan logging (misalnya, Serilog) di sekitar blok **call openai api** untuk melacak payload permintaan/respons.

## Langkah 7: Bonus – Menambahkan UI Sederhana

Jika Anda lebih suka front‑end Windows Forms yang cepat:

```csharp
// inside a button click handler
var filePath = openFileDialog1.FileName;
Document doc = new Document(filePath);
// reuse the same rewriting logic...
```

Dengan cara ini rekan tim yang tidak teknis dapat drag‑and‑drop file dan mendapatkan penulisan ulang formal tanpa menyentuh kode.

## Kesimpulan

Kami baru saja membangun utilitas C# kecil namun kuat yang **call openai api** (atau LLM lokal kompatibel apa pun) untuk **rewrite paragraph formal** di dalam file Word. Dengan **load word document**, mengirim prompt singkat, dan mengganti teks paragraf, Anda mendapatkan dokumen yang halus dalam hitungan detik.

Dari sini Anda dapat:

- Memperluas alat untuk menangani tabel dan gambar.  
- Mengintegrasikan dengan SharePoint untuk pemolesan dokumen otomatis.  
- Bereksperimen dengan nada lain—**rewrite sentence formal**, **rewrite sentence casual**, atau bahkan **rewrite sentence persuasive**.

Cobalah, sesuaikan prompt, dan biarkan LLM melakukan pekerjaan berat untuk Anda. Selamat coding!

## Tutorial Terkait

- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)
- [Apply Paragraph Style In Word Document](/words/english/net/document-formatting/apply-paragraph-style/)
- [Move To Paragraph In Word Document](/words/english/net/add-content-using-documentbuilder/move-to-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}