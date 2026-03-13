---
category: general
date: 2026-03-13
description: Cara menangkap peringatan saat memuat dokumen dengan Aspose.Words, serta
  tips untuk menangani font yang hilang dan mengatur pengaturan font khusus. Pelajari
  solusi C# lengkap.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: id
og_description: Cara menangkap peringatan saat memuat file Word dengan Aspose.Words,
  serta cara praktis menangani font yang hilang dan mengatur pengaturan font khusus.
og_title: Cara Menangkap Peringatan di Aspose.Words – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Document Processing
title: Cara Menangkap Peringatan di Aspose.Words – Panduan Lengkap
url: /id/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

happy coding!" translate.

Make sure to keep shortcodes at top and bottom unchanged.

Let's produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menangkap Peringatan di Aspose.Words – Panduan Lengkap

Pernah bertanya‑tanya **bagaimana cara menangkap peringatan** yang muncul saat Aspose.Words memuat dokumen? Dalam banyak proyek dunia nyata Anda akan melihat peringatan substitusi font, catatan fitur usang, atau bahkan pesan terkait keamanan. Mengabaikannya seperti mengemudi dengan kaca depan retak—Anda mungkin sampai tujuan, tetapi tidak akan tahu kapan sesuatu akan rusak.

Kabar baiknya, Aspose.Words menyediakan cara bersih berbasis callback untuk menyaring pesan‑pesan tersebut. Dalam tutorial ini kami akan membahas **contoh lengkap C#** yang tidak hanya menangkap peringatan tetapi juga menunjukkan **cara menangani font yang hilang** dan **mengatur pengaturan font kustom** sehingga dokumen Anda dirender persis seperti yang Anda harapkan.

---

## Apa yang Akan Anda Pelajari

- Mengonfigurasi `LoadOptions` untuk menyisipkan objek `FontSettings` kustom.  
- Mendaftarkan callback peringatan yang menyaring peristiwa `FontSubstitution`.  
- Mengeluarkan detail peringatan ke konsol (atau logger apa pun yang Anda pilih).  
- Memperluas solusi untuk menangani font yang hilang secara elegan di berbagai platform.  

Pada akhir panduan ini Anda akan memiliki potongan kode siap‑jalankan yang dapat Anda sisipkan ke proyek .NET mana pun, plus beberapa tips praktis untuk menghindari jebakan umum.

---

## Prasyarat

| Persyaratan | Mengapa Penting |
|-------------|-----------------|
| **Aspose.Words for .NET** (v23.12 atau lebih baru) | API yang kami gunakan (`LoadOptions`, `IWarningCallback`) berada di sini. |
| **.NET 6+** (atau .NET Framework 4.7.2+) | Fitur bahasa modern membuat kode lebih bersih. |
| **Sebuah file DOCX contoh** (bernama `input.docx`) ditempatkan di folder yang diketahui | Kami memerlukan sesuatu untuk dimuat dan memicu peringatan. |
| **Konsol atau kerangka kerja logging** (opsional) | Untuk melihat peringatan yang ditangkap beraksi. |

Tidak ada paket NuGet tambahan yang diperlukan selain Aspose.Words itu sendiri.

---

## Langkah 1: Siapkan Pengaturan Font Kustom  

Sebelum Anda memuat dokumen, Anda dapat memberi tahu Aspose.Words di mana mencari font. Inilah bagian **set custom font settings** dari puzzle.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Mengapa ini penting:**  
Jika sebuah DOCX merujuk ke font yang tidak terpasang di mesin, Aspose.Words akan secara diam‑diam mengganti dengan font fallback *kecuali* Anda telah mengonfigurasi folder dengan font yang dibutuhkan. Dengan mengatur folder kustom Anda mengurangi kemungkinan munculnya peringatan “font‑substitution” sejak awal.

> **Tip pro:** Di Linux Anda mungkin perlu menambahkan paket `fonts-dejavu-core` atau koleksi TrueType apa pun yang dibutuhkan dokumen Anda.

---

## Langkah 2: Daftarkan Callback Peringatan  

