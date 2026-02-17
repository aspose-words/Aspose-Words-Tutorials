---
category: general
date: 2026-02-17
description: Simpan docx sebagai markdown & ekstrak gambar menggunakan Aspose.Words
  di C#. Pelajari cara mengonversi Word ke markdown dan mengambil gambar dari file
  DOCX.
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- extract images from docx
- Aspose.Words markdown
- C# document conversion
language: id
og_description: Simpan docx sebagai markdown dengan Aspose.Words di C#. Panduan ini
  menunjukkan cara mengonversi Word ke markdown dan mengekstrak gambar dari file DOCX.
og_title: Simpan docx sebagai markdown & ekstrak gambar – Panduan C#
tags:
- C#
- Aspose.Words
- Markdown
- DOCX
- Image extraction
title: Simpan docx sebagai markdown & ekstrak gambar – Panduan C#
url: /id/net/programming-with-markdownsaveoptions/save-docx-as-markdown-extract-images-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save docx as markdown & extract images – Panduan lengkap C# 

Pernahkah Anda perlu **save docx as markdown** tetapi juga mempertahankan setiap gambar, diagram, atau SVG yang ada di dalam file Word? Anda bukan satu‑satunya yang mengalami hal ini. Dalam banyak proyek—generator situs statis, pipeline dokumentasi, atau alat pencatatan sederhana—kami harus **convert word to markdown** sambil menjaga aset, jika tidak file yang dihasilkan akan terlihat seperti kota hantu.

Berita baik? Dengan Aspose.Words Anda dapat melakukan keduanya dalam beberapa baris kode. Tutorial ini memandu Anda melalui proses memuat `.docx`, mengonfigurasi objek `MarkdownSaveOptions`, menulis `IResourceSavingCallback` khusus yang menyalurkan setiap sumber eksternal ke dalam folder `assets`, dan akhirnya memverifikasi output. Tidak ada keajaiban, hanya C# biasa yang dapat Anda masukkan ke dalam aplikasi konsol .NET mana pun.

> **Pro tip:** Jika Anda hanya peduli pada teks dan tidak memerlukan gambar, Anda dapat melewatkan callback sepenuhnya—Aspose akan menyematkan data URI base‑64 secara default.

Di bawah ini Anda juga akan melihat cara **extract images from docx** secara manual, mengapa Anda mungkin ingin folder terpisah untuk mereka, dan beberapa tip kasus tepi untuk menjaga proses build Anda tetap lancar.

---

## Apa yang Anda butuhkan

- **.NET 6.0** (atau versi .NET terbaru apa pun). Framework lama masih dapat bekerja, tetapi sintaks yang ditunjukkan menggunakan fitur C# terbaru.
- **Aspose.Words for .NET** paket NuGet (`Install-Package Aspose.Words`).
- Dokumen Word contoh (`input.docx`) yang berisi setidaknya satu gambar.
- Folder tempat Anda ingin markdown dan aset disimpan (kami akan menyebutnya `YOUR_DIRECTORY`).

Itu saja—tanpa perpustakaan tambahan, tanpa alat baris perintah yang rumit. Hanya beberapa baris kode dan Anda akan memiliki file Markdown bersih serta sub‑folder `assets` yang siap untuk generator situs statis.

## Implementasi langkah‑demi‑langkah

### ## Save docx as markdown – Muat dokumen sumber

Pertama-tama, kita membutuhkan instance `Document` yang menunjuk ke file Word kita.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Path to the original DOCX file
        string sourcePath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        // Load the document into Aspose.Words
        Document doc = new Document(sourcePath);
```

> **Mengapa ini penting:** Memuat file memvalidasi bahwa DOCX terbentuk dengan baik. Jika file rusak, Aspose akan melemparkan pengecualian yang jelas, menyelamatkan Anda dari kesalahan downstream yang membingungkan.

### ## Convert word to markdown – Konfigurasi opsi penyimpanan dengan callback

Kelas `MarkdownSaveOptions` memungkinkan kita mengontrol bagaimana sumber daya (gambar, SVG, dll.) ditangani. Dengan menetapkan `ResourceSavingCallback` khusus, kita menentukan secara tepat ke mana setiap file disimpan.

```csharp
        // Step 2: Create save options and plug in our callback
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Our callback will write every image to the assets folder
            ResourceSavingCallback = new CustomResourceCallback()
        };
```

> **Tip:** Jika Anda lebih suka penyematan data‑uri (default), cukup hilangkan callback. Callback hanya diperlukan ketika Anda *extract images from docx* ke direktori terpisah.

### ## Extract images from docx – Implementasikan callback khusus

Callback menerima objek `ResourceSavingArgs` untuk setiap sumber eksternal. Kami menggunakannya untuk membuat folder `assets` (jika belum ada), mengganti nama jalur file, dan membuka `FileStream` untuk menulis.

```csharp
        // Step 3: Save the markdown file; resources are handled by the callback
        string markdownPath = Path.Combine("YOUR_DIRECTORY", "DocWithResources.md");
        doc.Save(markdownPath, mdOptions);
    }
}

