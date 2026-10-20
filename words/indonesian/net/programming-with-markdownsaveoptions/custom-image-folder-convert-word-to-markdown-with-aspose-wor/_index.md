---
category: general
date: 2026-03-08
description: Panduan folder gambar khusus untuk mengonversi Word ke Markdown, mengekstrak
  gambar dari docx, dan mengubah format gambar menggunakan Aspose.Words – langkah
  demi langkah.
draft: false
keywords:
- custom image folder
- convert word to markdown
- change image format
- extract images docx
- convert docx to md
language: id
og_description: Panduan folder gambar khusus menunjukkan cara mengonversi Word ke
  Markdown, mengekstrak gambar dari DOCX, dan mengubah format gambar menggunakan Aspose.Words
  di C#.
og_title: folder gambar khusus – Konversi Word ke Markdown dengan Aspose.Words
tags:
- Aspose.Words
- C#
- Markdown
title: folder gambar khusus – Konversi Word ke Markdown dengan Aspose.Words
url: /id/net/programming-with-markdownsaveoptions/custom-image-folder-convert-word-to-markdown-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# folder gambar khusus – Convert Word to Markdown with Aspose.Words

Pernah bertanya-tanya bagaimana cara **custom image folder** konversi Word‑to‑Markdown Anda sehingga gambar‑gambar berakhir tepat di tempat yang Anda inginkan? Anda tidak sendirian. Banyak pengembang mengalami kesulitan ketika perilaku default Aspose.Words menyebarkan gambar‑gambar ke folder yang sama dengan file Markdown, membuat pembersihan proyek menjadi mimpi buruk.  

Dalam tutorial ini kami akan membahas solusi lengkap yang siap dijalankan yang **convert word to markdown**, **extract images docx**, dan bahkan **change image format** secara langsung. Pada akhir tutorial Anda akan memiliki sub‑folder `Resources/` yang bersih, gambar‑gambar yang telah dinamai ulang dengan rapi, dan file markdown yang merujuknya dengan benar. Tanpa skrip eksternal, tanpa menyalin‑tempel manual—hanya C# murni dan Aspose.Words.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi terbaru per 2026, misalnya 24.9).  
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau `dotnet` CLI).  
- Contoh `input.docx` yang berisi setidaknya satu gambar.  
- Familiaritas dasar dengan sintaks C# (tidak ada yang rumit).

Jika Anda sudah memiliki semua ini, bagus—langsung saja ke kode. Jika belum, dapatkan paket NuGet gratis dengan `dotnet add package Aspose.Words` dan buat proyek konsol baru.

## Langkah 1 – Memuat Dokumen Word Sumber

Hal pertama yang kita lakukan adalah membuka file `.docx` yang akan dikonversi. Kelas `Document` milik Aspose.Words menangani semua hal mulai dari teks hingga sumber daya yang disematkan.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Mengapa ini penting:** Memuat dokumen lebih awal memberi kami akses ke pohon node internalnya, yang kemudian memungkinkan callback **extract images docx** melihat setiap gambar sebagai sumber daya.

## Langkah 2 – Menyiapkan Opsi Penyimpanan Markdown dengan Callback Penyimpanan Sumber Daya

Aspose.Words memungkinkan Anda menambahkan callback yang dipanggil untuk setiap sumber daya eksternal (gambar, SVG, dll.). Kami akan menggunakan ini untuk menyalurkan setiap gambar ke **custom image folder** dan menamainya kembali.

```csharp
// Configure Markdown save options
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Attach our custom callback
    ResourceSavingCallback = new ImageSavingCallback()
};
```

### Mengapa Menggunakan Callback?

- **Kontrol atas lokasi:** Secara default, Aspose menulis gambar di samping file `.md`.  
- **Konsistensi penamaan:** Anda dapat menambahkan awalan, menambahkan timestamp, atau bahkan meng‑hash kontennya.  
- **Konversi format:** Callback memungkinkan Anda beralih dari PNG ke JPEG secara langsung, memenuhi kebutuhan **change image format**.

