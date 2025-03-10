---
title: Menggunakan Watermark pada Dokumen di Aspose.Words untuk Java
linktitle: Menggunakan Tanda Air pada Dokumen
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Pelajari cara menambahkan tanda air ke dokumen di Aspose.Words untuk Java. Sesuaikan tanda air teks dan gambar untuk dokumen yang tampak profesional.
weight: 15
url: /id/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Watermark pada Dokumen di Aspose.Words untuk Java


## Pengantar Menambahkan Tanda Air ke Dokumen di Aspose.Words untuk Java

Dalam tutorial ini, kita akan membahas cara menambahkan tanda air ke dokumen menggunakan API Aspose.Words for Java. Tanda air merupakan cara yang berguna untuk memberi label pada dokumen dengan teks atau gambar untuk menunjukkan status, kerahasiaan, atau informasi relevan lainnya. Kami akan membahas tanda air teks dan gambar dalam panduan ini.

## Menyiapkan Aspose.Words untuk Java

Sebelum kita mulai menambahkan tanda air ke dokumen, kita perlu menyiapkan Aspose.Words untuk Java. Ikuti langkah-langkah berikut untuk memulai:

1.  Unduh Aspose.Words untuk Java dari[Di Sini](https://releases.aspose.com/words/java/).
2. Tambahkan pustaka Aspose.Words untuk Java ke proyek Java Anda.
3. Impor kelas yang diperlukan dalam kode Java Anda.

Sekarang setelah perpustakaannya disiapkan, mari kita lanjutkan dengan menambahkan tanda air.

## Menambahkan Tanda Air Teks

Tanda air teks merupakan pilihan umum saat Anda ingin menambahkan informasi tekstual ke dokumen Anda. Berikut cara menambahkan tanda air teks menggunakan Aspose.Words untuk Java:

```java
// Buat contoh Dokumen
Document doc = new Document("Document.docx");

// Tentukan TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//Atur teks dan opsi tanda air
doc.getWatermark().setText("Test", options);

// Simpan dokumen dengan tanda air
doc.save("DocumentWithWatermark.docx");
```

## Menambahkan Tanda Air Gambar

Selain tanda air teks, Anda juga dapat menambahkan tanda air gambar ke dokumen Anda. Berikut cara menambahkan tanda air gambar:

```java
// Buat contoh Dokumen
Document doc = new Document("Document.docx");

// Muat gambar untuk tanda air
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Atur ukuran dan posisi tanda air
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Tambahkan tanda air ke dokumen
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Simpan dokumen dengan tanda air
doc.save("DocumentWithImageWatermark.docx");
```

## Menyesuaikan Tanda Air

Anda dapat menyesuaikan tanda air dengan menyesuaikan tampilan dan posisinya. Untuk tanda air teks, Anda dapat mengubah fon, ukuran, warna, dan tata letak. Untuk tanda air gambar, Anda dapat mengubah ukuran dan posisinya seperti yang ditunjukkan pada contoh sebelumnya.

## Menghapus Tanda Air

Untuk menghapus tanda air dari dokumen, Anda dapat menggunakan kode berikut:

```java
// Buat contoh Dokumen
Document doc = new Document("DocumentWithWatermark.docx");

// Hapus tanda air
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Simpan dokumen tanpa tanda air
doc.save("DocumentWithoutWatermark.docx");
```


## Kesimpulan

Dalam tutorial ini, kita telah mempelajari cara menambahkan tanda air ke dokumen menggunakan Aspose.Words untuk Java. Baik Anda perlu menambahkan tanda air teks atau gambar, Aspose.Words menyediakan alat untuk menyesuaikan dan mengelolanya secara efisien. Anda juga dapat menghapus tanda air saat tidak lagi diperlukan, memastikan dokumen Anda bersih dan profesional.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara mengubah font tanda air teks?

 Untuk mengubah font tanda air teks, ubah fontnya`setFontFamily` properti di`TextWatermarkOptions`. Misalnya:

```java
options.setFontFamily("Times New Roman");
```

### Bisakah saya menambahkan beberapa tanda air ke satu dokumen?

 Ya, Anda dapat menambahkan beberapa tanda air ke dokumen dengan membuat beberapa`Shape` objek dengan pengaturan berbeda dan menambahkannya ke dokumen.

### Bisakah tanda air diputar?

 Ya, Anda dapat memutar tanda air dengan mengatur`setRotation` properti di`Shape` objek. Nilai positif memutar tanda air searah jarum jam, dan nilai negatif memutarnya berlawanan arah jarum jam.

### Bagaimana cara membuat tanda air semi-transparan?

 Untuk membuat tanda air semi-transparan, atur`setSemitransparent`properti untuk`true` di dalam`TextWatermarkOptions`.

### Bisakah saya menambahkan tanda air ke bagian tertentu dari suatu dokumen?

Ya, Anda dapat menambahkan tanda air ke bagian tertentu pada suatu dokumen dengan mengulangi bagian tersebut dan menambahkan tanda air ke bagian yang diinginkan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
