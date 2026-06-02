---
category: general
date: 2026-06-02
description: Ganti teks dalam file docx menggunakan C#. Pelajari cara mengganti semua
  kemunculan kata, melakukan pencarian dan penggantian dalam dokumen Word, serta kuasai
  cara mengganti teks dengan C# secara efisien.
draft: false
keywords:
- replace text in docx
- replace all occurrences word
- find and replace word document
- how to replace text c#
language: id
og_description: Ganti teks dalam file docx menggunakan C#. Tutorial ini menunjukkan
  cara mengganti semua kemunculan kata dan melakukan pencarian serta penggantian dalam
  dokumen Word dengan contoh kode yang jelas.
og_title: Ganti teks dalam docx dengan C# – Panduan Pemrograman Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Replace text in docx using C#. Learn how to replace all occurrences
    word, perform find and replace word document, and master how to replace text c#
    efficiently.
  headline: Replace text in docx with C# – Full Step‑by‑Step Guide
  type: TechArticle
- description: Replace text in docx using C#. Learn how to replace all occurrences
    word, perform find and replace word document, and master how to replace text c#
    efficiently.
  name: Replace text in docx with C# – Full Step‑by‑Step Guide
  steps:
  - name: 1. Case‑Insensitive Replacement
    text: 'If you need to ignore case (e.g., replace “Foo”, “FOO”, and “foo” alike),
      tweak the regex options:'
  - name: 2. Replacing Whole Words Only
    text: 'Sometimes “foo” appears inside another word like “food”. To avoid accidental
      changes, anchor the pattern with word boundaries:'
  - name: 3. Using a Callback for Conditional Replacement
    text: Aspose lets you supply a delegate to decide on‑the‑fly whether to replace
      a match. This is handy for scenarios like “replace only if the word is in a
      table”.
  - name: 4. Handling Large Documents Efficiently
    text: For multi‑gigabyte files, consider processing the document in chunks (e.g.,
      per section) to keep memory usage low. Aspose provides `Section` collections
      you can iterate over and call `Replace` on each individually.
  - name: 5. Preserving Formatting
    text: 'The replacement text inherits the formatting of the first character of
      the match. If you need to enforce a specific style (e.g., bold), apply it after
      the replacement:'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words treats `.doc` and `.docx` uniformly. Just change the
      file extension in the load/save paths.
    question: Does this work with `.doc` files?
  - answer: You’ll need to unprotect the document first (`doc.Protect(ProtectionType.NoProtection,
      "password")`) or supply the password when loading.
    question: What if the document contains protected sections?
  - answer: Absolutely. Use `new LoadOptions { Password = "yourPassword" }` when constructing
      the `Document`.
    question: Can I replace text in a password‑protected file?
  - answer: 'The Open XML SDK can perform find/replace, but it lacks the high‑level
      `Range.Replace` convenience and requires more boilerplate. For production‑grade
      reliability, Aspose remains the recommended choice. --- ## Next Steps & Related
      Topics Now that you’ve mastered **replace text in docx**, you might w'
    question: Is there a free alternative to Aspose.Words?
  type: FAQPage
tags:
- C#
- Word Automation
- FindReplace
title: Ganti teks dalam docx dengan C# – Panduan Langkah-demi-Langkah Lengkap
url: /id/net/find-and-replace-text/replace-text-in-docx-with-c-full-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ganti teks dalam docx dengan C# – Panduan Langkah‑demi‑Langkah Lengkap

Pernah perlu mengganti teks dalam file docx tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian. Baik Anda sedang membersihkan sekumpulan kontrak atau secara otomatis membuat surat yang dipersonalisasi, mempelajari **replace text in docx** dengan C# dapat menghemat berjam‑jam penyuntingan manual.

