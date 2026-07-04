---
category: general
date: 2026-05-26
description: Buat folder aset saat Anda mengonversi Word ke Markdown dan mengekstrak
  gambar dari docx. Pelajari cara menulis aliran gambar dan menangani sumber daya
  di Aspose.Words.
draft: false
keywords:
- create assets folder
- convert word to markdown
- extract images from docx
- convert docx with images
- write image stream
language: id
og_description: Buat folder aset saat Anda mengonversi Word ke Markdown. Ikuti panduan
  langkah demi langkah ini untuk mengekstrak gambar dari docx dan menulis aliran gambar
  dengan Aspose.Words.
og_title: Buat Folder Aset untuk Mengonversi Word ke Markdown
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create assets folder while you convert Word to Markdown and extract
    images from docx. Learn how to write image stream and handle resources in Aspose.Words.
  headline: Create Assets Folder for Convert Word to Markdown
  type: TechArticle
tags:
- Aspose.Words
- C#
- Markdown
- Docx
- Image Extraction
title: Buat Folder Aset untuk Mengonversi Word ke Markdown
url: /id/net/programming-with-markdownsaveoptions/create-assets-folder-for-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Folder Assets untuk Mengonversi Word ke Markdown

Pernah perlu **membuat folder assets** saat Anda **mengonversi Word ke Markdown**? Jika Anda mengekstrak gambar dari DOCX, menyiapkan folder tersebut dengan benar adalah langkah pertama untuk konversi yang lancar.  

Dalam tutorial ini kami akan menjelaskan proses lengkap mengonversi `.docx` yang berisi gambar menjadi file Markdown, sambil secara otomatis mengekstrak gambar-gambar tersebut ke sub‑direktori **assets**. Pada akhir tutorial Anda akan tahu cara **mengekstrak gambar dari docx**, **menulis aliran gambar** ke file, dan menjaga referensi Markdown tetap rapi.

## Apa yang Akan Anda Pelajari

- Cara mengkonfigurasi **Aspose.Words** untuk ekspor Markdown  
- Kode tepat yang dibutuhkan untuk **membuat folder assets** secara otomatis  
- Bagaimana **ResourceSavingCallback** memungkinkan Anda **mengekstrak gambar dari docx** dan **menulis aliran gambar** ke file  
- Cara memverifikasi bahwa Markdown yang dihasilkan menautkan gambar dengan benar  
- Tips menangani kasus tepi seperti nama gambar duplikat atau izin menulis yang hilang  

> **Prasyarat** – Anda memerlukan .NET 6+ (atau .NET Framework 4.7.2+) dan referensi ke pustaka Aspose.Words untuk .NET. Tidak diperlukan alat pihak ketiga lainnya.

---

## Buat Folder Assets untuk Konversi Markdown

Hal pertama yang harus kami pastikan adalah adanya direktori **assets** di samping file Markdown output. Folder ini akan menampung setiap gambar yang diekstrak oleh proses konversi.

```csharp
// Ensure the assets folder exists before any conversion starts.
string assetsFolder = Path.Combine(outputDirectory, "assets");
Directory.CreateDirectory(assetsFolder);   // This call is idempotent – it won’t throw if the folder already exists.
```

> **Tips Pro:** `Directory.CreateDirectory` aman dipanggil berulang kali; ia hanya membuat folder jika belum ada, yang berarti Anda dapat menjalankan konversi berkali‑kali tanpa khawatir tentang error “folder already exists”.

---

## Konversi Word ke Markdown dengan Ekstraksi Gambar

Sekarang kami menghubungkan Aspose.Words ke objek `MarkdownSaveOptions`. Bagian pentingnya adalah `ResourceSavingCallback`. Di dalam callback kami **menulis aliran gambar** ke folder assets yang telah dibuat sebelumnya dan kemudian mengubah nama file sehingga file Markdown menunjuk ke lokasi yang tepat.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// -------------------------------------------------------------------
// 1️⃣ Load the source .docx that contains images.
// -------------------------------------------------------------------
Document doc = new Document(@"YOUR_DIRECTORY\WithImages.docx");

// -------------------------------------------------------------------
// 2️⃣ Configure Markdown save options with a custom callback.
// -------------------------------------------------------------------
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This delegate runs for every embedded resource (images, PDFs, etc.).
    ResourceSavingCallback = new ResourceSavingCallback(resourceInfo =>
    {
        // 2a️⃣ Build the full path for the output file inside the assets folder.
        string fileName = Path.GetFileName(resourceInfo.FileName); // Keep the original name.
        string outputPath = Path.Combine(assetsFolder, fileName);

        // 2b️⃣ Write the incoming stream (the image data) to disk.
        using (FileStream outStream = File.Create(outputPath))
        {
            // The stream contains the raw bytes of the image.
            resourceInfo.Stream.CopyTo(outStream);
        }

        // 2c️⃣ Update the reference that will appear in the Markdown file.
        // This tells Markdown to look for the image under the "assets" sub‑folder.
        resourceInfo.FileName = $"assets/{fileName}";
    })
};

