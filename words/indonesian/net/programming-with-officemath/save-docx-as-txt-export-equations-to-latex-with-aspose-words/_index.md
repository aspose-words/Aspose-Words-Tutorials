---
category: general
date: 2026-02-12
description: Simpan docx sebagai txt dan konversi persamaan ke LaTeX dalam satu langkah.
  Pelajari cara mengekspor matematika dari Word menggunakan C# dan Aspose.Words.
draft: false
keywords:
- save docx as txt
- convert docx to txt
- how to export math
- convert equations to latex
- how to export equations
language: id
og_description: Simpan docx sebagai txt dan ekspor matematika ke LaTeX menggunakan
  C#. Panduan langkah demi langkah untuk Aspose.Words.
og_title: Simpan docx sebagai txt – Ekspor Persamaan Word ke LaTeX
tags:
- Aspose.Words
- C#
- Document Conversion
title: Simpan docx sebagai txt – Ekspor Persamaan ke LaTeX dengan Aspose.Words
url: /id/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/
---

.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan docx sebagai txt – Ekspor Persamaan Word ke LaTeX dengan Aspose.Words

Pernah perlu **save docx as txt** tetapi selalu menemui kendala ketika dokumen Anda berisi Office Math? Anda tidak sendirian. Kebanyakan pengembang menganggap ekspor teks biasa akan sekadar menghapus semuanya, namun persamaannya menghilang, meninggalkan kekacauan yang tidak dapat dibaca.  

Berita baiknya? Dengan Aspose.Words Anda dapat **save docx as txt** *dan* memberi tahu perpustakaan untuk merender setiap persamaan sebagai kode LaTeX. Dalam tutorial ini kami akan membahas seluruh proses, mulai dari memuat file `.docx` hingga menghasilkan `.txt` bersih yang berisi semua matematika Anda dalam format yang siap untuk publikasi ilmiah.

Pada akhir tutorial Anda akan mengetahui **how to export math** dari Word, mengapa Anda mungkin ingin **convert equations to latex**, dan bagaimana **convert docx to txt** tanpa kehilangan konten penting apa pun.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi 23.8 atau lebih baru). Paket NuGet-nya adalah `Aspose.Words`.
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code dengan ekstensi C#).
- Dokumen Word contoh (`input.docx`) yang berisi setidaknya satu objek Office Math.
- Familiaritas dasar dengan C# dan aplikasi console.

Tidak diperlukan alat pihak ketiga tambahan; semuanya berjalan dalam C# murni.

## Langkah 1 – Muat Dokumen Sumber

Hal pertama yang kami lakukan adalah membaca file Word ke dalam objek `Document`. Objek ini mewakili seluruh paket Word dalam memori, memberi kami akses ke paragraf, tabel, dan node Office Math yang tersembunyi.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyFiles\input.docx");
```

> **Mengapa ini penting:** Memuat dokumen dengan cara ini memungkinkan Aspose.Words mempertahankan struktur asli, sehingga ketika kami kemudian mengekspor ke TXT perpustakaan masih mengetahui di mana setiap persamaan berada.

## Langkah 2 – Beri Tahu Aspose.Words Cara Menangani Office Math

Secara default, `TxtSaveOptions` hanya menulis teks biasa dan mengabaikan semua matematika. Kami mengubah perilaku itu dengan mengatur `OfficeMathExportMode` menjadi `LaTeX`. Ini memberi tahu mesin untuk mengganti setiap objek Office Math dengan representasi LaTeX-nya.

```csharp
// Step 2: Configure TXT save options to export Office Math as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

> **Tip pro:** Jika Anda pernah membutuhkan persamaan dalam MathML, ganti `OfficeMathExportMode.LaTeX` dengan `OfficeMathExportMode.MathML`. API yang sama bekerja untuk kedua format.

## Langkah 3 – Simpan Dokumen sebagai File Teks Biasa

Sekarang kami melakukan konversi sebenarnya. Metode `Save` menerima jalur target dan opsi yang baru saja kami konfigurasi.

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save(@"C:\MyFiles\Equations.txt", txtSaveOptions);
```

Saat kode dijalankan, `Equations.txt` akan berisi:

```
This is a sample paragraph.
Here is an inline equation: $E = mc^2$
And a displayed equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]
```

> **Apa yang Anda lihat:** Setiap objek Office Math kini dibungkus dalam delimiter LaTeX (`$…$` untuk inline, `\[`…`\]` untuk display). Teks di sekitarnya tetap persis seperti di DOCX asli.

## Contoh Lengkap yang Dapat Dijalankan

Berikut adalah aplikasi console minimal yang dapat Anda salin‑tempel ke proyek C# baru dan jalankan segera.

```csharp
using System;
using Aspose.Words;

