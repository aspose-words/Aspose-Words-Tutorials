---
title: Sisipkan Barcode DataMatrix dalam Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 210
limit:
description: Tambahkan barcode DataMatrix ke dokumen Word secara programatis dengan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Tambahkan barcode DataMatrix ke dokumen Word secara programatis dengan
    Aspose.Words untuk .NET.
  headline: Sisipkan Barcode DataMatrix dalam Dokumen Word Menggunakan Aspose.Words
    untuk .NET
  type: TechArticle
- description: Tambahkan barcode DataMatrix ke dokumen Word secara programatis dengan
    Aspose.Words untuk .NET.
  name: Sisipkan Barcode DataMatrix dalam Dokumen Word Menggunakan Aspose.Words untuk
    .NET
  steps:
  - name: Buat dokumen Word kosong baru dan DocumentBuilder untuk mengeditnya.
    text: Buat dokumen Word kosong baru dan DocumentBuilder untuk mengeditnya.
  - name: Sisipkan field DISPLAYBARCODE pada posisi kursor saat ini, yang menambahkan
      placeholder field ke dokumen.
    text: Sisipkan field DISPLAYBARCODE pada posisi kursor saat ini, yang menambahkan
      placeholder field ke dokumen.
  - name: Setel BarcodeType field menjadi DataMatrix dan berikan string data untuk
      dienkode.
    text: Setel BarcodeType field menjadi DataMatrix dan berikan string data untuk
      dienkode.
  - name: Secara opsional, definisikan warna latar belakang dan latar depan barcode.
    text: Secara opsional, definisikan warna latar belakang dan latar depan barcode.
  - name: Panggil UpdateFields pada dokumen untuk merender gambar barcode di dalam
      field.
    text: Panggil UpdateFields pada dokumen untuk merender gambar barcode di dalam
      field.
  - name: Simpan dokumen ke file .docx.
    text: Simpan dokumen ke file .docx.
  type: HowTo
- questions:
  - answer: Field akan disisipkan, tetapi `document.UpdateFields()` akan membuat barcode
      kosong dan Aspose.Words akan melempar `FieldException` yang menunjukkan tipe
      barcode tidak valid.
    question: Apa yang terjadi jika saya menetapkan nilai yang tidak didukung ke `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` merender gambar barcode, sehingga Anda dapat menyisipkan
      beberapa objek `FieldDisplayBarcode` dan memanggil `document.UpdateFields()`
      satu kali di akhir untuk merender semuanya.'
    question: Apakah saya perlu memanggil `document.UpdateFields()` setelah setiap
      penyisipan barcode, atau dapat memperbarui sekali setelah menambahkan semua
      field?
  - answer: Kedua properti mengharapkan string RGB heksadesimal yang diawali dengan
      `0x` (mis., `"0xFF0000"` untuk merah); format lain akan diabaikan dan warna
      default akan digunakan.
    question: Format apa yang harus digunakan untuk string warna pada `BackgroundColor`
      dan `ForegroundColor`?
  - answer: Ya—cukup setel `displayBarcodeField.BarcodeValue` ke string baru dan panggil
      `document.UpdateFields()` lagi untuk memperbarui gambar yang dirender.
    question: Apakah saya dapat mengubah payload barcode setelah field disisipkan?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Sisipkan Barcode DataMatrix dengan Aspose.Words
og_description: Pelajari cara menambahkan barcode DataMatrix ke file Word hanya dengan beberapa baris kode .NET.
og_image_alt: Panduan yang menunjukkan cara menyisipkan dan merender barcode DataMatrix dalam dokumen Word menggunakan Aspose.Words untuk .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Barcode DataMatrix dalam Dokumen Word Menggunakan Aspose.Words untuk .NET
Dengan Aspose.Words untuk .NET Anda dapat menambahkan barcode DataMatrix ke dokumen Word secara programatis. Tutorial ini menunjukkan cara membuat dokumen baru, menyisipkan field DISPLAYBARCODE, mengatur tipenya menjadi DataMatrix, dan merender gambar barcode menggunakan kelas Document dan DocumentBuilder. Ikuti langkah-langkah untuk menghasilkan barcode yang dapat dicetak langsung di dalam file .docx Anda.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Apa yang terjadi jika saya menetapkan nilai yang tidak didukung ke `displayBarcodeField.BarcodeType`?**  
A: Field akan disisipkan, tetapi `document.UpdateFields()` akan membuat barcode kosong dan Aspose.Words akan melempar `FieldException` yang menunjukkan tipe barcode tidak valid.

**Q: Apakah saya perlu memanggil `document.UpdateFields()` setelah setiap penyisipan barcode, atau dapat memperbarui sekali setelah menambahkan semua field?**  
A: `UpdateFields()` merender gambar barcode, sehingga Anda dapat menyisipkan beberapa objek `FieldDisplayBarcode` dan memanggil `document.UpdateFields()` satu kali di akhir untuk merender semuanya.

**Q: Format apa yang harus digunakan untuk string warna pada `BackgroundColor` dan `ForegroundColor`?**  
A: Kedua properti mengharapkan string RGB heksadesimal yang diawali dengan `0x` (mis., `"0xFF0000"` untuk merah); format lain akan diabaikan dan warna default akan digunakan.

**Q: Apakah saya dapat mengubah payload barcode setelah field disisipkan?**  
A: Ya—cukup setel `displayBarcodeField.BarcodeValue` ke string baru dan panggil `document.UpdateFields()` lagi untuk memperbarui gambar yang dirender.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}