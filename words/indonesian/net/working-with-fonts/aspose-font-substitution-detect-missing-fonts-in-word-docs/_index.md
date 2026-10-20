---
category: general
date: 2026-05-04
description: Pelajari cara menggunakan substitusi font Aspose untuk mendeteksi font
  yang hilang saat memuat dokumen Word dan mengambil detail font yang hilang—panduan
  langkah demi langkah.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: id
og_description: Menguasai substitusi font Aspose untuk mendeteksi font yang hilang
  saat memuat dokumen Word dan mengambil informasi font yang hilang dengan kode C#
  lengkap.
og_title: Penggantian Font Aspose – Deteksi Font yang Hilang dalam Dokumen Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Penggantian Font Aspose: Deteksi Font yang Hilang pada Dokumen Word'
url: /id/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Deteksi Font yang Hilang dalam Dokumen Word

Pernah bertanya-tanya mengapa dokumen Word terlihat salah di mesin lain? Seringkali penyebabnya adalah font yang hilang, dan **Aspose font substitution** adalah alat yang memungkinkan Anda menemukan celah tersebut sebelum menjadi bencana visual. Dalam tutorial ini kami akan menjelaskan cara **mendeteksi font yang hilang** saat Anda **memuat dokumen Word**, dan kemudian **mengambil detail font yang hilang** sehingga Anda dapat memperbaiki atau menggantinya.

Kami akan membahas semuanya mulai dari menyiapkan warning callback hingga mengambil daftar bersih font yang hilang. Pada akhirnya, Anda akan memiliki potongan kode C# siap‑jalankan yang memberi tahu secara tepat font mana yang tidak tersedia, dan Anda akan memahami mengapa hal ini penting untuk kesetiaan dokumen.

---

## Prasyarat – Apa yang Anda Butuhkan Sebelum Memulai

- **Aspose.Words for .NET** (v23.12 atau lebih baru disarankan).  
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau `dotnet` CLI).  
- Contoh DOCX yang sengaja menggunakan font yang tidak Anda miliki—misalnya `DocumentWithMissingFont.docx`.  
- Pengetahuan dasar C#—tidak perlu hal rumit, cukup kemampuan menjalankan aplikasi console.

Jika ada yang tidak familiar, jeda sejenak dan instal paket NuGet:

```bash
dotnet add package Aspose.Words
```

Itu saja. Tidak ada font tambahan, tidak ada layanan eksternal.

---

## Langkah 1: Muat Dokumen Word (dan Memicu Pemeriksaan Font)

Hal pertama yang Anda lakukan adalah **memuat dokumen Word**. Aspose.Words mem-parsing file dan, jika tidak dapat menemukan font yang dirujuk, ia menambahkan peringatan *FontSubstitution*. Berikut kode yang melakukan pemuatan:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Mengapa ini penting:** Memuat dokumen lebih awal memberi Aspose kesempatan untuk memindai setiap run teks, gaya, dan objek tersemat. Jika sebuah font tidak ditemukan di sistem atau di folder font khusus, Anda akan menerima peringatan nanti.

---

## Langkah 2: Lampirkan Warning Callback untuk Menangkap Peristiwa Substitusi

Aspose.Words menggunakan mekanisme callback untuk memberi tahu Anda tentang masalah seperti font yang hilang. Dengan menetapkan implementasi `IWarningCallback` ke `doc.WarningCallback`, Anda dapat menangkap setiap peringatan saat terjadi.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Pro tip:** Anda dapat melampirkan beberapa callback (mis., logging, pembaruan UI) dengan membungkusnya dalam pola komposit, tetapi untuk tutorial ini satu callback saja sudah cukup jelas.

---

## Langkah 3: Implementasikan Font Substitution Warning Callback

Sekarang kita mendefinisikan kelas yang benar‑benarnya melakukan pekerjaan. Callback menerima objek `WarningInfo`; kita menyaring untuk `WarningType.FontSubstitution` dan menyimpan deskripsinya untuk penggunaan selanjutnya.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Apa yang terjadi:** Ketika Aspose menemukan font yang hilang, ia membuat peringatan seperti “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Callback kami mencetak baris itu dan menyimpannya.

---

## Langkah 4: Proses Dokumen (Opsional) dan Kumpulkan Font yang Hilang

