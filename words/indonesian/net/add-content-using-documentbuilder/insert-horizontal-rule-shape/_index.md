---
title: Masukkan Bentuk Garis Horizontal dalam Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 110
limit:
description: Panduan langkah demi langkah untuk menyisipkan bentuk garis horizontal ke dalam dokumen Word dengan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Bentuk Garis Horizontal dalam Dokumen Word Menggunakan Aspose.Words untuk .NET
Pelajari cara menggunakan Aspose.Words untuk .NET untuk menyisipkan bentuk garis horizontal ke dalam dokumen Word. Tutorial ini memandu Anda melalui pembuatan dokumen baru, menambahkan satu baris teks, menempatkan bentuk garis horizontal dengan DocumentBuilder, dan menyimpan file. Garis horizontal memberikan pemisah visual sederhana untuk konten Anda.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: Apakah saya dapat mengubah tampilan (warna, ketebalan) dari garis horizontal yang disisipkan dengan DocumentBuilder.InsertHorizontalRule()?**
A: InsertHorizontalRule membuat bentuk garis horizontal bawaan dengan format default; untuk mengubah tampilannya Anda harus mengambil objek Shape yang disisipkan (builder.CurrentParagraph.LastChild) dan menyesuaikan properti LineFormat-nya.

**Q: Apa yang terjadi jika saya memanggil InsertHorizontalRule() setelah paragraf yang sudah berakhir dengan jeda baris?**
A: Metode ini menyisipkan garis sebagai paragraf terpisah, sehingga jeda baris sebelumnya hanya membuat paragraf kosong sebelum garis; garis tetap akan muncul pada barisnya sendiri.

**Q: Apakah memungkinkan menyisipkan lebih dari satu garis horizontal dalam dokumen yang sama menggunakan DocumentBuilder?**
A: Ya, setiap pemanggilan builder.InsertHorizontalRule() menambahkan bentuk garis horizontal baru pada posisi kursor saat ini, memungkinkan beberapa garis di seluruh dokumen.

**Q: Apakah InsertHorizontalRule() berfungsi saat menyimpan dokumen ke format selain DOCX, seperti PDF?**
A: Garis horizontal disimpan sebagai bentuk dalam model dokumen, sehingga saat Anda menyimpan ke PDF, XPS, atau format lain yang didukung, garis tersebut akan dirender dengan benar dalam output.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}