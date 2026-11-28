---
category: general
date: 2026-02-24
description: Pelajari cara menggunakan Aspose Load Options untuk memulihkan DOCX yang
  rusak, mengonversi docx ke markdown, dan mengonversi Word ke PDF dengan persamaan
  LaTeX.
draft: false
keywords:
- aspose load options
- convert docx to markdown
- convert word to pdf
- recover corrupted docx
- export equations as latex
language: id
og_description: Kuasi Opsi Muat Aspose untuk memulihkan DOCX yang rusak, mengonversi
  docx ke markdown, dan mengekspor persamaan sebagai LaTeX sambil menghasilkan file
  PDF/UA‑2.
og_title: Opsi Muat Aspose – Konversi DOCX ke Markdown & PDF
tags:
- Aspose.Words
- C#
- Document Conversion
title: Opsi Muat Aspose – Konversi DOCX ke Markdown & PDF
url: /id/net/programming-with-loadoptions/aspose-load-options-convert-docx-to-markdown-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – Mengonversi DOCX ke Markdown & PDF

Pernah bertanya-tanya bagaimana **aspose load options** memungkinkan Anda menyelamatkan file Word yang rusak dan mengubahnya menjadi Markdown bersih atau PDF yang sesuai? Anda tidak sendirian. Banyak pengembang mengalami masalah ketika DOCX datang dalam keadaan korup, atau ketika persamaan menghilang selama konversi. Dalam tutorial ini kami akan membahas solusi C# lengkap yang siap dijalankan yang tidak hanya *memulihkan docx yang rusak* tetapi juga **mengonversi docx ke markdown** dan **mengonversi word ke pdf** sambil **mengekspor persamaan sebagai latex**.

Kami akan membahas semuanya mulai dari menyiapkan mode pemulihan hingga mengunggah gambar yang diekstrak ke bucket cloud, dan akhirnya menghasilkan file PDF/UA‑2 yang memenuhi standar aksesibilitas. Pada akhir tutorial, Anda akan memiliki satu basis kode yang menangani kedua transformasi dengan hanya beberapa baris konfigurasi.

> **Apa yang akan Anda dapatkan:**  
> • Cara yang kuat untuk memuat DOCX apa pun, bahkan jika sebagian rusak.  
> • Output Markdown yang mempertahankan persamaan OfficeMath sebagai LaTeX.  
> • Output PDF/UA‑2 dengan bentuk mengambang (floating shapes) dipertahankan sebagai tag inline.  
> • Callback unggah gambar yang dapat digunakan kembali untuk penyimpanan cloud.

---

## Prerequisites

- **Aspose.Words for .NET** (v23.12 atau lebih baru).  
- .NET 6+ (SDK terbaru apa pun).  
- SDK penyimpanan cloud pilihan Anda (contoh menggunakan metode placeholder).  
- Familiaritas dasar dengan C# dan Visual Studio atau VS Code.

Jika Anda belum menginstal Aspose.Words, jalankan:

```bash
dotnet add package Aspose.Words
```

---

## Step 1: Load the Document with Aspose Load Options

Hal pertama yang Anda butuhkan adalah cara yang dapat diandalkan untuk membuka DOCX yang mungkin rusak. Di sinilah **aspose load options** bersinar—mereka memungkinkan Anda memberi tahu perpustakaan untuk mencoba pemulihan alih-alih melempar pengecualian.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Configure LoadOptions to recover corrupted documents.
LoadOptions loadOptions = new LoadOptions
{
    // RecoveryMode.Recover tells Aspose to salvage as much as possible.
    RecoveryMode = RecoveryMode.Recover
};

// Load the source file. Replace the path with your own.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Mengapa ini penting:**  
Ketika file Word terpotong atau berisi XML yang tidak valid, pemuat default akan menghentikan proses. Dengan mengaktifkan `RecoveryMode.Recover`, Aspose akan mem-parsing apa yang dapat diproses, melewati bagian yang rusak, dan tetap memberikan objek `Document` yang dapat digunakan. Inilah tulang punggung skenario *recover corrupted docx*.

