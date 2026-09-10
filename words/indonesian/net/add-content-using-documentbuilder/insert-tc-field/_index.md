---
title: Sisipkan Bidang TC dalam Dokumen Word Menggunakan Aspose.Words for .NET
weight: 110
limit:
description: Pelajari cara menyisipkan bidang TC dengan teks khusus ke dalam dokumen Word menggunakan Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Bidang TC dalam Dokumen Word Menggunakan Aspose.Words
Tutorial ini menunjukkan cara menggunakan Aspose.Words for .NET untuk menyisipkan bidang TC (Table of Contents) ke dalam dokumen Word yang baru dibuat. Dengan menggunakan DocumentBuilder Anda dapat menambahkan bidang TC dengan teks entri khusus, yang berguna untuk membuat indeks yang dapat dicari untuk daftar isi. Contoh ini juga memperlihatkan cara menyimpan dokumen ke disk.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: Apa arti switch "\f t" dalam kode bidang TC?**
A: Switch "\f t" memberi tahu Word untuk memperlakukan entri sebagai entri tabel, sehingga muncul dalam Daftar Isi yang dihasilkan dengan switch \f.

**Q: Bagaimana saya dapat mengubah teks yang muncul dalam bidang TC?**
A: Ganti "Entry Text" dalam pemanggilan InsertField dengan string apa pun yang Anda inginkan, misalnya, builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Apakah saya dapat menyisipkan beberapa bidang TC dalam dokumen yang sama?**
A: Ya; cukup panggil builder.InsertField dengan teks entri yang berbeda pada lokasi yang diinginkan sebelum menyimpan dokumen.

**Q: Apakah kode ini bekerja untuk format selain .docx, seperti .pdf?**
A: Dokumen disimpan sebagai .docx dalam contoh ini, tetapi Aspose.Words dapat menyimpan ke format lain (misalnya, .pdf) dengan mengubah ekstensi file pada doc.Save dan memastikan format output yang sesuai didukung.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}