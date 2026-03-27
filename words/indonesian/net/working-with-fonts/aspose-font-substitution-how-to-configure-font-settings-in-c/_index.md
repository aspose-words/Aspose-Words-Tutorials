---
category: general
date: 2026-03-27
description: 'Penggantian Font Aspose menjadi mudah: pelajari cara mengonfigurasi
  pengaturan font, menangkap peringatan, dan menangani font yang hilang dalam aplikasi
  .NET Anda.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: id
og_description: Kuasai Penggantian Font Aspose dengan mengonfigurasi pengaturan font
  dan menangani font yang hilang menggunakan callback peringatan. Panduan lengkap
  C#.
og_title: Penggantian Font Aspose – Konfigurasikan Pengaturan Font di C#
tags:
- Aspose.Words
- C#
- Font Management
title: Penggantian Font Aspose – Cara Mengonfigurasi Pengaturan Font di C#
url: /id/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Panduan Lengkap untuk Mengonfigurasi Pengaturan Font

Pernah menemukan dokumen yang tiba‑tiba mengganti jenis huruf khusus Anda dengan sesuatu yang generik? Itu **aspose font substitution** yang melakukan tugasnya—mengganti font yang hilang dengan kecocokan terdekat yang dapat ditemukan. Ini berguna, tetapi jika Anda perlu mengetahui *tepat* font mana yang diganti, Anda harus memanfaatkan sistem peringatan library dan mengonfigurasi pengaturan font sendiri.

Dalam tutorial ini kami akan membahas skenario dunia nyata: memuat DOCX yang merujuk pada font yang tidak Anda miliki, menangkap peristiwa substitusi, dan mencetak pesan ramah ke konsol. Pada akhir tutorial Anda akan nyaman dengan **configure font settings**, menyiapkan **Aspose.Words warning callback**, dan memperluas contoh untuk cocok dengan alur kerja apa pun.

