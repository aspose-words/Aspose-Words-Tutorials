---
category: general
date: 2026-04-21
description: Simpan matematika Office LaTeX dengan cepat menggunakan Aspose.Words
  – pelajari juga cara menyimpan teks biasa Word dan mengekspor persamaan Word ke
  LaTeX sekaligus.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: id
og_description: simpan matematika Office LaTeX secara instan; pelajari cara mengekspor
  persamaan Word ke LaTeX dan mengonversi matematika Word ke LaTeX dengan Aspose.Words
  di C#.
og_title: simpan Office Math LaTeX – Ekspor persamaan Word ke LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Simpan Office Math LaTeX – Ekspor Persamaan Word ke LaTeX dalam C#
url: /id/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Export Word equations to LaTeX with Aspose.Words

Pernah membutuhkan untuk **save office math latex** dari file `.docx` tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian, dan kabar baiknya solusinya cukup sederhana. Dalam panduan ini kami akan menjelaskan langkah‑langkah tepat untuk mengekspor persamaan Word latex (bahkan MathML) menggunakan Aspose.Words untuk .NET, sambil menunjukkan cara **save word plain text** bersama dengan matematika.

Kami akan membahas semua yang mungkin Anda tanyakan: mengapa Anda memilih LaTeX dibandingkan format lain, cara mengonfigurasi `TxtSaveOptions`, dan apa yang harus dilakukan jika Anda perlu **convert word math latex** ke representasi lain. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat dijalankan yang mengambil dokumen Word dengan objek Office Math dan menghasilkan file `.txt` bersih yang berisi persamaan LaTeX (atau MathML). Tanpa alat eksternal, tanpa menyalin‑tempel manual—hanya kode C# bersih yang dapat Anda masukkan ke proyek apa pun.

## Prasyarat

- **Aspose.Words for .NET** (v23.10 atau lebih baru). Paket NuGet adalah `Aspose.Words`.
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code dengan ekstensi C#).
- File Word (`.docx`) yang berisi setidaknya satu persamaan yang dibuat dengan editor Office Math.
- Familiaritas dasar dengan sintaks C#—tidak ada yang rumit, hanya pernyataan `using` biasa.

Jika semua poin di atas sudah terpenuhi, bagus—mari kita mulai.

## Langkah 1 – Siapkan opsi **save office math latex**

Hal pertama yang harus Anda lakukan adalah memberi tahu Aspose.Words bagaimana konten matematika harus dirender. Kelas `TxtSaveOptions` memiliki properti `OfficeMathExportMode` yang menerima tiga nilai: `LaTeX`, `MathML`, atau `Text`. Untuk tujuan utama kami, kami akan memilih `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Mengapa ini penting:** Ketika Anda mengatur `OfficeMathExportMode` ke `LaTeX`, setiap persamaan diubah menjadi sumber LaTeX mentahnya. Sumber tersebut kemudian dapat dikompilasi dengan mesin LaTeX apa pun, memberikan tipografi yang sempurna tanpa perlu mengetik ulang rumus.

> **Tip pro:** Jika Anda pernah perlu **convert word equations mathml**, cukup ganti nilai enum menjadi `OfficeMathExportMode.MathML`. Sisanya kode tetap sama.

## Langkah 2 – Muat dokumen Word (skenario **save word plain text**)

Selanjutnya, kami memuat file sumber `.docx`. Langkah ini sama baik Anda hanya tertarik pada ekstraksi teks biasa maupun Anda juga menginginkan persamaan dalam LaTeX.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**Apa yang terjadi di sini?** Konstruktor `Document` membaca file ke memori. Pemeriksaan cepat dengan `GetChildNodes` membantu Anda menangkap kasus tepi umum—mencoba mengekspor LaTeX dari file yang tidak mengandung persamaan. Ini adalah perlindungan kecil yang menyelamatkan Anda dari output kosong yang membingungkan nantinya.

## Langkah 3 – **save office math latex** ke file teks biasa

Sekarang kami akhirnya menulis file tersebut. Metode `Save` menghormati `TxtSaveOptions` yang kami konfigurasikan sebelumnya, sehingga `.txt` yang dihasilkan akan berisi teks biasa serta potongan LaTeX untuk setiap persamaan.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

Saat Anda membuka `Equations.txt`, Anda akan melihat sesuatu seperti:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

Blok LaTeX secara otomatis dibungkus dalam `\begin{equation}` … `\end{equation}`, sehingga siap dimasukkan ke dalam dokumen LaTeX apa pun.

## Langkah 4 – Alternatif: **convert word equations mathml** alih-alih LaTeX

Jika alur kerja Anda lebih memilih MathML (misalnya, halaman web yang merender persamaan dengan MathJax), cukup ubah mode ekspor:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

Output sekarang akan berisi tag MathML bergaya XML, seperti:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

Itulah cara cepat untuk **convert word equations mathml** tanpa menulis parser khusus.

## Langkah 5 – Bonus: **save word plain text** sambil memisahkan persamaan

Terkadang Anda menginginkan versi teks bersih dari dokumen *tanpa* LaTeX atau MathML yang disematkan. Anda dapat mencapainya dengan mengubah mode ekspor menjadi `Text` dan menjalankan proses simpan kedua:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Sekarang Anda memiliki tiga file berdampingan:

| File                         | Isi                                    |
|------------------------------|----------------------------------------|
| `Equations.txt`              | Teks biasa **+** persamaan LaTeX       |
| `EquationsMathML.txt`        | Teks biasa **+** persamaan MathML      |
| `PlainDocument.txt`          | Teks murni, persamaan dihapus          |

Pola ini berguna ketika Anda perlu memasukkan teks biasa ke dalam indeks pencarian sambil tetap mempertahankan matematika asli untuk publikasi akademik.

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

Di bawah ini adalah program lengkap yang dapat Anda kompilasi dan jalankan apa adanya. Program ini mendemonstrasikan **save office math latex**, **export word equations latex**, **convert word math latex**, dan **save word plain text**—semua dalam satu skrip rapi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Hasil yang diharapkan:** Setelah dijalankan, Anda akan menemukan tiga file teks di `C:\MyDocs`. Buka `Equations.txt` dan Anda akan melihat blok LaTeX; `EquationsMathML.txt` akan berisi MathML; `PlainDocument.txt` akan bebas dari markup persamaan apa pun.

## Pertanyaan Umum & Kasus Tepi

- **Bagaimana jika saya hanya membutuhkan LaTeX untuk sebagian persamaan?**  
  Gunakan API node `OfficeMath` untuk mengiterasi setiap persamaan, ekspor secara manual dengan `MathConverter`, dan ganti teks placeholder di tempat yang Anda inginkan. Pendekatan ini memberi Anda kontrol detail tetapi menambah beberapa baris kode ekstra.

- **Apakah ini bekerja dengan .NET Core / .NET 5+?**  
  Tentu saja. Aspose.Words bersifat lintas‑platform, sehingga kode yang sama berjalan di Windows, Linux, dan macOS selama versi runtime cocok dengan persyaratan pustaka.

- **Bisakah saya mengubah pembungkus LaTeX (`\begin{equation}`) ke sesuatu yang lain?**  
  Ya. Atur `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` lalu modifikasi `txtOptions.MathExportSettings` (tersedia pada rilis terbaru) untuk menyesuaikan delimiter.

- **Kekhawatiran performa untuk dokumen besar?**  
  Pustaka ini men‑stream output, sehingga penggunaan memori tetap wajar. Namun

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}