---
category: general
date: 2026-05-04
description: Pelajari cara menyimpan gambar saat mengonversi DOCX ke Markdown menggunakan
  Aspose.Words. Panduan ini juga menunjukkan cara mengekstrak gambar dari Word dan
  menyimpan Word sebagai Markdown.
draft: false
keywords:
- how to save images
- convert docx to markdown
- extract images from word
- how to convert docx
- save word as markdown
language: id
og_description: Cara menyimpan gambar saat mengonversi DOCX ke Markdown menggunakan
  Aspose.Words. Panduan langkah demi langkah dengan kode C# lengkap.
og_title: Cara Menyimpan Gambar – Mengonversi DOCX ke Markdown dengan Aspose.Words
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Cara Menyimpan Gambar – Mengonversi DOCX ke Markdown dengan Aspose.Words
url: /id/net/programming-with-markdownsaveoptions/how-to-save-images-convert-docx-to-markdown-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyimpan Gambar – Mengonversi DOCX ke Markdown dengan Aspose.Words

Pernah bertanya‑tanya **cara menyimpan gambar** ketika Anda harus mengubah file Word menjadi Markdown? Anda tidak sendirian. Banyak pengembang menemui masalah ketika konversi menumpahkan gambar menjadi tautan yang rusak, atau lebih parah—kehilangan gambar sama sekali. Kabar baiknya, Aspose.Words memberi Anda kontrol yang sangat detail, sehingga Anda dapat mengekstrak gambar dari Word, menentukan ke mana mereka disimpan, dan tetap mendapatkan output Markdown yang bersih.

Dalam tutorial ini kami akan menelusuri contoh lengkap C# yang siap dijalankan yang menunjukkan **cara menyimpan gambar** ke folder khusus saat mengonversi `.docx` ke `.md`. Sepanjang jalan kami juga akan menyentuh **convert docx to markdown**, **extract images from word**, dan pertanyaan lebih luas tentang **how to convert docx** dengan cara yang memungkinkan Anda **save word as markdown** tanpa kehilangan aset apa pun.

## Prasyarat

- .NET 6.0 atau yang lebih baru (API berfungsi sama pada .NET Framework 4.7+)
- Lisensi Aspose.Words yang aktif atau trial gratis (versi gratis menambahkan watermark pada output, tetapi kode tetap berfungsi sama)
- Dokumen Word yang sudah berisi gambar (misalnya `DocWithImages.docx`)
- Visual Studio 2022 atau editor apa pun yang dapat membangun proyek C#

> **Pro tip:** Jika Anda menggunakan trial, Anda masih dapat menguji logika penyimpanan gambar; cukup ingat bahwa PDF/MD akhir akan berisi watermark trial.

## Gambaran Umum Solusi

Secara garis besar prosesnya terlihat seperti ini:

1. Muat file `.docx` sumber dengan `Document`.
2. Buat objek `MarkdownSaveOptions` dan sambungkan `IResourceSavingCallback`.
3. Di dalam callback, tentukan folder dan nama file untuk setiap gambar.
4. Simpan dokumen sebagai Markdown; callback menulis setiap gambar ke disk.

Itulah inti **cara menyimpan gambar** selama konversi. Pola yang sama berlaku untuk tipe sumber daya lain (font, CSS, dll.) jika Anda membutuhkannya.

## Langkah 1 – Muat DOCX yang Berisi Gambar

Pertama kita memerlukan instance `Document` yang menunjuk ke file Word yang ingin Anda konversi. Tidak ada yang rumit di sini; hanya pemanggilan konstruktor standar.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to where your .docx lives
string sourcePath = @"C:\Docs\DocWithImages.docx";

