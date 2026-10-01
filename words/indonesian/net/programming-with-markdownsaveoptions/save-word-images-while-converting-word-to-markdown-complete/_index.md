---
category: general
date: 2026-02-20
description: Pelajari cara menyimpan gambar Word dan mengonversi Word ke markdown
  dalam C#. Panduan langkah demi langkah ini juga menunjukkan cara mengekstrak gambar
  dari Word dan mengekspor markdown dengan gambar.
draft: false
keywords:
- save word images
- convert word to markdown
- extract images from word
- convert docx to md
- export markdown with images
language: id
og_description: Dalam panduan ini kami menunjukkan cara menyimpan gambar Word dan
  mengonversi Word ke markdown menggunakan Aspose.Words. Ikuti langkah-langkah untuk
  mengekspor markdown dengan gambar.
og_title: Simpan gambar Word saat mengonversi Word ke Markdown – Tutorial C# Lengkap
tags:
- Aspose.Words
- C#
- Markdown
title: Simpan gambar Word saat mengonversi Word ke Markdown – Panduan Lengkap C#
url: /id/net/programming-with-markdownsaveoptions/save-word-images-while-converting-word-to-markdown-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan gambar Word saat mengonversi Word ke Markdown – Panduan Lengkap C#

Pernahkah Anda perlu **save word images** ketika mengonversi dokumen Word ke Markdown? Anda bukan satu‑satunya—para pengembang sering mengalami masalah di mana gambar menghilang setelah sekadar `convert docx to md`. Pada tutorial ini kami akan membahas cara bersih dan siap produksi untuk **save word images**, **convert word to markdown**, dan menghasilkan file Markdown yang tetap menampilkan setiap gambar.

Bayangkan Anda memiliki manual pengguna dalam `input.docx` dan ingin mempublikasikannya di situs statis. Anda memerlukan teks dalam format Markdown, tetapi juga memerlukan screenshot, diagram, dan logo muncul tepat di tempatnya. Itulah masalah yang akan kami selesaikan—tanpa alat eksternal, tanpa menyalin‑tempel manual, hanya beberapa baris C# dan Aspose.Words.

Pada akhir panduan ini Anda akan dapat:

* Memuat file `.docx` dengan Aspose.Words.  
* Mengonfigurasi `MarkdownSaveOptions` sehingga konversi juga **extracts images from word**.  
* Mengimplementasikan callback yang menulis setiap gambar ke folder khusus dengan nama unik.  
* Memverifikasi bahwa file `.md` yang dihasilkan mereferensikan gambar dengan benar, yaitu Anda telah berhasil **exported markdown with images**.

> **Prerequisites** – Anda memerlukan .NET 6+ (atau .NET Framework 4.6+), lisensi Aspose.Words yang valid (atau gunakan evaluasi gratis), dan pemahaman dasar tentang C#. Jika Anda belum pernah menggunakan Aspose sebelumnya, jangan khawatir; API‑nya sederhana dan kode di bawah ini sepenuhnya mandiri.

---

## Cara menyimpan gambar Word saat mengonversi Word ke Markdown

Langkah pertama adalah **save word images** selama proses konversi. Aspose.Words menyediakan `ResourceSavingCallback` yang dipicu untuk setiap sumber daya eksternal—gambar, diagram, SVG, apa saja. Dengan menyambungkan implementasi kita sendiri, kita memutuskan tepat di mana setiap gambar disimpan di disk.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Configure Markdown save options and attach a callback that will handle external resources
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image, letting us control the file name and folder
    ResourceSavingCallback = new MyResourceCallback()
};

// Save the document as Markdown; the callback will store images in a custom folder
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);

// -----------------------------------------------------------------
// Callback implementation – stores each image in a dedicated folder with a unique name
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define the folder where resources will be saved
        string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
        Directory.CreateDirectory(resourceFolder);

        // Generate a unique file name while preserving the original extension
        string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Tell Aspose.Words where to write the resource
        args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
    }
}
```

Itulah seluruh solusi—jalankan dan Anda akan memiliki `output.md` serta folder `MarkdownResources` yang berisi file‑file gambar. Markdown akan berisi tautan seperti `![](MarkdownResources/7f3c2a1e-...png)`, yang berarti Anda telah berhasil **save word images** dan **export markdown with images** dalam satu langkah.

---

## Konfigurasikan opsi Markdown untuk mengonversi docx ke md

Mengapa harus repot dengan callback? Secara default Aspose.Words akan menyematkan gambar sebagai string base‑64 di dalam Markdown, yang memperbesar ukuran file dan membuat kontrol versi menjadi berantakan. Menetapkan `ResourceSavingCallback` memberi tahu perpustakaan untuk **convert docx to md** *dan* menulis setiap gambar ke disk alih‑alih menyematkannya.

### Properti utama yang dapat Anda sesuaikan

| Property | Typical value | When to change |
|----------|---------------|----------------|
| `ExportImagesAsBase64` | `false` (default) | Simpan gambar sebagai file terpisah. |
| `ImagesFolder` | `null` (ignored when callback is used) | Anda dapat menetapkan folder statis jika tidak memerlukan penamaan dinamis. |
| `ExportHeadersFooters` | `true` | Pertahankan konten header/footer yang mungkin berisi gambar. |
| `EncodeUrls` | `true` | Diperlukan jika jalur Anda mengandung spasi atau karakter non‑ASCII. |

> **Pro tip:** Jika Anda membuat dokumentasi untuk banyak bahasa, pertimbangkan menambahkan kode bahasa ke `resourceFolder` (misalnya `MarkdownResources/en`) agar jalur gambar tetap rapi.

---

## Implementasikan callback sumber daya untuk mengekstrak gambar dari Word

Callback pada blok kode sebelumnya melakukan pekerjaan berat, tetapi mari kita uraikan sedikit. `IResourceSavingCallback` menerima objek `ResourceSavingArgs` untuk setiap sumber daya eksternal. Field terpentingnya adalah:

* `ResourceFileName` – jalur tempat file akan ditulis.  
* `ResourceFileExtension` – ekstensi asli (`.png`, `.jpg`, dll.).  
* `ResourceType` – memberi tahu apakah itu gambar, diagram, atau yang lainnya.

Anda dapat memfilter sumber daya non‑gambar jika hanya menginginkan gambar:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    // Skip non‑image resources – we only want to save pictures
    if (args.ResourceType != ResourceType.Image)
        return;

    string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
    Directory.CreateDirectory(resourceFolder);

    string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
    args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
}
```

