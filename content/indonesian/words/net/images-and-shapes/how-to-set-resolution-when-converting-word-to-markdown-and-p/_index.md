---
category: general
date: 2025-12-17
description: Cara mengatur resolusi untuk ekspor gambar saat mengonversi Word ke Markdown
  dan PDF. Pelajari cara memulihkan file Word yang rusak, memuat docx, dan mengonversi
  docx ke PDF dengan Aspose.Words.
draft: false
keywords:
- how to set resolution
- convert word to markdown
- recover corrupted word
- convert docx to pdf
- how to load docx
language: id
og_description: Cara mengatur resolusi ekspor gambar saat mengonversi dokumen Word.
  Panduan ini menunjukkan cara memulihkan file Word yang rusak, memuat docx, dan mengonversi
  ke Markdown serta PDF.
og_title: Cara Mengatur Resolusi – Panduan Word ke Markdown & PDF
tags:
- Aspose.Words
- C#
- Document Conversion
title: Cara Mengatur Resolusi Saat Mengonversi Word ke Markdown dan PDF – Panduan
  Lengkap
url: /indonesian/net/images-and-shapes/how-to-set-resolution-when-converting-word-to-markdown-and-p/
---

{{< layout-start >}}

{{< layout-start >}}

# Cara Mengatur Resolusi Saat Mengonversi Word ke Markdown dan PDF

Pernah bertanya-tanya **bagaimana cara mengatur resolusi** untuk gambar yang diekstrak dari dokumen Word? Mungkin Anda sudah mencoba ekspor cepat, hanya untuk mendapatkan gambar yang buram di Markdown atau PDF Anda. Itu adalah masalah umum, terutama ketika file `.docx` sumber agak rusak atau bahkan sebagian terkorupsi.

Dalam tutorial ini kita akan membahas solusi lengkap, end‑to‑end yang **memulihkan file Word yang korup**, **memuat docx**, lalu **mengonversi Word ke Markdown** (dengan gambar beresolusi tinggi) dan **mengonversi docx ke PDF** sambil memperhatikan aksesibilitas. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat dipakai ulang di proyek .NET apa pun—tidak lagi menebak DPI gambar atau sumber daya yang hilang.

> **Ringkasan cepat:** kami akan menggunakan Aspose.Words untuk .NET, mengatur resolusi gambar 300 dpi, mengekspor OfficeMath sebagai LaTeX, dan menghasilkan file yang sesuai dengan PDF‑/UA. Semua ini terjadi dalam beberapa baris kode C#.

---

## Apa yang Anda Butuhkan

- **Aspose.Words untuk .NET** (v23.10 atau lebih baru). Paket NuGet‑nya adalah `Aspose.Words`.
- .NET 6+ (kode ini juga bekerja pada .NET Framework 4.7.2, namun runtime yang lebih baru memberikan kinerja yang lebih baik).
- Sebuah file `.docx` **yang korup atau sebagian rusak** yang ingin Anda selamatkan, atau file Word biasa jika Anda hanya membutuhkan gambar beresolusi tinggi.
- Sebuah folder kosong tempat Markdown, gambar, dan PDF akan disimpan.  
  *(Silakan ubah jalur pada contoh bila diperlukan.)*

---

## Langkah 1 – Cara Memuat DOCX dan Memulihkan File Word yang Korup