Dalam panduan ini kami akan membahas solusi lengkap yang siap dijalankan yang menunjukkan cara mengganti semua kemunculan kata, melakukan pencarian dan penggantian kata yang kuat dalam dokumen Word, dan menjawab pertanyaan “how to replace text c#” yang terus mengganggu sekali dan untuk selamanya. Tanpa referensi yang samar—hanya kode yang solid, penjelasan yang jelas, dan beberapa pro tip yang Anda akan berharap sudah tahu sebelumnya.

## Apa yang Anda Butuhkan

- **.NET 6.0** atau yang lebih baru (contoh ini juga bekerja dengan .NET Framework 4.6+).  
- **Aspose.Words for .NET** (atau perpustakaan serupa yang mendukung `FindReplaceOptions`). Anda dapat mengunduhnya dari NuGet dengan `Install-Package Aspose.Words`.  
- Pemahaman dasar tentang sintaks C#—tidak rumit, hanya pernyataan `using` biasa dan metode `Main`.  
- File **.docx** input yang ditempatkan dalam folder yang dapat Anda referensikan (kami akan menyebutnya `YOUR_DIRECTORY/input.docx`).  

Itu saja. Tidak ada file konfigurasi tambahan, tidak ada interop COM, dan sama sekali tidak perlu menjalankan Microsoft Office di server.

> **Pro tip:** Jika Anda berada di pipeline CI/CD, kunci versi Aspose.Words di `csproj` Anda untuk menghindari perubahan yang tidak terduga.

## Langkah 1 – Muat Dokumen Sumber

Hal pertama yang kami lakukan adalah memuat file Word ke memori. Anggap saja seperti membuka sebuah buku catatan; perpustakaan memberikan kami objek `Document` yang mewakili seluruh file.

```csharp
using Aspose.Words;
using System.Text.RegularExpressions;

class Program
{
    static void Main()
    {
        // Load the source document (replace YOUR_DIRECTORY with your actual path)
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx");
```

Mengapa ini penting: memuat dokumen membuat struktur mirip DOM, memungkinkan kami menelusuri paragraf, tabel, header, dan bahkan objek Office Math yang tersembunyi. Jika file tidak ditemukan, Aspose akan melempar `FileNotFoundException` yang jelas, sehingga Anda langsung tahu di mana masalahnya.

## Langkah 2 – Konfigurasikan Opsi Find/Replace

Selanjutnya kami menyiapkan `FindReplaceOptions`. Objek ini memberi tahu mesin *apa* yang harus diabaikan dan *bagaimana* memperlakukan kecocokan. Untuk kebanyakan skenario Anda akan ingin mempertahankan nilai default, tetapi di sini kami menunjukkan cara menonaktifkan pencarian di dalam objek Office Math—sesuatu yang sering membuat banyak pengembang kebingungan.

```csharp
        // Create find/replace options
        FindReplaceOptions replaceOptions = new FindReplaceOptions();

        // Skip math objects during the search (optional but often useful)
        replaceOptions.IgnoreOfficeMath = true;
```

> **Mengapa mengabaikan Office Math?**  
> Persamaan matematika disimpan sebagai fragmen XML terpisah. Jika Anda mencari istilah yang muncul di dalam formula, mesin dapat merusak persamaan tersebut. Menetapkan `IgnoreOfficeMath` ke `true` menghindari risiko itu sambil tetap memodifikasi teks biasa.

## Langkah 3 – Ganti Semua Kemunculan Kata (Contoh Regex)

Sekarang masuk ke inti **replace text in docx**: sebenarnya menukar string lama dengan yang baru. Metode `Range.Replace` menerima sebuah `Regex`, string pengganti, dan opsi yang baru saja kami buat.

```csharp
        // Replace every occurrence of "foo" with "bar"
        doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
```

Beberapa hal yang perlu dicatat:

- Pola `Regex` dapat sesederhana string literal (`@"foo"`) atau ekspresi reguler lengkap (`@"\bfoo\b"` untuk mencocokkan seluruh kata saja).  
- Karena kami menggunakan `Range.Replace`, pencarian mencakup seluruh dokumen—termasuk header, footer, catatan kaki, dan bahkan teks di dalam shape.  
- Metode ini mengembalikan jumlah penggantian yang dilakukan, yang dapat Anda tangkap jika perlu mencatat operasi:

```csharp
        int count = doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        Console.WriteLine($"{count} occurrence(s) replaced.");
```

Baris itu secara langsung memenuhi persyaratan **replace all occurrences word** sambil tetap mudah dibaca.

## Langkah 4 – Simpan Dokumen yang Dimodifikasi

Akhirnya, kami menyimpan perubahan. Anda dapat menimpa file asli atau menulis ke lokasi baru. Menimpa cocok untuk skrip cepat; untuk pipeline produksi, tulis ke file baru untuk menjaga jejak audit.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY/output.docx");
    }
}
```

Itulah seluruh alur kerja untuk **how to replace text c#** dalam dokumen Word. Jalankan program, dan Anda akan melihat `output.docx` dengan setiap “foo” diubah menjadi “bar”.

---

## Topik Lanjutan & Kasus Tepi

### 1. Penggantian Tidak Sensitif Huruf Besar/Kecil

Jika Anda perlu mengabaikan huruf besar/kecil (misalnya, ganti “Foo”, “FOO”, dan “foo” secara bersamaan), sesuaikan opsi regex:

```csharp
        var pattern = new Regex(@"foo", RegexOptions.IgnoreCase);
        doc.Range.Replace(pattern, "bar", replaceOptions);
```

### 2. Mengganti Hanya Seluruh Kata

Kadang “foo” muncul di dalam kata lain seperti “food”. Untuk menghindari perubahan tidak sengaja, beri batas kata pada pola:

```csharp
        var wholeWord = new Regex(@"\bfoo\b");
        doc.Range.Replace(wholeWord, "bar", replaceOptions);
```

### 3. Menggunakan Callback untuk Penggantian Bersyarat

Aspose memungkinkan Anda menyediakan delegate untuk memutuskan secara langsung apakah akan mengganti sebuah kecocokan. Ini berguna untuk skenario seperti “ganti hanya jika kata berada dalam tabel”.

```csharp
        replaceOptions.ReplacingCallback = new ReplaceEvaluator((match, isInsideHeaderFooter, isInsideTable) =>
        {
            // Only replace when inside a table
            return isInsideTable ? "bar" : match.Value;
        });
        doc.Range.Replace(new Regex(@"foo"), "", replaceOptions);
```

### 4. Menangani Dokumen Besar Secara Efisien

Untuk file multi‑gigabyte, pertimbangkan memproses dokumen dalam potongan (misalnya, per bagian) untuk menjaga penggunaan memori tetap rendah. Aspose menyediakan koleksi `Section` yang dapat Anda iterasi dan panggil `Replace` pada masing‑masing secara terpisah.

```csharp
        foreach (Section sec in doc.Sections)
        {
            sec.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        }
```

### 5. Mempertahankan Pemformatan

Teks pengganti mewarisi pemformatan dari karakter pertama yang cocok. Jika Anda perlu menerapkan gaya tertentu (misalnya, tebal), terapkan setelah penggantian:

```csharp
        doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        foreach (Run run in doc.GetChildNodes(NodeType.Run, true))
        {
            if (run.Text.Contains("bar"))
                run.Font.Bold = true; // Force bold on replaced text
        }
```

---

## Kode Sumber Lengkap (Siap Salin‑Tempel)

Berikut adalah program lengkap yang berdiri sendiri yang dapat Anda masukkan ke dalam aplikasi console dan jalankan langsung. Tanpa ketergantungan tersembunyi, tanpa file konfigurasi eksternal.

```csharp
using Aspose.Words;
using System;
using System.Text.RegularExpressions;

