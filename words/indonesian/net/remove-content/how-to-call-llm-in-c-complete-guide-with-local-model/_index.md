---
category: general
date: 2026-01-13
description: Pelajari cara memanggil LLM dari C# menggunakan endpoint LLM lokal, mengedit
  file Word, menghapus semua konten, dan menyimpan docx—semua dalam satu tutorial.
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: id
og_description: Cara memanggil LLM dari C# menggunakan model lokal, mengedit dokumen
  Word, menghapus semua konten, dan menyimpan file docx secara efisien.
og_title: Cara Memanggil LLM di C# – Tutorial Langkah demi Langkah
tags:
- Aspose.Words
- C#
- LLM Integration
title: Cara Memanggil LLM di C# – Panduan Lengkap dengan Model Lokal
url: /id/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Memanggil LLM di C# – Panduan Lengkap dengan Model Lokal

Pernah bertanya-tanya **how to call LLM** dari aplikasi .NET tanpa mengirim data ke cloud? Anda tidak sendirian. Banyak pengembang ingin menyimpan prompt dan dokumen mereka secara on‑premises, terutama ketika menangani teks sensitif. Dalam tutorial ini kita akan menelusuri skenario dunia nyata: menggunakan endpoint LLM yang di‑host sendiri untuk menulis ulang dokumen Word, menghapus semua konten, mengedit file, dan akhirnya **how to save docx** kembali ke disk.  

Kami juga akan membahas **use local LLM**, menunjukkan kode tepat untuk **remove all content** dari `Document` Aspose.Words, dan menjelaskan nuansa mengedit file Word secara programatis. Pada akhir tutorial Anda akan memiliki solusi salin‑tempel yang berfungsi dengan Aspose.Words 7+ dan model lokal yang kompatibel dengan OpenAI.

## Prasyarat – Apa yang Anda Butuhkan Sebelum Memulai

- **.NET 6+** (atau .NET Framework 4.7.2 jika Anda lebih suka versi klasik)
- Paket NuGet **Aspose.Words for .NET** (`Aspose.Words` dan `Aspose.Words.AI`)
- Sebuah **local LLM** yang menyediakan endpoint `/v1` kompatibel OpenAI (misalnya server GPT‑Neo pada `http://localhost:8000/v1`)
- Contoh file `input.docx` yang ditempatkan di folder yang Anda kontrol
- Visual Studio, Rider, atau editor apa pun yang Anda suka – saya akan menggunakan VS Code dalam tangkapan layar

> **Pro tip:** Jika Anda belum memiliki model lokal, coba gambar Docker gratis untuk GPT‑Neo 2.7B – gambar ini dapat dijalankan dalam kurang dari satu menit dan mematuhi kontrak API yang sama seperti yang kami gunakan di sini.

## Langkah 1 – Konfigurasikan Endpoint Local LLM (How to Call LLM)

