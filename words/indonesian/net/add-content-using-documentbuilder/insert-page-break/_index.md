---
title: Sisipkan Jeda Halaman dalam Dokumen Word dengan Aspose.Words for .NET
weight: 110
limit:
description: Pelajari cara menambahkan jeda halaman ke file Word dengan Aspose.Words for .NET menggunakan Document dan DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Jeda Halaman dalam Dokumen Word dengan Aspose.Words
Dalam tutorial interaktif ini Anda akan belajar cara menambahkan jeda halaman secara programatis ke dokumen Word menggunakan Aspose.Words for .NET. Dengan membuat objek Document dan menggunakan DocumentBuilder, Anda dapat mengontrol di mana halaman baru dimulai, yang penting untuk memformat laporan, faktur, atau dokumen multi‑bagian apa pun. Ikuti contoh langkah demi langkah untuk melihat kode beraksi dan pratinjau file yang dihasilkan.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: Apakah saya dapat menggunakan InsertBreak untuk menambahkan jeda baris atau jeda seksi alih-alih jeda halaman?**
A: Ya, InsertBreak menerima nilai enum BreakType apa pun, seperti BreakType.LineBreak atau BreakType.SectionBreakContinuous, untuk menyisipkan jeda yang sesuai.

**Q: Apakah saya perlu memanggil InsertBreak sebelum atau setelah menulis teks untuk halaman baru?**
A: InsertBreak harus dipanggil setelah konten yang Anda inginkan pada halaman saat ini; Writeln berikutnya kemudian akan dimulai pada halaman baru yang dibuat oleh jeda tersebut.

**Q: Apa yang terjadi jika jalur dataDir tidak diakhiri dengan pemisah direktori?**
A: Jika dataDir tidak memiliki garis miring akhir, nama file akan digabungkan langsung (mis., "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), yang dapat menyebabkan jalur tidak valid; pastikan jalur diakhiri dengan "\\" atau gunakan Path.Combine.

**Q: Apakah saya dapat menggunakan kembali instance DocumentBuilder yang sama untuk menyisipkan beberapa jeda di seluruh dokumen?**
A: Ya, DocumentBuilder yang sama dapat digunakan berulang kali; setiap panggilan ke InsertBreak menyisipkan jeda pada posisi kursor builder saat ini.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}