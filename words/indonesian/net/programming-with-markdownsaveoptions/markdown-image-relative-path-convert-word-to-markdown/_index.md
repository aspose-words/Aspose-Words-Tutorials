---
category: general
date: 2026-04-28
description: Pelajari cara mengatur jalur relatif gambar markdown saat Anda mengonversi
  Word ke markdown, mengekstrak gambar dari Word, dan membuat folder sumber daya untuk
  gambar yang diekspor.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: id
og_description: Atur jalur relatif gambar markdown saat Anda mengonversi Word ke markdown,
  mengekstrak gambar dari Word, dan membuat folder sumber daya untuk gambar yang diekspor.
og_title: Jalur Relatif Gambar Markdown – Konversi Word ke Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: Jalur Relatif Gambar Markdown – Konversi Word ke Markdown
url: /id/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jalur relatif gambar markdown – Mengonversi Word ke Markdown

Pernah membutuhkan **jalur relatif gambar markdown** saat Anda **mengonversi Word ke markdown**? Anda tidak sendirian. Kebanyakan pengembang mengalami masalah ketika Markdown yang dihasilkan menunjuk ke gambar di folder datar, memutuskan struktur tautan relatif yang Anda harapkan di situs statis atau repositori GitHub.

Dalam tutorial ini kita akan membahas solusi lengkap, end‑to‑end yang **mengekstrak gambar dari Word**, **membuat folder resources**, dan menulis ulang referensi gambar sehingga menggunakan *jalur relatif gambar markdown* yang bersih. Pada akhir tutorial Anda akan memiliki file `.md` siap‑terbit dan direktori `Resources` yang terorganisir rapi berisi setiap gambar yang diekstrak dari `.docx` asli.

> **Apa yang akan Anda dapatkan:** satu program C# (tanpa skrip eksternal), penjelasan jelas tentang *mengapa* setiap bagian penting, dan beberapa tips praktis yang dapat Anda salin‑tempel ke proyek Anda sendiri.

---

## Prasyarat

Sebelum kita masuk ke kode, pastikan Anda memiliki:

- **.NET 6.0** atau yang lebih baru terpasang (Anda juga dapat menargetkan .NET Framework 4.7+, tetapi .NET 6 adalah pilihan tepat untuk proyek baru).
- **Aspose.Words for .NET** (paket NuGet terbaru pada saat penulisan, versi 23.12). Instal dengan:
  ```bash
  dotnet add package Aspose.Words
  ```
- Dokumen Word yang memang berisi gambar—misalnya `WithImages.docx`.
- Folder tempat Anda ingin menyimpan markdown hasil dan gambar, misalnya `C:\Projects\MarkdownExport`.

Tidak ada pustaka tambahan yang diperlukan; semua hal lain ditangani oleh Aspose.Words.

---

## Langkah 1: Muat dokumen Word sumber (titik awal untuk mengonversi word ke markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Mengapa ini penting:* Memuat dokumen memberi kita akses ke pohon node internal, yang mencakup bagian gambar yang nanti akan **mengekspor gambar dari docx**. Jika pemuatan gagal, langkah‑langkah selanjutnya tidak akan berjalan, jadi periksa kembali jalur dan izin file.

---

## Langkah 2: Konfigurasikan `MarkdownSaveOptions` dengan callback khusus (inti dari membuat folder resources)

`ResourceSavingCallback` memungkinkan kita menyela setiap kali Aspose.Words ingin menulis file gambar. Di dalam callback kita akan **membuat sub‑folder Resources** dan menyesuaikan referensi sehingga markdown yang dihasilkan menggunakan *jalur relatif gambar markdown*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

Perhatikan kami mengoper `resourcesFolder` ke konstruktor callback—ini menjaga jalur folder tetap fleksibel dan menghindari hard‑coding string di seluruh kode.

---

