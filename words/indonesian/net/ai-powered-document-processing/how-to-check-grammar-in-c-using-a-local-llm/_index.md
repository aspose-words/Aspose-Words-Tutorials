---
category: general
date: 2026-02-21
description: Cara memeriksa tata bahasa di C# dengan memuat file DOCX, mengirim teksnya
  ke LLM lokal, dan menulis kembali versi yang telah diperbaiki. Termasuk cara menggunakan
  LLM dan membaca teks dokumen Word.
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: id
og_description: Cara memeriksa tata bahasa di C# dengan memuat file DOCX, mengirimkan
  teksnya ke LLM lokal, dan menulis kembali versi yang telah diperbaiki. Pelajari
  cara menggunakan LLM dan membaca teks dokumen Word.
og_title: Cara Memeriksa Tata Bahasa di C# Menggunakan LLM Lokal
tags:
- C#
- LLM
- Aspose.Words
title: Cara Memeriksa Tata Bahasa di C# dengan LLM Lokal
url: /id/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

Let's produce final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Memeriksa Tata Bahasa di C# Menggunakan LLM Lokal

Pernah bertanya-tanya **cara memeriksa tata bahasa** dalam dokumen Word tanpa meninggalkan proyek C# Anda? Anda bukan satu-satunya—para pengembang terus bertanya, “Bisakah saya mengotomatiskan proofreading dengan kode yang sama yang menggerakkan chatbot?” Jawaban singkatnya adalah ya. Dengan memuat DOCX, mengekstrak teksnya, dan mengirimkannya ke model bahasa besar (LLM) yang dihosting secara lokal, Anda dapat mendapatkan perbaikan tata bahasa secara instan dan menulis hasil yang sudah dipoles kembali ke dalam file.

Dalam tutorial ini kami akan membahas seluruh proses: membaca `.docx` dengan **load docx in c#**, memanggil **how to use llm** untuk koreksi tata bahasa, dan akhirnya menyimpan dokumen yang sudah dibersihkan. Pada akhir tutorial Anda akan memiliki aplikasi console yang siap dijalankan yang melakukan persis apa yang Anda butuhkan—tanpa menyalin‑tempel manual, tanpa API eksternal, hanya C# murni dan endpoint LLM lokal.

