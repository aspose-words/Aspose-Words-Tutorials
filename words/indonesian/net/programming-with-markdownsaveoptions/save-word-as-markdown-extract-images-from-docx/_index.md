---
category: general
date: 2026-02-13
description: Simpan Word sebagai markdown dan ekstrak gambar dari docx di C#. Pelajari
  cara mengonversi docx ke markdown, menyimpan gambar dari docx, dan menjaga sumber
  daya tetap terorganisir.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- how to extract images
- save images from docx
language: id
og_description: simpan Word sebagai markdown dan ekstrak gambar dari docx dengan contoh
  C# lengkap. konversi docx ke markdown, simpan gambar dari docx, dan jaga semuanya
  tetap rapi.
og_title: simpan Word sebagai markdown – ekstrak gambar dari docx
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Simpan Word sebagai Markdown – Ekstrak Gambar dari DOCX
url: /id/net/programming-with-markdownsaveoptions/save-word-as-markdown-extract-images-from-docx/
---

Now produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# simpan word sebagai markdown – ekstrak gambar dari docx

Pernah perlu **simpan word sebagai markdown** tetapi juga ingin mempertahankan setiap gambar yang ada di dalam *.docx* asli? Mungkin Anda sedang membangun static site generator, atau hanya ingin memindahkan laporan Word lama ke format yang ramah Git. Bagaimanapun, masalahnya sama: konversi menghilangkan gambar, atau Anda berakhir dengan sekumpulan tautan yang rusak.

Begini, Anda tidak perlu menulis parser khusus atau menelusuri struktur ZIP *.docx* secara manual. Dengan Aspose.Words Anda dapat **mengonversi docx ke markdown** dan, pada saat yang sama, **menyimpan gambar dari docx** ke folder pilihan Anda. Dalam panduan ini kami akan menelusuri program C# lengkap yang siap dijalankan dan melakukan hal tersebut.

Anda akan mendapatkan:

* File markdown yang mencerminkan tata letak Word asli.
* Folder “MarkdownResources” yang berisi setiap gambar yang diekstrak, dengan nama persis seperti di sumber.
* Pola callback yang dapat digunakan kembali dan dapat Anda adaptasi untuk PDF, HTML, atau format lain yang didukung Aspose.

> **Prasyarat** – Anda memerlukan .NET 6+ (atau .NET Framework 4.7+), lisensi Aspose.Words yang valid (atau trial gratis), serta Visual Studio atau VS Code. Tidak ada paket NuGet lain yang diperlukan.

---

## Apa yang dibahas dalam tutorial ini

Kami akan membagi solusi menjadi langkah‑langkah logis:

1. **Muat dokumen sumber** – buka *.docx* yang ingin Anda konversi.  
2. **Buat callback penyimpanan sumber daya** – ini memberi tahu Aspose ke mana menaruh setiap gambar.  
3. **Konfigurasikan `MarkdownSaveOptions`** – sambungkan callback ke exporter markdown.  
4. **Simpan file markdown** – satu baris kode melakukan semua pekerjaan berat.  

Sepanjang proses kami akan menjelaskan *mengapa* setiap bagian penting, menyoroti jebakan umum (seperti izin folder yang hilang), dan menunjukkan cara menyesuaikan kode untuk kasus khusus seperti ekstraksi hanya PNG atau penamaan gambar khusus.

---

## Langkah 1 – Muat dokumen sumber

Sebelum melakukan apa pun Anda memerlukan instance `Document` yang menunjuk ke file Word Anda. Aspose mengabstraksi format ZIP *.docx* sehingga Anda dapat memperlakukannya seperti objek dokumen lainnya.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to where your .docx lives.
const string inputPath = @"YOUR_DIRECTORY\input.docx";

Document doc = new Document(inputPath);
```

*Mengapa ini penting*: Jika jalur file salah, Aspose akan melempar `FileNotFoundException` dan seluruh pipeline berhenti. Menggunakan konstanta (atau lebih baik lagi, nilai konfigurasi) memudahkan penggantian file tanpa mengubah logika inti.

> **Tips pro** – Bungkus proses pemuatan dalam try/catch bila file di‑supplied oleh pengguna. Dengan begitu Anda dapat menampilkan pesan error yang bersahabat alih‑alih menampilkan stack trace.

---

## Langkah 2 – Definisikan callback yang menentukan tempat penyimpanan setiap gambar

Aspose memungkinkan Anda menyisipkan proses penyimpanan melalui `IResourceSavingCallback`. Callback menerima objek `ResourceSavingArgs` untuk setiap sumber daya eksternal (gambar, CSS, dll.). Kami akan menggunakannya untuk menyalurkan setiap gambar ke folder khusus sambil mempertahankan nama file aslinya.

```csharp
// Step 2: Define a callback that decides where each image is saved.
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a path like: YOUR_DIRECTORY\MarkdownResources\image001.png
        string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
        Directory.CreateDirectory(resourcesFolder); // ensures the folder exists

        string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);

        // Tell Aspose where to write the file.
        args.ResourceFilePath = imagePath;
        args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
    }
}
```

*Mengapa ini penting*: Tanpa callback, Aspose akan menaruh gambar di folder yang sama dengan file markdown dan memberi nama generik. Dengan mengontrol jalur, Anda menjaga proyek tetap rapi dan menghindari tabrakan nama.

**Kasus khusus** – Beberapa file Word menyisipkan gambar yang sama berkali‑kali. `args.ResourceFileName` sudah mengandung hash unik, sehingga tidak akan terjadi penimpaan. Jika Anda lebih suka skema penamaan berurutan, Anda dapat mempertahankan counter statis di dalam callback.

---

## Langkah 3 – Konfigurasikan opsi penyimpanan Markdown untuk menggunakan callback khusus

Sekarang kita hubungkan callback ke exporter markdown. `MarkdownSaveOptions` juga memungkinkan Anda menyesuaikan hal‑hal seperti level heading, fence kode blok, atau apakah menyematkan gambar sebagai Base64 (kami *tidak* melakukannya di sini).

```csharp
// Step 3: Configure Markdown save options to use the custom callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Attach our resource‑saving logic.
    ResourceSavingCallback = new MyMarkdownResourceCallback(),

    // Optional: keep original line breaks for better diff‑friendliness.
    ExportHeadersFooters = false,
    ExportImagesAsBase64 = false
};
```

*Mengapa ini penting*: Properti `ResourceSavingCallback` adalah jembatan antara model dokumen dan sistem file. Jika tidak diset, gambar akan hilang, dan markdown Anda akan merujuk ke file yang tidak ada.

---

## Langkah 4 – Simpan dokumen sebagai Markdown, memanggil callback untuk setiap sumber daya

Akhirnya, kita meminta Aspose menulis file markdown. Library akan memanggil callback kita untuk setiap gambar, menulis file gambar, lalu menyisipkan tautan relatif di markdown.

```csharp
// Step 4: Save the document as Markdown, invoking the callback for each resource.
const string outputPath = @"YOUR_DIRECTORY\output.md";