---

## Step 2: Set Up Markdown Conversion (Export Equations as LaTeX)

Sekarang dokumen sudah berada di memori, kita dapat mengonfigurasi cara menyimpannya sebagai Markdown. Dua hal sangat penting:

1. **OfficeMathExportMode.LaTeX** – memastikan setiap persamaan matematika menjadi potongan LaTeX, mempertahankan semantik mereka.  
2. **ResourceSavingCallback** – hook yang memungkinkan kita mengunggah gambar yang diekstrak ke bucket cloud alih-alih menulisnya secara lokal.

```csharp
using Aspose.Words.Saving;

// Prepare Markdown save options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This converts OfficeMath objects to LaTeX.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Hook to upload images to the cloud.
    ResourceSavingCallback = new CloudImageCallback()
};

// Save as Markdown.
document.Save("YOUR_DIRECTORY/result.md", markdownOptions);
```

**Tips profesional:** Jika Anda tidak memerlukan LaTeX, ubah `OfficeMathExportMode` menjadi `Image`. Namun untuk dokumen ilmiah, LaTeX jauh lebih portabel.

---

## Step 3: Implement the Cloud Image Callback

Aspose memanggil `IResourceSavingCallback.ResourceSaving` untuk setiap sumber daya eksternal (gambar, diagram, dll.). Di bawah ini adalah implementasi minimal yang berpura‑pura mengunggah stream ke CDN dan mengembalikan URL publik.

```csharp
using Aspose.Words.Saving;
using System.IO;

public class CloudImageCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Upload the image stream to your cloud storage and get a URL.
        string url = UploadToCloud(args.Stream, args.FileName);

        // Point the Markdown image reference to the CDN URL.
        args.Uri = url;

        // Prevent Aspose from writing a local copy.
        args.KeepOriginalDocumentUri = false;
    }

    private string UploadToCloud(Stream data, string name)
    {
        // Replace this stub with your actual SDK call.
        // For demo purposes we just return a placeholder.
        return $"https://cdn.example.com/{name}";
    }
}
```

**Bagaimana jika Anda tidak memiliki bucket cloud?**  
Anda cukup mengatur `args.Uri = $"images/{args.FileName}"` dan membiarkan Aspose menulis file di samping file Markdown. Callback memberi Anda kontrol penuh.

---

## Step 4: Configure PDF Conversion (Convert Word to PDF with UA‑2 Compliance)

Ketika dokumen yang sama perlu menjadi PDF, terutama yang harus memenuhi standar aksesibilitas, Aspose menyediakan `PdfSaveOptions`. Dua pengaturan penting untuk konversi bersih:

- **Compliance = PdfCompliance.PdfUa2** – menghasilkan file PDF/UA‑2, standar ISO untuk PDF yang dapat diakses.  
- **ExportFloatingShapesAsInlineTag = true** – mempertahankan bentuk mengambang (seperti text box) dalam urutan yang benar.

```csharp
using Aspose.Words.Saving;

// Prepare PDF save options.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // Enforce PDF/UA‑2 compliance.
    Compliance = PdfCompliance.PdfUa2,

    // Preserve layout of floating shapes.
    ExportFloatingShapesAsInlineTag = true
};

// Save as PDF.
document.Save("YOUR_DIRECTORY/result.pdf", pdfOptions);
```

**Mengapa ini berhasil:**  
Menetapkan `Compliance` membuat Aspose menyisipkan tag, teks alternatif, dan elemen struktur yang diperlukan. Flag `ExportFloatingShapesAsInlineTag` memastikan bahwa bentuk yang biasanya mengambang di atas teks di‑anchor secara inline, mencegah kejutan tata letak pada PDF akhir.

---

## Step 5: Full End‑to‑End Example

Menggabungkan semuanya, berikut program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Saving;

