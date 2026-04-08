---
category: general
date: 2026-04-07
description: Simpan Word sebagai Markdown dan ekstrak gambar dari docx menggunakan
  callback. Pelajari cara menggunakan callback untuk menyimpan folder gambar markdown
  secara efisien.
draft: false
keywords:
- save word as markdown
- extract images from docx
- how to use callback
- markdown images folder
language: id
og_description: Simpan Word sebagai Markdown dan ekstrak gambar dari docx menggunakan
  callback. Panduan ini menunjukkan cara menggunakan callback untuk membuat folder
  gambar markdown.
og_title: Simpan Word sebagai Markdown – Panduan Langkah-demi-Langkah Lengkap
tags:
- Aspose.Words
- C#
- Markdown
- Image Extraction
title: Simpan Word sebagai Markdown dengan Folder Gambar Kustom – Panduan Lengkap
url: /id/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-custom-image-folder-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Word sebagai Markdown – Panduan Lengkap Langkah‑per‑Langkah

Pernahkah Anda perlu **menyimpan Word sebagai Markdown** tetapi tidak yakin harus berbuat apa dengan gambar yang disematkan? Anda tidak sendirian. Dalam banyak proyek, output markdown terlihat bagus—*sampai* Anda menyadari tautan gambar rusak karena file tidak pernah keluar dari paket Word.  

Kabar baiknya, Aspose.Words memberi Anda cara bersih untuk **mengekstrak gambar dari docx** dan menempatkannya tepat di mana Anda inginkan, menggunakan **callback** yang memungkinkan Anda mengontrol folder gambar markdown. Dalam tutorial ini kami akan membahas seluruh proses, mulai dari memuat file `.docx` hingga menghasilkan folder PNG yang rapi (atau format apa pun yang Anda miliki) dan file markdown yang mengarah ke gambar-gambar tersebut.

Pada akhir panduan ini Anda akan dapat:

* Mengonversi dokumen Word apa pun ke Markdown dengan satu baris kode.  
* Secara otomatis mengekspor setiap gambar ke sub‑folder `images` yang khusus.  
* Menyesuaikan nama file sehingga tidak pernah bentrok, bahkan ketika sumber berisi puluhan gambar.  

Tanpa skrip eksternal, tanpa menyalin‑tempel manual—hanya C# murni dan Aspose.Words.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

* **Aspose.Words for .NET** (versi stabil terbaru; pada saat penulisan ini versi 24.9).  
* Lingkungan pengembangan .NET (Visual Studio, Rider, atau `dotnet` CLI).  
* Dokumen Word (`.docx`) yang berisi setidaknya satu gambar—sebut saja `DocWithImages.docx`.  

Jika Anda belum pernah menggunakan Aspose.Words sebelumnya, jangan khawatir. Library ini sepenuhnya dikelola, tidak memerlukan interop COM, dan berfungsi pada .NET 6+ serta .NET Framework 4.8.

## Langkah 1 – Menyiapkan Proyek dan Menginstal Paket

Pertama, buat aplikasi console baru (atau tambahkan kode ke proyek yang sudah ada).

```bash
dotnet new console -n WordToMarkdownDemo
cd WordToMarkdownDemo
dotnet add package Aspose.Words
```

> **Tips pro:** Jika Anda menargetkan .NET 6, `Program.cs` default sudah menggunakan pernyataan top‑level, yang membuat contoh menjadi singkat.

## Langkah 2 – Membuat Callback untuk Mengontrol Penyimpanan Gambar

Aspose.Words memanggil `IResourceSavingCallback.ResourceSaving` untuk setiap sumber daya eksternal yang perlu ditulis (gambar, CSS, dll.). Dengan mengimplementasikan antarmuka ini, kami memperoleh kontrol penuh atas **bagaimana folder gambar markdown** dibangun.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles the saving of resources (e.g., images) when a document is converted to Markdown.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    // Folder where we want to dump the images.
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        // Ensure the folder exists before the first write.
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique filename: img_<guid>.<originalExtension>
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";

        // Full path where the image will be saved.
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        // Copy the incoming stream to our file.
        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        // Tell Aspose we’ve handled the write; skip its default behavior.
        args.Cancel = true;
    }
}
```

### Mengapa menggunakan callback?

* **Kontrol granular** – Anda menentukan struktur folder dan skema penamaan.  
* **Kinerja** – Anda menulis aliran sekali, menghindari fallback penulisan ganda library.  
* **Fleksibilitas** – Anda dapat menambahkan logging, optimasi gambar, atau bahkan mengunggah ke penyimpanan cloud pada titik ini.

## Langkah 3 – Memuat Dokumen Word

Sekarang callback sudah siap, kita hanya perlu mengarahkan Aspose.Words ke file sumber.

```csharp
// Path to the source .docx (adjust as needed).
string sourcePath = Path.Combine("YOUR_DIRECTORY", "DocWithImages.docx");

