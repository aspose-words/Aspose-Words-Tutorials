---
category: general
date: 2026-01-05
description: Pelajari cara menyimpan markdown dan mengonversi docx ke markdown sambil
  mengekstrak gambar dari Word. Termasuk langkah demi langkah membuat folder sumber
  daya.
draft: false
keywords:
- how to save markdown
- convert docx to markdown
- extract images from word
- how to extract images
- create resources folder
language: id
og_description: Cara menyimpan markdown dari file DOCX, mengekstrak gambar, dan membuat
  folder sumber daya menggunakan Aspose.Words di C#.
og_title: Cara Menyimpan Markdown dari Word – Tutorial Lengkap
tags:
- Aspose.Words
- C#
- Markdown
title: Cara Menyimpan Markdown dari Word – Panduan Lengkap
url: /id/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-word-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyimpan Markdown dari Word – Panduan Lengkap

Pernah bertanya‑tanya **cara menyimpan markdown** langsung dari dokumen Word tanpa kehilangan gambar yang disematkan? Anda bukan satu‑satunya. Dalam banyak proyek kami perlu **mengonversi docx ke markdown**, mengekstrak gambar, dan menjaga semuanya rapi dalam folder khusus. Tutorial ini memandu Anda melalui solusi bersih dan dapat diulang menggunakan Aspose.Words untuk .NET.

Kami akan membahas semua yang Anda perlukan: memuat `.docx`, mengekstrak gambar, membuat **folder sumber daya**, dan akhirnya menulis file markdown. Pada akhir tutorial Anda akan memiliki potongan kode siap pakai yang dapat Anda sisipkan ke dalam aplikasi konsol atau web C# apa pun.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

* .NET 6.0 atau lebih baru (kode ini juga bekerja dengan .NET Framework 4.6+).  
* Salinan berlisensi **Aspose.Words for .NET** – versi percobaan gratis cukup untuk pengujian.  
* File Word (`input.docx`) yang berisi setidaknya satu gambar.  
* Familiaritas dasar dengan C# dan Visual Studio (atau IDE favorit Anda).

Tidak ada paket NuGet tambahan yang diperlukan selain Aspose.Words.

## Langkah 1 – Muat Dokumen Sumber

Hal pertama yang perlu kita lakukan adalah membaca file Word ke dalam objek `Aspose.Words.Document`. Objek ini memberi kita akses penuh ke konten dokumen, termasuk gambar yang akan Anda ekstrak nanti.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to point at your .docx file
string sourcePath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Create the Document instance – this is where the magic starts
Document document = new Document(sourcePath);
```

> **Mengapa ini penting:** Memuat file sebagai `Document` menyembunyikan struktur OOXML yang kompleks, memungkinkan kita bekerja dengan objek tingkat tinggi seperti gambar, tabel, dan paragraf.

## Langkah 2 – Implementasikan Callback Penyimpanan Sumber Daya

Aspose.Words memungkinkan Anda menyisipkan logika ke dalam proses penyimpanan melalui `IResourceSavingCallback`. Kita akan menggunakan ini untuk mengontrol ke mana setiap gambar yang diekstrak disimpan. Callback akan membuat **folder sumber daya** yang dinamai berdasarkan dokumen sumber dan menulis setiap file gambar ke dalamnya.

```csharp
// Step 2: Define a callback that decides where each resource (image) is stored
class ResourceSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a folder path like: YOUR_DIRECTORY/Resources/input.docx
        string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "Resources", args.DocumentName);
        Directory.CreateDirectory(resourcesFolder); // Guarantees the folder exists

        // Combine folder path with the original file name (e.g., image001.png)
        string resourcePath = Path.Combine(resourcesFolder, args.ResourceFileName);

        // Override the default name and supply a stream that writes the file
        args.ResourceFileName = resourcePath;
        args.Stream = new FileStream(resourcePath, FileMode.Create);
    }
}
```

> **Tips pro:** Jika Anda menginginkan struktur yang lebih datar (semua gambar dalam satu folder), cukup ganti `Path.Combine(..., args.DocumentName)` dengan nama folder konstan.

## Langkah 3 – Konfigurasikan Opsi Penyimpanan Markdown

Sekarang kita memberi tahu Aspose.Words untuk menggunakan Markdown sebagai format keluaran dan menyambungkan callback kita. Langkah ini adalah tempat operasi **mengonversi docx ke markdown** sebenarnya terjadi.

```csharp
// Step 3: Prepare the MarkdownSaveOptions and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This tells Aspose.Words to invoke our callback for every resource
    ResourceSavingCallback = new ResourceSavingCallback()
};
```

> **Apa yang terjadi di balik layar?** Perpustakaan menelusuri dokumen, mengonversi run paragraf, tabel, dan elemen lainnya menjadi sintaks Markdown, sambil menyerahkan setiap operasi penulisan gambar ke callback yang kita sediakan.

## Langkah 4 – Simpan Dokumen sebagai Markdown

Akhirnya, kita menulis file markdown ke disk. Gambar‑gambar sudah disimpan ke dalam folder yang kita buat pada langkah sebelumnya.

```csharp
// Step 4: Save the markdown file alongside the resources folder
string markdownPath = Path.Combine("YOUR_DIRECTORY", "WithImages.md");
document.Save(markdownPath, markdownOptions);

Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
Console.WriteLine("🖼️ Images extracted to the Resources folder.");
```

### Hasil yang Diharapkan

* `WithImages.md` – file markdown bersih di mana setiap referensi gambar terlihat seperti `![Image](Resources/input.docx/image001.png)`.  
* `Resources/input.docx/` – sub‑folder yang berisi semua gambar yang diekstrak (PNG, JPEG, dll.).

Anda dapat membuka file markdown di penampil apa pun (VS Code, GitHub, MkDocs) dan melihat gambar ditampilkan persis di tempatnya dalam file Word asli.

## Cara Mengekstrak Gambar Tanpa Mengonversi ke Markdown (Bonus)

Kadang‑kadang Anda hanya membutuhkan gambar, bukan markdown. Anda dapat menggunakan kembali logika callback yang sama tetapi memanggil `document.Save` dengan format berbeda, seperti `SaveFormat.Html`. Gambar‑gambar akan disimpan ke folder yang sama, dan Anda dapat mengabaikan file HTML setelahnya.

```csharp
HtmlSaveOptions htmlOptions = new HtmlSaveOptions
{
    ResourceSavingCallback = new ResourceSavingCallback()
};

