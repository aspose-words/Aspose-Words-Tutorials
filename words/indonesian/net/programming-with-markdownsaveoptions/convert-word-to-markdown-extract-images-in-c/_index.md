---
category: general
date: 2026-02-18
description: Konversi Word ke Markdown dan ekstrak gambar dari docx menggunakan Aspose.Words.
  Pelajari cara menghasilkan markdown dari Word dengan contoh lengkap C#.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: id
og_description: Konversi Word ke Markdown dan ekstrak gambar dari docx dengan Aspose.Words.
  Panduan ini menunjukkan cara menghasilkan markdown dari Word langkah demi langkah.
og_title: Konversi Word ke Markdown – Ekstrak Gambar di C#
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Konversi Word ke Markdown – Ekstrak Gambar di C#
url: /id/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konversi Word ke Markdown – Ekstrak Gambar dalam C#

Pernah bertanya‑tanya bagaimana cara **convert Word to Markdown** sambil mengambil setiap gambar dari file `.docx`? Anda tidak sendirian. Banyak pengembang mengalami kebuntuan ketika mereka membutuhkan versi markdown yang bersih dari kontrak, posting blog, atau spesifikasi teknis yang awalnya ditulis di Word. Kabar baiknya? Dengan Aspose.Words untuk .NET Anda dapat melakukannya dalam beberapa baris kode, dan Anda akan mendapatkan file markdown *plus* sebuah folder berisi gambar‑gambar asli.

Dalam tutorial ini kami akan menelusuri program C# lengkap yang siap‑jalan yang **generates markdown from Word**, mengekstrak gambar dari docx, dan menyimpan semuanya ke disk. Pada akhir tutorial Anda akan tahu persis cara **convert docx to markdown**, cara **extract images from docx**, dan cara menyesuaikan proses untuk proyek Anda sendiri.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (v23.10 atau lebih baru). Anda dapat mengunduh paket percobaan gratis NuGet dengan `Install-Package Aspose.Words`.
- .NET 6+ SDK (versi terbaru apa pun sudah cukup).
- Contoh file `input.docx` yang berisi setidaknya satu gambar.
- Folder tempat Anda ingin menyimpan markdown dan aset gambar.

Tidak ada pustaka pihak ketiga lain yang diperlukan. Kode di bawah ini mencakup setiap direktif `using` yang Anda perlukan, sehingga Anda dapat menyalin‑tempelnya ke aplikasi console dan menekan **F5**.

![Contoh Konversi Word ke Markdown](/images/convert-word-to-markdown.png "convert word to markdown")

*Teks alt gambar: ilustrasi convert word to markdown yang menunjukkan file Word berubah menjadi file Markdown dengan gambar.*

---

## Langkah 1: Muat Dokumen Word Sumber

Hal pertama yang harus dilakukan adalah menunjuk Aspose.Words ke file yang ingin Anda ubah. Anggap `Document` sebagai gerbang ke semua yang ada di dalam `.docx`—teks, tabel, gambar, apa saja.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **Mengapa ini penting:** Memuat dokumen sekali saja menjaga penggunaan memori tetap rendah dan memungkinkan perpustakaan memeriksa struktur paket internal, yang penting untuk mengekstrak gambar nanti.

---

## Langkah 2: Beri Tahu Aspose.Words Cara Menyimpan sebagai Markdown

Aspose.Words dilengkapi dengan kelas `MarkdownSaveOptions`. Kelas ini memungkinkan Anda mengontrol segala hal mulai dari akhir baris hingga folder tempat sumber daya eksternal (seperti gambar) disimpan.

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **Mengapa callback?** `ResourceSavingCallback` memberi Anda kontrol penuh atas nama file dan lokasi setiap gambar yang diekstrak. Tanpa callback, Aspose akan menumpuk semuanya ke folder yang sama dengan nama generik, yang dapat menjadi berantakan untuk proyek berskala besar.

---

## Langkah 3: Simpan Dokumen sebagai Markdown

