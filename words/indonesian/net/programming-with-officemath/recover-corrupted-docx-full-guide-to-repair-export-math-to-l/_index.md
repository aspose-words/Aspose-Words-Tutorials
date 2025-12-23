---
category: general
date: 2025-12-23
description: Pelajari cara memulihkan file docx yang rusak, menggunakan mode pemulihan,
  mengekspor persamaan ke LaTeX, dan menghasilkan nama gambar unik dalam C#. Kode
  langkah demi langkah dengan penjelasan.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: id
og_description: Pulihkan file docx yang rusak, gunakan mode pemulihan, ekspor persamaan
  ke LaTeX, dan hasilkan nama gambar unik dengan Aspose.Words di C#.
og_title: Pulihkan docx yang rusak – Tutorial C# Lengkap
tags:
- Aspose.Words
- C#
- Document Recovery
title: Pulihkan docx yang rusak – Panduan Lengkap untuk Memperbaiki, Mengekspor Matematika
  ke LaTeX & Menghasilkan Nama Gambar Unik
url: /id/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# memulihkan docx yang rusak – Panduan Lengkap untuk Memperbaiki, Mengekspor Math ke LaTeX & Menghasilkan Nama Gambar Unik

Pernah membuka **.docx** yang tidak dapat dimuat karena rusak? Anda tidak sendirian. Dalam banyak proyek dunia nyata, file Word yang rusak dapat menghentikan seluruh alur kerja, tetapi kabar baiknya adalah Anda dapat **memulihkan docx yang rusak** secara programatis.  

Dalam tutorial ini kami akan menelusuri langkah‑langkah tepat untuk **memulihkan docx yang rusak**, menunjukkan **cara menggunakan mode pemulihan**, mendemonstrasikan **ekspor persamaan ke LaTeX**, dan akhirnya **menghasilkan nama gambar unik** saat menyimpan ke Markdown. Pada akhir tutorial Anda akan memiliki satu program C# yang dapat dijalankan dan menangani semua tugas ini tanpa masalah.

## Prerequisites

- .NET 6 atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.6+).  
- Aspose.Words for .NET (versi trial gratis atau berlisensi). Instal via NuGet:

```bash
dotnet add package Aspose.Words
```

- Familiaritas dasar dengan C# dan I/O file.  
- File `corrupt.docx` yang rusak untuk diuji (Anda dapat mensimulasikan kerusakan dengan memotong file yang valid).

> **Pro tip:** Simpan cadangan file asli sebelum memulai—pemulihan bersifat destruktif hanya jika Anda menimpa sumbernya.

## Step 1 – Recover the corrupted DOCX using Recovery Mode

Hal pertama yang harus kita lakukan adalah memberi tahu Aspose.Words untuk memperlakukan file yang masuk sebagai kemungkinan rusak. Di sinilah **cara menggunakan mode pemulihan** berperan.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**Mengapa ini penting:**  
Ketika `RecoveryMode.Recover` diaktifkan, Aspose.Words berusaha membangun kembali pohon dokumen internal, melewati bagian yang tidak dapat dibaca sambil mempertahankan sebanyak mungkin konten. Tanpa mode ini, konstruktor `Document` akan melemparkan pengecualian dan Anda akan kehilangan kesempatan untuk menyelamatkan file.

> **Bagaimana jika file tidak dapat diperbaiki?**  
> Perpustakaan tetap akan mengembalikan objek `Document`, tetapi beberapa node mungkin hilang. Anda dapat memeriksa `doc.GetChildNodes(NodeType.Any, true).Count` untuk melihat berapa banyak elemen yang bertahan.

## Step 2 – Export Office Math equations to LaTeX when saving as Markdown

Banyak dokumen teknis berisi persamaan yang ditulis dengan Office Math. Jika Anda memerlukan persamaan tersebut dalam LaTeX—misalnya, untuk dipublikasikan di blog ilmiah—Anda dapat meminta Aspose.Words melakukan konversi untuk Anda.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**Cara kerjanya:**  
`OfficeMathExportMode.LaTeX` memberi tahu saver untuk mengganti setiap node `OfficeMath` dengan representasi LaTeX‑nya yang dibungkus dalam `$…$` (inline) atau `$$…$$` (display). File Markdown yang dihasilkan dapat langsung diproses oleh generator situs statis seperti Hugo atau Jekyll.

