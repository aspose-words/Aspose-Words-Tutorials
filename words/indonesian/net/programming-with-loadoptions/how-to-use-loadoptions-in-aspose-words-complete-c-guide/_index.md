---
category: general
date: 2026-04-10
description: Cara menggunakan LoadOptions di Aspose.Words untuk menangkap peringatan
  substitusi font saat memuat dokumen. Pelajari solusi C# langkah demi langkah dengan
  contoh kode lengkap.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: id
og_description: Cara menggunakan LoadOptions di Aspose.Words untuk menangkap peringatan
  substitusi font saat memuat dokumen. Panduan ini memandu Anda melalui implementasi
  C# lengkap.
og_title: Cara Menggunakan LoadOptions di Aspose.Words – Panduan Lengkap C#
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Cara Menggunakan LoadOptions di Aspose.Words – Panduan Lengkap C#
url: /id/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggunakan LoadOptions di Aspose.Words – Panduan Lengkap C#

Cara menggunakan LoadOptions di Aspose.Words adalah tantangan umum ketika Anda memerlukan kontrol ketat atas pemuatan dokumen. Pada tutorial ini kami akan menunjukkan **cara menggunakan LoadOptions** untuk menangkap peringatan substitusi font dan menanggapinya dalam C#.  

Jika Anda pernah membuka file DOCX yang merujuk pada font yang tidak ada dan bertanya-tanya mengapa hasilnya terlihat aneh, Anda berada di tempat yang tepat. Kami akan membahas seluruh proses, mulai dari membuat instance `LoadOptions` hingga mencetak detail peringatan ke konsol. Pada akhir tutorial Anda akan memiliki potongan kode siap‑jalankan yang dapat Anda sisipkan ke proyek .NET mana pun.

## Apa yang Akan Anda Pelajari

- Mengapa `LoadOptions` penting untuk impor dokumen yang dapat diandalkan.  
- Cara menambahkan **WarningCallback** yang khusus memantau **peringatan substitusi font**.  
- Kode tepat yang diperlukan untuk memuat file Word dengan opsi ini diaktifkan.  
- Tips menangani kasus tepi, seperti dokumen yang berisi banyak font yang hilang.  

Tidak memerlukan dokumentasi eksternal—semua yang Anda butuhkan ada di sini.

## Prasyarat

| Persyaratan | Alasan |
|-------------|--------|
| .NET 6.0 atau lebih baru | Menyediakan runtime untuk sintaks C# 10 yang digunakan dalam contoh. |
| Aspose.Words for .NET (versi terbaru) | Perpustakaan yang menyediakan `LoadOptions` dan infrastruktur peringatan. |
| File DOCX yang mungkin merujuk pada font yang tidak terpasang | Untuk melihat callback peringatan beraksi. |
| Visual Studio 2022 (atau IDE lain pilihan Anda) | Mempermudah debugging dan pengujian. |

Jika Anda sudah memiliki semua ini, bagus—mari kita mulai.

## Langkah 1 – Buat Objek LoadOptions dan Hubungkan WarningCallback

Hal pertama yang Anda lakukan ketika **cara menggunakan LoadOptions** adalah menginstansiasinya. Bagian pentingnya adalah menetapkan delegate ke `WarningCallback`. Delegate ini dipicu setiap kali Aspose.Words menemukan situasi yang ingin diberitahukan—terutama font yang hilang.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Mengapa ini penting:** Tanpa callback, Aspose.Words secara diam‑diam mengganti font yang hilang dengan default, dan Anda mungkin tidak pernah menyadari pergeseran visual tersebut. Dengan mendaftarkan `WarningCallback`, Anda mendapatkan log waktu nyata dari setiap substitusi, yang esensial untuk pipeline dokumen yang terjamin kualitasnya.

## Langkah 2 – Tanggapi Hanya Peringatan Substitusi Font

Anda mungkin bertanya apakah callback akan membanjiri Anda dengan peringatan yang tidak relevan (seperti fitur usang). Jawabannya *ya*—tetapi kita dapat memfilter mereka. Pada potongan kode di atas kami sudah memeriksa `args.WarningType == WarningType.FontSubstitution`. Baris itu adalah penjaga **peringatan substitusi font**, kata kunci sekunder yang menjaga output tetap terfokus.

Jika Anda perlu menangani jenis peringatan lain, cukup tambahkan ke blok `if`:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

Pola ini menunjukkan betapa fleksibelnya mekanisme **warningcallback**, memungkinkan Anda menyesuaikan respons tepat pada skenario yang Anda pedulikan.

## Langkah 3 – Muat Dokumen Anda Menggunakan LoadOptions yang Telah Dikonfigurasi

