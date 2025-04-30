---
"description": "Buka Kekuatan Bentuk Dokumen di Aspose.Words untuk Java. Pelajari Cara Membuat Dokumen yang Menarik Secara Visual dengan Contoh Langkah demi Langkah."
"linktitle": "Menggunakan Bentuk Dokumen"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menggunakan Bentuk Dokumen di Aspose.Words untuk Java"
"url": "/id/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Bentuk Dokumen di Aspose.Words untuk Java


## Pengantar Penggunaan Bentuk Dokumen di Aspose.Words untuk Java

Dalam panduan lengkap ini, kita akan menyelami dunia bentuk dokumen di Aspose.Words untuk Java. Bentuk merupakan elemen penting dalam membuat dokumen yang menarik secara visual dan interaktif. Baik Anda perlu menambahkan keterangan, tombol, gambar, atau tanda air, Aspose.Words untuk Java menyediakan alat untuk melakukannya secara efisien. Mari kita jelajahi cara menggunakan bentuk ini langkah demi langkah dengan contoh kode sumber.

## Memulai dengan Bentuk Dokumen

Sebelum kita mulai membuat kode, mari kita siapkan lingkungan kita. Pastikan Anda telah mengintegrasikan Aspose.Words untuk Java ke dalam proyek Anda. Jika belum, Anda dapat mengunduhnya dari situs web Aspose [Unduh Aspose.Words untuk Java](https://releases.aspose.com/words/java/)

## Menambahkan Bentuk ke Dokumen

### Memasukkan GroupShape

A `GroupShape` memungkinkan Anda mengelompokkan beberapa bentuk bersama-sama. Berikut cara membuat dan menyisipkan `GroupShape`:

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

### Memasukkan Bentuk Kotak Teks

Untuk menyisipkan bentuk kotak teks, Anda dapat menggunakan `insertShape` metode seperti yang ditunjukkan pada contoh di bawah ini:

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

## Memanipulasi Properti Bentuk

### Mengelola Rasio Aspek

Anda dapat mengontrol apakah rasio aspek suatu bentuk terkunci atau tidak. Berikut cara membuka kunci rasio aspek suatu bentuk:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Menempatkan Bentuk di Sel Tabel

Jika Anda perlu menempatkan bentuk di dalam sel tabel, Anda dapat melakukannya dengan kode berikut:

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
watermark.isLayoutInCell(true); // Menampilkan bentuk di luar sel tabel jika akan ditempatkan ke dalam sel.
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

Anda dapat mendeteksi bentuk SmartArt dalam dokumen menggunakan kode berikut:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Memperbarui Gambar SmartArt

Untuk memperbarui gambar SmartArt dalam dokumen, gunakan kode berikut:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Kesimpulan

Dalam panduan ini, kami telah menjelajahi dunia bentuk dokumen di Aspose.Words untuk Java. Anda telah mempelajari cara menambahkan berbagai bentuk ke dokumen Anda, memanipulasi propertinya, dan bekerja dengan bentuk SmartArt. Dengan pengetahuan ini, Anda dapat membuat dokumen yang menarik secara visual dan interaktif dengan mudah.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk Java?

Aspose.Words untuk Java adalah pustaka Java yang memungkinkan pengembang membuat, memodifikasi, dan mengonversi dokumen Word secara terprogram. Pustaka ini menyediakan berbagai fitur dan alat untuk bekerja dengan dokumen dalam berbagai format.

### Bagaimana cara mengunduh Aspose.Words untuk Java?

Anda dapat mengunduh Aspose.Words untuk Java dari situs web Aspose dengan mengikuti tautan ini: [Unduh Aspose.Words untuk Java](https://releases.aspose.com/words/java/)

### Apa keuntungan menggunakan bentuk dokumen?

Bentuk dokumen menambahkan elemen visual dan interaktivitas ke dokumen Anda, sehingga membuatnya lebih menarik dan informatif. Dengan bentuk, Anda dapat membuat keterangan, tombol, gambar, tanda air, dan banyak lagi, yang akan meningkatkan pengalaman pengguna secara keseluruhan.

### Bisakah saya menyesuaikan tampilan bentuk?

Ya, Anda dapat menyesuaikan tampilan bentuk dengan menyesuaikan propertinya seperti ukuran, posisi, rotasi, dan warna isian. Aspose.Words untuk Java menyediakan opsi yang luas untuk penyesuaian bentuk.

### Apakah Aspose.Words untuk Java kompatibel dengan SmartArt?

Ya, Aspose.Words untuk Java mendukung bentuk SmartArt, yang memungkinkan Anda bekerja dengan diagram dan grafik kompleks dalam dokumen Anda.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}