---
category: general
date: 2026-01-14
description: Pelajari cara menggunakan callback di C# untuk mengonversi DOCX ke markdown,
  mengekstrak gambar dari Word, dan menghasilkan nama gambar yang unik.
draft: false
keywords:
- how to use callback
- convert docx to markdown
- extract images from word
- save word as markdown
- generate unique image names
language: id
og_description: Cara menggunakan callback di C# untuk mengonversi DOCX ke markdown,
  mengekstrak gambar, dan menghasilkan nama gambar unik.
og_title: Cara Menggunakan Callback di C# – Mengonversi DOCX ke Markdown
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: Cara Menggunakan Callback di C# – Mengonversi DOCX ke Markdown
url: /id/net/programming-with-markdownsaveoptions/how-to-use-callback-in-c-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggunakan Callback di C# – Mengonversi DOCX ke Markdown

Pernah bertanya-tanya **bagaimana cara menggunakan callback** ketika Anda perlu mengubah dokumen Word menjadi markdown yang bersih? Anda bukan satu-satunya. Kebanyakan pengembang menemui kendala ketika konversi menghasilkan sekumpulan file gambar dengan nama yang bentrok atau ketika markdown mengarah ke folder yang salah. Kabar baiknya? Dengan callback khusus yang kecil, Anda dapat mengontrol tepat di mana setiap sumber disimpan, memberi setiap gambar nama yang unik, dan menjaga markdown Anda tetap rapi.

Dalam panduan ini kami akan menelusuri seluruh proses: memuat sebuah `.docx`, mengonfigurasi callback yang memutuskan **di mana** dan **bagaimana** gambar disimpan, dan akhirnya menulis hasilnya sebagai markdown. Pada akhir panduan Anda akan dapat **mengonversi docx ke markdown**, **mengekstrak gambar dari Word**, dan **menghasilkan nama gambar unik** tanpa harus mengangkat jari setiap kali. Tanpa skrip eksternal, hanya C# murni dan Aspose.Words.

> **Prasyarat**  
> • .NET 6+ (atau .NET Framework 4.7+) terpasang  
> • Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)  
> • Pemahaman dasar tentang kelas C# dan I/O file  

---

![diagram cara menggunakan callback](https://example.com/images/callback-diagram.png "Diagram yang menunjukkan cara menggunakan callback untuk ekstraksi gambar")

## Cara Menggunakan Callback Saat Menyimpan Sumber Daya

Inti solusi berada dalam sebuah kelas yang mengimplementasikan `IResourceSavingCallback`. Aspose.Words memanggil antarmuka ini untuk setiap sumber eksternal (seperti gambar) yang perlu ditulis ke disk. Dengan menimpa `ResourceSaving` kita mendapatkan kontrol penuh atas jalur target dan nama file.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Custom callback that decides where each image extracted from a Word document will be saved.
/// </summary>
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Choose the folder where images will be stored.
        string folder = @"YOUR_DIRECTORY/Images/";

        // 2️⃣ Create a unique name – Guid guarantees no collisions.
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // 3️⃣ Combine folder and file name, then tell Aspose to use it.
        args.SavePath = Path.Combine(folder, uniqueName);
        args.Cancel = false; // Let Aspose perform the actual write.
    }
}
```

**Mengapa ini penting:**  
- **Prediktabilitas** – Semua gambar berakhir di folder yang sama, membuat referensi markdown menjadi dapat diandalkan.  
- **Penamaan bebas bentrok** – Menggunakan `Guid.NewGuid()` berarti Anda tidak akan pernah menimpa gambar yang sudah ada, bahkan jika dokumen sumber berisi nama yang duplikat.  
- **Fleksibilitas** – Ubah `folder` atau skema penamaan tanpa menyentuh logika konversi.

## Konfigurasi Opsi Penyimpanan Markdown (Simpan Word sebagai Markdown)

Sekarang kita menghubungkan callback ke `MarkdownSaveOptions`. Objek ini memberi tahu Aspose bagaimana memperlakukan konversi dan callback mana yang harus dipicu.

```csharp
// Step 4: Hook our custom callback into the markdown options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

Anda juga dapat menyesuaikan opsi lain di sini, seperti `ExportImagesAsBase64` (atur ke `false` karena kami menginginkan file gambar terpisah) atau `ExportHeadersAsHtml` jika Anda memerlukan kontrol lebih pada pemformatan heading. Pengaturan default sudah menghasilkan markdown bersih yang cocok untuk kebanyakan generator situs statis.

## Muat Dokumen dan Lakukan Konversi (Konversi DOCX ke Markdown)

Dengan opsi yang siap, langkah akhir menjadi sederhana: muat `.docx` dan minta Aspose menyimpannya sebagai markdown.

