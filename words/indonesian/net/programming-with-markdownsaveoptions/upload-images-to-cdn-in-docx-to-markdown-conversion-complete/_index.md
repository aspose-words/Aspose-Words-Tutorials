---
category: general
date: 2026-06-24
description: Unggah gambar ke CDN selama konversi DOCX ke Markdown menggunakan Aspose.Words.
  Pelajari cara menangkap aliran gambar, mengekspor gambar Word, dan menangani sumber
  daya secara efisien.
draft: false
keywords:
- upload images to cdn
- convert docx to markdown
- export word images
- word to markdown conversion
- capture image stream
language: id
og_description: Unggah gambar ke CDN sambil mengonversi DOCX ke Markdown dengan Aspose.Words.
  Panduan lengkap langkah demi langkah yang mencakup penangkapan aliran gambar dan
  penanganan sumber daya khusus.
og_title: Unggah Gambar ke CDN dalam Konversi DOCX ke Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Upload images to CDN during DOCX to Markdown conversion using Aspose.Words.
    Learn how to capture image stream, export Word images, and handle resources efficiently.
  headline: Upload Images to CDN in DOCX to Markdown Conversion – Complete Guide
  type: TechArticle
- description: Upload images to CDN during DOCX to Markdown conversion using Aspose.Words.
    Learn how to capture image stream, export Word images, and handle resources efficiently.
  name: Upload Images to CDN in DOCX to Markdown Conversion – Complete Guide
  steps:
  - name: 1️⃣ Do I need to set `args.Cancel = true`?
    text: Yes. If you leave `Cancel` false, Aspose will still write a local copy of
      the image, resulting in duplicate files and potentially broken links if the
      Markdown references the CDN URL but the local file also exists.
  - name: 2️⃣ What if the image format isn’t supported by my CDN?
    text: The callback gives you the raw bytes, so you can run them through an image‑processing
      library (e.g., `SixLabors.ImageSharp`) to convert PNG → JPEG before uploading.
      Just remember to adjust the file extension in `args.ResourceFileName`.
  - name: 3️⃣ How do I handle large documents with hundreds of images?
    text: Consider batching uploads or using async streaming APIs. The callback runs
      synchronously, but you can queue the upload work and block until the CDN returns
      a URL. Just be careful not to block the UI thread in a GUI app.
  - name: 4️⃣ Can I reuse the same callback for HTML export?
    text: Absolutely. `IResourceSavingCallback` works for any save format that emits
      external resources, including HTML, EPUB, and PDF (for embedded files). The
      same pattern of “capture → upload → rewrite URL” applies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- CDN
title: Unggah Gambar ke CDN dalam Konversi DOCX ke Markdown – Panduan Lengkap
url: /id/net/programming-with-markdownsaveoptions/upload-images-to-cdn-in-docx-to-markdown-conversion-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Unggah Gambar ke CDN dalam Konversi DOCX ke Markdown – Panduan Lengkap

Pernah bertanya-tanya bagaimana cara **mengunggah gambar ke CDN** saat mengonversi file DOCX ke Markdown? Dalam tutorial ini kami akan menjelaskan solusi lengkap Aspose.Words yang melakukan hal tersebut, dan kami juga akan menunjukkan cara **menangkap aliran gambar** untuk alur kerja khusus apa pun yang Anda miliki.

Jika Anda terjebak pada *konversi word ke markdown* yang kehilangan gambar Anda, Anda tidak sendirian. Kabar baiknya, Aspose.Words menyediakan hook—`IResourceSavingCallback`—sehingga Anda dapat menyela setiap gambar, mengirimnya ke bucket penyimpanan cloud, dan menulis ulang tautan Markdown agar mengarah ke URL CDN. Mari kita mulai.

> **Tips pro:** Pendekatan ini tidak hanya bekerja dengan Azure Blob Storage tetapi juga dengan CDN yang dapat diakses via HTTP (Amazon S3, Cloudflare Images, dll.). Cukup ganti logika unggah di dalam callback.

---