## Langkah 3: Implementasikan callback yang **membuat folder resources** dan menulis ulang jalur

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Mengapa ini berhasil:* `args.Stream` berisi byte gambar mentah. Dengan menyalinnya ke file di dalam folder `Resources` kita **mengekspor gambar dari docx** dengan aman. Kemudian kita mengganti `args.ResourceFileName` dengan URL relatif (`Resources/image.png`). Saat Aspose.Words kemudian menulis markdown, ia menyuntikkan string tersebut persis, memberi kita *jalur relatif gambar markdown* yang diinginkan.

---

## Langkah 4: Verifikasi Markdown yang dihasilkan (seperti apa output akhir)

Buka `Doc.md` di editor teks apa pun. Anda akan melihat sesuatu yang mirip dengan:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

Bagian pentingnya adalah setiap referensi gambar menunjuk ke `Resources/...` – itulah **jalur relatif gambar markdown** yang kita cari.

![contoh jalur relatif gambar markdown](example.png "contoh jalur relatif gambar markdown")

*Tip:* Jika Anda membuka markdown di penampil yang menghormati tautan relatif (pratinjau VS Code, GitHub, atau generator situs statis), gambar akan ditampilkan dengan benar tanpa konfigurasi tambahan.

---

## Langkah 5: Kesalahan umum dan pro‑tips

| Masalah | Mengapa terjadi | Cara memperbaikinya |
|---------|----------------|---------------------|
| Gambar berakhir di folder root alih‑alih `Resources` | Callback tidak terpasang atau `args.ResourceFileName` tidak ditimpa. | Pastikan `ResourceSavingCallback` diset **sebelum** memanggil `doc.Save`. |
| Nama file mengandung karakter ilegal | Word kadang memberi nama gambar dengan spasi atau simbol Unicode. | Gunakan `Path.GetInvalidFileNameChars()` untuk membersihkan `args.ResourceFileName` di dalam callback. |
| Dokumen besar memakan waktu lama untuk diproses | Setiap gambar ditulis secara sinkron. | Beralih ke I/O asynchronous (`await args.Stream.CopyToAsync(fileStream)`) jika Anda berada di .NET 6+ dan membutuhkan performa. |
| Jalur relatif rusak saat markdown dipindahkan | Jalur relatif terhadap lokasi file markdown. | Simpan `Doc.md` dan folder `Resources` bersama, atau sesuaikan callback untuk menggunakan prefiks relatif lain (misalnya `../assets`). |

---

## Langkah 6: Memperluas solusi (bagaimana jika Anda membutuhkan kontrol lebih?)

- **Beberapa format output:** Ganti `MarkdownSaveOptions` dengan `HtmlSaveOptions` atau `PdfSaveOptions` sambil tetap menggunakan callback yang sama—Aspose.Words akan memanggilnya untuk setiap gambar terlepas dari format.
- **Penamaan gambar khusus:** Jika Anda ingin mengganti nama gambar (misalnya `figure-01.png`), ubah `args.ResourceFileName` di dalam callback sebelum menulis file.
- **Menyematkan gambar sebagai Base64:** Set `args.ResourceFileName` ke data URI (`data:image/png;base64,...`) dan lewati penulisan file. Ini berguna untuk ekspor markdown satu‑file.

---

## Kesimpulan

Anda kini memiliki program C# yang berfungsi penuh untuk **mengonversi Word ke markdown**, **mengekstrak gambar dari word**, **membuat folder resources**, dan menjamin **jalur relatif gambar markdown** yang bersih untuk setiap gambar. Kode ini berdiri sendiri, bekerja dengan versi Aspose.Words terbaru, dan dapat dimasukkan ke proyek .NET mana pun dengan usaha minimal.

Langkah selanjutnya? Coba masukkan markdown yang dihasilkan ke generator situs statis seperti Hugo atau Jekyll, atau bereksperimen dengan callback untuk menyematkan gambar langsung sebagai string Base64. Jika Anda menemukan kasus tepi—misalnya gambar SVG atau file sangat besar—kembali ke tabel “Kesalahan umum”; penyesuaian kecil biasanya menyelesaikannya.

Selamat coding, semoga markdown Anda selalu menunjuk ke folder yang tepat!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}