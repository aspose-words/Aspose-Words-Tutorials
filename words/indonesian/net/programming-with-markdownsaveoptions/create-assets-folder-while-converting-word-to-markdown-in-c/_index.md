---
category: general
date: 2026-01-02
description: Buat folder assets dan konversi Word ke Markdown dengan Aspose.Words.
  Pelajari cara mengekstrak gambar dari docx dan menyimpan docx sebagai markdown menggunakan
  C#.
draft: false
keywords:
- create assets folder
- convert word to markdown
- extract images from docx
- save docx as markdown
- docx to markdown c#
language: id
og_description: Buat folder assets dan konversi Word ke Markdown menggunakan Aspose.Words.
  Tutorial ini menunjukkan cara mengekstrak gambar dari docx dan menyimpan docx sebagai
  markdown dalam C#.
og_title: Buat folder aset saat mengonversi Word ke Markdown – Panduan C#
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Buat folder aset saat mengonversi Word ke Markdown di C#
url: /id/net/programming-with-markdownsaveoptions/create-assets-folder-while-converting-word-to-markdown-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat folder aset saat mengonversi Word ke Markdown dalam C#

Pernahkah Anda perlu **membuat folder aset** saat mengubah dokumen Word menjadi Markdown? Anda tidak sendirian. Banyak pengembang mengalami masalah ketika gambar dan sumber daya tersemat lainnya hilang dalam konversi, meninggalkan tautan yang rusak di file `.md` yang dihasilkan.  

Kabar baik? Dengan Aspose.Words Anda dapat **mengonversi Word ke Markdown** dan secara otomatis menaruh setiap gambar ke dalam direktori `assets` yang rapi—tanpa perlu menyalin secara manual. Dalam tutorial ini kami akan membahas seluruh proses, mulai dari memuat file `.docx`, mengekstrak gambar, menyimpan markdown, dan tentu saja membuat folder aset yang Anda cari.

Pada akhir tutorial Anda akan dapat **menyimpan docx sebagai markdown**, semua gambar tersimpan rapi, dan memahami cara menyesuaikan alur untuk kasus tepi seperti PDF besar atau skema penamaan gambar khusus. Siap? Mari kita mulai.

---

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (v23.12 atau lebih baru). Perpustakaan ini gratis untuk percobaan; lisensi menghilangkan watermark evaluasi.
- **.NET 6+** (atau .NET Framework 4.7.2+ jika Anda lebih suka runtime klasik).
- IDE C# dasar (Visual Studio, Rider, atau VS Code dengan ekstensi C#).
- Contoh `input.docx` yang berisi setidaknya satu gambar, sehingga kita dapat melihat langkah **extract images from docx** dalam aksi.

Tidak diperlukan paket NuGet tambahan selain Aspose.Words.

---

## Langkah 1: Siapkan Proyek Anda dan Instal Aspose.Words

Pertama, buat aplikasi console:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> Pro tip: Jika Anda menggunakan Visual Studio, cukup buat proyek “Console App (.NET Core)” baru dan tambahkan paket NuGet melalui UI Package Manager.

Setelah paket terpasang, buka `Program.cs`. Kami akan mulai dengan menambahkan direktif `using` yang diperlukan:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;
```

Namespace ini memberi kami akses ke kelas `Document`, `MarkdownSaveOptions`, dan pembantu sistem file yang kami perlukan untuk langkah **create assets folder**.

---

## Langkah 2: Muat Dokumen Word Sumber

Memuat sebuah `.docx` semudah mengarahkan konstruktor `Document` ke jalur file. Pastikan file berada di lokasi yang dapat dibaca aplikasi Anda—sebaiknya berdampingan dengan executable untuk demo ini.

```csharp
// Step 2: Load the source Word document
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

if (!File.Exists(inputPath))
{
    Console.WriteLine($"❌ Could not find {inputPath}. Drop a Word file there and try again.");
    return;
}