Aspose.Words mengimplementasikan `IWarningCallback`. Kami akan membuat handler kecil yang mencetak hanya peringatan yang kami pedulikan: font yang hilang atau yang disubstitusi.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Mengapa ini penting:**  
Skenario **handle missing fonts** kini terlihat jelas. Alih‑alih menebak font mana yang diganti, Anda mendapatkan deskripsi jelas seperti “Font 'Calibri' was substituted with 'Arial'”. Ini sangat berharga saat men-debug masalah tata letak pada PDF yang dihasilkan atau laporan tercetak.

---

## Langkah 3: Muat Dokumen dengan Opsi yang Dikonfigurasi  

Sekarang kita akhirnya membawa dokumen ke memori, menggunakan `LoadOptions` yang baru saja dipersiapkan.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Jika file sumber menggunakan font yang tidak ada di `C:\MyFonts`, Anda akan melihat output serupa dengan:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Baris itu adalah hasil **how to capture warnings** yang Anda cari.

---

## Langkah 4: Contoh Lengkap yang Siap Pakai (Copy‑Paste Ready)

Berikut seluruh program, siap untuk dikompilasi. Tempelkan ke proyek konsol baru dan jalankan—pastikan jalur mengarah ke lokasi yang nyata di mesin Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Output yang diharapkan:**  

- Jika semua font tersedia:  
  `Document processed. Check console for any warning messages.`  

- Jika ada font yang hilang:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Langkah 5: Variasi Umum & Kasus Edge  

| Situasi | Apa yang Harus Disesuaikan |
|---------|----------------------------|
| **Beberapa folder font** | Panggil `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` untuk setiap lokasi tambahan. |
| **Menekan semua peringatan** | Implementasikan `Warn` tetapi biarkan tubuhnya kosong, atau set `loadOptions.WarningCallback = null;`. |
| **Menangkap tipe peringatan lain** | Periksa `info.WarningType` terhadap `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent`, dll. |
| **Menjalankan di Linux/macOS** | Pastikan folder font berisi file `.ttf`/`.otf` yang kompatibel dengan Linux; Anda mungkin perlu menginstal `libfontconfig`. |
| **Dokumen besar** | Pertimbangkan streaming dokumen (`LoadOptions.LoadFormat = LoadFormat.Docx;`) untuk mengurangi tekanan memori. |

Dengan mengantisipasi skenario‑skenario ini Anda akan menghindari kejutan saat berpindah dari mesin dev ke pipeline CI atau VM cloud.

---

## Langkah 6: Konfirmasi Visual (Opsional)

Jika Anda lebih suka isyarat visual cepat, Anda dapat menuliskan peringatan yang ditangkap ke laporan HTML kecil. Berikut snippet singkat yang menulis pesan ke `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Setelah memuat dokumen, panggil `handler.WriteReport(@"C:\Docs\warnings.html");` dan buka di browser. Gambar di bawah menunjukkan tampilan laporan yang mungkin:

![Tangkapan layar cara menangkap peringatan](/images/capture-warnings.png)

*Alt text:* **cara menangkap peringatan** – screenshot output konsol dan laporan HTML.

---

## Kesimpulan  

Kami telah membahas **cara menangkap peringatan** di Aspose.Words, mendemonstrasikan cara andal **menangani font yang hilang**, dan menunjukkan **cara mengatur pengaturan font kustom** untuk rendering yang deterministik. Contoh lengkap siap disisipkan ke solusi .NET apa pun, dan `FontWarningHandler` modular dapat diperluas untuk menyesuaikan strategi logging atau telemetry Anda.

Langkah selanjutnya? Coba ganti pemanggilan `Console.WriteLine` dengan logger terstruktur seperti Serilog, atau dorong peringatan ke Application Insights untuk pemantauan real‑time. Anda juga dapat menjelajahi pola `DocumentVisitor` jika perlu memeriksa konten dokumen setelah dimuat.

Ada pertanyaan tentang tipe peringatan lain atau strategi embedding font? Tinggalkan komentar di bawah—selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}