---
title: Buat Watermark Teks Diagonal dengan Font Kustom dalam Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 210
limit:
description: Kode langkah demi langkah untuk menambahkan watermark teks diagonal dengan font kustom ke file Word .docx menggunakan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Kode langkah demi langkah untuk menambahkan watermark teks diagonal
    dengan font kustom ke file Word .docx menggunakan Aspose.Words untuk .NET.
  headline: Buat Watermark Teks Diagonal dengan Font Kustom dalam Dokumen Word Menggunakan
    Aspose.Words untuk .NET
  type: TechArticle
- description: Kode langkah demi langkah untuk menambahkan watermark teks diagonal
    dengan font kustom ke file Word .docx menggunakan Aspose.Words untuk .NET.
  name: Buat Watermark Teks Diagonal dengan Font Kustom dalam Dokumen Word Menggunakan
    Aspose.Words untuk .NET
  steps:
  - name: Buat sebuah instance dokumen Word kosong baru dengan nama `document`.
    text: Buat sebuah instance dokumen Word kosong baru dengan nama `document`.
  - name: Konfigurasikan `watermarkSettings` dengan font Arial 48‑pt berwarna abu-abu,
      tata letak diagonal, dan render opak.
    text: Konfigurasikan `watermarkSettings` dengan font Arial 48‑pt berwarna abu-abu,
      tata letak diagonal, dan render opak.
  - name: Terapkan watermark teks "Private" ke `document` menggunakan pengaturan yang
      telah didefinisikan sebelumnya.
    text: Terapkan watermark teks "Private" ke `document` menggunakan pengaturan yang
      telah didefinisikan sebelumnya.
  - name: Tentukan jalur file tempat dokumen berwatermark akan disimpan.
    text: Tentukan jalur file tempat dokumen berwatermark akan disimpan.
  - name: Simpan `document` yang telah dimodifikasi ke jalur yang ditentukan sebagai
      file .docx.
    text: Simpan `document` yang telah dimodifikasi ke jalur yang ditentukan sebagai
      file .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` menentukan apakah watermark dirender dengan opasitas
      parsial; mengatur ke `false` membuat watermark sepenuhnya opak, sedangkan `true`
      menerapkan efek semi‑transparan default.'
    question: Apa yang dikontrol oleh flag **IsSemitrasparent** dalam `TextWatermarkOptions`?
  - answer: Ya—atur properti `Layout` ke `WatermarkLayout.Horizontal` (atau nilai
      enum lain) sebelum memanggil `document.Watermark.SetText`.
    question: Apakah saya dapat mengubah orientasi watermark menjadi horizontal alih-alih
      diagonal?
  - answer: Word akan kembali ke font defaultnya untuk watermark, sehingga teks tetap
      muncul tetapi mungkin terlihat berbeda dari gaya yang dimaksud.
    question: Apa yang terjadi jika `FontFamily` yang ditentukan (misalnya "Arial")
      tidak terpasang di mesin target?
  - answer: Muat file yang ada dengan `Document document = new Document("Existing.docx");`
      kemudian konfigurasikan `TextWatermarkOptions` dan panggil `document.Watermark.SetText`
      seperti yang ditunjukkan.
    question: Apakah memungkinkan menambahkan watermark ke file `.docx` yang sudah
      ada alih-alih membuat yang baru?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Tambahkan Watermark Teks Diagonal dengan Font Kustom
og_description: Pelajari cara menyematkan watermark teks miring dengan font Anda sendiri ke dalam file Word dalam hitungan menit.
og_image_alt: Panduan yang menunjukkan cara menambahkan watermark teks diagonal dengan font kustom ke dokumen Word menggunakan Aspose.Words untuk .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Buat Watermark Teks Diagonal dengan Font Kustom dalam Dokumen Word Menggunakan Aspose.Words untuk .NET
Tutorial ini memandu Anda melalui pembuatan dokumen Word baru, mengonfigurasi watermark teks diagonal dengan pengaturan font pilihan Anda, menerapkannya melalui API Document.Watermark.SetText, dan menyimpan hasilnya sebagai file .docx. Pada akhir tutorial Anda akan memiliki dokumen berwatermark profesional yang menampilkan merek atau kepemilikan Anda. Kode langkah demi langkah siap disalin ke proyek .NET mana pun.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Apa yang dikontrol oleh flag **IsSemitrasparent** dalam `TextWatermarkOptions`?**  
A: `IsSemitrasparent` menentukan apakah watermark dirender dengan opasitas parsial; mengatur ke `false` membuat watermark sepenuhnya opak, sedangkan `true` menerapkan efek semi‑transparan default.

**Q: Apakah saya dapat mengubah orientasi watermark menjadi horizontal alih-alih diagonal?**  
A: Ya—atur properti `Layout` ke `WatermarkLayout.Horizontal` (atau nilai enum lain) sebelum memanggil `document.Watermark.SetText`.

**Q: Apa yang terjadi jika `FontFamily` yang ditentukan (misalnya "Arial") tidak terpasang di mesin target?**  
A: Word akan kembali ke font defaultnya untuk watermark, sehingga teks tetap muncul tetapi mungkin terlihat berbeda dari gaya yang dimaksud.

**Q: Apakah memungkinkan menambahkan watermark ke file `.docx` yang sudah ada alih-alih membuat yang baru?**  
A: Muat file yang ada dengan `Document document = new Document("Existing.docx");` kemudian konfigurasikan `TextWatermarkOptions` dan panggil `document.Watermark.SetText` seperti yang ditunjukkan.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}