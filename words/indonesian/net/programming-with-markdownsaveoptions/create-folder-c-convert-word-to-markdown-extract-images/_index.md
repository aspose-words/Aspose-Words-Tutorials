---
category: general
date: 2026-02-26
description: Buat folder tutorial C# yang menunjukkan cara mengonversi Word ke markdown,
  mengekstrak gambar dari docx, dan menyalin stream ke file—semua dalam satu langkah.
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: id
og_description: Tutorial C# “Create folder” membimbing Anda melalui konversi Word
  ke markdown, mengekstrak gambar dari docx, dan menyalin stream ke file dengan contoh
  kode yang jelas.
og_title: Buat folder C# – Konversi Word ke Markdown & Ekstrak Gambar
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: Buat folder C# – Konversi Word ke Markdown & Ekstrak Gambar
url: /id/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat folder C# – Konversi Word ke Markdown & Ekstrak Gambar

Pernah perlu **membuat folder C#** sekaligus mengubah dokumen Word menjadi markdown dan mengekstrak semua gambar di dalamnya? Anda bukan satu‑satunya yang kebingungan dengan hal ini. Dalam banyak pipeline otomatisasi, Anda harus menangani pekerjaan sistem file, konversi format, dan penanganan data biner—semua dalam satu langkah.  

Dalam panduan ini kami akan membahas solusi lengkap yang dapat dijalankan yang melakukan hal tersebut: membuat direktori target, mengonversi `.docx` ke markdown, mengekstrak setiap gambar yang disematkan, dan menggunakan logika **copy stream to file** sehingga gambar tersimpan di lokasi yang Anda inginkan. Tanpa skrip eksternal, tanpa langkah manual. Hanya C# murni dan pustaka Aspose.Words.

> **Apa yang akan Anda dapatkan**  
> * Struktur folder yang jelas siap untuk markdown dan aset  
> * File markdown yang mereferensikan gambar yang diekstrak dengan benar  
> * Kode sumber lengkap yang dapat Anda masukkan ke proyek .NET mana pun  

Sebelum kita mulai, pastikan Anda memiliki:

* .NET 6.0 (atau lebih baru) SDK terpasang – kode ini menggunakan fitur bahasa modern.  
* Lisensi untuk **Aspose.Words for .NET** (versi percobaan gratis cukup untuk pengujian).  
* Visual Studio 2022 atau editor favorit Anda.  

Jika Anda bertanya-tanya *mengapa* Anda ingin mengekstrak gambar alih‑alih menyematkannya, pikirkan tentang generator situs statis: mereka menyukai markdown dengan jalur gambar relatif, dan menyimpan aset di folder khusus membuat semuanya rapi dan ramah cache.

---

## Buat folder C# dan siapkan struktur output

Hal pertama yang kita butuhkan adalah tempat di disk tempat semua file akan disimpan. Langkah ini adalah tempat aksi **create folder C#** terjadi, dan cukup sederhana berkat `Directory.CreateDirectory`. Metode ini idempotent—tidak akan melempar pengecualian jika folder sudah ada, sehingga menghindari pemeriksaan tambahan.

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**Mengapa ini penting:**  
Membuat folder terlebih dahulu menjamin bahwa langkah penyimpanan selanjutnya tidak akan gagal dengan `DirectoryNotFoundException`. Ini juga memberi Anda tata letak yang dapat diprediksi: `output/markdown` untuk file `.md` dan `output/MyImages` untuk setiap gambar yang kita ekstrak.

> **Tip pro:** Jika Anda menjalankan program berulang kali, Anda mungkin ingin membersihkan folder gambar terlebih dahulu (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`) agar tidak ada file usang.

---

## Konversi Word ke Markdown menggunakan Aspose.Words

Setelah pohon direktori siap, mari ubah dokumen Word menjadi markdown. Aspose.Words melakukan pekerjaan berat—tanpa harus berurusan dengan OpenXML atau konverter pihak ketiga.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**Apa yang terjadi di balik layar?**  
`MarkdownSaveOptions` memberi tahu Aspose untuk menghasilkan sintaks markdown. Secara default, pustaka akan menaruh gambar di folder yang sama dengan file markdown dengan nama yang dihasilkan otomatis. Dengan menyediakan `ResourceSavingCallback`, kita menyela perilaku itu dan **copy stream to file** ke lokasi pilihan kita.

---

## Ekstrak gambar dari DOCX dan simpan

Kelas callback mengimplementasikan `IResourceSavingCallback`. Di dalamnya kita menerima objek `ResourceSavingArgs` yang berisi aliran gambar asli dan nama file yang disarankan. Kita kemudian menulis aliran tersebut ke disk, mengganti nama file jika diinginkan, dan memberi tahu Aspose bahwa kita telah menanganinya.

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### Seperti apa markdownnya

Setelah konversi, file `output.md` yang dihasilkan akan berisi baris‑baris seperti:

```markdown
![Image 1](MyImages/img_picture1.png)
```

Karena kami mengubah `args.ResourceFileName` menjadi jalur relatif, markdown langsung menunjuk ke folder yang kami buat. Inilah yang diharapkan oleh generator situs statis.

**Penanganan kasus tepi:**  
*Jika dokumen berisi nama gambar yang duplikat*, awalan `img_` ditambah nama asli biasanya menghindari benturan, tetapi Anda juga dapat menambahkan GUID (`Guid.NewGuid()`) untuk keunikan mutlak.

---

## Copy stream to file – menangani data gambar

Anda mungkin bertanya mengapa tidak langsung memanggil `File.WriteAllBytes`. Jawabannya terletak pada **fleksibilitas stream**. `args.Stream` bisa berupa memory stream, network stream, atau implementasi lain. Dengan menggunakan `CopyTo`, kita tetap agnostik dan membiarkan .NET mengatur ukuran buffer secara efisien.

Berikut metode utilitas ringkas jika Anda pernah perlu menyalin stream generik ke tempat lain:

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

Anda dapat mengganti penyalinan inline di `ImageSavingCallback` dengan pemanggilan `CopyStreamToFile` jika lebih menyukai pendekatan tanggung jawab tunggal.

---

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian memberi Anda program mandiri yang dapat dijalankan dari baris perintah:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**Hasil yang diharapkan**

* `output/markdown/output.md` – file markdown yang referensi gambarnya terlihat seperti `![Alt text](MyImages/img_picture1.png)`.  
* `output/MyImages/` – satu file PNG/JPEG per gambar yang semula berada di dalam `input.docx`.  

Buka markdown di penampil apa pun (VS Code, GitHub, atau generator situs statis) dan Anda akan melihat gambar ditampilkan persis di tempatnya dalam file Word asli.

---

## Pertanyaan yang sering diajukan & pemecahan masalah

| Pertanyaan | Jawaban |
|----------|--------|
| **Bagaimana jika folder target sudah berisi file?** | `Directory.CreateDirectory` tidak akan menimpa. Jika Anda memerlukan run bersih, hapus |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}