---
category: general
date: 2026-03-30
description: Cara menyimpan file markdown di C# sambil mengekstrak gambar dari markdown
  dan menyimpan dokumen sebagai markdown menggunakan Aspose.Words.
draft: false
keywords:
- how to save markdown
- extract images from markdown
- save document as markdown
- markdown resource handling
- C# markdown export
language: id
og_description: Cara menyimpan markdown dengan cepat. Pelajari cara mengekstrak gambar
  dari markdown dan menyimpan dokumen sebagai markdown dengan contoh kode lengkap.
og_title: Cara Menyimpan Markdown – Panduan Lengkap C#
tags:
- C#
- Markdown
- Aspose.Words
title: Cara Menyimpan Markdown – Panduan Lengkap dengan Ekstraksi Gambar
url: /id/net/programming-with-markdownsaveoptions/how-to-save-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyimpan Markdown – Panduan Lengkap C#

Pernah bertanya-tanya **bagaimana cara menyimpan markdown** sambil menjaga semua gambar tersemat tetap utuh? Anda bukan satu-satunya. Banyak pengembang mengalami kebuntuan ketika perpustakaan mereka menaruh gambar ke folder acak atau, lebih buruk lagi, tidak menyertakannya sama sekali. Kabar baik? Dengan beberapa baris C# dan Aspose.Words Anda dapat mengekspor dokumen ke markdown, mengekstrak setiap gambar, dan mengontrol tepat di mana setiap file disimpan.

Dalam tutorial ini kami akan membahas skenario dunia nyata: mengambil objek `Document`, mengonfigurasi `MarkdownSaveOptions`, dan memberi tahu penyimpan ke mana menaruh setiap gambar. Pada akhir tutorial Anda akan dapat **menyimpan dokumen sebagai markdown**, **mengekstrak gambar dari markdown**, dan memiliki struktur folder yang rapi siap untuk dipublikasikan. Tanpa referensi yang samar—hanya contoh lengkap yang dapat dijalankan dan Anda dapat menyalin‑tempel.

## Apa yang Anda Butuhkan

- **.NET 6+** (SDK terbaru apa pun dapat digunakan)
- **Aspose.Words for .NET** (paket NuGet `Aspose.Words`)
- Pemahaman dasar tentang sintaks C# (kami akan membuatnya sederhana)
- Instance `Document` yang sudah ada (kami akan membuat satu untuk tujuan demo)

Jika Anda sudah memiliki semua itu, mari kita mulai.

## Langkah 1: Siapkan Proyek dan Impor Namespace

Pertama, buat aplikasi console baru (atau integrasikan ke dalam solusi Anda yang sudah ada). Kemudian tambahkan paket Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Sekarang impor namespace yang diperlukan:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

> **Tip pro:** Letakkan pernyataan `using` Anda di bagian atas file; ini membuat kode lebih mudah dipindai baik oleh manusia maupun parser AI.

## Langkah 2: Buat Dokumen Contoh (atau muat milik Anda sendiri)

Untuk demonstrasi kami akan membuat dokumen kecil yang berisi paragraf dan gambar tersemat. Ganti bagian ini dengan `Document.Load("YourFile.docx")` jika Anda sudah memiliki file sumber.

```csharp
// Step 2: Build a simple document with an image
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Add some text
builder.Writeln("Hello, Markdown world!");

// Insert an image from disk (make sure the path exists)
string imagePath = @"YOUR_DIRECTORY/sample-image.png";
builder.InsertImage(imagePath);
```

> **Mengapa ini penting:** Jika Anda melewatkan gambar, tidak ada yang dapat *diekstrak* nanti, dan Anda tidak akan melihat callback beraksi.

## Langkah 3: Konfigurasikan MarkdownSaveOptions dengan Callback Penyimpanan Sumber Daya

Berikut inti solusi. `ResourceSavingCallback` dipicu untuk **setiap** sumber daya eksternal—gambar, font, CSS, dll. Kami akan menggunakannya untuk membuat sub‑folder `Resources` khusus dan memberi setiap file nama unik.

```csharp
// Step 3: Define markdown save options and attach a callback
var markdownSaveOptions = new MarkdownSaveOptions
{
    // This delegate runs for each resource the saver wants to write out
    ResourceSavingCallback = (sender, args) =>
    {
        // Ensure the Resources folder exists (creates it only once)
        string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename: img_0.png, img_1.jpg, etc.
        string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Tell the saver where to place the file
        args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
    }
};
```

**Apa yang terjadi?**  
- `args.Index` adalah penghitung berbasis nol, menjamin keunikan.  
- `Path.GetExtension(args.FileName)` mempertahankan tipe file asli (PNG, JPG, dll.).  
- Dengan mengatur `args.SavePath`, kami mengganti lokasi default dan menjaga semuanya tetap rapi.

## Langkah 4: Simpan Dokumen sebagai Markdown

Dengan opsi yang sudah disiapkan, proses ekspor menjadi satu baris:

```csharp
// Step 4: Export to markdown using the configured options
string outputMarkdown = @"YOUR_DIRECTORY/Doc.md";
doc.Save(outputMarkdown, markdownSaveOptions);
```

Setelah dijalankan Anda akan menemukan:

- `Doc.md` yang berisi teks markdown yang merujuk ke gambar.  
- Folder `Resources` di sampingnya berisi `img_0.png`, `img_1.jpg`, …  

Itulah alur **cara menyimpan markdown**, lengkap dengan ekstraksi sumber daya.

## Langkah 5: Verifikasi Hasil (Opsional tetapi Disarankan)

Buka `Doc.md` di editor teks apa pun. Anda seharusnya melihat sesuatu seperti:

```markdown
Hello, Markdown world!

![image](Resources/img_0.png)
```

Dan folder `Resources` akan berisi gambar asli yang Anda sisipkan. Jika Anda membuka file markdown di penampil (misalnya, VS Code, GitHub), gambar akan ditampilkan dengan benar.

> **Pertanyaan umum:** *Bagaimana jika saya ingin gambar berada di folder yang sama dengan file markdown?*  
> Cukup ubah `resourcesFolder` menjadi `Path.GetDirectoryName(outputMarkdown)` dan sesuaikan jalur gambar markdown sesuai.

## Ekstrak Gambar dari Markdown – Penyesuaian Lanjutan

Terkadang Anda memerlukan kontrol lebih pada konvensi penamaan atau ingin melewatkan tipe sumber daya tertentu. Berikut beberapa variasi yang mungkin berguna.

### 5.1 Lewati Sumber Daya Non‑Gambar

```csharp
ResourceSavingCallback = (sender, args) =>
{
    // Only process images; ignore CSS, fonts, etc.
    if (!args.ContentType.StartsWith("image/", StringComparison.OrdinalIgnoreCase))
        return; // Let the default handling continue

    // ...same folder creation logic as before...
};
```

### 5.2 Pertahankan Nama File Asli

Jika Anda lebih suka nama file asli alih-alih `img_0`, cukup hilangkan bagian `args.Index`:

```csharp
string resourceFileName = args.FileName; // uses the name from the source document
```

### 5.3 Gunakan Sub‑Folder Kustom per Dokumen

```csharp
string docName = Path.GetFileNameWithoutExtension(outputMarkdown);
string resourcesFolder = $@"YOUR_DIRECTORY/{docName}_Resources/";
Directory.CreateDirectory(resourcesFolder);
```

Potongan kode ini menggambarkan **ekstrak gambar dari markdown** secara fleksibel, menyesuaikan dengan konvensi proyek yang berbeda.

## Pertanyaan yang Sering Diajukan (FAQ)

| Question | Answer |
|----------|--------|
| **Apakah ini bekerja dengan .NET Core?** | Tentu—Aspose.Words bersifat lintas‑platform, sehingga kode yang sama dapat dijalankan di Windows, Linux, atau macOS. |
| **Bagaimana dengan gambar SVG?** | SVG diperlakukan sebagai gambar; callback akan menerima ekstensi `.svg`. Pastikan penampil markdown Anda mendukung SVG. |
| **Bisakah saya mengubah sintaks markdown (misalnya, menggunakan tag HTML `<img>`)?** | Setel `markdownSaveOptions.ExportImagesAsBase64 = false` dan sesuaikan `ExportImagesAsHtml` jika Anda memerlukan tag HTML mentah. |
| **Apakah ada cara untuk memproses banyak dokumen secara batch?** | Bungkus logika di atas dalam loop `foreach` atas koleksi file—hanya ingat untuk memberi setiap dokumen folder sumber daya masing-masing. |

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a document and add an image
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, Markdown world!");
        string imagePath = @"YOUR_DIRECTORY/sample-image.png"; // <-- change this
        builder.InsertImage(imagePath);

        // 2️⃣ Configure save options with a callback to extract images
        var markdownSaveOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
                args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
            }
        };

        // 3️⃣ Save as markdown
        string outputPath = @"YOUR_DIRECTORY/Doc.md";
        doc.Save(outputPath, markdownSaveOptions);

        Console.WriteLine("Markdown saved successfully!");
        Console.WriteLine($"Check {outputPath} and the Resources folder for images.");
    }
}
```

Jalankan program (`dotnet run`) dan Anda akan melihat pesan konsol yang mengonfirmasi keberhasilan. Semua gambar kini tersimpan rapi, dan file markdown menunjuk ke mereka dengan benar.

## Kesimpulan

Anda baru saja mempelajari **cara menyimpan markdown** sambil **mengekstrak gambar dari markdown** dan memastikan dokumen dapat **disimpan sebagai markdown** dengan kontrol penuh atas lokasi sumber daya. Inti pentingnya adalah `ResourceSavingCallback`—ia memberi Anda otoritas terperinci atas setiap file eksternal yang dihasilkan oleh exporter.

Dari sini Anda dapat:

- Integrasikan alur ini ke dalam layanan web yang mengonversi file DOCX yang diunggah pengguna menjadi markdown secara langsung.  
- Perluas callback untuk mengganti nama file berdasarkan konvensi penamaan yang cocok dengan CMS Anda.  
- Gabungkan dengan fitur Aspose.Words lainnya seperti `ExportImagesAsBase64` untuk markdown dengan gambar inline.

Cobalah, sesuaikan logika folder agar cocok dengan proyek Anda, dan biarkan output markdown bersinar dalam alur dokumentasi Anda.

--- 

![how to save markdown example](/assets/how-to-save-markdown.png "how to save markdown example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}