doc.Save(outputPath, mdOptions);
```

Setelah kode selesai, Anda akan melihat dua hal di disk:

1. **output.md** – representasi Markdown dari konten Word asli.  
2. **MarkdownResources/** – folder yang berisi setiap gambar yang diekstrak (misalnya `image001.png`, `image002.jpg`).

**Verifikasi** – Buka `output.md` di penampil markdown apa pun. Anda akan melihat tag gambar seperti `![image001.png](MarkdownResources/image001.png)`. Jika gambar tampil, Anda berhasil.

---

## Variasi umum dan skenario “bagaimana jika”

### 1. Ingin gambar disematkan sebagai Base64?

Setel `ExportImagesAsBase64 = true` pada `MarkdownSaveOptions`. Ini menghasilkan satu file markdown dengan data URI inline—berguna untuk dokumentasi satu‑file tetapi memperbesar ukuran file.

### 2. Hanya butuh gambar PNG?

Modifikasi callback untuk menyaring berdasarkan ekstensi:

```csharp
if (Path.GetExtension(args.ResourceFileName).Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Save as before.
}
else
{
    // Skip non‑PNG resources.
    args.Cancel = true;
}
```

### 3. Mengubah folder output saat runtime

Teruskan jalur folder melalui argumen baris perintah atau file konfigurasi, lalu gunakan variabel tersebut saat membangun `resourcesFolder`. Ini membuat alat dapat dipakai ulang di berbagai proyek.

### 4. Menangani dokumen besar

Untuk file Word yang sangat besar, pertimbangkan streaming output untuk menghindari memuat semuanya ke memori. Kelas `Document` milik Aspose sudah bekerja dengan jejak memori rendah, namun Anda juga dapat menyetel `MemoryOptimization = MemoryOptimization.MemoryOptimized` pada `LoadOptions`.

---

## Contoh lengkap yang dapat dijalankan

Berikut seluruh program yang dapat Anda salin‑tempel ke dalam aplikasi Console baru (`dotnet new console`). Jangan lupa ganti `YOUR_DIRECTORY` dengan jalur yang sebenarnya di mesin Anda dan tambahkan paket NuGet Aspose.Words (`dotnet add package Aspose.Words`).

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdown
{
    // Step 2: Callback that saves each image into a dedicated folder.
    class MyMarkdownResourceCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
            Directory.CreateDirectory(resourcesFolder);

            string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);
            args.ResourceFilePath = imagePath;
            args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Load the source document.
            const string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);

            // Step 3: Configure the markdown options.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyMarkdownResourceCallback(),
                ExportImagesAsBase64 = false,
                ExportHeadersFooters = false
            };

            // Step 4: Save as markdown.
            const string outputPath = @"YOUR_DIRECTORY\output.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
            Console.WriteLine($"Images folder: {Path.Combine("YOUR_DIRECTORY", "MarkdownResources")}");
        }
    }
}
```

**Output yang diharapkan** (di konsol):

```
Conversion complete!
Markdown file: C:\Projects\MyDocs\output.md
Images folder: C:\Projects\MyDocs\MarkdownResources
```

Buka `output.md` dan Anda akan melihat sintaks markdown dengan referensi gambar yang mengarah ke folder `MarkdownResources`. Semua gambar mempertahankan nama file aslinya, sehingga Anda dapat melacak kembali ke file Word sumber bila diperlukan.

---

## Kesimpulan

Kami baru saja menunjukkan cara **simpan word sebagai markdown** sekaligus **ekstrak gambar dari docx** menggunakan Aspose.Words. Inti utama adalah `IResourceSavingCallback`—ia memberi Anda kontrol penuh atas lokasi setiap sumber daya, memungkinkan markdown tetap rapi dan gambar terorganisir.

Dalam satu program mandiri Anda dapat:

* Mengonversi *.docx* apa pun ke markdown bersih (`convert docx to markdown`).  
* Mempertahankan setiap gambar (`save images from docx`).  
* Menyesuaikan tata letak output untuk pipeline downstream.

Langkah selanjutnya? Coba konversi ke HTML atau PDF dengan pola callback yang sama, atau integrasikan ini ke dalam job CI yang secara otomatis menyinkronkan laporan Word ke repositori static‑site. Kemungkinannya tak terbatas, dan kini Anda memiliki fondasi yang kuat untuk membangunnya.

Punya pertanyaan, atau menemukan trik cerdas? Tinggalkan komentar di bawah—selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}