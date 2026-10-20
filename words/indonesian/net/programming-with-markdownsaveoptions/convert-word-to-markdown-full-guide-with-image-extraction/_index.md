---
category: general
date: 2026-03-14
description: Konversi Word ke Markdown dengan cepat sambil mengekstrak gambar dari
  docx menggunakan Aspose.Words. Contoh C# langkah demi langkah untuk pengembang.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- Aspose.Words C#
- markdown conversion tutorial
- docx image handling
language: id
og_description: Konversi Word ke Markdown dan ekstrak gambar dari docx dengan Aspose.Words.
  Ikuti panduan terperinci ini untuk konversi tanpa masalah.
og_title: Ubah Word ke Markdown – Tutorial C# Lengkap
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Ubah Word ke Markdown – Panduan Lengkap dengan Ekstraksi Gambar
url: /id/net/programming-with-markdownsaveoptions/convert-word-to-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konversi Word ke Markdown – Tutorial C# Lengkap

Pernahkah Anda perlu **mengonversi Word ke Markdown** tetapi tidak yakin bagaimana menjaga gambar tersemat tetap utuh? Anda tidak sendirian. Banyak pengembang mengalami kendala di mana teks berhasil dikonversi, namun gambar menghilang begitu saja. Kabar baiknya? Dengan beberapa baris C# dan pustaka Aspose.Words yang kuat, Anda dapat **mengonversi Word ke Markdown** *dan* **mengekstrak gambar dari docx** dalam satu operasi yang mulus.

Dalam tutorial ini kami akan membahas semua yang Anda perlukan: mulai dari menginstal paket NuGet, memuat file `.docx`, mengonfigurasi penyimpan markdown, hingga menghubungkan callback yang menempatkan setiap gambar ke folder khusus dan menulis ulang tautan gambar. Pada akhir tutorial Anda akan memiliki file Markdown siap pakai dan direktori `resources` yang rapi berisi setiap gambar dari dokumen Word asli.

## Apa yang Akan Anda Pelajari

- Cara menyiapkan Aspose.Words untuk .NET dalam proyek C#.
- Kode tepat yang diperlukan untuk **mengonversi Word ke Markdown** sambil mempertahankan gambar.
- Mengapa `ResourceSavingCallback` penting untuk **mengekstrak gambar dari docx**.
- Jebakan umum (mis., pemisah jalur, nama file duplikat) dan cara menghindarinya.
- Langkah verifikasi cepat untuk memastikan Markdown yang dihasilkan ditampilkan dengan benar.

### Prasyarat

