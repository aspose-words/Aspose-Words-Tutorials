---
"description": "Pelajari cara menyimpan dokumen Word sebagai PDF menggunakan Aspose.Words untuk Java. Sesuaikan font, properti, dan kualitas gambar. Panduan lengkap untuk konversi PDF."
"linktitle": "Menyimpan Dokumen sebagai PDF"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menyimpan Dokumen sebagai PDF di Aspose.Words untuk Java"
"url": "/id/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menyimpan Dokumen sebagai PDF di Aspose.Words untuk Java


## Pengantar Menyimpan Dokumen sebagai PDF di Aspose.Words untuk Java

Dalam panduan langkah demi langkah ini, kita akan membahas cara menyimpan dokumen sebagai PDF menggunakan Aspose.Words untuk Java. Kita akan membahas berbagai aspek konversi PDF dan memberikan contoh kode untuk mempermudah prosesnya.

## Prasyarat

Sebelum kita memulai, pastikan Anda memiliki prasyarat berikut:

- Java Development Kit (JDK) terinstal di sistem Anda.
- Aspose.Words untuk pustaka Java. Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/java/).

## Mengonversi Dokumen ke PDF

Untuk mengonversi dokumen Word ke PDF, Anda dapat menggunakan potongan kode berikut:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Mengganti `"input.docx"` dengan jalur ke dokumen Word Anda dan `"output.pdf"` dengan jalur berkas PDF keluaran yang diinginkan.

## Mengontrol Opsi Penyimpanan PDF

Anda dapat mengontrol berbagai opsi penyimpanan PDF menggunakan `PdfSaveOptions` kelas. Misalnya, Anda dapat mengatur judul tampilan untuk dokumen PDF sebagai berikut:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Menanamkan Font dalam PDF

Untuk menanamkan font pada PDF yang dihasilkan, gunakan kode berikut:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Menyesuaikan Properti Dokumen

Anda dapat menyesuaikan properti dokumen dalam PDF yang dihasilkan. Misalnya:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Mengekspor Struktur Dokumen

Untuk mengekspor struktur dokumen, atur `exportDocumentStructure` pilihan untuk `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Kompresi Gambar

Anda dapat mengontrol kompresi gambar menggunakan kode berikut:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Memperbarui Properti Terakhir Dicetak

Untuk memperbarui properti "Terakhir Dicetak" dalam PDF, gunakan:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Merender Efek DML 3D

Untuk rendering efek DML 3D tingkat lanjut, atur mode rendering:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Interpolasi Gambar

Anda dapat mengaktifkan interpolasi gambar untuk meningkatkan kualitas gambar:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Kesimpulan

Aspose.Words untuk Java menyediakan kemampuan komprehensif untuk mengonversi dokumen Word ke format PDF dengan fleksibilitas dan opsi penyesuaian. Anda dapat mengontrol berbagai aspek keluaran PDF, termasuk font, properti dokumen, kompresi gambar, dan banyak lagi.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara mengonversi dokumen Word ke PDF menggunakan Aspose.Words untuk Java?

Untuk mengonversi dokumen Word ke PDF, gunakan kode berikut:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Mengganti `"input.docx"` dengan jalur ke dokumen Word Anda dan `"output.pdf"` dengan jalur berkas PDF keluaran yang diinginkan.

### Dapatkah saya menyematkan font dalam PDF yang dihasilkan oleh Aspose.Words untuk Java?

Ya, Anda dapat menyematkan font di PDF dengan mengatur `setEmbedFullFonts` pilihan untuk `true` di dalam `PdfSaveOptions`Berikut ini contohnya:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Bagaimana saya dapat menyesuaikan properti dokumen dalam PDF yang dihasilkan?

Anda dapat menyesuaikan properti dokumen dalam PDF menggunakan `setCustomPropertiesExport` pilihan di `PdfSaveOptions`. Misalnya:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Apa tujuan kompresi gambar di Aspose.Words untuk Java?

Kompresi gambar memungkinkan Anda mengontrol kualitas dan ukuran gambar dalam PDF yang dihasilkan. Anda dapat mengatur mode kompresi gambar menggunakan `setImageCompression` di dalam `PdfSaveOptions`.

### Bagaimana cara memperbarui properti "Terakhir Dicetak" dalam PDF?

Anda dapat memperbarui properti "Terakhir Dicetak" dalam PDF dengan mengatur `setUpdateLastPrintedProperty` ke `true` di dalam `PdfSaveOptions`Ini akan mencerminkan tanggal cetak terakhir dalam metadata PDF.

### Bagaimana cara meningkatkan kualitas gambar saat mengonversi ke PDF?

Untuk meningkatkan kualitas gambar, aktifkan interpolasi gambar dengan menyetel `setInterpolateImages` ke `true` di dalam `PdfSaveOptions`Ini akan menghasilkan gambar yang lebih halus dan berkualitas tinggi dalam PDF.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}