namespace DocxReplaceDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"YOUR_DIRECTORY/input.docx");

            // 2️⃣ Set up find/replace options
            FindReplaceOptions replaceOptions = new FindReplaceOptions
            {
                // Skip Office Math objects – optional but safe
                IgnoreOfficeMath = true
            };

            // 3️⃣ Perform the replacement (replace all occurrences word)
            // Change the pattern or replacement as needed
            var pattern = new Regex(@"foo", RegexOptions.IgnoreCase); // case‑insensitive
            int replacedCount = doc.Range.Replace(pattern, "bar", replaceOptions);

            Console.WriteLine($"{replacedCount} occurrence(s) replaced.");

            // 4️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY/output.docx");
        }
    }
}
```

**Output yang diharapkan:**  
Jika `input.docx` berisi tiga contoh “foo” (dalam huruf apa pun), konsol akan mencetak `3 occurrence(s) replaced.` dan `output.docx` akan berisi “bar” di tiga tempat tersebut, sambil mempertahankan gaya asli.

---

## Pertanyaan yang Sering Diajukan

**Q: Apakah ini bekerja dengan file `.doc`?**  
A: Ya. Aspose.Words memperlakukan `.doc` dan `.docx` secara seragam. Cukup ubah ekstensi file pada jalur load/save.

**Q: Bagaimana jika dokumen berisi bagian yang dilindungi?**  
A: Anda perlu membuka perlindungan dokumen terlebih dahulu (`doc.Protect(ProtectionType.NoProtection, "password")`) atau menyediakan kata sandi saat memuat.

**Q: Bisakah saya mengganti teks dalam file yang dilindungi kata sandi?**  
A: Tentu saja. Gunakan `new LoadOptions { Password = "yourPassword" }` saat membuat `Document`.

**Q: Apakah ada alternatif gratis untuk Aspose.Words?**  
A: Open XML SDK dapat melakukan find/replace, tetapi tidak memiliki kemudahan `Range.Replace` tingkat tinggi dan memerlukan lebih banyak boilerplate. Untuk keandalan tingkat produksi, Aspose tetap menjadi pilihan yang direkomendasikan.

---

## Langkah Selanjutnya & Topik Terkait

Setelah Anda menguasai **replace text in docx**, Anda mungkin ingin menjelajahi:

- **Insert images programmatically** – pelajari cara menyisipkan gambar ke dalam placeholder.  
- **Create tables on the fly** – berguna untuk membuat faktur atau laporan.  
- **Batch processing** – iterasi folder berisi file `.docx` dan terapkan logika find‑and‑replace yang sama.  

Setiap topik tersebut dibangun di atas model objek `Document` yang sama yang baru saja Anda gunakan, sehingga Anda akan merasa nyaman.

---

## Kesimpulan

Kami telah membahas semua yang perlu Anda ketahui tentang **replace text in docx** menggunakan C#. Dari memuat dokumen, mengonfigurasi `FindReplaceOptions`, menukar setiap kemunculan kata, hingga menyimpan hasil—tutorial ini memberi Anda solusi lengkap yang dapat disalin‑tempel. Anda juga melihat cara menangani ketidaksensitifan huruf, pencocokan seluruh kata, dan file besar, yang melengkapi skenario **replace all occurrences word** dan **find and replace word document**.

Cobalah, ubah pola regex, dan saksikan tugas otomasi Word Anda berkurang dari jam menjadi detik. Ada variasi yang ingin Anda terapkan? Tinggalkan komentar—selamat coding!

![Tangkapan layar kode C# yang mengganti teks dalam file DOCX](replace-text-in-docx.png "contoh replace text in docx")

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Dokumen Word - Temukan dan Ganti Teks](/words/english/net/find-and-replace-text/)
- [Temukan dan Ganti Teks Sederhana di Word](/words/english/net/find-and-replace-text/simple-find-replace/)
- [Word Ganti Teks yang Mengandung Karakter Meta](/words/english/net/find-and-replace-text/replace-text-containing-meta-characters/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}