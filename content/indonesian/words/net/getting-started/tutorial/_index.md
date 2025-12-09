---
language: id
url: /indonesian/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Mendeteksi Font yang Hilang dalam Dokumen Aspose.Words – Panduan Lengkap C#

Pernah bertanya-tanya bagaimana cara **mendeteksi font yang hilang** saat Anda memuat file Word dengan Aspose.Words? Dalam pekerjaan sehari-hari saya, saya pernah menemukan beberapa PDF yang tampak aneh karena dokumen asli menggunakan font yang tidak terpasang di sistem saya. Kabar baiknya? Aspose.Words dapat memberi tahu Anda secara tepat kapan ia menggantikan sebuah font, dan Anda dapat menangkap informasi tersebut dengan callback peringatan sederhana.  

Dalam tutorial ini kami akan membahas **contoh lengkap yang dapat dijalankan** yang menunjukkan cara mencatat setiap substitusi font, mengapa callback penting, dan beberapa trik tambahan untuk deteksi font yang hilang yang kuat. Tanpa basa-basi, hanya kode dan penjelasan yang Anda perlukan untuk membuatnya berfungsi hari ini.

---

## Apa yang Akan Anda Pelajari

- Cara mengimplementasikan **Aspose.Words warning callback** untuk menangkap peristiwa substitusi font.  
- Cara mengkonfigurasi **LoadOptions C#** sehingga callback dipanggil saat memuat dokumen.  
- Cara memverifikasi bahwa deteksi font yang hilang benar‑benar berhasil, dan seperti apa output konsolnya.  
- Penyesuaian opsional untuk batch besar atau lingkungan tanpa UI.  

**Prasyarat** – Anda memerlukan versi terbaru Aspose.Words untuk .NET (kode ini diuji dengan 23.12), .NET 6 atau lebih baru, dan pemahaman dasar tentang C#. Jika Anda sudah memiliki itu, Anda siap memulai.

---

## Mendeteksi Font yang Hilang dengan Callback Peringatan

Inti dari solusi ini adalah implementasi `IWarningCallback`. Aspose.Words memicu objek `WarningInfo` untuk banyak situasi, tetapi kita hanya peduli pada `WarningType.FontSubstitution`. Mari kita lihat cara mengaitkannya.

### Langkah 1: Buat Font‑Warning Collector

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Mengapa ini penting*: Dengan memfilter pada `WarningType.FontSubstitution` kita menghindari kebisingan dari peringatan yang tidak terkait (seperti fitur yang sudah usang). `info.Description` sudah berisi nama font asli dan fallback yang digunakan, memberikan jejak audit yang jelas.

---

## Konfigurasikan LoadOptions untuk Menggunakan Callback

Sekarang kita memberi tahu Aspose.Words untuk menggunakan collector kami saat memuat file.

### Langkah 2: Siapkan LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Mengapa ini penting*: `LoadOptions` adalah satu‑satunya tempat di mana Anda dapat menyambungkan callback, kata sandi en, dan perilaku pemuatan lainnya. Memisahkannya dari konstruktor `Document` membuat kode dapat digunakan kembali pada banyak file.

---

## Muat Dokumen dan Tangkap Font yang Hilang

Dengan callback terpasang, langkah selanjutnya cukup memuat dokumen.

### Langkah 3: Muat DOCX Anda (atau format lain yang didukung)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Saat konstruktor `Document` mem-parsing file, setiap font yang hilang memicu `FontWarningCollector` kami. Konsol akan menampilkan baris seperti:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Baris itu adalah bukti konkret bahwa **mendeteksi font yang hilang** berhasil.

---

## Verifikasi Output – Apa yang Diharapkan

Jalankan program dari terminal atau Visual Studio. Jika dokumen sumber berisi font yang tidak terpasang di sistem Anda, Anda akan melihat setidaknya satu baris “Font substituted”. Jika dokumen hanya menggunakan font yang terpasang, callback tetap diam dan Anda hanya akan melihat pesan “Document loaded successfully.”  

**Tip**: Untuk memeriksa kembali, buka file Word di Microsoft Word dan lihat daftar font. Font apa pun yang muncul di *Replace Fonts* di bawah grup *Home → Font* adalah kandidat untuk substitusi.

---

## Lanjutan: Mendeteksi Font yang Hilang secara Massal

Seringkali Anda perlu memindai puluhan file. Pola yang sama dapat diskalakan dengan baik:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Karena `FontWarningCollector` menulis ke konsol setiap kali dipanggil, Anda akan mendapatkan laporan per‑file tanpa tambahan kode. Untuk skenario produksi Anda mungkin ingin mencatat ke file atau basis data – cukup ganti `Console.WriteLine` dengan logger pilihan Anda.

---

## Kesalahan Umum & Tips Pro

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| **Tidak ada peringatan muncul** | Dokumen sebenarnya hanya berisi font yang terpasang. | Verifikasi dengan membuka file di Word atau dengan sengaja menghapus sebuah font dari sistem Anda. |
| **Callback tidak dipanggil** | `LoadOptions.WarningCallback` tidak pernah ditetapkan atau instance `LoadOptions` baru digunakan kemudian. | Gunakan satu objek `LoadOptions` dan gunakan kembali untuk setiap pemuatan. |
| **Terlalu banyak peringatan yang tidak terkait** | Anda tidak memfilter berdasarkan `WarningType.FontSubstitution`. | Tambahkan guard `if (info.Type == WarningType.FontSubstitution)` seperti yang ditunjukkan. |
| **Penurunan kinerja pada file besar** | Callback dijalankan pada setiap peringatan, yang dapat banyak untuk dokumen besar. | Nonaktifkan tipe peringatan lain melalui `LoadOptions.WarningCallback` atau set `LoadOptions.LoadFormat` ke tipe spesifik jika Anda mengetahuinya. |

---

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Output konsol yang diharapkan** (ketika font yang hilang ditemukan):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Jika tidak ada substitusi, Anda hanya akan melihat baris keberhasilan.

---

## Kesimpulan

Anda kini memiliki **cara lengkap dan siap produksi untuk mendeteksi font yang hilang** dalam dokumen apa pun yang diproses oleh Aspose.Words. Dengan memanfaatkan **Aspose.Words warning callback** dan mengkonfigurasi **LoadOptions C#**, Anda dapat mencatat setiap substitusi font, memecahkan masalah tata letak, dan memastikan PDF Anda mempertahankan tampilan‑dan‑rasa yang dimaksudkan.  

Dari satu file hingga batch besar, pola tetap sama—implementasikan `IWarningCallback`, sambungkan ke `LoadOptions`, dan biarkan Aspose.Words melakukan pekerjaan berat.  

Siap untuk langkah selanjutnya? Cobalah menggabungkan ini dengan **font embedding** atau **fallback font families** untuk secara otomatis memperbaiki masalah, atau jelajahi API **DocumentVisitor** untuk analisis konten yang lebih mendalam. Selamat coding, dan semoga semua font Anda tetap berada di tempat yang Anda harapkan!

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}