Hal pertama yang harus Anda lakukan adalah **memuat DOCX** dengan aman. Aspose.Words menyediakan flag `RecoveryMode` yang memberi tahu perpustakaan untuk mengabaikan bagian yang korup alih‑alih melempar pengecualian.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// Load the potentially corrupted document using recovery mode
LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.IgnoreCorrupt };
Document document = new Document("YOUR_DIRECTORY/corrupt.docx", loadOptions);
```

> **Mengapa ini penting:** Jika Anda melewatkan `RecoveryMode`, satu paragraf yang rusak dapat menghentikan seluruh proses konversi. `IgnoreCorrupt` memungkinkan parser melewati bagian yang buruk dan mempertahankan sisa konten—sempurna untuk skenario “memulihkan Word yang korup”.

---

## Langkah 2 – Cara Mengatur Resolusi untuk Ekspor Gambar Saat Mengonversi Word ke Markdown

Setelah dokumen berada di memori, kita perlu memberi tahu Aspose.Words seberapa tajam gambar yang diekstrak. Di sinilah **cara mengatur resolusi** berperan.

```csharp
// Prepare Markdown export options
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // Export OfficeMath as LaTeX for better compatibility with Markdown renderers
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Set a higher image resolution (300 DPI works well for most screens and print)
    ImageResolution = 300,

    // Store generated images in a dedicated folder and return the relative path
    ResourceSavingCallback = resourceInfo =>
    {
        string imageFolder = Path.Combine("YOUR_DIRECTORY/md_images");
        Directory.CreateDirectory(imageFolder); // Ensure folder exists
        string imagePath = Path.Combine(imageFolder, resourceInfo.FileName);
        File.WriteAllBytes(imagePath, resourceInfo.Content);
        // Return the path that will be written into the Markdown file
        return Path.Combine("md_images", resourceInfo.FileName);
    }
};
```

### Apa yang Dilakukan Kode Ini

| Pengaturan | Mengapa Membantu |
|------------|------------------|
| `OfficeMathExportMode = LaTeX` | Persamaan matematika dirender bersih di sebagian besar penampil Markdown. |
| `ImageResolution = 300` | Gambar 300 dpi cukup tajam untuk PDF dan tetap menjaga ukuran file tetap wajar. |
| `ResourceSavingCallback` | Memberi Anda kontrol penuh atas tempat penyimpanan gambar; Anda bahkan dapat mengunggahnya ke CDN nanti. |

> **Tip pro:** Jika Anda memerlukan kualitas ultra‑tinggi untuk pencetakan, naikkan DPI menjadi 600. Ingat saja ukuran file akan bertambah secara proporsional.

---

## Langkah 3 – Mengonversi Word ke Markdown (dan Memverifikasi Output)

Dengan opsi‑opsi sudah siap, konversi sebenarnya cukup satu baris kode.

```csharp
// Save the document as Markdown
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

Setelah kode ini dijalankan, Anda akan menemukan:

- `output.md` yang berisi teks Markdown dengan tautan gambar seperti `![](md_images/Image_0.png)`.
- Sebuah folder `md_images` yang berisi file PNG dengan resolusi 300 dpi.

Buka file Markdown di VS Code atau penampil apa pun untuk memastikan gambar terlihat tajam dan persamaan muncul sebagai blok LaTeX.

---

## Langkah 4 – Cara Mengonversi DOCX ke PDF dengan Memperhatikan Aksesibilitas

Jika Anda juga memerlukan versi PDF, Aspose.Words memungkinkan Anda mengatur kepatuhan PDF (PDF/UA untuk aksesibilitas) dan mengontrol cara penanganan bentuk mengambang.

```csharp
// Configure PDF export for accessibility
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // PDF/UA ensures the file meets accessibility standards
    Compliance = PdfCompliance.PdfUa,

    // Export floating shapes as inline <span> tags for better screen‑reader support
    ExportFloatingShapesAsInlineTag = true
};

// Save the document as PDF
document.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

### Mengapa PDF/UA?

PDF/UA (Universal Accessibility) menandai PDF dengan informasi struktur yang dibutuhkan teknologi bantu. Jika audiens Anda mencakup orang yang menggunakan pembaca layar, flag ini wajib ada.

---

## Langkah 5 – Contoh Lengkap yang Siap Pakai (Copy‑Paste)

Berikut adalah program lengkap yang menyatukan semua langkah. Silakan tempelkan ke aplikasi console dan jalankan.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the document (recover corrupted word) ----------
        LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.IgnoreCorrupt };
        Document doc = new Document("YOUR_DIRECTORY/corrupt.docx", loadOptions);

        // ---------- Step 2: Set resolution for Markdown image export ----------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ImageResolution = 300,
            ResourceSavingCallback = info =>
            {
                string imgFolder = Path.Combine("YOUR_DIRECTORY/md_images");
                Directory.CreateDirectory(imgFolder);
                string imgPath = Path.Combine(imgFolder, info.FileName);
                File.WriteAllBytes(imgPath, info.Content);
                // Relative path used inside the Markdown file
                return Path.Combine("md_images", info.FileName);
            }
        };

        // ---------- Step 3: Save as Markdown ----------
        doc.Save("YOUR_DIRECTORY/output.md", mdOptions);
        Console.WriteLine("Markdown export completed.");

        // ---------- Step 4: Configure PDF export (convert docx to pdf) ----------
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUa,
            ExportFloatingShapesAsInlineTag = true
        };

        // ---------- Step 5: Save as PDF ----------
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
        Console.WriteLine("PDF export completed.");
    }
}
```

