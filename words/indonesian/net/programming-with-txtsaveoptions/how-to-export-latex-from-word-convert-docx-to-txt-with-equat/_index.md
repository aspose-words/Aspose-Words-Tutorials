---
category: general
date: 2026-03-21
description: Pelajari cara mengekspor LaTeX dari file Word DOCX dengan mengonversinya
  ke TXT, sambil mempertahankan persamaan. Panduan C# langkah demi langkah untuk mengekspor
  persamaan dari Word.
draft: false
keywords:
- how to export latex
- convert docx to txt
- export equations from word
- save docx as txt
- convert word equations latex
language: id
og_description: Bagaimana mengekspor LaTeX dari Word? Tutorial ini menunjukkan cara
  mengonversi DOCX ke TXT sambil mempertahankan persamaan sebagai LaTeX, menggunakan
  C#.
og_title: Cara Mengekspor LaTeX dari Word – Panduan Cepat DOCX ke TXT
tags:
- C#
- Aspose.Words
- LaTeX
- DOCX
- Text Export
title: Cara Mengekspor LaTeX dari Word – Mengonversi DOCX ke TXT dengan Persamaan
url: /id/net/programming-with-txtsaveoptions/how-to-export-latex-from-word-convert-docx-to-txt-with-equat/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengekspor LaTeX dari Word – Mengonversi DOCX ke TXT dengan Persamaan

Pernah bertanya-tanya **cara mengekspor LaTeX** dari dokumen Word tanpa menyalin setiap rumus secara manual? Anda bukan satu-satunya. Kebanyakan pengembang menemui kendala ketika mereka harus mengambil persamaan dari *.docx* dan memasukkannya ke dalam pipeline yang mendukung LaTeX.  

Berita baik? Dengan beberapa baris C# dan opsi penyimpanan yang tepat, Anda dapat **mengonversi docx ke txt** dan mendapatkan setiap persamaan Office Math yang dihasilkan sebagai LaTeX bersih. Dalam panduan ini kami akan membahas langkah‑langkah tepat, menjelaskan mengapa setiap pengaturan penting, dan menunjukkan hasil akhir yang dapat Anda verifikasi dalam hitungan detik.

## Apa yang Dibahas dalam Tutorial Ini

Kami akan memulai dengan menjelaskan prasyarat (Anda hanya memerlukan pustaka Aspose.Words untuk .NET). Kemudian kami akan menyelami proses tiga langkah:

1. Muat file *.docx* sumber.
2. Konfigurasikan `TxtSaveOptions` sehingga Office Math diekspor sebagai LaTeX.
3. Simpan dokumen sebagai file teks biasa.

Pada akhir, Anda akan mengetahui **cara mengekspor latex**, merasa nyaman dengan **mengekspor persamaan dari word**, dan memiliki potongan kode yang dapat digunakan kembali yang dapat Anda sisipkan ke dalam proyek C# mana pun.  

*Mengapa penting?* Jika Anda menghasilkan laporan ilmiah, tugas rumah, atau konten apa pun yang kemudian dikompilasi dengan LaTeX, mengotomatisasi ekspor ini menghemat berjam‑jam menyalin‑tempel dan menghilangkan kesalahan format.

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Core dan .NET Framework).
- Aspose.Words untuk .NET (versi percobaan gratis atau berlisensi). Instal melalui NuGet:

```bash
dotnet add package Aspose.Words
```

- Dokumen Word (`input.docx`) yang berisi setidaknya satu persamaan Office Math.

> **Tips pro:** Jika Anda tidak memiliki DOCX, buat file Word baru, sisipkan persamaan melalui *Insert → Equation*, dan simpan sebagai `input.docx`.

## Langkah 1: Muat Dokumen Sumber yang Ingin Anda Ekspor

Pertama kita membutuhkan instance `Document` yang menunjuk ke file yang ingin kita konversi. Kelas `Document` mengabstraksi seluruh file Word, memberi kami akses ke paragraf, tabel, dan—yang paling penting—objek Office Math.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source DOCX file
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Mengapa ini penting:** Memuat file membuat representasi dalam memori yang dapat dijelajahi oleh mesin penyimpanan. Tanpa objek ini, tidak ada yang dapat diekspor, dan opsi selanjutnya tidak akan berpengaruh.

## Langkah 2: Konfigurasikan Opsi Penyimpanan Teks untuk Mengekspor Office Math sebagai LaTeX

Keajaiban terletak pada `TxtSaveOptions`. Secara default, menyimpan ke teks biasa menghapus semua yang bukan teks, termasuk persamaan. Menetapkan `OfficeMathExportMode` ke `LaTeX` memberi tahu Aspose untuk menerjemahkan setiap node Office Math ke dalam padanan LaTeX-nya.

