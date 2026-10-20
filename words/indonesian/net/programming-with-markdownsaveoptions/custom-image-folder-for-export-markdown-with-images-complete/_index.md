---
category: general
date: 2026-06-20
description: Folder gambar khusus memungkinkan Anda mengekspor markdown dengan gambar
  dengan mudah. Pelajari cara menyimpan gambar ke direktori tertentu dan menyimpan
  gambar markdown di .NET.
draft: false
keywords:
- custom image folder
- export markdown with images
- save images specific directory
- save markdown images
language: id
og_description: Folder gambar khusus memudahkan mengekspor markdown dengan gambar.
  Ikuti panduan langkah demi langkah ini untuk menyimpan gambar ke direktori tertentu
  dan menyimpan gambar markdown.
og_title: folder gambar khusus – Ekspor Markdown dengan Gambar
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  headline: custom image folder for export markdown with images – Complete Guide
  type: TechArticle
- description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  name: custom image folder for export markdown with images – Complete Guide
  steps:
  - name: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
    text: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
  - name: Eliminates a second file‑system scan, which can be costly for large docs.
    text: Eliminates a second file‑system scan, which can be costly for large docs.
  - name: Gives you the flexibility to rename or compress images on the fly.
    text: Gives you the flexibility to rename or compress images on the fly.
  type: HowTo
tags:
- Aspose.Words
- Markdown
- .NET
title: Folder gambar khusus untuk mengekspor markdown dengan gambar – Panduan Lengkap
url: /id/net/programming-with-markdownsaveoptions/custom-image-folder-for-export-markdown-with-images-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# folder gambar khusus – Ekspor Markdown dengan Gambar di .NET

Pernah membutuhkan **folder gambar khusus** saat mengekspor markdown dengan gambar? Anda bukan satu‑satunya yang mengalami hal itu. Baik Anda membuat dokumentasi, posting blog, atau panduan API, menyimpan gambar Anda rapi dalam direktori khusus akan menghindarkan Anda dari struktur file yang berantakan di kemudian hari.

Dalam tutorial ini kami akan menelusuri solusi lengkap yang siap dijalankan yang menunjukkan **cara menyimpan gambar ke direktori khusus** saat membuat file markdown. Anda akan melihat mengapa menggunakan callback adalah cara paling bersih, dan Anda akan mengakhiri panduan dengan contoh kode lengkap yang dapat Anda masukkan ke proyek .NET apa pun.

## Apa yang Akan Anda Pelajari

- Mengonfigurasi Aspose.Words (atau perpustakaan serupa) untuk mengarahkan penyimpanan gambar.
- Mengimplementasikan callback yang menulis setiap gambar ke **folder gambar khusus**.
- Menggunakan `MarkdownSaveOptions` untuk mengikat semuanya bersama dan **menyimpan gambar markdown** dengan benar.
- Tips menangani kasus tepi seperti nama duplikat atau file besar.

### Prasyarat

| Persyaratan | Mengapa penting |
|-------------|-----------------|
| .NET 6+ (atau .NET Framework 4.7+) | Kode menggunakan `FileStream` dan `Guid`. |
| Aspose.Words for .NET (atau exporter markdown yang sebanding) | Menyediakan `MarkdownSaveOptions` dan antarmuka callback. |
| Pengetahuan dasar C# | Anda perlu memahami kelas dan stream. |
| Objek `Document` yang sudah ada (`doc`) | Tutorial mengasumsikan Anda sudah memiliki dokumen yang terisi. |

Tidak ada alat eksternal selain yang disebutkan yang diperlukan—semuanya berjalan secara lokal.

## Langkah 1: Definisikan Callback yang Menyimpan Setiap Gambar di Folder Gambar Khusus

Inti dari solusi ini adalah kelas yang mengimplementasikan `IResourceSavingCallback`. Di dalam `ResourceSaving` kami menghasilkan nama file unik, membangun jalur lengkap di dalam folder yang Anda pilih, lalu memberi tahu perpustakaan untuk menulis gambar ke sana.

```csharp
// Step 1: Define a callback that stores each image in a custom folder
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique file name for the image
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Build the full path inside the desired resources directory
        var fullPath = Path.Combine("YOUR_DIRECTORY", fileName);

        // Redirect the saving stream to the new location
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;   // close after save

        // Update the markdown reference to point to the new file name
        args.ResourceFileName = fileName;
    }
}
```

**Mengapa ini berhasil:**  
- `Guid.NewGuid()` menjamin nama yang unik, mencegah bentrok ketika dokumen sumber berisi beberapa gambar dengan nama file asli yang sama.  
- Dengan mengganti `args.Stream` kami memberi tahu exporter tepat di mana menulis data biner.  
- Memperbarui `args.ResourceFileName` memastikan referensi markdown (`![](img_…​)`) mengarah ke file yang kini berada di **folder gambar khusus** Anda.

> **Pro tip:** Ganti `"YOUR_DIRECTORY"` dengan jalur yang dibangun dari `Path.Combine(Environment.CurrentDirectory, "Images")` jika Anda ingin folder tersebut berada di samping file markdown secara otomatis.

## Langkah 2: Sambungkan Callback ke Markdown Save Options

Selanjutnya kami membuat instance `MarkdownSaveOptions` dan menetapkan callback kami. Ini memberi tahu exporter untuk memanggil `ImageSavingCallback` untuk setiap sumber daya tersemat yang ditemukannya.

```csharp
// Step 2: Configure Markdown save options to use the callback
var markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ImageSavingCallback()
};
```