**Hasil yang Diharapkan**

- `output.md` – file Markdown bersih dengan gambar PNG beresolusi tinggi.
- `md_images/` – folder yang berisi PNG 300 dpi.
- `output.pdf` – file PDF/UA yang dapat dibuka di Adobe Reader tanpa peringatan.

---

## Pertanyaan Umum & Kasus Pinggir

### Bagaimana jika DOCX sumber berisi gambar EMF atau WMF yang tertanam?
Aspose.Words secara otomatis merasterisasi format vektor tersebut menggunakan DPI yang Anda tentukan. Jika Anda memerlukan output vektor sejati di PDF, atur `PdfSaveOptions.VectorResources = true` dan pertahankan resolusi gambar rendah—grafik vektor tidak akan terkena kehilangan DPI.

### Dokumen saya memiliki ratusan gambar; konversinya terasa lambat.
Bottleneck biasanya terletak pada langkah rasterisasi gambar. Anda dapat meningkatkan kecepatan dengan:

1. **Meningkatkan thread pool** (`Parallel.ForEach` pada `ResourceSavingCallback`) – namun hati‑hati dengan I/O disk.
2. **Menyimpan cache** gambar yang sudah dikonversi jika Anda menjalankan konversi berulang kali pada sumber yang sama.

### Bagaimana cara menangani file DOCX yang dilindungi password?
Cukup tambahkan password ke `LoadOptions`:

```csharp
LoadOptions opts = new LoadOptions { Password = "mySecret" };
Document protected = new Document("secret.docx", opts);
```

### Bisakah saya mengekspor Markdown langsung ke repositori yang kompatibel dengan GitHub?
Ya. Setelah konversi, commit `output.md` dan folder `md_images`. Tautan relatif yang dihasilkan oleh Aspose.Words berfungsi sempurna di GitHub Pages.

---

## Tips Pro untuk Pipeline yang Siap Produksi

- **Catat status pemulihan.** `LoadOptions` menyediakan `DocumentLoadingException` yang dapat Anda tangkap untuk merekam bagian mana yang dilewati.
- **Validasi kepatuhan PDF/UA** menggunakan alat seperti “Preflight” di Adobe Acrobat atau pustaka open‑source `veraPDF`.
- **Kompres PNG** setelah ekspor jika penyimpanan menjadi masalah. Alat seperti `pngquant` dapat dipanggil dari C# lewat `Process.Start`.
- **Parameterisasi DPI** dalam file konfigurasi sehingga Anda dapat beralih antara “web” (150 dpi) dan “print” (300 dpi) tanpa mengubah kode.

---

## Kesimpulan

Kami telah membahas **cara mengatur resolusi** untuk ekstraksi gambar, memperlihatkan cara andal **memulihkan file Word yang korup**, menunjukkan langkah‑langkah tepat untuk **memuat docx**, serta menuntun Anda melalui **konversi word ke markdown** dan **konversi docx ke pdf** dengan pengaturan aksesibilitas. Potongan kode lengkap siap disalin, ditempel, dan dijalankan—tanpa dependensi tersembunyi, tanpa shortcut “lihat dokumentasi”.

Selanjutnya, Anda dapat menjelajahi:

- Mengekspor langsung ke **HTML** dengan pengaturan resolusi yang sama.
- Menggunakan **Aspose.PDF** untuk menggabungkan PDF yang dihasilkan dengan dokumen lain.
- Mengotomatiskan alur kerja ini dalam Azure Function atau AWS Lambda untuk konversi on‑demand.

Cobalah, sesuaikan DPI sesuai kebutuhan, dan biarkan gambar beresolusi tinggi berbicara untuk dirinya sendiri. Selamat coding!

{{< layout-end >}}

{{< layout-end >}}