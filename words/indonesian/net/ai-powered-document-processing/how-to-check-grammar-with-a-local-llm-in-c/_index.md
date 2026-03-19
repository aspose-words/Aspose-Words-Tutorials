---
category: general
date: 2026-03-19
description: Pelajari cara memeriksa tata bahasa di Word menggunakan LLM lokal, mendaftarkan
  model, dan menyimpan dokumen yang telah diperbaiki—semua dalam satu tutorial C#.
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: id
og_description: Cara memeriksa tata bahasa di Word menggunakan LLM lokal, mendaftarkan
  model, dan menyimpan dokumen yang telah diperbaiki—panduan langkah demi langkah.
og_title: Cara memeriksa tata bahasa dengan LLM lokal di C#
tags:
- Aspose.Words
- AI
- C#
title: Cara memeriksa tata bahasa dengan LLM lokal di C#
url: /id/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memeriksa tata bahasa dengan LLM lokal di C#

Pernah bertanya‑tanya **cara memeriksa tata bahasa** dalam dokumen Word tanpa mengirim teks Anda ke cloud? Anda tidak sendirian. Banyak pengembang menginginkan privasi model yang di‑host sendiri sambil tetap mendapatkan saran berbasis AI. Dalam panduan ini kami akan menjelaskan cara mendaftarkan LLM khusus, mengonfigurasi Aspose.Words untuk menggunakannya, dan akhirnya **cara menyimpan file yang telah diperbaiki**—semua dalam C# biasa.

Kami juga akan membahas detail **menyiapkan llm lokal**, menunjukkan **cara mendaftarkan endpoint llm**, dan mendemonstrasikan langkah‑langkah tepat untuk **memeriksa tata bahasa dalam word**. Pada akhir tutorial Anda akan memiliki contoh yang dapat dijalankan dan dapat disisipkan ke proyek .NET apa pun.

## Prerequisites

Sebelum kita mulai, pastikan Anda memiliki:

- .NET 6+ SDK (kode ini bekerja pada .NET Core dan .NET Framework)
- Visual Studio 2022 atau VS Code dengan ekstensi C#
- Aspose.Words for .NET (v24.12 atau lebih baru) – Anda dapat mengunduhnya dari NuGet
- Sebuah LLM yang berjalan secara lokal dan mendukung API kompatibel OpenAI (misalnya, Ollama pada port 11434)

> **Pro tip:** Jika Anda menggunakan Ollama, perintah `ollama serve` akan secara otomatis menjalankan endpoint `http://localhost:11434/api/generate`.

## Step 1 – How to register llm: Add the custom model to Aspose.Words

Hal pertama yang perlu kita lakukan adalah memberi tahu Aspose.Words tentang **llm lokal** kita. Ini dilakukan satu kali saat aplikasi dimulai.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**Mengapa ini penting:** Dengan mendaftarkan model, Anda memberikan Aspose.Words sebuah handle bernama (`"local-llm"`). Nanti, ketika kita memanggil `CheckGrammar`, perpustakaan tahu tepat endpoint mana yang harus dihubungi. Melewatkan langkah ini akan memaksa perpustakaan kembali ke layanan cloud bawaan, yang menghilangkan tujuan memiliki LLM pribadi.

## Step 2 – Load the Word document you want to analyze

Sekarang kita memuat file ke memori. Anda dapat menunjuk ke file `.docx`, `.doc`, atau bahkan `.rtf` apa pun.

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**Apa yang terjadi:** `Document` adalah model objek inti Aspose.Words. Ia mem‑parsing file dan membangun pohon node (paragraf, tabel, gambar, dll.). Ini memungkinkan mesin AI menargetkan rentang teks tertentu untuk analisis tata bahasa.

## Step 3 – Configure grammar‑check options (set up local llm)

Di sini kita mengaitkan model yang telah didaftarkan sebelumnya dengan operasi pemeriksaan tata bahasa.

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**Mengapa kami mengekspose opsi ini:** Setiap LLM memiliki perilaku yang berbeda. Dengan mengekspose `Model`, Aspose.Words memungkinkan Anda beralih antara model lokal dan model berbasis cloud tanpa mengubah kode lain. Fleksibilitas ini penting ketika **menyiapkan llm lokal** untuk kepatuhan atau skenario offline.

## Step 4 – Run the AI‑driven grammar check (check grammar in word)

Setelah semuanya terhubung, pemeriksaan tata bahasa sebenarnya cukup satu baris kode.

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**Di balik layar:** Aspose.Words mengekstrak setiap kalimat, mengirimnya ke endpoint LLM, menerima payload JSON dengan saran perbaikan, dan kemudian menerapkan perubahan tersebut kembali ke pohon dokumen. Proses ini berjalan secara sinkron di contoh ini untuk kesederhanaan; Anda juga dapat memanggil overload async `CheckGrammarAsync` jika menginginkan I/O non‑blocking.

## Step 5 – How to save corrected documents

Setelah AI selesai bekerja, Anda ingin menyimpan perubahan tersebut.

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**Apa yang diharapkan:** Buka `checked.docx` di Word dan Anda akan melihat masalah tata bahasa yang disorot (atau otomatis diperbaiki, tergantung pada `AiGrammarCheckOptions`). Jika Anda mengaktifkan pelacakan, Anda juga akan melihat tanda revisi.

## Full Working Example

Menggabungkan semua bagian, berikut adalah aplikasi console yang siap dijalankan:

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**Output yang diharapkan di konsol:**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

Buka `checked.docx` dan Anda akan melihat perbaikan tata bahasa yang diterapkan secara otomatis.

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| *What if my LLM requires an API key?* | Pass the key to `apiKey` in `RegisterModel`. The same code works for both keyed and key‑less services. |
| *Can I use a different file format?* | Absolutely. `Document.Save` accepts `.pdf`, `.html`, `.txt`, etc. Just change the extension. |
| *What if the LLM returns an error?* | Wrap `CheckGrammar` in a try/catch; inspect `AiException` for details. Often it’s a timeout—consider increasing `grammarOptions.Timeout`. |
| *Is the operation thread‑safe?* | The registration step is global and should be done once at startup. Subsequent `CheckGrammar` calls are safe to run in parallel as long as each uses its own `Document` instance. |

## Next Steps

Sekarang Anda sudah tahu **cara memeriksa tata bahasa** menggunakan **llm lokal**, Anda dapat mengeksplorasi:

- **Pemrosesan batch**: Loop melalui folder berisi dokumen dan jalankan pipeline yang sama.
- **Prompt khusus**: Sesuaikan payload permintaan dengan mengatur `grammarOptions.PromptTemplate` untuk pemeriksaan gaya tertentu.
- **Integrasi dengan ASP.NET Core**: Ekspos endpoint API yang menerima file `.docx` yang di‑upload, menjalankan pemeriksaan tata bahasa, dan mengembalikan file yang telah diperbaiki.

Ekstensi‑ekstensi ini memungkinkan Anda membangun platform “grammar‑as‑a‑service” lengkap tanpa pernah meninggalkan infrastruktur Anda.

---

*Selamat coding! Jika Anda menemui kendala, tinggalkan komentar di bawah—saya siap membantu menyempurnakan pengaturan Anda.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}