Document doc = new Document(inputPath);
Console.WriteLine("✅ Loaded input.docx successfully.");
```

Mengapa kami memeriksa `File.Exists`? Karena file yang hilang adalah penyebab paling umum saat Anda pertama kali mencoba **convert word to markdown**. Guard clause ini memberikan pesan error yang ramah alih-alih pengecualian yang membingungkan.

---

## Langkah 3: Konfigurasikan Opsi Markdown dan Callback Penyimpanan Aset

Aspose.Words memungkinkan kami menyambungkan ke pipeline penyimpanan melalui `IResourceSavingCallback`. Di sinilah kami akan **create assets folder** dan memberi setiap gambar nama yang unik.

```csharp
// Step 3: Configure Markdown save options and attach a resource‑saving callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Use a callback to control where each resource (image, etc.) ends up
    ResourceSavingCallback = new MyResourceCallback()
};
```

Kelas callback berada beberapa baris di bawah. Ia melakukan tiga hal:

1. Memastikan direktori `assets` ada.
2. Menghasilkan nama file berbasis GUID untuk menghindari tabrakan.
3. Memperbarui `args.ResourceFileName` sehingga Aspose menulis file ke lokasi yang tepat.

---

## Langkah 4: Implementasikan Callback Penyimpanan Sumber Daya (Buat Folder Aset)

Berikut implementasi lengkapnya. Perhatikan komentar yang banyak—ini membuat tutorial **citation‑worthy** karena siapa pun dapat mengikuti logika tanpa menebak.

```csharp
// Step 4: Callback that stores each resource (e.g., images) in an assets folder
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // -----------------------------------------------------------------
        // 1️⃣ Decide where the assets folder lives.
        //    You can make this configurable, but for this demo we’ll
        //    place it next to the output markdown file.
        // -----------------------------------------------------------------
        string outputDir = Path.GetDirectoryName(args.DocumentFileName);
        string assetsFolder = Path.Combine(outputDir, "assets");

        // Ensure the folder exists – this is the core of “create assets folder”
        Directory.CreateDirectory(assetsFolder);

        // -----------------------------------------------------------------
        // 2️⃣ Generate a unique file name.
        //    Using a GUID prevents name clashes when the source doc has
        //    multiple images with the same original name.
        // -----------------------------------------------------------------
        string extension = Path.GetExtension(args.ResourceFileName);
        string uniqueName = $"{Guid.NewGuid()}{extension}";

        // -----------------------------------------------------------------
        // 3️⃣ Tell Aspose where to write the file.
        //    The markdown will reference this relative path.
        // -----------------------------------------------------------------
        args.ResourceFileName = Path.Combine(assetsFolder, uniqueName);

        // No need to set args.Cancel = true; the default saving will continue.
    }
}
```

> **Mengapa GUID?** Jika Anda hanya menggunakan kembali `args.ResourceFileName`, dua gambar bernama `image1.png` dapat menimpa satu sama lain. GUID menjamin keunikan, yang sangat berguna ketika Anda **extract images from docx** yang berisi banyak nama file identik.

---

## Langkah 5: Simpan Dokumen sebagai Markdown

Sekarang kami siap menjalankan konversi. File output akan berada di samping folder `assets`, dan markdown akan berisi tautan relatif seperti `![Image](assets/123e4567-e89b-12d3-a456-426614174000.png)`.

```csharp
// Step 5: Save the document as Markdown; the callback will handle embedded resources
string outputPath = Path.Combine(Environment.CurrentDirectory, "output", "report.md");

// Ensure the output directory exists
Directory.CreateDirectory(Path.GetDirectoryName(outputPath));

doc.Save(outputPath, mdOptions);
Console.WriteLine($"✅ Markdown saved to {outputPath}");
Console.WriteLine("📁 Assets folder created at: " + Path.Combine(Path.GetDirectoryName(outputPath), "assets"));
```

Menjalankan program sekarang menghasilkan:

- `output/report.md` – versi markdown dari file Word Anda.
- `output/assets/` – folder yang berisi semua gambar yang diekstrak.

Buka `report.md` di penampil markdown apa pun (pratinjau VS Code, GitHub, dll.) dan Anda akan melihat gambar ditampilkan dengan benar.

---

## Langkah 6: Verifikasi Hasil – Seperti Apa Markdownnya

Berikut cuplikan dari markdown yang dihasilkan setelah konversi:

```markdown
# Sample Document

Here’s a paragraph with an image:

![Image](assets/4f3c2a1b-9e6d-4b2f-a9d3-0c9e5d6f7a12.png)

