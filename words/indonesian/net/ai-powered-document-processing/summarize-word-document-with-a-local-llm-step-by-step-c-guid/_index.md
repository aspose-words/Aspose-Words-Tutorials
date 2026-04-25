---
category: general
date: 2026-04-24
description: Ringkas dokumen Word menggunakan Aspose.Words dan jalankan LLM secara
  lokal. Pelajari cara menghubungkan ke LLM lokal, menghasilkan ringkasan dokumen,
  dan memanggil LLM lokal dalam hitungan menit.
draft: false
keywords:
- summarize word document
- connect to local llm
- run llm locally
- generate document summary
- how to call local llm
language: id
og_description: Ringkas dokumen Word secara instan dengan menghubungkan ke LLM lokal.
  Panduan ini menunjukkan cara menjalankan LLM secara lokal dan menghasilkan ringkasan
  dokumen dengan Aspose.Words.
og_title: Ringkas Dokumen Word dengan LLM Lokal – Tutorial C# Lengkap
tags:
- Aspose.Words
- C#
- LLM
- AI
title: Ringkas Dokumen Word dengan LLM Lokal – Panduan C# Langkah demi Langkah
url: /id/net/ai-powered-document-processing/summarize-word-document-with-a-local-llm-step-by-step-c-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ringkas Dokumen Word dengan LLM Lokal – Tutorial Lengkap C#

Pernah perlu **meringkas dokumen word** secara otomatis tetapi organisasi Anda menolak mengirim data ke cloud? Anda tidak sendirian. Di banyak lingkungan yang diatur, satu‑satunya cara aman adalah **menjalankan LLM secara lokal** dan membiarkannya melakukan pekerjaan berat di‑premises. Tutorial ini menunjukkan secara tepat cara **menghubungkan ke llm lokal**, memasukkan file Word ke Aspose.Words, dan **menghasilkan ringkasan dokumen** dalam beberapa baris C#.

Kami akan membahas semua yang Anda perlukan—prasyarat, kode, penjelasan, dan bahkan beberapa jebakan yang mungkin Anda temui. Pada akhir tutorial, Anda akan dapat memanggil LLM lokal dari C# dan menghasilkan ringkasan singkat untuk file `.docx` apa pun, tanpa meninggalkan mesin Anda.

## Apa yang Anda Butuhkan

- **.NET 6+** (atau .NET Framework 4.7+ jika Anda lebih suka runtime klasik)  
- Paket NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
- Paket NuGet **Aspose.Words.AI** (`Aspose.Words.AI`) – paket ini menyediakan helper `DocumentAI`.  
- **Endpoint LLM lokal** yang mengekspos API kompatibel OpenAI (misalnya Ollama, LM Studio, atau vLLM yang di‑host sendiri). Endpoint harus dapat diakses di `http://localhost:5000`.  
- File Word contoh (`input.docx`) yang ditempatkan di folder yang dapat direferensikan dari kode Anda.

> **Pro tip:** Jika Anda belum memiliki LLM lokal, coba `ollama run llama3` – perintah ini akan memulai server di `localhost:11434`. Anda kemudian dapat mem‑proxy port tersebut ke `5000` dengan Nginx kecil atau menggunakan flag `--port` jika alat Anda mendukungnya.

## Ikhtisar Solusi

1. Muat dokumen Word sumber menggunakan Aspose.Words.  
2. Buat objek `LocalLargeLanguageModel` yang menunjuk ke LLM yang berjalan secara lokal.  
3. Panggil `DocumentAI.Summarize` agar AI membaca dokumen dan mengembalikan ringkasan singkat.  
4. Cetak hasilnya ke konsol (atau simpan di mana pun Anda perlukan).

Itu saja—empat langkah logis, masing‑masing dijelaskan di bawah ini.

## Langkah 1 – Muat Dokumen Word yang Ingin Dirangkum

Hal pertama yang kita lakukan adalah membuat instance `Document` yang mewakili file `.docx` di disk. Aspose.Words mem‑parsing file menjadi model objek yang kaya, memberi kita akses ke paragraf, tabel, gambar, dan metadata.

