---
date: 2026-01-09
description: Pelajari cara menggabungkan dokumen dengan Aspose.Words untuk Java sambil
  mempertahankan format, menautkan header dan footer, serta lainnya.
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
title: Cara Menggabungkan Dokumen Menggunakan Aspose.Words untuk Java
url: /id/java/document-manipulation/joining-and-appending-documents/
weight: 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggabungkan Dokumen dengan Aspose.Words untuk Java

Menggabungkan file Word secara programatik dapat menjadi sakit kepala—terutama ketika Anda perlu menjaga gaya, nomor halaman, dan header/footer tetap utuh. Dalam tutorial ini Anda akan menemukan **cara menggabungkan dokumen** menggunakan pustaka Aspose.Words untuk Java, langkah demi langkah. Kami akan membahas penambahan sederhana, opsi impor lanjutan, penanganan pengaturan halaman yang berbeda, dan trik yang Anda perlukan untuk **mempertahankan format hasil penggabungan** dalam berbagai skenario dunia nyata.

## Jawaban Cepat
- **Apa cara termudah untuk menggabungkan dokumen Word?** Gunakan `Document.appendDocument` dengan `ImportFormatMode.KEEP_SOURCE_FORMATTING`.  
- **Apakah saya dapat mempertahankan gaya asli setiap file sumber?** Ya—atur `ImportFormatMode.USE_DESTINATION_STYLES` atau aktifkan Smart Style Behavior.  
- **Bagaimana cara menjaga nomor halaman tetap benar setelah penggabungan?** Konversi field `NUMPAGES` menjadi referensi halaman dan panggil `updatePageLayout()`.  
- **Apakah header dan footer tetap terhubung secara otomatis?** Anda dapat menautkan atau memutuskan tautannya dengan `linkToPrevious(true/false)`.  
- **Apa yang saya perlukan sebelum memulai?** Aspose.Words untuk Java ditambahkan ke proyek Anda dan file sumber `.docx` siap.

## Pengantar Penggabungan dan Penambahan Dokumen di Aspose.Words untuk Java

Dalam tutorial ini, kita akan menjelajahi cara menggabungkan dan menambahkan dokumen menggunakan pustaka Aspose.Words untuk Java. Anda akan belajar cara menggabungkan beberapa dokumen secara mulus sambil mempertahankan format dan struktur.

## Prasyarat

Sebelum kita mulai, pastikan Anda telah menyiapkan API Aspose.Words untuk Java di proyek Java Anda.

## Opsi Penggabungan Dokumen

### Penambahan Sederhana

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Penambahan dengan Opsi Format Impor

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Penambahan ke Dokumen Kosong

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Penambahan dengan Konversi Nomor Halaman

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## Menangani Pengaturan Halaman yang Berbeda

Saat menambahkan dokumen dengan pengaturan halaman yang berbeda:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## Menggabungkan Dokumen dengan Gaya yang Berbeda

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Perilaku Gaya Pintar

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Menyisipkan Dokumen dengan DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Menjaga Penomoran Sumber

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Menangani Kotak Teks

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Mengelola Header dan Footer

### Menautkan Header dan Footer

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Memutuskan Tautan Header dan Footer

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Mengapa Ini Penting untuk Proyek “merge word documents java”

Ketika Anda perlu **menggabungkan dokumen word java**‑style, mempertahankan tampilan dan nuansa setiap file sangat penting untuk alur kerja hukum, penerbitan, atau pelaporan. Menggunakan teknik di atas memastikan bahwa:

* Gaya dari setiap sumber tetap utuh (atau disatukan, tergantung pilihan Anda).  
* Penomoran halaman dan pemisah bagian berperilaku dapat diprediksi.  
* Header dan footer dapat ditautkan atau dipertahankan terpisah dengan satu baris kode.  

## Kesalahan Umum & Tips

| Masalah | Mengapa Terjadi | Cara Memperbaiki |
|---------|----------------|------------------|
| Kehilangan penomoran setelah penggabungan | field `NUMPAGES` masih mengarah ke bagian asli | Panggil `convertNumPageFieldsToPageRef` dan `updatePageLayout()` |
| Benturan gaya | Menggunakan `KEEP_SOURCE_FORMATTING` dengan gaya yang konflik | Ganti ke `USE_DESTINATION_STYLES` atau aktifkan Smart Style Behavior |
| Halaman kosong muncul | Nilai `SectionStart` yang berbeda | Atur `SectionStart.CONTINUOUS` pada bagian sumber sebelum menambahkan |

## Pertanyaan yang Sering Diajukan

**T: Bagaimana saya dapat menggabungkan dokumen dengan gaya yang berbeda secara mulus?**  
J: Gunakan `ImportFormatMode.USE_DESTINATION_STYLES` saat menambahkan, atau aktifkan `SmartStyleBehavior` untuk penggabungan yang lebih pintar.

**T: Bisakah saya mempertahankan penomoran halaman saat menambahkan dokumen?**  
J: Ya, konversi field `NUMPAGES` menjadi referensi halaman dengan `convertNumPageFieldsToPageRef` lalu panggil `updatePageLayout()`.

**T: Apa itu Smart Style Behavior?**  
J: Ini secara otomatis memetakan gaya sumber ke gaya tujuan bila memungkinkan, membantu menjaga tampilan konsisten di seluruh konten yang digabungkan.

**T: Bagaimana saya menangani kotak teks saat menambahkan dokumen?**  
J: Atur `importFormatOptions.setIgnoreTextBoxes(false)` sehingga kotak teks dipertahankan selama penggabungan.

**T: Bagaimana jika saya ingin menautkan atau memutuskan tautan header dan footer antar dokumen?**  
J: Gunakan `linkToPrevious(true)` untuk menautkan, atau `linkToPrevious(false)` untuk memisahkannya sebelum memanggil `appendDocument`.

## Kesimpulan

Aspose.Words untuk Java menyediakan alat yang fleksibel dan kuat untuk **cara menggabungkan dokumen**, baik Anda perlu mempertahankan format yang tepat, menangani pengaturan halaman yang beragam, atau mengontrol penautan header/footer. Bereksperimenlah dengan potongan kode di atas untuk menyesuaikan alur kerja pemrosesan dokumen Anda, dan Anda akan dapat **menggabungkan dokumen word java**‑style dengan percaya diri.

---

**Terakhir Diperbarui:** 2026-01-09  
**Diuji Dengan:** Aspose.Words for Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}