// ---------------------------------------------------------------------
// Custom callback that stores all external resources in a sub‑folder "assets"
public class CustomResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build the assets folder path (e.g., YOUR_DIRECTORY/assets)
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder); // No‑op if it already exists

        // Preserve the original file name but prepend the assets folder
        string fileName = Path.GetFileName(args.ResourceFileName);
        args.ResourceFileName = Path.Combine(assetsFolder, fileName);

        // Open a stream that writes the resource to disk
        args.Stream = new FileStream(args.ResourceFileName, FileMode.Create);
    }
}
```

> **Apa yang terjadi di balik layar?** Aspose men-stream setiap gambar (PNG, JPEG, GIF, SVG, dll.) ke `args.Stream` yang Anda sediakan. Dengan mengganti stream default dengan `FileStream` yang mengarah ke `assets/<image-name>`, kita secara efektif *extract images from docx* dan menjaga markdown tetap bersih.

### ## Verify the output – Apa yang harus Anda lihat

Setelah Anda menjalankan program:

1. `YOUR_DIRECTORY/DocWithResources.md` berisi teks Markdown dengan tautan gambar seperti `![](assets/image1.png)`.
2. `YOUR_DIRECTORY/assets/` menyimpan setiap gambar yang ada di `input.docx`.

Buka file markdown di editor apa pun—jika Anda melihat placeholder gambar ditampilkan dengan benar, Anda telah berhasil **save docx as markdown** sambil mengekstrak semua aset.

## Variasi umum & kasus tepi

### ### Menangani aset yang sudah ada

Jika Anda menjalankan konversi berkali‑kali, Anda mungkin secara tidak sengaja menimpa gambar. Langkah pengamanan cepat adalah menambahkan timestamp atau GUID ke setiap nama file:

```csharp
string uniqueName = $"{Path.GetFileNameWithoutExtension(fileName)}_{Guid.NewGuid()}{Path.GetExtension(fileName)}";
args.ResourceFileName = Path.Combine(assetsFolder, uniqueName);
```

### ### Gambar besar atau PDF yang disematkan sebagai gambar

Aspose.Words men-stream byte mentah, sehingga bahkan diagram 10 MB akan disimpan apa adanya. Namun, renderer Markdown mungkin kesulitan dengan file besar. Pertimbangkan untuk mengubah ukuran gambar sebelum menyimpan:

```csharp
// Example using System.Drawing (requires System.Drawing.Common on .NET Core)
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var resized = new Bitmap(img, new Size(800, 0)); // Keep aspect ratio
    resized.Save(args.ResourceFileName, img.RawFormat);
}
```

> **Peringatan:** Potongan kode untuk mengubah ukuran bersifat opsional dan menambahkan ketergantungan pada `System.Drawing.Common`. Gunakan hanya jika pipeline Anda memerlukan aset yang lebih kecil.

### ### Penanganan SVG

SVG adalah grafik vektor; kebanyakan generator situs statis memperlakukan mereka sebagai file biasa. Callback berfungsi tanpa perubahan, tetapi pastikan prosesor Markdown Anda mendukung SVG inline (misalnya, GitHub Pages mendukungnya).

### ### Sumber daya non‑gambar (font, objek OLE)

Aspose juga memperlakukan font, objek OLE, dan blob biner lainnya sebagai sumber daya. Jika Anda hanya peduli pada gambar, filter berdasarkan ekstensi:

```csharp
if (!args.ResourceFileName.EndsWith(".png", StringComparison.OrdinalIgnoreCase) &&
    !args.ResourceFileName.EndsWith(".jpg", StringComparison.OrdinalIgnoreCase) &&
    !args.ResourceFileName.EndsWith(".svg", StringComparison.OrdinalIgnoreCase))
{
    // Skip non‑image resources
    args.Skip = true;
    return;
}
```

## Contoh lengkap yang dapat dijalankan (siap salin‑tempel)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Load the source DOCX
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2️⃣ Set up Markdown save options with a custom resource callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new CustomResourceCallback()
        };

        // -----------------------------------------------------------------
        // 3️⃣ Save as Markdown; the callback will store images in assets/
        // -----------------------------------------------------------------
        string markdownPath = Path.Combine("YOUR_DIRECTORY", "DocWithResources.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("🖼️  Images extracted to: assets folder");
    }
}

// ---------------------------------------------------------------------
// Custom callback – extracts every external resource into YOUR_DIRECTORY/assets
// ---------------------------------------------------------------------
public class CustomResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build assets folder (creates it if missing)
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder);

        // Keep the original file name, but place it in assets/
        string fileName = Path.GetFileName(args.ResourceFileName);
        args.ResourceFileName = Path.Combine(assetsFolder, fileName);

        // Write the resource to disk
        args.Stream = new FileStream(args.ResourceFileName, FileMode.Create);
    }
}
```

**Hasil yang diharapkan:**  
- `DocWithResources.md` berisi markdown seperti `![](assets/image1.png)`.  
- Direktori `assets` menyimpan `image1.png`, `image2.svg`, dll.  
- Membuka markdown di VS Code atau pratinjau situs statis menampilkan gambar secara inline.

## Pertanyaan yang sering diajukan (FAQ)

| Pertanyaan | Jawaban |
|------------|---------|
| *Do I need a license for Aspose.Words?* | The library works in

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}