Setelah opsi diatur, proses penyimpanan cukup satu baris kode. Perpustakaan melakukan pekerjaan berat: mengonversi paragraf, heading, daftar, tabel, dan—berkat callback—menulis setiap gambar ke folder yang Anda tentukan.

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### Hasil yang Diharapkan

- `output.md` berisi sintaks markdown (misalnya `![Image](markdown-resources/img_1234.png)`).
- Folder `markdown-resources` menyimpan setiap gambar dari file Word asli, masing‑masing dengan nama unik.

Buka `output.md` di penampil markdown apa pun (VS Code, GitHub, atau generator situs statis) dan Anda akan melihat teks serta gambar yang identik dengan tata letak Word asli—hanya dalam format ringan yang ramah web.

## Langkah 4: Variasi Umum & Kasus Tepi

### 4.1 Menangani Folder Sumber Daya yang Sudah Ada

Jika Anda menjalankan konversi berulang kali, mungkin akan ada gambar usang. Klausa guard sederhana dapat membersihkan folder sebelum setiap proses:

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 Mengubah Format Gambar

Kadang‑kadang Anda memerlukan semua gambar dalam format JPEG untuk optimasi web. Di dalam callback Anda dapat meng‑encode ulang stream:

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **Pro tip:** `System.Drawing.Common` berfungsi di Windows; di Linux/macOS Anda mungkin lebih memilih `ImageSharp` untuk keamanan lintas‑platform.

### 4.3 Mempertahankan Gaya Tabel

Jika dokumen Word Anda sangat bergantung pada pemformatan tabel, Anda dapat menyesuaikan `MarkdownSaveOptions`:

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 Menggunakan Direktori Output yang Berbeda

Metode `Save` menerima jalur absolut atau relatif apa pun. Untuk pipeline CI Anda dapat mengarahkannya ke folder build sementara:

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

## Pertanyaan yang Sering Diajukan

**Q: Apakah ini bekerja dengan file `.doc` (biner)?**  
A: Ya. `new Document("file.doc")` secara otomatis mendeteksi format, sehingga kode yang sama menangani baik `.doc` maupun `.docx`.

**Q: Bagaimana jika file Word berisi gambar SVG yang disematkan?**  
A: Aspose.Words mengekstraknya dalam format aslinya. Jika Anda memerlukan versi raster, Anda harus mengonversi stream SVG di dalam callback (misalnya dengan `Svg.Skia`).

**Q: Bisakah saya melewatkan ekstraksi gambar sama sekali?**  
A: Atur `markdownOptions.ExportImagesAsBase64 = true;` untuk menyematkan gambar langsung dalam markdown menggunakan data URI—berguna untuk pembuatan README satu‑file.

## Ringkasan & Langkah Selanjutnya

Kami baru saja membahas alur kerja lengkap **convert word to markdown**:

1. Muat file `.docx`.
2. Konfigurasikan `MarkdownSaveOptions` dengan `ResourceSavingCallback`.
3. Simpan dokumen, biarkan callback menulis setiap gambar ke folder khusus.

Itulah seluruh solusi dalam kurang dari 50 baris C#.  

Jika Anda siap melangkah lebih jauh, pertimbangkan:

- **Membuat situs statis**: Masukkan markdown ke generator seperti Hugo atau Jekyll.
- **Pemrosesan batch**: Bungkus kode dalam loop `foreach` untuk menangani puluhan file secara otomatis.
- **Penanganan gambar lanjutan**: Ubah ukuran, tambahkan watermark, atau konversi gambar secara dinamis menggunakan callback.

Jangan ragu bereksperimen—ganti logika callback, sesuaikan opsi penyimpanan, atau integrasikan ini ke dalam pipeline dokumen yang lebih besar. Langit adalah batasnya, dan kini Anda memiliki fondasi yang kuat untuk proyek **generate markdown from word** apa pun.

Selamat coding, semoga markdown Anda selalu bersih dan gambar selalu ditemukan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}