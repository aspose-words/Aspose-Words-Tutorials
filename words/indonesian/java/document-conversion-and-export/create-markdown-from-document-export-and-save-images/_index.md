---
category: general
date: 2026-02-18
description: Buat markdown dari dokumen dengan langkah mudah untuk mengekspor dokumen
  ke markdown dan menyimpan gambar ke subfolder. Pelajari cara menyimpan dokumen sebagai
  markdown dalam C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: id
og_description: Buat markdown dari dokumen di C# dan pelajari cara mengekspor dokumen
  ke markdown sambil menyimpan gambar ke subfolder. Ikuti panduan langkah demi langkah.
og_title: Buat markdown dari dokumen – Ekspor dan simpan gambar
tags:
- C#
- Aspose.Words
- Markdown export
title: Buat markdown dari dokumen – Ekspor dan simpan gambar
url: /id/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat markdown dari dokumen – Ekspor dan simpan gambar

Pernah membutuhkan untuk **create markdown from document** tetapi tidak yakin bagaimana cara menjaga gambar yang disisipkan tetap rapi? Anda tidak sendirian. Dalam banyak proyek kami menghasilkan laporan, manual, atau draf blog secara programatis, dan hal terakhir yang kami inginkan adalah berkas‑berkas gambar berhamburan di folder output.

Dalam tutorial ini kami akan membahas solusi lengkap yang siap dijalankan untuk **export document to markdown**, menyimpan setiap gambar di sub‑folder *md‑resources* yang khusus, dan akhirnya **save document as markdown** menggunakan API Aspose.Words for .NET. Pada akhir tutorial Anda akan memiliki satu metode yang dapat disisipkan ke dalam kode C# mana pun, serta beberapa tips untuk menangani kasus pinggiran.

> **Sekilas cepat:**  
> • Siapkan `MarkdownSaveOptions`  
> • Sediakan `IResourceSavingCallback` yang mengarahkan gambar ke subfolder  
> • Panggil `Document.Save` dengan opsi yang telah dikonfigurasi  

Jika Anda penasaran mengapa kami memilih callback alih‑alih pemrosesan pasca‑ekspor, teruskan membaca – alasannya dijelaskan langkah demi langkah.

---

## Prasyarat

- .NET 6.0 atau yang lebih baru (kode ini juga berfungsi dengan .NET Framework 4.7+)  
- Aspose.Words for .NET (paket NuGet `Aspose.Words`)  
- Objek `Document` sumber (bisa .docx, .pdf, .rtf, dll.)  

Tidak diperlukan pustaka tambahan; API callback sudah terintegrasi dalam Aspose.Words.

---

## Langkah 1: Buat markdown dari dokumen – konfigurasikan opsi penyimpanan

Hal pertama yang kami lakukan adalah menginstansiasi `MarkdownSaveOptions`. Objek ini memberi tahu Aspose.Words bagaimana konversi harus berperilaku, seperti varian Markdown mana yang dipakai, apakah menyisipkan gambar sebagai Base64, dan ke mana menempatkan berkas‑berkas yang dihasilkan.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Mengapa ini penting:**  
> Tanpa secara eksplisit membuat `MarkdownSaveOptions`, perpustakaan akan kembali ke pengaturan default yang menyisipkan gambar langsung ke dalam berkas Markdown sebagai string Base64. Hal itu membuat berkas menjadi sangat besar dan menghilangkan tujuan memiliki folder *images* yang bersih.

---

## Langkah 2: Ekspor dokumen ke markdown dan definisikan penanganan sumber daya

Sekarang kami memberi tahu penyimpan **di mana** menaruh setiap gambar. Antarmuka `IResourceSavingCallback` memberikan hook yang dipicu untuk setiap sumber daya (gambar, SVG, dll.) yang ditemukan selama proses ekspor. Di dalam callback kami:

1. Memastikan folder target ada (`md-resources/`).  
2. Menetapkan `OutputFileName` ke folder ditambah nama sumber daya asli.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Pertanyaan umum:** *Bagaimana jika saya ingin menyisipkan gambar alih‑alih menyimpannya?*  
> Cukup lewati callback atau set `args.OutputFileName = null;` – penyimpan akan menyisipkan gambar sebagai string Base64 secara otomatis.

> **Kasus pinggiran:** Beberapa dokumen lama berisi nama gambar yang duplikat. Callback di atas akan menimpa berkas sebelumnya. Untuk menghindarinya, Anda dapat menambahkan GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Langkah 3: Simpan dokumen sebagai markdown dan verifikasi gambar yang tersimpan

Dengan opsi yang sudah sepenuhnya dikonfigurasi, panggilan akhir cukup satu baris yang menulis berkas Markdown serta gambar‑gambar terkait ke disk.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Jika semuanya berjalan lancar, Anda akan melihat:

- `MyReport.md` – representasi Markdown dari dokumen sumber Anda.  
- `md-resources/` – folder di samping berkas .md yang berisi setiap gambar yang diekstrak (misalnya `image001.png`, `image002.jpg`).  

**Potongan Markdown contoh** (dibuat otomatis oleh Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Tips pro:** Buka berkas `.md` yang dihasilkan di VS Code atau penampil Markdown apa pun; gambar seharusnya langsung ditampilkan karena jalur relatif cocok dengan struktur folder.

---

## Contoh lengkap yang dapat dijalankan

Berikut adalah program konsol mandiri yang dapat Anda tempel ke dalam proyek .NET baru dan jalankan. Program ini membuat dokumen Word sederhana, menambahkan gambar, lalu **create markdown from document** sambil menyimpan gambar di subfolder.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Apa yang akan Anda lihat** setelah menjalankan:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Buka `ExportedDoc.md` – referensi gambar akan mengarah ke `md-resources/sample-image.png`, dan gambar akan ditampilkan dengan benar di penampil Markdown mana pun.

---

## Variasi yang sering ditanyakan

| Skenario | Cara menyesuaikan kode |
|----------|------------------------|
| **Lewati ekspor gambar** (sisipkan sebagai Base64) | Hapus `ResourceSavingCallback` sepenuhnya, atau set `args.OutputFileName = null;` di dalam callback. |
| **Ubah format gambar** (misalnya semua PNG) | Di dalam callback, ubah `args.ResourceFileName` dan opsional konversi aliran sebelum menulis. |
| **Nama folder khusus** | Ganti `"md-resources/"` dengan jalur relatif atau absolut apa pun yang Anda inginkan. |
| **Banyak dokumen dalam satu batch** | Lakukan loop atas koleksi objek `Document`, gunakan kembali instance `MarkdownSaveOptions` yang sama (pastikan folder dibersihkan atau diberi nama unik per proses). |

---

## Kesimpulan

Kami baru saja menunjukkan **cara create markdown from document**, **export document to markdown**, dan **save images to subfolder** menggunakan pendekatan berbasis callback yang bersih. Poin penting yang dapat diambil:

- Gunakan `MarkdownSaveOptions` untuk mendapatkan kontrol halus atas proses ekspor.  
- Implementasikan `IResourceSavingCallback` untuk mengarahkan gambar ke folder khusus, menjaga Markdown Anda tetap rapi.  
- Pola yang sama berlaku untuk tipe sumber daya lain (SVG, audio) – cukup periksa `args.ResourceType`.  

Selanjutnya, Anda dapat menjelajahi **saving document as markdown** dengan gaya heading khusus, atau mengintegrasikan rutinitas ini ke dalam ASP.NET Web API yang mengembalikan ZIP berisi berkas `.md` dan sumber dayanya. Bagaimanapun, blok‑blok bangunan kini sudah ada di kotak peralatan Anda.

Punya pertanyaan, atau menemukan kasus pinggiran yang belum kami bahas? Tinggalkan komentar di bawah, dan selamat coding!

---

![buat markdown dari dokumen contoh](placeholder.png "buat markdown dari dokumen contoh")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}