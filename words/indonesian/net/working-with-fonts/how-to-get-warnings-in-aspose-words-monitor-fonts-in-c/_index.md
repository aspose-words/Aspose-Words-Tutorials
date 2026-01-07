---
category: general
date: 2026-01-06
description: Pelajari cara mendapatkan peringatan saat memuat dokumen dan cara memantau
  font menggunakan Aspose.Words. Panduan ini mencakup callback peringatan dan pelacakan
  substitusi font.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: id
og_description: Bagaimana cara mendapatkan peringatan di Aspose.Words? Ikuti tutorial
  langkah demi langkah ini untuk memantau font dan menangkap pesan substitusi saat
  memuat dokumen.
og_title: Cara Mendapatkan Peringatan di Aspose.Words – Memantau Font
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Cara Mendapatkan Peringatan di Aspose.Words – Memantau Font di C#
url: /id/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendapatkan Peringatan di Aspose.Words – Memantau Font di C#

Pernah bertanya-tanya **bagaimana cara mendapatkan peringatan** ketika dokumen Word berisi font yang tidak Anda miliki terpasang? Ini adalah masalah umum—aplikasi Anda secara diam-diam mengganti font yang hilang, dan Anda tidak pernah tahu apa yang berubah. Kabar baiknya, Anda dapat mengaitkan ke sistem peringatan Aspose.Words dan **memantau font** secara real time.

Dalam tutorial ini kami akan menunjukkan secara tepat cara menangkap peringatan substitusi font tersebut, mengapa hal itu penting, dan apa yang harus dilakukan dengan informasi tersebut setelah Anda memilikinya. Tanpa dokumen eksternal, hanya contoh lengkap yang dapat dijalankan yang dapat Anda tempel ke Visual Studio sekarang.

> **Pro tip:** Jika Anda membangun pipeline konversi dokumen, mencatat font yang hilang sejak awal menyelamatkan Anda dari kejutan tata letak yang tidak menyenangkan di kemudian hari.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi terbaru; API belum berubah sejak v23.10)
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code dengan ekstensi C#)
- Contoh file `.docx` yang merujuk pada font yang tidak terpasang di sistem Anda (misalnya **“NonExistentFont”**)

Itu saja—tidak ada paket NuGet tambahan selain Aspose.Words.

## Langkah 1 – Menyiapkan Pengumpul Peringatan (Primary Keyword in Header)

Hal pertama yang Anda butuhkan adalah tempat untuk menyimpan peringatan saat terjadi. Aspose.Words menyediakan properti `WarningCallback` pada `LoadOptions` untuk tujuan ini.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Mengapa ini penting:**  
Ketika perpustakaan menemukan font yang hilang, ia tidak melemparkan pengecualian; ia menghasilkan objek `WarningInfo`. Dengan menghubungkan pengumpul, Anda mendapatkan visibilitas penuh pada setiap peristiwa substitusi, memungkinkan Anda **memantau font** tanpa mencemari konsol dengan pesan yang tidak relevan.

## Langkah 2 – Memuat Dokumen dengan Opsi Peringatan yang Diaktifkan

Sekarang kita benar-benar membaca file. `LoadOptions` yang kami siapkan pada langkah sebelumnya memastikan bahwa semua peringatan terkait font ditangkap.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Apa yang terjadi di balik layar?**  
Aspose.Words mengurai file Word, menyelesaikan font, dan setiap kali tidak dapat menemukan font yang diminta, ia beralih ke font pengganti (biasanya Arial). Penggantian ini memicu peringatan `WarningType.FontSubstitution`, yang masuk ke `warningCollector`.

## Langkah 3 – Memeriksa Peringatan yang Dikumpulkan (Primary Keyword Appears Again)

