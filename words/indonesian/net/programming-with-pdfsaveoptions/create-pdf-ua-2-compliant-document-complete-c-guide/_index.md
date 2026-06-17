---
category: general
date: 2026-06-02
description: Buat dokumen yang mematuhi PDF/UA‑2 dengan Aspose.Words di C#. Tutorial
  langkah demi langkah yang mencakup kepatuhan PDF/UA‑2, PdfSaveOptions, dan aksesibilitas.
draft: false
keywords:
- create pdf/ua-2 compliant document
- Aspose.Words PDF/UA
- C# document conversion
- PDF accessibility
- PdfSaveOptions
language: id
og_description: Pelajari cara membuat dokumen yang mematuhi PDF/UA‑2 menggunakan Aspose.Words
  untuk .NET. Kode lengkap, tips kepatuhan, dan penjelasan aksesibilitas PDF.
og_title: Buat dokumen yang mematuhi pdf/ua-2 – Panduan Lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
    tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
  headline: Create pdf/ua-2 compliant document – Complete C# Guide
  type: TechArticle
- description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
    tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
  name: Create pdf/ua-2 compliant document – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Core, .NET Framework 4.7+,
      and .NET 5+). - A licensed copy of **Aspose.Words for .NET** (the free trial
      works for testing). - Basic familiarity with C# and Visual Studio (or your favourite
      IDE).'
  - name: Why These Settings Matter
    text: '- **Compliance = PdfUa2** – This flag adds the *PDF/UA* metadata and logical
      structure tree. - **EmbedFullFonts** – PDF/UA requires that all glyphs used
      in the document are embedded, otherwise a screen reader might miss characters.
      - **ExportDocumentStructure** – Tags the PDF so assistive technologi'
  - name: Quick Validation with the PDF/UA Validator
    text: 1. Download the free **PDF/UA‑2 validator** from the PDF Association (search
      “PDF/UA validator”). 2. Drag `Doc_UA.pdf` onto the validator window. 3. The
      tool will report “No errors” if the document meets the standard.
  - name: Custom Fonts
    text: If your source uses a font that isn’t installed on the server, enable `FontEmbeddingMode
      = FontEmbeddingMode.Always` to force embedding.
  - name: Complex Tables
    text: PDF/UA‑2 requires that tables have proper structure. Ensure every table
      in the Word file has header rows defined (`Table Tools → Layout → Repeat Header
      Rows`). Aspose.Words respects this setting automatically.
  - name: Images Without Alt Text
    text: 'Screen readers rely on alternative text. If an image lacks alt text, Aspose.Words
      will insert an empty description, which may cause a compliance warning. Add
      alt text in Word (`Picture Tools → Alt Text`) or programmatically:'
  type: HowTo
tags:
- PDF
- C#
- Aspose.Words
- Accessibility
title: Buat dokumen yang mematuhi pdf/ua-2 – Panduan Lengkap C#
url: /id/net/programming-with-pdfsaveoptions/create-pdf-ua-2-compliant-document-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen yang mematuhi pdf/ua-2 – Panduan Lengkap C#

Perlu **membuat dokumen yang mematuhi pdf/ua-2** tetapi tidak yakin harus mulai dari mana? Dalam tutorial ini kami akan memandu Anda cara membuat dokumen yang mematuhi pdf/ua-2 dengan Aspose.Words untuk .NET, menjamin aksesibilitas PDF dan kepatuhan penuh PDF/UA‑2.  

Jika Anda pernah berjuang dengan persyaratan aksesibilitas untuk PDF, Anda akan menghargai kesederhanaan pendekatan yang akan kami bahas. Pada akhir tutorial, Anda akan memiliki potongan kode C# siap pakai, memahami mengapa setiap pengaturan penting, dan mengetahui cara memverifikasi bahwa output benar‑benar memenuhi standar PDF/UA‑2.

## Apa yang Akan Anda Pelajari

