---
category: general
date: 2026-04-21
description: Pelajari cara mendeteksi font, menangkap peringatan, mengonfigurasi callback,
  dan mendaftar peringatan dengan Aspose.Words di C#. Panduan langkah demi langkah
  untuk penanganan font yang andal.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: id
og_description: Bagaimana cara mendeteksi font di Aspose.Words? Tutorial ini menunjukkan
  cara menangkap peringatan, mengonfigurasi callback, dan mendaftar peringatan dalam
  C#.
og_title: Cara Mendeteksi Font di Aspose.Words – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Document Processing
title: Cara Mendeteksi Font di Aspose.Words – Panduan Lengkap
url: /id/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendeteksi Font di Aspose.Words – Panduan Lengkap

Pernah bertanya-tanya **cara mendeteksi font** yang hilang saat Anda memuat dokumen Word? Ini adalah situasi yang muncul lebih sering daripada yang Anda inginkan, terutama ketika berurusan dengan file legacy atau deployment lintas‑platform. Pada tutorial ini kami akan membahas contoh lengkap yang dapat dijalankan, yang **menangkap peringatan**, **mengonfigurasi callback**, dan **mengenumerasi peringatan** sehingga Anda selalu tahu font mana yang diganti.

Kami akan menggunakan Aspose.Words untuk .NET (v24.9 pada saat penulisan) dan C# biasa. Tanpa layanan eksternal, tanpa keajaiban—hanya API dan beberapa baris kode. Pada akhir tutorial Anda akan dapat melihat setiap substitusi font, mencatatnya, dan bahkan memutuskan apakah akan menghentikan proses pemuatan jika font penting tidak tersedia.  

### Apa yang Anda Butuhkan
- **Aspose.Words untuk .NET** (pasang via NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 atau lebih baru (kode ini juga bekerja di .NET Framework)
- Contoh DOCX yang merujuk ke font yang tidak ada di mesin (misalnya “MyCustomFont.ttf”)
- Visual Studio, Rider, atau editor C# apa pun yang Anda sukai

> **Pro tip:** Jika Anda tidak memiliki dokumen dengan font yang hilang, cukup ubah nama file font di sistem Anda atau edit XML DOCX untuk merujuk ke keluarga font yang tidak ada.

---

## Cara Mendeteksi Font dengan Aspose.Words

Ide dasarnya adalah memanfaatkan sistem peringatan Aspose.Words. Ketika perpustakaan tidak dapat menemukan font yang diminta, ia menghasilkan peringatan `WarningType.FontSubstitution`. Dengan menyediakan implementasi `IWarningCallback` khusus, Anda dapat **mendeteksi font** yang diganti selama proses pemuatan.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Mengapa ini berhasil:** Aspose.Words memanggil metode `Warning` untuk setiap masalah non‑kritikal. Dengan menyimpan objek `WarningInfo` Anda mendapatkan akses penuh ke tipe, pesan, dan konteks, yang tepat apa yang Anda butuhkan untuk **mendeteksi font** yang disubstitusi.

---

## Cara Menangkap Peringatan Saat Memuat Dokumen

Setelah kita memiliki kolektor, kita perlu memberi tahu `LoadOptions` untuk menggunakannya. Inilah bagian **cara menangkap peringatan** dari puzzle.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Kasus tepi:** Jika Anda memuat dokumen dari stream (`new Document(stream, loadOptions)`), callback yang sama tetap berfungsi—cukup kirimkan stream alih‑alih jalur file.

Pada titik ini dokumen sudah sepenuhnya dimuat, tetapi semua peringatan substitusi font telah disimpan dengan aman di dalam `warningCollector.Warnings`.

---

## Cara Mengenumerasi Peringatan dan Melaporkan Substitusi Font

Akhirnya, kita menyaring peringatan yang terkumpul dan **mengenumerasi peringatan** yang secara khusus mengenai substitusi font. Langkah ini mengubah data mentah menjadi laporan yang dapat dibaca.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Output yang diharapkan** (contoh):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Jika dokumen tidak mengandung font yang hilang, loop tersebut tidak menghasilkan output apa pun—tidak ada yang perlu dikhawatirkan.

---

## Contoh Lengkap yang Berfungsi (Semua Langkah dalam Satu File)

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke proyek konsol. Program ini menggabungkan **cara mendeteksi font**, **cara menangkap peringatan**, **cara mengonfigurasi callback**, dan **cara mengenumerasi peringatan** dalam alur yang terpadu.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Menjalankan program ini** akan mencetak setiap font yang harus diganti oleh Aspose.Words. Anda dapat mengarahkan output ke file log, memicu peringatan, atau bahkan menghentikan pemuatan jika font penting tidak tersedia.

---

## Pertanyaan Umum & Hal-hal yang Perlu Diwaspadai

### Bagaimana jika saya perlu menghentikan pemuatan ketika font yang dibutuhkan tidak ada?
Anda dapat memeriksa objek `WarningInfo` di dalam callback dan melemparkan pengecualian ketika nama font tertentu muncul. Pengecualian tersebut akan menghentikan proses pemuatan, memberi Anda kontrol penuh.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Apakah ini bekerja dengan PDF atau format lain?
Ya. Aspose.Words menggunakan infrastruktur peringatan yang sama untuk PDF, RTF, dan HTML. Cukup ganti ekstensi file dan sisanya tetap identik.

### Bagaimana saya dapat mencatat peringatan ke file alih‑alih ke konsol?
Ganti `Console.WriteLine` dengan kerangka pencatatan apa pun yang Anda sukai (`Serilog`, `NLog`, dll.). Kelas `WarningInfo` menyediakan `Message`, `Source`, dan `Exception` untuk log yang detail.

### Apakah ini akan memengaruhi performa?
Overheadnya dapat diabaikan—Aspose.Words sudah menghasilkan peringatan secara internal. Menambahkan callback hanya menyimpannya dalam daftar, yang bersifat O(n) terhadap jumlah peringatan. Untuk dokumen tipikal, dampaknya jauh di bawah 1 % dari total waktu pemuatan.

---

## Ringkasan Visual

![How to Detect Fonts in Aspose.Words – warning flow diagram](https://example.com/images/font-detection-diagram.png "how to detect fonts")

*Alt text:* **cara mendeteksi font** – diagram yang menunjukkan langkah callback peringatan, pengumpulan, dan enumerasi.

---

## Penutup

Kami telah membahas **cara mendeteksi font** di Aspose.Words dengan **menangkap peringatan**, **mengonfigurasi callback**, dan **mengenumerasi peringatan**. Contoh kode lengkap menunjukkan pola siap produksi yang dapat Anda masukkan ke aplikasi .NET apa pun.  

Selanjutnya, Anda mungkin ingin menjelajahi:

- **Cara menangkap peringatan** untuk masalah lain (misalnya masalah konversi gambar)
- **Cara mengonfigurasi callback** untuk kerangka pencatatan khusus
- **Cara mengenumerasi peringatan** pada banyak dokumen dalam pekerjaan batch
- Menggunakan **Aspose.Words.Fonts.FontSettings** untuk menyediakan folder font fallback, yang dapat mengurangi jumlah substitusi sejak awal.

Cobalah, sesuaikan kolektor agar cocok dengan gaya pencatatan Anda, dan Anda tidak akan lagi terkejut oleh pertukaran font yang tak terduga. Jika Anda menemukan hal aneh, tinggalkan komentar di bawah—selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}