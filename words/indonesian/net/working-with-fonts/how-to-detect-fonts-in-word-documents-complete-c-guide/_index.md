---
category: general
date: 2026-02-24
description: Cara mendeteksi font dalam dokumen Word menggunakan Aspose.Words. Pelajari
  cara mengatur callback dan memuat dokumen Word dengan contoh kode lengkap.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: id
og_description: Cara mendeteksi font dalam dokumen Word menggunakan callback peringatan.
  Panduan ini menunjukkan cara mengatur callback dan memuat dokumen Word dengan Aspose.Words.
og_title: Cara Mendeteksi Font di Dokumen Word – Tutorial C# Langkah demi Langkah
tags:
- C#
- Aspose.Words
- Document Processing
title: Cara Mendeteksi Font di Dokumen Word – Panduan Lengkap C#
url: /id/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendeteksi Font dalam Dokumen Word – Panduan Lengkap C# 

Pernah bertanya-tanya **bagaimana cara mendeteksi font** yang hilang saat Anda memuat file Word? Mungkin Anda pernah menemukan dokumen yang terlihat baik di editor, tetapi PDF yang Anda hasilkan menukar beberapa jenis huruf di balik layar. Itu adalah gejala klasik substitusi font, dan menanganinya lebih awal dapat menyelamatkan Anda dari kejutan tata letak yang tidak menyenangkan.

Dalam tutorial ini kami akan membahas solusi praktis: menggunakan **Aspose.Words** untuk memuat sebuah `.docx`, melampirkan warning callback, dan **how to set callback** yang melaporkan setiap substitusi font. Pada akhir tutorial Anda tidak hanya akan mengetahui **how to detect fonts** secara programatis, tetapi juga memahami **how to set callback** dengan benar dan **load word document** dengan aman—semuanya dalam satu contoh C# yang dapat dijalankan.

> **Apa yang akan Anda dapatkan**
> * Contoh kode lengkap yang siap disalin‑tempel  
> * Penjelasan langkah‑demi‑langkah untuk setiap baris  
> * Tips menangani kasus tepi seperti beberapa font yang hilang atau folder font khusus  
> * Output konsol yang diharapkan sehingga Anda dapat memverifikasi semuanya berfungsi  

---

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga bekerja dengan .NET Core)  
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)  
- File Word yang secara sengaja merujuk ke font yang tidak Anda miliki terpasang (misalnya `MissingFont.docx`)  
- Visual Studio, Rider, atau editor apa pun yang Anda suka  

Tidak ada pustaka lain yang diperlukan; semuanya merupakan bagian dari runtime .NET standar.

---

## Cara Mendeteksi Font dalam Dokumen Word

### Langkah 1: Buat Load Options dan Lampirkan Warning Callback

Hal pertama yang kami lakukan adalah memberi tahu Aspose.Words bahwa kami ingin diberi notifikasi tentang masalah apa pun yang muncul saat memuat file. Di sinilah **how to set callback** berperan.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Mengapa ini penting:**  
`LoadOptions` adalah gerbang untuk menyesuaikan proses pemuatan. Dengan menetapkan sebuah instance `FontWarningCollector` ke `WarningCallback`, Aspose.Words akan memanggil metode `Warning` kami setiap kali ia mengganti font yang hilang dengan fallback. Ini adalah inti dari **how to detect fonts** yang tidak ada di mesin.

---

### Langkah 2: Siapkan Instance LoadOptions

Sekarang kami membuat instance `LoadOptions` dan menghubungkan callback kami.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Pro tip:** Jika Anda perlu mengontrol *di mana* Aspose mencari font pengganti, Anda juga dapat mengatur `loadOptions.FontSettings` di sini. Ini berguna ketika Anda memiliki folder font pribadi di server.

---

### Langkah 3: Muat Dokumen Word