- Cara menyiapkan dukungan **Aspose.Words PDF/UA** dalam proyek C#.  
- Peran tepat **PdfSaveOptions** saat menargetkan PDF/UA‑2.  
- Tips menangani kasus tepi seperti font kustom dan tabel kompleks.  
- Cara cepat memvalidasi file yang dihasilkan dengan validator PDF/UA gratis.  

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini bekerja dengan .NET Core, .NET Framework 4.7+, dan .NET 5+).  
- Salinan berlisensi **Aspose.Words for .NET** (versi percobaan gratis cukup untuk pengujian).  
- Familiaritas dasar dengan C# dan Visual Studio (atau IDE favorit Anda).  

Jika Anda mencentang semua kotak tersebut, mari kita mulai—tanpa alat tambahan yang diperlukan.

![contoh dokumen yang mematuhi pdf/ua-2](images/pdf-ua2-example.png "contoh dokumen yang mematuhi pdf/ua-2")

## Langkah 1: Instal Aspose.Words dan Tambahkan Referensi  

Pertama-tama, Anda memerlukan pustaka Aspose.Words. Buka terminal di folder proyek Anda dan jalankan:

```bash
dotnet add package Aspose.Words
```

Atau, gunakan NuGet Package Manager di Visual Studio. Ini akan menambahkan kemampuan **Aspose.Words PDF/UA**, termasuk kelas `PdfSaveOptions` yang akan kami gunakan nanti.  

> **Pro tip:** Jika Anda berencana mengirimkan fitur pembuatan PDF ke klien, tambahkan file lisensi (`Aspose.Words.lic`) ke proyek Anda dan panggil `License license = new License(); license.SetLicense("Aspose.Words.lic");` di awal `Main()`—ini menghilangkan watermark evaluasi.

## Langkah 2: Muat Dokumen Sumber  

Tujuan kami adalah mengubah file Word (`.docx`) menjadi dokumen yang mematuhi PDF/UA‑2. Sumbernya dapat berupa dokumen Word apa saja, tetapi untuk audit aksesibilitas yang bersih, mulailah dengan file sederhana yang mencakup heading, teks alt untuk gambar, dan struktur tabel yang tepat.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class PdfUaGenerator
{
    static void Main()
    {
        // Load the source .docx file
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        
        // Proceed to configure PDF/UA‑2 options
        SaveAsPdfUa2(doc);
    }
}
```

Mengapa harus memuat dokumen terlebih dahulu? Aspose.Words mem-parsing file Word menjadi model objek, memungkinkan kami memeriksa atau memodifikasi konten sebelum konversi—berguna bila Anda perlu menyisipkan tag aksesibilitas nanti.

## Langkah 3: Konfigurasikan PdfSaveOptions untuk PDF/UA‑2  

Kelas **PdfSaveOptions** adalah tempat keajaiban terjadi. Menetapkan `Compliance = PdfCompliance.PdfUa2` memberi tahu Aspose.Words untuk menyematkan tag yang diperlukan, elemen struktur logis, dan menetapkan versi PDF yang tepat.

```csharp
static void SaveAsPdfUa2(Document doc)
{
    // Create a new PdfSaveOptions instance
    PdfSaveOptions pdfOptions = new PdfSaveOptions
    {
        // Enforce PDF/UA‑2 compliance
        Compliance = PdfCompliance.PdfUa2,

        // Optional but recommended: embed all fonts to avoid substitution issues
        EmbedFullFonts = true,

        // Ensure the document is tagged (required for PDF/UA)
        ExportDocumentStructure = true,

        // Preserve hyperlinks and bookmarks for better navigation
        ExportHyperlinks = true,
        ExportBookmarks = true
    };

    // Save the PDF/UA‑2 file
    doc.Save(@"YOUR_DIRECTORY\Doc_UA.pdf", pdfOptions);
}
```

### Mengapa Pengaturan Ini Penting  

- **Compliance = PdfUa2** – Flag ini menambahkan metadata *PDF/UA* dan pohon struktur logis.  
- **EmbedFullFonts** – PDF/UA mengharuskan semua glif yang digunakan dalam dokumen disematkan, jika tidak pembaca layar mungkin melewatkan karakter.  
- **ExportDocumentStructure** – Menandai PDF sehingga teknologi bantu dapat menginterpretasikan heading, paragraf, dan tabel dengan benar.  
- **ExportHyperlinks / ExportBookmarks** – Meningkatkan navigasi bagi pengguna yang mengandalkan pintasan keyboard atau pintasan pembaca layar.

## Langkah 4: Jalankan Kode dan Verifikasi Output  

Bangun dan jalankan proyek. Jika semuanya terhubung dengan benar, Anda akan menemukan `Doc_UA.pdf` di folder target. Buka file tersebut di Adobe Acrobat Reader dan periksa **File → Properties → Description** – Anda harus melihat *PDF/UA‑2* tercantum di bawah bidang “PDF/A”.

### Validasi Cepat dengan PDF/UA Validator  

1. Unduh validator **PDF/UA‑2** gratis dari PDF Association (cari “PDF/UA validator”).  
2. Seret `Doc_UA.pdf` ke jendela validator.  
3. Alat akan melaporkan “No errors” jika dokumen memenuhi standar.  

Jika Anda menemukan peringatan tentang tag bahasa yang hilang, tambahkan atribut bahasa ke dokumen Word (`Review → Language → Set Proofing Language`) sebelum konversi.

## Langkah 5: Tangani Kasus Tepi Umum  

### Font Kustom  

Jika sumber Anda menggunakan font yang tidak terpasang di server, aktifkan `FontEmbeddingMode = FontEmbeddingMode.Always` untuk memaksa penyematan.  

```csharp
pdfOptions.FontEmbeddingMode = FontEmbeddingMode.Always;
```

### Tabel Kompleks  

PDF/UA‑2 mengharuskan tabel memiliki struktur yang tepat. Pastikan setiap tabel dalam file Word memiliki baris header yang didefinisikan (`Table Tools → Layout → Repeat Header Rows`). Aspose.Words secara otomatis menghormati pengaturan ini.

### Gambar Tanpa Teks Alt  

Pembaca layar mengandalkan teks alternatif. Jika sebuah gambar tidak memiliki teks alt, Aspose.Words akan menyisipkan deskripsi kosong, yang dapat menyebabkan peringatan kepatuhan. Tambahkan teks alt di Word (`Picture Tools → Alt Text`) atau secara programatis:

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage && string.IsNullOrEmpty(shape.AlternativeText))
    {
        shape.AlternativeText = "Descriptive text for accessibility";
    }
}
```