## Langkah 3 – Menyimpan Dokumen sebagai Markdown

Sekarang kami memberi tahu Aspose untuk menghasilkan file markdown. Callback yang didefinisikan sebelumnya secara otomatis dijalankan untuk setiap gambar yang ditemukannya.

```csharp
// Save the document as Markdown; images are handled by the callback
doc.Save("YOUR_DIRECTORY/output.md", mdOptions);
```

Pada titik ini Anda seharusnya melihat `output.md` dan folder baru bernama `Resources` (atau nama yang Anda pilih) yang berisi file gambar yang telah dinamai ulang.

## Langkah 4 – Mengimplementasikan Callback Penyimpanan Gambar

Berikut adalah implementasi lengkap dari `ImageSavingCallback`. Ia membuat folder tujuan, menamai ulang setiap gambar, dan secara opsional mengubah formatnya.

```csharp
/// <summary>
/// Handles saving of external resources (images) during Markdown export.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    /// <summary>
    /// Invoked for each resource (image, SVG, etc.) Aspose.Words wants to write.
    /// </summary>
    /// <param name="args">Information about the resource being saved.</param>
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Define the custom folder – this is our "custom image folder"
        string folder = "YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(folder); // ensures the folder exists

        // 2️⃣ Build a clean, predictable file name
        //   Example: img_12345.png → img_input_12345.png
        string safeBaseName = Path.GetFileNameWithoutExtension(args.ResourceFileName);
        string newName = $"img_{safeBaseName}{Path.GetExtension(args.ResourceFileName)}";

        // 3️⃣ Update the path that Markdown will reference
        args.ResourceFileName = Path.Combine(folder, newName);

        // 4️⃣ OPTIONAL: Change the image format (covers "change image format")
        // Uncomment the line below to force JPEG output for all images.
        // args.ResourceFileFormat = SaveFormat.Jpeg;

        // 5️⃣ Log for debugging – helpful when troubleshooting edge cases
        Console.WriteLine($"Saving image as: {args.ResourceFileName}");
    }
}
```

#### Tips Pro & Kasus Edge

- **Folder tidak ada:** `Directory.CreateDirectory` bersifat idempotent; tidak akan melempar error jika folder sudah ada.  
- **Tabrakan nama:** Jika dua gambar memiliki nama asli yang sama, trik `safeBaseName` menambahkan awalan unik (`img_`). Untuk keamanan ekstra, tambahkan GUID: `Guid.NewGuid().ToString("N")`.  
- **Mengubah format:** Saat Anda meng‑uncomment `args.ResourceFileFormat = SaveFormat.Jpeg;`, Aspose secara otomatis mengonversi data gambar, memenuhi kebutuhan **change image format**.  
- **Kinerja:** Untuk dokumen yang sangat besar, pertimbangkan streaming output alih‑alih memuat semuanya ke memori—Aspose menyediakan `LoadOptions` untuk itu.

## Langkah 5 – Memverifikasi Hasil

Setelah program selesai, buka `output.md`. Anda harus melihat tautan gambar Markdown yang mengarah ke lokasi baru, misalnya:

```markdown
![Sample Image](Resources/img_SampleImage.png)
```

Jika Anda mengaktifkan konversi JPEG, tautan akan berakhiran `.jpeg`. Buka folder `Resources` dan pastikan gambar‑gambar ada, telah dinamai ulang dengan benar, dan dapat dilihat.

## Pertanyaan yang Sering Diajukan (FAQs)

### Bisakah saya menggunakan pendekatan ini untuk **convert docx to md** tanpa Aspose?

Ya, tetapi Anda akan kehilangan penanganan sumber daya bawaan. Pustaka seperti **DocX** atau **Open XML SDK** dapat mengekstrak gambar, namun Anda harus menulis generator markdown sendiri—bekerja lebih banyak dan rawan kesalahan.

### Bagaimana jika file Word saya berisi grafik SVG?