```csharp
using Aspose.Words;

// Step 1: Load the source document you want to summarize
// Replace "YOUR_DIRECTORY" with the actual path where input.docx lives.
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
Document doc = new Document(inputPath);
```

**Mengapa ini penting:**  
Memuat dokumen secara lokal memastikan Anda tidak pernah mengekspos konten mentah ke layanan eksternal. Aspose.Words juga menormalkan teks (menghapus karakter tersembunyi, menangani Unicode) sehingga LLM menerima input yang bersih.

## Langkah 2 – Buat Koneksi ke Endpoint LLM Lokal Anda

Selanjutnya kita memerlukan objek yang tahu cara berkomunikasi dengan LLM yang berjalan di mesin kita. `LocalLargeLanguageModel` adalah wrapper tipis di atas klien HTTP yang mengikuti kontrak API OpenAI.

```csharp
using Aspose.Words.AI;

// Step 2: Create a connection to your local Large Language Model endpoint
// The URL should point to the base address of the API (e.g., http://localhost:5000/v1)
var llm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Mengapa ini penting:**  
Dengan menentukan endpoint secara eksplisit, Anda **cara memanggil llm lokal** dengan cara yang bekerja pada server kompatibel apa pun—Ollama, LM Studio, atau wrapper Flask khusus. Jika endpoint memerlukan API key, Anda dapat memberikannya sebagai argumen kedua: `new LocalLargeLanguageModel(url, "my‑api‑key")`.

## Langkah 3 – Hasilkan Ringkasan Singkat Menggunakan DocumentAI

Sekarang keajaiban terjadi. `DocumentAI.Summarize` mengalirkan teks dokumen ke LLM, meminta LLM menghasilkan ringkasan pendek, dan mengembalikan hasilnya sebagai string.

```csharp
// Step 3: Generate a concise summary of the document using DocumentAI
string summary = DocumentAI.Summarize(doc, llm);
```

**Mengapa ini penting:**  
`DocumentAI` menangani chunking (memecah dokumen besar menjadi potongan yang dapat dikelola) dan prompt engineering di balik layar. Anda tidak perlu khawatir tentang batas token atau format—cukup panggil `Summarize` dan dapatkan paragraf yang dapat dibaca manusia.

### Menyesuaikan Prompt (Opsional)

Jika Anda memerlukan nada atau panjang tertentu, Anda dapat mengirimkan objek `SummarizationOptions`:

```csharp
var options = new SummarizationOptions
{
    MaxTokens = 150,                 // limit the summary size
    Temperature = 0.3,               // keep it deterministic
    Prompt = "Provide a bullet‑point summary in plain English."
};

string customSummary = DocumentAI.Summarize(doc, llm, options);
```

## Langkah 4 – Tampilkan atau Simpan Ringkasan yang Dihasilkan

Akhirnya, kita menampilkan ringkasan. Dalam aplikasi dunia nyata Anda mungkin menulisnya ke basis data, mengirimnya lewat email, atau menyematkannya kembali ke file Word asli sebagai komentar.

```csharp
// Step 4: Display the generated summary
Console.WriteLine("=== Document Summary ===");
Console.WriteLine(summary);
```

**Output yang diharapkan** (contoh untuk brief pemasaran 2‑halaman):

```
=== Document Summary ===
The brief outlines a Q3 product launch targeting millennials, emphasizing social media outreach, influencer partnerships, and a limited‑edition colorway. Key milestones include design finalization by June 15, production start July 1, and a soft rollout on August 10.
```

Jika Anda menggunakan opsi khusus di atas, Anda akan melihat poin‑poin bullet alih‑alih paragraf.

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut adalah aplikasi konsol satu‑file yang dapat Anda salin‑tempel ke Visual Studio atau VS Code.

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document you want to summarize
        // -------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -------------------------------------------------
        // Step 2: Connect to your locally running LLM
        // -------------------------------------------------
        var llm = new LocalLargeLanguageModel("http://localhost:5000");

        // -------------------------------------------------
        // Step 3: Ask the AI to summarize the document
        // -------------------------------------------------
        string summary = DocumentAI.Summarize(doc, llm);

        // -------------------------------------------------
        // Step 4: Show the result (or store it somewhere)
        // -------------------------------------------------
        Console.WriteLine("=== Document Summary ===");
        Console.WriteLine(summary);
    }
}
```