// -------------------------------------------------------------------
// 3️⃣ Save the document as Markdown.
// -------------------------------------------------------------------
string markdownPath = Path.Combine(outputDirectory, "DocWithImages.md");
doc.Save(markdownPath, mdOptions);
```

### Mengapa Ini Berfungsi

- **`ResourceSavingCallback`** dipanggil untuk *setiap* sumber daya yang disematkan—sehingga Anda secara otomatis **mengekstrak gambar dari docx** tanpa menulis logika parsing tambahan.  
- Dengan menetapkan `resourceInfo.FileName = "assets/" + fileName;` kami memastikan Markdown yang dihasilkan berisi tautan relatif seperti `![Image](assets/picture.png)`.  
- Callback dijalankan **setelah** aliran gambar tersedia, itulah mengapa kami dapat dengan aman **menulis aliran gambar** ke disk.

---

## Verifikasi Hasil

Setelah kode dijalankan Anda harus melihat dua hal di `YOUR_DIRECTORY`:

1. `DocWithImages.md` – file Markdown dengan referensi gambar yang terlihat seperti `![Image](assets/picture.png)`.  
2. Folder `assets` yang berisi file gambar sebenarnya (`picture.png`, `photo.jpg`, …).

Buka file Markdown di penampil apa pun (VS Code, GitHub, atau generator situs statis). Gambar-gambar harus ditampilkan dengan benar, mengonfirmasi bahwa Anda berhasil **mengonversi docx dengan gambar**.

---

## Menangani Kasus Tepi Umum

| Situasi | Apa yang Harus Dilakukan |
|-----------|------------|
| **Nama gambar duplikat** (mis., dua file `image1.png` yang identik) | Tambahkan GUID atau penghitung yang meningkat ke `fileName` sebelum menyimpan: <br>`string uniqueName = $"{Path.GetFileNameWithoutExtension(fileName)}_{Guid.NewGuid()}{Path.GetExtension(fileName)}";` |
| **Folder sumber hanya-baca** | Pastikan proses dijalankan dengan akun yang memiliki izin menulis, atau ubah `assetsFolder` ke lokasi yang dapat ditulis pengguna (mis., `%TEMP%`). |
| **Dokumen besar** (ratusan gambar) | Pertimbangkan melakukan streaming konversi dalam batch atau meningkatkan batas memori proses; Aspose.Words menangani file besar tetapi sistem file mungkin menjadi bottleneck. |
| **Sumber daya non‑gambar** (mis., PDF yang disematkan) | Callback yang sama berfungsi; hanya perlu diingat bahwa Markdown tidak dapat menyematkan PDF secara langsung—Anda mungkin perlu menyesuaikan format tautan secara manual. |

---

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class WordToMarkdownWithAssets
{
    static void Main()
    {
        // -------------------------------------------------------------------
        // Define input and output locations.
        // -------------------------------------------------------------------
        string inputPath   = @"C:\Temp\WithImages.docx";
        string outputDir   = @"C:\Temp\Output";
        string markdownPath = Path.Combine(outputDir, "DocWithImages.md");
        string assetsFolder = Path.Combine(outputDir, "assets");

        // -------------------------------------------------------------------
        // Step 1: Ensure the assets folder exists.
        // -------------------------------------------------------------------
        Directory.CreateDirectory(assetsFolder);

        // -------------------------------------------------------------------
        // Step 2: Load the Word document.
        // -------------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -------------------------------------------------------------------
        // Step 3: Set up Markdown save options with a resource callback.
        // -------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ResourceSavingCallback(resourceInfo =>
            {
                // Determine a safe file name.
                string originalName = Path.GetFileName(resourceInfo.FileName);
                string outputPath   = Path.Combine(assetsFolder, originalName);

                // Write the image (or other binary) stream to the assets folder.
                using (FileStream outStream = File.Create(outputPath))
                {
                    resourceInfo.Stream.CopyTo(outStream);
                }

                // Update the Markdown reference.
                resourceInfo.FileName = $"assets/{originalName}";
            })
        };

        // -------------------------------------------------------------------
        // Step 4: Save as Markdown.
        // -------------------------------------------------------------------
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Assets folder: {assetsFolder}");
    }
}
```

**Output yang diharapkan** (console):

```
Conversion complete!
Markdown: C:\Temp\Output\DocWithImages.md
Assets folder: C:\Temp\Output\assets
```

Buka `DocWithImages.md` dan Anda akan melihat tautan gambar yang mengarah ke `assets/…`. Gambar-gambar itu sendiri berada di direktori `assets` yang baru saja Anda buat.

---

## Kesimpulan

Kami telah menunjukkan cara **membuat folder assets** secara otomatis saat Anda **mengonversi Word ke Markdown**, dan cara **mengekstrak gambar dari docx** dengan **menulis aliran gambar** ke disk. Contoh lengkap yang dapat dijalankan ini memperlihatkan cara yang direkomendasikan untuk **mengonversi docx dengan gambar** menggunakan Aspose.Words, menangani baik konten Markdown maupun sumber daya terkait dalam satu operasi yang rapi.

Siap untuk langkah selanjutnya? Cobalah menyesuaikan callback untuk mengganti nama gambar berdasarkan alt‑text mereka, atau bereksperimen dengan format output lain seperti HTML atau PDF sambil menggunakan kembali logika folder assets yang sama. Pola ini dapat diskalakan dengan baik ke skenario konversi dokumen‑ke‑teks apa pun.

Jika Anda mengalami kendala atau memiliki ide untuk perbaikan, tinggalkan komentar di bawah


## Related Tutorials

- [Simpan Gambar Word – Konversi Word ke Markdown dengan Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Konversi Word ke Markdown – Sematkan Gambar sebagai Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [Konversi Word ke Markdown dalam C# – Panduan Lengkap dengan Ekstraksi Gambar](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-in-c-full-guide-with-image-extracti/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}