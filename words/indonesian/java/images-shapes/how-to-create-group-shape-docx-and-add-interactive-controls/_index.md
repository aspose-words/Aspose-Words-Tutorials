---
category: general
date: 2026-09-05
description: Pelajari cara membuat grup shape docx, menyisipkan tombol perintah ActiveX,
  dan memuat Markdown ke dalam dokumen Word dengan contoh lengkap C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: id
lastmod: 2026-09-05
og_description: Buat grup shape docx, sisipkan tombol perintah ActiveX, dan muat Markdown
  ke dalam dokumen Word menggunakan C#. Ikuti tutorial langkah demi langkah ini.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Buat grup shape docx dan sematkan kontrol ActiveX – Panduan C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Cara membuat grup shape docx dan menambahkan kontrol interaktif di C#
url: /id/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat group shape docx dan menambahkan kontrol interaktif di C#

Jika Anda perlu **create group shape docx** file secara programatis, panduan ini menunjukkan secara tepat cara melakukannya. Anda juga akan melihat cara **insert ActiveX command button** kontrol dan **load Markdown into a Word document** tanpa kehilangan format underline. Pada akhir tutorial Anda akan memiliki `.docx` yang berfungsi penuh yang menggabungkan grafik vektor, elemen UI interaktif, dan konten berbasis markdown.

Tutorial ini mengasumsikan Anda memiliki lingkungan pengembangan C# dasar dan perpustakaan Aspose.Words untuk .NET terpasang. Tidak diperlukan alat eksternal—semua berjalan di dalam aplikasi konsol atau desktop .NET standar.

## Prasyarat

- .NET 6.0 SDK atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)
- Sertifikat X.509 yang valid (`.pfx`) jika Anda ingin menguji langkah penandatanganan
- File gambar (mis., `logo.png`) dan file markdown (`sample.md`) yang ditempatkan di folder yang diketahui

> **Pro tip:** Simpan semua file input dalam satu folder *resources* untuk mempermudah jalur relatif.

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek konsol baru dan tambahkan direktif `using` yang diperlukan. Blok ini juga menunjukkan cara merujuk kelas Aspose.Words yang akan Anda gunakan nanti.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

Pernyataan `using` memberi Anda akses langsung ke `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl`, dan tipe lainnya yang digunakan sepanjang tutorial.

## Langkah 2: **Create group shape docx** – tambahkan shape yang dikelompokkan dengan elemen anak

Sebuah *group shape* memungkinkan Anda memperlakukan beberapa objek gambar sebagai satu unit. Ini berguna untuk memindahkan atau mengubah ukuran grafik yang terkait secara bersamaan.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Why a group shape?**  
Pengelompokan menjaga persegi panjang dan elips tetap sejajar ketika pengguna menyeretnya di Word. Ini juga menyederhanakan operasi selanjutnya seperti menerapkan border umum atau memindahkan seluruh grafik secara programatis.

## Langkah 3: Sisipkan kontrol konten plain‑text (placeholder untuk input pengguna)

Kontrol konten memberikan pengguna akhir area terstruktur untuk mengetik teks. Teks placeholder menghilang begitu pengguna mulai mengetik.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

Properti `PlaceholderName` adalah apa yang ditampilkan Word dalam petunjuk berwarna abu‑abu muda. Pengguna dapat menggantinya dengan teks mereka sendiri, dan XML yang mendasarinya tetap terstruktur dengan baik.

## Langkah 4: **Insert ActiveX command button** – tambahkan UI interaktif ke dokumen

Kontrol ActiveX masih didukung dalam file Word modern dan dapat memicu makro atau otomatisasi eksternal. Di bawah ini kami menambahkan *command button* dan mengatur caption-nya.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**When to use an ActiveX button?**  
Jika Anda mendistribusikan dokumen dalam lingkungan korporat yang mengandalkan makro VBA, tombol ActiveX dapat meluncurkan makro atau aplikasi eksternal. Untuk interaktivitas berbasis HTML murni, pertimbangkan menggunakan *content controls* dengan *Office.js* sebagai gantinya.