![Diagram yang menunjukkan pengunggahan gambar ke CDN selama konversi docx ke markdown](https://example.com/placeholder-diagram.png "Diagram mengunggah gambar ke CDN")

## Apa yang Akan Anda Pelajari

- Cara **mengonversi docx ke markdown** dengan Aspose.Words sambil mempertahankan setiap gambar yang disematkan.  
- Cara **mengekspor gambar Word** menggunakan `IResourceSavingCallback` khusus.  
- Cara **menangkap aliran gambar** di memori untuk pemrosesan lebih lanjut (mis., mengunggah ke CDN).  
- Jebakan umum seperti nama file duplikat, format gambar tidak didukung, dan masalah pembuangan stream.  

Pada akhir tutorial Anda akan memiliki aplikasi konsol C# siap‑jalankan yang mengambil `DocWithImages.docx` dan menghasilkan `Doc.md`, dengan semua gambar dihosting di CDN Anda.

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi pada .NET Framework 4.6+).  
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`).  
- Akses ke endpoint CDN dimana Anda dapat POST data biner (contoh menggunakan URL palsu).  
- Pemahaman dasar tentang C# async/await (opsional tetapi disarankan).  

Tidak diperlukan pustaka tambahan; callback hanya menggunakan `System.IO` dan API Aspose.

## Langkah 1: Siapkan Proyek dan Instal Aspose.Words

Buat proyek konsol baru:

```bash
dotnet new console -n DocxToMarkdownCdn
cd DocxToMarkdownCdn
dotnet add package Aspose.Words
```

Buka `Program.cs` dan bersihkan templat – kami akan menempelkan contoh lengkap nanti. Langkah ini memastikan Anda memiliki binari Aspose.Words terbaru, yang mencakup kelas `MarkdownSaveOptions` yang diperlukan untuk **konversi word ke markdown**.

## Langkah 2: Muat Dokumen DOCX Sumber

Baris pertama dari alur kerja Aspose.Words mana pun adalah memuat dokumen. Pastikan file input Anda berada di folder yang dapat Anda referensikan.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source DOCX that contains images.
Document doc = new Document("YOUR_DIRECTORY/DocWithImages.docx");
```

> **Mengapa ini penting:** Memuat dokumen memvalidasi struktur file lebih awal, sehingga jika DOCX rusak, pengecualian akan muncul sebelum kita mulai menangani gambar.

## Langkah 3: Buat Callback Penyimpanan Sumber Daya Kustom

Berikut inti dari tutorial. Dengan mengimplementasikan `IResourceSavingCallback` kami mendapatkan kontrol atas setiap sumber daya biner yang akan ditulis oleh Aspose.Words—gambar, font, bahkan file CSS jika Anda pernah mengekspor ke HTML.

```csharp
class ImageResourceSaver : IResourceSavingCallback
{
    // You could inject a service (e.g., AzureBlobService) via constructor.
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Capture the image data into a MemoryStream.
        using (MemoryStream memoryStream = new MemoryStream())
        {
            args.Stream.CopyTo(memoryStream);
            byte[] imageBytes = memoryStream.ToArray();

            // 2️⃣ Upload the byte array to your CDN.
            //    The upload method is abstracted – replace with real SDK call.
            string cdnUrl = UploadToCdn(imageBytes, args.ResourceFileName);

            // 3️⃣ Tell Aspose to use the CDN URL in the generated Markdown.
            args.ResourceFileName = cdnUrl;
        }

        // 4️⃣ Cancel the default file write; we already handled the resource.
        args.Cancel = true;
    }

    private string UploadToCdn(byte[] data, string originalFileName)
    {
        // Placeholder implementation – in production you’d call your CDN SDK.
        // For demo purposes we just return a fake URL.
        return $"https://mycdn.example.com/{originalFileName}";
    }
}
```

**Penjelasan “mengapa”:**  

- **Menangkap aliran gambar** – `args.Stream` adalah stream hanya-baca yang menunjuk pada data gambar. Dengan menyalinnya ke dalam `MemoryStream` kami dapat memanipulasi byte sesuka hati (kompres, ubah ukuran, dll.).  
- **Unggah ke CDN** – Callback adalah tempat yang tepat untuk memanggil HTTP POST async atau SDK cloud. Kami menjaga contoh ini sinkron untuk singkatnya, tetapi Anda dapat `await` metode unggah async dan kemudian mengatur `args.ResourceFileName`.  
- **Batalkan penulisan default** – Menetapkan `args.Cancel = true` mencegah Aspose menulis file lokal, menghindari penyimpanan duplikat dan menjaga folder output tetap bersih.  

> **Kasus khusus:** Jika CDN Anda memerlukan nama file unik, pertimbangkan menambahkan GUID ke `originalFileName` sebelum mengunggah.

## Langkah 4: Konfigurasikan Opsi Penyimpanan Markdown dan Lampirkan Callback

Sekarang kami memberi tahu Aspose.Words untuk menggunakan Markdown sebagai format output dan menyerahkan setiap gambar ke `ImageResourceSaver` kami.

```csharp
// Configure Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Register the custom callback.
    ResourceSavingCallback = new ImageResourceSaver(),

    // Optional: you can control how headings are generated.
    ExportHeadersAsHtml = false
};
```

Anda juga dapat menyesuaikan `MarkdownSaveOptions` untuk mengubah sintaks gambar (`![]()` vs HTML `<img>`), tetapi nilai default bekerja untuk kebanyakan generator situs statis.