| Persyaratan | Alasan |
|-------------|--------|
| .NET 6.0 atau lebih baru (atau .NET Framework 4.7+) | Aspose.Words mendukung keduanya; runtime yang lebih baru memberikan kinerja yang lebih baik. |
| Visual Studio 2022 (atau IDE C# apa pun) | Memudahkan debugging dan manajemen paket. |
| Koneksi internet untuk pemulihan NuGet | Pustaka diunduh dari feed resmi. |
| Contoh `input.docx` yang berisi teks **dan** gambar | Untuk melihat ekstraksi gambar secara langsung. |

Tidak diperlukan alat pihak ketiga tambahan—Aspose.Words menangani semuanya di balik layar.

---

## Langkah 1: Instal Aspose.Words via NuGet

Pertama, tambahkan paket Aspose.Words ke proyek Anda. Buka **Package Manager Console** dan jalankan:

```powershell
Install-Package Aspose.Words
```

Atau, gunakan UI: klik kanan proyek → *Manage NuGet Packages* → cari “Aspose.Words” → klik **Install**. Ini akan menambahkan DLL inti dan namespace `Saving` yang akan kita perlukan nanti.

> **Pro tip:** Tetapkan versi (mis., `22.12.0`) untuk menghindari perubahan yang merusak secara tak terduga ketika pustaka memperbarui secara otomatis.

---

## Langkah 2: Muat Dokumen Word Sumber

Setelah pustaka siap, kita dapat memuat file `.docx`. Gunakan jalur absolut atau relatif yang mengarah ke dokumen sumber Anda.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file. Replace the placeholder with your actual path.
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Mengapa ini penting:** `Document` mem-parsing seluruh paket Word, memberi kami akses ke paragraf, tabel, dan bagian gambar tersembunyi yang akan kami ekstrak nanti.

---

## Langkah 3: Buat Opsi Penyimpanan Markdown

Aspose.Words menyediakan kelas `MarkdownSaveOptions` yang memungkinkan kami menyesuaikan perilaku konversi. Pada dasarnya kami membuat instance-nya; nanti kami akan menambahkan callback.

```csharp
// Instantiate the options object.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

Anda dapat menyesuaikan properti seperti `ExportImagesAsBase64` (atur ke `false` karena kami menginginkan file gambar terpisah) atau `ExportHeadersFooters` jika Anda memerlukan bagian tersebut dalam Markdown.

---

## Langkah 4: Konfigurasikan ResourceSavingCallback – Ekstrak Gambar dari DOCX

Ini adalah inti dari tutorial. `ResourceSavingCallback` dipicu untuk **setiap sumber daya** (gambar, font, dll.) yang ingin ditulis oleh penyimpan. Dengan menyediakan handler kami sendiri, kami memutuskan ke mana gambar disimpan dan bagaimana file Markdown merujuknya.

```csharp
mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // 1️⃣ Define the folder where we’ll dump extracted pictures.
        string imageFolder = @"YOUR_DIRECTORY\resources\";

        // 2️⃣ Ensure the folder exists – create it on the fly.
        Directory.CreateDirectory(imageFolder);

        // 3️⃣ Preserve the original filename (e.g., Image1.png).
        string imageFileName = Path.GetFileName(args.FileName);
        string targetPath   = Path.Combine(imageFolder, imageFileName);

        // 4️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(targetPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 5️⃣ Tell the Markdown generator to use a relative path.
        //    This is the step that **extract images from docx** correctly.
        args.ResourceFileName = $"resources/{imageFileName}";
    });
```

### Apa yang Dilakukan Ini

1. **Membuat** sub‑folder `resources` jika belum ada.  
2. **Menyalin** setiap aliran gambar yang masuk ke folder tersebut, mempertahankan nama file asli untuk menghindari kebingungan.  
3. **Memperbarui** tautan Markdown (`![alt](resources/Image1.png)`) sehingga pembaca dapat melihat gambar ketika file ditampilkan.

> **Kasus khusus:** Jika dua gambar memiliki nama yang sama, gambar yang terakhir akan menimpa yang sebelumnya. Untuk menghindarinya, Anda dapat menambahkan GUID di depan atau menggunakan `Path.GetUniqueFileName` (pembantu khusus) sebelum menyimpan.

---

## Langkah 5: Simpan Dokumen sebagai Markdown

Dengan callback terhubung, langkah terakhir adalah satu baris kode yang menulis file Markdown.

```csharp
// Choose the output path for the Markdown file.
string markdownPath = @"YOUR_DIRECTORY\output.md";

