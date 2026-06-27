---
category: general
date: 2026-06-27
description: Cara memeriksa tata bahasa di C# menggunakan Aspose.Words AI dan LLM
  yang dihosting sendiri. Pelajari cara mengintegrasikan LLM lokal, menjalankan pemeriksa
  tata bahasa, dan mengonfigurasi LLM yang dihosting sendiri.
draft: false
keywords:
- how to check grammar
- integrate local llm
- run grammar checker
- how to use grammarchecker
- configure self‑hosted llm
language: id
og_description: Cara memeriksa tata bahasa di C# dengan Aspose.Words AI. Panduan ini
  menunjukkan cara mengintegrasikan LLM lokal, menjalankan pemeriksa tata bahasa,
  dan mengonfigurasi LLM yang dihosting sendiri.
og_title: Cara Memeriksa Tata Bahasa dengan Aspose.Words AI – Tutorial Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: How to check grammar in C# using Aspose.Words AI and a self‑hosted
    LLM. Learn to integrate local LLM, run grammar checker, and configure self‑hosted
    LLM.
  headline: How to Check Grammar with Aspose.Words AI – Complete Guide
  type: TechArticle
- description: How to check grammar in C# using Aspose.Words AI and a self‑hosted
    LLM. Learn to integrate local LLM, run grammar checker, and configure self‑hosted
    LLM.
  name: How to Check Grammar with Aspose.Words AI – Complete Guide
  steps:
  - name: '**Sentence segmentation:** Aspose.Words splits the document into individual
      sentences.'
    text: '**Sentence segmentation:** Aspose.Words splits the document into individual
      sentences.'
  - name: '**Prompt construction:** Each sentence is wrapped in a prompt that asks
      the LLM to identify grammatical issues.'
    text: '**Prompt construction:** Each sentence is wrapped in a prompt that asks
      the LLM to identify grammatical issues.'
  - name: '**Batching:** To reduce round‑trip latency, sentences are sent in batches
      (default size = 10).'
    text: '**Batching:** To reduce round‑trip latency, sentences are sent in batches
      (default size = 10).'
  - name: '**Result aggregation:** The LLM’s responses are parsed into `GrammarIssue`
      objects, each containing a position and a human‑readable message.'
    text: '**Result aggregation:** The LLM’s responses are parsed into `GrammarIssue`
      objects, each containing a position and a human‑readable message.'
  type: HowTo
tags:
- Aspose.Words
- C#
- AI
- Grammar Checking
- Local LLM
title: Cara Memeriksa Tata Bahasa dengan Aspose.Words AI – Panduan Lengkap
url: /id/net/ai-powered-document-processing/how-to-check-grammar-with-aspose-words-ai-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Memeriksa Tata Bahasa dengan Aspose.Words AI – Panduan Lengkap

Cara memeriksa tata bahasa dalam dokumen Word menggunakan Aspose.Words AI lebih mudah daripada yang Anda kira. Jika Anda pernah bertanya-tanya apakah model bahasa yang di‑host secara mandiri dapat memberikan validasi tata bahasa secara real‑time, Anda berada di tempat yang tepat. Dalam tutorial ini kami akan menunjukkan cara memuat file .docx, mengonfigurasi endpoint LLM lokal, dan akhirnya menjalankan `GrammarChecker` bawaan. Pada akhir tutorial Anda akan benar‑benar tahu **cara menggunakan GrammarChecker** dalam aplikasi C# tingkat produksi—tanpa memerlukan kunci cloud.

> **Anda akan mendapatkan:** contoh kode yang berfungsi penuh, penjelasan langkah‑demi‑langkah, dan beberapa tips praktis yang membantu Anda menghindari jebakan umum. Tidak diperlukan dokumentasi eksternal; semuanya ada di sini.

---

## Cara Memeriksa Tata Bahasa dengan Aspose.Words AI

Sebelum kita masuk ke kode, mari kita tetapkan konteksnya. Bayangkan Anda sedang membangun editor dokumen yang harus berfungsi secara offline—mungkin untuk lembaga pemerintah yang aman atau perangkat lapangan yang remote. Anda membutuhkan mesin tata bahasa yang tidak pernah meninggalkan lingkungan Anda. Di sinilah **mengintegrasikan LLM lokal** bersinar. Aspose.Words AI dilengkapi dengan kelas `SelfHostedLlmModel` yang memungkinkan Anda menunjuk ke endpoint kompatibel OpenAI apa pun yang Anda jalankan sendiri. Sisa tutorial menunjukkan secara tepat cara menghubungkannya.

![How to check grammar with Aspose.Words AI](/images/grammar-checker-aspnet.png "how to check grammar with Aspose.Words AI")