Jika Anda hanya perlu **mendeteksi font yang hilang**, langkah pemuatan sudah cukup—peringatan akan muncul secara otomatis. Namun, banyak pengembang juga perlu **mengambil informasi font yang hilang** setelah melakukan beberapa operasi (mis., menyimpan, mengonversi). Di bawah ini kami memaksa operasi kecil—menyimpan ke PDF—untuk memastikan semua peringatan dikeluarkan, lalu kami mengambil pesan yang terkumpul.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Output console yang diharapkan** (contoh):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Perhatikan bagaimana setiap baris dengan jelas menyatakan font asli dan fallback yang dipilih Aspose. Itulah inti pelaporan **aspose font substitution**.

---

## Langkah 5: Lanjutan – Menggunakan Sumber Font Kustom untuk Mengurangi Substitusi

Kadang‑kadang Anda *memiliki* font yang hilang, hanya saja tidak berada di folder sistem default. Aspose.Words memungkinkan Anda menunjuk ke direktori kustom melalui `FontSettings`. Menambahkan langkah ini dapat secara dramatis mengurangi jumlah peringatan substitusi.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Mengapa menambahkan ini?** Jika Anda mendistribusikan dokumen ke berbagai mesin, menyertakan font yang diperlukan dalam folder yang diketahui memastikan tampilan visual yang sama di mana pun. Ini juga membuat rutinitas **deteksi font yang hilang** Anda lebih akurat karena Aspose memeriksa folder tersebut sebelum melakukan fallback.

---

## Contoh Kerja Lengkap

Menggabungkan semuanya, berikut program console siap‑salin‑tempel. Simpan sebagai `Program.cs` dan jalankan dengan `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Apa yang akan Anda lihat:** Jika DOCX sumber merujuk pada font yang tidak Anda miliki, console akan mencetak setiap baris substitusi diikuti oleh ringkasan singkat. Jika semua font tersedia, Anda akan mendapatkan pesan “No missing fonts were detected.”.

---

## Kesalahan Umum & Cara Menghindarinya

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| **Tidak ada peringatan muncul** | Dokumen hanya menggunakan font sistem, atau Anda sudah menambahkan folder kustom yang berisi font yang hilang. | Verifikasi bahwa DOCX benar‑benar merujuk pada font yang tidak tersedia. Anda dapat membukanya di Word dan mengubah sebuah paragraf ke font yang jarang (mis., “Papyrus”). |
| **Pesan duplikat** | Font yang sama digunakan dalam beberapa run, menyebabkan beberapa peringatan. | Hilangkan duplikat pada daftar dengan `Distinct()` jika Anda hanya membutuhkan satu set unik. |
| **Penurunan performa pada dokumen besar** | Setiap peringatan diproses pada thread UI. | Jalankan pemuatan dalam tugas latar belakang atau gunakan `Parallel.ForEach` untuk pemrosesan lanjutan. |
| **Font fallback yang salah** | fallback default Aspose mungkin tidak cocok dengan merek Anda. | Setel `FontSettings.SubstitutionSettings.DefaultFontName` ke fallback yang diinginkan (mis., “Calibri”). |

---

## Memperluas Solusi – Mengekspor Font yang Hilang ke JSON

Jika Anda membangun layanan web yang perlu melaporkan font yang hilang kembali ke klien, serialisasi daftar tersebut sangat mudah:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Sekarang API Anda dapat mengembalikan payload JSON bersih yang dapat dikonsumsi sistem lain.

---

## Kesimpulan

Dalam panduan ini kami mendemonstrasikan **Aspose font substitution** dari awal hingga akhir: memuat dokumen Word, melampirkan warning callback, menangkap setiap peristiwa *deteksi font yang hilang*, dan akhirnya **mengambil informasi font yang hilang** untuk pelaporan atau perbaikan. Dengan menambahkan folder font kustom opsional Anda dapat mengurangi daftar substitusi, dan dengan beberapa baris tambahan Anda bahkan dapat mengekspor hasilnya sebagai JSON.

Ingat, integritas visual dokumen Anda bergantung pada font yang digunakan. Dengan teknik yang ditunjukkan di sini, Anda tidak akan lagi terkejut oleh fallback yang tidak terduga.  

Siap melangkah ke tahap berikutnya? Cobalah mengintegrasikan logika ini ke dalam pipeline pemrosesan dokumen yang lebih besar, atau jelajahi fitur Aspose.Words lainnya seperti embedding font (`doc.FontSettings.EmbeddedFonts`). Kemungkinannya tak terbatas, dan pengguna Anda akan berterima kasih atas output yang rapi.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}