---
category: general
date: 2026-03-19
description: Pelajari cara menangkap peringatan di Aspose.Words, mengatur pengaturan
  font default, dan mendeteksi font yang hilang saat memuat dokumen Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: id
og_description: Cara menangkap peringatan di Aspose.Words, mengatur pengaturan font
  default, dan mendeteksi font yang hilang saat memuat dokumen Word.
og_title: Cara Menangkap Peringatan – Atur Pengaturan Font Default
tags:
- Aspose.Words
- C#
- Document Processing
title: Cara Menangkap Peringatan – Atur Pengaturan Font Default
url: /id/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menangkap Peringatan – Mengatur Pengaturan Font Default

**How to capture warnings** adalah kebutuhan umum ketika Anda bekerja dengan Aspose.Words, terutama jika dokumen Anda bergantung pada font tertentu yang mungkin tidak ada di mesin target. Pernah membuka sebuah DOCX dan bertanya-tanya mengapa tata letaknya terlihat aneh? Jawabannya sering tersembunyi dalam peringatan tentang font yang hilang.  

Dalam panduan ini kami akan menjelaskan **how to capture warnings** saat Anda **load word document**, mengonfigurasi **set default font settings**, dan akhirnya **detect missing fonts** sehingga Anda dapat merespons secara programatis. Tanpa basa‑basi—hanya contoh lengkap yang dapat dijalankan dan penjelasan di balik setiap baris.

> *Pro tip:* Menangkap peringatan lebih awal menyelamatkan Anda dari debugging gangguan tata letak yang misterius nanti.

---

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi terbaru per 2026).  
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code).  
- Contoh DOCX yang merujuk ke font yang *tidak* Anda miliki (misalnya *Comic Sans MS* pada mesin Linux).  

Itu saja. Tidak ada paket NuGet tambahan yang diperlukan selain Aspose.Words.

---

## Langkah 1 – Memahami Mengapa Anda Perlu Menangkap Peringatan

Saat Aspose.Words mengurai sebuah dokumen, ia mungkin menemukan font yang tidak tersedia di host. Secara default perpustakaan ini secara diam-diam mengganti dengan font cadangan, yang dapat mengubah pemenggalan baris, spasi, bahkan menyebabkan teks menghilang.  

Menggunakan **WarningCallback** bersama dengan objek **FontSettings** memberi Anda dua hal:

1. **Visibility** – Anda mendapatkan entri `WarningInfo` untuk setiap substitusi.  
2. **Control** – Anda dapat mengonfigurasi sebelumnya font default untuk meminimalkan kejutan visual.

Anggaplah ini seperti memasang “watchdog” yang berteriak setiap kali mesin menukar komponen di dalamnya.

---

## Langkah 2 – Mengatur Pengaturan Font Default

Keyword sekunder pertama, **set default font settings**, muncul di sini. Anda membuat sebuah instance `FontSettings` dan secara opsional menunjuk ke folder yang berisi font cadangan Anda.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Why?**  
> Jika Anda tidak menentukan fallback, Aspose.Words memilih font sistem pertama yang cocok dengan gaya, yang mungkin sangat berbeda. Dengan mengatur default yang diketahui, Anda menjamin rendering yang konsisten di semua mesin.

---

## Langkah 3 – Menyiapkan Warning Callback untuk Menangkap Peringatan

Sekarang kami akan **how to capture warnings** dengan melampirkan `WarningInfoCollection` ke opsi pemuatan. Koleksi ini akan menyimpan setiap peringatan yang dihasilkan selama proses pemuatan.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` mengimplementasikan `IWarningCallback`, sehingga Aspose.Words secara otomatis menyalurkan setiap peringatan ke `warningInfos`. Tidak diperlukan polling.

---

## Langkah 4 – Memuat Dokumen Word dengan Opsi yang Dikonfigurasi

Di sinilah keyword sekunder kedua, **load word document**, bersinar. Kami melewatkan baik `FontSettings` maupun `WarningCallback` melalui sebuah instance `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Jika dokumen merujuk ke font yang tidak terpasang, warning callback akan menangkap entri `WarningType.FontSubstitution`.

---

## Langkah 5 – Mendeteksi Font yang Hilang dari Peringatan yang Dikumpulkan

Akhirnya, kami menjawab keyword sekunder ketiga, **detect missing fonts**, dengan mengiterasi peringatan yang terkumpul.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Output tipikal terlihat seperti:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Baris itu memberi tahu Anda secara tepat font mana yang hilang dan fallback mana yang digunakan—informasi yang dapat Anda log, tampilkan kepada pengguna, atau bahkan memicu rutinitas pemasangan font khusus.

---

## Contoh Lengkap yang Dapat Dijalankan

Di bawah ini adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mendemonstrasikan **how to capture warnings**, **set default font settings**, **load word document**, dan **detect missing fonts** semuanya dalam satu alur.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Expected result:** Ketika DOCX yang ditentukan merujuk ke font yang tidak terpasang, konsol mencetak peringatan untuk setiap substitusi. Jika semua font hadir, loop tidak menghasilkan output.

---

## Kesalahan Umum & Kasus Tepi

| Situasi | Mengapa Terjadi | Cara Menangani |
|-----------|----------------|------------------|
| **No warnings appear** even though the layout looks wrong | Dokumen mungkin menggunakan font *embedded*, yang dirender oleh Aspose.Words tanpa substitusi. | Periksa `Document.HasEmbeddedFonts` dan pertimbangkan mengekstrak font embedded jika Anda membutuhkannya di mesin lain. |
| **Multiple warnings for the

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}