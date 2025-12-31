---
category: general
date: 2025-12-31
description: Ekspor gambar Word ke Markdown dengan cepat. Pelajari cara mengonversi
  Word ke markdown, mengekstrak gambar dari docx, dan mengatur DPI gambar dalam satu
  tutorial.
draft: false
keywords:
- export word images
- convert word to markdown
- extract images from docx
- how to convert docx to markdown
- how to set image dpi
language: id
og_description: Ekspor gambar Word ke Markdown dengan Aspose.Words. Panduan ini menunjukkan
  cara mengonversi docx ke markdown, mengekstrak gambar, dan mengatur DPI gambar.
og_title: Ekspor Gambar Word ke Markdown – Tutorial C# Langkah demi Langkah
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: Ekspor Gambar Word ke Markdown – Panduan Lengkap C#
url: /id/net/programming-with-markdownsaveoptions/export-word-images-to-markdown-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ekspor Gambar Word ke Markdown – Panduan Lengkap CPernahkah Anda perlu **mengekspor gambar word** ke Markdown tetapi tidak tahu harus mulai dari mana? Anda tidak sendirian—banyak pengembang mengalami kendala ini saat mencoba memindahkan dokumentasi dari alur kerja Word korporat ke generator situs statis. Dalam tutorial ini kami akan membahas solusi tunggal yang **mengonversi file DOCX ke Markdown**, mengekstrak setiap gambar yang disisipkan dengan resolusi 300 DPI, dan bahkan mengubah persamaan Office Math menjadi LaTeX.

Mengapa ini penting? Gambar beresolusi tinggi menjaga diagram tetap tajam di web, sementara persamaan LaTeX ditampilkan dengan indah di sebagian besar penampil Markdown. Pada akhir tutorial Anda akan memiliki file `.md` siap terbit dan folder PNG berukuran tepat, semuanya dihasilkan dari kode C#.

## Apa yang Akan Anda Pelajari

* Cara **mengonversi word ke markdown** menggunakan Aspose.Words.  
* Langkah‑langkah tepat untuk **mengekstrak gambar dari docx** sambil mengontrol DPI.  
* Cara menjawab “**bagaimana cara mengatur dpi gambar**” dalam kode.  
* Tips menangani dokumen besar, gambar yang hilang, dan folder output khusus.  
* Contoh lengkap yang dapat dijalankan dan Anda dapat menambahkannya ke proyek .NET mana pun.

### Prasyarat

* .NET 6.0 atau lebih baru (kode ini juga berfungsi pada .NET Framework 4.7+).  
* Lisensi aktif Aspose.Words untuk .NET (Anda dapat memulai dengan evaluasi gratis).  
* Familiaritas dasar dengan C# dan command line.  
* File DOCX yang berisi setidaknya satu gambar atau persamaan—contoh `input.docx` kami sudah cukup.

> **Pro tip:** Jika Anda menggunakan pipeline CI/CD, simpan file lisensi di luar kontrol sumber dan muat dari variabel lingkungan.

---

## Langkah 1 – Instal Aspose.Words dan Siapkan Proyek

Hal pertama yang perlu Anda lakukan adalah menambahkan pustaka yang melakukan pekerjaan berat.

```bash
dotnet new console -n WordToMarkdown
cd WordToMarkdown
dotnet add package Aspose.Words
```

Ini membuat aplikasi konsol minimal bernama **WordToMarkdown** dan mengambil paket Aspose.Words terbaru dari NuGet.  

> **Mengapa Aspose.Words?** Ia mendukung ekstraksi gambar lossless, skala DPI, dan ekspor LaTeX native untuk Office Math—fitur yang kebanyakan pustaka gratis tidak miliki.

---

## Langkah 2 – Muat Dokumen Sumber

Sekarang kita membaca file `.docx` yang berisi gambar yang ingin Anda ekspor.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Replace with the actual path on your machine
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document – this also parses all embedded resources
Document sourceDocument = new Document(inputPath);
```

Jika file tidak ditemukan, Aspose akan melempar `FileNotFoundException`. Menangkapnya lebih awal memberikan pesan error yang lebih jelas bagi pengguna akhir.

```csharp
if (!File.Exists(inputPath))
{
    Console.Error.WriteLine($"❌ Cannot locate '{inputPath}'. Ensure the file exists.");
    return;
}
```

---

## Langkah 3 – Konfiguras Opsi Penyimpanan Markdown (Termasuk DPI)

Di sinilah kita menjawab **bagaimana cara mengatur dpi gambar**. Secara default Aspose mengekspor gambar pada 96 DPI, yang tampak buram pada layar retina. Menetapkan `ImageResolution` ke **300** memberi Anda gambar kualitas cetak.

```csharp
// Configure the export settings
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // Export each image at 300 DPI – ideal for most web and print scenarios
    ImageResolution = 300,

    // Turn Office Math equations into LaTeX so they render nicely in Markdown
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: store images in a sub‑folder called "images"
    ImagesFolder = "images"
};
```

> **Mengapa LaTeX?** Sebagian besar penampil Markdown (GitHub, GitLab, MkDocs) memahami sintaks `$…$`, memberikan persamaan yang tajam dan dapat diskalakan tanpa plugin tambahan.

---

## Langkah 4 – Simpan Dokumen sebagai Markdown

Dengan opsi yang sudah disiapkan, kita akhirnya dapat **mengekspor gambar word** beserta konten lainnya.

```csharp
// Destination markdown file
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.md");

// Perform the conversion
sourceDocument.Save(outputPath, markdownOptions);

