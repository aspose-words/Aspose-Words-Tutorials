---
category: general
date: 2026-06-27
description: Konversi docx ke markdown dan simpan gambar dari docx menggunakan Aspose.Words.
  Pelajari cara mengekstrak gambar dari file Word dan mengekspor dokumen Word sebagai
  markdown.
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: id
og_description: Konversi docx ke markdown dan simpan gambar dari docx. Panduan ini
  menunjukkan cara mengekstrak gambar dari file Word dan mengekspor dokumen Word sebagai
  markdown.
og_title: Konversi docx ke markdown & simpan gambar dari docx
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: Konversi docx ke markdown & simpan gambar dari docx
url: /id/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengonversi docx ke markdown & menyimpan gambar dari docx

Pernah bertanya-tanya bagaimana cara **convert docx to markdown** tanpa kehilangan gambar yang tertanam dalam file Word Anda? Anda tidak sendirian—para pengembang sering membutuhkan versi Markdown yang bersih dari sebuah laporan sambil tetap mempertahankan setiap diagram, logo, atau tangkapan layar.

Dalam tutorial ini kami akan menelusuri contoh lengkap yang **mengonversi .docx ke Markdown**, **menyimpan gambar dari docx** ke folder pilihan Anda, dan menunjukkan cara **extract images from Word file** menggunakan pustaka Aspose.Words yang kuat. Pada akhir tutorial Anda juga akan tahu cara **export Word document as markdown** dalam satu baris kode.

## Apa yang Anda butuhkan

- .NET 6+ (atau .NET Framework 4.7.2+) terpasang di mesin Anda  
- Referensi NuGet ke `Aspose.Words` (versi percobaan gratis sudah cukup)  
- Contoh `input.docx` yang berisi setidaknya satu gambar  
- IDE pilihan Anda—Visual Studio, Rider, atau bahkan VS Code sudah cukup  

Tidak ada alat pihak ketiga tambahan, tidak ada akrobatik baris perintah yang rumit. Hanya kode C# langsung.

## Mengonversi docx ke markdown – Gambaran Umum

Ide dasarnya sederhana:

1. Muat dokumen Word sumber.  
2. Beri tahu Aspose.Words bagaimana Anda ingin sumber daya eksternal (seperti gambar) ditangani.  
3. Simpan dokumen sebagai Markdown, biarkan pustaka melakukan pekerjaan berat.

Di bawah ini adalah **program lengkap yang dapat dijalankan**. Silakan salin‑tempel ke proyek konsol baru dan tekan `Ctrl+F5`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### Cara kerja kode

- **Loading the document** (`new Document(inputPath)`) memberi kita representasi dalam memori dari file Word, lengkap dengan semua bagiannya—paragraf, tabel, dan **images**.  
- **`MarkdownSaveOptions`** adalah tempat keajaiban terjadi. Dengan melampirkan `ResourceSavingCallback`, kita mendapatkan kontrol penuh atas setiap sumber daya eksternal yang coba ditulis oleh Aspose.Words.  
- Di dalam callback kita **extract images from Word file** dengan memeriksa `args.ResourceType == ResourceType.Image`. Callback menerima byte gambar, ekstensi aslinya, dan properti `SavePath` yang kami tetapkan ke folder yang kami buat secara dinamis. Menggunakan `Guid.NewGuid()` menjamin nama file unik, sehingga Anda tidak akan secara tidak sengaja menimpa hasil sebelumnya.  
- Kami **skip CSS** (`ResourceType.CssStyleSheet`) karena Markdown biasa tidak memerlukan stylesheet. Ini membuat output tetap rapi.  
- Akhirnya, `doc.Save(outputPath, mdOptions)` menulis file Markdown, menggantikan konstruksi Word dengan padanan Markdown (heading menjadi `#`, tabel menjadi baris dipisahkan pipa, dll.).

## Menyimpan gambar dari docx – Strategi folder khusus

Mengapa repot dengan folder khusus? Bayangkan Anda menghasilkan dokumentasi untuk pipeline CI. Anda ingin file Markdown dan aset‑asetnya berada berdampingan dalam tata letak yang bersih dan dapat direproduksi.

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

Beberapa **pro tips**:

- **Keep the folder path relative** ke akar proyek Anda. Dengan begitu file Markdown dapat merujuk gambar dengan tautan relatif (`![Alt text](Images/abc123.png)`), yang berfungsi di GitHub, GitLab, atau generator situs statis apa pun.  
- **If you need deterministic names** (misalnya, gambar yang sama selalu mendapatkan nama file yang sama), ganti GUID dengan hash dari byte gambar: `MD5.Create().ComputeHash(args.Data)`. Itu hanya tweak kecil tetapi dapat berguna untuk caching.

## Extract images from Word file – Edge cases

1. **Multiple image formats** – Aspose.Words mendukung PNG, JPEG, GIF, BMP, dan bahkan SVG. Properti `args.Extension` sudah berisi ekstensi file yang tepat, jadi Anda tidak perlu menebak.  
2. **Very large images** – Jika dokumen sumber Anda berisi foto beresolusi tinggi, file yang dihasilkan bisa berukuran besar. Pertimbangkan menambahkan langkah kompresi setelah callback, menggunakan `System.Drawing` atau `ImageSharp`.  
3. **Hidden images** – Word dapat menyimpan gambar di header/footer atau bahkan di dalam text box. Callback melihat semuanya, sehingga Anda akan **extract every picture**, bukan hanya yang terlihat. Jika Anda hanya menginginkan gambar di badan dokumen, tambahkan filter pada `args.ImageIndex` atau inspeksi `args.ImageType`.

## Export Word document as markdown – Memverifikasi hasil

Setelah menjalankan program, buka `output.md` di penampil Markdown apa pun. Anda seharusnya melihat sesuatu seperti:

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

Perhatikan bagaimana tautan gambar mengarah ke folder **Images** yang kami buat. Itu adalah tanda bahwa operasi **export Word document as markdown** berhasil.

### Quick sanity check

- Apakah file Markdown terbuka tanpa error di panel preview VS Code? ✅  
- Apakah semua gambar ditampilkan saat Anda melihat file di GitHub? ✅  
- Apakah direktori `Images` berisi satu file per gambar dari `.docx` asli? ✅  

Jika salah satu pemeriksaan tersebut gagal, periksa kembali logika `ResourceSavingCallback` dan pastikan placeholder `YOUR_DIRECTORY` mengarah ke lokasi yang dapat ditulisi.

## Common pitfalls and how to avoid them

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Images not appearing** | Callback never fired because `ResourceSavingCallback` wasn’t assigned. | Assign the callback **before** calling `doc.Save`. |
| **Empty Images folder** | `args.Cancel = true` was set for all resources inadvertently. | Only cancel CSS (`ResourceType.CssStyleSheet`), leave images untouched. |
| **File‑path too long on Windows** | Using deep nested folders plus GUIDs can exceed 260 characters. | Keep the folder shallow, or enable long‑path support in Windows 10+. |
| **Duplicate image names** | Using `DateTime.Now.Ticks` instead of GUID can collide on fast loops. | Stick with `Guid.NewGuid()` for uniqueness. |

## Wrap‑up

Kami baru saja **converted docx to markdown**, **saved images from docx**, dan mendemonstrasikan cara **extract images from Word file** sambil **exporting Word document as markdown** secara bersih dan dapat diulang. Seluruh proses bergantung pada `ResourceSavingCallback` milik Aspose.Words, yang memberi Anda kontrol granular atas setiap aset eksternal.

### What’s next?

- **Style the Markdown** – tambahkan blok front‑matter untuk Jekyll atau Hugo.  
- **Automate the pipeline** – sematkan kode ini dalam langkah Azure DevOps atau GitHub Action.  
- **Handle tables and footnotes** – jelajahi flag `MarkdownSaveOptions` lain seperti `ExportTableBorderStyles`.  

Silakan ubah struktur folder, tambahkan kompresi gambar, atau bahkan ganti format output ke HTML dengan menukar `MarkdownSaveOptions` dengan `HtmlSaveOptions`. Langit adalah batasnya ketika Anda memiliki dasar yang kuat untuk **convert docx to markdown**.

Selamat coding, dan semoga dokumentasi Anda selalu tetap indah **dan** dapat dibaca mesin!

## What Should You Learn Next?

Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}