## Langkah 1: Muat Dokumen Word Anda

Hal pertama yang Anda butuhkan adalah instance `Document`. Objek ini mewakili seluruh file .docx dan memberikan mesin tata bahasa tampilan teks yang bersih dan terurai.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Load the input file – make sure the path is correct for your environment.
var document = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of pages so you know the file loaded.
Console.WriteLine($"Document loaded: {document.PageCount} pages");
```

**Mengapa ini penting:** Aspose.Words melakukan semua pekerjaan berat—ekstraksi teks, analisis tata letak, dan pelestarian gaya—sehingga model AI hanya melihat kalimat yang bersih dan ter‑tokenisasi. Melewatkan langkah ini akan memaksa Anda menulis parser sendiri, yang jarang sepadan dengan usaha.

## Konfigurasikan Endpoint LLM Self‑Hosted

Sekarang kita memberi tahu Aspose.Words di mana menemukan model bahasa. Kelas `SelfHostedLlmModel` adalah pembungkus tipis di atas server apa pun yang mengikuti kontrak OpenAI `/v1/completions`.

```csharp
var llmModel = new SelfHostedLlmModel
{
    Endpoint = "http://localhost:5000/v1/completions", // your local server address
    ApiKey   = "my-local-key"                         // keep this secret!
};
```

### Tips untuk konfigurasi yang lancar

* **Pemilihan port:** 5000 adalah default untuk banyak penyebaran lokal, tetapi Anda dapat memilih port bebas apa saja. Cukup perbarui URL sesuai.
* **TLS:** Jika Anda menjalankan endpoint melalui HTTPS, pastikan sertifikat dipercaya oleh runtime .NET; jika tidak Anda akan mendapatkan `HttpRequestException`.
* **Timeout:** Timeout default adalah 30 detik. Untuk dokumen besar Anda mungkin perlu meningkatkan nilai ini melalui `llmModel.Timeout = TimeSpan.FromMinutes(2);`.

Dengan **mengonfigurasi LLM self‑hosted**, Anda menjaga data tetap di‑premises dan menghindari latensi pihak ketiga—sempurna untuk skenario dengan kepatuhan yang ketat.

## Jalankan Grammar Checker Menggunakan LLM Lokal

Dengan dokumen dan model siap, langkah berikutnya adalah memanggil mesin tata bahasa. Metode statis `GrammarChecker.CheckGrammar` melakukan pekerjaan berat.

```csharp
// Execute grammar checking – the call is synchronous for simplicity.
var grammarResult = GrammarChecker.CheckGrammar(document, llmModel);
```

### Apa yang terjadi di balik layar?

1. **Segmentasi kalimat:** Aspose.Words memecah dokumen menjadi kalimat‑kalimat terpisah.
2. **Konstruksi prompt:** Setiap kalimat dibungkus dalam prompt yang meminta LLM mengidentifikasi masalah tata bahasa.
3. **Batching:** Untuk mengurangi latensi round‑trip, kalimat dikirim dalam batch (ukuran default = 10).
4. **Agregasi hasil:** Respons LLM diurai menjadi objek `GrammarIssue`, masing‑masing berisi posisi dan pesan yang dapat dibaca manusia.

Karena kita **menjalankan grammar checker** terhadap model lokal, seluruh pipeline tetap berada dalam jaringan Anda—tidak ada data yang pernah menyentuh internet.

## Cara Menggunakan GrammarChecker dalam Proyek C# Anda

Anda mungkin bertanya, “Apakah saya perlu merujuk paket NuGet khusus?” Jawabannya ya, tetapi hanya dua paket:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Setelah menambahkannya, kelas `GrammarChecker` menjadi tersedia. Berikut ringkasan cepat properti paling berguna pada `GrammarResult` yang dikembalikan:

| Properti | Tipe | Deskripsi |
|----------|------|-------------|
| `Issues` | `IReadOnlyList<GrammarIssue>` | Kumpulan semua masalah yang terdeteksi. |
| `Score` | `float` | Skor kepercayaan keseluruhan (0‑1). |
| `ProcessingTime` | `TimeSpan` | Berapa lama pemeriksaan berlangsung. |

Anda juga dapat memfilter masalah berdasarkan tingkat keparahan jika model Anda mengembalikan metadata tersebut:

```csharp
var highSeverity = grammarResult.Issues
    .Where(i => i.Severity == Severity.High);