Document sourceDoc = new Document(sourcePath);
```

> **Mengapa ini penting:** Memuat dokumen adalah satu‑satunya tempat Aspose mem-parsing XML Word, sehingga font yang hilang atau bagian yang rusak akan melemparkan pengecualian pada saat ini—sebelum kita mulai menyimpan gambar.

## Langkah 2 – Siapkan MarkdownSaveOptions dengan Callback Penyimpanan Gambar

Kelas `MarkdownSaveOptions` memungkinkan Anda menyisipkan logika ke proses penyimpanan melalui `ResourceSavingCallback`. Callback tersebut menerima objek `ResourceSavingArgs` untuk setiap sumber daya eksternal (gambar, CSS, dll.) yang harus ditulis Aspose.

```csharp
// Define where the Markdown file will be written
string markdownPath = @"C:\Docs\Doc.md";

// Create the options object and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This is the heart of how to save images
    ResourceSavingCallback = new ImageSavingCallback()
};
```

### Implementasi Callback

Berikut implementasi lengkap `ImageSavingCallback`. Ia membuat sub‑folder `Images` di samping file Markdown, memberi setiap gambar nama berurutan (`img_0.png`, `img_1.jpg`, …), dan opsional memungkinkan Anda menyalurkan gambar ke tempat lain (misalnya, ke bucket cloud).

```csharp
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only handle images; other resources (like CSS) are ignored here
        if (args.ResourceType != ResourceType.Image)
            return;

        // Build a folder called "Images" right next to the markdown file
        string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
        string imagesFolder = Path.Combine(markdownDir, "Images");
        Directory.CreateDirectory(imagesFolder);

        // Compose a safe file name: img_<index>.<original extension>
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
        args.FileName = Path.Combine(imagesFolder, newFileName);

        // If you wanted to push the image to a remote store, you could replace args.Stream here.
        // For now we just let Aspose write to the local file system.
    }
}
```

> **Bagaimana ini membantu Anda:** Dengan menyesuaikan `args.FileName` Anda mengontrol secara tepat **cara menyimpan gambar**—apakah dalam folder datar, hierarki berbasis tanggal, atau bahkan BLOB basis data. Callback dijalankan untuk setiap gambar, sehingga Anda tidak perlu memproses ulang file Markdown nanti.

## Langkah 3 – Simpan Dokumen sebagai Markdown

Setelah opsi dan callback siap, konversi sebenarnya hanya satu baris kode.

```csharp
// Save the document; the callback will fire for each image automatically
sourceDoc.Save(markdownPath, markdownOptions);
```

Saat baris tersebut selesai, Anda akan memiliki:

- `Doc.md` – representasi Markdown dari konten Word Anda.
- `Images\img_0.png`, `Images\img_1.jpg`, … – setiap gambar yang diekstrak dari DOCX asli.

## Contoh Lengkap yang Siap Dijalan

Menggabungkan semuanya, berikut aplikasi konsol mandiri yang dapat Anda salin‑tempel ke proyek C# baru.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // 1️⃣ Load the source DOCX that contains images
            // -----------------------------------------------------------------
            string sourcePath = @"C:\Docs\DocWithImages.docx";
            Document sourceDoc = new Document(sourcePath);

            // -----------------------------------------------------------------
            // 2️⃣ Prepare Markdown options with a custom image‑saving callback
            // -----------------------------------------------------------------
            string markdownPath = @"C:\Docs\Doc.md";
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // -----------------------------------------------------------------
            // 3️⃣ Perform the conversion – this is where we actually learn
            //     how to save images while converting docx to markdown
            // -----------------------------------------------------------------
            sourceDoc.Save(markdownPath, markdownOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {markdownPath}");
            Console.WriteLine("Images folder: " + Path.Combine(Path.GetDirectoryName(markdownPath), "Images"));
        }
    }

    // -----------------------------------------------------------------
    // 4️⃣ Callback that decides where each image ends up
    // -----------------------------------------------------------------
    class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType != ResourceType.Image)
                return;

            string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
            string imagesFolder = Path.Combine(markdownDir, "Images");
            Directory.CreateDirectory(imagesFolder);

            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(imagesFolder, newFileName);

            // Optional: redirect the image stream elsewhere (e.g., cloud storage)
            // args.Stream = new MemoryStream(); // your custom stream here
        }
    }
}
```

