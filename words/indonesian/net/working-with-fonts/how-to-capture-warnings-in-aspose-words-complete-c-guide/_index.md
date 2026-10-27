---
category: general
date: 2026-03-28
description: Cara menangkap peringatan saat memuat DOCX dengan Aspose.Words dan mendapatkan
  pesan peringatan untuk font yang hilang. Pelajari cara menangani font yang hilang
  secara efisien.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: id
og_description: Cara menangkap peringatan saat memuat DOCX dengan Aspose.Words, mendapatkan
  pesan peringatan, dan menangani font yang hilang dengan contoh kode praktis.
og_title: Cara Menangkap Peringatan di Aspose.Words – Panduan Lengkap C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Cara Menangkap Peringatan di Aspose.Words – Panduan Lengkap C#
url: /id/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menangkap Peringatan di Aspose.Words – Panduan Lengkap C#

Pernah bertanya-tanya **bagaimana cara menangkap peringatan** yang muncul saat Anda memuat dokumen Word dengan Aspose.Words? Mungkin Anda melihat perubahan font yang aneh dan perlu mengetahui persis alasannya. Singkatnya, Anda dapat mengaitkan ke sistem peringatan perpustakaan, **mendapatkan pesan peringatan**, dan bahkan **menangani font yang hilang** sebelum mereka merusak tata letak Anda.  

Dalam tutorial ini kami akan membahas skenario dunia nyata: memuat sebuah DOCX, mengumpulkan setiap peringatan yang dikeluarkan mesin, dan mencetak rincian tentang substitusi font apa pun yang terjadi. Pada akhir tutorial Anda akan memiliki contoh kode siap‑jalankan, memahami “mengapa” di balik setiap langkah, dan mengetahui cara memperluas pendekatan ini untuk proyek Anda sendiri.

## Apa yang Akan Anda Pelajari

- Cara mengonfigurasi `LoadOptions` sehingga peringatan ditangkap secara otomatis.  
- Cara **mengambil pesan peringatan** dari `WarningInfoCollection`.  
- Bagaimana mengidentifikasi dan merespons **font yang hilang** melalui flag `WarningType.FontSubstitution`.  
- Tips untuk memecahkan masalah kasus tepi, seperti dokumen dengan font tersemat atau folder font khusus.  

Tidak memerlukan referensi eksternal – semua yang Anda butuhkan ada di sini.

