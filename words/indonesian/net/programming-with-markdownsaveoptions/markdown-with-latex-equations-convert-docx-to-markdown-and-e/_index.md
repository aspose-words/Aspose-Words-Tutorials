---
category: general
date: 2025-12-19
description: Panduan markdown dengan persamaan LaTeX – pelajari cara mengonversi docx
  ke markdown, mengekspor persamaan ke LaTeX, dan menyimpan gambar ke folder dengan
  nama unik menggunakan Aspose.Words dalam C#.
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: id
og_description: Tutorial markdown dengan persamaan LaTeX menunjukkan cara mengonversi
  DOCX ke markdown, mengekspor persamaan ke LaTeX, dan menghasilkan nama gambar unik
  untuk gambar yang disimpan.
og_title: markdown dengan persamaan LaTeX – Panduan Konversi C# Lengkap
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: 'markdown dengan persamaan LaTeX: Konversi DOCX ke Markdown dan Ekspor Gambar'
url: /id/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown dengan persamaan latex: Konversi DOCX ke Markdown dan Ekspor Gambar

Pernah membutuhkan **markdown dengan persamaan latex** tetapi tidak yakin bagaimana mengekstraknya dari file Word? Anda tidak sendirian—banyak pengembang mengalami masalah ini saat memindahkan dokumentasi dari Office ke generator situs statis.  

Dalam tutorial ini kami akan membahas solusi lengkap, end‑to‑end yang **mengonversi docx ke markdown**, **mengekspor persamaan ke latex**, dan **menyimpan gambar ke folder** dengan logika **menghasilkan nama gambar unik**, semuanya menggunakan Aspose.Words untuk .NET.  

Pada akhir tutorial Anda akan memiliki program C# siap‑jalankan yang menghasilkan file Markdown bersih, matematika siap‑LaTeX, dan direktori gambar yang rapi—tanpa perlu menyalin‑tempel secara manual.

## Apa yang Anda Butuhkan

- .NET 6 (atau runtime .NET terbaru)  
- Aspose.Words untuk .NET 23.10 atau lebih baru (paket NuGet `Aspose.Words`)  
- Contoh `input.docx` yang berisi teks biasa, objek Office Math, dan beberapa gambar  
- IDE pilihan Anda (Visual Studio, Rider, atau VS Code)  

Itu saja. Tidak ada pustaka tambahan, tidak ada alat baris perintah yang rumit—hanya C# murni.

## Langkah 1: Muat Dokumen dengan Aman (Mode Pemulihan)

Ketika Anda menangani file yang mungkin telah diedit oleh banyak orang, korupsi menjadi risiko nyata. Aspose.Words memungkinkan Anda mengaktifkan *RecoveryMode* sehingga pemuat mencoba memperbaiki bagian yang rusak alih‑alih melemparkan pengecualian.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**Mengapa ini penting:**  
Jika file sumber berisi node XML yang terselip atau aliran gambar yang rusak, mode pemulihan tetap akan memberikan objek `Document` yang dapat digunakan. Melewatkan langkah ini dapat menyebabkan crash keras, terutama di pipeline CI dimana Anda tidak mengontrol setiap unggahan.

> **Pro tip:** Saat memproses batch, bungkus pemuatan dalam `try/catch` dan catat setiap `DocumentCorruptedException` untuk inspeksi nanti.

## Langkah 2: Konversi DOCX ke Markdown dengan Persamaan LaTeX

Sekarang masuk ke inti tutorial: kami menginginkan **markdown dengan persamaan latex**. `MarkdownSaveOptions` milik Aspose.Words memungkinkan Anda menentukan `OfficeMathExportMode.LaTeX`, yang mengonversi setiap objek Office Math menjadi string LaTeX yang dibungkus dalam `$…$` atau `$$…$$`.

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

