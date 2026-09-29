---
title: Tambahkan Watermark Teks Diagonal Merah ke Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 110
limit:
description: Secara otomatis terapkan watermark teks diagonal merah ke setiap file Word yang dihasilkan dalam batch menggunakan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Secara otomatis terapkan watermark teks diagonal merah ke setiap file
    Word yang dihasilkan dalam batch menggunakan Aspose.Words untuk .NET.
  headline: Tambahkan Watermark Teks Diagonal Merah ke Dokumen Word Menggunakan Aspose.Words
    untuk .NET
  type: TechArticle
- description: Secara otomatis terapkan watermark teks diagonal merah ke setiap file
    Word yang dihasilkan dalam batch menggunakan Aspose.Words untuk .NET.
  name: Tambahkan Watermark Teks Diagonal Merah ke Dokumen Word Menggunakan Aspose.Words
    untuk .NET
  steps:
  - name: Buat folder "GeneratedReports" tempat file output akan disimpan.
    text: Buat folder "GeneratedReports" tempat file output akan disimpan.
  - name: Mulai loop yang akan menghasilkan tiga dokumen terpisah.
    text: Mulai loop yang akan menghasilkan tiga dokumen terpisah.
  - name: Buat objek dokumen Word kosong baru.
    text: Buat objek dokumen Word kosong baru.
  - name: Gunakan DocumentBuilder untuk menulis baris judul dan deskripsi ke dalam
      dokumen.
    text: Gunakan DocumentBuilder untuk menulis baris judul dan deskripsi ke dalam
      dokumen.
  - name: Tentukan tampilan watermark, termasuk font, ukuran, warna, dan tata letak
      diagonal.
    text: Tentukan tampilan watermark, termasuk font, ukuran, warna, dan tata letak
      diagonal.
  - name: Terapkan watermark diagonal merah yang telah dikonfigurasi dengan teks "PROTECTED"
      ke dokumen.
    text: Terapkan watermark diagonal merah yang telah dikonfigurasi dengan teks "PROTECTED"
      ke dokumen.
  - name: Simpan dokumen yang telah diberi watermark ke folder "GeneratedReports"
      dengan nama file unik.
    text: Simpan dokumen yang telah diberi watermark ke folder "GeneratedReports"
      dengan nama file unik.
  - name: Tutup loop setelah memproses dokumen saat ini.
    text: Tutup loop setelah memproses dokumen saat ini.
  type: HowTo
- questions:
  - answer: IsSemitrasparent menentukan apakah watermark dirender dengan opasitas
      parsial; mengaturnya ke **true** membuat teks semi‑transparan sehingga konten
      di bawahnya tetap lebih terbaca.
    question: Apa yang dikontrol oleh opsi **IsSemitrasparent** dan efek apa yang
      terjadi bila mengaturnya ke **true**?
  - answer: Ya—atur properti **Layout** menjadi **WatermarkLayout.Horizontal** dalam
      **TextWatermarkOptions** sebelum memanggil **document.Watermark.SetText**.
    question: Apakah saya dapat mengubah orientasi watermark menjadi horizontal alih-alih
      diagonal?
  - answer: Potongan kode ini membuat instance **Document** baru, tetapi Anda dapat
      membuka file yang sudah ada (misalnya, `new Document("Existing.docx")`) dan
      kemudian memanggil **document.Watermark.SetText** untuk menerapkan watermark
      yang sama.
    question: Apakah kode ini akan menambahkan watermark ke file Word yang sudah ada,
      atau hanya ke dokumen yang baru dibuat?
  - answer: Tetapkan warna khusus dengan **Color.FromArgb(red, green, blue)** ke properti
      **Color** pada **TextWatermarkOptions**, misalnya, `Color = Color.FromArgb(128,
      0, 128)` untuk warna ungu.
    question: Bagaimana saya dapat menggunakan warna RGB khusus untuk watermark alih-alih
      **Color.Red** yang telah ditentukan?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Tambahkan Watermark Teks Diagonal Merah ke Dokumen Word
og_description: Lihat cara otomatis menerapkan watermark diagonal merah ke setiap dokumen Word dalam batch dengan Aspose.Words.
og_image_alt: Panduan yang menunjukkan cara menambahkan watermark teks diagonal merah ke dokumen Word menggunakan Aspose.Words untuk .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Watermark Teks Diagonal Merah ke Dokumen Word Menggunakan Aspose.Words untuk .NET
Tutorial ini menunjukkan cara secara otomatis menyematkan watermark teks diagonal merah ke setiap dokumen Word yang dibuat selama proses pembuatan laporan batch. Dengan menggunakan kelas Document dan DocumentBuilder dari Aspose.Words untuk .NET, watermark diterapkan secara programatis saat file dihasilkan, memastikan setiap dokumen memiliki branding atau pemberitahuan kerahasiaan yang sama tanpa upaya manual.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Apa yang dikontrol oleh opsi **IsSemitrasparent** dan efek apa yang terjadi bila mengaturnya ke **true**?**  
A: IsSemitrasparent menentukan apakah watermark dirender dengan opasitas parsial; mengaturnya ke **true** membuat teks semi‑transparan sehingga konten di bawahnya tetap lebih terbaca.

**Q: Apakah saya dapat mengubah orientasi watermark menjadi horizontal alih-alih diagonal?**  
A: Ya—atur properti **Layout** menjadi **WatermarkLayout.Horizontal** dalam **TextWatermarkOptions** sebelum memanggil **document.Watermark.SetText**.

**Q: Apakah kode ini akan menambahkan watermark ke file Word yang sudah ada, atau hanya ke dokumen yang baru dibuat?**  
A: Potongan kode ini membuat instance **Document** baru, tetapi Anda dapat membuka file yang sudah ada (misalnya, `new Document("Existing.docx")`) dan kemudian memanggil **document.Watermark.SetText** untuk menerapkan watermark yang sama.

**Q: Bagaimana saya dapat menggunakan warna RGB khusus untuk watermark alih-alih **Color.Red** yang telah ditentukan?**  
A: Tetapkan warna khusus dengan **Color.FromArgb(red, green, blue)** ke properti **Color** pada **TextWatermarkOptions**, misalnya, `Color = Color.FromArgb(128, 0, 128)` untuk warna ungu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}