Setelah listener siap, langkah terakhir adalah meneruskan instance `LoadOptions` ke konstruktor `Document`. Inilah momen di mana **contoh LoadOptions Aspose.Words** benar‑benar bersinar.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**Apa yang akan Anda lihat:** Jika DOCX merujuk pada font yang tidak terpasang di mesin, konsol akan menampilkan baris seperti:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

Output tersebut mengonfirmasi bahwa Anda telah berhasil **cara menggunakan LoadOptions** untuk memantau masalah font.

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

Berikut adalah program lengkap yang dapat Anda kompilasi dan jalankan langsung. Program ini menggabungkan ketiga langkah, menambahkan beberapa sentuhan (seperti banner ramah), dan mendemonstrasikan penanganan error.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### Output yang Diharapkan

Menjalankan program pada mesin yang tidak memiliki font yang dirujuk dalam `input.docx` menghasilkan sesuatu yang mirip dengan:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

Jika semua font tersedia, Anda hanya akan melihat pesan keberhasilan—tidak ada baris peringatan yang muncul.

## Kesalahan Umum & Tips Profesional

- **Kesalahan:** Lupa menetapkan `WarningCallback`. Kode tetap dapat memuat, tetapi Anda akan kehilangan detail substitusi.  
  **Tips profesional:** Selalu tetapkan callback segera setelah membuat `LoadOptions`; biayanya rendah dan memberi manfaat di kemudian hari.

- **Kesalahan:** Menggunakan path relatif yang mengarah ke folder yang salah.  
  **Tips profesional:** Gunakan `Path.Combine(Environment.CurrentDirectory, "input.docx")` untuk pencarian file yang lebih handal.

- **Kesalahan:** Mengira peringatan akan menghentikan proses pemuatan.  
  **Tips profesional:** Peringatan substitusi font bersifat *informasional*; mereka tidak menghentikan pemuatan. Jika Anda memerlukan validasi yang lebih ketat, lemparkan exception di dalam callback ketika terjadi substitusi.

- **Kesalahan:** Menjalankan di server tanpa font terpasang (misalnya image Docker minimal).  
  **Tips profesional:** Pra‑instal font yang diperlukan atau bundel bersama aplikasi Anda, lalu verifikasi dengan callback bahwa tidak ada substitusi yang terjadi di produksi.

## Kapan Menggunakan LoadOptions vs. Pemeriksaan Pasca‑Muat

Anda mungkin bertanya, “Mengapa tidak memeriksa dokumen setelah dimuat?” Jawabannya terletak pada performa dan keakuratan. Dengan menangani peringatan **selama** proses pemuatan, Anda menangkap masalah lebih awal—sebelum perhitungan tata letak atau konversi PDF terjadi. Ini sangat berharga dalam pipeline pemrosesan batch di mana setiap langkah tambahan menambah waktu.

## Memperluas Contoh: Menyimpan Laporan Semua Font yang Disubstitusi

Jika Anda memerlukan catatan permanen (misalnya untuk kepatuhan), ubah callback untuk mengumpulkan pesan ke dalam daftar dan menuliskannya ke file setelah pemuatan:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

Sekarang Anda memiliki umpan balik di konsol serta log yang tahan lama.

## Topik Terkait yang Bisa Anda Jelajahi Selanjutnya

- **Cara menyematkan font khusus di Aspose.Words** – menghilangkan substitusi sepenuhnya.  
- **Menggunakan LoadOptions untuk membatasi ukuran dokumen** – membantu melindungi dari file berukuran besar yang berbahaya.  
- **Mengonversi Word ke PDF dengan tipografi terjaga** – cocok dipadukan dengan pendekatan warning‑callback.  

Masing‑masing topik ini dibangun di atas fondasi yang baru saja Anda buat dengan `LoadOptions`.

## Kesimpulan

Kami telah membahas **cara menggunakan LoadOptions** di Aspose.Words dari awal hingga akhir: membuat opsi, menyambungkan `WarningCallback` yang fokus pada **peringatan substitusi font**, dan memuat dokumen dengan keyakinan. Contoh lengkap dapat dijalankan langsung, dan tips tambahan memastikan Anda menghindari jebakan umum.  

Silakan bereksperimen—ganti callback untuk jenis peringatan lain, log ke basis data, atau integrasikan logika ke layanan web yang memvalidasi file Word yang diunggah. Pola ini fleksibel, dapat diandalkan, dan yang terpenting, memberi Anda visibilitas ke proses substitusi font tersembunyi yang dapat merusak tampilan dokumen Anda.

Selamat coding, semoga dokumen Anda selalu ter-render persis seperti yang diharapkan! 

![Diagram showing the flow of using LoadOptions with a warning callback in Aspose.Words](https://example.com/images/loadoptions-flow.png "How to use LoadOptions diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}