### Hasil yang Diharapkan

Setelah Anda menjalankan program:

- Buka `C:\Docs\Doc.md` di editor teks apa pun. Anda akan melihat tautan gambar Markdown seperti `![](Images/img_0.png)`.
- Folder `Images` akan berisi setiap gambar yang diekstrak, bernama berurutan.
- File Markdown akan ditampilkan dengan benar di viewer mana pun yang mendukung gambar lokal (preview VS Code, GitHub, dll.).

## Pertanyaan yang Sering Diajukan (FAQ)

### Apakah ini bekerja dengan format gambar lain (SVG, TIFF)?

Ya. `Path.GetExtension(args.FileName)` mempertahankan ekstensi asli, sehingga SVG, TIFF, BMP, dan bahkan EMF disimpan tanpa perubahan. Satu‑satunya catatan adalah beberapa renderer Markdown mungkin tidak menampilkan SVG secara inline; dalam kasus itu Anda dapat mengonversi SVG ke PNG terlebih dahulu.

### Bagaimana jika saya perlu menyematkan gambar sebagai Base64 alih‑alih file terpisah?

Di dalam `ResourceSaving`, Anda dapat mengganti penulisan file fisik dengan memory stream lalu memodifikasi tautan Markdown secara manual. Aspose tidak menyediakan saklar langsung “embed as Base64”, tetapi callback memberi Anda kontrol penuh atas `args.Stream`.

### Bagaimana ini berbeda dari metode bawaan `ExportImages`?

`ExportImages` mengekstrak semua gambar ke folder **tanpa** menghasilkan Markdown. Callback kami menggabungkan kedua aksi, menjamin bahwa nama file gambar cocok dengan referensi di dalam `.md`. Keselarasan itulah yang menjadi kunci **cara menyimpan gambar** dengan benar selama konversi.

### Bisakah saya mengonversi beberapa file DOCX sekaligus (batch)?

Tentu saja. Bungkus logika inti dalam loop `foreach (var file in Directory.GetFiles(..., "*.docx"))`, sesuaikan jalur output, dan gunakan kembali `ImageSavingCallback` yang sama. Hanya ingat untuk membuat `MarkdownSaveOptions` baru untuk setiap dokumen, karena `args.DestinationFileName` berubah tiap iterasi.

## Kasus Khusus & Praktik Terbaik

| Situasi | Hal yang Perlu Diwaspadai | Solusi yang Disarankan |
|-----------|----------------------|-----------------|
| **DOCX besar (ratusan MB)** | Tekanan memori saat memuat | Gunakan `LoadOptions` dengan `LoadFormat.Docx` dan set `LoadOptions.LoadFormat = LoadFormat.Docx` untuk memuat bagian secara streaming |
| **Nama gambar bentrok** | Jika sumber sudah memiliki `img_0.png` di folder target, Anda dapat menimpa | Tambahkan GUID: `newFileName = $"img_{args.Index}_{Guid.NewGuid():N}{Path.GetExtension(args.FileName)}"` |
| **Folder output hanya‑baca** | Simpan akan melempar `UnauthorizedAccessException` | Pastikan proses berjalan dengan izin yang tepat atau pilih jalur yang dapat ditulisi |
| **Sumber daya non‑gambar (CSS, font)** | Callback juga menerima mereka | Lindungi dengan `if (args.ResourceType != ResourceType.Image) return;` (sudah ditunjukkan) |
| **Nama file Unicode** | Beberapa sistem file tidak menangani karakter tersebut | Gunakan `Path.GetInvalidFileNameChars()` untuk membersihkan `args.FileName` sebelum menetapkannya |

## Topik Terkait yang Mungkin Ingin Anda Jelajahi Selanjutnya

- **convert docx to markdown** dengan gaya heading khusus (gunakan `MarkdownSaveOptions.ExportImagesAsBase64` untuk gambar inline)
- **extract images from word** menggunakan `Document.GetChildNodes(NodeType.Shape,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}