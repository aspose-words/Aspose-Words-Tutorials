---
date: 2026-02-16
description: Pelajari cara membuat kotak teks, menambahkan watermark kata, mengelompokkan
  beberapa bentuk, mengatur rasio aspek bentuk, dan menempatkan bentuk dalam sel tabel
  menggunakan Aspose.Words untuk Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Cara membuat kotak teks dan menggunakan Bentuk Dokumen di Aspose.Words untuk
  Java
url: /id/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Bentuk Dokumen di Aspose.Words untuk Java

## Pendahuluan tentang Menggunakan Bentuk Dokumen di Aspose.Words untuk Java

Dalam panduan komprehensif ini, **Anda akan belajar cara membuat kotak teks** dan bentuk kuat lainnya dengan Aspose.Words untuk Java. Bentuk memungkinkan Anda memperkaya dokumen Word dengan callout, tombol, watermark, SmartArt, dan lainnya—menjadikannya lebih menarik secara visual dan interaktif. Kami akan menelusuri contoh dunia nyata, mulai dari menyisipkan kotak teks sederhana hingga mengelompokkan beberapa bentuk, mengatur rasio aspek, dan menempatkan bentuk di dalam sel tabel.

## Jawaban Cepat
- **Apa cara utama untuk menambahkan kotak teks?** Gunakan `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Bisakah saya mengelompokkan beberapa bentuk?** Ya – buat `GroupShape` dan tambahkan bentuk anak.
- **Bagaimana cara mengunci atau membuka kunci rasio aspek sebuah bentuk?** Panggil `shape.setAspectRatioLocked(true/false)`.
- **Apakah memungkinkan menambahkan watermark dengan bentuk?** Tentu – sisipkan `Shape` dengan `TEXT_PLAIN_TEXT` dan atur isian/garisnya.
- **Apakah diagram SmartArt bekerja dengan Aspose.Words?** Ya – deteksi dengan `shape.hasSmartArt()` dan perbarui melalui `shape.updateSmartArtDrawing()`.

## Apa itu kotak teks dan mengapa membuat bentuk kotak teks?

Kotak teks adalah wadah yang dapat menampung teks terformat, gambar, atau bentuk lain. Menggunakan **membuat kotak teks** dalam otomatisasi Anda memungkinkan penempatan konten mengambang di mana saja pada halaman, cocok untuk anotasi, callout, atau elemen dekoratif tanpa mengubah alur utama dokumen.

## Cara menambahkan bentuk

Sebelum kita masuk ke kode, pastikan Aspose.Words untuk Java sudah direferensikan dalam proyek Anda. Jika belum menambahkannya, unduh perpustakaan dari situs resmi:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Menambahkan Bentuk ke Dokumen

## Cara mengelompokkan beberapa bentuk

`GroupShape` memungkinkan Anda memperlakukan beberapa bentuk individu sebagai satu unit—berguna untuk memindahkan atau memutar mereka bersama.

### Menyisipkan GroupShape

Berikut contoh lengkap yang membuat grup, menambahkan dua bentuk berbeda, dan menyisipkan grup ke dalam dokumen.

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## Cara membuat kotak teks (create text box)

### Menyisipkan Bentuk Kotak Teks

Metode `insertShape` memudahkan penambahan kotak teks. Contoh di bawah menunjukkan dua cara memposisikan dan memutar kotak teks.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Cara mengatur rasio aspek bentuk

### Mengelola Rasio Aspek

Kadang Anda memerlukan bentuk yang meregang tanpa mempertahankan proporsi aslinya. Potongan kode berikut memperlihatkan cara membuka kunci rasio aspek pada bentuk gambar.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Cara menempatkan bentuk di dalam sel tabel

### Menempatkan Bentuk di Dalam Sel Tabel

Berikut contoh langkah demi langkah yang membangun tabel, lalu menyisipkan bentuk watermark yang diposisikan relatif terhadap halaman tetapi juga dapat ditempatkan di dalam sel.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Bekerja dengan Bentuk SmartArt

### Mendeteksi Bentuk SmartArt

Anda dapat secara programatis menemukan objek SmartArt dalam dokumen menggunakan metode `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Memperbarui Gambar SmartArt

