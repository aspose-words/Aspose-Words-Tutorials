---
category: general
date: 2026-05-29
description: Simpan docx sebagai markdown menggunakan Aspose.Words dan pelajari cara
  mengekstrak gambar dari docx dalam satu alur kerja. Kode langkah demi langkah dan
  tips.
draft: false
keywords:
- save docx as markdown
- extract images from docx
- convert word to markdown
- convert docx to markdown
- how to extract images
language: id
og_description: Simpan docx sebagai markdown dengan Aspose.Words. Pelajari cara mengekstrak
  gambar dari docx saat mengonversi Word ke markdown, kode lengkap disertakan.
og_title: Simpan docx sebagai markdown – Tutorial Lengkap dengan Ekstraksi Gambar
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  headline: Save docx as markdown – Complete Guide with Image Extraction
  type: TechArticle
- description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  name: Save docx as markdown – Complete Guide with Image Extraction
  steps:
  - name: – Load the source document
    text: First we need a `Document` object that points at the Word file we want to
      transform.
  - name: – Define a callback that extracts images from docx
    text: The magic lives in `IResourceSavingCallback`. Aspose.Words calls `ResourceSaving`
      for every external resource (images, fonts, etc.) it needs to write out. By
      providing our own implementation we gain total control over the file name, folder,
      and even the stream used.
  - name: – Wire the callback into Markdown save options
    text: Now we create a `MarkdownSaveOptions` instance and assign our custom saver.
  - name: – Save the document as markdown
    text: Finally, we ask Aspose.Words to write out the markdown file. The images
      are saved automatically by the callback we just hooked.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Conversion
title: Simpan docx sebagai markdown – Panduan Lengkap dengan Ekstraksi Gambar
url: /id/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save docx as markdown – Panduan Lengkap dengan Ekstraksi Gambar

Pernah bertanya-tanya bagaimana cara **save docx as markdown** tanpa kehilangan gambar yang tersembunyi di dalam file Word Anda? Anda tidak sendirian. Banyak pengembang mengalami kebuntuan ketika mencoba mengubah dokumen rich‑text menjadi markdown bersih dan berakhir dengan tautan gambar yang rusak.  

Dalam tutorial ini kami akan membahas solusi praktis yang tidak hanya **convert docx to markdown** tetapi juga **extract images from docx** secara otomatis. Pada akhir tutorial Anda akan memiliki cuplikan C# yang siap dijalankan, beberapa tips praktik terbaik, dan gambaran jelas tentang apa yang akan terjadi saat Anda menjalankan kode.

## Apa yang Akan Anda Pelajari

- Siapkan Aspose.Words untuk .NET untuk menangani konversi Word‑to‑markdown.  
- Implementasikan `IResourceSavingCallback` khusus yang menyimpan setiap gambar ter-embed ke folder pilihan Anda.  
- Pahami mengapa callback penting dan bagaimana ia menjaga referensi gambar tetap utuh dalam markdown yang dihasilkan.  
- Lihat contoh lengkap yang dapat dijalankan dan output markdown persis yang akan Anda dapatkan.  

**Prerequisites** – Anda memerlukan .NET 6 (atau versi .NET terbaru apa pun), Visual Studio 2022 (atau VS Code), dan lisensi Aspose.Words untuk .NET yang aktif (versi percobaan gratis dapat digunakan untuk pengujian). Tidak ada pustaka pihak ketiga lain yang diperlukan.

---

## Cara menyimpan docx sebagai markdown menggunakan Aspose.Words

Berikut adalah alur tingkat tinggi yang akan kami ikuti:

1. Muat file sumber `.docx` yang berisi gambar.  
2. Buat kelas callback yang menentukan ke mana setiap gambar yang diekstrak harus disimpan.  
3. Sambungkan callback ke `MarkdownSaveOptions`.  
4. Simpan dokumen – markdown ditulis ke disk, gambar disimpan di folder yang Anda tentukan.

Setiap langkah dijelaskan secara detail, dan kode ditampilkan tepat setelah penjelasan.

### Langkah 1 – Muat dokumen sumber

Pertama kami memerlukan objek `Document` yang menunjuk ke file Word yang ingin kami ubah.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source .docx that contains images.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why this matters:** Aspose.Words mem-parsing paket DOCX, membangun model objek internal, dan membuat setiap paragraf, tabel, serta gambar dapat diakses. Jika file tidak dapat dimuat, sisa pipeline tidak akan berjalan.