Console.WriteLine($"✅ Conversion complete! Markdown saved to '{outputPath}'.");
Console.WriteLine($"🖼️ Extracted images are in the '{markdownOptions.ImagesFolder}' folder.");
```

Menjalankan program menghasilkan dua artefak:

1. `output.md` – representasi Markdown lengkap dari file Word asli.  
2. `images/` – folder yang berisi setiap gambar dari DOCX, kini dalam PNG 300 DPI (atau format asli jika sudah beresolusi tinggi).

---

## Langkah 5 – Verifikasi Hasil (Opsional tapi Disarankan)

Pemeriksaan cepat menyelamatkan Anda dari kejutan tidak menyenangkan di kemudian hari.

```csharp
// Verify that at least one image was extracted
int imageCount = Directory.GetFiles(markdownOptions.ImagesFolder).Length;
if (imageCount == 0)
{
    Console.WriteLine("⚠️ No images were found. Did the source DOCX contain pictures?");
}
else
{
    Console.WriteLine($"🔎 Found {imageCount} image(s) at 300 DPI.");
}
```

Buka `output.md` di editor favorit Anda. Anda harus melihat tag gambar Markdown seperti:

```markdown
![Figure 1](images/Image_0.png)
```

Jika Anda menyertakan persamaan, mereka akan muncul sebagai blok LaTeX:

```markdown
$$
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

---

## Kasus Khusus & Pertanyaan Umum

### Bagaimana jika DOCX berisi gambar sangat besar?

Aspose secara otomatis menurunkan sampel gambar yang melebihi DPI yang diminta, tetapi Anda dapat mengontrol lebar/tinggi maksimum menggunakan properti `ImageSize` pada `MarkdownSaveOptions`. Contoh:

```csharp
markdownOptions.ImageSize = new Size(1200, 0); // 1200px wide, preserve aspect ratio
```

### Bagaimana menangani DOCX tanpa gambar?

Konversi tetap berjalan; Anda hanya akan mendapatkan file Markdown tanpa tag `![...]`. Langkah verifikasi di atas akan memberi peringatan, yang berguna untuk pipeline CI.

### Bisakah saya mengubah format gambar?

Ya. Tetapkan `markdownOptions.ImageExportFormat` ke `ImageExportFormat.Jpeg`, `Png`, atau `Bmp`. PNG adalah default karena mempertahankan kualitas lossless.

### Apakah lisensi diperlukan untuk skala DPI?

Lisensi evaluasi gratis mencakup skala DPI, tetapi menambahkan watermark kecil pada halaman pertama. Untuk penggunaan produksi, beli lisensi untuk menghilangkan watermark dan membuka kinerja penuh.

### Bagaimana cara menjalankannya di Linux/macOS?

Aplikasi konsol .NET yang sama bekerja lintas‑platform. Cukup instal .NET SDK untuk OS Anda dan jalankan `dotnet run`. Pastikan dependensi native Aspose.Words tersedia; paket NuGet sudah menyertakan semuanya.

---

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

Berikut seluruh `Program.cs` yang dapat Anda masukkan ke proyek konsol baru. Tidak ada bagian yang terlewat.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣  Load the source DOCX
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        if (!File.Exists(inputPath))
        {
            Console.Error.WriteLine($"❌ Cannot locate '{inputPath}'.");
            return;
        }

        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // 2️⃣  Configure Markdown export options
        // -------------------------------------------------
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            ImageResolution = 300,                     // How to set image DPI
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ImagesFolder = "images",                   // Extracted images go here
            ImageExportFormat = ImageExportFormat.Png   // Keep lossless quality
        };

        // -------------------------------------------------
        // 3️⃣  Save as Markdown
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.md");
        sourceDocument.Save(outputPath, markdownOptions);
        Console.WriteLine($"✅ Markdown saved to '{outputPath}'.");
        Console.WriteLine($"🖼️ Images saved to folder '{markdownOptions.ImagesFolder}'.");

        // -------------------------------------------------
        // 4️⃣  Quick verification (optional)
        // -------------------------------------------------
        if (Directory.Exists(markdownOptions.ImagesFolder))
        {
            int imageCount = Directory.GetFiles(markdownOptions.ImagesFolder).Length;
            Console.WriteLine(imageCount > 0
                ? $"🔎 Found {imageCount} image(s) at 300 DPI."
                : "⚠️ No images were extracted.");
        }
    }
}
```

Simpan sebagai `Program.cs`, jalankan `dotnet run`, dan saksikan keajaibannya.

---

## Kesimpulan

Kami baru saja menunjukkan cara **mengekspor gambar word** ke Markdown, **mengonversi word ke markdown**, dan **mengekstrak gambar dari docx** sambil mengontrol DPI secara tepat. Langkah‑langkah utama—menginstal Aspose.Words, memuat dokumen, menyesuaikan `MarkdownSaveOptions`, dan menyimpan—cukup sederhana untuk skrip cepat namun cukup kuat untuk pipeline produksi.

Dari sini Anda dapat:

* Menyalurkan Markdown yang dihasilkan ke generator situs statis seperti Hugo atau MkDocs.  
* Menambahkan langkah pasca‑proses yang mengganti nama gambar menjadi lebih bermakna.  
* Mengintegrasikan kode ini ke Azure Function untuk konversi dokumen on‑demand.

Silakan bereksperimen dengan nilai DPI berbeda, format gambar, atau bahkan CSS khusus untuk Markdown yang dihasilkan. Jika Anda menemukan kendala, tinggalkan komentar di bawah—selamat mengonversi!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}