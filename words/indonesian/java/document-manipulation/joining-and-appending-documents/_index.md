---
"description": "Pelajari cara menggabungkan dan menambahkan dokumen dengan mudah menggunakan Aspose.Words untuk Java. Pertahankan format, kelola header, footer, dan banyak lagi."
"linktitle": "Menggabungkan dan Menambahkan Dokumen"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menggabungkan dan Menambahkan Dokumen di Aspose.Words untuk Java"
"url": "/id/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggabungkan dan Menambahkan Dokumen di Aspose.Words untuk Java


## Pengantar Penggabungan dan Penambahan Dokumen di Aspose.Words untuk Java

Dalam tutorial ini, kita akan mempelajari cara menggabungkan dan menambahkan dokumen menggunakan pustaka Aspose.Words untuk Java. Anda akan mempelajari cara menggabungkan beberapa dokumen dengan lancar sambil mempertahankan format dan struktur.

## Prasyarat

Sebelum memulai, pastikan Anda telah menyiapkan Aspose.Words untuk Java API di proyek Java Anda.

## Opsi Penggabungan Dokumen

### Penambahan Sederhana

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Tambahkan dengan Opsi Format Impor

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Tambahkan ke Dokumen Kosong

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Tambahkan dengan Konversi Nomor Halaman

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Konversi bidang NUMPAGES
dstDoc.updatePageLayout(); // Perbarui tata letak halaman untuk penomoran yang benar
```

## Menangani Pengaturan Halaman yang Berbeda

Saat menambahkan dokumen dengan pengaturan halaman yang berbeda:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Pastikan pengaturan pengaturan halaman sesuai dengan dokumen tujuan
```

## Menggabungkan Dokumen dengan Gaya Berbeda

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Perilaku Gaya Cerdas

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Memasukkan Dokumen dengan DocumentBuilder

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

### Menghubungkan Header dan Footer

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Memutuskan Tautan Header dan Footer

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Kesimpulan

Aspose.Words untuk Java menyediakan alat yang fleksibel dan canggih untuk menggabungkan dan menambahkan dokumen, baik Anda perlu mempertahankan format, menangani pengaturan halaman yang berbeda, atau mengelola header dan footer. Bereksperimenlah dengan teknik-teknik ini untuk memenuhi kebutuhan pemrosesan dokumen spesifik Anda.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menggabungkan dokumen dengan gaya berbeda dengan mudah?

Untuk menggabungkan dokumen dengan gaya yang berbeda, gunakan `ImportFormatMode.USE_DESTINATION_STYLES` saat menambahkan.

### Bisakah saya mempertahankan penomoran halaman saat menambahkan dokumen?

Ya, Anda dapat mempertahankan penomoran halaman dengan menggunakan `convertNumPageFieldsToPageRef` metode dan memperbarui tata letak halaman.

### Apa itu Perilaku Gaya Cerdas?

Perilaku Gaya Cerdas membantu mempertahankan gaya yang konsisten saat menambahkan dokumen. Gunakan dengan `ImportFormatOptions` untuk hasil yang lebih baik.

### Bagaimana saya dapat menangani kotak teks saat menambahkan dokumen?

Mengatur `importFormatOptions.setIgnoreTextBoxes(false)` untuk menyertakan kotak teks selama penambahan.

### Bagaimana jika saya ingin menautkan/melepas tautan header dan footer antar dokumen?

Anda dapat menghubungkan header dan footer dengan `linkToPrevious(true)` atau putuskan tautannya dengan `linkToPrevious(false)` sesuai kebutuhan.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}