// Load the document into memory.
Document doc = new Document(sourcePath);
```

> **Bagaimana jika file tidak ditemukan?**  
> `Document` akan melempar `FileNotFoundException`. Bungkus pemuatan dalam `try/catch` jika Anda mengharapkan jalur dinamis.

## Langkah 4 – Menghubungkan MarkdownSaveOptions

Kelas `MarkdownSaveOptions` memungkinkan kami menyambungkan callback yang baru saja dibuat. Kami juga mengatur folder tempat gambar akan disimpan relatif terhadap file markdown.

```csharp
// Define where we want the images folder to sit.
string markdownFolder = Path.Combine("YOUR_DIRECTORY", "markdown-output");
string imagesSubFolder = Path.Combine(markdownFolder, "images");

// Ensure the markdown output directory exists.
Directory.CreateDirectory(markdownFolder);

// Create the save options and attach the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image.
    ResourceSavingCallback = new MyMarkdownResourceCallback(imagesSubFolder),

    // Optional: keep image references relative to the markdown file.
    ImagesFolder = "images"
};
```

Properti `ImagesFolder` memberi tahu Aspose untuk menghasilkan tautan markdown seperti `![Alt text](images/img_123.png)`. Karena kami juga mengatur `ResourceFileName` di dalam callback, file sebenarnya akan ditempatkan tepat di sana.

## Langkah 5 – Menyimpan sebagai Markdown dan Memverifikasi Hasil

Akhirnya, kami menulis file markdown. Callback sudah mengisi sub‑folder `images`.

```csharp
// Destination markdown file.
string markdownPath = Path.Combine(markdownFolder, "Doc.md");

// Save the document.
doc.Save(markdownPath, mdOptions);

// Quick sanity check – list the generated files.
Console.WriteLine("Markdown saved to: " + markdownPath);
Console.WriteLine("Extracted images:");
foreach (var img in Directory.GetFiles(imagesSubFolder))
{
    Console.WriteLine("  • " + Path.GetFileName(img));
}
```

### Output yang Diharapkan

Menjalankan program seharusnya mencetak sesuatu seperti:

```
Markdown saved to: C:\Project\markdown-output\Doc.md
Extracted images:
  • img_5c2a1f8b-3e7b-4d9a-9c1f-2b6e5f9d9a3c.png
  • img_a7d4c9e2-1f55-4c2b-8f6a-9e1b2c3d4e5f.jpg
```

Buka `Doc.md` di penampil markdown apa pun; Anda akan melihat tautan gambar yang mengarah dengan benar ke folder `images`.

---

## Pertanyaan yang Sering Diajukan (FAQ)

### Cara **mengekstrak gambar dari docx** tanpa mengonversi ke markdown?

Anda dapat menggunakan kembali `MyMarkdownResourceCallback` yang sama tetapi memberikannya ke `doc.Save("images.zip", SaveFormat.Zip)`. Callback tetap akan dipanggil untuk setiap gambar, memungkinkan Anda menempatkannya di mana saja yang Anda inginkan.

### Bagaimana jika saya membutuhkan **format gambar yang berbeda**?

`args.FileName` sudah berisi ekstensi asli (`.png`, `.jpg`, dll.). Jika Anda harus mengonversi semua gambar ke satu format, tambahkan langkah konversi di dalam `ResourceSaving` sebelum menulis aliran.

### Bisakah saya **menyesuaikan folder gambar markdown** per dokumen?

Tentu saja. Callback menerima jalur folder melalui konstruktor, sehingga Anda dapat membuat instance callback baru dengan folder yang berbeda untuk setiap dokumen dalam proses batch.

### Apakah ini bekerja dengan **dokumen besar** (ratusan gambar)?

Ya. Callback menyalurkan gambar langsung ke disk, menjaga penggunaan memori tetap rendah. Pastikan drive target memiliki ruang yang cukup dan Anda tidak mencapai batas handle file OS.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang siap disalin‑tempel. Ganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif yang sesuai dengan lingkungan Anda.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        args.Cancel = true;
    }
}

class Program
{
    static void Main()
    {
        // Adjust these paths.
        string baseDir = Path.Combine(Environment.CurrentDirectory, "demo");
        string sourceDoc = Path.Combine(baseDir, "DocWithImages.docx");
        string markdownDir = Path.Combine(baseDir, "markdown-output");
        string imagesDir = Path.Combine(markdownDir, "images");
        string markdownFile = Path.Combine(markdownDir, "Doc.md");

        // Load the document.
        Document doc;
        try
        {
            doc = new Document(sourceDoc);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // Configure save options with our callback.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceCallback(imagesDir),
            ImagesFolder = "images"
        };

        // Ensure output folder exists.
        Directory.CreateDirectory(markdownDir);

        // Save as markdown.
        doc.Save(markdownFile, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownFile}");
        Console.WriteLine("🖼️ Extracted images:");
        foreach (var file in Directory.GetFiles(imagesDir))
            Console.WriteLine($"   - {Path.GetFileName(file)}");
    }
}
```

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}