Dengan opsi siap, kami akhirnya **load word document**. Ini adalah momen di mana Aspose mem-parsing DOCX dan, jika ada font yang hilang, callback kami dipicu.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Apa yang terjadi di balik layar?**  
Aspose.Words membaca bagian XML dari DOCX, menyelesaikan setiap referensi `<w:font>`, dan memeriksa koleksi font sistem. Setiap kali referensi tidak dapat dipenuhi, ia mengganti dengan font fallback pertama yang cocok dan menghasilkan peringatan `FontSubstitution`.

---

### Langkah 4: Verifikasi Output

Jalankan program dan perhatikan konsol. Untuk setiap font yang hilang Anda akan melihat baris seperti:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Jika dokumen tidak mengandung font yang hilang, konsol tetap diam—artinya **how to detect fonts** tidak menemukan apa pun.

---

### Langkah 5: Contoh Lengkap yang Berfungsi (Aplikasi Konsol)

Berikut adalah `Program.cs` yang berdiri sendiri yang dapat Anda masukkan ke dalam proyek konsol baru. Ini mencakup semua bagian yang kami bahas serta pembantu kecil untuk menjaga jendela konsol tetap terbuka saat debugging.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Output konsol yang diharapkan** (contoh):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Jika Anda mengganti `MissingFont.docx` dengan file yang hanya menggunakan font yang terpasang, Anda hanya akan melihat baris “Press any key…”—menegaskan bahwa logika deteksi berfungsi sebagaimana mestinya.

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya perlu menangkap *semua* peringatan, bukan hanya substitusi font?

Cukup hapus guard `if (info.Type == WarningType.FontSubstitution)`. Objek `WarningInfo` berisi enum `Type` yang dapat Anda gunakan untuk skenario lain (mis., `DocumentStructure`, `ImageLoading`).

### Bisakah saya mencatat peringatan ke file alih-alih konsol?

Tentu saja. Ganti `Console.WriteLine` dengan panggilan ke framework logging apa pun (`Serilog`, `NLog`, dll.). Callback dijalankan pada thread yang sama dengan yang memuat dokumen, jadi pastikan logger Anda aman untuk thread.

### Bagaimana perilaku ini dalam aplikasi web?

Di ASP.NET Core Anda biasanya menyuntikkan implementasi singleton `IWarningCallback` dan melewatkannya melalui `LoadOptions`. Ingatlah untuk menghindari menulis langsung ke aliran respons—catat ke basis data atau koleksi dalam memori yang kemudian dapat Anda ekspos melalui endpoint API.

### Bagaimana dengan font khusus yang disimpan di folder non‑sistem?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Sekarang Aspose.Words akan mencari `C:\MyCustomFonts` sebelum beralih ke font OS, mengurangi jumlah peringatan substitusi yang Anda lihat.

---

## Ringkasan Visual

![Mendeteksi peringatan callback font di Aspose.Words](/images/font-warning-callback.png "Cara mendeteksi font menggunakan callback peringatan")

*Tangkapan layar menunjukkan output konsol ketika font yang hilang digantikan. Teks alt berisi kata kunci utama untuk SEO.*

---

## Kesimpulan

Anda kini memiliki pola yang solid dan siap produksi untuk **how to detect fonts** dalam file Word apa pun yang Anda muat dengan Aspose.Words. Dengan **how to set callback** Anda mendapatkan wawasan waktu nyata tentang jenis huruf yang hilang atau digantikan, dan Anda telah mempelajari cara yang tepat untuk **load word document** sambil menjaga kode Anda tetap bersih dan dapat dipelihara.

Langkah selanjutnya? Cobalah memperluas callback untuk mengumpulkan peringatan ke dalam daftar, lalu menampilkannya di UI atau laporan otomatis. Anda juga dapat mengeksplorasi `FontSettings.SubstitutionSettings` untuk mengontrol *font mana* yang dipilih sebagai fallback.

Jangan ragu untuk bereksperimen—ganti dokumen, tambahkan lebih banyak font yang hilang, atau integrasikan logika ini ke dalam pipeline pemrosesan dokumen yang lebih besar. Jika Anda mengalami kendala, tinggalkan komentar di bawah atau hubungi saya di GitHub.

Selamat coding, semoga dokumen Anda selalu ditampilkan dengan font yang Anda harapkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}