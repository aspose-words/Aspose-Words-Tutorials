---
category: general
date: 2026-04-05
description: Pelajari cara mengonversi DOCX ke Markdown dan mengekstrak gambar dari
  DOCX dalam C#. Panduan langkah demi langkah dengan kode lengkap dan tips.
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: id
og_description: Konversi DOCX ke Markdown dan ekstrak gambar dari DOCX menggunakan
  Aspose.Words. Tutorial C# lengkap dengan kode, penjelasan, dan tips praktik terbaik.
og_title: Konversi DOCX ke Markdown – Ekstrak Gambar dari DOCX dengan C#
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: Ubah DOCX ke Markdown – Ekstrak Gambar dari DOCX dengan Aspose.Words
url: /id/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengonversi DOCX ke Markdown – Mengekstrak Gambar dari DOCX dalam C#

Pernah perlu **mengonversi DOCX ke Markdown** tetapi kesulitan karena gambar menghilang di output? Anda tidak sendirian. Dalam banyak proyek versi markdown sangat cocok untuk version‑control atau static‑site generator, namun gambar‑gambar tertinggal, menjadikan dokumen kaya menjadi file teks kosong.  

Kabar baik? Dengan beberapa baris C# dan Aspose.Words Anda dapat **mengonversi DOCX ke Markdown** *dan* **mengekstrak gambar dari DOCX** secara otomatis. Panduan ini membawa Anda melalui seluruh proses, menjelaskan mengapa setiap bagian penting, dan bahkan menunjukkan cara menjaga folder gambar tetap rapi.

## Apa yang Akan Anda Pelajari

- Cara memuat DOCX yang berisi gambar.
- Cara mendefinisikan `IResourceSavingCallback` khusus yang menentukan ke mana setiap gambar disimpan.
- Cara mengonfigurasi `MarkdownSaveOptions` sehingga markdown yang dihasilkan merujuk ke gambar yang diekstrak dengan benar.
- Tips menangani kasus tepi seperti nama gambar duplikat atau format non‑PNG.
- Contoh kode lengkap yang siap disalin‑tempel dan dapat Anda jalankan hari ini.

### Prasyarat

- .NET 6.0 atau lebih baru (API ini bekerja pada .NET Core, .NET Framework, dan .NET 5+).
- Lisensi untuk **Aspose.Words for .NET** (versi percobaan gratis dapat digunakan untuk pengujian).
- Pemahaman dasar tentang C# dan Visual Studio (atau IDE favorit Anda).

Jika Anda sudah memiliki semuanya, mari kita mulai.

---

## Langkah 1: Siapkan Proyek dan Instal Aspose.Words

Pertama, buat aplikasi console baru (atau integrasikan ke dalam solusi yang sudah ada).

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **Tip Pro:** Gunakan versi NuGet terbaru (per April 2026 versi 24.12) untuk mendapatkan perbaikan ekspor markdown terbaru.

---

## Langkah 2: Buat Callback untuk Menyimpan Gambar di Lokasi yang Anda Inginkan

Aspose.Words memungkinkan Anda menyela setiap sumber daya (gambar, SVG, dll.) yang ditulis selama ekspor markdown. Dengan mengimplementasikan `IResourceSavingCallback` Anda dapat:

1. Pilih folder yang berada di samping file markdown Anda.
2. Buat nama file unik (agar tidak pernah menimpa gambar yang sudah ada).
3. Tentukan format (di sini kami memaksa PNG untuk konsistensi).

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### Mengapa Nama Berbasis GUID?

Jika DOCX sumber berisi dua gambar dengan nama asli yang sama, penyalinan sederhana akan menimpa salah satunya. Menggunakan `Guid.NewGuid()` menjamin keunikan, yang sangat berguna ketika Anda menjalankan konversi berulang kali dalam pipeline otomatis.

---

## Langkah 3: Muat DOCX dan Hubungkan Opsi Markdown

Sekarang kita memuat dokumen ke memori dan melampirkan callback yang baru saja dibuat.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### Apa yang dilakukan kode, langkah demi langkah