Callback berfungsi untuk semua sumber daya eksternal, termasuk SVG. Properti `ResourceSavingArgs.ResourceFileFormat` akan melaporkan format asli, sehingga Anda dapat memutuskan apakah akan mempertahankan SVG atau merasternya.

### Apakah ini bekerja pada .NET 6/7/8?

Tentu saja. Aspose.Words menargetkan .NET Standard 2.0+, sehingga semua runtime .NET modern kompatibel.

### Bagaimana cara menangani gambar *sangat* besar yang perlu diubah ukurannya?

Anda dapat menyisipkan pemrosesan gambar di dalam callback menggunakan `System.Drawing` atau `ImageSharp`. Setelah gambar disimpan ke stream sementara, ubah ukurannya, lalu tulis data yang telah diubah kembali ke `args.Stream`.

## Contoh Lengkap yang Berfungsi

Berikut seluruh program dalam satu file. Salin‑tempel, sesuaikan jalur, dan jalankan.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 1: Load the source Word document
            // -----------------------------------------------------------------
            string inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // -----------------------------------------------------------------
            // Step 2: Configure Markdown save options with a custom callback
            // -----------------------------------------------------------------
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // -----------------------------------------------------------------
            // Step 3: Save as Markdown – images are routed to the custom folder
            // -----------------------------------------------------------------
            string outputPath = "YOUR_DIRECTORY/output.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
        }
    }

    // -----------------------------------------------------------------
    // Step 4 – Callback that stores each image in a custom folder
    // -----------------------------------------------------------------
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            // Define the folder where images will be placed (our custom image folder)
            string folder = "YOUR_DIRECTORY/Resources/";
            Directory.CreateDirectory(folder);

            // Build a new, predictable name for the image
            string safeBase = Path.GetFileNameWithoutExtension(args.ResourceFileName);
            string newName = $"img_{safeBase}{Path.GetExtension(args.ResourceFileName)}";

            // Update the path used in the generated Markdown
            args.ResourceFileName = Path.Combine(folder, newName);

            // OPTIONAL: Force JPEG output – uncomment to enable
            // args.ResourceFileFormat = SaveFormat.Jpeg;

            // Debug output
            Console.WriteLine($"Saving image as: {args.ResourceFileName}");
        }
    }
}
```

### Output yang Diharapkan

```
Saving image as: YOUR_DIRECTORY/Resources/img_SampleImage.png
Conversion complete!
Markdown file: YOUR_DIRECTORY/output.md
```

Buka `output.md` dan Anda akan melihat:

```markdown
# Sample Document

Here is an image:

![Sample Image](Resources/img_SampleImage.png)
```

File gambar berada rapi di dalam `Resources/`, memenuhi kebutuhan **custom image folder**.

## Kesimpulan

Kami baru saja membangun pipeline yang kuat yang **convert word to markdown**, **extract images docx**, dan **change image format** sambil menjaga setiap gambar berada di dalam **custom image folder** yang Anda kontrol. Solusinya adalah:

1. Memuat `.docx` dengan Aspose.Words.  
2. Menempelkan `ResourceSavingCallback` yang membuat folder, menamai ulang file, dan secara opsional mengonversi format.  
3. Menyimpan sebagai Markdown – callback melakukan pekerjaan berat secara otomatis.

Silakan bereksperimen: ganti `SaveFormat.Jpeg` dengan `SaveFormat.Png`, tambahkan timestamp ke nama file, atau integrasikan pustaka kompresi gambar untuk aset yang lebih kecil. Pola ini dapat diskalakan untuk pemrosesan batch, pipeline CI, atau bahkan layanan web yang menerima file Word yang diunggah dan mengembalikan Markdown siap terbit.

---

*Siap untuk tantangan berikutnya?* Cobalah menghubungkan konversi ini dengan generator situs statis seperti Hugo atau MkDocs untuk mengotomatisasi alur kerja dokumentasi Anda. Atau jelajahi exporter **HTML** dan **PDF** milik Aspose.Words untuk penerbitan multi‑format. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}