> **Kasus tepi:** Jika dokumen asli berisi objek persamaan kompleks (misalnya, matriks), konversi LaTeX mungkin menghasilkan output multi‑baris. Tinjau file `.md` yang dihasilkan untuk memastikan formatnya sesuai harapan.

## Step 3 – Save the document as PDF while controlling floating shape tags

Kadang‑kadang Anda membutuhkan versi PDF dari dokumen yang sama, tetapi Anda juga peduli bagaimana bentuk mengambang (gambar, kotak teks) ditandai untuk aksesibilitas. Flag `ExportFloatingShapesAsInlineTag` memberi Anda kontrol tersebut.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**Mengapa mengubah flag ini?**  
- `true` → Bentuk mengambang menjadi tag `<Figure>`, yang banyak pembaca layar perlakukan sebagai gambar terpisah dengan caption.  
- `false` → Bentuk dibungkus dalam tag `<Div>` generik, yang mungkin diabaikan oleh teknologi bantu. Pilih sesuai kebutuhan aksesibilitas Anda.

## Step 4 – Export to Markdown with custom image handling (generate unique image names)

Saat Anda menyimpan dokumen Word ke Markdown, semua gambar yang disisipkan ditulis ke disk. Secara default mereka menerima nama file asli, yang dapat menyebabkan benturan jika Anda memproses banyak dokumen dalam folder yang sama. Mari kita kaitkan proses penyimpanan dan **menghasilkan nama gambar unik** secara otomatis.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**Apa yang terjadi di balik layar?**  
`ResourceSavingCallback` dipanggil untuk setiap sumber eksternal (gambar, SVG, dll.) selama operasi penyimpanan. Dengan mengembalikan jalur lengkap, Anda menentukan di mana file disimpan dan apa namanya. GUID memastikan **menghasilkan nama gambar unik** tanpa harus mengelola secara manual.

> **Tip:** Jika Anda memerlukan skema penamaan deterministik (misalnya berdasarkan teks alt gambar), ganti `Guid.NewGuid()` dengan hash dari `resourceInfo.Name`.

## Full Working Example

Menggabungkan semuanya, berikut program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### Expected Output

Menjalankan program seharusnya menghasilkan pesan konsol serupa dengan:

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

Anda akan menemukan tiga file:

| File | Tujuan |
|------|--------|
| `out.md` | Markdown di mana setiap persamaan Office Math muncul sebagai LaTeX (`$…$` atau `$$…$$`). |
| `out.pdf` | Versi PDF dengan bentuk mengambang ditandai sebagai `<Figure>` untuk aksesibilitas yang lebih baik. |
| `out2.md` + `md_images\*` | Markdown plus folder berisi file gambar dengan nama unik (berbasis GUID). |

## Frequently Asked Questions & Edge Cases

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika file yang rusak tidak memiliki konten yang dapat dipulihkan?** | Aspose.Words tetap akan mengembalikan objek `Document`, tetapi mungkin kosong. Periksa `doc.GetChildNodes(NodeType.Paragraph, true).Count` sebelum melanjutkan. |
| **Bisakah saya mengubah delimiter LaTeX?** | Ya—atur `markdownMathOptions.MathDelimiter = "$$"` untuk memaksa delimiter gaya tampilan. |
| **Apakah saya perlu membuang (dispose) objek `Document`?** | Kelas `Document` mengimplementasikan `IDisposable`. Bungkus dalam blok `using` jika Anda memproses banyak file untuk membebaskan sumber daya native dengan cepat. |
| **Bagaimana cara mempertahankan nama file gambar asli?** | Kembalikan `Path.Combine(imageFolder, resourceInfo.Name)` di dalam callback. Ingat risiko benturan nama. |
| **Apakah pendekatan GUID aman untuk repositori yang dikontrol versi?** | GUID stabil antar run, tetapi tidak mudah dibaca manusia. Jika Anda memerlukan nama yang dapat direproduksi, hash nama asli ditambah salt proyek secara keseluruhan. |

## Conclusion

Kami telah menunjukkan cara **memulihkan docx yang rusak**, mendemonstrasikan **cara menggunakan

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}