Setelah menemukan bentuk SmartArt, Anda dapat menyegarkan data gambar internalnya dengan `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Kesimpulan

Dalam panduan ini, kami telah membahas cara **membuat kotak teks** objek, mengelompokkan beberapa bentuk, menyesuaikan rasio aspek, menyematkan bentuk di dalam sel tabel, menambahkan watermark, dan bekerja dengan diagram SmartArt menggunakan Aspose.Words untuk Java. Teknik-teknik ini memberi Anda kemampuan untuk membangun dokumen Word yang kaya format, interaktif secara programatik.

## FAQ's

### Apa itu Aspose.Words untuk Java?

Aspose.Words untuk Java adalah perpustakaan Java yang memungkinkan pengembang membuat, memodifikasi, dan mengonversi dokumen Word secara programatik. Ia menyediakan berbagai fitur dan alat untuk bekerja dengan dokumen dalam berbagai format.

### Bagaimana cara mengunduh Aspose.Words untuk Java?

Anda dapat mengunduh Aspose.Words untuk Java dari situs Aspose dengan mengikuti tautan ini: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Apa manfaat menggunakan bentuk dokumen?

Bentuk dokumen menambahkan elemen visual dan interaktivitas ke dokumen Anda, membuatnya lebih menarik dan informatif. Dengan bentuk, Anda dapat membuat callout, tombol, gambar, watermark, dan lainnya, meningkatkan pengalaman pengguna secara keseluruhan.

### Bisakah saya menyesuaikan tampilan bentuk?

Ya, Anda dapat menyesuaikan tampilan bentuk dengan mengatur properti seperti ukuran, posisi, rotasi, dan warna isi. Aspose.Words untuk Java menyediakan opsi yang luas untuk penyesuaian bentuk.

### Apakah Aspose.Words untuk Java kompatibel dengan SmartArt?

Ya, Aspose.Words untuk Java mendukung bentuk SmartArt, memungkinkan Anda bekerja dengan diagram dan grafik kompleks dalam dokumen Anda.

## Frequently Asked Questions

**Q: Bisakah saya menggabungkan kotak teks dengan gambar di dalam bentuk yang sama?**  
A: Ya. Sisipkan gambar ke dalam bentuk kotak teks menggunakan `builder.insertImage()` setelah membuat bentuk, lalu sesuaikan tata letaknya sesuai kebutuhan.

**Q: Bagaimana cara memastikan watermark muncul di belakang semua konten dokumen?**  
A: Atur `WrapType` bentuk menjadi `NONE` dan sesuaikan `RelativeHorizontalPosition` serta `RelativeVerticalPosition` menjadi `PAGE`. Ini menempatkan watermark di belakang alur utama.

**Q: Apakah memungkinkan memberi animasi pada bentuk yang dikelompokkan di Word?**  
A: Meskipun Aspose.Words dapat membuat dan mengelompokkan bentuk, fitur animasi tidak didukung karena bergantung pada kemampuan UI Word.

**Q: Versi Aspose.Words berapa yang diperlukan untuk dukungan SmartArt?**  
A: Deteksi dan pembaruan SmartArt tersedia mulai dari Aspose.Words 20.9 untuk Java dan versi selanjutnya.

**Q: Apakah perpustakaan ini menangani dokumen besar dengan banyak bentuk secara efisien?**  
A: Ya. Gunakan `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` atau yang lebih tinggi untuk meningkatkan kinerja pada dokumen dengan banyak bentuk.

---

**Terakhir Diperbarui:** 2026-02-16  
**Diuji Dengan:** Aspose.Words untuk Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}