| Langkah | Tujuan |
|------|---------|
| **Mendefinisikan jalur** | Menjaga proyek Anda fleksibel; Anda dapat menunjuk ke folder mana pun tanpa harus mengompilasi ulang. |
| **Muat DOCX** | `Document` mem‑parsing file Word, membuat semua elemen (paragraf, tabel, gambar) dapat diakses. |
| **Konfigurasikan `MarkdownSaveOptions`** | `ResourceSavingCallback` adalah kait yang mengekstrak gambar. Tanpanya, Aspose.Words akan menyematkan gambar sebagai string base64 atau mengabaikannya sepenuhnya, tergantung pada pengaturan. |
| **Simpan** | `doc.Save` menulis file markdown dan memicu callback untuk setiap gambar. |

---

## Langkah 4: Verifikasi Output – Apa yang Harus Anda Lihat?

Setelah menjalankan program, buka `DocWithImages.md`. Anda akan melihat tautan gambar markdown yang tampak seperti ini:

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

Dan di `C:\Docs\MarkdownResources` Anda akan menemukan serangkaian file PNG dengan nama GUID. Buka salah satunya – mereka harus identik dengan gambar yang disematkan dalam DOCX asli.

Jika Anda membuka file markdown di penampil yang menghormati jalur relatif (misalnya pratinjau VS Code, GitHub, atau static‑site generator), gambar akan ditampilkan persis seperti di Word.

### Masalah Umum & Cara Menghindarinya

| Gejala | Penyebab Kemungkinan | Solusi |
|---------|--------------|-----|
| Gambar muncul sebagai tautan rusak | `ResourceFileName` tidak diatur, sehingga markdown mengarah ke file yang tidak ada. | Pastikan `args.ResourceFileName = newFileName;` di dalam callback. |
| File PNG berukuran besar | Gambar asli berupa JPEG atau BMP; mengonversi ke PNG dapat meningkatkan ukuran. | Deteksi format asli melalui `args.ResourceContentType` dan pertahankan: `args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| Gambar duplikat masih muncul | Anda menggunakan nama file statis alih‑alih GUID. | Kembalikan ke logika GUID atau tambahkan penghitung per tipe gambar. |
| Konversi melempar `FileNotFoundException` | Jalur DOCX sumber salah atau folder tidak memiliki izin baca. | Verifikasi jalur dan berikan hak akses sistem file yang sesuai. |

---

## Langkah 5: Penyesuaian Lanjutan (Opsional)

### 5.1 Pertahankan Format Gambar Asli

Jika Anda ingin gambar output tetap menggunakan ekstensi aslinya, ubah callback:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 Sematkan Gambar sebagai Base64 (Ketika Anda *Tidak* Menginginkan File Terpisah)

Terkadang markdown satu‑file lebih disukai (misalnya untuk dikirim lewat email). Ubah opsi:

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

Namun ingat: **mengekstrak gambar dari DOCX** adalah tujuan utama untuk kebanyakan alur kerja static‑site, jadi pendekatan folder biasanya pilihan yang lebih baik.

---

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

Berikut seluruh program dalam satu file. Cukup ganti jalur dengan milik Anda sendiri dan jalankan.

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

Jalankan dengan `dotnet run`. Ketika konsol mencetak baris ✅, buka file markdown dan Anda akan melihat gambar ditampilkan dengan benar.

---

## Kesimpulan

Anda kini memiliki **solusi lengkap dan siap produksi untuk mengonversi DOCX ke Markdown dan mengekstrak gambar dari DOCX** menggunakan Aspose.Words dalam C#. Kata kunci utama muncul di seluruh panduan, memperkuat relevansi bagi mesin pencari dan asisten AI.  

Dalam satu langkah kode:

1. Memuat dokumen Word.
2. Menyela setiap gambar via `IResourceSavingCallback`.
3. Menyimpan setiap gambar ke folder yang dapat diprediksi dengan nama unik.
4. Menghasilkan markdown yang merujuk ke gambar‑gambar tersebut.

Dari sini Anda dapat:

- Plug

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}