---

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi pada .NET Framework 4.7+).  
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`).  
- Sebuah contoh DOCX (`input.docx`) yang tidak memiliki beberapa font atau menggunakan font yang tidak terpasang di mesin Anda.  

Itu saja. Jika Anda sudah nyaman dengan C# dan Visual Studio, Anda dapat menyalin‑tempel kode dan menjalankannya langsung.

---

## Langkah 1: Siapkan Load Options dan Callback Peringatan

Hal pertama yang dilakukan Aspose.Words ketika Anda memanggil `new Document(path, loadOptions)` adalah mem-parsing file. Selama parsing ia dapat menemukan font yang hilang, fitur yang tidak didukung, atau markup yang sudah usang. Untuk menangkap peristiwa‑peristiwa tersebut Anda memerlukan objek **callback peringatan**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Mengapa ini penting:** Tanpa callback, Aspose.Words secara diam‑diam mencatat peringatan ke konsol (atau mengabaikannya), membuat Anda tidak menyadari substitusi font yang dapat memengaruhi tata letak. Dengan menyediakan `WarningInfoCollection` khusus, Anda mendapatkan visibilitas penuh.

> **Pro tip:** Jika Anda hanya peduli pada peringatan terkait font, Anda dapat memfilter nanti – tetapi mengumpulkan *semua* peringatan memberi Anda jaring pengaman untuk masalah di masa depan.

---

## Langkah 2: Muat Dokumen dengan Opsi yang Sudah Dikonfigurasi

Setelah callback siap, muat file tersebut. Konstruktor `Document` secara otomatis akan memanggil callback untuk setiap masalah yang ditemukannya.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Apa yang terjadi di balik layar?** Aspose.Words mem-parsing Open XML, menyelesaikan gaya, dan berusaha memetakan setiap referensi font ke font yang terpasang di sistem. Jika tidak ditemukan padanan, ia membuat entri `WarningInfo` dengan tipe `FontSubstitution`.

---

## Langkah 3: Ambil dan Periksa Peringatan yang Dikumpulkan

Setelah proses pemuatan selesai, `warningCollector` Anda kini berisi setiap peringatan yang terjadi. Mari kita ambil dan fokus pada pesan substitusi font.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Contoh output** (konsol Anda mungkin menampilkan sesuatu seperti):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Jika Anda ingin *semua* peringatan, cukup hapus pengecekan `if` atau log `warning.Type` untuk setiap entri.

---

## Langkah 4: Menangani Font yang Hilang – Lebih dari Sekadar Logging

Menangkap peringatan memang berguna, tetapi seringkali Anda perlu **menangani font yang hilang** secara programatik. Berikut dua strategi umum:

### 4.1 Ganti Font yang Hilang dengan Fallback Khusus

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Sekarang setiap font yang hilang akan diganti dengan *Calibri* alih‑alih fallback default perpustakaan.

### 4.2 Sematkan Font Pengganti Secara Dinamis

Jika Anda memiliki file font khusus (misalnya `MyFallback.ttf`) Anda dapat mendaftarkannya pada waktu berjalan:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Pendekatan ini berguna ketika Anda mendistribusikan font korporat tertentu bersama aplikasi Anda.

> **Kasus tepi:** Dokumen yang sudah menyematkan font yang diperlukan akan mengabaikan aturan substitusi sistem. Dalam skenario itu, koleksi peringatan akan kosong untuk font tersebut, yang justru merupakan hasil yang Anda inginkan.

---

## Langkah 5: Contoh Lengkap yang Siap Pakai (Copy‑Paste)

Berikut adalah program mandiri yang mendemonstrasikan semuanya dari awal hingga akhir. Ganti saja `YOUR_DIRECTORY/input.docx` dengan jalur ke file uji Anda.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Apa yang diharapkan**

- Konsol mencetak setiap peringatan substitusi font, diawali dengan emoji peringatan untuk visibilitas.  
- Dokumen output DOCX (`output.docx`) menggunakan *Calibri* di mana pun font yang hilang terdeteksi.  
- Tidak ada pengecualian yang tidak tertangani – sistem peringatan menangani font yang tidak dikenal dengan elegan.

---

## Pertanyaan Umum & Jawaban

**T: Apakah ini akan bekerja dengan PDF yang dihasilkan dari Word?**  
J: Ya. Aspose.Words memperlakukan PDF sebagai format output lain. Penangkapan peringatan terjadi selama fase *load*, sehingga independen dari proses ekspor akhir.

**T: Bagaimana jika saya perlu menangkap peringatan untuk **semua** operasi dokumen (save, convert, dll.)?**  
J: Anda dapat menggunakan kembali `WarningInfoCollection` yang sama dengan menetapkannya ke `Document.WarningCallback` setelah dokumen diinstansiasi. Setiap operasi selanjutnya akan menambahkan entri baru ke koleksi yang sama.

**T: Apakah callback peringatan memengaruhi kinerja?**  
J: Sangat sedikit. Koleksi hanya menyimpan objek; kecuali Anda memproses ribuan peringatan dalam loop ketat, Anda tidak akan merasakan penurunan kecepatan.

**T: Bagaimana cara menekan peringatan yang tidak saya pedulikan?**  
J: Implementasikan kelas kustom yang mewarisi `IWarningCallback` dan lakukan penyaringan di dalam metode `Warning`. `WarningInfoCollection` bawaan hanya menyimpan, tidak menyaring.

---

## Pro Tips & Pitfalls

- **Pro tip:** Selalu periksa `Warning.Description` – di sana terdapat nama font yang tepat yang hilang. Ini dapat membantu Anda memutuskan apakah akan menyertakan font tersebut dalam aplikasi Anda.  
- **Waspadai font yang tersemat:** Jika DOCX sumber sudah menyematkan font yang diperlukan, Aspose.Words tidak akan mengeluarkan peringatan substitusi, bahkan jika font tersebut tidak terpasang secara lokal.  
- **Keamanan thread:** `WarningInfoCollection` tidak thread‑safe. Jika Anda memuat banyak dokumen secara bersamaan, berikan setiap thread koleksi masing‑masing.  
- **Pemeriksaan versi:** API peringatan telah stabil sejak Aspose.Words 20.8. Pastikan Anda menggunakan versi terbaru agar tidak melewatkan tipe peringatan yang lebih baru.

---

## Kesimpulan

Kami telah membahas **cara menangkap peringatan** dari Aspose.Words, mendemonstrasikan cara **mengambil pesan peringatan**, dan menunjukkan cara praktis **menangani font yang hilang** melalui font fallback atau folder font khusus. Contoh lengkap siap disisipkan ke proyek .NET mana pun, dan konsepnya dapat diskalakan ke pipeline otomasi yang lebih besar.

Selanjutnya, Anda dapat menjelajahi:

- Menggunakan `Document.WarningCallback` untuk menangkap peringatan selama operasi **save**.  
- Mencatat peringatan ke file atau sistem telemetri untuk pemantauan produksi.  
- Memperluas callback untuk secara otomatis mengganti font yang hilang dengan tipografi khusus merek.

Silakan bereksperimen—ganti font fallback, tambahkan lebih banyak dokumen ke batch, atau integrasikan pengumpul peringatan ke dalam pipeline CI yang menandai regresi terkait font. Selamat coding, semoga dokumen Anda selalu tampil persis seperti yang Anda harapkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}