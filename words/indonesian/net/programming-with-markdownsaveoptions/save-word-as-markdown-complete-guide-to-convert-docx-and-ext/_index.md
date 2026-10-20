---
category: general
date: 2026-03-13
description: Simpan Word sebagai Markdown dan konversi DOCX ke Markdown sambil mengekstrak
  gambar. Pelajari cara mengekstrak gambar dari DOCX dengan Aspose.Words di C#.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- extract images from docx
- how to extract images
- extract embedded images word
language: id
og_description: Simpan Word sebagai Markdown di C#. Panduan ini menunjukkan cara mengonversi
  DOCX ke Markdown dan mengekstrak gambar, menyediakan solusi siap pakai.
og_title: Simpan Word sebagai Markdown – Konversi DOCX & Ekstrak Gambar
tags:
- Aspose.Words
- C#
- Markdown
title: Simpan Word sebagai Markdown – Panduan Lengkap untuk Mengonversi DOCX dan Mengekstrak
  Gambar
url: /id/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Word sebagai Markdown – Panduan Lengkap Mengonversi DOCX dan Mengekstrak Gambar

Pernah perlu **menyimpan Word sebagai markdown** tetapi tidak yakin bagaimana menjaga gambar tetap utuh? Anda tidak sendirian. Banyak pengembang menemui kendala ketika file DOCX mereka berisi grafik tersemat dan konverter sederhana menghasilkan sekumpulan tautan rusak.  

Dalam tutorial ini kita akan membahas solusi praktis yang **mengonversi DOCX ke markdown** **dan** mengekstrak setiap gambar ke folder yang Anda kontrol. Pada akhir tutorial Anda akan memiliki file `.md` yang bersih, direktori `markdown_resources` yang rapi, dan pemahaman yang kuat mengapa pendekatan callback adalah cara paling dapat diandalkan untuk menangani sumber daya.

> **Pro tip:** Pola yang sama bekerja untuk CSS, font, atau sumber daya eksternal apa pun yang mungkin dikeluarkan Aspose.Words selama operasi penyimpanan.

![Diagram alur konversi Save Word as Markdown](conversion-diagram.png "Diagram alur konversi")

## Apa yang Akan Anda Pelajari

- Cara **menyimpan Word sebagai markdown** menggunakan Aspose.Words for .NET.  
- Langkah‑langkah tepat untuk **mengonversi docx ke markdown** sambil mempertahankan gambar.  
- Implementasi `IResourceSavingCallback` yang dapat digunakan kembali untuk **mengekstrak gambar dari docx**.  
- Kesulitan umum (misalnya, nama file duplikat, folder yang hilang) dan cara menghindarinya.  
- Seperti apa markdown yang dihasilkan dan ke mana gambar‑gambar tersebut disimpan.

Anda memerlukan versi terbaru **Aspose.Words for .NET** (panduan ini diuji dengan 24.12) dan runtime .NET 6+. Tidak ada pustaka pihak ketiga lain yang diperlukan.

---

## Prasyarat

| Persyaratan | Mengapa penting |
|-------------|----------------|
| Aspose.Words for .NET (NuGet `Aspose.Words`) | Menyediakan kelas `Document` dan `MarkdownSaveOptions`. |
| .NET 6 atau lebih baru | Menjamin fitur bahasa seperti pernyataan `using` berfungsi tanpa tambahan ceremony. |
| File DOCX yang berisi gambar (misalnya `Images.docx`) | Sumber yang akan kita konversi dan dari mana kita akan mengekstrak gambar. |
| Izin menulis ke folder output | Callback menulis file gambar; tanpa izin Anda akan mendapatkan pengecualian. |

Jika Anda sudah memiliki semua ini, bagus—mari kita mulai.

---

## Langkah 1: Muat DOCX Sumber – Titik Awal untuk Simpan Word sebagai Markdown

