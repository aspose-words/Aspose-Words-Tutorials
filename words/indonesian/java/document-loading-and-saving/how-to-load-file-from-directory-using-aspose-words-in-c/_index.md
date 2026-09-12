---
category: general
date: 2026-09-11
description: Muat file dari direktori dengan Aspose.Words menggunakan opsi muat default
  dan pelajari cara mengatur enkoding dokumen atau menyesuaikan opsi muat di C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load file from directory
- default load options
- set document encoding
- set load options
language: id
lastmod: 2026-09-11
og_description: Muat file dari direktori dengan Aspose.Words menggunakan opsi muat
  default, atur enkoding dokumen, dan sesuaikan opsi muat untuk dokumen Word apa pun.
og_image_alt: Diagram illustrating load file from directory process with Aspose.Words
og_title: Muat file dari direktori dengan Aspose.Words – panduan lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Load file from directory with Aspose.Words using default load options
    and learn how to set document encoding or customize load options in C#.
  headline: How to load file from directory using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document processing
title: Cara memuat file dari direktori menggunakan Aspose.Words di C#
url: /id/java/document-loading-and-saving/how-to-load-file-from-directory-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memuat file dari direktori menggunakan Aspose.Words di C#

Jika Anda perlu **memuat file dari direktori** ke dalam alur kerja pemrosesan Word, Aspose.Words membuatnya sederhana. Panduan ini menunjukkan cara menggunakan **default load options**, **set document encoding**, dan **set load options** untuk menyesuaikan skenario spesifik Anda.

Pemuat dokumen sering membuat pengembang kebingungan ketika file sumber berada di folder khusus atau menggunakan enkoding non‑UTF‑8. Pada akhir tutorial ini Anda akan dapat memuat file `.docx` apa pun dari direktori mana pun, mengontrol enkodingnya, dan menyesuaikan perilaku pemuatan tanpa menulis kode tambahan.

## Apa yang akan Anda capai

- Muat dokumen Word dari direktori sembarang menggunakan satu baris kode.  
- Pahami apa yang disediakan oleh **default load options** dan kapan Anda perlu mengubahnya.  
- Terapkan **set document encoding** untuk menginterpretasikan set karakter lama seperti Big5 dengan benar.  
- Sesuaikan **set load options** untuk mengoptimalkan penggunaan memori, penanganan kata sandi, dan lainnya.  

### Prasyarat

- .NET 6.0 atau lebih baru (contoh ini menargetkan .NET 6, tetapi versi .NET terbaru mana pun dapat digunakan).  
- Aspose.Words untuk .NET 23.9 atau lebih baru – tambahkan paket NuGet `Aspose.Words`.  
- Pemahaman dasar tentang C# dan Visual Studio atau IDE pilihan Anda.

---

## Cara memuat file dari direktori dengan Aspose.Words

Inti operasi adalah konstruktor `Document` tunggal yang menerima jalur file dan instance `LoadOptions` opsional. Ketika Anda mengabaikan `LoadOptions`, Aspose.Words secara otomatis menerapkan **default load options**, yang cukup untuk kebanyakan dokumen modern.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1: Define the absolute path to the .docx file you want to load.
        string filePath = @"C:\MyDocuments\big5.docx";

        // Step 2: Load the document using the default load options.
        Document doc = new Document(filePath, new LoadOptions());

        // Verify that the document loaded by outputting the page count.
        Console.WriteLine($"Document loaded. Page count: {doc.PageCount}");
    }
}
```

**Mengapa ini berhasil:**  
- Konstruktor `Document` membaca file yang terletak di `filePath`.  
- Menyertakan `new LoadOptions()` memberi tahu Aspose.Words untuk menggunakan **default load options**, yang secara otomatis mendeteksi format file, memilih enkoding yang sesuai, dan menerapkan pemeriksaan keamanan standar.  

Menjalankan program mencetak jumlah halaman, mengonfirmasi bahwa operasi **load file from directory** berhasil.

---

## Menggunakan default load options

Meskipun Anda dapat melewatkan argumen `LoadOptions` sepenuhnya, membuat objek `LoadOptions` secara eksplisit memperjelas maksud dan mempersiapkan Anda untuk penyesuaian di kemudian hari.

```csharp
// Create a LoadOptions instance with the default configuration.
LoadOptions loadOptions = new LoadOptions();

// Load the document with those options.
Document doc = new Document(@"C:\MyDocuments\sample.docx", loadOptions);
```

**Poin penting tentang default load options**

| Feature | Default behavior |
|---------|------------------|
| **Format detection** | Mendeteksi secara otomatis DOC, DOCX, ODT, RTF, HTML, dan banyak format lainnya. |
| **Encoding** | Mendeteksi UTF‑8, UTF‑16, dan enkoding lama umum; kembali ke UTF‑8 bila tidak terdeteksi. |
| **Password handling** | Melempar `IncorrectPasswordException` jika file dilindungi kata sandi. |
| **Memory usage** | Muat seluruh dokumen ke memori, yang optimal untuk file di bawah 100 MB. |

Jika dokumen Anda dienkoding dengan charset lama (misalnya, Big5) dan deteksi otomatis gagal, Anda harus **set document encoding** secara manual.

## Menetapkan enkoding dokumen

Ketika sebuah file berisi font atau teks yang dienkoding dengan halaman kode lama, Anda dapat memberi tahu Aspose.Words enkoding mana yang harus digunakan melalui properti `LoadOptions.Encoding`. Ini adalah cara umum untuk **set document encoding** bagi file yang tidak dapat dideteksi oleh detektor default.

```csharp
using System.Text;