> **Apa yang Anda butuhkan**
> - .NET 6.0 atau lebih baru (kode ini juga bekerja di .NET Framework, tetapi .NET 6 adalah pilihan terbaik)
> - Library [Aspose.Words for .NET](https://products.aspose.com/words/net/) (versi trial gratis cukup untuk pengujian)
> - Server LLM yang berjalan dan menyediakan endpoint sederhana `CheckGrammar(string)` (misalnya Ollama, LM Studio, atau wrapper FastAPI khusus)
> - Familiaritas dasar dengan async/await (opsional tetapi disarankan)

Jika Anda bertanya-tanya **mengapa ini penting**, pikirkan berapa banyak waktu yang Anda habiskan untuk memperbaiki typo secara manual dalam laporan yang dihasilkan. Mengotomatiskan langkah ini tidak hanya mempercepat pipeline tetapi juga menjamin konsistensi di antara puluhan dokumen. Mari kita mulai.

---

## Cara Memeriksa Tata Bahasa – Ikhtisar

Sebelum kita mulai, berikut peta jalan singkat:

1. **Buat klien** yang berkomunikasi dengan endpoint LLM lokal.  
2. **Baca dokumen Word** menggunakan Aspose.Words—ini cara klasik untuk **read word document text** di C#.  
3. **Kirim teks mentah** ke LLM dan terima versi yang sudah dikoreksi.  
4. **Ganti konten asli** dalam dokumen dengan teks yang sudah dikoreksi.  
5. **Simpan** file yang telah diperbarui (opsional tetapi biasanya diperlukan).

Setiap langkah dibungkus dalam metode terpisah sehingga Anda dapat menggunakan kembali atau mengganti bagian-bagian nanti. Kode sumber lengkap muncul di akhir artikel.

---

## Langkah 1: Siapkan Klien LLM (How to Use LLM)

Agar tetap rapi, kami akan membungkus panggilan HTTP dalam kelas wrapper kecil. Kelas ini mengasumsikan layanan LLM menerima permintaan POST dengan payload JSON `{ "prompt": "..."} ` dan mengembalikan `{ "response": "..." }`. Sesuaikan serialisasi jika layanan Anda berbeda.

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**Mengapa ini penting:**  
- **Decoupling** – Jika Anda nanti beralih dari Ollama ke LM Studio, Anda hanya perlu mengubah URL atau format payload.  
- **Async‑friendly** – I/O jaringan tidak akan memblokir UI atau worker latar belakang Anda.  
- **Error handling** – `EnsureSuccessStatusCode` melemparkan pengecualian yang jelas jika LLM tidak merespon, yang akan kami tangkap nanti.

> **Pro tip:** Jika LLM Anda berjalan di GPU, jaga ukuran permintaan di bawah ~4 KB untuk menghindari lonjakan latensi.

---

## Langkah 2: Muat DOCX dan Ekstrak Teks (Read Word Document Text)

Aspose.Words memudahkan pembacaan file Word. Metode `Document.GetText()` mengembalikan seluruh teks yang terlihat, mempertahankan jeda baris. Jika Anda memerlukan format yang lebih kaya (tabel, catatan kaki), Anda harus menelusuri pohon node, tetapi untuk pemeriksaan tata bahasa saja teks polos sudah cukup.

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**Catatan kasus tepi:**  
Jika dokumen berisi karakter non‑English atau simbol khusus, pastikan model LLM yang Anda gunakan mendukung Unicode. Sebagian besar model modern melakukannya, tetapi model lama mungkin memotong atau salah menafsirkan karakter tersebut.

---

## Langkah 3: Ganti Konten dengan Teks yang Sudah Dikoreksi

Aspose.Words tidak memiliki metode satu baris “replace whole body”, tetapi mengosongkan pohon node dan menyisipkan satu paragraf bekerja dengan baik. Ini juga memastikan semua markup tersembunyi (seperti tracked changes) dihapus.

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**Mengapa kami menghapus semua anak:**  
- Menjamin kanvas bersih, mencegah format lama mengganggu konten baru.  
- Menyederhanakan kode—tidak perlu mencari node tertentu untuk diganti.

Jika Anda lebih suka mempertahankan heading asli, Anda dapat menelusuri pohon node asli, mengganti hanya node `Run`, tetapi itu menambah kompleksitas di luar lingkup tutorial ini.

---

## Langkah 4: Sambungkan Semua – Contoh Lengkap yang Berfungsi

Berikut program console lengkap. Program ini menunjukkan **how to check grammar** dari awal hingga akhir, termasuk penanganan error dasar dan argumen baris perintah opsional.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### Output yang Diharapkan

Saat Anda menjalankan program (`dotnet run`), konsol akan menampilkan sesuatu seperti:

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

Buka `output.docx` di Word—Anda akan melihat konten yang sama tetapi dengan tanda baca, kesesuaian subjek‑kata kerja, dan typo jelas yang diperbaiki oleh LLM.

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika LLM mengembalikan `null` atau string kosong?

Metode `CheckGrammarAsync` akan kembali ke input asli jika payload respons tidak memiliki field `response`. Ini mencegah Anda secara tidak sengaja mengosongkan dokumen.

### Seberapa besar dokumen sebelum permintaan timeout?

Sebagian besar server LLM lokal menangani beberapa ribu karakter dengan nyaman. Untuk file yang lebih besar (misalnya 100 KB+), pertimbangkan memecah teks menjadi paragraf, mengirim tiap potongan secara terpisah, lalu menyatukan kembali bagian yang sudah dikoreksi. Ukuran potongan sekitar ~2 KB adalah titik awal yang baik.

### Apakah ini mempertahankan gambar, tabel, atau catatan kaki?

Tidak. Dengan menghapus semua anak kita kehilangan elemen non‑teks apa pun. Jika Anda perlu mempertahankan elemen tersebut, Anda harus menelusuri pohon node, mengganti hanya node `Run` (fragmen teks), dan membiarkan node lain tidak tersentuh. Itu merupakan skenario yang lebih maju—silakan eksplorasi API Aspose.Words untuk manipulasi `NodeCollection`.

### Bisakah saya menggunakan LLM cloud alih-alih yang lokal?

Tentu saja. Cukup ganti URL endpoint dan format payload di `LocalLargeLanguageModel`. Perlu diingat bahwa layanan cloud biasanya memiliki batasan rate dan biaya, sementara model lokal berjalan offline dan gratis setelah setup GPU/CPU selesai.

---

## Pro Tips & Praktik Terbaik

- **Cache the client**: Re‑using the same `HttpClient` instance avoids

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}