Hal pertama yang kita lakukan adalah membuka dokumen Word. Aspose.Words membaca file ke dalam memori, mempertahankan semua struktur internal (paragraf, tabel, gambar, dll.).

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the DOCX that contains images.
Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");
```

> **Mengapa ini penting:** Memuat file di awal memungkinkan kita memeriksa isinya (misalnya, `sourceDoc.GetChildNodes(NodeType.Shape, true)`) jika pernah perlu men-debug gambar yang hilang.

---

## Langkah 2: Konfigurasikan Markdown Save Options dengan Callback Penyimpanan Gambar

Saat Aspose.Words menulis file markdown, ia mungkin perlu menyimpan sumber daya eksternal seperti gambar. Dengan melampirkan `ResourceSavingCallback`, kita mendapatkan kontrol penuh atas tempat file tersebut disimpan dan nama apa yang diberikan.

```csharp
// Prepare markdown options and tell Aspose.Words to use our callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // The callback fires for every image, CSS file, etc.
    ResourceSavingCallback = new ImageSavingCallback()
};
```

> **Cara mengekstrak gambar:** Callback menerima instance `ResourceSavingArgs` yang berisi aliran gambar, nama file asli, dan indeks. Kita dapat mengganti nama file, memindahkannya, atau bahkan melewatkan penyimpanan sama sekali.

---

## Langkah 3: Simpan Dokumen sebagai Markdown – Inti dari Simpan Word sebagai Markdown

Sekarang kita memanggil `Document.Save`. Perpustakaan akan memanggil callback kita untuk setiap gambar, menulis file gambar ke lokasi yang kita tentukan, dan akhirnya menghasilkan file markdown dengan tautan `![]()` yang tepat.

```csharp
// Execute the conversion. The markdown file will reference the extracted images.
sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);
```

Pada titik ini Anda harus melihat dua hal di `YOUR_DIRECTORY`:

1. `DocWithImages.md` – representasi markdown dari file Word asli.  
2. Folder `markdown_resources` – kumpulan file `img_0.png`, `img_1.jpg`, … dll.

---

## Langkah 4: Implementasikan Callback Penyimpanan Gambar – Cara Mengekstrak Gambar dari DOCX

Berikut adalah kelas callback lengkap. Ia membuat folder bila diperlukan, membangun nama file unik, menulis aliran gambar, lalu memberi tahu Aspose.Words untuk menggunakan nama file kita (dengan mengatur `args.FileName`) dan melewatkan penyimpanan defaultnya (`args.Stream = null`).

```csharp
public class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
        Directory.CreateDirectory(resourcesFolder);

        // 2️⃣ Build a unique name – img_0.png, img_1.jpg, etc.
        string imageFileName = Path.Combine(
            resourcesFolder,
            $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Tell the markdown writer to reference the new name.
        args.FileName = Path.GetFileName(imageFileName);
        args.Stream = null; // Prevent default saving – we already handled it.
    }
}
```

### Mengapa Ini Berhasil

- **Nama file deterministik** – Menggunakan `args.ImageIndex` menjamin keunikan bahkan jika DOCX asli memiliki nama duplikat.  
- **Isolasi folder** – Semua aset yang diekstrak berada di bawah `markdown_resources`, menjaga proyek Anda tetap rapi.  
- **Kinerja** – Kami menyalin aliran secara langsung; tidak ada buffering tambahan atau pemrosesan gambar, sehingga konversi tetap cepat.

---

## Langkah 5: Verifikasi Output – Seperti Apa Markdownnya

Buka `DocWithImages.md` di editor apa pun. Anda harus melihat sesuatu seperti:

```markdown
# Sample Document

Here is an illustration:

![](markdown_resources/img_0.png)

Another picture appears below:

![](markdown_resources/img_1.jpg)
```

Jika Anda membuka file markdown di penampil yang menghormati jalur relatif (pratinjau VS Code, GitHub, dll.), gambar akan ditampilkan dengan benar.

### Pemeriksaan cepat

```bash
# On Linux/macOS
cat YOUR_DIRECTORY/DocWithImages.md | grep -E '\!\[.*\]\(markdown_resources/img_.*\)'
```

Anda harus melihat satu baris per gambar; jumlahnya harus cocok dengan jumlah gambar yang semula tersemat di `Images.docx`.

---

## Pertanyaan Umum & Kasus Pojok

### Bagaimana jika DOCX berisi grafik SVG atau EMF?

Aspose.Words mengonversi sebagian besar format vektor ke PNG secara otomatis. Callback tetap akan menerima aliran, dan ekstensi file akan menjadi `.png`. Tidak diperlukan kode tambahan.

### Bagaimana cara mengubah nama folder output?

Cukup ubah variabel `resourcesFolder` di dalam `ImageSavingCallback`. Ingat untuk tetap mempertahankan referensi relatif yang sama (`args.FileName = Path.GetFileName(imageFileName)`) agar tautan markdown tetap benar.

### Bisakah saya melewatkan penyimpanan gambar tertentu (misalnya, yang sangat besar)?

Ya. Periksa `args.Stream.Length` di dalam callback. Jika melebihi ambang batas, Anda dapat mengganti namanya menjadi placeholder atau mengatur `args.Cancel = true` untuk mengabaikannya sepenuhnya.

```csharp
if (args.Stream.Length > 5 * 1024 * 1024) // >5 MB
{
    args.Cancel = true; // Image will be omitted from markdown.
    return;
}
```

### Apakah pendekatan ini bekerja untuk tipe sumber daya lain seperti CSS?

Tentu saja. Callback yang sama dipicu untuk setiap sumber daya eksternal. Anda dapat memeriksa `args.ContentType` untuk memperlakukan CSS, font, atau video secara berbeda.

---

## Contoh Lengkap yang Siap Pakai – Salin‑Tempel

Berikut adalah program mandiri yang dapat Anda letakkan di aplikasi konsol. Sesuaikan placeholder `YOUR_DIRECTORY` ke jalur absolut atau relatif di mesin Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // ① Load the source DOCX that contains images.
            Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");

            // ② Configure markdown options with our callback.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // ③ Save as markdown – images will be stored by the callback.
            sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);

            // ④ Inform the user.
            System.Console.WriteLine("Conversion complete! Check the markdown file and the markdown_resources folder.");
        }
    }

    // ⑤ Callback that extracts each image to a custom folder.
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
            Directory.CreateDirectory(resourcesFolder);

            string imageFileName = Path.Combine(
                resourcesFolder,
                $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

            using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
            {
                args.Stream.CopyTo(fileStream);
            }

            args.FileName = Path.GetFileName(imageFileName);
            args.Stream = null; // Skip default saving.
        }
    }
}
```

Jalankan program, buka markdown yang dihasilkan, dan Anda akan melihat semua gambar ditampilkan persis di tempat mereka muncul di file Word asli.

---

## Kesimpulan

Kami baru saja membahas **cara menyimpan Word sebagai markdown** sambil **mengekstrak gambar dari docx** menggunakan pola callback yang bersih. Inti utama adalah bahwa `IResourceSavingCallback` memberi Anda kontrol total atas setiap file eksternal, menjadikan konversi dapat diandalkan untuk pipeline produksi apa pun.

Dalam satu contoh yang dapat disalin‑tempel, kami:

1. Memuat DOCX yang berisi gambar.  
2. Mengonfigurasi `MarkdownSaveOptions` dengan `ImageSavingCallback` khusus.  
3. Menyimpan dokumen sebagai markdown, membiarkan callback menulis setiap gambar ke `markdown_resources`.  
4. Memverifikasi output dan membahas cara menyesuaikan proses untuk kasus pojok.

Dari sini Anda dapat:

- **Mengonversi docx ke markdown** secara massal dengan mengulang pada direktori.  
- **Mengganti nama gambar** berdasarkan caption asli untuk SEO yang lebih baik.  
- **Mengintegrasikan dengan generator situs statis** (misalnya, Hugo, Jekyll) dengan memindahkan folder markdown ke dalam pohon konten Anda.  
- **Memperluas callback** untuk juga mengekstrak font atau CSS yang tersemat jika Anda pernah membutuhkan ekspor HTML yang sepenuhnya mandiri.

Silakan bereksperimen—mungkin ganti skema penamaan gambar dengan GUID untuk keunikan absolut, atau tambahkan baris log untuk melacak setiap sumber daya yang disimpan. Langit adalah batasnya setelah Anda menguasai pipeline penyimpanan.

Selamat coding, semoga markdown Anda selalu menampilkan gambar yang tepat!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}