### Langkah 2 – Definisikan callback yang mengekstrak gambar dari docx

Keajaiban berada di `IResourceSavingCallback`. Aspose.Words memanggil `ResourceSaving` untuk setiap sumber daya eksternal (gambar, font, dll.) yang perlu ditulis. Dengan menyediakan implementasi kami sendiri, kami mendapatkan kontrol penuh atas nama file, folder, dan bahkan aliran (stream) yang digunakan.

```csharp
// Step 2: Define a callback that stores each extracted image in a sub‑folder
// and gives it a unique name.
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create (or reuse) a folder for the images.
        string folder = "YOUR_DIRECTORY/markdown_images";
        Directory.CreateDirectory(folder);

        // Build a new file name like "img_0.png", "img_1.jpg", etc.
        string newName = Path.Combine(folder,
            $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

        // Tell Aspose.Words where to write the image.
        args.ResourceFileName = newName;
        args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);

        // Allow the default saving process to continue.
        args.Cancel = false;
    }
}
```

> **Pro tip:** `args.Index` berbasis nol dan menjamin keunikan bahkan jika dua gambar memiliki nama file asli yang sama. Ini menghilangkan kesalahan “duplicate file name” yang menakutkan saat Anda menjalankan konversi berkali‑kali.

### Langkah 3 – Sambungkan callback ke opsi penyimpanan Markdown

Sekarang kami membuat instance `MarkdownSaveOptions` dan menetapkan saver khusus kami.

```csharp
// Step 3: Configure Markdown save options to use the custom resource saver.
MarkdownSaveOptions opts = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

> **Why this is essential:** Tanpa callback, Aspose.Words akan menyematkan gambar sebagai string base‑64 di dalam markdown atau menghilangkannya sepenuhnya, tergantung pada pengaturan default. Callback kami memaksa referensi berbasis file yang bersih yang bekerja dengan generator situs statis apa pun.

### Langkah 4 – Simpan dokumen sebagai markdown

Akhirnya, kami meminta Aspose.Words menulis file markdown. Gambar disimpan secara otomatis oleh callback yang baru saja kami hubungkan.

```csharp
// Step 4: Save the document as Markdown; images will be written to the folder above.
doc.Save("YOUR_DIRECTORY/output.md", opts);
```

Setelah kode selesai, Anda akan menemukan:

- `output.md` – representasi markdown dari file Word asli.  
- `markdown_images/` – folder yang berisi `img_0.png`, `img_1.jpg`, … untuk setiap gambar yang ada di DOCX.

#### Cuplikan markdown yang diharapkan

```markdown
# Sample Title

Here is some introductory text.

![Image 1](markdown_images/img_0.png)

