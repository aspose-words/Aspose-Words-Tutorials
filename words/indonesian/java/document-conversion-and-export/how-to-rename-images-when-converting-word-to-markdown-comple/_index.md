---
category: general
date: 2025-12-18
description: Pelajari cara mengganti nama gambar saat mengonversi dokumen Word ke
  Markdown, serta petunjuk langkah demi langkah untuk mengonversi docx ke markdown
  dan mengekspor docx ke markdown secara efisien.
draft: false
keywords:
- how to rename images
- convert word to markdown
- export docx to markdown
- how to convert docx
- how to extract images
language: id
og_description: Temukan cara mengganti nama gambar saat konversi Word ke Markdown,
  lengkap dengan contoh kode untuk mengekspor docx ke markdown dan mengekstrak gambar.
og_title: cara mengganti nama gambar – panduan konversi Word ke Markdown
tags:
- Aspose.Words
- C#
- Markdown conversion
title: cara mengganti nama gambar saat mengonversi Word ke Markdown – panduan lengkap
url: /id/java/document-conversion-and-export/how-to-rename-images-when-converting-word-to-markdown-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara mengganti nama gambar – Tutorial Lengkap untuk Konversi Word ke Markdown

Pernah bertanya-tanya **bagaimana cara mengganti nama gambar** saat Anda mengubah sebuah Word .docx menjadi Markdown yang bersih? Anda tidak sendirian. Banyak pengembang mengalami masalah ketika nama gambar default menjadi kumpulan GUID yang berantakan, membuat Markdown akhir sulit dibaca dan dipelihara.  

Dalam panduan ini kami akan membahas solusi lengkap yang dapat dijalankan yang tidak hanya **bagaimana cara mengganti nama gambar**, tetapi juga menunjukkan **cara mengonversi word ke markdown**, **mengekspor docx ke markdown**, dan bahkan **cara mengekstrak gambar** untuk pemrosesan terpisah. Pada akhir tutorial Anda akan memiliki satu skrip C# yang melakukan semuanya—tanpa alat tambahan, tanpa mengganti nama secara manual.

> **Pratinjau cepat:** Kami akan menggunakan Aspose.Words untuk .NET, menyiapkan callback `MarkdownSaveOptions`, dan mengganti nama setiap gambar yang disematkan menjadi nama file yang unik dan mudah dibaca manusia. Semua kode siap untuk disalin‑tempel.

## Apa yang Akan Anda Pelajari

- **Mengapa mengganti nama gambar penting** – keterbacaan, SEO, dan kontrol versi.
- **Cara mengonversi Word ke Markdown** menggunakan Aspose.Words.
- **Cara mengekspor DOCX ke Markdown** dengan penanganan sumber daya khusus.
- **Cara mengekstrak gambar** dari DOCX dan menyimpannya di folder pilihan Anda.
- Tips praktis, penanganan kasus tepi, dan contoh lengkap yang dapat dijalankan.

**Prasyarat**

- .NET 6.0 atau lebih baru (kode ini bekerja dengan .NET Core dan .NET Framework).
- Perpustakaan Aspose.Words untuk .NET (versi percobaan gratis atau berlisensi).
- Pengetahuan dasar C# – jika Anda dapat menulis `Console.WriteLine`, Anda sudah cukup.

## Cara Mengganti Nama Gambar Selama Konversi Word ke Markdown

Ini adalah inti dari tutorial. `MarkdownSaveOptions.ResourceSavingCallback` memberikan kami kait untuk setiap sumber daya yang disematkan (gambar, audio, dll.). Di dalam callback kami menghasilkan nama file baru, menulis aliran ke disk, dan memberi tahu Aspose apa nama baru yang harus digunakan.

![How to rename images example – screenshot of renamed image files](/images/how-to-rename-images-example.png "how to rename images during conversion")

### Langkah 1: Instal Aspose.Words

Tambahkan paket NuGet ke proyek Anda:

```bash
dotnet add package Aspose.Words
```

Atau melalui Package Manager Console:

```powershell
Install-Package Aspose.Words
```

