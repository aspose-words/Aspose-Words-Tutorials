---
category: general
date: 2026-01-03
description: Konversi Word ke Markdown dan sematkan gambar sebagai base64 sekaligus.
  Pelajari cara menyimpan Word sebagai markdown, menghasilkan markdown dari Word,
  dan menggunakan data URI gambar base64.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: id
og_description: Konversi Word ke Markdown dan sematkan gambar sebagai data URI base64.
  Tutorial langkah demi langkah ini menunjukkan cara menyimpan Word sebagai markdown
  dan menghasilkan markdown dari Word.
og_title: Mengonversi Word ke Markdown – Panduan Penyematan Gambar Base64
tags:
- Aspose.Words
- C#
- Markdown
title: Konversi Word ke Markdown – Sisipkan Gambar sebagai Base64
url: /id/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert Word to Markdown – Embed Images as Base64

Pernah perlu **mengonversi Word ke markdown** tetapi selalu terhambat oleh gambar? Anda tidak sendirian. Word suka menyimpan gambar sebagai file terpisah, sementara markdown lebih menyukai string `data:image/...;base64,` yang menjaga semuanya rapi dalam satu file.  

Dalam tutorial ini kita akan membahas solusi lengkap yang siap dijalankan yang **menyimpan Word sebagai markdown**, **menyematkan gambar sebagai base64**, dan bahkan menunjukkan cara **menghasilkan markdown dari Word** menggunakan Aspose.Words untuk .NET. Pada akhir tutorial, Anda akan memiliki satu file `.md` yang menampilkan hasil persis seperti dokumen asli—tanpa folder gambar eksternal.

## Apa yang Anda Butuhkan

- **.NET 6.0 atau lebih baru** (apa saja yang dapat merujuk ke paket NuGet)
- **Aspose.Words untuk .NET** (versi percobaan gratis sudah cukup untuk pengujian)
- Sebuah file `.docx` sederhana dengan beberapa gambar (kita akan menyebutnya `input.docx`)
- IDE favorit Anda (Visual Studio, Rider, VS Code—pilih yang Anda suka)

Jika Anda sudah memiliki semuanya, bagus—langsung saja. Jika belum, menginstal paket NuGet cukup dengan satu baris:

```bash
dotnet add package Aspose.Words
```

## Langkah 1: Muat Dokumen Word — titik awal untuk **convert word to markdown**

Pertama kita perlu memuat `.docx` ke dalam memori. Di sinilah proses konversi dimulai.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Mengapa ini penting:**  
> Memuat dokumen memberi Aspose akses penuh ke teks, gaya, dan setiap sumber daya yang disematkan. Tanpa langkah ini, tidak ada yang dapat dikonversi.

## Langkah 2: Siapkan MarkdownSaveOptions dengan Callback Penyimpanan Sumber Daya

Aspose memungkinkan Anda menyela setiap sumber daya (seperti gambar) yang biasanya akan ditulis ke disk. Dengan menyediakan `IResourceSavingCallback` khusus, kita dapat mengganti penyimpanan berbasis file standar dengan **data uri gambar base64**.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### Handler Khusus – Mengubah gambar menjadi Base64

Berikut adalah implementasi lengkapnya. Perhatikan bagaimana kami memeriksa `args.ResourceType == ResourceType.Image` dan kemudian:

1. Menulis gambar ke `MemoryStream`.
2. Mengonversi array byte menjadi string Base64.
3. Membuat URI `data:image/jpeg;base64,` dan menetapkannya ke `args.Uri`.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **Tips pro:** Jika dokumen Word sumber Anda menggunakan PNG, ganti `ImageSaveOptions.DefaultJpeg` dengan `ImageSaveOptions.DefaultPng` dan ubah tipe MIME yang sesuai (`image/png`).

## Langkah 3: Simpan Dokumen sebagai Markdown – langkah akhir **save word as markdown**

Setelah callback siap, penyimpanan sebenarnya cukup satu baris kode.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

Saat Anda membuka `output.md` di penampil markdown apa pun (pratinjau VS Code, GitHub, dll.), Anda akan melihat teks persis seperti di file Word asli, dan gambar akan muncul secara inline tanpa file gambar terpisah.

## Output yang Diharapkan

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

Baris `![Embedded Image]` adalah **data uri gambar base64**—seluruh gambar dikodekan di sana. Tidak ada folder tambahan, tidak ada tautan yang rusak.

## Kasus Khusus & Cara Menanganinya

| Situasi | Apa yang Harus Dilakukan |
|-----------|------------|
| **Gambar Besar** – Base64 menambah ukuran sekitar ~33% | Pertimbangkan mengubah ukuran sebelum konversi: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Gambar Bukan JPEG** (PNG, GIF) | Deteksi format asli lewat `args.ResourceData.ImageType` dan tetapkan tipe MIME yang tepat (`image/png`, `image/gif`). |
| **Dokumen Sangat Panjang** (ratusan gambar) | Pantau penggunaan memori; Anda dapat men-stream setiap gambar ke disk sementara jika proses kehabisan RAM. |
| **Butuh File Gambar Terpisah** (misalnya untuk situs statis) | Kembalikan `false` dari callback untuk gambar yang ingin disimpan sebagai file, dan biarkan Aspose menuliskannya ke folder. |

## Pertanyaan Umum (Jawaban di Depan)

- **Apakah ini bekerja dengan file .doc?** Ya—Aspose.Words dapat memuat file legacy `.doc` dengan cara yang sama seperti Anda memuat `.docx`. Cukup panggil `new Document("myfile.doc")`.
- **Bagaimana dengan tabel dan catatan kaki?** Kedua elemen tersebut didukung penuh oleh eksportir Markdown. Tabel menjadi tabel markdown; catatan kaki menjadi referensi inline.
- **Bisakah saya mengubah varian markdown?** `MarkdownSaveOptions` memiliki properti `MarkdownVersion` (CommonMark, GitHub, dll.). Setel sebelum menyimpan jika Anda memerlukan sintaks tertentu.

## Contoh Lengkap yang Siap Dijalan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi console. Program ini mencakup semua pernyataan `using`, kelas handler, dan penanganan error.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

Jalankan program, buka `output.md` yang dihasilkan, dan Anda akan melihat replika markdown yang sempurna dari file Word Anda—**convert word to markdown** tidak pernah semudah ini.

## Ringkasan

Kami memulai dengan masalah **convert word to markdown** sambil menjaga gambar tetap inline. Dengan memuat dokumen, mengonfigurasi callback `MarkdownSaveOptions`, dan menyimpan file, kami menghasilkan solusi **save word as markdown** yang bersih dengan string **base64 image data uri**. Sekarang Anda juga tahu cara **embed images as base64**, menangani kasus khusus, dan menyesuaikan proses untuk tipe gambar yang berbeda.

## Apa Selanjutnya?

- **Hasilkan HTML alih-alih markdown** – ganti `MarkdownSaveOptions` dengan `HtmlSaveOptions` dan gunakan kembali callback yang sama.
- **Konversi batch banyak file** – bungkus logika dalam loop `foreach` pada sebuah folder.
- **Integrasikan ke pipeline CI** – otomatisasi pembuatan dokumentasi untuk situs statis.

Silakan bereksperimen, ubah kualitas gambar, atau bahkan tambahkan penanganan sumber daya khusus Anda (misalnya, mengunggah gambar ke CDN dan menyisipkan URL). Langit adalah batasnya ketika Anda menggabungkan Aspose.Words dengan sedikit kecerdikan C#.

Selamat coding, semoga markdown Anda selalu tampil sempurna! 

![Diagram showing convert word to markdown flow – embed images as base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}