doc.Save(markdownPath, mdOptions);
```

Setelah pemanggilan ini selesai, Anda akan memiliki:

- `output.md` berisi teks Markdown dan referensi gambar seperti `![Image1](resources/Image1.png)`.  
- Folder `resources` berisi semua gambar yang diekstrak dari `.docx` asli.

---

## Langkah 6: Verifikasi Hasil

Buka `output.md` di penampil Markdown apa pun (VS Code, GitHub, Typora). Anda harus melihat heading, daftar, dan **gambar yang ditampilkan dengan benar** dari dokumen asli. Jika ada gambar yang hilang:

1. Periksa bahwa folder `resources` berisi file tersebut.  
2. Pastikan jalur relatif dalam Markdown (`resources/<filename>`) persis sama dengan nama folder (peka huruf pada Linux).  
3. Pastikan file gambar tidak rusak – buka langsung di penampil gambar.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang siap dijalankan. Ganti placeholder `YOUR_DIRECTORY` dengan jalur folder Anda yang sebenarnya.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class WordToMarkdown
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the source Word document.
        // -------------------------------------------------
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // -------------------------------------------------
        // 2️⃣ Prepare Markdown save options.
        // -------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Export images as separate files, not Base64.
            ExportImagesAsBase64 = false
        };

        // -------------------------------------------------
        // 3️⃣ Set up the callback to **extract images from docx**.
        // -------------------------------------------------
        mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
            (sender, args) =>
            {
                string imageFolder = @"YOUR_DIRECTORY\resources\";
                Directory.CreateDirectory(imageFolder);

                string imageFileName = Path.GetFileName(args.FileName);
                string targetPath = Path.Combine(imageFolder, imageFileName);

                using (FileStream fs = new FileStream(targetPath, FileMode.Create))
                {
                    args.Stream.CopyTo(fs);
                }

                // Update the reference used inside the Markdown file.
                args.ResourceFileName = $"resources/{imageFileName}";
            });

        // -------------------------------------------------
        // 4️⃣ Save as Markdown.
        // -------------------------------------------------
        string outputPath = @"YOUR_DIRECTORY\output.md";
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Check output.md and the resources folder.");
    }
}
```

**Output yang diharapkan:** Buka `output.md` dan Anda akan melihat sesuatu seperti:

```markdown
# Sample Title

Here is some introductory text.

![Image1](resources/Image1.png)

More paragraphs…

![Diagram](resources/Diagram.jpg)
```

Semua gambar muncul berdampingan dengan teks, persis seperti di file Word asli.

---

## Pertanyaan Umum & Hal-hal yang Perlu Diwaspadai

**Q: Bisakah saya mengubah format gambar saat ekstraksi?**  
A: Ya. Di dalam callback Anda dapat meng-encode ulang aliran (mis., ke PNG) sebelum menulisnya. Gunakan `System.Drawing` atau `ImageSharp` untuk memanipulasi `args.Stream`.

**Q: Bagaimana jika dokumen Word berisi gambar SVG atau EMF?**  
A: Aspose.Words mengonversi sebagian besar format vektor ke PNG raster secara default. Jika Anda memerlukan vektor asli, atur `mdOptions.ExportImageResolution` dan tangani aliran sesuai.

**Q: Apakah ini bekerja pada .NET Core di Linux?**  
A: Tentu saja. Pastikan jalur `resources` menggunakan garis miring (`/`) atau `Path.Combine` seperti yang ditunjukkan. Ingat bahwa sistem file Linux peka huruf, jadi jaga konsistensi nama folder.

**Q: Bagaimana cara menonaktifkan catatan kaki atau komentar?**  
A: Sesuaikan properti `mdOptions.ExportFootnotes` atau `mdOptions.ExportComments` sebelum menyimpan.

---

## Kesimpulan

Kami baru saja membahas **solusi lengkap end‑to‑end untuk mengonversi Word ke Markdown** sambil secara andal **mengekstrak gambar dari docx**. Dengan memanfaatkan `MarkdownSaveOptions` dari Aspose.Words dan `ResourceSavingCallback`, Anda mendapatkan kontrol detail atas konversi teks serta penanganan gambar. Kode ini mandiri, bekerja pada platform .NET apa pun, dan dapat dimasukkan ke dalam pipeline yang ada dengan gesekan minimal.

Siap untuk langkah selanjutnya? Pertimbangkan mengotomatisasi konversi massal, mengintegrasikan logika ini ke dalam API ASP.NET, atau memperluas callback untuk menghasilkan thumbnail bagi setiap gambar yang diekstrak. Langit adalah batasnya setelah Anda menguasai konversi inti.

---

![contoh mengonversi word ke markdown](convert-word-to-markdown.png "contoh mengonversi word ke markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}