More text after the picture.
```

Tautan gambar mengarah ke file yang kami simpan pada langkah 2, sehingga setiap penampil markdown akan menampilkan gambar dengan benar.

---

## Ekstrak gambar dari docx sambil mengonversi ke markdown

Jika tujuan utama Anda hanya **how to extract images** dari dokumen Word, Anda dapat menggunakan kembali callback yang sama tanpa menyimpan markdown. Cukup panggil `doc.Save("dummy.md", opts)` atau gunakan `doc.GetChildNodes(NodeType.Shape, true)` untuk menelusuri gambar. Callback akan dipicu untuk setiap gambar, memungkinkan Anda menyimpannya di mana saja.

```csharp
// Example: extract images only – we still need a save call to trigger the callback.
doc.Save("YOUR_DIRECTORY/placeholder.md", opts);
```

> **Note:** File markdown placeholder dapat dihapus setelah ekstraksi; callback telah menulis gambar ke disk.

---

## Konversi Word ke markdown dengan penanganan gambar khusus

Frasa **convert word to markdown** sering dicari bersama dengan “preserve formatting”. Aspose.Words melakukan pekerjaan yang solid dalam mempertahankan heading, daftar, tabel, dan blok kode. Satu-satunya hal yang perlu Anda perhatikan adalah skala gambar. Secara default markdown yang dihasilkan menggunakan dimensi gambar asli. Jika Anda membutuhkan thumbnail, ubah callback untuk mengubah ukuran gambar sebelum menulisnya (mis., menggunakan `System.Drawing` atau `ImageSharp`).

```csharp
// Inside ResourceSaving, you could resize before saving:
using (var original = Image.Load(args.Stream))
{
    var thumbnail = original.Clone(ctx => ctx.Resize(new ResizeOptions
    {
        Size = new Size(300, 0),
        Mode = ResizeMode.Max
    }));
    thumbnail.Save(newName);
}
```

*(Cuplikan di atas menggunakan ImageSharp – Anda perlu menambahkan paket NuGet jika menggunakan jalur tersebut.)*

---

## Kesalahan umum saat Anda mengonversi docx ke markdown

| Pitfall | Why it happens | How to avoid it |
|---------|----------------|-----------------|
| Gambar menjadi string **base64** | `ResourceSavingCallback` default tidak disetel | Selalu sediakan `IResourceSavingCallback` khusus |
| Tautan rusak setelah memindahkan file markdown | Path relatif mengarah ke folder yang tidak lagi ada | Simpan folder `markdown_images` di samping file `.md` atau sesuaikan path di `MarkdownSaveOptions.ImageFolder` |
| Nama gambar duplikat | Dua gambar memiliki nama asli yang sama | Gunakan `args.Index` (seperti yang kami lakukan) atau GUID dalam nama file |
| Kehabisan memori pada dokumen besar | Menyimpan gambar besar tanpa streaming | Gunakan `args.Stream = new FileStream(..., FileMode.Create, FileAccess.Write, FileShare.None, 4096, FileOptions.SequentialScan)` untuk streaming secara efisien |

---

## Cara mengekstrak gambar – skenario lanjutan

Kadang-kadang Anda membutuhkan gambar **tanpa** markdown, mungkin untuk dimasukkan ke model machine‑learning. Dalam kasus itu Anda dapat:

1. Set `opts.SaveFormat = SaveFormat.Png` (atau format gambar apa pun) untuk memaksa ekspor hanya gambar.  
2. Atau, gunakan kembali `MyResourceSaver` yang sama tetapi panggil `doc.Save("dummy.docx", SaveFormat.Docx)` hanya untuk memicu callback.

Kedua pendekatan memungkinkan Anda menggunakan kembali logika yang sama, menjaga kode tetap DRY (Don’t Repeat Yourself).

---

## Contoh lengkap yang dapat dijalankan

Berikut adalah seluruh program yang dapat Anda salin‑tempel ke aplikasi console. Ganti `YOUR_DIRECTORY` dengan path absolut atau relatif yang ada di mesin Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    // Step 2 – custom callback that saves each image.
    class MyResourceSaver : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string folder = "YOUR_DIRECTORY/markdown_images";
            Directory.CreateDirectory(folder);

            string newName = Path.Combine(folder,
                $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

            args.ResourceFileName = newName;
            args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);
            args.Cancel = false;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 – load the .docx.
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3 – set up save options with our callback.
            MarkdownSaveOptions opts = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceSaver()
            };

            // Step 4 – save as markdown; images will be extracted automatically.
            doc.Save("YOUR_DIRECTORY/output.md", opts);

            System.Console.WriteLine("Conversion complete! Check output.md and the markdown_images folder.");
        }
    }
}
```

**Apa yang akan Anda lihat setelah menjalankan:**  

- `output.md` berisi teks markdown dengan tautan gambar seperti `![Image](markdown_images/img_0.png)`.  
- Folder `markdown_images` terisi dengan satu file per gambar yang ter-embed.

---

## Kesimpulan

Anda kini memiliki resep menyeluruh, end‑to‑end untuk **save docx as markdown** sambil dengan bersih **extract images from docx**. Kuncinya adalah `IResourceSavingCallback` yang memberi Anda kontrol penuh atas lokasi dan cara setiap gambar disimpan.  

Dari sini Anda dapat:

- Sesuaikan callback untuk mengganti nama file menggunakan judul yang bermakna (mis., berdasarkan alt‑text).  
- Tambahkan post‑processing untuk mengonversi markdown ke HTML dengan static

## Apa yang Harus Anda Pelajari Selanjutnya?

- [Cara Menyematkan Gambar dalam Markdown Saat Mengonversi DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Simpan Gambar Word – Konversi Word ke Markdown dengan Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Cara Mengganti Nama Gambar Saat Mengonversi DOCX ke Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}