Setelah dokumen dimuat, kami cukup mengiterasi `warningCollector` dan mencetak semua pesan substitusi font.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Output yang diharapkan** (asumsi font yang hilang adalah *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Jika dokumen berisi beberapa font yang tidak dikenal, Anda akan melihat satu baris per substitusi—sempurna untuk pencatatan atau peringatan.

## Langkah 4 – Opsional: Mencatat atau Menyimpan Informasi Peringatan

Dalam produksi Anda mungkin menginginkan lebih dari sekadar `Console.WriteLine`. Berikut contoh singkat yang menulis peringatan ke file JSON untuk analisis selanjutnya.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Sekarang Anda memiliki catatan permanen yang dapat Anda masukkan ke dasbor pemantauan, atau bahkan memicu permintaan otomatis untuk file font yang hilang.

## Langkah 5 – Verifikasi Hasil dan Bersihkan

Jalankan program. Jika Anda melihat pesan substitusi, Anda telah berhasil **mendapatkan peringatan** dan kini aktif **memantau font**. Jika tidak ada yang muncul, periksa kembali bahwa dokumen uji benar‑benar merujuk pada font yang tidak terpasang di mesin.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Jumlah nol biasanya berarti salah satu dari:

1. Semua font berhasil diselesaikan (mungkin font *sudah* terpasang secara lokal), atau
2. Dokumen tidak berisi referensi font yang memerlukan substitusi.

## Kesalahan Umum & Cara Menghindarinya

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **Tidak ada peringatan muncul** | Font sebenarnya ada di sistem, atau dokumen hanya menggunakan font bawaan. | Ubah nama font di file sumber menjadi sesuatu yang tidak mungkin (misalnya `XYZ123`) dan coba lagi. |
| **Terlalu banyak peringatan (noise)** | Anda memuat banyak dokumen dalam loop tanpa membersihkan pengumpul. | Buat ulang `WarningInfoCollection` untuk setiap dokumen, atau panggil `warningCollector.Clear()` setelah memproses. |
| **Dampak kinerja** | Pencatatan berlebihan ke disk dapat memperlambat pemrosesan batch. | Buffer peringatan di memori dan tulis secara massal, atau gunakan I/O file asynchronous. |
| **Kehilangan `using Aspose.Words.Loading;`** | Kelas `LoadOptions` berada di namespace ini. | Tambahkan direktif `using` yang hilang, seperti yang ditunjukkan pada Langkah 1. |

## Memperluas Solusi – Memantau Jenis Peringatan Lain

Meskipun substitusi font adalah yang paling terlihat, Aspose.Words dapat menghasilkan peringatan untuk:

- **Fitur usang** (`WarningType.Deprecated`),
- **Potensi kehilangan data** (`WarningType.DataLoss`),
- **Format file yang tidak didukung** (`WarningType.UnsupportedFileFormat`).

Anda dapat memperluas filter pada Langkah 3 untuk menangkap ini juga:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Dengan begitu Anda tidak hanya **memantau font**, tetapi juga **mendapatkan peringatan** untuk skenario apa pun yang mungkin dihadapi aplikasi Anda.

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Jalankan:** Bangun proyek, eksekusi, dan Anda akan melihat peringatan dicetak dan disimpan. Itu adalah jawaban lengkap untuk **cara mendapatkan peringatan** dan **cara memantau font** dengan Aspose.Words.

## Kesimpulan

Anda sekarang tahu **cara mendapatkan peringatan** dari Aspose.Words, khususnya untuk skenario substitusi font, dan Anda telah belajar **cara memantau font** selama proses pemuatan dokumen. Dengan melampirkan `WarningCallback`, mengiterasi objek `WarningInfo` yang dikumpulkan, dan secara opsional menyimpan data, Anda memperoleh transparansi penuh atas peristiwa font yang hilang—kemampuan penting untuk setiap pipeline pemrosesan dokumen.

Langkah selanjutnya? Coba memperluas filter peringatan untuk mencakup peringatan kehilangan data atau fitur usang, atau integrasikan log JSON ke dasbor pemantauan seperti Grafana. Pola yang sama berlaku untuk semua jenis peringatan, sehingga Anda akan siap memantau setiap masalah yang dilemparkan Aspose.Words.

Selamat coding, dan semoga dokumen Anda selalu ditampilkan persis seperti yang Anda harapkan!

<img src="font-warnings.png" alt="cara mendapatkan peringatan di Aspose.Words" style="max-width:100%;">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}