Console.WriteLine($"High‑severity issues: {highSeverity.Count()}");
```

## Integrasikan LLM Lokal untuk Pemeriksaan Tata Bahasa Real‑Time

Jika aplikasi Anda membutuhkan **umpan balik real‑time** (bayangkan add‑in pengolah kata), Anda dapat membungkus pemeriksaan dalam metode async dan memanggilnya pada setiap penekanan tombol. Di bawah ini contoh wrapper async minimal yang menunda (debounce) panggilan cepat:

```csharp
private static readonly SemaphoreSlim _semaphore = new SemaphoreSlim(1, 1);
private static DateTime _lastEdit = DateTime.MinValue;
private const int DebounceMs = 500;

public async Task CheckGrammarAsync(Document doc, SelfHostedLlmModel model)
{
    // Debounce: wait until the user pauses typing.
    var now = DateTime.UtcNow;
    if ((now - _lastEdit).TotalMilliseconds < DebounceMs) return;
    _lastEdit = now;

    await _semaphore.WaitAsync();
    try
    {
        var result = await Task.Run(() => GrammarChecker.CheckGrammar(doc, model));
        // Update UI with result.Issues …
    }
    finally
    {
        _semaphore.Release();
    }
}
```

**Mengapa debounce?** Mengirim permintaan untuk setiap karakter akan membebani LLM dan CPU Anda. jeda 500 ms adalah kompromi yang baik antara responsivitas dan penggunaan sumber daya.

## Menampilkan dan Menindaklanjuti Hasil

Akhirnya, mari cetak masalah ke konsol—seperti potongan kode asli—tetapi dengan sedikit konteks tambahan:

```csharp
// Show a summary line.
Console.WriteLine($"Issues found: {grammarResult.Issues.Count} (processed in {grammarResult.ProcessingTime.TotalSeconds:F2}s)");

// Iterate through each issue.
foreach (var issue in grammarResult.Issues)
{
    // Position is a zero‑based character offset.
    Console.WriteLine($"{issue.Position:D6}: {issue.Message} (Severity: {issue.Severity})");
}
```

Output mungkin terlihat seperti:

```
Issues found: 3 (processed in 1.42s)
000015: Use of passive voice – consider active construction. (Severity: Medium)
000087: Missing article before 'apple'. (Severity: Low)
000212: Subject‑verb agreement error: 'they is' → 'they are'. (Severity: High)
```

Anda kini dapat mengirimkan pesan-pesan ini kembali ke UI Anda, menyorot teks yang bermasalah, atau bahkan menawarkan perbaikan satu‑klik.

## Jebakan Umum & Tips Pro

| Jebakan | Cara Menghindari |
|---------|-------------------|
| **Endpoint tidak dapat dijangkau** | Verifikasi URL dengan `curl` atau Postman sebelum menjalankan aplikasi Anda. |
| **Kunci API tidak cocok** | Simpan kunci dalam `appsettings.json` yang aman dan baca melalui `Configuration["Llm:ApiKey"]`. |
| **Dokumen besar menyebabkan timeout** | Tingkatkan `SelfHostedLlmModel.Timeout` atau bagi dokumen menjadi beberapa bagian. |
| **Payload JSON tidak terduga** | Pastikan server lokal Anda mengikuti skema OpenAI (`model`, `prompt`, `max_tokens`). |
| **Referensi `Aspose.Words.AI` hilang** | Periksa kembali paket NuGet; paket AI terpisah dari core Aspose.Words. |

## Kesimpulan

Anda kini memiliki **solusi lengkap end‑to‑end untuk memeriksa tata bahasa** dalam file .docx menggunakan Aspose.Words AI dan **LLM self‑hosted**. Kami telah membahas cara memuat dokumen, **mengonfigurasi LLM self‑hosted**, **menjalankan grammar checker**, dan bahkan **mengintegrasikan pemeriksaan ke dalam alur kerja real‑time**. Kode siap disisipkan ke proyek .NET apa pun, dan penjelasannya akan memberi Anda kepercayaan untuk menyesuaikannya ke skenario lain—seperti pemeriksaan ejaan, penegakan gaya, atau aturan linguistik khusus.

Apa selanjutnya? Coba ganti endpoint dengan model yang lebih besar, bereksperimen dengan ukuran batch, atau hubungkan daftar `GrammarIssue` ke editor Rich Text untuk menggarisbawahi kesalahan saat pengguna mengetik. Tidak ada batasan ketika Anda **mengintegrasikan LLM lokal** untuk kecerdasan bahasa di perangkat.

Selamat coding, semoga dokumen Anda selalu bebas dari kesalahan!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara Mengintegrasikan AI dengan Aspose.Words untuk Java – AI & ML](/words/english/java/ai-machine-learning-integration/)
- [Cara Memuat HTML dan Menyimpan sebagai DOCX menggunakan Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [Cara Menangkap Font di Aspose.Words – Panduan Lengkap](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}