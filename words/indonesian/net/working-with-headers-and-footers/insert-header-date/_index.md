---
title: Sisipkan Tanggal Header Dinamis dalam Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 110
limit:
description: Pelajari cara menambahkan field DATE dinamis ke header utama dokumen Word dengan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Pelajari cara menambahkan field DATE dinamis ke header utama dokumen
    Word dengan Aspose.Words untuk .NET.
  headline: Sisipkan Tanggal Header Dinamis dalam Dokumen Word Menggunakan Aspose.Words
    untuk .NET
  type: TechArticle
- description: Pelajari cara menambahkan field DATE dinamis ke header utama dokumen
    Word dengan Aspose.Words untuk .NET.
  name: Sisipkan Tanggal Header Dinamis dalam Dokumen Word Menggunakan Aspose.Words
    untuk .NET
  steps:
  - name: Buat sebuah Document baru dan DocumentBuilder untuk mengeditnya.
    text: Buat sebuah Document baru dan DocumentBuilder untuk mengeditnya.
  - name: Pindahkan kursor builder ke header utama sehingga penyisipan berikutnya
      memengaruhi header.
    text: Pindahkan kursor builder ke header utama sehingga penyisipan berikutnya
      memengaruhi header.
  - name: Tuliskan label statis dan sisipkan field DATE dengan format “MMMM d, yyyy”
      ke dalam header, menghasilkan tanggal dinamis.
    text: Tuliskan label statis dan sisipkan field DATE dengan format “MMMM d, yyyy”
      ke dalam header, menghasilkan tanggal dinamis.
  - name: Kembali ke badan utama dan tambahkan paragraf contoh, yang menunjukkan konten
      dokumen normal bersamaan dengan header.
    text: Kembali ke badan utama dan tambahkan paragraf contoh, yang menunjukkan konten
      dokumen normal bersamaan dengan header.
  - name: Simpan dokumen ke file .docx.
    text: Simpan dokumen ke file .docx.
  type: HowTo
- questions:
  - answer: Panggilan `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` menempatkan
      builder pada header utama yang sudah ada, dan `Write`/`InsertField` hanya menambahkan
      teks ke apa yang sudah ada; mereka tidak menghapus konten yang sudah ada.
    question: Apa yang terjadi jika dokumen sudah memiliki header utama – apakah kode
      saya akan menimpanya?
  - answer: Ya – ubah format switch dalam kode field yang diberikan ke `InsertField`,
      misalnya `builder.InsertField(\"DATE \\\\@ \\"yyyy-MM-dd\\\")` akan menghasilkan
      tanggal seperti 2026-09-22.
    question: Apakah saya dapat mengubah format tanggal yang digunakan oleh field
      DATE, dan bagaimana caranya?
  - answer: Ganti `HeaderFooterType.HeaderPrimary` dengan `HeaderFooterType.HeaderFirst`
      saat memanggil `MoveToHeaderFooter`; sisanya tetap berfungsi sama.
    question: Jika saya membutuhkan field tanggal di header halaman pertama alih-alih
      header utama, apa yang harus saya lakukan?
  - answer: Field tersebut disisipkan hanya dengan switch `\\@`, yang memberi tahu
      Word untuk menampilkan tanggal saat ini setiap kali field disegarkan (mis.,
      saat membuka file atau ketika Anda menekan Ctrl+Alt+F9).
    question: Apakah field DATE secara otomatis memperbarui saat dokumen dibuka nanti?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Tambahkan Tanggal Dinamis ke Header Word
og_description: Panduan langkah demi langkah untuk menyematkan field tanggal aktif di header Word Anda dengan Aspose.Words.
og_image_alt: Tangkapan layar yang menunjukkan cara menyisipkan field DATE dinamis ke header dokumen Word menggunakan Aspose.Words untuk .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Tanggal Header Dinamis dalam Dokumen Word Menggunakan Aspose.Words untuk .NET
Tutorial ini menunjukkan cara menggunakan kelas Document dan DocumentBuilder dalam Aspose.Words untuk .NET untuk menyisipkan field DATE dinamis ke header utama sebuah dokumen Word. Field yang ditambahkan secara otomatis memperbarui ke tanggal saat ini setiap kali dokumen dibuka, memastikan header Anda selalu menampilkan tanggal terbaru. Ikuti kode langkah demi langkah untuk menambahkan field dan menyimpan file yang telah diperbarui.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Apa yang terjadi jika dokumen sudah memiliki header utama – apakah kode saya akan menimpanya?**  
A: Panggilan `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` menempatkan builder pada header utama yang sudah ada, dan `Write`/`InsertField` hanya menambahkan teks ke apa yang sudah ada; mereka tidak menghapus konten yang sudah ada.

**Q: Apakah saya dapat mengubah format tanggal yang digunakan oleh field DATE, dan bagaimana caranya?**  
A: Ya – ubah format switch dalam kode field yang diberikan ke `InsertField`, misalnya `builder.InsertField(\"DATE \\\\@ \\"yyyy-MM-dd\\\")` akan menghasilkan tanggal seperti 2026-09-22.

**Q: Jika saya membutuhkan field tanggal di header halaman pertama alih-alih header utama, apa yang harus saya lakukan?**  
A: Ganti `HeaderFooterType.HeaderPrimary` dengan `HeaderFooterType.HeaderFirst` saat memanggil `MoveToHeaderFooter`; sisanya tetap berfungsi sama.

**Q: Apakah field DATE secara otomatis memperbarui saat dokumen dibuka nanti?**  
A: Field tersebut disisipkan hanya dengan switch `\\@`, yang memberi tahu Word untuk menampilkan tanggal saat ini setiap kali field disegarkan (mis., saat membuka file atau ketika Anda menekan Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}