> **Apa yang Anda perlukan**  
> • .NET 6+ (or .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (latest NuGet)  
> • A DOCX that references a missing font (we’ll call it `MissingFont.docx`)  

Mari kita mulai.

---

## Langkah 1: Instal Aspose.Words dan Siapkan Proyek

Sebelum kita menulis kode apa pun, pastikan paket Aspose.Words sudah direferensikan:

```bash
dotnet add package Aspose.Words
```

> **Tip Pro:** Gunakan versi stabil terbaru; per Maret 2026 versi terbarunya adalah 23.11.0. Rilis yang lebih baru meningkatkan algoritma pencocokan font dan menambahkan tipe peringatan tambahan.

Buat aplikasi konsol baru (atau masukkan kode ke dalam proyek yang sudah ada) dan tambahkan direktif `using` yang biasa:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Namespace ini memberi kita akses ke `Document`, `LoadOptions`, dan kelas‑kelas terkait font yang akan kita butuhkan.

## Langkah 2: Konfigurasikan Pengaturan Font dengan LoadOptions

Inti kontrol **aspose font substitution** berada di `LoadOptions.FontSettings`. Dengan menyediakan objek `FontSettings` kosong, kita memberi tahu Aspose untuk menggunakan jalur pencarian default *dan* melaporkan setiap substitusi melalui callback peringatan.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Mengapa tidak hanya mengandalkan default? Karena menempelkan callback peringatan (langkah berikutnya) hanya berfungsi ketika properti `FontSettings` tidak null. Baris kecil ini memberi kita kait ke proses substitusi tanpa mengubah perilaku pencarian font sebenarnya.

## Langkah 3: Lampirkan Callback Peringatan untuk Menangkap Substitusi

Aspose.Words mengimplementasikan antarmuka `IWarningCallback`. Setiap kali terjadi sesuatu yang penting—seperti font yang hilang—ia memanggil metode `Warning` kami. Kami akan mengimplementasikan handler kecil yang menyaring `WarningType.FontSubstitution` dan mencetak deskripsinya.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

Dan inilah handlernya sendiri:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Mengapa ini penting** – Tanpa callback, Aspose secara diam‑diam mengganti font, dan Anda tidak pernah tahu font mana yang digunakan. Callback membuat proses menjadi transparan, yang penting untuk pelaporan kepatuhan atau debugging masalah tata letak.

## Langkah 4: Muat Dokumen Menggunakan Opsi yang Dikonfigurasi

Sekarang kita akhirnya memuat dokumen, dengan melewatkan `loadOptions` yang baru saja kita siapkan. Jika file sumber merujuk pada font yang tidak terpasang, handler kami akan dipanggil.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Ganti `YOUR_DIRECTORY` dengan jalur sebenarnya tempat `MissingFont.docx` berada. Saat Anda menjalankan program, Anda akan melihat output serupa dengan:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Baris itu memberi tahu Anda secara tepat font mana yang hilang dan fallback mana yang dipilih Aspose.

## Langkah 5: (Opsional) Sesuaikan Jalur Pencarian Font

Jika Anda memiliki folder pribadi dengan font perusahaan, Anda dapat memberi tahu Aspose ke mana harus mencari sebelum kembali ke font sistem. Ini adalah penggunaan lanjutan dari **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Menetapkan `recursive: true` membuat Aspose memindai subfolder juga. Sekarang perpustakaan akan mencoba font pribadi Anda terlebih dahulu, mengurangi kemungkinan substitusi yang tidak diinginkan.

## Contoh Kerja Lengkap

Menggabungkan semuanya, berikut program lengkap yang siap dijalankan:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Output yang diharapkan** (ketika font yang hilang ditemukan):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Jika semua font ada, program berjalan diam‑diam (tanpa peringatan) dan tetap menghasilkan PDF.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya perlu *mencegah* substitusi sama sekali?

Setel `FontSettings.SubstitutionSettings` ke `null` atau gunakan `FontSettings.FontSubstitutionSettings` untuk mengontrol perilaku. Misalnya:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Sekarang Aspose akan melemparkan pengecualian alih‑alih mengganti secara diam‑diam, yang dapat ditangkap dan ditangani.

### Apakah ini bekerja dengan format file lain (mis., .doc, .rtf)?

Tentu saja. Objek `LoadOptions` yang sama dapat diteruskan ke konstruktor `Document` mana pun yang menerima jalur file. Callback peringatan akan dipanggil untuk semua format yang bergantung pada font.

### Bisakah saya menangkap nama font fallback yang *tepat*?

Ya. String `info.Description` berisi kedua font yang hilang dan penggantinya. Jika Anda memerlukan nama secara programatik, Anda dapat mem‑parse atau menggunakan objek `FontInfo` (tersedia di versi yang lebih baru).

### Bagaimana perilakunya dalam lingkungan multi‑thread?

`FontSettings` **tidak** thread‑safe. Buat `LoadOptions` terpisah (dengan `FontSettings` masing‑masing) per thread, atau lindungi akses dengan lock.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk menguasai **aspose font substitution** dan **configure font settings** dalam aplikasi C#:

1. Instal Aspose.Words dan tambahkan pernyataan `using` yang diperlukan.  
2. Buat objek `LoadOptions` dengan `FontSettings` baru.  
3. Lampirkan `IWarningCallback` khusus untuk menampilkan peristiwa substitusi.  
4. Muat dokumen, biarkan callback melaporkan font yang hilang.  
5. (Opsional) Perluas jalur pencarian atau nonaktifkan substitusi sepenuhnya.

Dengan pola ini Anda dapat mencatat font yang hilang untuk kepatuhan, memberi peringatan kepada pengguna di UI, atau secara otomatis menyematkan font fallback sebelum publikasi. Selanjutnya, Anda dapat menjelajahi **Aspose.Words font substitution policies** atau mengintegrasikan alur kerja ke dalam pipeline pemrosesan dokumen yang lebih besar.

Selamat coding, dan semoga dokumen Anda selalu ditampilkan dengan jenis huruf yang tepat!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}