namespace DocxToTxtWithLatex
{
    class Program
    {
        static void Main(string[] args)
        {
            // Define input and output paths
            string inputPath = @"C:\MyFiles\input.docx";
            string outputPath = @"C:\MyFiles\Equations.txt";

            // Load the Word document
            Document doc = new Document(inputPath);

            // Configure save options – export equations as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX
            };

            // Perform the conversion
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"Successfully saved TXT with LaTeX equations to: {outputPath}");
        }
    }
}
```

### Hasil yang Diharapkan

Buka `Equations.txt` dengan editor teks apa pun. Anda akan melihat paragraf asli, dan setiap persamaan muncul sebagai kode LaTeX. File ini kini siap untuk dimasukkan ke dalam kompilator LaTeX, prosesor markdown, atau sistem apa pun yang memahami sintaks LaTeX.

## Pertanyaan Umum & Kasus Tepi

### 1. *Bagaimana jika dokumen saya tidak memiliki persamaan?*  
Konversi tetap berfungsi; Aspose.Words akan sekadar menulis konten teks. Tidak ada delimiter LaTeX tambahan yang ditambahkan.

### 2. *Bisakah saya menyesuaikan delimiter?*  
Ya. `TxtSaveOptions` menyediakan properti `InlineMathDelimiter` dan `DisplayMathDelimiter`. Misalnya:

```csharp
saveOptions.InlineMathDelimiter = @"\(";
saveOptions.DisplayMathDelimiter = @"\[\[";
```

### 3. *Bagaimana dengan dokumen besar (ratusan MB)?*  
Aspose.Words melakukan streaming file secara internal, sehingga penggunaan memori tetap wajar. Namun, Anda mungkin ingin meningkatkan pengaturan `MemoryUsage` jika mengalami `OutOfMemoryException`.

### 4. *Apakah output LaTeX dijamin dapat dikompilasi?*  
Aspose.Words mengikuti pemetaan Office Math ke LaTeX yang didefinisikan oleh Microsoft. Kebanyakan konstruksi umum (fraksi, integral, penjumlahan, matriks) dapat dikompilasi tanpa masalah. Simbol khusus mungkin memerlukan penyesuaian manual.

### 5. *Bisakah saya juga mengekspor ke format teks biasa lainnya?*  
Tentu saja. Pola yang sama bekerja untuk `HtmlSaveOptions`, `MarkdownSaveOptions`, dll. Cukup ganti `TxtSaveOptions` dengan kelas yang sesuai.

## Tips untuk Pengalaman Lancar

- **Validate the output**: Jalankan `pdflatex` cepat pada potongan kecil untuk memastikan LaTeX yang dihasilkan tidak kehilangan paket.
- **Batch processing**: Bungkus kode di atas dalam loop `foreach` untuk mengonversi beberapa file DOCX sekaligus.
- **Logging**: Gunakan `Console.WriteLine` atau logger yang tepat untuk menangkap peringatan apa pun yang mungkin dikeluarkan Aspose.Words tentang fitur matematika yang tidak didukung.
- **Version check**: Enum `OfficeMathExportMode` diperkenalkan di Aspose.Words 22.9. Jika Anda menggunakan versi yang lebih lama, tingkatkan melalui NuGet.

## Kesimpulan

Kami telah menunjukkan cara **save docx as txt** sambil mempertahankan setiap persamaan sebagai LaTeX. Pendekatan tiga langkah—muat, konfigurasi, simpan—mencakup seluruh alur kerja, dan contoh lengkap memungkinkan Anda menempatkan kode ke dalam proyek .NET apa pun sekarang juga.  

Jika Anda ingin **convert docx to txt** untuk pemrosesan lanjutan, atau Anda hanya perlu **how to export equations** untuk makalah ilmiah, metode ini andal dan mudah diperluas. Selanjutnya, Anda dapat menjelajahi **how to export math** ke bahasa markup lain (MathML, ASCIIMath) atau menggabungkan output TXT dengan generator situs statis untuk situs dokumentasi.

Selamat coding, semoga konversi Anda bebas error!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}