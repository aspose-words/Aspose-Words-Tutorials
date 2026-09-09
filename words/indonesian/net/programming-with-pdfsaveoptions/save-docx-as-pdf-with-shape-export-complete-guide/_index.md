---
category: general
date: 2026-02-13
description: Simpan docx sebagai pdf sambil mempertahankan bentuk mengambang. Pelajari
  cara mengonversi Word ke pdf, mengekspor bentuk, dan menangani kasus khusus dalam
  C#.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: id
og_description: Simpan docx sebagai pdf sambil mempertahankan bentuk mengambang. Panduan
  ini menunjukkan cara mengonversi Word ke pdf, mengekspor bentuk, dan menangani jebakan
  umum.
og_title: Simpan docx sebagai PDF dengan Ekspor Bentuk – Panduan Lengkap
tags:
- Aspose.Words
- C#
- PDF conversion
title: Simpan docx sebagai PDF dengan Shape Export – Panduan Lengkap
url: /id/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan docx sebagai pdf – Tutorial Full‑stack (C#)

Pernahkah Anda perlu **save docx as pdf** dan menjaga diagram mengambang tetap persis sama? Anda tidak sendirian. Banyak pengembang mengalami masalah ketika bentuk Word menghilang atau rusak setelah konversi. Kabar baiknya? Dengan beberapa baris C# Anda dapat memberi tahu perpustakaan untuk memperlakukan setiap bentuk sebagai elemen tingkat‑blok, dan hasilnya adalah replika PDF yang setia.

Dalam panduan ini kami akan membahas seluruh proses: memuat file `.docx`, mengonfigurasi opsi **convert word to pdf** sehingga bentuk diekspor dengan benar, dan akhirnya menulis PDF ke disk. Pada akhir tutorial Anda akan mengetahui **how to export shapes**, memahami trade‑offs dari berbagai mode ekspor, dan memiliki contoh kode siap‑jalankan yang dapat Anda masukkan ke proyek .NET mana pun.

> **What you’ll get:** contoh lengkap yang dapat dijalankan, penjelasan tentang *mengapa* setiap pengaturan penting, tips untuk kasus tepi, dan ide untuk memperluas solusi (mis., menangani gambar, font khusus, atau PDF yang dilindungi kata sandi).

---

## Prasyarat

- .NET 6+ (atau .NET Framework 4.7+). API yang kami gunakan berfungsi pada keduanya.
- Aspose.Words untuk .NET (versi percobaan gratis atau berlisensi). Instal via NuGet: `Install-Package Aspose.Words`.
- Dokumen Word (`input.docx`) yang berisi bentuk mengambang (kotak teks, auto‑shapes, SmartArt, dll.).
- Visual Studio 2022 atau IDE apa pun yang Anda sukai.

Tidak ada pustaka pihak ketiga lain yang diperlukan.

---

## Implementasi Langkah‑per‑Langkah

Di bawah setiap langkah Anda akan melihat cuplikan kode singkat, penjelasan dalam bahasa Inggris sederhana, dan catatan tentang **how to export shapes** dengan benar.

### ## Step 1 – Muat dokumen sumber (save docx as pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*Why this matters:* Kelas `Document` mewakili seluruh file Word dalam memori. Jika Anda melewatkan langkah ini, tidak ada yang dapat dikonversi, dan opsi PDF berikutnya tidak memiliki apa‑apa untuk diproses.

### ## Step 2 – Konfigurasikan opsi penyimpanan PDF (how to export shapes)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Explanation**

- `PdfSaveOptions` adalah “kantong pengaturan” yang memberi tahu Aspose.Words cara menerjemahkan konstruksi Word ke PDF.
- Properti **ExportFloatingShapesAsInlineTag** memiliki tiga nilai kemungkinan:
  1. **Inline** – bentuk menjadi elemen inline (sering tertekan ke dalam teks di sekitarnya).
  2. **Block** – setiap bentuk ditempatkan pada bloknya sendiri, yang merupakan cara paling aman untuk mempertahankan tampilan asli.
  3. **Auto** – perpustakaan memutuskan secara otomatis (tidak selalu memilih opsi terbaik).

Memilih **Block** adalah pendekatan yang disarankan ketika Anda *need to export shapes* persis seperti yang muncul di dokumen asli. Ini mencegah masalah “bentuk menghilang” yang banyak ditemui ketika hanya memanggil `doc.Save("out.pdf")`.

### ## Step 3 – Simpan dokumen sebagai PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*What you’ll see:* Setelah baris ini dijalankan, `FloatingShapes.pdf` berada di `C:\MyFolder`. Buka file tersebut, dan Anda harus melihat setiap kotak teks, panggilan, dan SmartArt ditempatkan persis seperti di `.docx` sumber.

## Contoh Kerja Lengkap

Berikut adalah **complete program** yang dapat Anda kompilasi dan jalankan sebagai aplikasi konsol. Ini mencakup semua pernyataan `using` yang diperlukan dan komentar untuk kejelasan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Output yang Diharapkan**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

Buka PDF yang dihasilkan dan verifikasi bahwa semua bentuk mempertahankan posisi aslinya. Jika ada bentuk yang masih tampak tidak tepat, periksa kembali bahwa itu benar‑benar bentuk *floating* (bukan gambar inline) di Word.

## Pertanyaan yang Sering Diajukan & Kasus Tepi

| Question | Answer |
|----------|--------|
| **Bisakah saya mengekspor bentuk sebagai inline alih-alih block?** | Ya – atur `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline`. Ini mungkin berguna untuk tata letak sederhana, tetapi harapkan aliran teks yang lebih rapat dan kemungkinan tumpang tindih. |
| **Bagaimana jika dokumen saya berisi gambar di dalam bentuk?** | Opsi yang sama berfungsi; Aspose.Words merasterisasi bentuk bersama dengan gambarnya. Untuk fidelitas tertinggi, juga aktifkan `PdfSaveOptions.JpegQuality` jika Anda memerlukan kompresi gambar yang lebih baik. |
| **Apakah ini bekerja dengan file DOCX yang dilindungi kata sandi?** | Muat dokumen dengan objek `LoadOptions` yang menyediakan kata sandi, lalu lanjutkan seperti biasa. |
| **Bisakah saya mengonversi beberapa file DOCX sekaligus?** | Bungkus logika tiga langkah dalam loop `foreach` atas daftar file. Ingat untuk menggunakan kembali `PdfSaveOptions` demi kinerja. |
| **Apakah PDF kompatibel dengan pembaca lama (Acrobat 7)?** | Secara default Aspose.Words membuat file PDF 1.7. Atur `pdfOptions.Compliance = PdfCompliance.PdfA1b` untuk PDF tingkat arsip yang dapat bekerja pada pembaca lama. |

## Tips Pro & Kesalahan Umum

- **Pro tip:** Jika Anda melihat pergeseran vertikal kecil setelah konversi, coba atur `pdfOptions.UsePdfDocumentStructure = true`. Ini memaksa mesin PDF menghormati hierarki tata letak Word.
- **Watch out for:** Dokumen yang mencampur bentuk mengambang dengan tabel yang di‑anchor. Dalam beberapa kasus, ekspor blok dapat memindahkan tabel ke halaman baru; Anda dapat mengurangi hal ini dengan menyesuaikan `pdfOptions.PageSetup` sebelum menyimpan.
- **Performance note:** Menggunakan kembali satu instance `PdfSaveOptions` untuk banyak file mengurangi tekanan GC dan mempercepat konversi batch.

## Referensi Visual

Berikut adalah screenshot skematis (placeholder) yang menunjukkan sebelum/ sesudah dokumen dengan kotak teks mengambang.

![save docx as pdf example with floating shapes](image-placeholder.png "save docx as pdf example with floating shapes")

*Gambar ini menggambarkan bagaimana bentuk tetap persis di tempat semula dalam file Word asli setelah konversi.*

## Kesimpulan

Kami telah membahas **how to save docx as pdf** sambil menjaga setiap bentuk mengambang tetap utuh, mengeksplorasi pengaturan **convert word to pdf** yang penting, dan menjawab pertanyaan paling umum tentang “**how to export shapes**”. Contoh kode lengkap siap dimasukkan ke proyek C# mana pun, dan penyesuaian opsional memberi Anda fleksibilitas untuk skenario dunia nyata seperti pemrosesan batch atau kepatuhan PDF/A.

### Langkah Selanjutnya

- Coba **convert word document pdf** dengan tingkat kepatuhan yang berbeda (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`) untuk memenuhi persyaratan regulasi.
- Bereksperimen dengan **how to convert docx pdf** untuk file yang dilindungi kata sandi—tambahkan `LoadOptions` dengan kata sandi dan `PdfSaveOptions` dengan `EncryptionDetails`.
- Jelajahi format output lain (mis., XPS, HTML) menggunakan objek `Document` yang sama; satu‑satunya perubahan adalah argumen format pada metode `Save`.

Ada pertanyaan lain? Tinggalkan komentar, dan selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}