**Cara menjalankannya**

1. `dotnet new console -n Summarizer`  
2. `cd Summarizer`  
3. `dotnet add package Aspose.Words`  
4. `dotnet add package Aspose.Words.AI`  
5. Ganti `Program.cs` dengan kode di atas, sesuaikan `YOUR_DIRECTORY`.  
6. Pastikan server LLM Anda sudah aktif (`curl http://localhost:5000/v1/models` harus mengembalikan JSON).  
7. `dotnet run`

Anda akan melihat ringkasan tercetak di terminal.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika dokumen saya lebih besar daripada batas token model?

`DocumentAI` secara otomatis membagi teks menjadi potongan yang cocok dengan jendela konteks model, lalu menggabungkan ringkasan parsial. Jika Anda ingin kontrol lebih, kirimkan objek `ChunkingOptions` khusus.

### LLM saya mengembalikan error “model not found”. Bagaimana cara memperbaikinya?

Pastikan endpoint yang Anda tunjuk memang menyajikan model bernama `default`. Dengan Ollama, Anda dapat menetapkan model di body permintaan atau menggunakan `llm = new LocalLargeLanguageModel("http://localhost:5000", "my‑model")`.

### Bisakah saya menyematkan ringkasan kembali ke file Word asli?

Tentu saja. Gunakan kelas `Comment` dari Aspose.Words:

```csharp
doc.Comments.Add(new Comment(doc, "AI", "Summary", DateTime.Now) { Text = summary });
doc.Save("output_with_summary.docx");
```

Sekarang ringkasan berada di dalam dokumen sebagai catatan tempel.

### Bagaimana cara mengamankan komunikasi dengan LLM lokal?

Jika endpoint Anda mendukung HTTPS, ubah URL menjadi `https://localhost:5000`. Anda juga dapat menambahkan bearer token saat membuat `LocalLargeLanguageModel`.

## Tips untuk Penggunaan Produksi

- **Cache ringkasan**: Simpan hasil di basis data dengan kunci hash file untuk menghindari meringkas ulang file yang tidak berubah.  
- **Rate‑limit panggilan**: Bahkan model lokal mengonsumsi CPU/GPU; semaphore sederhana dapat mencegah overload.  
- **Logging**: Rekam payload permintaan/response mentah (redact teks sensitif) untuk debugging.  
- **Penanganan error**: Bungkus `DocumentAI.Summarize` dalam try/catch dan gunakan fallback heuristik (misalnya ekstraksi paragraf pertama) jika LLM tidak tersedia.

## Kesimpulan

Anda kini tahu cara **meringkas konten dokumen word** dengan **menghubungkan ke llm lokal**, memanggil API AI Aspose.Words, dan menangani hasilnya dalam aplikasi konsol C# yang bersih. Pendekatan ini memungkinkan Anda **menjalankan llm secara lokal**, menjaga data tetap on‑prem, dan tetap memanfaatkan kemampuan ringkasan bahasa alami yang kuat.

Langkah selanjutnya? Coba ganti pemanggilan `Summarize` dengan `ExtractKeyPhrases` atau `TranslateDocument`—keduanya tersedia di `DocumentAI`. Anda juga dapat bereksperimen dengan LLM berbeda (misalnya `phi‑3`, `gemma‑2b`) untuk membandingkan kualitas dan latensi. Polanya tetap sama: muat, hubungkan, panggil, dan konsumsi.

Selamat coding, dan jangan ragu berbagi pengalaman atau mengajukan pertanyaan lanjutan di kolom komentar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}