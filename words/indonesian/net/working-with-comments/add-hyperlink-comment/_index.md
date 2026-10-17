---
title: Tambahkan Hyperlink Comment dan Ekspor sebagai PDF Annotation Menggunakan Aspose.Words untuk .NET
weight: 110
limit:
description: Pelajari cara menambahkan komentar hyperlink dalam file Word dan mengekspornya sebagai anotasi PDF dengan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Pelajari cara menambahkan komentar hyperlink dalam file Word dan mengekspornya
    sebagai anotasi PDF dengan Aspose.Words untuk .NET.
  headline: Tambahkan Hyperlink Comment dan Ekspor sebagai PDF Annotation Menggunakan
    Aspose.Words untuk .NET
  type: TechArticle
- description: Pelajari cara menambahkan komentar hyperlink dalam file Word dan mengekspornya
    sebagai anotasi PDF dengan Aspose.Words untuk .NET.
  name: Tambahkan Hyperlink Comment dan Ekspor sebagai PDF Annotation Menggunakan
    Aspose.Words untuk .NET
  steps:
  - name: Buat objek Document kosong baru dan DocumentBuilder untuk bekerja dengannya.
    text: Buat objek Document kosong baru dan DocumentBuilder untuk bekerja dengannya.
  - name: Tulis satu baris teks yang terlihat yang akan menjadi tempat komentar yang
      akan datang.
    text: Tulis satu baris teks yang terlihat yang akan menjadi tempat komentar yang
      akan datang.
  - name: Buat Comment yang ditulis oleh Jane Doe dan lampirkan ke paragraf pertama
      dokumen.
    text: Buat Comment yang ditulis oleh Jane Doe dan lampirkan ke paragraf pertama
      dokumen.
  - name: Di dalam komentar, tambahkan paragraf dan sisipkan hyperlink berwarna biru
      dan bergaris bawah ke situs web Aspose.Words Library.
    text: Di dalam komentar, tambahkan paragraf dan sisipkan hyperlink berwarna biru
      dan bergaris bawah ke situs web Aspose.Words Library.
  - name: Konfigurasikan dokumen untuk merender komentar sebagai anotasi PDF dan segarkan
      tata letaknya.
    text: Konfigurasikan dokumen untuk merender komentar sebagai anotasi PDF dan segarkan
      tata letaknya.
  - name: Buat folder "Output" di direktori saat ini untuk menyimpan PDF yang dihasilkan.
    text: Buat folder "Output" di direktori saat ini untuk menyimpan PDF yang dihasilkan.
  - name: Simpan dokumen yang telah disiapkan sebagai file PDF menggunakan PdfSaveOptions.
    text: Simpan dokumen yang telah disiapkan sebagai file PDF menggunakan PdfSaveOptions.
  - name: Periksa bahwa file PDF ada dan berisi data, lalu tampilkan hasilnya ke konsol.
    text: Periksa bahwa file PDF ada dan berisi data, lalu tampilkan hasilnya ke konsol.
  type: HowTo
- questions:
  - answer: Parameter ketiga `InsertHyperlink` menentukan apakah tautan harus diperlakukan
      sebagai field; mengaturnya ke `false` menyisipkan hyperlink biasa yang berfungsi
      dalam anotasi PDF tanpa memerlukan kode field.
    question: Apa yang dikontrol oleh argumen ketiga (`false`) dalam `InsertHyperlink`?
  - answer: Setel `myDocument.LayoutOptions.CommentDisplayMode` ke `CommentDisplayMode.ShowInBalloons`
      sebelum memanggil `Save`; PDF kemudian akan berisi komentar sebagai komentar
      Word biasa bukan sebagai anotasi.
    question: Bagaimana saya dapat membuat komentar muncul sebagai balon di dokumen
      Word alih-alih anotasi PDF?
  - answer: Ya—setiap `Comment` yang Anda tambahkan ke paragraf dapat berisi panggilan
      `InsertHyperlink` masing‑masing, dan semua hyperlink akan dipertahankan sebagai
      anotasi PDF terpisah saat dokumen disimpan.
    question: Jika saya menambahkan lebih dari satu komentar, apakah setiap hyperlink
      akan berfungsi dalam PDF yang diekspor?
  - answer: Buka PDF yang dihasilkan, temukan anotasi komentar (biasanya ditampilkan
      sebagai ikon catatan), klik untuk menampilkan teks komentar, lalu klik tautan
      berwarna biru bergaris bawah; tautan tersebut harus membuka URL target di peramban
      web.
    question: Bagaimana saya memverifikasi bahwa hyperlink di dalam komentar benar‑benar
      berfungsi setelah PDF dihasilkan?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Sisipkan Hyperlink Comment & Ekspor ke PDF
og_description: Pelajari cara menyematkan tautan yang dapat diklik dalam komentar Word dan mengubahnya menjadi anotasi PDF.
og_image_alt: Panduan yang menunjukkan cara menambahkan komentar dengan hyperlink yang dapat diklik ke dokumen Word dan mengekspornya sebagai anotasi PDF menggunakan Aspose.Words untuk .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Hyperlink Comment dan Ekspor sebagai PDF Annotation Menggunakan Aspose.Words untuk .NET
Di tutorial ini Anda akan melihat cara membuat dokumen Word, menyisipkan komentar yang berisi hyperlink yang dapat diklik ke situs web eksternal, mengonfigurasi komentar tersebut agar muncul sebagai anotasi PDF, mengekspor dokumen ke PDF, dan memverifikasi file PDF yang dihasilkan. Kode langkah demi langkah memungkinkan Anda menambahkan komentar kaya dengan tautan dan mempertahankannya saat mengonversi ke PDF, sehingga mudah berbagi catatan interaktif dengan pembaca.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Apa yang dikontrol oleh argumen ketiga (`false`) dalam `InsertHyperlink`?**  
A: Parameter ketiga `InsertHyperlink` menentukan apakah tautan harus diperlakukan sebagai field; mengaturnya ke `false` menyisipkan hyperlink biasa yang berfungsi dalam anotasi PDF tanpa memerlukan kode field.

**Q: Bagaimana saya dapat membuat komentar muncul sebagai balon di dokumen Word alih-alih anotasi PDF?**  
A: Setel `myDocument.LayoutOptions.CommentDisplayMode` ke `CommentDisplayMode.ShowInBalloons` sebelum memanggil `Save`; PDF kemudian akan berisi komentar sebagai komentar Word biasa bukan sebagai anotasi.

**Q: Jika saya menambahkan lebih dari satu komentar, apakah setiap hyperlink akan berfungsi dalam PDF yang diekspor?**  
A: Ya—setiap `Comment` yang Anda tambahkan ke paragraf dapat berisi panggilan `InsertHyperlink` masing‑masing, dan semua hyperlink akan dipertahankan sebagai anotasi PDF terpisah saat dokumen disimpan.

**Q: Bagaimana saya memverifikasi bahwa hyperlink di dalam komentar benar‑benar berfungsi setelah PDF dihasilkan?**  
A: Buka PDF yang dihasilkan, temukan anotasi komentar (biasanya ditampilkan sebagai ikon catatan), klik untuk menampilkan teks komentar, lalu klik tautan berwarna biru bergaris bawah; tautan tersebut harus membuka URL target di peramban web.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}