## Langkah 6: Praktik Terbaik untuk Proyek PDF/UA‑2 Berkelanjutan  

- **Automate validation**: Integrasikan validator PDF/UA ke dalam pipeline CI Anda sehingga setiap PDF yang dihasilkan diperiksa sebelum dirilis.  
- **Keep libraries current**: Aspose.Words secara rutin merilis pembaruan yang meningkatkan dukungan PDF/UA—upgrade setidaknya sekali setahun.  
- **Document your workflow**: Simpan checklist (penyematan font, teks alt, header tabel) untuk memastikan anggota tim non‑teknis dapat mempertahankan kepatuhan.  

---

## Kesimpulan  

Anda kini tahu persis cara **membuat dokumen yang mematuhi pdf/ua-2** menggunakan C# dan Aspose.Words. Dengan mengonfigurasi `PdfSaveOptions` dengan flag yang tepat, menyematkan font, dan memastikan file Word sumber mengikuti praktik terbaik aksesibilitas, Anda dapat menghasilkan PDF yang lolos validasi resmi PDF/UA‑2 tanpa hambatan.  

Siap untuk tantangan berikutnya? Cobalah menambahkan fitur **aksesibilitas PDF** seperti urutan baca logis untuk tata letak multi‑kolom, atau jelajahi **konversi dokumen C#** ke format lain seperti EPUB sambil mempertahankan metadata aksesibilitas yang sama.  

Jika Anda mengalami kendala, tinggalkan komentar di bawah—selamat coding, dan nikmati membangun PDF inklusif!  

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat PDF Aksesibel – Panduan Langkah‑per‑Langkah untuk Kepatuhan PDF/UA](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-step-by-step-guide-for-pdf-ua-complian/)
- [Buat PDF Aksesibel di C# – Tutorial Aksesibilitas PDF](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-in-c-pdf-accessibility-tutorial/)
- [konversi word ke pdf di C# menggunakan Aspose.Words – Panduan](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}