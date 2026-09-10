---
title: Tambahkan Field TC ke Dokumen Word dengan Aspose.Words for .NET
weight: 310
limit:
description: Pelajari cara menyisipkan field TC ke dalam dokumen Word baru dengan Aspose.Words for .NET menggunakan DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Field TC ke Dokumen Word dengan Aspose.Words
Dalam tutorial interaktif ini Anda akan belajar cara menambahkan field TC secara programatis—sebuah penanda tersembunyi yang digunakan oleh fitur pengindeksan dan daftar isi Word—ke dokumen yang baru dibuat menggunakan Aspose.Words for .NET. Dengan menggunakan DocumentBuilder Anda dapat menempatkan field tepat di tempat yang Anda butuhkan dan kemudian menyimpan file, siap untuk pemrosesan lebih lanjut.

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

**Q: Apa yang sebenarnya dilakukan field \"TC\" yang disisipkan oleh `builder.InsertField(\\\"TC \\\"Entry Text\\\" \\\\f t\\\")` dalam dokumen Word?**
A: Ia membuat entri Daftar Isi dengan teks yang terlihat \"Entry Text\" dan menandainya sebagai entri TC (Table of Contents), yang kemudian dapat digunakan Word saat menghasilkan TOC.

**Q: Apa tujuan switch `\\f t` dalam string field TC?**
A: Switch `\\f t` memberi tahu Word untuk memperlakukan entri tersebut sebagai entri teks biasa (bukan heading) dan untuk menyertakannya dalam Daftar Isi saat TOC dibangun.

**Q: Apakah saya dapat menyisipkan beberapa field TC dengan teks entri yang berbeda menggunakan instance `DocumentBuilder` yang sama?**
A: Ya; cukup panggil `builder.InsertField` lagi dengan string yang berbeda, misalnya `builder.InsertField(\"TC \\"Another Entry\" \\f t\")`, dan setiap pemanggilan akan menyisipkan field TC baru pada posisi kursor saat ini.

**Q: Jika saya memerlukan teks entri yang dinamis (misalnya, dari variabel), bagaimana saya harus memformat pemanggilan `InsertField`?**
A: Bangun string field dengan interpolasi string atau `String.Format`, misalnya: `string entry = \"Chapter 1\"; builder.InsertField($\"TC \\\"{entry}\\\" \\\\f t\");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}