### Langkah 2: Siapkan MarkdownSaveOptions dengan Callback Penggantian Nama

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Define the folder where images will be saved
string imageFolder = Path.Combine(Environment.CurrentDirectory, "myImages");
Directory.CreateDirectory(imageFolder);

// Create Markdown save options
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

// Set up the callback that runs for each embedded resource
mdOptions.ResourceSavingCallback = (resource, stream) =>
{
    // Only act on images – other resources (like audio) are left untouched
    if (resource.Type == ResourceType.Image)
    {
        // Generate a friendly, unique name: img_<guid>.png
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Build the full path and copy the stream
        string fullPath = Path.Combine(imageFolder, newFileName);
        using (FileStream file = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            stream.CopyTo(file);
        }

        // Tell Aspose the new filename so the Markdown reference is correct
        resource.FileName = newFileName;
    }
};
```

**Mengapa ini berhasil:**  
- Callback menerima objek `ResourceSavingArgs` (`resource`) dan sebuah `Stream`.  
- Dengan memeriksa `resource.Type == ResourceType.Image` kami menghindari mengutak‑atik sumber daya non‑gambar.  
- `Guid.NewGuid():N` menghasilkan string heksadesimal 32‑karakter tanpa tanda hubung, menjamin keunikan.  
- Memperbarui `resource.FileName` menulis ulang tautan gambar Markdown (`![](img_…png)`).

### Langkah 3: Muat DOCX dan Simpan sebagai Markdown

```csharp
// Path to the source Word document
string docxPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document
Document doc = new Document(docxPath);

