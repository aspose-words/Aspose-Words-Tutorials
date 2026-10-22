---
category: general
date: 2026-10-13
description: Pelajari substitusi font dalam dokumen menggunakan C#. Panduan ini menunjukkan
  cara mengatur enkoding big5, memuat sebuah DOCX, dan mengganti font lama dengan
  font modern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: id
lastmod: 2026-10-13
og_description: Penggantian font dalam dokumen sangat penting saat bekerja dengan
  file Cina lama. Ikuti tutorial langkah demi langkah ini untuk memuat DOCX dengan
  enkoding big5 dan mengganti font lama.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Penggantian font dalam dokumen dengan C# – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Cara melakukan substitusi font dalam dokumen dengan C#
url: /id/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Penggantian font dalam dokumen – tutorial lengkap C#

Jika Anda membutuhkan **font substitution in document** untuk menampilkan file Chinese lama dengan benar, panduan ini menunjukkan secara tepat cara melakukannya. Dengan mengonfigurasi pengkodean teks yang tepat dan menukar font yang usang dengan yang modern, Anda menjamin bahwa DOCX akhir ditampilkan sebagaimana mestinya.

Pemrosesan dokumen sering gagal ketika sumber menggunakan pengkodean lama seperti **big5** atau merujuk pada font yang tidak lagi ada di sistem. Tutorial ini memandu Anda memuat DOCX dengan **big5 encoding** yang tepat, menerapkan **legacy font replacement**, dan menghasilkan output bersih yang dapat berjalan di mesin Windows mana pun.

Anda akan belajar:

* Cara membuat objek `LoadOptions` dengan **big5 encoding**.  
* Cara membuka file DOCX menggunakan **C# LoadOptions**.  
* Cara melakukan **font substitution in document** dengan memetakan font lama ke padanan modern.  
* Penanganan kasus tepi untuk font yang hilang dan beberapa keluarga font.

Tidak diperlukan alat eksternal selain pustaka Aspose.Words untuk .NET, dan kode lengkap dapat disalin ke dalam proyek konsol dan dijalankan segera.

## Prasyarat

* .NET 6.0 atau lebih baru (contoh menggunakan sintaks konsol .NET 6).  
* Aspose.Words untuk .NET – pasang via `dotnet add package Aspose.Words`.  
* File DOCX yang disimpan dengan **big5 encoding** yang merujuk pada font lama `MingLiU-ExtB`.  
* Familiaritas dasar dengan C# dan Visual Studio atau IDE pilihan Anda.

## Langkah 1: Siapkan proyek dan impor namespace

Buat aplikasi konsol baru dan tambahkan direktif `using` yang diperlukan. Ini memastikan kode dapat dikompilasi tanpa modifikasi tambahan.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Pro tip:** Jaga metode `Main` tetap minimal; ini meningkatkan keterbacaan dan membuat tutorial lebih mudah diikuti.

## Langkah 2: Tentukan load options dengan pengkodean teks yang tepat (big5 untuk Chinese Tradisional)

Kelas `LoadOptions` memberi tahu Aspose.Words cara menafsirkan byte mentah dalam file sumber. Menggunakan **big5 encoding** sangat penting untuk karakter Chinese Tradisional yang disimpan dengan halaman kode lama tersebut.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Mengapa ini penting:** Jika Anda mengabaikan pengkodean atau menggunakan UTF‑8 default, karakter dapat muncul sebagai simbol kacau (mojibake). Menentukan `big5` mempertahankan glyph asli sebelum terjadi penggantian font apa pun.

## Langkah 3: Muat file DOCX menggunakan pengkodean yang ditentukan

Berikan instance `loadOptions` ke konstruktor `Document`. Ini memuat file sambil menghormati **document encoding for Chinese** yang Anda definisikan sebelumnya.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Jika file tidak dapat ditemukan, program akan melempar `FileNotFoundException`. Pastikan jalur sudah benar dan aplikasi memiliki izin membaca.

## Langkah 4: Ganti font lama dengan padanan modern

Banyak dokumen Chinese lama merujuk pada `MingLiU-ExtB`, yang mungkin tidak ada pada instalasi Windows terbaru. Memetakan ke `Microsoft JhengHei` (font Unicode yang banyak tersedia) memastikan rendering yang tepat.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Penjelasan:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` mendaftarkan aturan penggantian global. Setiap kali Aspose.Words menemukan `MingLiU-ExtB`, ia menukarnya dengan `Microsoft JhengHei`.  
* Loop opsional mencetak pemetaan, yang berguna untuk debugging pada dokumen besar dengan banyak keluarga font.

## Langkah 5: Simpan dokumen yang telah diproses

Setelah penggantian, tulis dokumen ke file baru. Output akan menampilkan teks Chinese menggunakan font modern, menghilangkan peringatan glyph yang hilang.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Buka file hasil di Microsoft Word atau penampil DOCX apa pun; Anda harus melihat karakter Chinese Tradisional ditampilkan bersih dengan `Microsoft JhengHei`.

## Menangani kasus tepi dan jebakan umum

| Situation | Recommended approach |
|-----------|----------------------|
| **Font sumber tidak terdaftar dalam dokumen** | Gunakan `doc.FontInfos.Substitution.Add` dengan pola wildcard, misalnya `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Beberapa font lama perlu diganti** | Panggil `Add` untuk setiap pasangan, atau muat kamus penggantian dari file konfigurasi. |
| **Font target tidak tersedia di mesin target** | Pilih font yang disertakan dengan Windows (mis., `Arial Unicode MS`) atau sematkan font menggunakan `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Kesalahan pengkodean masih muncul** | Verifikasi file sumber benar-benar menggunakan **big5**; Anda dapat memeriksa file dengan editor hex atau menggunakan `File.ReadAllBytes` dan membandingkan pola byte. |

## Contoh lengkap yang berfungsi

Berikut adalah program lengkap yang berdiri sendiri. Salin ke `Program.cs`, sesuaikan jalur file, dan jalankan.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Hasil yang diharapkan:** Membuka `big5_doc_fixed.docx` menampilkan semua karakter Chinese Tradisional yang dirender dengan benar, tanpa peringatan glyph yang hilang, karena `MingLiU-ExtB` telah diganti dengan `Microsoft JhengHei`.

## Kesimpulan

Anda kini memiliki metode andal untuk tugas **font substitution in document** menggunakan C#. Dengan mengonfigurasi **big5 encoding**, memuat DOCX dengan `LoadOptions`, dan memetakan font lama ke padanan modern, Anda menghilangkan masalah rendering yang mengganggu file Chinese lama.  

Dari sini Anda dapat:

* Memperluas peta penggantian untuk mencakup font lama tambahan.  
* Mengotomatiskan proses untuk kumpulan dokumen (loop melalui direktori).  
* Menggabungkan penggantian font dengan transformasi dokumen lain seperti watermark atau konversi PDF.

Silakan bereksperimen dengan font target yang berbeda atau sematkan font khusus untuk portabilitas penuh. Jika Anda menemui masalah, tinjau kembali tabel kasus tepi di atas atau konsultasikan dokumentasi Aspose.Words untuk penanganan font lanjutan.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Aktifkan Peringatan Penggantian Font di Aspose.Words – Panduan Lengkap](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Catat Peringatan Penggantian Font – Panduan Lengkap Aspose.Words](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Muat dengan Pengkodean dalam Dokumen Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}