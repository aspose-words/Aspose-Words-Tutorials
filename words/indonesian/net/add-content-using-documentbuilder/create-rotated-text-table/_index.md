---
title: Buat Tabel Teks Berputar di Dokumen Word Menggunakan Aspose.Words untuk .NET
weight: 110
limit:
description: Pelajari cara membuat tabel Word dengan lebar kolom tetap, teks berputar, tinggi baris yang presisi, dan sel terisi menggunakan Aspose.Words untuk .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Pelajari cara membuat tabel Word dengan lebar kolom tetap, teks berputar,
    tinggi baris yang presisi, dan sel terisi menggunakan Aspose.Words untuk .NET.
  headline: Buat Tabel Teks Berputar di Dokumen Word Menggunakan Aspose.Words untuk
    .NET
  type: TechArticle
- description: Pelajari cara membuat tabel Word dengan lebar kolom tetap, teks berputar,
    tinggi baris yang presisi, dan sel terisi menggunakan Aspose.Words untuk .NET.
  name: Buat Tabel Teks Berputar di Dokumen Word Menggunakan Aspose.Words untuk .NET
  steps:
  - name: Instansiasi Document baru dan DocumentBuilder yang akan digunakan untuk
      membangun tabel.
    text: Instansiasi Document baru dan DocumentBuilder yang akan digunakan untuk
      membangun tabel.
  - name: Mulai tabel baru, sisipkan sel pertama, dan tetapkan lebar kolom sehingga
      tidak otomatis menyesuaikan.
    text: Mulai tabel baru, sisipkan sel pertama, dan tetapkan lebar kolom sehingga
      tidak otomatis menyesuaikan.
  - name: Ratakan konten secara vertikal di tengah pada sel saat ini dan tulis teks
      sel pertama baris pertama.
    text: Ratakan konten secara vertikal di tengah pada sel saat ini dan tulis teks
      sel pertama baris pertama.
  - name: Sisipkan sel kedua pada baris pertama dan tulis teksnya.
    text: Sisipkan sel kedua pada baris pertama dan tulis teksnya.
  - name: Tutup baris pertama, menyelesaikan tata letaknya.
    text: Tutup baris pertama, menyelesaikan tata letaknya.
  - name: Mulai sel pertama pada baris kedua, atur tinggi baris menjadi tepat 100
      poin, putar teks ke atas, dan tulis teks sel tersebut.
    text: Mulai sel pertama pada baris kedua, atur tinggi baris menjadi tepat 100
      poin, putar teks ke atas, dan tulis teks sel tersebut.
  - name: Sisipkan sel kedua pada baris kedua, putar teksnya ke bawah, dan tulis teks
      sel tersebut.
    text: Sisipkan sel kedua pada baris kedua, putar teksnya ke bawah, dan tulis teks
      sel tersebut.
  - name: Tutup baris kedua, menyelesaikan baris kedua tabel.
    text: Tutup baris kedua, menyelesaikan baris kedua tabel.
  - name: Akiri konstruksi tabel, mengunci struktur tabel.
    text: Akiri konstruksi tabel, mengunci struktur tabel.
  - name: Simpan dokumen yang selesai ke file .docx.
    text: Simpan dokumen yang selesai ke file .docx.
  type: HowTo
- questions:
  - answer: Setelah mengatur lebar kolom, tetapkan lebar untuk setiap sel menggunakan
      `builder.CellFormat.Width = <valueInPoints>;` sebelum menyisipkan sel berikutnya;
      tabel akan mempertahankan lebar tepat tersebut.
    question: Bagaimana saya dapat mengatur lebar kolom tertentu setelah memanggil
      `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` adalah pengaturan tingkat sel,
      jadi Anda perlu mengaturnya kembali untuk sel‑sel di baris kedua (mis., `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) sebelum menulis kontennya.'
    question: Mengapa perataan vertikal hanya memengaruhi baris pertama dan tidak
      baris kedua?
  - answer: Ya—atur `builder.RowFormat.Height` dan `builder.RowFormat.HeightRule =
      HeightRule.Exactly` sebelum setiap pemanggilan `builder.EndRow();`; baris berikutnya
      dapat memiliki nilai tinggi yang berbeda.
    question: Apakah saya dapat memberikan setiap baris tinggi tepat yang berbeda,
      dan jika ya, bagaimana caranya?
  - answer: Setel kembali orientasi dengan menetapkan `builder.CellFormat.Orientation
      = TextOrientation.Horizontal;` sebelum menulis ke sel berikutnya.
    question: Bagaimana cara mengembalikan orientasi teks ke default setelah menggunakan
      `TextOrientation.Upward` atau `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Buat Tabel Teks Berputar di Word dengan Aspose.Words
og_description: Kode langkah demi langkah untuk membangun tabel berlebar tetap dengan teks berputar vertikal dan tinggi baris yang tepat.
og_image_alt: Tangkapan layar yang menampilkan dokumen Word dengan tabel yang memiliki lebar kolom tetap, teks berputar di dalam sel, dan tinggi baris yang ditentukan, dibuat menggunakan Aspose.Words untuk .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Buat Tabel Teks Berputar di Dokumen Word Menggunakan Aspose.Words untuk .NET
Tutorial ini menunjukkan cara menghasilkan dokumen Word dan menambahkan tabel dengan kolom berlebar tetap, baris dengan tinggi tepat, dan teks sel diputar secara vertikal. Anda akan belajar mengatur perataan vertikal, menerapkan orientasi teks, mengisi setiap sel dengan konten, dan akhirnya menyimpan dokumen—semua dengan Aspose.Words untuk .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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

**Q: Bagaimana saya dapat mengatur lebar kolom tertentu setelah memanggil `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: Setelah mengatur lebar kolom, tetapkan lebar untuk setiap sel menggunakan `builder.CellFormat.Width = <valueInPoints>;` sebelum menyisipkan sel berikutnya; tabel akan mempertahankan lebar tepat tersebut.

**Q: Mengapa perataan vertikal hanya memengaruhi baris pertama dan tidak baris kedua?**  
A: `builder.CellFormat.VerticalAlignment` adalah pengaturan tingkat sel, jadi Anda perlu mengaturnya kembali untuk sel‑sel di baris kedua (mis., `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) sebelum menulis kontennya.

**Q: Apakah saya dapat memberikan setiap baris tinggi tepat yang berbeda, dan jika ya, bagaimana caranya?**  
A: Ya—atur `builder.RowFormat.Height` dan `builder.RowFormat.HeightRule = HeightRule.Exactly` sebelum setiap pemanggilan `builder.EndRow();`; baris berikutnya dapat memiliki nilai tinggi yang berbeda.

**Q: Bagaimana cara mengembalikan orientasi teks ke default setelah menggunakan `TextOrientation.Upward` atau `Downward`?**  
A: Setel kembali orientasi dengan menetapkan `builder.CellFormat.Orientation = TextOrientation.Horizontal;` sebelum menulis ke sel berikutnya.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}