## Langkah 5: Simpan Dokumen sebagai Markdown

Akhirnya, panggil `Document.Save` dengan opsi yang baru saja kami buat.

```csharp
// Perform the conversion. The callback will fire for every image.
doc.Save("YOUR_DIRECTORY/Doc.md", mdOptions);
```

Setelah metode selesai, Anda akan menemukan `Doc.md` di folder target. Buka di editor apa pun, dan Anda akan melihat tautan gambar yang langsung mengarah ke `https://mycdn.example.com/…`. Tidak ada file gambar lokal yang tersisa.

## Contoh Kerja Lengkap

Berikut adalah program lengkap yang siap disalin‑tempel. Ganti `YOUR_DIRECTORY` dengan jalur sebenarnya tempat DOCX Anda berada, dan ganti stub `UploadToCdn` dengan logika unggah yang nyata.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // Load the source DOCX that contains images.
        Document doc = new Document("YOUR_DIRECTORY/DocWithImages.docx");

        // Set up Markdown options with our custom callback.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver()
        };

        // Save as Markdown; images are uploaded to CDN on the fly.
        doc.Save("YOUR_DIRECTORY/Doc.md", mdOptions);

        Console.WriteLine("Conversion complete! Check Doc.md for Markdown with CDN image URLs.");
    }
}

// -----------------------------------------------------------------
class ImageResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Capture the image data.
        using (MemoryStream memoryStream = new MemoryStream())
        {
            args.Stream.CopyTo(memoryStream);
            byte[] imageBytes = memoryStream.ToArray();

            // Upload the image to the CDN (replace with real implementation).
            string cdnUrl = UploadToCdn(imageBytes, args.ResourceFileName);

            // Point the Markdown link to the CDN location.
            args.ResourceFileName = cdnUrl;
        }

        // Skip default file creation.
        args.Cancel = true;
    }

    private string UploadToCdn(byte[] data, string fileName)
    {
        // TODO: integrate Azure Blob, AWS S3, Cloudflare, etc.
        // For demonstration we just return a placeholder URL.
        return $"https://mycdn.example.com/{fileName}";
    }
}
```

**Output yang diharapkan** – Buka `Doc.md` dan Anda akan melihat sesuatu seperti:

```markdown
# Sample Document

Here is an image:

![](https://mycdn.example.com/image1.png)

More text follows…
```

Semua gambar kini dilayani dari CDN, artinya Markdown Anda dapat dipublikasikan ke situs statis mana pun tanpa khawatir aset yang hilang.

## Pertanyaan Umum & Hal-hal yang Perlu Diwaspadai

### 1️⃣ Apakah saya perlu mengatur `args.Cancel = true`?

Ya. Jika Anda membiarkan `Cancel` false, Aspose tetap akan menulis salinan lokal gambar, menghasilkan file duplikat dan berpotensi tautan rusak jika Markdown merujuk ke URL CDN tetapi file lokal juga ada.

### 2️⃣ Bagaimana jika format gambar tidak didukung oleh CDN saya?

Callback memberikan byte mentah, sehingga Anda dapat memprosesnya melalui pustaka pemrosesan gambar (mis., `SixLabors.ImageSharp`) untuk mengonversi PNG → JPEG sebelum mengunggah. Cukup ingat untuk menyesuaikan ekstensi file di `args.ResourceFileName`.

### 3️⃣ Bagaimana saya menangani dokumen besar dengan ratusan gambar?

Pertimbangkan mengelompokkan unggahan atau menggunakan API streaming async. Callback berjalan secara sinkron, tetapi Anda dapat mengantri pekerjaan unggah dan menunggu hingga CDN mengembalikan URL. Hanya berhati-hatilah agar tidak memblokir thread UI dalam aplikasi GUI.

### 4️⃣ Bisakah saya menggunakan kembali callback yang sama untuk ekspor HTML?

Tentu saja. `IResourceSavingCallback` bekerja untuk format penyimpanan apa pun yang menghasilkan sumber daya eksternal, termasuk HTML, EPUB, dan PDF (untuk file tersemat). Pola yang sama “menangkap → unggah → menulis ulang URL” berlaku.

## Tips Kinerja

- **

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode kerja lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [menyematkan gambar markdown – Panduan Lengkap Mengonversi Dokumen Word](/words/english/java/document-conversion-and-export/embed-images-markdown-complete-guide-to-converting-word-docs/)
- [Simpan Gambar Word – Konversi Word ke Markdown dengan Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Menguasai Konversi Markdown dengan Aspose.Words: Panduan Tabel & Gambar](/words/english/java/tables-lists/mastering-markdown-conversion-aspose-words-tables-images/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}