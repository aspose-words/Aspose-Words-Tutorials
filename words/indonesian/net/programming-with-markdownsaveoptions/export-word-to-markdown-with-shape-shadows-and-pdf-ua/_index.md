---
category: general
date: 2026-03-28
description: Pelajari cara mengekspor Word ke markdown, menambahkan bayangan bentuk,
  dan menyimpan PDF/UA menggunakan Aspose.Words dalam C# – panduan langkah demi langkah.
draft: false
keywords:
- export word to markdown
- add shape shadow
- save pdf ua
- Aspose.Words markdown
- C# document conversion
language: id
og_description: Ekspor Word ke markdown, tambahkan bayangan bentuk, dan simpan PDF/UA
  dengan Aspose.Words di C#. Tutorial lengkap dengan kode dan tips.
og_title: Ekspor Word ke Markdown – Tambahkan Bayangan Bentuk & Simpan PDF/UA
tags:
- Aspose.Words
- C#
- Markdown
- PDF/UA
title: Ekspor Word ke Markdown dengan Bayangan Bentuk dan PDF/UA
url: /id/net/programming-with-markdownsaveoptions/export-word-to-markdown-with-shape-shadows-and-pdf-ua/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ekspor Word ke Markdown dengan Bayangan Bentuk dan PDF/UA

Pernahkah Anda perlu **mengekspor Word ke markdown** tetapi juga mempertahankan bayangan bentuk yang mewah dan tetap memenuhi kepatuhan PDF/UA? Anda tidak sendirian. Banyak pengembang mengalami kebuntuan ketika mencoba mempertahankan kesetiaan visual saat beralih format, terutama ketika aksesibilitas (PDF/UA) menjadi keharusan.

Dalam panduan ini kami akan membimbing Anda melalui contoh lengkap yang dapat dijalankan yang menunjukkan cara **mengekspor Word ke markdown**, **menambahkan bayangan bentuk** pada gambar, dan akhirnya **menyimpan PDF/UA** dengan bentuk mengambang dipaksa menjadi inline. Kami akan menggunakan Aspose.Words untuk .NET, yang merupakan perpustakaan utama untuk konversi dokumen yang kuat. Tanpa skrip eksternal, tanpa parser buatan sendiri—hanya kode C# bersih yang dapat Anda masukkan ke dalam aplikasi konsol hari ini.

> **Pro tip:** Jika Anda belum menginstal Aspose.Words, dapatkan paket NuGet terbaru (`Install-Package Aspose.Words`) – ia bekerja dengan .NET 6+, .NET Framework 4.8, dan bahkan .NET Core.

## Apa yang Anda Butuhkan

- **Visual Studio 2022** (atau IDE apa pun yang mendukung .NET 6+)
- **Aspose.Words for .NET** (versi NuGet 23.8 atau lebih baru)
- Contoh `input.docx` yang berisi setidaknya satu bentuk (mis., persegi panjang)
- Pengetahuan dasar C# – kami akan menjaga sintaks sederhana

Setelah prasyarat tersebut terpenuhi, mari kita mulai.

![Diagram menunjukkan alur ekspor word ke markdown](export_word_to_markdown_diagram.png){alt="contoh ekspor word ke markdown"}

## Langkah 1: Muat Dokumen Word dalam Recovery Mode  

Sebelum kita dapat memodifikasi apa pun, kita memerlukan dokumen dalam memori. Memuat dengan **RecoveryMode.Recover** menangkap semua peringatan substitusi font, yang berguna ketika sumber menggunakan font yang tidak Anda miliki.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

// 1️⃣ Load the document while collecting warnings
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover,
    WarningCallback = new WarningInfoCollection()
};

Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Mengapa RecoveryMode?*  
Jika file asli merujuk pada font yang hilang, Aspose akan menggantinya dan mengeluarkan peringatan. Dengan menangkap peringatan tersebut kita dapat mencatatnya nanti—berguna untuk debugging dan laporan kepatuhan.

## Langkah 2: Tambahkan Bayangan Bentuk  

Setelah dokumen dimuat, mari tingkatkan tampilan sebuah bentuk. Kami akan mengambil node `Shape` pertama dan mengaktifkan bayangan jatuh yang halus.

```csharp
// 2️⃣ Find the first shape and enable its shadow
Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
shape.ShadowFormat.Visible = true;
shape.ShadowFormat.BlurRadius = 4;   // soft edges
shape.ShadowFormat.Distance = 2;    // how far the shadow is from the shape
shape.ShadowFormat.Angle = 30;      // direction of the light source
```

*Mengapa mengubah bayangan?*  
Bayangan menambah kedalaman, membuat bentuk menonjol baik di Word maupun gambar markdown yang diekspor (jika Anda kemudian mengonversi bentuk menjadi gambar). Ini juga cara cepat untuk menguji bahwa properti visual bertahan melalui pipeline konversi.

## Langkah 3: Ekspor Dokumen ke Markdown (dengan LaTeX Math)  

Aspose.Words dapat mengubah file Word menjadi markdown bersih. Di sini kami juga memberi tahu untuk mengekspor semua persamaan OfficeMath sebagai LaTeX, yang merupakan standar de‑facto untuk dokumen ilmiah.