Hal pertama yang harus Anda lakukan ketika ingin **how to call llm** dari C# adalah membuat objek klien yang mengarah ke layanan yang di‑host sendiri. Aspose.Words.AI menyediakan helper `LocalLargeLanguageModel` yang mengabstraksi panggilan HTTP.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Configure the self‑hosted LLM endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",   // your local server
    ModelName = "my-gpt-neo"                // name as registered in the server
};
```

> **Mengapa ini penting:** Dengan mengonfigurasi endpoint sendiri, Anda memiliki kontrol penuh atas payload permintaan, otentikasi, dan latensi. Ini adalah inti dari **how to call llm** tanpa bergantung pada layanan eksternal.

## Langkah 2 – Muat Dokumen Word Sumber (How to Edit Word)

Selanjutnya, kita memuat file `.docx` asli ke dalam `Document` Aspose. Ini adalah langkah klasik “how to edit word”: begitu file berada di memori, Anda dapat menanyakan, memodifikasi, atau sepenuhnya mengganti isinya.

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Jika file tidak ada, Anda akan mendapatkan `FileNotFoundException`, jadi pastikan jalurnya benar. Anda juga dapat memuat dari `Stream` jika sedang menangani unggahan.

## Langkah 3 – Hasilkan Teks Revisi Menggunakan Local LLM (How to Call LLM)

Sekarang saatnya sihir: kita meminta LLM menulis ulang seluruh teks dengan nada formal. Prompt dibangun dengan menggabungkan instruksi singkat dengan teks mentah yang diekstrak melalui `document.GetText()`.

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **Kasus tepi:** Jika dokumen sumber sangat besar (lebih dari 10 k token) Anda mungkin akan mencapai batas konteks model. Dalam hal ini, bagi teks menjadi paragraf dan panggil `GenerateText` untuk setiap potongan.

## Langkah 4 – Hapus Semua Konten yang Ada (Remove All Content)

Sebelum kita menyisipkan teks baru, kita perlu membersihkan dokumen. Aspose menyediakan `RemoveAllChildren()` yang menghapus semua section, paragraph, table—semuanya. Ini adalah cara kanonik untuk **remove all content** dari file Word.

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **Bagaimana jika Anda hanya ingin menghapus body tetapi tetap menyimpan header?** Gunakan `document.Sections.Clear()` lalu bangun kembali section yang Anda perlukan.

## Langkah 5 – Sisipkan Teks Revisi (How to Edit Word)

Dengan kanvas bersih, kita dapat menulis kembali teks yang dihasilkan LLM. `DocumentBuilder` adalah pembungkus yang ramah yang memungkinkan Anda menambahkan paragraf, tabel, gambar, dll. Di sini kami cukup menulis seluruh string sebagai satu paragraf.

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

Jika Anda memerlukan format yang lebih kaya (tebal, heading) Anda dapat mem-parsing output LLM untuk penanda markdown dan menerapkan pengaturan `builder.Font` yang sesuai.

## Langkah 6 – Simpan Dokumen yang Diperbarui (How to Save Docx)

Akhirnya, kami menyimpan perubahan ke file baru. Ini mendemonstrasikan **how to save docx** setelah edit secara programatis.

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

Metode `Save` secara otomatis mendeteksi format dari ekstensi file, jadi Anda juga dapat mengekspor ke PDF, HTML, atau ODT hanya dengan mengubah satu baris.

### Hasil yang Diharapkan

Saat Anda membuka `output.docx`, Anda akan melihat seluruh konten asli telah ditulis ulang dalam gaya formal yang terpolitur. Tidak ada tabel, header, atau footer yang tersisa dari sumber—hanya teks segar yang diminta LLM untuk dihasilkan.

---

![Screenshot of output.docx opened in Word, showing formal rewritten text – how to call llm](/images/output-docx.png "contoh cara memanggil llm")

*Teks alt gambar:* **how to call llm example showing rewritten Word document**

## Pertanyaan Umum & Pemecahan Masalah

### 1. “Bagaimana jika LLM saya mengembalikan error?”

Metode `GenerateText` melempar `HttpRequestException` untuk respons non‑2xx. Bungkus panggilan dalam `try/catch` dan periksa `ex.Message`. Seringkali masalahnya adalah header API key yang hilang atau melebihi batas token model.

```csharp
try
{
    string revisedText = llm.GenerateText(prompt);
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"LLM call failed: {ex.Message}");
    // fallback logic, e.g., return the original text
}
```

### 2. “Bisakah saya mengedit bagian tertentu dari dokumen alih‑alih menghapus semuanya?”

Tentu saja. Gunakan `document.GetChildNodes(NodeType.Paragraph, true)` untuk menelusuri paragraf, lalu ganti properti `Paragraph.Text` hanya pada bagian yang perlu diubah. Pendekatan ini memungkinkan Anda **how to edit word** secara granular sambil mempertahankan gaya.

### 3. “Apakah ada cara untuk mempertahankan format asli?”

Jika Anda ingin mempertahankan gaya, pertimbangkan mengembalikan output LLM sebagai teks biasa dan kemudian menerapkan `builder.Font.StyleIdentifier` ke setiap paragraf berdasarkan templat Anda. Alternatifnya, gunakan `DocumentBuilder.InsertHtml()` jika LLM dapat menghasilkan HTML.

### 4. “Bagaimana cara menangani dokumen besar?”

Bagi dokumen menjadi section (`document.Sections`) dan proses masing‑masing secara terpisah. Ini tidak hanya menghindari batas token tetapi juga mengurangi tekanan memori.

## Tips Kinerja

- **Gunakan kembali instance `LocalLargeLanguageModel`** untuk banyak panggilan; `HttpClient` di bawahnya akan menjaga koneksi tetap hidup.
- **Cache teks yang telah direvisi** jika Anda memperkirakan akan menjalankan prompt yang sama berulang kali—panggilan LLM dapat mahal bahkan pada perangkat keras lokal.
- **Paralelisasi** pemrosesan section dengan `Parallel.ForEach` ketika Anda memiliki CPU multi‑core dan klien LLM yang thread‑safe.

## Langkah Selanjutnya – Memperluas Alur Kerja

Setelah Anda menguasai **how to call llm**, **use local llm**, **remove all content**, **how to edit word**, dan **how to save docx**, Anda mungkin ingin menjelajahi:

- **Pemrosesan batch**: Loop melalui folder berisi file `.docx` dan terapkan logika penulisan ulang yang sama.
- **Prompt khusus**: Sesuaikan instruksi untuk menghasilkan ringkasan, daftar poin, atau terjemahan.
- **Integrasi dengan ASP.NET Core**: Ekspos endpoint HTTP yang menerima unggahan file, menjalankan LLM, dan mengembalikan dokumen yang telah diedit.
- **Styling lanjutan**: Parse markdown dari LLM dan petakan ke gaya Word menggunakan `DocumentBuilder`.

Setiap ekstensi ini dibangun di atas pola inti yang telah kami bahas, sehingga Anda dapat menyesuaikan kode dengan usaha minimal.

---

## Kesimpulan

Dalam panduan ini kami membahas **how to call llm** dari C# menggunakan endpoint yang di‑host sendiri, mendemonstrasikan **use local llm**, menunjukkan cara yang tepat untuk **remove all content** dari file Word, menjelaskan **how to edit word** secara programatis, dan menutup semuanya dengan contoh jelas **how to save docx**. Contoh lengkap yang dapat dijalankan siap disisipkan ke proyek .NET apa pun, dan penjelasan memberikan “mengapa” di balik setiap langkah—sehingga Anda dapat menyesuaikan, memperluas, atau debug dengan percaya diri.

Cobalah, eksperimen dengan berbagai prompt, dan biarkan LLM lokal melakukan pekerjaan berat untuk pipeline otomatisasi dokumen Anda. Jika Anda menemui kendala, bagian pemecahan masalah akan mengarahkan Anda ke solusi yang tepat. Selamat coding, dan nikmati kekuatan LLM on‑prem!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}