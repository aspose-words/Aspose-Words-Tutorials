---
title: Tambahkan bidang formulir Kotak Centang ke Dokumen Word dengan Aspose.Words for .NET
weight: 210
limit:
description: Pelajari cara menambahkan bidang formulir kotak centang secara programatis ke dokumen Word baru menggunakan Aspose.Words for .NET dan menyimpan file tersebut.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan bidang formulir Kotak Centang ke Dokumen Word dengan Aspose.Words
Tutorial ini menunjukkan cara membuat dokumen Word baru dan menggunakan DocumentBuilder dari Aspose.Words for .NET untuk menyisipkan bidang formulir kotak centang. Dengan mengikuti langkah-langkah, Anda akan melihat kode tepat yang diperlukan untuk menambahkan elemen interaktif tersebut dan kemudian menyimpan dokumen ke sebuah file. Ini adalah cara cepat untuk membuat file Word yang mendukung formulir secara programatis.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: Apa yang dimaksud dengan argumen keempat (0) dalam InsertCheckBox?**
A: Ini menentukan ukuran visual kotak centang dalam poin; nilai 0 memberi tahu Aspose.Words untuk menggunakan ukuran default.

**Q: Apakah saya dapat menyisipkan lebih dari satu kotak centang dengan nama yang sama?**
A: Tidak – setiap nama bidang formulir harus unik; mencoba menyisipkan kotak centang lain dengan nama "CheckBox" akan menyebabkan ArgumentException.

**Q: Bagaimana cara menambahkan kotak centang ke dokumen yang sudah ada alih-alih dokumen baru?**
A: Muat dokumen terlebih dahulu (misalnya, `Document doc = new Document("Existing.docx");`) kemudian buat DocumentBuilder untuk dokumen tersebut dan panggil `InsertCheckBox` pada posisi kursor yang diinginkan.

**Q: Bagaimana saya dapat membaca status kotak centang yang disisipkan setelah dokumen disimpan?**
A: Ambil bidang formulir melalui `doc.Range.FormFields["CheckBox"]` dan periksa properti `Checked`-nya untuk melihat apakah kotak tersebut tercentang.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}