```csharp
// 3️⃣ Configure markdown export options
var markdownOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Store all extracted images in a dedicated folder
    ResourceSavingCallback = (s, e) =>
    {
        string assetsFolder = "YOUR_DIRECTORY/assets";
        Directory.CreateDirectory(assetsFolder);
        e.FileName = Path.Combine(assetsFolder, e.FileName);
    }
};

// Save as markdown
doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

*Apa yang akan Anda lihat:*  
- File `output.md` dengan sintaks markdown standar.  
- Semua gambar tersemat (termasuk bentuk yang baru saja kami beri bayangan) disimpan di bawah `assets/`.  
- Semua persamaan muncul sebagai blok LaTeX `$…$`, siap dirender oleh MathJax atau KaTeX.

## Langkah 4: Simpan Dokumen yang Sama sebagai PDF/UA  

PDF/UA (PDF/Universal Accessibility) memastikan PDF memenuhi ISO 14289‑1. Kami juga akan memaksa bentuk mengambang disimpan sebagai tag inline, yang menyederhanakan penandaan aksesibilitas.

```csharp
// 4️⃣ Set up PDF/UA compliance and inline floating shapes
var pdfOptions = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfUAX2,
    ExportFloatingShapesAsInlineTag = true
};

// Save the PDF/UA file
doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Mengapa PDF/UA?*  
Jika audiens Anda mencakup pengguna pembaca layar atau Anda perlu memenuhi standar aksesibilitas hukum, PDF/UA adalah pilihan yang tepat. Flag `ExportFloatingShapesAsInlineTag` mencegah objek mengambang mengganggu urutan bacaan logis.

## Langkah 5: Tinjau Peringatan Substitusi Font  

Setelah langkah konversi, merupakan praktik yang baik untuk menampilkan semua peringatan terkait font yang kami tangkap di **Langkah 1**.

```csharp
// 5️⃣ List font‑substitution warnings (if any)
var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
foreach (var warning in warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"⚠️ {warning.Description}");
}
```

Jika Anda melihat pesan seperti *“Font 'Calibri' digantikan dengan 'Arial'”* Anda kini tahu persis font mana yang hilang dan dapat memutuskan apakah akan menyematkan pengganti atau menyertakan font yang hilang bersama aplikasi Anda.

## Contoh Lengkap yang Berfungsi  

Menggabungkan semuanya, berikut program lengkap yang dapat Anda salin‑tempel ke dalam proyek konsol baru:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load with recovery mode and capture warnings
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Recover,
            WarningCallback = new WarningInfoCollection()
        };
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Add a shadow to the first shape
        Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.BlurRadius = 4;
        shape.ShadowFormat.Distance = 2;
        shape.ShadowFormat.Angle = 30;

        // Export to Markdown with LaTeX math and custom assets folder
        var markdownOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = (s, e) =>
            {
                string assetsFolder = "YOUR_DIRECTORY/assets";
                Directory.CreateDirectory(assetsFolder);
                e.FileName = Path.Combine(assetsFolder, e.FileName);
            }
        };
        doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);

        // Save as PDF/UA, forcing floating shapes inline
        var pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUAX2,
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // Print any font‑substitution warnings
        var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
        foreach (var warning in warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ {warning.Description}");
        }
    }
}
```

### Hasil yang Diharapkan  

- `output.md` berisi markdown bersih, persamaan berformat LaTeX, dan tautan gambar seperti `![Shape](assets/shape0.png)`.  
- `output.pdf` adalah file yang mematuhi PDF/UA dan lulus pemeriksaan aksesibilitas Adobe Acrobat.  
- Output konsol menampilkan semua peringatan substitusi font, membantu Anda melacak font yang hilang.

## Pertanyaan Umum & Kasus Tepi  

**Bagaimana jika dokumen saya memiliki banyak bentuk?**  
Lakukan iterasi melalui `doc.GetChildNodes(NodeType.Shape, true)` dan terapkan pengaturan bayangan ke setiap elemen.  

**Bisakah saya mengubah warna bayangan?**  
Ya—atur `shape.ShadowFormat.Color = Color.Gray;` sebelum menyimpan.  

**Apakah saya perlu menyesuaikan path folder assets untuk penyebaran web?**  
Tentu saja. Gunakan path relatif atau konfigurasikan URL CDN dalam `ResourceSavingCallback` untuk melayani gambar secara efisien.  

**Apakah ekspor markdown akan kehilangan fitur khusus Word?**  
Fitur seperti perubahan yang dilacak, komentar, atau SmartArt kompleks tidak terwakili dalam markdown. Jika Anda memerlukannya, simpan versi PDF/UA sebagai cadangan.

## Kesimpulan  

Anda baru saja mempelajari cara **mengekspor Word ke markdown**, **menambahkan bayangan bentuk**, dan **menyimpan PDF/UA** menggunakan Aspose.Words dalam C#. Contoh kode lengkap menunjukkan alur kerja siap produksi yang menangani peringatan font, manajemen sumber daya, dan kepatuhan aksesibilitas—semuanya dalam satu skrip yang mudah dibaca.

Langkah selanjutnya? Coba ubah parameter bayangan, bereksperimen dengan `MarkdownSaveOptions` yang berbeda (mis., `ExportImagesAsBase64`), atau integrasikan pipeline ini ke dalam API ASP.NET Core yang mengonversi file Word yang diunggah pengguna secara langsung. Dan jika Anda penasaran dengan format output lain, lihat opsi ekspor **HTML**, **EPUB**, atau **TIFF** dari Aspose—masing‑masing mengikuti pola serupa.

Selamat coding, dan semoga dokumen Anda selalu ditampilkan persis seperti yang Anda inginkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}