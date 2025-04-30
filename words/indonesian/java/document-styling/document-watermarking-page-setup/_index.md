---
"description": "Pelajari cara menerapkan tanda air dan mengatur konfigurasi halaman dengan Aspose.Words untuk Java. Panduan lengkap dengan kode sumber."
"linktitle": "Penandaan Air Dokumen dan Pengaturan Halaman"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Penandaan Air Dokumen dan Pengaturan Halaman"
"url": "/id/java/document-styling/document-watermarking-page-setup/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Penandaan Air Dokumen dan Pengaturan Halaman

## Perkenalan

Dalam ranah manipulasi dokumen, Aspose.Words untuk Java merupakan alat yang ampuh, yang memungkinkan pengembang memegang kendali atas setiap aspek pemrosesan dokumen. Dalam panduan komprehensif ini, kita akan membahas seluk-beluk pemberian tanda air pada dokumen dan pengaturan halaman menggunakan Aspose.Words untuk Java. Apakah Anda seorang pengembang berpengalaman atau baru saja terjun ke dunia pemrosesan dokumen Java, panduan langkah demi langkah ini akan membekali Anda dengan pengetahuan dan kode sumber yang Anda butuhkan.

## Penandaan Air Dokumen

### Menambahkan Tanda Air

Menambahkan tanda air ke dokumen dapat menjadi hal penting untuk memberi merek atau mengamankan konten Anda. Aspose.Words untuk Java mempermudah tugas ini. Berikut caranya:

```java
// Muat dokumen
Document doc = new Document("document.docx");

// Buat tanda air
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// Posisikan tanda air
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// Masukkan tanda air
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Simpan dokumen
doc.save("document_with_watermark.docx");
```

### Menyesuaikan Tanda Air

Anda dapat menyesuaikan tanda air lebih lanjut dengan menyesuaikan font, ukuran, warna, dan rotasi. Fleksibilitas ini memastikan tanda air Anda sesuai dengan gaya dokumen Anda dengan sempurna.

## Pengaturan Halaman

### Ukuran dan Orientasi Halaman

Pengaturan halaman sangat penting dalam pemformatan dokumen. Aspose.Words untuk Java menawarkan kontrol penuh atas ukuran dan orientasi halaman:

```java
// Muat dokumen
Document doc = new Document("document.docx");

// Atur ukuran halaman ke A4
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// Ubah orientasi halaman menjadi lanskap
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// Simpan dokumen yang dimodifikasi
doc.save("formatted_document.docx");
```

### Margin dan Penomoran Halaman

Kontrol yang tepat atas margin dan penomoran halaman sangat penting untuk dokumen profesional. Raihlah ini dengan Aspose.Words untuk Java:

```java
// Muat dokumen
Document doc = new Document("document.docx");

// Mengatur margin
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// Aktifkan penomoran halaman
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// Simpan dokumen yang diformat
doc.save("formatted_document.docx");
```

## Tanya Jawab Umum

### Bagaimana cara menghapus tanda air dari dokumen?

Untuk menghapus tanda air dari dokumen, Anda dapat menelusuri bentuk dokumen dan menghapus bentuk yang mewakili tanda air. Berikut cuplikannya:

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### Bisakah saya menambahkan beberapa tanda air ke satu dokumen?

Ya, Anda dapat menambahkan beberapa tanda air ke dokumen dengan membuat objek Bentuk tambahan dan memposisikannya sesuai kebutuhan.

### Bagaimana cara mengubah ukuran halaman menjadi legal dalam orientasi lanskap?

Untuk mengatur ukuran halaman menjadi legal dalam orientasi lanskap, ubah lebar dan tinggi halaman sebagai berikut:

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### Apa font default untuk tanda air?

Font default untuk tanda air adalah Calibri dengan ukuran font 36.

### Bagaimana cara menambahkan nomor halaman mulai dari halaman tertentu?

Anda dapat mencapainya dengan mengatur nomor halaman awal dalam dokumen Anda sebagai berikut:

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### Bagaimana cara meratakan tengah teks di header atau footer?

Anda dapat meratakan tengah teks di header atau footer dengan menggunakan metode setAlignment pada objek Paragraph di dalam header atau footer.

## Kesimpulan

Dalam panduan lengkap ini, kami telah menjelajahi seni pemberian tanda air pada dokumen dan pengaturan halaman menggunakan Aspose.Words untuk Java. Berbekal potongan kode sumber dan wawasan yang disediakan, kini Anda memiliki alat untuk memanipulasi dan memformat dokumen Anda dengan cermat. Aspose.Words untuk Java memberdayakan Anda untuk membuat dokumen bermerek profesional yang disesuaikan dengan spesifikasi persis Anda.

Menguasai manipulasi dokumen merupakan keterampilan yang berharga bagi para pengembang, dan Aspose.Words untuk Java adalah teman tepercaya Anda dalam perjalanan ini. Mulailah membuat dokumen yang menakjubkan hari ini!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}