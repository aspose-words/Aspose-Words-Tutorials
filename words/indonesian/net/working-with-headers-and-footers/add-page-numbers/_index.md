---
title: Tambahkan Nomor Halaman ke Footer Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 210
limit:
description: Tambahkan nomor halaman yang otomatis diperbarui ke footer utama dokumen Word menggunakan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Tambahkan nomor halaman yang otomatis diperbarui ke footer utama dokumen
    Word menggunakan Aspose.Words untuk .NET.
  headline: Tambahkan Nomor Halaman ke Footer Dokumen Word Menggunakan Aspose.Words
    untuk .NET
  type: TechArticle
- description: Tambahkan nomor halaman yang otomatis diperbarui ke footer utama dokumen
    Word menggunakan Aspose.Words untuk .NET.
  name: Tambahkan Nomor Halaman ke Footer Dokumen Word Menggunakan Aspose.Words untuk
    .NET
  steps:
  - name: Buat objek Document baru dan DocumentBuilder yang terhubung dengannya.
    text: Buat objek Document baru dan DocumentBuilder yang terhubung dengannya.
  - name: Pindahkan kursor builder ke footer utama pada bagian pertama.
    text: Pindahkan kursor builder ke footer utama pada bagian pertama.
  - name: Atur perataan paragraf ke tengah sehingga teks footer akan berada di tengah.
    text: Atur perataan paragraf ke tengah sehingga teks footer akan berada di tengah.
  - name: Tuliskan label \"Page \" dan sisipkan field PAGE yang menampilkan nomor
      halaman saat ini.
    text: Tuliskan label \"Page \" dan sisipkan field PAGE yang menampilkan nomor
      halaman saat ini.
  - name: Tuliskan \" of \" dan sisipkan field NUMPAGES yang menunjukkan total jumlah
      halaman.
    text: Tuliskan \" of \" dan sisipkan field NUMPAGES yang menunjukkan total jumlah
      halaman.
  - name: Simpan dokumen ke file .docx.
    text: Simpan dokumen ke file .docx.
  type: HowTo
- questions:
  - answer: Tidak. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` memindahkan
      builder hanya ke footer utama *bagian pertama*, sehingga field disisipkan hanya
      di sana.
    question: Jika dokumen memiliki lebih dari satu bagian, apakah kode ini akan menambahkan
      nomor halaman ke footer setiap bagian?
  - answer: Atur `builder.ParagraphFormat.Alignment` ke nilai `ParagraphAlignment`
      lain (mis., `ParagraphAlignment.Right`) sebelum menulis field.
    question: Bagaimana saya dapat mengubah perataan paragraf nomor halaman di footer?
  - answer: '`InsertField` menerima kode field dan hasil field opsional; memberikan
      `null` memberi tahu Aspose.Words untuk membiarkan Word menghitung hasilnya saat
      runtime.'
    question: Apa yang dimaksud dengan argumen `null` dalam `InsertField(\"PAGE\",
      null)`?
  - answer: Ya—ganti `HeaderFooterType.FooterPrimary` dengan `HeaderFooterType.HeaderPrimary`
      (atau tipe header lain) sebelum menyisipkan field.
    question: Apakah saya dapat menempatkan field \"Page X of Y\" yang sama di header
      alih-alih di footer?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Sisipkan Nomor Halaman Otomatis di Footer Word
og_description: Kode langkah demi langkah untuk menambahkan nomor halaman dinamis ke footer Word dengan Aspose.Words untuk .NET.
og_image_alt: Panduan yang menunjukkan cara menambahkan nomor halaman otomatis ke footer dokumen Word menggunakan Aspose.Words untuk .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Nomor Halaman ke Footer Dokumen Word Menggunakan Aspose.Words untuk .NET
Tutorial ini menunjukkan cara menggunakan Aspose.Words Document dan DocumentBuilder untuk menyisipkan nomor halaman yang otomatis diperbarui ke footer utama dokumen Word. Dengan menambahkan nomor halaman secara programatik, Anda memastikan penomoran halaman yang konsisten di seluruh file tanpa penyuntingan manual. Kode contoh siap dijalankan di lingkungan .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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

**Q: Jika dokumen memiliki lebih dari satu bagian, apakah kode ini akan menambahkan nomor halaman ke footer setiap bagian?**  
A: Tidak. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` memindahkan builder hanya ke footer utama *bagian pertama*, sehingga field disisipkan hanya di sana.

**Q: Bagaimana saya dapat mengubah perataan paragraf nomor halaman di footer?**  
A: Atur `builder.ParagraphFormat.Alignment` ke nilai `ParagraphAlignment` lain (mis., `ParagraphAlignment.Right`) sebelum menulis field.

**Q: Apa yang dimaksud dengan argumen `null` dalam `InsertField(\"PAGE\", null)`?**  
A: `InsertField` menerima kode field dan hasil field opsional; memberikan `null` memberi tahu Aspose.Words untuk membiarkan Word menghitung hasilnya saat runtime.

**Q: Apakah saya dapat menempatkan field \"Page X of Y\" yang sama di header alih-alih di footer?**  
A: Ya—ganti `HeaderFooterType.FooterPrimary` dengan `HeaderFooterType.HeaderPrimary` (atau tipe header lain) sebelum menyisipkan field.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}