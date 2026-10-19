---
category: general
date: 2026-03-25
description: Konversi DOCX ke Markdown dengan cepat sambil mengekstrak gambar dari
  Word menggunakan Aspose.Words. Pelajari langkah demi langkah dengan kode lengkap.
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: id
og_description: Ubah DOCX menjadi Markdown dan ekstrak gambar dari Word dengan Aspose.Words.
  Ikuti tutorial lengkap ini untuk solusi siap‑jalankan.
og_title: Mengonversi DOCX ke Markdown di C# – Panduan Langkah demi Langkah
tags:
- Aspose.Words
- C#
- Markdown
title: Mengonversi DOCX ke Markdown di C# – Panduan Lengkap
url: /id/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengonversi DOCX ke Markdown dengan Aspose.Words

Pernah perlu **mengonversi DOCX ke markdown** tetapi tidak yakin bagaimana cara menjaga gambar yang disematkan tetap utuh? Anda tidak sendirian—banyak pengembang mengalami masalah ini ketika mencoba memindahkan konten Word ke generator situs statis atau repositori dokumentasi.  
Kabar baiknya, Aspose.Words untuk .NET dapat melakukan pekerjaan berat untuk Anda, dan dengan callback kecil Anda juga dapat **mengekstrak gambar dari file Word** secara bersamaan.

Dalam tutorial ini kami akan membahas contoh dunia nyata yang memuat sebuah `.docx`, menyimpannya sebagai file Markdown, dan menulis setiap gambar ke folder khusus. Pada akhir tutorial Anda akan memiliki aplikasi konsol siap‑jalankan yang dapat Anda masukkan ke proyek .NET mana pun.

> **Pro tip:** Jika Anda hanya membutuhkan teks dan tidak peduli dengan gambar, Anda dapat melewatkan `ResourceSavingCallback` sepenuhnya – kode tetap akan menghasilkan Markdown yang bersih.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi terbaru, misalnya 24.12). Anda dapat mengunduhnya dari NuGet: `Install-Package Aspose.Words`.
- **.NET 6.0** atau yang lebih baru (API ini juga bekerja di .NET Framework, tetapi .NET 6 memberikan kinerja terbaik).
- Proyek konsol sederhana atau host C# apa pun yang Anda sukai.
- File Word input (`input.docx`) yang berisi setidaknya satu gambar agar kami dapat melihat proses ekstraksi.

Itu saja—tanpa pustaka tambahan, tanpa alat baris perintah yang rumit. Mari kita mulai.

![contoh mengonversi docx ke markdown](images/convert-docx-to-markdown.png)

*Image alt text: contoh mengonversi docx ke markdown*

## Langkah 1 – Siapkan Proyek dan Tambahkan Aspose.Words

Untuk menjaga kebersihan, buat aplikasi konsol baru:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

## Langkah 2 – Muat DOCX Sumber

Hal pertama yang kami lakukan adalah memberi tahu Aspose.Words untuk membaca file Word. Operasi ini **cepat**—perpustakaan mem‑parsing struktur dokumen tanpa membuka Word secara langsung.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

Mengapa kami membungkus path dengan `Path.Combine`? Ini membuat kode dapat dipindahkan ke Windows, macOS, dan Linux—sesuatu yang akan Anda hargai ketika memindahkan proyek ke pipeline CI.

## Langkah 3 – Konfigurasikan Opsi Penyimpanan Markdown dengan Callback Sumber Daya

Ketika Anda meminta Aspose.Words untuk menyimpan sebagai Markdown, biasanya gambar disematkan sebagai string Base64. Itu baik untuk ikon kecil, tetapi untuk foto yang lebih besar akan memperbesar ukuran file. Sebagai gantinya, kami menambahkan **callback penyimpanan sumber daya** yang menulis setiap gambar ke disk dan memperbarui tautan Markdown.

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

Perhatikan kami mengirim `resourcesDir` ke konstruktor callback—ini menjaga logika path di luar callback itu sendiri dan membuat kelas dapat digunakan kembali.

## Langkah 4 – Implementasikan Callback Penyimpanan Sumber Daya

Callback mengimplementasikan `IResourceSavingCallback`. Untuk setiap gambar yang ingin ditulis oleh Aspose.Words, ia memberikan kami objek `ResourceSavingArgs`. Kami memutuskan **di mana** menyimpan file, memberi nama unik, dan kemudian memberi tahu mesin untuk melewatkan perilaku penyimpanan defaultnya.

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**Mengapa ini penting:** Dengan mengatur `args.Uri` kami mengontrol tepat bagaimana gambar akan direferensikan dalam file `.md` yang dihasilkan. Path relatif `Resources/img_0.png` berfungsi baik Anda membuka Markdown di VS Code, GitHub, atau generator situs statis.

## Langkah 5 – Simpan Dokumen sebagai Markdown

Sekarang bagian akhir: minta Aspose.Words menulis file Markdown. Callback yang kami hubungkan akan dipicu untuk setiap gambar secara otomatis.

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

Setelah baris selesai, Anda akan memiliki:

- `output.md` – representasi Markdown bersih dari konten Word asli.
- folder `Resources/` – berisi setiap gambar yang diekstrak dari DOCX.

## Contoh Kerja Lengkap

Berikut adalah program **lengkap, siap‑salin‑tempel**. Ganti `YOUR_DIRECTORY` dengan path absolut atau relatif yang berisi `input.docx` Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### Output yang Diharapkan

Buka `Output/output.md` di penampil Markdown apa pun dan Anda akan melihat sesuatu seperti:

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

Folder `Resources` akan berisi `img_0.png`, `img_1.jpg`, dll., yang sesuai dengan gambar yang awalnya disematkan dalam `input.docx`.

## Pertanyaan yang Sering Diajukan (FAQ)

**Apakah ini bekerja dengan file .doc?**  
Ya. Aspose.Words dapat memuat `.doc`, `.docx`, `.rtf`, dan banyak format lainnya. Cukup ubah ekstensi file di `inputPath`.

**Bagaimana jika saya membutuhkan URL absolut untuk gambar?**  
Ganti `args.Uri = $"Resources/{fileName}";` dengan sesuatu seperti `args.Uri = $"https://mycdn.com/docs/{fileName}";`. Markdown kemudian akan merujuk ke lokasi remote tersebut.

**Bisakah saya mengontrol kualitas atau format gambar?**  
Callback menerima aliran gambar asli. Jika Anda ingin mengonversi PNG ke JPEG, Anda dapat memuat aliran ke `System.Drawing.Image`, melakukan re‑encode, dan menulis byte baru sebelum mengatur `args.Uri`.

**Apakah `ResourceSavingCallback` aman untuk thread?**  
Aspose.Words memanggil callback secara berurutan untuk setiap sumber daya, jadi

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}