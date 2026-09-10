---
title: Sisipkan Bentuk Garis Horizontal dalam Dokumen Word Menggunakan Aspose.Words for .NET
weight: 110
limit:
description: Pelajari cara menambahkan bentuk garis horizontal ke dokumen Word dengan Aspose.Words for .NET menggunakan DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Bentuk Garis Horizontal dalam Dokumen Word Menggunakan Aspose.Words
Dalam tutorial ini Anda akan belajar cara menyisipkan bentuk garis horizontal ke dalam dokumen Word secara programatis dengan Aspose.Words for .NET. Dengan menggunakan kelas Document dan DocumentBuilder, kami membuat dokumen baru, menambahkan paragraf teks, dan kemudian menempatkan bentuk garis horizontal pada lokasi yang diinginkan. Garis horizontal berfungsi sebagai pemisah visual yang dapat berguna untuk pemisahan bagian atau penekanan visual.

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

**Q: Di mana tepatnya `builder.InsertHorizontalRule()` menempatkan garis dalam dokumen?**
A: `InsertHorizontalRule` menyisipkan bentuk garis horizontal pada posisi kursor saat ini dari `DocumentBuilder`; jika Anda menginginkannya berada pada baris terpisah, panggil `builder.Writeln()` sebelum penyisipan.

**Q: Apakah saya dapat mengubah ketebalan, warna, atau lebar garis horizontal yang disisipkan?**
A: `InsertHorizontalRule` menambahkan garis dengan gaya default dan tidak menyediakan opsi pemformatan; untuk menyesuaikan properti tersebut Anda perlu menyisipkan `Shape` secara manual (misalnya, `builder.InsertShape(ShapeType.HorizontalLine)`) dan kemudian mengatur properti `LineFormat`-nya.

**Q: Apakah memungkinkan menambahkan lebih dari satu garis horizontal dalam dokumen yang sama?**
A: Ya—cukup panggil `builder.InsertHorizontalRule()` setiap kali Anda membutuhkan garis baru; setiap pemanggilan membuat bentuk terpisah pada lokasi saat ini builder.

**Q: Apakah garis horizontal akan terlihat ketika .docx yang disimpan dibuka di Microsoft Word?**
A: Tentu saja; garis tersebut disimpan sebagai bentuk di dalam file .docx, sehingga Word menampilkannya persis seperti yang terlihat dalam dokumen yang dihasilkan.

**Q: Apa yang terjadi jika folder `dataDir` tidak ada sebelum memanggil `doc.Save(...)`?**
A: `doc.Save` akan melempar `DirectoryNotFoundException`; pastikan direktori target ada atau buat secara programatis sebelum menyimpan.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}