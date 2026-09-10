---
title: Sisipkan HTML yang Terjajar ke Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 210
limit:
description: Pelajari cara menyisipkan HTML mentah dengan penjajaran kiri, tengah, atau kanan ke dalam dokumen Word menggunakan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan HTML yang Terjajar ke Dokumen Word Menggunakan Aspose.Words untuk .NET
Tutorial interaktif ini menunjukkan cara menyisipkan HTML mentah ke dalam dokumen Word sambil mengontrol penjajarannya—kiri, tengah, atau kanan—menggunakan Aspose.Words untuk .NET. Dengan memanfaatkan Document dan DocumentBuilder, Anda dapat menyisipkan string HTML dan menerapkan penjajaran paragraf yang diinginkan hanya dalam beberapa baris kode. Contoh ini ideal ketika Anda perlu mempertahankan format HTML dan menempatkan konten secara tepat di dalam dokumen Anda.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Apa yang terjadi jika string HTML yang diberikan ke DocumentBuilder.InsertHtml berisi tag yang tidak didukung oleh Aspose.Words, seperti <script> atau <iframe>?**
A: Tag yang tidak didukung akan diabaikan; Aspose.Words hanya mem-parsing subset HTML yang dapat dirender, sehingga <script>, <iframe>, dan elemen serupa dihapus sementara sisanya tetap disisipkan.

**Q: Apakah gaya CSS inline (misalnya, <span style\="color:red;\">) akan dipertahankan saat menggunakan InsertHtml?**
A: Ya, InsertHtml menghormati banyak properti CSS inline seperti color, font‑size, dan background, mengonversinya ke format Word yang sesuai.

**Q: Apakah InsertHtml secara otomatis membuat paragraf baru untuk elemen level‑blok seperti <div> atau <h1>?**
A: Elemen level‑blok dipetakan ke paragraf Word, sehingga setiap <div>, <p>, <h1>, dll., menjadi paragraf terpisah dalam dokumen.

**Q: Bagaimana cara menyisipkan HTML pada lokasi tertentu dalam dokumen yang sudah ada, bukan di awal?**
A: Pindahkan kursor DocumentBuilder ke node yang diinginkan (misalnya, builder.MoveToDocumentEnd() atau builder.MoveToParagraph(index)) sebelum memanggil InsertHtml; HTML akan disisipkan pada posisi kursor saat ini.

**Q: Jika dokumen sudah berisi teks, apakah memanggil InsertHtml akan menimpa konten yang ada?**
A: Tidak, InsertHtml menyisipkan HTML yang telah diparsing pada posisi saat ini dari builder tanpa menghapus node yang ada, kecuali Anda secara eksplisit memindahkan kursor ke dalam atau menghapus node tersebut terlebih dahulu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}