// Step 1: Create LoadOptions and specify the encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Big5 is code page 950.
    Encoding = Encoding.GetEncoding(950)
};

// Step 2: Load the document from the target directory.
Document doc = new Document(@"C:\MyDocuments\big5.docx", loadOptions);

// Step 3: Verify that the special characters are preserved.
Console.WriteLine($"First paragraph text: {doc.FirstSection.Body.Paragraphs[0].GetText()}");
```

**Mengapa Anda memerlukannya:**  
- Tanpa secara eksplisit mengatur `Encoding`, Aspose.Words mungkin menginterpretasikan byte sebagai UTF‑8, menghasilkan karakter yang rusak.  
- Dengan menyediakan halaman kode yang tepat, perpustakaan membaca teks persis seperti yang dimaksud penulis.  

**Tip:** Gunakan `Encoding.GetEncoding("big5")` atau kode halaman numerik (`950`) untuk dokumen Chinese Traditional (Big5).

## Menyesuaikan load options (set load options)

Selain enkoding, `LoadOptions` menyediakan banyak properti yang memungkinkan Anda **set load options** untuk skenario lanjutan:

```csharp
// Create a LoadOptions object with several custom settings.
LoadOptions loadOptions = new LoadOptions
{
    // Force the document to be treated as a DOCX file, even if the extension is wrong.
    LoadFormat = LoadFormat.Docx,

    // Limit memory usage for very large files (e.g., 200 MB+).
    LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory,

    // Provide a password if the file is encrypted.
    Password = "MySecretPassword"
};

// Load the document using the customized options.
Document doc = new Document(@"C:\MyDocuments\protected.docx", loadOptions);
```

**Penjelasan properti yang dipilih**

| Property | Purpose |
|----------|---------|
| `LoadFormat` | Memaksa format tertentu, melewati deteksi otomatis. Berguna ketika ekstensi file menyesatkan. |
| `LoadOptionsMemoryUsage` | Memilih strategi penghematan memori (`LowMemory`) untuk dokumen besar. |
| `Password` | Menyediakan kata sandi untuk file terenkripsi, menghindari pengecualian. |
| `ValidateDocumentStructure` | Ketika `true`, loader memvalidasi struktur XML internal dan melempar pengecualian jika rusak. |

Anda dapat menggabungkan salah satu dari ini dengan **set document encoding** untuk menangani alur impor yang paling menuntut.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program mandiri yang mendemonstrasikan semua konsep dalam satu alur:

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;

class LoadFileDemo
{
    static void Main()
    {
        // ------------------------------------------------------------------
        // 1️⃣ Define the directory and file name.
        // ------------------------------------------------------------------
        string directory = @"C:\MyDocuments";
        string fileName   = "big5.docx";               // Change as needed.
        string fullPath   = System.IO.Path.Combine(directory, fileName);

        // ------------------------------------------------------------------
        // 2️⃣ Create LoadOptions with explicit encoding (Big5) and low‑memory mode.
        // ------------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            Encoding = Encoding.GetEncoding(950), // Big5 code page.
            LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory
        };

        // ------------------------------------------------------------------
        // 3️⃣ Load the document from the directory using the custom options.
        // ------------------------------------------------------------------
        Document doc = new Document(fullPath, loadOptions);

        // ------------------------------------------------------------------
        // 4️⃣ Verify the load succeeded.
        // ------------------------------------------------------------------
        Console.WriteLine($"Document loaded from \"{fullPath}\"");
        Console.WriteLine($"Page count: {doc.PageCount}");
        Console.WriteLine($"First paragraph: {doc.FirstSection.Body.Paragraphs[0].GetText().Trim()}");

        // ------------------------------------------------------------------
        // 5️⃣ (Optional) Save as PDF to confirm visual fidelity.
        // ------------------------------------------------------------------
        string pdfPath = System.IO.Path.ChangeExtension(fullPath, ".pdf");
        doc.Save(pdfPath);
        Console.WriteLine($"Saved PDF version to \"{pdfPath}\"");
    }
}
```

**Output konsol yang diharapkan**

```
Document loaded from "C:\MyDocuments\big5.docx"
Page count: 3
First paragraph: 這是一個測試文件
Saved PDF version to "C:\MyDocuments\big5.pdf"
```

Menjalankan program memperlihatkan cara **load file from directory**, **set document encoding**, dan **set load options** dalam satu alur kerja yang jelas.

## Kesalahan umum dan cara menghindarinya

| Symptom | Likely cause | Fix |
|---------|--------------|-----|
| Karakter Cina yang rusak | Enkoding tidak diatur atau halaman kode salah | **Set document encoding** ke `Encoding.GetEncoding(950)` untuk Big5. |
| `IncorrectPasswordException` meskipun file tidak dilindungi kata sandi | Loader salah mendeteksi file biner sebagai terenkripsi | Setel secara eksplisit `LoadFormat` ke tipe yang benar (mis., `LoadFormat.Docx`). |
| Out

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [memulihkan docx yang rusak dengan Aspose.Words – mengatur mode pemulihan dan load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Cara Memuat Dokumen RTF dengan Mengonfigurasi RTF Load Options di Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)
- [Menguasai Markdown Load Options dengan Aspose.Words untuk Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}