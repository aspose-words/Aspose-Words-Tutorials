---
date: 2025-12-14
description: Pelajari cara **menyisipkan bentuk gambar** dengan Aspose.Words untuk
  Java. Panduan ini menunjukkan cara menambahkan bentuk, membuat bentuk kotak teks,
  menempatkan bentuk dalam tabel, mengatur rasio aspek bentuk, dan menambahkan bentuk
  penjelasan.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Menggunakan Bentuk Dokumen di Aspose.Words untuk Java
url: /id/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara **menyisipkan bentuk gambar** dengan Aspose.Words untuk Java

Dalam tutorial komprehensif ini Anda akan menemukan cara **menyisipkan bentuk gambar** ke dalam dokumen Word menggunakan Aspose.Words untuk Java. Baik Anda membuat laporan, materi pemasaran, atau formulir interaktif, bentuk memungkinkan Anda menambahkan callout, tombol, kotak teks, watermark, bahkan SmartArt. Kami akan membahas setiap langkah, menjelaskan mengapa Anda menggunakan bentuk tertentu, dan menyediakan potongan kode yang siap dijalankan.

## Jawaban Cepat
- **Apa cara utama untuk menambahkan sebuah bentuk?** Gunakan `DocumentBuilder.insertShape` atau buat instance `Shape` dan tambahkan ke pohon dokumen.  
- **Bisakah saya menyisipkan gambar sebagai bentuk?** Ya – panggil `builder.insertImage` dan kemudian perlakukan `Shape` yang dikembalikan seperti bentuk lainnya.  
- **Bagaimana cara menjaga rasio aspek bentuk?** Atur `shape.setAspectRatioLocked(true)` atau `false` sesuai kebutuhan Anda.  
- **Apakah memungkinkan untuk mengelompokkan bentuk?** Tentu – bungkus mereka dalam `GroupShape` dan sisipkan grup sebagai satu node.  
- **Apakah diagram SmartArt bekerja dengan Aspose.Words?** Ya, Anda dapat mendeteksi dan memperbarui bentuk SmartArt secara programatis.

## Apa itu **insert image shape**?
*Bentuk gambar* adalah elemen visual yang menyimpan grafik raster atau vektor di dalam dokumen Word. Di Aspose.Words, gambar direpresentasikan oleh objek `Shape`, memberi Anda kontrol penuh atas ukuran, posisi, rotasi, dan pembungkusannya.

## Mengapa menggunakan bentuk dalam dokumen Anda?
- **Dampak visual:** Bentuk menarik perhatian ke informasi penting.  
- **Interaktivitas:** Tombol dan callout dapat ditautkan ke URL atau bookmark.  
- **Fleksibilitas tata letak:** Posisi grafik secara tepat dengan koordinat absolut atau relatif.  
- **Otomatisasi:** Hasilkan tata letak kompleks tanpa penyuntingan manual.

## Prasyarat
- Java Development Kit (JDK 8 atau lebih tinggi)  
- Perpustakaan Aspose.Words untuk Java (unduh dari situs resmi)  
- Pengetahuan dasar tentang Java dan pemrograman berorientasi objek  

Anda dapat mengunduh perpustakaan di sini: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Cara **menambahkan bentuk** – Menyisipkan GroupShape
`GroupShape` memungkinkan Anda memperlakukan beberapa bentuk sebagai satu unit. Ini berguna untuk memindahkan atau memformat beberapa elemen sekaligus.

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

## Membuat **bentuk kotak teks**
Kotak teks adalah wadah yang dapat menampung teks terformat. Anda juga dapat memutarnya untuk tampilan yang dinamis.

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

## Mengatur **rasio aspek bentuk**
Terkadang Anda perlu bentuk yang dapat meregang bebas, kadang Anda ingin mempertahankan proporsi aslinya. Mengontrol rasio aspek sangat mudah.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Menempatkan **bentuk dalam tabel**
Menyisipkan bentuk di dalam sel tabel dapat berguna untuk tata letak laporan. Contoh di bawah ini membuat tabel dan kemudian menyisipkan bentuk bergaya watermark yang melintasi seluruh halaman.

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

## Menambahkan **bentuk callout**
Bentuk callout sangat cocok untuk menyoroti catatan atau peringatan. Walaupun kode di atas sudah menunjukkan `ACCENT_BORDER_CALLOUT_1`, Anda dapat mengganti `ShapeType` ke varian callout lain sesuai desain Anda.

## Bekerja dengan Bentuk SmartArt

### Mendeteksi Bentuk SmartArt
Diagram SmartArt dapat diidentifikasi secara programatis, memungkinkan Anda memproses atau menggantinya sesuai kebutuhan.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Memperbarui Gambar SmartArt
Setelah terdeteksi, Anda dapat menyegarkan grafik SmartArt untuk mencerminkan perubahan data apa pun.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Masalah Umum & Tips
- **Bentuk tidak muncul:** Pastikan bentuk disisipkan setelah node target menggunakan `builder.insertNode`.  
- **Rotasi tidak terduga:** Ingat bahwa rotasi diterapkan di sekitar pusat bentuk; sesuaikan `setLeft`/`setTop` bila diperlukan.  
- **Rasio aspek terkunci:** Secara default, banyak bentuk mengunci rasio aspeknya; panggil `setAspectRatioLocked(false)` untuk meregang bebas.  
- **Deteksi SmartArt gagal:** Pastikan Anda menggunakan versi Aspose.Words yang mendukung SmartArt (v24+).

## Pertanyaan yang Sering Diajukan

**T: Apa itu Aspose.Words untuk Java?**  
J: Aspose.Words untuk Java adalah perpustakaan Java yang memungkinkan pengembang membuat, memodifikasi, dan mengonversi dokumen Word secara programatis. Ia menyediakan berbagai fitur dan alat untuk bekerja dengan dokumen dalam berbagai format.

**T: Bagaimana cara mengunduh Aspose.Words untuk Java?**  
J: Anda dapat mengunduh Aspose.Words untuk Java dari situs Aspose dengan mengikuti tautan ini: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**T: Apa manfaat menggunakan bentuk dokumen?**  
J: Bentuk dokumen menambahkan elemen visual dan interaktivitas ke dokumen Anda, menjadikannya lebih menarik dan informatif. Dengan bentuk, Anda dapat membuat callout, tombol, gambar, watermark, dan lainnya, meningkatkan pengalaman pengguna secara keseluruhan.

**T: Bisakah saya menyesuaikan tampilan bentuk?**  
J: Ya, Anda dapat menyesuaikan tampilan bentuk dengan mengatur properti seperti ukuran, posisi, rotasi, dan warna isi. Aspose.Words untuk Java menyediakan opsi yang luas untuk kustomisasi bentuk.

**T: Apakah Aspose.Words untuk Java kompatibel dengan SmartArt?**  
J: Ya, Aspose.Words untuk Java mendukung bentuk SmartArt, memungkinkan Anda bekerja dengan diagram dan grafik kompleks dalam dokumen Anda.

---

**Terakhir Diperbarui:** 2025-12-14  
**Diuji Dengan:** Aspose.Words untuk Java 24.12 (terbaru)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}