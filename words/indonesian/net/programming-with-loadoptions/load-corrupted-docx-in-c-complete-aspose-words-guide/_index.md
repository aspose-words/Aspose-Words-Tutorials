---
category: general
date: 2026-03-17
description: Pelajari cara memuat file docx yang rusak di C# menggunakan Aspose.Words
  LoadOptions. Kode langkah demi langkah, mode pemulihan, dan tips untuk penanganan
  dokumen yang kuat.
draft: false
keywords:
- load corrupted docx
- Aspose.Words LoadOptions
- RecoveryMode Partial
- skip corrupted parts
- document styles count
language: id
og_description: Muat file docx yang rusak di C# dengan Aspose.Words. Tutorial ini
  menunjukkan cara menggunakan LoadOptions, memilih RecoveryMode, dan memverifikasi
  dokumen.
og_title: Muat DOCX Rusak di C# – Panduan Lengkap Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Muat DOCX Rusak di C# – Panduan Lengkap Aspose.Words
url: /id/net/programming-with-loadoptions/load-corrupted-docx-in-c-complete-aspose-words-guide/
---

X – Complete Aspose.Words Guide" translate: "# Memuat DOCX Rusak – Panduan Lengkap Aspose.Words". Keep "DOCX" and "Aspose.Words". Good.

Paragraphs translate.

Need to keep code block placeholders unchanged.

Proceed step by step.

Will produce final markdown.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Memuat DOCX Rusak – Panduan Lengkap Aspose.Words

Pernah mencoba **memuat docx yang rusak** dan melihat aplikasi Anda langsung crash? Itu memang menyebalkan—terutama ketika bagian lain dari file tersebut sempurna. Kabar baiknya? Aspose.Words memberi Anda kontrol yang sangat detail tentang cara menangani bagian yang rusak, sehingga Anda masih dapat mengekstrak apa yang masih dapat digunakan.

Dalam tutorial ini kita akan membahas solusi dunia nyata untuk memuat DOCX yang rusak di C#. Kami akan membahas kelas `LoadOptions`, menjelaskan nilai‑nilai `RecoveryMode` yang berbeda, dan menunjukkan cara memverifikasi bahwa dokumen terbuka dengan benar. Pada akhir tutorial Anda akan memiliki potongan kode siap‑jalankan yang menangani file rusak secara elegan—tidak ada lagi pengecualian yang tidak tertangani.

> **Apa yang Anda perlukan**  
> • .NET 6 atau lebih baru (kode ini juga bekerja pada .NET Framework 4.6+)  
> • Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)  
> • Sebuah DOCX yang Anda curigai rusak (kami akan menyebutnya *Corrupted.docx*)

Mari kita mulai.

---

## Memahami Aspose.Words LoadOptions

`LoadOptions` adalah gerbang yang memberi tahu Aspose.Words **bagaimana** cara menafsirkan sebuah file ketika Anda memanggil `new Document(path, options)`. Anggap saja ini seperti lembar instruksi yang Anda berikan kepada pustakawan—jika buku memiliki halaman yang sobek, Anda dapat memintanya hanya memberikan bab‑bab yang masih dapat dibaca.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Configures the loader to decide what to do with corrupted parts.
/// </summary>
LoadOptions loadOptions = new LoadOptions
{
    // RecoveryMode.Partial returns the readable sections and skips the rest.
    RecoveryMode = RecoveryMode.Partial   // Change to Full or SkipCorrupted as needed
};
```

### Mengapa RecoveryMode penting

- **Partial** – Mengembalikan apa saja yang dapat diparse, membuang bagian yang rusak. Ideal ketika Anda membutuhkan konten sekecil apapun.  
- **Full** – Mencoba merekonstruksi seluruh dokumen, yang dapat lebih lambat dan mungkin menghasilkan artefak.  
- **SkipCorrupted** – Mengabaikan dokumen yang rusak sepenuhnya dan melempar pengecualian. Gunakan hanya ketika Anda menginginkan kegagalan keras.

Memilih mode yang tepat mencegah aplikasi Anda meledak ketika pengguna mengunggah file yang rusak.

---

## Langkah 1: Memuat File DOCX yang Rusak

Setelah kita mengonfigurasi `LoadOptions`, langkah selanjutnya adalah **memuat docx yang rusak**. Kode di bawah ini menunjukkan contoh aplikasi konsol lengkap yang dapat dijalankan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Path to the possibly damaged document.
        string filePath = @"YOUR_DIRECTORY\Corrupted.docx";

        // Configure LoadOptions – see the previous section for details.
        LoadOptions options = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Partial // Try Partial first; switch if needed.
        };

        Document doc;
        try
        {
            // Attempt to load the document with the chosen recovery strategy.
            doc = new Document(filePath, options);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // Verify that something useful was loaded.
        VerifyDocument(doc);
    }

    /// <summary>
    /// Simple verification that the document contains at least one style.
    /// </summary>
    static void VerifyDocument(Document document)
    {
        // The Styles collection is always populated for a valid docx.
        int styleCount = document.Styles.Count;
        Console.WriteLine($"Loaded with {styleCount} style{(styleCount == 1 ? "" : "s")}.");
    }
}
```