namespace AsposeDocxConversion
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load with recovery.
            LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 2️⃣ Convert to Markdown (export equations as LaTeX, upload images).
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                ResourceSavingCallback = new CloudImageCallback()
            };
            doc.Save("YOUR_DIRECTORY/result.md", mdOptions);
            Console.WriteLine("✅ Markdown saved.");

            // 3️⃣ Convert to PDF/UA‑2 (preserve floating shapes).
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                Compliance = PdfCompliance.PdfUa2,
                ExportFloatingShapesAsInlineTag = true
            };
            doc.Save("YOUR_DIRECTORY/result.pdf", pdfOptions);
            Console.WriteLine("✅ PDF/UA‑2 saved.");
        }
    }

    // Callback for uploading images.
    public class CloudImageCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string url = UploadToCloud(args.Stream, args.FileName);
            args.Uri = url;
            args.KeepOriginalDocumentUri = false;
        }

        private string UploadToCloud(Stream data, string name)
        {
            // Insert real SDK code here.
            return $"https://cdn.example.com/{name}";
        }
    }
}
```

**Output yang diharapkan:**  
Menjalankan program akan membuat dua file di `YOUR_DIRECTORY`:

- `result.md` – dokumen Markdown di mana setiap persamaan muncul sebagai `$$\LaTeX$$` dan tautan gambar mengarah ke `https://cdn.example.com/...`.  
- `result.pdf` – file PDF/UA‑2 yang mematuhi standar dan dapat dibuka di Adobe Reader dengan pemeriksa aksesibilitas lulus.

Anda dapat membuka Markdown di editor apa pun atau menggunakannya pada generator situs statis, dan PDF dapat didistribusikan kepada pengguna yang memerlukan format yang dapat diakses.

---

## Frequently Asked Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **What if the DOCX is completely unreadable?** | Bahkan dengan `RecoveryMode.Recover`, file yang sangat korup dapat melempar `FileCorruptedException`. Bungkus pemanggilan load dalam `try/catch` dan tampilkan halaman error yang ramah pengguna. |
| **Can I change the image format during upload?** | Ya. Di dalam `UploadToCloud` Anda dapat menggunakan pustaka pemrosesan gambar (mis. ImageSharp) untuk mengubah ukuran atau mengonversi ke WebP sebelum mengirim ke CDN. |
| **Do I need a license for Aspose.Words?** | Versi trial gratis berfungsi hingga 20 halaman. Untuk produksi, lisensi komersial menghilangkan watermark evaluasi dan membuka semua fitur. |
| **What if I want to keep equations as images instead of LaTeX?** | Ganti `OfficeMathExportMode` menjadi `Image` pada `MarkdownSaveOptions`. Callback kemudian akan menerima stream PNG yang dapat Anda unggah. |
| **How do I add custom metadata to the PDF?** | Gunakan `pdfOptions.CustomProperties.Add("Author", "Your Name")` sebelum memanggil `Save`. |

---

## 🎯 Wrap‑Up

Kami baru saja menunjukkan bagaimana **aspose load options** memberi Anda kemampuan untuk **recover corrupted docx**, **convert docx to markdown**, dan **convert word to pdf** sambil **export equations as latex**. Pendekatannya modular: Anda dapat mengganti callback unggah gambar, mengubah tingkat kepatuhan, atau bahkan menambahkan langkah DOCX‑to‑HTML dengan opsi serupa.

Langkah selanjutnya yang dapat Anda eksplorasi:

- Integrasikan pipeline ini ke dalam API ASP .NET Core sehingga pengguna dapat mengunggah file dan menerima Markdown serta PDF secara instan.  
- Ganti URL CDN placeholder dengan panggilan SDK Azure Blob Storage atau Amazon S3.  
- Tambahkan langkah pasca‑pemrosesan yang menjalankan linter Markdown untuk memastikan output bersih.  

Silakan bereksperimen—mungkin Anda akan menambahkan ekspor tabel‑to‑CSV atau footer PDF khusus. API Aspose.Words cukup fleksibel untuk sebagian besar skenario otomatisasi dokumen.

**Selamat coding!** Jika Anda mengalami kendala, tinggalkan komentar di bawah atau sapa forum komunitas Aspose.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}