Another paragraph follows...
```

Jika Anda membuka file markdown dan gambar muncul, Anda telah berhasil **save docx as markdown** sementara folder aset menyimpan setiap gambar yang Anda perlukan untuk **extract images from docx**.

---

## Pertanyaan Umum & Kasus Tepi

### 1️⃣ Bagaimana jika file Word berisi grafik SVG atau EMF?

Aspose.Words mengonversi kebanyakan format vektor ke PNG secara default saat menyimpan ke Markdown. Jika Anda memerlukan format asli, Anda dapat menyesuaikan `mdOptions.ImageSavingOptions` (misalnya, set `ImageSavingOptions.ImageFormat = ImageSaveOptions.SaveFormat.Svg`). Ingat untuk memperbarui callback agar mempertahankan ekstensi file yang benar.

### 2️⃣ Bagaimana cara mengontrol nama folder aset?

Cukup ganti `"assets"` dalam `MyResourceCallback` dengan string apa pun yang Anda inginkan, atau bacalah dari file konfigurasi:

```csharp
string assetsFolder = Path.Combine(outputDir, ConfigurationManager.AppSettings["AssetsFolderName"]);
```

### 3️⃣ Dokumen saya memiliki ratusan gambar beresolusi tinggi. Apakah ini akan membebani memori?

Aspose.Words menyalurkan sumber daya ke disk satu per satu, sehingga konsumsi memori tetap rendah. Namun, total ukuran folder aset akan sama dengan ukuran gambar yang tersemat. Pertimbangkan untuk mengompresnya setelah konversi jika penyimpanan menjadi masalah.

### 4️⃣ Saya membutuhkan markdown yang merujuk gambar melalui URL absolut (misalnya untuk generator situs statis). Bisakah saya melakukannya?

Ya. Di dalam callback Anda dapat menambahkan URL dasar di depan nama file:

```csharp
string baseUrl = "https://cdn.example.com/docs/assets/";
args.ResourceFileName = baseUrl + uniqueName;
```

Pastikan file diunggah ke lokasi yang sama dengan URL yang ditunjuk.

### 5️⃣ Apakah ini bekerja dengan file `.doc` (Word biner)?

Tentu saja. Konstruktor `Document` secara otomatis mendeteksi format, sehingga Anda dapat memberi file `.doc` dan pipeline yang sama akan mengonversinya ke Markdown, mengekstrak gambar dengan cara yang sama.

---

## Tips Pro untuk Konversi Siap Produksi

- **Pemrosesan Batch:** Bungkus logika konversi dalam loop `foreach` yang iterasi melalui folder berisi file `.docx`. Gunakan satu instance `MyResourceCallback` dan pakai kembali untuk meningkatkan kecepatan.
- **Logging:** Gunakan kerangka kerja logging (Serilog, NLog) alih-alih `Console.WriteLine` untuk aplikasi dunia nyata. Log nama gambar asli untuk jejak audit.
- **Penanganan Error:** Bungkus pemanggilan `doc.Save` dengan blok try‑catch yang menangkap pengecualian `Aspose.Words`. Seringkali pengecualian muncul ketika fitur yang tidak didukung (seperti objek OLE) ada.
- **Unit Test:** Tulis tes yang memberi `.docx` dengan dua gambar dan memastikan folder `assets` berisi tepat dua file setelah konversi. Ini melindungi dari regresi saat memperbarui Aspose.

---

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document
            string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
            if (!File.Exists(inputPath))
            {
                Console.WriteLine($"❌ {inputPath} not found.");
                return;
            }

            Document doc = new Document(inputPath);
            Console.WriteLine("✅ Loaded input.docx");

            // 2️⃣ Configure save options with our callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceCallback()
            };

            // 3️⃣ Prepare output location
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output", "report.md");
            Directory.CreateDirectory(Path.GetDirectoryName(outputPath));

            // 4️⃣ Save as Markdown (assets folder will be created automatically)
            doc.Save(outputPath, mdOptions);
            Console.WriteLine($"✅ Markdown saved to {outputPath}");
            Console.WriteLine("📁 Assets folder: " + Path.Combine(Path.GetDirectoryName(outputPath), "assets"));
        }
    }

    // 5️⃣ Callback that creates the assets folder and gives each image a unique name

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}