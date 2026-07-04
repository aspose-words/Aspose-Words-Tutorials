---
category: general
date: 2026-05-29
description: Pelajari cara mengatur FontSettings di Aspose.Words dan menangani font
  yang hilang dengan elegan. Panduan langkah demi langkah dengan kode lengkap dan
  praktik terbaik.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: id
og_description: Cara mengatur FontSettings di Aspose.Words dan menangani font yang
  hilang dengan cepat. Ikuti panduan ini untuk solusi lengkap yang dapat dijalankan.
og_title: Cara Mengatur FontSettings – Menangani Font yang Hilang
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Cara Mengatur FontSettings – Menangani Font yang Hilang
url: /id/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengatur FontSettings – Menangani Font yang Hilang

Pernah bertanya‑tanya **cara mengatur FontSettings** saat bekerja dengan Aspose.Words dan tiba‑tiba menemukan dokumen yang merujuk pada font yang tidak terpasang? Ini adalah masalah umum, terutama saat memproses file yang diberikan klien di server yang hanya memiliki kumpulan font minimal. Kabar baiknya? Anda dapat menangkap kekosongan tersebut dan **menangani font yang hilang** tanpa aplikasi Anda crash atau menghasilkan PDF yang jelek.

Dalam tutorial ini kita akan membahas skenario dunia nyata: memuat DOCX yang meminta “Calibri” sementara kontainer Linux Anda hanya menyediakan “DejaVu Sans”. Anda akan melihat secara tepat cara mengonfigurasi FontSettings, berlangganan peringatan substitusi, dan menyediakan font fallback sehingga dokumen dirender persis seperti yang dimaksud penulis. Tanpa basa‑basi—hanya kode yang dapat Anda salin ke proyek Anda hari ini.

## Prasyarat

- .NET 6.0 atau lebih baru (API bekerja sama pada .NET Framework 4.7+)
- Aspose.Words untuk .NET 23.10 atau lebih baru (nama paket NuGet adalah `Aspose.Words`)
- Lingkungan pengembangan C# dasar (Visual Studio, Rider, atau VS Code)

Jika Anda sudah memiliki semuanya, mari mulai.

## Langkah 1: Buat FontSettings dan Dengarkan Peristiwa Substitusi

Inti solusi adalah objek `FontSettings`. Dengan menempelkan handler pada peristiwa `FontSubstitutionWarning` Anda akan mendapatkan laporan langsung setiap kali Aspose.Words harus mengganti tipe huruf yang tidak ada.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Mengapa ini penting:**  
Ketika mesin tidak dapat menemukan *Calibri*, ia mungkin beralih ke *Arial* secara diam‑diam. Dengan mendengarkan peringatan, Anda memiliki jejak audit yang transparan—sempurna untuk debugging atau pelaporan kepatuhan.

> **Pro tip:** Jika Anda menjalankan ini di server CI, alirkan output ke file log sehingga Anda dapat meninjau font apa saja yang hilang setelah batch selesai.

## Langkah 2: Lampirkan FontSettings ke LoadOptions

`LoadOptions` adalah gerbang untuk mengontrol cara dokumen diparsing. Dengan menetapkan `FontSettings` yang baru saja Anda konfigurasikan, setiap pemuatan `Document` berikutnya akan menghormati logika substitusi kami.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Apa yang terjadi di balik layar?**  
Selama konstruktor `Document`, Aspose.Words membaca XML DOCX, menyelesaikan referensi font, dan—jika font tidak ditemukan—memicu peringatan yang telah Anda siapkan sebelumnya. Tanpa hook ini, Anda tidak akan pernah tahu bahwa substitusi terjadi.

## Langkah 3: Muat Dokumen dan (Opsional) Tentukan Font Fallback

Sekarang kita akhirnya memuat file ke memori. Jika Anda sudah memiliki folder font fallback (misalnya, direktori font OpenType yang disertakan bersama aplikasi), beri tahu `FontSettings` di mana mencarinya. Langkah ini opsional tetapi sering menjadi cara paling bersih untuk *menangani font yang hilang*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Peringatan kasus tepi:**  
Jika dokumen berisi font khusus yang disematkan sebagai aliran biner, Aspose.Words akan menggunakannya secara otomatis—tidak diperlukan substitusi. Peringatan hanya muncul untuk font sistem yang *hilang*.

### Memverifikasi Hasil

Setelah memuat, Anda mungkin ingin menyimpan dokumen ke PDF atau Word untuk memastikan semuanya terlihat benar.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Saat Anda menjalankan program, konsol akan menampilkan baris‑baris seperti:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Jika Anda melihat pesan‑pesan ini, Anda telah berhasil **menangani font yang hilang** dan mengetahui tepat substitusi apa yang terjadi.

## Langkah 4: Lanjutan – Aturan Substitusi Font Kustom (Opsional)

Kadang‑kadang Anda memerlukan pemetaan deterministik, misalnya selalu mengganti *Times New Roman* dengan *Liberation Serif*. Anda dapat melakukannya dengan `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Mengapa repot?**  
Aturan eksplisit memberi Anda kontrol atas tipografi, memastikan konsistensi merek di seluruh PDF yang dihasilkan, terutama ketika Anda membuat materi pemasaran.

## Kesalahan Umum & Cara Menghindarinya

| Kesalahan | Gejala | Solusi |
|-----------|--------|--------|
| **Tidak ada output peringatan** | Anda mengira font baik‑baik saja tetapi dokumen terlihat aneh. | Pastikan `FontSubstitutionWarning` terpasang **sebelum** memuat dokumen. |
| **Folder fallback tidak dipindai** | Substitusi masih kembali ke default sistem. | Panggil `SetFontsFolder(path, true)` dengan argumen kedua `true` untuk memindai sub‑folder. |
| **Penurunan performa pada batch besar** | Memuat 10 ribu dokumen menjadi lambat. | Cache satu instance `FontSettings` dan gunakan kembali pada setiap pemuatan; hindari membuatnya berulang‑ulang. |
| **Font tersemat diabaikan** | Anda mengharapkan font tersemat khusus dipakai, tetapi terjadi substitusi. | Verifikasi DOCX sumber memang menyematkan font (cek di Word → File → Info → Fonts). |

## Contoh Lengkap yang Siap Pakai

Berikut adalah program lengkap yang dapat Anda salin‑tempel. Program ini menunjukkan segala hal mulai dari penanganan peristiwa hingga menyimpan PDF akhir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Output konsol yang diharapkan** (contoh):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Jalankan program, buka `Output.pdf`, dan Anda akan melihat teks dirender dengan font fallback—tidak ada kotak glyph yang hilang, tidak ada crash.

## Kesimpulan

Anda kini memiliki pola produksi yang solid untuk **cara mengatur FontSettings** di Aspose.Words dan **menangani font yang hilang** secara elegan. Dengan menyambungkan peristiwa `FontSubstitutionWarning`, menunjuk ke direktori font fallback, dan (jika diperlukan) mendefinisikan aturan substitusi eksplisit, Anda memperoleh visibilitas dan kontrol penuh atas tipografi dalam pipeline dokumen otomatis.

Apa selanjutnya? Coba tambahkan koleksi font kustom untuk tipe huruf merek, atau jelajahi API `FontSourceBase` untuk memuat font dari basis data atau penyimpanan cloud. Prinsip yang sama berlaku—cukup sambungkan sumber yang berbeda ke `FontSettings`.

Punya pertanyaan tentang kasus tepi, seperti menangani skrip kanan‑ke‑kiri atau font emoji? Tinggalkan komentar di bawah, dan selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}