```csharp
// Step 2: Set up save options for LaTeX export
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This flag ensures every equation becomes LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

> **Apa yang terjadi di balik layar?** Aspose mengurai XML Office Math, memetakan operator ke perintah LaTeX, dan menulis hasilnya ke aliran teks. Enum `OfficeMathExportMode` juga menawarkan `Unicode` dan `MathML`—pilih yang sesuai dengan rantai alat Anda.

## Langkah 3: Simpan Dokumen sebagai File Teks Biasa Menggunakan Opsi yang Dikonfigurasi

Sekarang kami menulis konten yang telah diubah ke disk. Ekstensi file `.txt` menandakan format teks biasa, tetapi berkat opsi yang kami atur, file akan berisi campuran teks biasa dan potongan LaTeX di mana pun persamaan ada.

```csharp
// Step 3: Export the document to a TXT file with LaTeX equations
doc.Save(@"YOUR_DIRECTORY\Equations.txt", txtSaveOptions);
```

### Output yang Diharapkan

Buka `Equations.txt` di editor apa pun. Anda akan melihat sesuatu seperti:

```
This is a sample paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]
```

Jika LaTeX muncul persis seperti di atas, Anda telah berhasil **menyimpan docx sebagai txt** sambil mempertahankan persamaan.

## Variasi Umum & Kasus Tepi

### Mengonversi Banyak File dalam Batch

Jika Anda perlu memproses folder berisi file DOCX, bungkus tiga langkah tersebut dalam loop `foreach`:

```csharp
string[] files = Directory.GetFiles(@"YOUR_DIRECTORY", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtSaveOptions);
}
```

### Menangani Konten Bukan Persamaan

`TxtSaveOptions` juga memungkinkan Anda mengontrol pemutusan baris, pengkodean, dan apakah menyimpan teks tersembunyi. Misalnya, untuk memaksa UTF‑8:

```csharp
txtSaveOptions.Encoding = Encoding.UTF8;
```

### Mengekspor ke Format Berbasis Teks Lain

Jika Anda lebih suka Markdown daripada TXT mentah, cukup ubah ekstensi dan sesuaikan opsi bila perlu:

```csharp
doc.Save(@"YOUR_DIRECTORY\Equations.md", txtSaveOptions);
```

Blok LaTeX tetap utuh, yang dapat diproses oleh pengolah Markdown seperti Pandoc nanti.

## Contoh Lengkap yang Dapat Dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup semua pernyataan `using` yang diperlukan, penanganan kesalahan, dan komentar yang menjelaskan setiap baris.

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Adjust these paths to match your environment
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\Equations.txt";

            try
            {
                // 1️⃣ Load the Word document
                Document doc = new Document(inputPath);

                // 2️⃣ Prepare save options – this is where we tell Aspose to export equations as LaTeX
                TxtSaveOptions saveOptions = new TxtSaveOptions
                {
                    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                    Encoding = Encoding.UTF8          // Ensure Unicode characters survive
                };

                // 3️⃣ Perform the export
                doc.Save(outputPath, saveOptions);

                Console.WriteLine($"✅ Success! LaTeX‑rich text file created at: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Oops – something went wrong: {ex.Message}");
            }
        }
    }
}
```

Jalankan program, buka `Equations.txt` yang dihasilkan, dan Anda akan melihat setiap persamaan ditampilkan sebagai LaTeX—siap untuk dimasukkan ke dalam kompiler LaTeX atau alur kerja penerbitan ilmiah.

## Pertanyaan yang Sering Diajukan

**Apakah ini bekerja dengan versi Aspose.Words yang lebih lama?**  
Ya. Properti `OfficeMathExportMode` telah ada sejak versi 19.8. Jika Anda menggunakan versi yang lebih lama, tingkatkan setidaknya ke versi tersebut.

**Bagaimana jika DOCX saya berisi gambar?**  
Ekspor teks biasa memang mengabaikan gambar secara sengaja. Jika Anda membutuhkan gambar dan LaTeX, pertimbangkan mengekspor ke HTML (`HtmlSaveOptions`) dan kemudian memproses HTML untuk mengekstrak blok LaTeX.

**Bisakah saya mengekspor langsung ke file `.tex`?**  
Aspose tidak menyediakan penulis `.tex` bawaan, tetapi Anda dapat mengganti nama `.txt` menjadi `.tex` setelah ekspor—kode LaTeXnya tetap sama. Pastikan struktur dokumen di sekitarnya (preambule, `\begin{document}`) ditambahkan secara manual.

## Kesimpulan

Sekarang Anda tahu **cara mengekspor latex** dari file Word dengan **mengonversi docx ke txt** sambil mempertahankan setiap persamaan. Potongan kode C# tiga langkah—muat, konfigurasikan, simpan—menangani inti dari **mengekspor persamaan dari word**, dan pola yang sama dapat disesuaikan untuk pemrosesan batch atau format output alternatif.  

Siap untuk tantangan berikutnya? Coba **menyimpan docx sebagai txt** untuk dokumen multibahasa, atau jelajahi mengonversi potongan LaTeX tersebut menjadi PDF dengan alat seperti `pdflatex`. Tidak ada batasan ketika Anda menggabungkan Aspose.Words dengan alur kerja LaTeX yang solid.

---

![Diagram yang menunjukkan alur: DOCX → Aspose.Words → TXT dengan persamaan LaTeX](https://example.com/flow-diagram.png "diagram alur cara mengekspor latex")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}