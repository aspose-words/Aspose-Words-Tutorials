---
title: Menyisipkan HTML Beralign ke Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 210
limit:
description: Pelajari cara menyisipkan HTML dengan perataan tertentu ke dalam dokumen Word menggunakan Aspose.Words untuk .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menyisipkan HTML Beralign ke Dokumen Word Menggunakan Aspose.Words untuk .NET
Tutorial ini menunjukkan cara menggunakan DocumentBuilder dari Aspose.Words untuk .NET untuk menyematkan markup HTML ke dalam dokumen Word dan mengontrol perataannya. Anda akan melihat cara menyisipkan HTML, mengatur perataan paragraf (kiri, tengah, atau kanan), dan kemudian menyimpan dokumen yang dihasilkan. Contoh ini ideal bagi pengembang yang perlu mempertahankan format gaya web saat menghasilkan file Word secara programatis.

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

**Q: Apakah InsertHtml dapat digunakan untuk menambahkan HTML ke dalam dokumen Word yang sudah ada daripada yang baru?**  
A: Ya. Buat Document dari file yang sudah ada, posisikan kursor DocumentBuilder di tempat Anda ingin menyisipkan HTML (misalnya, dengan menggunakan builder.MoveToDocumentEnd()), lalu panggil builder.InsertHtml dengan markup Anda.

**Q: Atribut HTML mana yang dihormati oleh InsertHtml untuk perataan?**  
A: InsertHtml menghormati atribut "align" pada elemen level blok seperti &lt;p&gt;, &lt;div&gt;, dan tag heading, menerapkan perataan paragraf yang sesuai dalam dokumen Word yang dihasilkan.

**Q: Apa yang terjadi jika string HTML berisi tag atau CSS yang tidak didukung?**  
A: Tag yang tidak didukung akan diabaikan dan teks di dalamnya disisipkan sebagai teks biasa; gaya CSS inline yang tidak dikenali oleh Aspose.Words juga diabaikan, sehingga hanya subset HTML yang didukung yang akan dirender.

**Q: Apakah saya perlu menutup DocumentBuilder sebelum menyimpan dokumen?**  
A: Tidak diperlukan penutupan eksplisit; setelah menyisipkan HTML Anda dapat langsung memanggil doc.Save dengan nama file dan format yang diinginkan, dan sumber daya builder akan dilepaskan secara otomatis.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}