**Output yang diharapkan (ketika file dapat dibaca sebagian):**

```
✅ Document loaded successfully.
Loaded with 37 styles.
```

Jika file tidak dapat dibaca sama sekali, Anda akan melihat pesan error dari blok `catch` sebagai gantinya.

---

## Langkah 2: Memilih RecoveryMode yang Tepat untuk Skenario Anda

Anda mungkin bertanya, *“Haruskah saya selalu menggunakan RecoveryMode.Partial?”* Tidak selalu. Berikut matriks keputusan singkat:

| Situasi | RecoveryMode yang Disarankan | Alasan |
|-----------|--------------------------|--------|
| Anda hanya membutuhkan teks apa pun (misalnya, pengindeksan pencarian) | **Partial** | Memberikan apa saja yang dapat diselamatkan dengan overhead minimal. |
| Anda membutuhkan dokumen yang tampak sedekat mungkin dengan aslinya (misalnya, pratinjau) | **Full** | Mencoba rekonstruksi sebaik mungkin, mempertahankan tata letak. |
| Kerusakan jarang terjadi dan Anda lebih suka kegagalan yang tegas | **SkipCorrupted** | Gagal cepat, memungkinkan Anda mencatat masalah dan meminta pengguna mengunggah file baru. |

Ubah mode dengan mengedit baris `RecoveryMode` pada inisialisasi `LoadOptions`.

---

## Langkah 3: Memverifikasi Dokumen yang Dimuat (Lebih dari Sekadar Gaya)

Menghitung gaya merupakan pemeriksaan sanity yang berguna, tetapi Anda mungkin menginginkan validasi yang lebih mendalam. Berikut beberapa pemeriksaan tambahan yang dapat Anda semprotkan setelah dokumen dimuat:

```csharp
static void VerifyDocument(Document document)
{
    // 1️⃣ Check that at least one section exists.
    if (document.Sections.Count == 0)
    {
        Console.WriteLine("⚠️ No sections were found – the document might be empty.");
        return;
    }

    // 2️⃣ Ensure the main body has paragraphs.
    var body = document.FirstSection.Body;
    if (body.Paragraphs.Count == 0)
    {
        Console.WriteLine("⚠️ No paragraphs detected – content could be missing.");
    }
    else
    {
        Console.WriteLine($"✅ Document contains {body.Paragraphs.Count} paragraph{(body.Paragraphs.Count == 1 ? "" : "s")}.");
    }

    // 3️⃣ Report the number of styles (as before).
    Console.WriteLine($"🖋️ Document loaded with {document.Styles.Count} style{(document.Styles.Count == 1 ? "" : "s")}.");
}
```

Pemeriksaan ekstra ini membantu Anda memutuskan apakah dokumen yang dipulihkan *cukup baik* untuk proses selanjutnya.

---

## Langkah 4: Menangani Kasus Tepi dan Jebakan Umum

### 1. Lisensi Aspose.Words Hilang

Jika Anda menjalankan contoh tanpa lisensi, Anda akan melihat watermark pada PDF output (jika Anda kemudian mengonversinya). Daftarkan lisensi sementara gratis selama pengembangan:

```csharp
License license = new License();
license.SetLicense("Aspose.Words.lic");
```