document.Save(Path.Combine("YOUR_DIRECTORY", "temp.html"), htmlOptions);
```

> **Mengapa ini berhasil:** Penyimpanan HTML juga memicu callback sumber daya, memberi Anda solusi cepat “cara mengekstrak gambar” tanpa kode tambahan.

## Kesalahan Umum & Cara Menghindarinya

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| Gambar berakhir dengan nama duplikat | Beberapa gambar memiliki nama file asli yang sama di dalam Word. | Tambahkan GUID atau penghitung yang meningkat di dalam callback (`args.ResourceFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";`). |
| Tautan markdown mengarah ke folder yang tidak ada | Path folder `Resources` salah relatif terhadap file markdown. | Gunakan `Path.GetRelativePath` untuk menghitung path relatif, atau letakkan folder di samping file markdown seperti contoh di atas. |
| Aspose.Words melempar `FileNotFoundException` | Path `.docx` sumber tidak tepat. | Verifikasi path absolut dengan `Path.GetFullPath` sebelum membuat `Document`. |
| Dokumen besar menyebabkan error out‑of‑memory | Perpustakaan memuat seluruh dokumen ke memori. | Stream dokumen menggunakan overload `Document.Load` yang menerima `FileStream` dengan mode `ReadOnly`. |

## Contoh Lengkap yang Dapat Dijalankan (Copy‑Paste)

Berikut adalah *seluruh* program yang dapat Anda kompilasi dan jalankan. Ganti `YOUR_DIRECTORY` dengan folder nyata di mesin Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdown
{
    // Callback that saves each image to a resources folder
    class ResourceSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "Resources", args.DocumentName);
            Directory.CreateDirectory(resourcesFolder);

            string resourcePath = Path.Combine(resourcesFolder, args.ResourceFileName);
            args.ResourceFileName = resourcePath;
            args.Stream = new FileStream(resourcePath, FileMode.Create);
        }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the DOCX
            string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
            Document document = new Document(docPath);

            // 2️⃣ Set up Markdown options with our callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ResourceSavingCallback()
            };

            // 3️⃣ Save as Markdown – images are extracted automatically
            string mdPath = Path.Combine("YOUR_DIRECTORY", "WithImages.md");
            document.Save(mdPath, mdOptions);

            Console.WriteLine($"✅ Markdown saved to: {mdPath}");
            Console.WriteLine("🖼️ Images extracted to the Resources folder.");
        }
    }
}
```

Jalankan program (`dotnet run` atau tekan **F5** di Visual Studio) dan Anda akan melihat pesan konsol yang mengonfirmasi keberhasilan.

## Menguji Output Anda

Buka `WithImages.md` di penampil markdown:

```markdown
# Sample Heading

Here is an image extracted from the original Word file:

![Image](Resources/input.docx/image001.png)
```

Jika gambar muncul, Anda telah berhasil **menyimpan markdown** sambil mempertahankan konten visual. Jika tidak, periksa kembali path relatif yang dicetak oleh konsol.

## Memperluas Solusi

* **Konversi batch** – Loop melalui direktori berisi file `.docx`, gunakan kembali logika callback yang sama.  
* **Format gambar khusus** – Konversi semua gambar ke WebP di dalam callback untuk ukuran file yang lebih kecil.  
* **Pemrosesan paralel** – Gunakan `Parallel.ForEach` untuk batch besar, tetapi hati‑hati dengan kontensi sistem file.

Semua variasi ini tetap menjawab pertanyaan inti: **cara menyimpan markdown** dari Word dengan alur kerja **membuat folder sumber daya** yang bersih.

## Kesimpulan

Anda kini tahu **cara menyimpan markdown** dari dokumen Word, **mengonversi docx ke markdown**, dan **mengekstrak gambar dari Word** menggunakan Aspose.Words. Kuncinya adalah `IResourceSavingCallback`, yang memberi Anda kontrol penuh atas lokasi setiap gambar, secara efektif memungkinkan Anda **membuat folder sumber daya** yang sesuai dengan tata letak proyek Anda.

Cobalah, sesuaikan penamaan folder sesuai konvensi Anda, dan Anda akan memiliki pipeline yang kuat untuk dokumentasi, generator situs statis, atau skenario apa pun di mana markdown dan gambar harus tetap bersama.

---

*Selamat coding! Jika Anda mengalami kendala, tinggalkan komentar di bawah atau hubungi saya di GitHub – saya selalu siap membantu debugging cepat.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}