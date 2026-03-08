---
category: general
date: 2026-03-08
description: Pengaturan font khusus memungkinkan Anda mengatur pengaturan font, memuat
  dokumen Word dengan aman, dan menangani font yang hilang dengan Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: id
og_description: Pengaturan font khusus memungkinkan Anda mengatur pengaturan font,
  memuat dokumen Word dengan aman, dan menangani font yang hilang dengan Aspose.Words.
og_title: Pengaturan Font Kustom di C# – Memuat Word & Menangani Font yang Hilang
tags:
- Aspose.Words
- C#
- Font Management
title: Pengaturan Font Kustom di C# – Memuat Word & Menangani Font yang Hilang
url: /id/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

a complete, production‑ready pattern for using **custom font settings** in C#. By configuring `LoadOptions`, registering a warning callback, and optionally pointing to a private font folder, you can **set font settings**, **load Word document** content reliably

Translate.

Then closing shortcodes.

Make sure to keep all shortcodes unchanged.

Now produce final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pengaturan Font Kustom di C# – Memuat Word & Menangani Font yang Hilang

Pernah bertanya‑tanya bagaimana **custom font settings** bekerja ketika file Word merujuk ke font yang tidak Anda miliki terpasang? Ini adalah masalah umum—dokumen Anda terlihat baik di satu mesin, lalu tiba‑tiba setiap paragraf beralih ke font fallback di mesin lain.  

Kabar baiknya? Dengan Aspose.Words Anda dapat **set font settings**, **load Word document** content, dan **handle missing fonts** dalam satu alur yang rapi. Di bawah ini Anda akan menemukan contoh lengkap yang siap dijalankan yang menunjukkan cara melakukannya, beserta “mengapa” di balik setiap langkah.

## Apa yang Akan Anda Pelajari

Dalam panduan ini kami akan membahas:

* Membuat objek `LoadOptions` dan melampirkan instance `FontSettings`.  
* Mendaftarkan callback peringatan sehingga Anda dapat melihat font mana yang diganti.  
* Memuat file DOCX yang mungkin kehilangan font, dan mencetak detail substitusi ke konsol.  

Pada akhir tutorial Anda akan dapat mengirimkan aplikasi C# Anda dengan percaya diri, mengetahui setiap skenario font yang hilang tercatat dan dapat ditangani nanti.

> **Prasyarat:** Aspose.Words untuk .NET (v23.12 atau lebih baru) terpasang via NuGet, dan pemahaman dasar tentang aplikasi konsol C#.

---

## Pengaturan Font Kustom – Mengonfigurasi LoadOptions

Hal pertama yang Anda perlukan adalah objek `LoadOptions`. Ini memberi tahu Aspose.Words bagaimana memperlakukan file yang masuk. Dengan menetapkan instance `FontSettings` yang baru, kita memberi perpustakaan tempat untuk mencari font kustom.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Mengapa ini penting:**  
Jika Anda melewatkan `FontSettings`, Aspose.Words akan kembali ke koleksi font default sistem. Itu berarti setiap font yang hilang akan secara diam‑diam diganti, dan Anda tidak akan tahu font mana yang ditukar. Dengan membuat kontainer `FontSettings` yang eksplisit, Anda mendapatkan kontrol penuh atas proses pencarian.

---

## Mengatur Font Settings pada LoadOptions

Sekarang kita memiliki objek `FontSettings`, Anda mungkin bertanya ke mana harus menunjukkannya. Biasanya Anda akan menambahkan folder yang berisi font yang Anda kirim bersama aplikasi:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Jika Anda tidak memiliki folder pribadi, Anda dapat menghilangkan blok ini—Aspose.Words tetap akan melaporkan font yang hilang melalui callback peringatan.*

**Tips pro:** Gunakan flag `recursive: true` jika font Anda tersebar di sub‑folder. Ini menghemat Anda dari menambahkan setiap path secara manual.

---

## Memuat Dokumen Word dengan Pengaturan Font Kustom

Dengan opsi yang sudah dipersiapkan, memuat dokumen menjadi sangat mudah. Konstruktor `Document` menerima path file dan `LoadOptions` yang baru saja kita buat.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Apa yang terjadi di balik layar?**  
Aspose.Words mem-parsing DOCX, memeriksa setiap referensi `<w:font>`, dan berkonsultasi dengan `FontSettings` yang Anda sediakan. Jika sebuah font tidak ditemukan, ia memicu peringatan tipe `FontSubstitution`. Handler kustom kami (ditunjukkan berikutnya) akan menangkap peringatan tersebut.

---

## Menangani Font yang Hilang dengan Warning Callback

Interface `IWarningCallback` memungkinkan Anda merespons masalah apa pun yang muncul selama pemuatan. Mengimplementasikannya sangat sederhana:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Saat dokumen dimuat, setiap font yang hilang akan menghasilkan baris seperti:

```
Font substituted: Arial -> Liberation Sans
```

**Mengapa Anda harus mencatat ini:**  
Di lingkungan produksi Anda dapat mengarahkan pesan‑pesan ini ke file atau sistem telemetri, sehingga mudah melihat font mana yang perlu Anda bundel atau lisensikan.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah program konsol mandiri yang mengikat semua komponen. Salin‑tempel ke proyek konsol .NET Core baru dan tekan **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Output yang diharapkan** (misalkan `input.docx` menggunakan font yang tidak Anda miliki):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Jika semua font tersedia, Anda hanya akan melihat baris konfirmasi akhir.

---

## Pertanyaan Umum & Kasus Tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika saya perlu menyematkan font yang hilang ke dalam PDF?** | Setelah memuat, panggil `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` lalu aktifkan penyematan dengan `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Bisakah saya menekan peringatan alih‑alih mencatatnya?** | Ya—set `loadOptions.WarningCallback = null;` atau implementasikan callback untuk mengabaikan peringatan non‑font. |
| **Apakah ini bekerja dengan file `.doc` dan `.rtf`?** | Tentu saja. Objek `LoadOptions` yang sama berlaku untuk format apa pun yang didukung oleh Aspose.Words. |
| **Apakah callback ini thread‑safe?** | Callback dijalankan pada thread yang sama dengan proses pemuatan dokumen, sehingga Anda dapat menulis ke konsol dengan aman. Untuk skenario multi‑thread, gunakan koleksi bersamaan atau kerangka kerja logging. |

---

## Tips Pro & Jebakan

* **Tips pro:** Jika Anda mengirimkan font yang tidak terpasang di mesin target, tambahkan ke folder yang Anda berikan ke `SetFontsFolder`. Ini menjamin rendering yang deterministik.
* **Perhatikan lisensi:** Beberapa font memerlukan lisensi komersial untuk penyematan. Selalu verifikasi EULA font sebelum membundelnya.
* **Catatan performa:** Memuat perpustakaan font yang besar dapat memperlambat parsing dokumen. Jaga folder tetap ramping—hanya sertakan font yang memang Anda perlukan.
* **Kasus tepi:** Ketika dokumen merujuk font dengan *PostScript name* alih‑alih nama keluarga, Aspose.Words tetap dapat menyelesaikannya selama file font ada di jalur pencarian.

---

## Kesimpulan

Anda kini memiliki pola lengkap yang siap produksi untuk menggunakan **custom font settings** di C#. Dengan mengonfigurasi `LoadOptions`, mendaftarkan warning callback, dan secara opsional menunjuk ke folder font pribadi, Anda dapat **set font settings**, **load Word document** content secara andal.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}