### Penanganan kasus tepi

1. **Duplicate images** – Jika gambar yang sama muncul beberapa kali, callback tetap akan menulis file baru untuk setiap kemunculan. Jika Anda lebih suka deduplikasi, simpan `Dictionary<string, string>` yang memetakan hash byte gambar ke nama file yang sudah ada.  
2. **Unsupported formats** – Aspose.Words dapat mengekspor PNG, JPEG, GIF, BMP, dan TIFF. Jika Anda menemukan format eksotis, Anda harus mengonversinya sendiri (misalnya dengan `System.Drawing`).  
3. **Large documents** – Untuk PDF atau DOCX yang sangat besar, pertimbangkan streaming output untuk menghindari kehabisan memori. `MarkdownSaveOptions` mendukung `SaveOptions.UseMemoryCache = false`.

---

## Simpan dokumen dan verifikasi markdown yang diekspor dengan gambar

Setelah Anda menjalankan kode, buka `output.md` di editor teks apa pun. Anda seharusnya melihat sesuatu seperti:

```markdown
# Chapter 1

Here is a diagram:

![](MarkdownResources/2c7f9a3e-9b4d-4f6a-8d12-5e9f2c7a1b3c.png)

And another screenshot:

![](MarkdownResources/7a1d4e2f-3c9b-4a5d-9e8f-6b2c3d4e5f6a.jpg)
```

Jika tautan gambar terlihat benar, buka file Markdown tersebut di penampil (pratinjau VS Code, GitHub, atau generator situs statis). Gambar akan otomatis ditampilkan, mengonfirmasi bahwa Anda telah berhasil **save word images** dan **export markdown with images**.

### Skrip verifikasi cepat

Jika Anda ingin mengotomatisasi pemeriksaan, cuplikan di bawah ini memindai Markdown yang dihasilkan untuk file yang hilang:

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;

string mdPath = "YOUR_DIRECTORY/output.md";
string mdFolder = Path.GetDirectoryName(mdPath)!;
string[] lines = File.ReadAllLines(mdPath);

foreach (var line in lines)
{
    var match = Regex.Match(line, @"!\[.*?\]\((.+?)\)");
    if (match.Success)
    {
        string imgPath = Path.Combine(mdFolder, match.Groups[1].Value);
        if (!File.Exists(imgPath))
            Console.WriteLine($"Missing image: {imgPath}");
    }
}
Console.WriteLine("Verification complete.");
```

Jalankan setelah konversi; setiap gambar yang hilang akan dicetak ke konsol.

---

## Kesalahan umum dan praktik terbaik untuk mengonversi Word ke Markdown

| Pitfall | Why it hurts | Fix |
|---------|--------------|-----|
| **Images end up with long GUID names** | Sulit dibaca dalam kontrol sumber. | Lakukan post‑process pada folder untuk mengganti nama file dengan judul yang bermakna (misalnya berdasarkan `args.ResourceFileName` asli). |
| **Relative paths break after moving the Markdown file** | Tautan `![]()` bersifat relatif terhadap lokasi `.md`. | Simpan folder gambar di samping file Markdown atau gunakan jalur dasar yang konsisten dalam konfigurasi situs statis Anda. |
| **Missing images when `ExportImagesAsBase64` is `true`** | Callback tidak pernah dipanggil karena gambar disematkan. | Pastikan `ExportImagesAsBase64 = false` (default). |
| **Large documents cause `OutOfMemoryException`** | Aspose memuat seluruh dokumen ke RAM. | Gunakan `LoadOptions` dengan `LoadFormat.Docx` dan atur flag `MemoryOptimization` bila tersedia. |
| **Non‑ASCII file names break on some platforms** | Pengkodean URL dapat gagal. | Gunakan karakter ASCII saja atau set `EncodeUrls = true`. |

---

## Ringkasan

Kami telah membahas semua yang Anda perlukan untuk **save word images** sambil **convert word to markdown** menggunakan Aspose.Words. Ide dasarnya sederhana: lampirkan `ResourceSavingCallback`, arahkan ke folder yang Anda kontrol, dan biarkan perpustakaan melakukan sisanya. Setelah dijalankan, Anda akan memiliki file `.md` bersih dan sekumpulan aset gambar yang rapi—sempurna untuk dipublikasikan atau dikontrol versinya.

Jika Anda ingin **extract images from word** untuk keperluan lain (misalnya membuat galeri), cukup gunakan kembali kode callback tanpa langkah penyimpanan Markdown. Demikian pula, pola yang sama berlaku untuk **convert docx to md** dalam pekerjaan batch—cukup iterasi melalui direktori berisi file `.docx` dan panggil logika yang sama.

**Langkah selanjutnya** yang dapat Anda jelajahi:

* Integrasikan konversi ke dalam API ASP.NET Core sehingga pengguna dapat mengunggah DOCX dan menerima paket Markdown yang dapat diunduh.  
* Tambahkan dukungan untuk tabel dan

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}