```csharp
// Step 5: Load the source DOCX and save it as Markdown.
Document doc = new Document(@"YOUR_DIRECTORY/input.docx");

// The output markdown will reference the images saved by MyResourceSaver.
doc.Save(@"YOUR_DIRECTORY/output.md", mdOptions);
```

**Apa yang akan Anda lihat:**  
- `output.md` berisi sintaks markdown (`![Alt text](Images/img_…png)`) yang mengarah ke folder gambar yang Anda tentukan.  
- Setiap gambar yang diekstrak dari `input.docx` berada di bawah `YOUR_DIRECTORY/Images/` dengan nama berbasis GUID yang unik.  

---

## Variasi Umum & Kasus Tepi

### 1️⃣ Mengubah Skema Penamaan
Jika Anda lebih suka nama yang dapat dibaca (mis., `figure_1.png`) daripada GUID, ganti baris `uniqueName` dengan sesuatu seperti:

```csharp
int counter = 0;
string uniqueName = $"figure_{++counter}{Path.GetExtension(args.ResourceFileName)}";
```

Ingatlah untuk menjadikan `counter` sebuah field statis atau melewatkannya melalui konstruktor callback agar tetap ada di antara pemanggilan.

### 2️⃣ Menangani Sub‑folder
Beberapa proyek mengatur gambar berdasarkan bab. Anda dapat memeriksa `args.ResourceFileName` atau bahkan teks paragraf di sekitarnya untuk memutuskan sub‑folder:

```csharp
string chapterFolder = Path.Combine(folder, $"Chapter_{args.ResourceFileName.Substring(0,1)}");
Directory.CreateDirectory(chapterFolder);
args.SavePath = Path.Combine(chapterFolder, uniqueName);
```

### 3️⃣ Melewatkan Gambar Tertentu
Jika Anda hanya ingin mengekstrak PNG, tambahkan pengecekan:

```csharp
if (!args.ResourceFileName.EndsWith(".png", StringComparison.OrdinalIgnoreCase))
{
    args.Cancel = true; // Skip non‑PNG images.
    return;
}
```

### 4️⃣ Memverifikasi Output
Setelah konversi, Anda dapat memverifikasi secara programatik bahwa setiap gambar yang direferensikan dalam markdown memang ada:

```csharp
string markdown = File.ReadAllText(@"YOUR_DIRECTORY/output.md");
var matches = System.Text.RegularExpressions.Regex.Matches(markdown, @"!\[.*?\]\((.*?)\)");
foreach (System.Text.RegularExpressions.Match m in matches)
{
    string imgPath = Path.Combine(@"YOUR_DIRECTORY", m.Groups[1].Value);
    Console.WriteLine(File.Exists(imgPath) ? "OK" : $"Missing: {imgPath}");
}
```

---

## Tips Pro untuk Pengalaman Lancar

- **Buat folder Images terlebih dahulu.** Aspose akan membuatnya secara otomatis, tetapi membuatnya sebelumnya menghindari kondisi balapan pada skenario multi‑thread.  
- **Gunakan `Path.GetInvalidFileNameChars()`** jika Anda perlu membersihkan nama yang berasal dari dokumen asli.  
- **Dispose `Document`** setelah selesai (bungkus dalam blok `using`) untuk membebaskan sumber daya native dengan cepat.  
- **Uji dengan dokumen yang berisi SVG.** Aspose mengonversinya ke PNG secara default; jika Anda memerlukan format asli, sesuaikan callback sesuai kebutuhan.

## Hasil yang Diharapkan

Menjalankan skrip pada contoh `input.docx` yang berisi dua gambar menghasilkan:

**`output.md` (kutipan)**  
```markdown
# Sample Document

Here is the first image:

![Image 1](Images/img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png)

And here is the second one:

![Image 2](Images/img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg)
```

**Struktur folder**  
```
YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ Images/
   ├─ img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png
   └─ img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg
```

Semua referensi gambar terresolusi dengan benar, dan Anda telah berhasil **menyimpan word sebagai markdown** sambil **mengekstrak gambar dari Word** dan **menghasilkan nama gambar unik**.

---

## Kesimpulan

Kami telah membahas **bagaimana cara menggunakan callback** di Aspose.Words untuk mengubah DOCX menjadi markdown, mengekstrak setiap gambar yang disematkan, dan memberi setiap file nama yang berbeda serta bebas bentrok. Pendekatan ini ringan, sepenuhnya dapat disesuaikan, dan bekerja dengan versi .NET apa pun yang mendukung Aspose.Words.

Langkah selanjutnya? Coba sambungkan ini dengan generator situs statis seperti Hugo atau Jekyll, atau otomatisasi konversi batch untuk seluruh folder dokumen. Anda juga dapat bereksperimen mengekspor tabel sebagai markdown atau menyesuaikan callback untuk menyematkan gambar sebagai Base64 ketika ukuran bukan menjadi masalah.

Ada variasi yang ingin Anda coba? Tinggalkan komentar, dan mari kita jelajahi bersama. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}