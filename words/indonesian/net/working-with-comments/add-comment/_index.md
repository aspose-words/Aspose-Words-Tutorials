---
title: Sisipkan Comment pada Paragraf Tertentu dalam Dokumen Word Menggunakan Aspose.Words for .NET
weight: 210
limit:
description: Panduan langkah demi langkah untuk menambahkan komentar penulis ke paragraf yang dipilih dalam dokumen Word dan menyimpannya sebagai DOCX menggunakan Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Panduan langkah demi langkah untuk menambahkan komentar penulis ke
    paragraf yang dipilih dalam dokumen Word dan menyimpannya sebagai DOCX menggunakan
    Aspose.Words for .NET.
  headline: Sisipkan Comment pada Paragraf Tertentu dalam Dokumen Word Menggunakan
    Aspose.Words for .NET
  type: TechArticle
- description: Panduan langkah demi langkah untuk menambahkan komentar penulis ke
    paragraf yang dipilih dalam dokumen Word dan menyimpannya sebagai DOCX menggunakan
    Aspose.Words for .NET.
  name: Sisipkan Comment pada Paragraf Tertentu dalam Dokumen Word Menggunakan Aspose.Words
    for .NET
  steps:
  - name: Instansiasi Document baru dan DocumentBuilder untuk mulai membangun file
      Word.
    text: Instansiasi Document baru dan DocumentBuilder untuk mulai membangun file
      Word.
  - name: Gunakan DocumentBuilder.Writeln untuk menambahkan tiga paragraf teks terpisah
      ke dalam dokumen.
    text: Gunakan DocumentBuilder.Writeln untuk menambahkan tiga paragraf teks terpisah
      ke dalam dokumen.
  - name: Dapatkan paragraf kedua secara aman, kembali ke paragraf pertama jika dokumen
      memiliki kurang dari dua paragraf.
    text: Dapatkan paragraf kedua secara aman, kembali ke paragraf pertama jika dokumen
      memiliki kurang dari dua paragraf.
  - name: Buat Comment dengan detail penulis, atur teksnya, dan lampirkan ke paragraf
      yang dipilih.
    text: Buat Comment dengan detail penulis, atur teksnya, dan lampirkan ke paragraf
      yang dipilih.
  - name: Simpan dokumen yang dimodifikasi sebagai file DOCX bernama 'sample.docx'
      di folder saat ini.
    text: Simpan dokumen yang dimodifikasi sebagai file DOCX bernama 'sample.docx'
      di folder saat ini.
  type: HowTo
- questions:
  - answer: Blok `if` kembali ke paragraf pertama (`paraList[0]`) ketika `paraList.Count`
      kurang dari 2, sehingga komentar akan dilampirkan ke paragraf tunggal itu alih-alih
      paragraf kedua yang tidak ada.
    question: Apa yang dilakukan kode jika dokumen hanya berisi satu paragraf?
  - answer: Mereka diteruskan ke konstruktor `Comment` sebagai argumen kedua dan ketiga
      – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – di mana \"Jordan\"
      adalah nama penulis dan \"JH\" adalah inisialnya.
    question: Bagaimana nama penulis komentar dan inisialnya diatur dalam contoh ini?
  - answer: Dalam potongan kode ini komentar terhubung ke seluruh `Paragraph` melalui
      `AppendChild`, tetapi untuk mengomentari rentang teks Anda perlu membuat `CommentRangeStart`
      dan `CommentRangeEnd` di sekitar node `Run` yang diinginkan dan kemudian menambahkan
      node `Comment` di antara keduanya.
    question: Apakah saya dapat melampirkan komentar ke bagian teks tertentu alih-alih
      seluruh paragraf?
  - answer: '`AppendChild` menambahkan node `Comment` ke koleksi anak paragraf, dan
      Aspose.Words secara otomatis menghasilkan penanda mulai/akhir komentar yang
      diperlukan saat dokumen disimpan.'
    question: Apakah saya perlu menyisipkan penanda komentar secara manual, atau `AppendChild`
      menangani itu?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Sisipkan komentar ke dalam paragraf Word
og_description: Tambahkan komentar penulis ke paragraf tertentu dan ekspor file sebagai DOCX dengan Aspose.Words.
og_image_alt: Panduan yang menunjukkan cara menambahkan komentar ke paragraf dalam dokumen Word menggunakan Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Comment pada Paragraf Tertentu dalam Dokumen Word Menggunakan Aspose.Words
Dengan Aspose.Words for .NET Anda dapat menambahkan komentar ke file Word secara programatik. Tutorial ini menjelaskan cara membuat dokumen baru, menyisipkan tiga paragraf, menemukan paragraf kedua, dan melampirkan komentar yang mencakup informasi penulis dan tanggal. Akhirnya, dokumen disimpan sebagai file DOCX yang mempertahankan komentar.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: Apa yang dilakukan kode jika dokumen hanya berisi satu paragraf?**  
A: Blok `if` kembali ke paragraf pertama (`paraList[0]`) ketika `paraList.Count` kurang dari 2, sehingga komentar akan dilampirkan ke paragraf tunggal itu alih-alih paragraf kedua yang tidak ada.

**Q: Bagaimana nama penulis komentar dan inisialnya diatur dalam contoh ini?**  
A: Mereka diteruskan ke konstruktor `Comment` sebagai argumen kedua dan ketiga – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – di mana \"Jordan\" adalah nama penulis dan \"JH\" adalah inisialnya.

**Q: Apakah saya dapat melampirkan komentar ke bagian teks tertentu alih-alih seluruh paragraf?**  
A: Dalam potongan kode ini komentar terhubung ke seluruh `Paragraph` melalui `AppendChild`, tetapi untuk mengomentari rentang teks Anda perlu membuat `CommentRangeStart` dan `CommentRangeEnd` di sekitar node `Run` yang diinginkan dan kemudian menambahkan node `Comment` di antara keduanya.

**Q: Apakah saya perlu menyisipkan penanda komentar secara manual, atau `AppendChild` menangani itu?**  
A: `AppendChild` menambahkan node `Comment` ke koleksi anak paragraf, dan Aspose.Words secara otomatis menghasilkan penanda mulai/akhir komentar yang diperlukan saat dokumen disimpan.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}