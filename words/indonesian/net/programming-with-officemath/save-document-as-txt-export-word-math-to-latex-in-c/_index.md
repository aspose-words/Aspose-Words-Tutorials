---
category: general
date: 2026-04-24
description: Simpan dokumen sebagai txt dan konversi Word ke LaTeX dengan Aspose.Words.
  Pelajari cara mengekspor persamaan matematika Word ke LaTeX dengan cepat.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: id
og_description: Simpan dokumen sebagai txt dan konversi persamaan Word ke LaTeX menggunakan
  C#. Panduan lengkap langkah demi langkah dengan kode.
og_title: Simpan Dokumen sebagai TXT – Ekspor Matematika Word ke LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Simpan Dokumen sebagai TXT – Ekspor Matematika Word ke LaTeX dalam C#
url: /id/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Dokumen sebagai TXT – Ekspor Word Math ke LaTeX di C#

Pernahkah Anda perlu **save document as txt** sambil mempertahankan persamaan rumit Anda? Anda bukan satu‑satunya. Fitur bawaan Word “Save as plain text” membuang Office Math, meninggalkan teks yang tidak dapat dibaca. Bagaimana kalau Anda bisa menyimpan persamaan‑persamaan itu, tetapi dalam LaTeX yang bersih?

Dalam tutorial ini kita akan melangkah melalui cara **convert Word to LaTeX**‑ready text menggunakan Aspose.Words untuk .NET. Pada akhir tutorial Anda akan memiliki file `.txt` di mana setiap persamaan direpresentasikan sebagai markup LaTeX yang tepat, siap ditempelkan ke makalah atau file markdown. Tanpa konverter eksternal, tanpa menyalin‑tempel manual—hanya beberapa baris C#.

## Apa yang Akan Anda Pelajari

- Cara memuat file `.docx` dengan Aspose.Words.  
- Mengonfigurasi `TxtSaveOptions` sehingga Office Math diekspor sebagai LaTeX.  
- Menyimpan hasilnya ke file teks biasa yang dapat dibuka di editor apa pun.  
- Penanganan kasus tepi untuk persamaan inline vs. display, serta tip cepat untuk memproses batch banyak dokumen.

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga bekerja dengan .NET Framework 4.6+).  
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`).  
- Dokumen Word yang berisi setidaknya satu persamaan (objek Office Math).

---

## Langkah 1: Instal Aspose.Words dan Siapkan Proyek

Pertama, tambahkan pustaka ke proyek Anda. Buka terminal di folder solusi dan jalankan:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Jika Anda menggunakan Visual Studio, UI NuGet Package Manager juga dapat dipakai—cari “Aspose.Words” dan klik Install.

Sekarang buat aplikasi console baru (atau letakkan kode ke dalam yang sudah ada). Direktif `using` yang diperlukan adalah:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Ini akan membawa kelas `Document` dan tipe `TxtSaveOptions` ke dalam ruang lingkup.

## Langkah 2: Muat Dokumen Sumber

Kita perlu memberi tahu Aspose.Words lokasi file Word yang berisi persamaan. Ganti `YOUR_DIRECTORY/input.docx` dengan jalur sebenarnya di mesin Anda.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Mengapa ini penting:** Memuat dokumen memberi Aspose.Words akses penuh ke objek Office Math internal, yang sebaliknya tidak terlihat oleh pengekspor teks sederhana.

## Langkah 3: Konfigurasikan TxtSaveOptions untuk Ekspor LaTeX

Keajaiban terjadi pada objek `TxtSaveOptions`. Dengan mengatur `OfficeMathExportMode` ke `LaTeX`, setiap persamaan diubah menjadi ekivalen LaTeX‑nya.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **Bagaimana jika Anda membutuhkan MathML?** Ubah `OfficeMathExportMode` menjadi `MathML`. API yang sama mendukung beberapa format output.

## Langkah 4: Simpan Dokumen sebagai Teks Biasa

Sekarang kita menulis file keluar. File `Math.txt` yang dihasilkan akan berisi teks biasa ditambah fragmen LaTeX untuk setiap persamaan.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Menjalankan program menghasilkan file yang tampak kira‑kira seperti ini:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Perhatikan bagaimana persamaan inline menggunakan `$…$` sementara persamaan display dibungkus dengan `\[` dan `\]`. Itu adalah konvensi LaTeX standar, dan Aspose.Words melakukannya secara otomatis.

## Langkah 5: Verifikasi Output (Opsional)

Jika Anda ingin memastikan LaTeX yang dihasilkan valid, Anda dapat memberi file `.txt` ke kompiler LaTeX seperti `pdflatex` atau renderer daring seperti Overleaf. Teks tersebut harus dapat dikompilasi tanpa error, dan persamaan akan muncul persis seperti di Word.

```bash
pdflatex Math.txt
```

Jika muncul “Undefined control sequence”, pastikan paket LaTeX yang diperlukan (misalnya `amsmath`) sudah dimasukkan ke preamble saat Anda menyisipkan teks ke dalam dokumen LaTeX yang lebih besar.

## Menangani Variasi Umum

### Mengonversi Banyak File dalam Satu Folder

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Menangani Persamaan Inline vs. Display

Aspose.Words secara otomatis mendeteksi tipe persamaan berdasarkan tata letaknya di Word. Jika Anda perlu memaksa gaya tertentu, Anda dapat memproses output setelahnya:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Mengekspor ke Format Lain

Jika LaTeX bukan target Anda, cukup ganti mode ekspor:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Atau gunakan `HtmlSaveOptions` jika Anda lebih suka MathML yang disisipkan dalam HTML.

---

## Contoh Lengkap yang Siap Jalan

Berikut adalah program lengkap yang siap dijalankan. Salin‑tempel ke `Program.cs` pada proyek console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Jalankan program (`dotnet run`), buka `Math.txt`, dan Anda akan melihat konten Word Anda dengan persamaan LaTeX tetap utuh.

---

## Pertanyaan yang Sering Diajukan

**T: Apakah ini bekerja dengan file .doc lama?**  
J: Ya—Aspose.Words dapat membuka file `.doc` lama, tetapi persamaan kompleks mungkin disimpan sebagai gambar. Dalam kasus itu pengekspor akan menggantinya dengan komentar placeholder.

**T: Bagaimana jika persamaan mengandung simbol khusus?**  
J: Aspose.Words memetakan sebagian besar simbol Office Math ke perintah LaTeX standar. Untuk simbol yang benar‑benar khusus, Anda mungkin perlu mengedit LaTeX yang dihasilkan secara manual.

**T: Apakah outputnya ber‑encoding UTF‑8?**  
J: Secara default, `TxtSaveOptions` menulis UTF‑8, yang aman untuk kebanyakan bahasa dan simbol.

---

## Kesimpulan

Sekarang Anda tahu cara **save document as txt** sambil mempertahankan setiap persamaan sebagai markup LaTeX yang bersih. Pendekatan ini memungkinkan Anda **convert Word to LaTeX** tanpa alat pihak ketiga, dan dapat diskalakan dari satu file ke seluruh folder. Selanjutnya, Anda dapat menjelajahi **convert word equations to LaTeX** untuk pemrosesan batch, atau menyelam ke **export word math latex** untuk pipeline HTML atau Markdown.

Silakan bereksperimen—ganti `OfficeMathExportMode` ke MathML, sesuaikan penanganan line‑break, atau integrasikan potongan kode ini ke dalam alur kerja generasi dokumen yang lebih besar. Selamat coding, semoga persamaan Anda selalu ter‑render dengan sempurna!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}