**Apa yang terjadi di balik layar?**  
Saat `doc.Save` dijalankan, Aspose.Words menelusuri pohon node dokumen. Setiap kali menemukan gambar, ia memicu `ResourceSaving`. Callback kami menangkap event tersebut, mengarahkan ulang stream gambar, dan memperbarui tautan markdown. Hasilnya? Semua gambar berakhir di folder yang Anda tentukan, dan file markdown merujuknya dengan benar.

## Langkah 3: Simpan Dokumen sebagai Markdown – Gambar Disimpan melalui Callback

Akhirnya, kami memanggil `Save` dengan objek opsi. Perpustakaan melakukan pekerjaan berat; callback kami mengatur penempatan file.

```csharp
// Step 3: Save the document as Markdown; images are saved via the callback
doc.Save("YOUR_DIRECTORY/DocWithImages.md", markdownOptions);
```

Jika `"YOUR_DIRECTORY"` adalah `C:\Docs\MyProject`, Anda akan melihat:

```
C:\Docs\MyProject\DocWithImages.md
C:\Docs\MyProject\img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png
C:\Docs\MyProject\img_7e8f9a0b‑c1d2‑3e4f‑5g6h‑7i8j9k0l1m2n.jpg
```

File markdown berisi baris‑baris seperti:

```markdown
![Image](img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png)
```

Itulah tepatnya yang Anda butuhkan untuk **menyimpan gambar markdown** di lokasi yang dapat diprediksi.

## Contoh Lengkap yang Berfungsi

Berikut adalah aplikasi console mandiri yang dapat Anda salin‑tempel ke Visual Studio. Ia membuat dokumen sederhana dengan gambar, lalu mengekspornya menggunakan pendekatan folder khusus.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, markdown with images!");
        builder.InsertImage("sample.jpg"); // Ensure sample.jpg exists next to the exe

        // 2️⃣ Define the callback (same as earlier)
        var options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback()
        };

        // 3️⃣ Choose output folder (feel free to change)
        string outputDir = Path.Combine(Environment.CurrentDirectory, "Exported");
        Directory.CreateDirectory(outputDir); // creates if missing

        // 4️⃣ Save markdown and images
        string mdPath = Path.Combine(outputDir, "Document.md");
        doc.Save(mdPath, options);

        Console.WriteLine($"Markdown saved to: {mdPath}");
        Console.WriteLine("Images stored in the same folder.");
    }
}

// Callback class – identical to the earlier snippet
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
        var fullPath = Path.Combine("Exported", fileName);
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;
        args.ResourceFileName = fileName;
    }
}
```

**Output yang diharapkan**

Menjalankan program mencetak sesuatu seperti:

```
Markdown saved to: C:\MyApp\Exported\Document.md
Images stored in the same folder.
```

Buka `Document.md` dan Anda akan melihat referensi gambar markdown yang mengarah ke `img_…​`. File gambar berada tepat di sebelah file markdown, persis seperti yang ditentukan oleh desain **folder gambar khusus**.

## Menangani Kasus Tepi yang Umum

| Situasi | Solusi |
|---------|--------|
| **Nama file duplikat** | Menggunakan `Guid` sudah menghindari duplikat; jika Anda lebih suka nama yang dapat dibaca, tambahkan penghitung (`img_001.png`, `img_002.png`). |
| **Set gambar besar** | Stream langsung ke disk seperti yang ditunjukkan; hindari memuat seluruh gambar ke memori. |
| **Direktori output berbeda per run** | Kirim folder target sebagai argumen konstruktor ke `ImageSavingCallback` alih‑alih menuliskan `"Exported"` secara keras. |
| **Tidak ada izin menulis** | Pastikan aplikasi berjalan dengan hak yang cukup atau pilih folder yang dapat ditulis pengguna seperti `%TEMP%`. |
| **Sumber daya non‑gambar (misalnya CSS)** | Callback dipicu untuk semua sumber daya; Anda dapat memeriksa `args.ResourceType` dan menangani hanya gambar. |

## Mengapa Menggunakan Callback Daripada Post‑Processing?

Anda mungkin bertanya, “Mengapa tidak menghasilkan markdown dulu, lalu memindahkan gambar setelahnya?” Pendekatan callback:

1. Menjamin **atomisitas** – gambar dan markdown ditulis bersamaan, mencegah tautan rusak.  
2. Menghilangkan pemindaian sistem file kedua, yang dapat mahal untuk dokumen besar.  
3. Memberi Anda fleksibilitas untuk mengganti nama atau mengompres gambar secara langsung.

Singkatnya, ini adalah cara **paling kuat untuk mengekspor markdown dengan gambar** sambil menjaga semuanya dalam **folder gambar khusus**.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **menyimpan gambar ke direktori khusus** dan **menyimpan gambar markdown** menggunakan strategi **folder gambar khusus**. Dengan mengimplementasikan `IResourceSavingCallback`, mengonfigurasi `MarkdownSaveOptions`, dan memanggil `doc.Save`, Anda mendapatkan tata letak folder yang bersih dan referensi markdown yang dapat diandalkan—semua dalam beberapa puluh baris kode.

Selanjutnya, Anda dapat menjelajahi:

- Menambahkan kompresi gambar di dalam callback.  
- Menghasilkan `README.md` yang secara otomatis menautkan ke folder.  
- Memperluas callback untuk menangani tipe sumber daya lain seperti CSS atau skrip.

Cobalah dalam pipeline dokumentasi berikutnya—diri Anda di masa depan akan berterima kasih atas struktur folder yang rapi.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang berhubungan erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}