### 2. Masalah Jalur File

Jalur relatif dapat menjadi rumit ketika aplikasi Anda berjalan dari direktori kerja yang berbeda. Gunakan `Path.Combine` dengan `AppDomain.CurrentDomain.BaseDirectory` untuk membangun jalur absolut.

```csharp
string filePath = Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Corrupted.docx");
```

### 3. Dokumen Besar

Pemulihan parsial pada DOCX berukuran 200 MB masih dapat mengonsumsi memori yang signifikan. Pertimbangkan streaming file atau meningkatkan batas memori proses jika Anda menemui `OutOfMemoryException`.

### 4. Skenario Multi‑Threaded

`LoadOptions` tidak thread‑safe. Buat instance baru untuk setiap thread guna menghindari kondisi balapan.

---

## Langkah 5: Contoh Kerja Lengkap (Siap Salin‑Tempel)

Berikut adalah seluruh program yang dapat Anda masukkan ke dalam proyek Console App baru. Program ini mencakup semua potongan kode praktik terbaik dari bagian‑bagian sebelumnya.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class LoadCorruptedDocxDemo
{
    static void Main()
    {
        // ---------- 1. Optional: Apply a license ----------
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // ---------- 2. Build a safe file path ----------
        string filePath = Path.Combine(
            AppDomain.CurrentDomain.BaseDirectory,
            "Corrupted.docx");

        // ---------- 3. Configure LoadOptions ----------
        LoadOptions options = new LoadOptions
        {
            // Choose Partial, Full, or SkipCorrupted depending on your needs.
            RecoveryMode = RecoveryMode.Partial
        };

        // ---------- 4. Load the document ----------
        Document doc;
        try
        {
            doc = new Document(filePath, options);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load corrupted docx: {ex.Message}");
            return;
        }

        // ---------- 5. Verify the loaded content ----------
        VerifyDocument(doc);
    }

    static void VerifyDocument(Document document)
    {
        // Section sanity check
        if (document.Sections.Count == 0)
        {
            Console.WriteLine("⚠️ No sections detected – file might be empty.");
            return;
        }

        // Paragraph sanity check
        var body = document.FirstSection.Body;
        Console.WriteLine(body.Paragraphs.Count > 0
            ? $"✅ Document contains {body.Paragraphs.Count} paragraph{(body.Paragraphs.Count == 1 ? "" : "s")}."
            : "⚠️ No paragraphs found.");

        // Styles count (quick indicator)
        Console.WriteLine($"🖋️ Loaded with {document.Styles.Count} style{(document.Styles.Count == 1 ? "" : "s")}.");
    }
}
```

Jalankan program, arahkan `Corrupted.docx` ke file rusak yang nyata, dan saksikan konsol memberi tahu apa yang berhasil diselamatkan.

---

## Kesimpulan

Kami baru saja membahas semua yang Anda perlukan untuk **memuat docx yang rusak** di C# menggunakan Aspose.Words:

* Konfigurasikan `LoadOptions` dengan `RecoveryMode` yang sesuai.  
* Coba buka file di dalam blok `try/catch`.  
* Verifikasi hasil dengan memeriksa bagian, paragraf, dan jumlah gaya.  
* Tangani jebakan umum seperti lisensi, resolusi jalur, dan masalah memori.

Dengan pengetahuan ini Anda dapat mengubah error yang berpotensi fatal menjadi fallback yang elegan—baik Anda membangun layanan unggah dokumen, pipeline pengindeksan otomatis, atau penampil desktop sederhana.

**Langkah selanjutnya?** Coba konversi dokumen yang dipulihkan ke PDF (`doc.Save("output.pdf")`), atau ekstrak teks polos (`doc.GetText()`) untuk pengindeksan pencarian. Anda juga dapat menjelajahi `LoadOptions.Password` jika perlu membuka file terenkripsi bersamaan dengan file yang rusak.

Punya pertanyaan atau file rumit yang tidak mau bekerja? Tinggalkan komentar di bawah, dan kami akan membantu memecahkan masalah bersama. Selamat coding!  



![Diagram yang menunjukkan alur kerja memuat docx rusak](/images/load-corrupted-docx-workflow.png "diagram alur kerja memuat docx rusak")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}