File `output_math.md` yang dihasilkan akan terlihat kira‑kira seperti:

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**Mengapa Anda menginginkannya:**  
Sebagian besar generator situs statis (Hugo, Jekyll, MkDocs) sudah memahami delimiter LaTeX ketika Anda mengaktifkan plugin MathJax atau KaTeX. Dengan mengekspor langsung ke LaTeX Anda menghindari langkah pasca‑pemrosesan yang sebaliknya memerlukan hack regex.

### Kasus Tepi

- **Persamaan kompleks:** Struktur bersarang yang sangat dalam tetap dapat dirender dengan benar, tetapi Anda mungkin perlu meningkatkan batas memori `MathRenderer` jika mengalami `OutOfMemoryException`.  
- **Konten campuran:** Jika sebuah paragraf mencampur teks biasa dan persamaan, Aspose.Words secara otomatis memisahkannya, mempertahankan markdown di sekitarnya.

## Langkah 3: Simpan Gambar ke Folder dengan Nama Unik

Jika dokumen Word Anda berisi gambar, Anda mungkin menginginkannya sebagai file gambar terpisah yang dapat direferensikan oleh markdown. `ResourceSavingCallback` pada `MarkdownSaveOptions` memberi Anda kontrol penuh atas cara setiap gambar ditulis.

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**Bagaimana markdown terlihat sekarang:**  

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**Mengapa menghasilkan nama unik?**  
Jika gambar yang sama muncul berkali‑kali, menggunakan nama asli akan menyebabkan penimpaan. Nama berbasis GUID menjamin setiap file bersifat unik, yang sangat berguna ketika Anda menjalankan konversi dalam pekerjaan paralel.

### Tips & Hal yang Perlu Diwaspadai

- **Kinerja:** Membuat GUID untuk setiap gambar menambah beban yang dapat diabaikan, tetapi jika Anda memproses ribuan gambar Anda dapat beralih ke hash deterministik (mis., SHA‑256 dari byte gambar).  
- **Format file:** `resource.Save` menulis gambar dalam format aslinya. Jika Anda memerlukan semua PNG, ganti `resource.Save(imageFile);` dengan `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));`.

## Langkah 4: Ekspor PDF dengan Bentuk Inline (Opsional)

Terkadang Anda masih memerlukan versi PDF dari dokumen yang sama, mungkin untuk tinjauan hukum. Menyetel `ExportFloatingShapesAsInlineTag` menjaga objek mengambang (seperti kotak teks) dalam PDF sebagai tag inline, mempertahankan kesetiaan tata letak.

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

Anda dapat melewatkan langkah ini jika output PDF bukan bagian dari alur kerja Anda—tidak ada yang rusak jika Anda mengabaikannya.

## Contoh Kerja Lengkap (Semua Langkah Digabungkan)

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi console. Ingat untuk mengganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif yang sebenarnya.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

Menjalankan program ini menghasilkan tiga file:

| File | Tujuan |
|------|---------|
| `output_math.md` | Markdown yang berisi persamaan siap‑LaTeX |
| `output_images.md` | Markdown dengan tautan gambar yang mengarah ke PNG dengan nama unik |
| `output_shapes.pdf` | Versi PDF yang mempertahankan bentuk mengambang sebagai tag inline (opsional) |

## Kesimpulan

Anda kini memiliki pipeline **markdown dengan persamaan latex** yang **mengonversi docx ke markdown**, **mengekspor persamaan ke latex**, dan **menyimpan gambar ke folder** sambil **menghasilkan nama gambar unik** untuk setiap gambar. Pendekatan ini sepenuhnya mandiri, bekerja dengan proyek .NET modern apa pun, dan hanya memerlukan paket NuGet Aspose.Words.

Apa selanjutnya? Cobalah memasukkan markdown yang dihasilkan ke dalam generator situs statis seperti Hugo, aktifkan MathJax, dan saksikan dokumentasi Anda bertransformasi dari format kantor tertutup menjadi situs web yang indah dan siap pakai. Butuh tabel? Aspose.Words juga mendukung `MarkdownSaveOptions.ExportTableAsHtml`, sehingga Anda dapat mempertahankan tata letak kompleks.

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}