// Export to Markdown, applying our custom resource handling
string markdownPath = Path.Combine(Environment.CurrentDirectory, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Conversion complete! Markdown saved to {markdownPath}");
Console.WriteLine($"Images saved to {imageFolder}");
```

Itu saja. Menjalankan program menghasilkan:

- `output.md` – Markdown bersih dengan referensi gambar seperti `![](img_1a2b3c4d5e6f7g8h9i0j1k2l3m4n5o6p.png)`.
- Sebuah folder `myImages` yang berisi setiap file gambar dengan nama yang sama ramah.

## Konversi Word ke Markdown – Contoh Lengkap

Jika Anda lebih suka skrip satu‑file, salin berikut ke `Program.cs` dan jalankan:

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // ---------- Configuration ----------
        string inputDocx = "YOUR_DIRECTORY/input.docx";
        string outputMd = "YOUR_DIRECTORY/output.md";
        string imagesDir = Path.Combine("YOUR_DIRECTORY", "myImages");
        Directory.CreateDirectory(imagesDir);

        // ---------- Step 1: Set up Markdown options ----------
        var mdOptions = new MarkdownSaveOptions();
        mdOptions.ResourceSavingCallback = (resource, stream) =>
        {
            if (resource.Type == ResourceType.Image)
            {
                string uniqueName = $"img_{Guid.NewGuid():N}.png";
                string destPath = Path.Combine(imagesDir, uniqueName);
                using (var file = new FileStream(destPath, FileMode.Create, FileAccess.Write))
                    stream.CopyTo(file);
                resource.FileName = uniqueName;
            }
        };

        // ---------- Step 2: Load DOCX ----------
        var doc = new Document(inputDocx);

        // ---------- Step 3: Save as Markdown ----------
        doc.Save(outputMd, mdOptions);

        Console.WriteLine($"✅ Done! Markdown at {outputMd}");
        Console.WriteLine($"🖼️ Images saved in {imagesDir}");
    }
}
```

**Penjelasan setiap blok**

| Block | Purpose |
|-------|---------|
| **Configuration** | Memusatkan jalur sehingga Anda hanya mengeditnya sekali. |
| **Step 1** | Membuat `MarkdownSaveOptions` dan callback penggantian nama. |
| **Step 2** | Memuat `.docx` ke dalam objek `Document` Aspose. |
| **Step 3** | Memanggil `Save` dengan opsi khusus, menulis baik Markdown maupun gambar yang telah diganti nama. |

Jalankan dengan:

```bash
dotnet run
```

Anda akan melihat dua pesan konsol yang mengonfirmasi keberhasilan.

## Ekspor DOCX ke Markdown – Mengapa Pendekatan Ini Lebih Baik daripada Alat Manual

- **Otomatisasi** – Tidak perlu membuka Word, menyalin‑tempel, dan mengganti nama file secara manual.  
- **Konsistensi** – Setiap gambar mendapatkan nama yang dapat diprediksi dan unik, yang sangat baik untuk kontrol versi (Git tidak akan menganggap file berubah hanya karena GUID berubah).  
- **Skalabilitas** – Bekerja untuk dokumen dengan puluhan atau ratusan gambar; callback dipicu untuk setiap sumber daya secara otomatis.  
- **Portabilitas** – Markdown yang dihasilkan bekerja di generator situs statis apa pun (Jekyll, Hugo, MkDocs) karena tautan gambar bersifat relatif dan bersih.

## Cara Mengekstrak Gambar dari File DOCX (Bonus)

Kadang-kadang Anda hanya menginginkan gambar mentah, bukan file Markdown. Callback yang sama dapat digunakan kembali, atau Anda dapat menggunakan API `Document` Aspose secara langsung:

```csharp
using Aspose.Words;
using System.IO;

// Load the document
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Iterate over all shapes (including inline images)
int imgCount = 0;
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage)
    {
        imgCount++;
        string imgPath = Path.Combine("YOUR_DIRECTORY/extractedImages", $"extracted_{imgCount}.png");
        shape.ImageData.Save(imgPath);
    }
}
Console.WriteLine($"{imgCount} images extracted.");
```

**Poin penting**

- `NodeType.Shape` menangkap gambar baik yang mengambang maupun inline.  
- `shape.ImageData.Save` menulis gambar biner langsung ke disk.  
- Anda dapat menggabungkan potongan kode ini dengan konversi Markdown jika memerlukan kedua output.

## Tips Praktis & Kesalahan Umum

- **Tabrakan penamaan:** Menggunakan GUID pada dasarnya menghilangkan tabrakan, tetapi jika Anda memerlukan nama yang dapat dibaca manusia (mis., `chapter1_figure2.png`), Anda dapat menurunkan nama dari `resource.Name` atau teks paragraf di sekitarnya.  
- **Dokumen besar:** Stream disalin langsung ke disk; untuk file yang sangat besar pertimbangkan buffering atau menulis ke lokasi sementara terlebih dahulu.  
- **Gambar non‑PNG:** Callback di atas memaksa ekstensi `.png`. Jika gambar sumber adalah JPEG, Anda mungkin ingin mempertahankan format aslinya: `Path.GetExtension(resource.FileName)` atau `resource.ContentType`.  
- **Kinerja:** Callback dijalankan secara sinkron. Jika Anda memproses puluhan dokumen secara paralel, bungkus konversi dalam `Task.Run` atau gunakan thread‑pool untuk menghindari pemblokiran UI.  
- **Lisensi:** Aspose.Words dapat bekerja tanpa lisensi dalam mode evaluasi, tetapi akan menambahkan watermark pada output. Pasang file lisensi (`Aspose.Words.lic`) untuk mendapatkan hasil bersih.

## Kesimpulan

Kami telah membahas **cara mengganti nama gambar** saat mengonversi dokumen Word ke Markdown, menunjukkan alur kerja lengkap **konversi word ke markdown**, mendemonstrasikan **ekspor docx ke markdown** dengan penanganan sumber daya khusus, dan bahkan menjelaskan **cara mengekstrak gambar** dari file DOCX. Kode tersebut mandiri, modern, dan siap untuk produksi.

Cobalah—letakkan `.docx` Anda ke dalam folder, jalankan skrip, dan saksikan Markdown bersih serta file gambar dengan nama rapi muncul. Dari situ Anda dapat mengirimkan Markdown ke generator situs statis, meng-commit gambar ke Git, atau memasukkan output ke dalam pipeline dokumentasi.

Ada pertanyaan tentang kasus tepi atau ingin mengintegrasikan ini ke dalam layanan ASP.NET Core? Tinggalkan komentar, dan kami akan menjelajahi skenario tersebut bersama. Selamat mengonversi!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}