## Langkah 5: Sisipkan gambar tersembunyi (mis., logo) untuk branding atau akses skrip nanti

Shape tersembunyi tidak ditampilkan dalam dokumen yang dicetak tetapi tetap ada di XML, memungkinkan Anda mengambilnya secara programatis nanti.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Langkah 6: **Load markdown into a Word document** sambil mempertahankan format underline

Aspose.Words dapat mengimpor Markdown secara langsung. Mengaktifkan `ImportUnderlineFormatting` memastikan bahwa underline markdown (`<u>` atau `__text__`) menjadi gaya underline Word alih-alih teks biasa.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Edge case:** Jika file markdown berisi tabel, mereka secara otomatis dikonversi menjadi tabel Word. Jika Anda memerlukan gaya tabel khusus, terapkan `DocumentBuilder` setelah penyisipan.

## Langkah 7: Tanda tangani dokumen dengan XAdES‑EPES (langkah keamanan opsional)

Tanda tangan digital menjamin integritas dokumen. Kode berikut menandatangani file **create group shape docx** menggunakan profil XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Security note:** Simpan kata sandi sertifikat di luar kontrol sumber. Gunakan variabel lingkungan atau vault yang aman dalam produksi.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua langkah menghasilkan satu program yang berdiri sendiri. Simpan file sebagai `Program.cs` dan jalankan dari baris perintah.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Menjalankan program menghasilkan `CompleteGroupShape.docx` yang berisi:

- Sebuah persegi panjang + elips yang dikelompokkan (inti **create group shape docx**)
- Kontrol konten plain‑text dengan teks placeholder
- Sebuah **insert ActiveX command button** berlabel “Click Me”
- Gambar logo tersembunyi
- Konten Markdown dengan underline yang dipertahankan
- Tanda tangan digital XAdES‑EPES (jika sertifikat disediakan)

## Pertanyaan umum dan pemecahan masalah

| Question | Answer |
|---|---|
| **Apakah tombol ActiveX akan berfungsi di Word macOS?** | Word di macOS tidak mendukung kontrol ActiveX. Tombol akan muncul sebagai gambar statis. Gunakan content controls dengan Office.js untuk interaktivitas lintas‑platform. |
| **Bagaimana jika file markdown berisi CSS khusus?** | Aspose.Words mengabaikan CSS; hanya sintaks markdown standar yang diproses. Konversi elemen yang bergaya CSS ke gaya Word secara manual setelah impor. |
| **Bisakah saya menambahkan lebih banyak shape ke grup yang sama nanti?** | Ya. Dapatkan `GroupShape` berdasarkan nama atau indeksnya, lalu panggil `AppendChild(newShape)`. Ingat untuk menyimpan kembali dokumen setelah modifikasi. |
| **Bagaimana cara mengubah algoritma tanda tangan?** | Setel `signature.SignatureAlgorithm` sebelum memanggil `Sign`. Defaultnya adalah SHA‑256, yang memenuhi sebagian besar persyaratan kepatuhan. |
| **Apakah gambar tersembunyi terlihat di UI Word?** | Tidak, tetapi dapat ditampilkan dengan mengaktifkan *Show hidden text* di opsi Word. Ini berguna untuk menyimpan metadata tanpa mengacaukan tata letak. |

## Langkah selanjutnya

Sekarang Anda dapat **create group shape docx**, **insert ActiveX command button**, dan **load markdown into a Word document**, Anda mungkin ingin mengeksplorasi:

- **Embedding VBA macros** yang merespon klik tombol ActiveX.
- **Applying custom styles** pada paragraf yang dihasilkan dari markdown.
- **Generating PDFs** dari dokumen yang sama menggunakan `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automating batch processing** dari beberapa file markdown menjadi satu laporan terkompilasi.

Ekstensi ini memungkinkan Anda membangun pipeline dokumen yang sepenuhnya otomatis yang menggabungkan grafik kaya, kontrol interaktif, dan penulisan berbasis markdown—semua dari C#.

---

*Selamat coding! Jika Anda menemukan tutorial ini

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun pada teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat shape persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Buat markdown dari Word – Panduan C# Lengkap](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}