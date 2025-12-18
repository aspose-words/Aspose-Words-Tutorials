---
date: 2025-12-18
description: Pelajari cara menambahkan watermark ke dokumen dengan Aspose.Words untuk
  Java, termasuk contoh watermark gambar, mengubah warna watermark, mengatur transparansi
  watermark, dan menghapus watermark dari dokumen.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Cara Menambahkan Watermark ke Dokumen Menggunakan Aspose.Words untuk Java
url: /id/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menambahkan Watermark ke Dokumen Menggunakan Aspose.Words untuk Java

## Pendahuluan tentang Menambahkan Watermark ke Dokumen dalam Aspose.Words untuk Java

Dalam tutorial ini Anda akan belajar **cara menambahkan watermark** ke dokumen Word dengan Aspose.Words untuk Java. Watermark adalah cara cepat untuk menandai file sebagai rahasia, draf, atau disetujui, dan dapat berbasis teks atau gambar. Kami akan membahas cara menyiapkan pustaka, membuat watermark teks dan gambar, menyesuaikan tampilan mereka (termasuk mengubah warna watermark dan mengatur transparansi watermark), serta bahkan menghapus watermark dari dokumen ketika tidak lagi diperlukan.

## Jawaban Cepat
- **Apa itu watermark?** Sebuah lapisan semi‑transparan (teks atau gambar) yang muncul di belakang konten utama dokumen.  
- **Bisakah saya menambahkan beberapa watermark?** Ya – buat beberapa objek `Shape` dan tambahkan masing‑masing ke bagian yang diinginkan.  
- **Bagaimana cara mengubah warna watermark?** Sesuaikan properti `Color` dalam `TextWatermarkOptions`.  
- **Apakah ada contoh watermark gambar?** Lihat bagian “Menambahkan Watermark Gambar” di bawah.  
- **Apakah saya memerlukan lisensi untuk menghapus watermark?** Lisensi Aspose.Words yang valid diperlukan untuk penggunaan produksi.

## Menyiapkan Aspose.Words untuk Java

Sebelum kita mulai menambahkan watermark ke dokumen, kita perlu menyiapkan Aspose.Words untuk Java. Ikuti langkah‑langkah berikut untuk memulai:

1. Unduh Aspose.Words untuk Java dari [here](https://releases.aspose.com/words/java/).  
2. Tambahkan pustaka Aspose.Words untuk Java ke proyek Java Anda.  
3. Impor kelas‑kelas yang diperlukan dalam kode Java Anda.

Setelah pustaka siap, mari kita selami pembuatan watermark yang sebenarnya.

## Menambahkan Watermark Teks

Watermark teks adalah pilihan umum ketika Anda ingin menambahkan informasi teks ke dokumen Anda. Berikut cara menambahkan watermark teks menggunakan Aspose.Words untuk Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Mengapa ini penting:** Dengan menyesuaikan `setFontFamily`, `setFontSize`, dan `setColor` Anda dapat **mengubah warna watermark** agar sesuai dengan merek Anda, dan `setSemitransparent(true)` memungkinkan Anda **mengatur transparansi watermark** untuk efek yang halus.

## Menambahkan Watermark Gambar

Selain watermark teks, Anda juga dapat menambahkan watermark gambar ke dokumen Anda. Di bawah ini adalah **contoh watermark gambar** yang menunjukkan cara menyematkan logo atau stempel PNG:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Anda dapat mengulang blok ini dengan gambar atau posisi yang berbeda untuk **menambahkan beberapa watermark** ke satu file.

## Menyesuaikan Watermark

Anda dapat menyesuaikan watermark dengan mengatur tampilan dan posisinya. Untuk watermark teks, Anda dapat mengubah font, ukuran, warna, dan tata letak. Untuk watermark gambar, Anda dapat memodifikasi ukuran, rotasi, dan perataan seperti yang ditunjukkan pada contoh sebelumnya.

## Menghapus Watermark

Jika Anda perlu **menghapus konten watermark** dari dokumen, kode berikut akan mengiterasi semua shape dan menghapus yang diidentifikasi sebagai watermark:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Kasus Penggunaan Umum & Tips

- **Draf rahasia:** Terapkan watermark teks semi‑transparan seperti “CONFIDENTIAL”.  
- **Branding:** Gunakan watermark gambar yang berisi logo perusahaan Anda.  
- **Watermark khusus bagian:** Loop melalui `doc.getSections()` dan tambahkan watermark hanya ke bagian yang Anda pilih.  
- **Tip performa:** Gunakan kembali instance `TextWatermarkOptions` yang sama saat menerapkan watermark yang sama ke banyak dokumen.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara mengubah font watermark teks?

Untuk mengubah font watermark teks, ubah properti `setFontFamily` dalam `TextWatermarkOptions`. Misalnya:

```java
options.setFontFamily("Times New Roman");
```

### Bisakah saya menambahkan beberapa watermark ke satu dokumen?

Ya, Anda dapat menambahkan beberapa watermark ke dokumen dengan membuat beberapa objek `Shape` dengan pengaturan berbeda dan menambahkannya ke dokumen.

### Apakah memungkinkan memutar watermark?

Ya, Anda dapat memutar watermark dengan mengatur properti `setRotation` pada objek `Shape`. Nilai positif memutar watermark searah jarum jam, dan nilai negatif memutar berlawanan arah jarum jam.

### Bagaimana cara membuat watermark semi‑transparan?

Untuk membuat watermark semi‑transparan, atur properti `setSemitransparent` menjadi `true` dalam `TextWatermarkOptions`.

### Bisakah saya menambahkan watermark ke bagian tertentu dari dokumen?

Ya, Anda dapat menambahkan watermark ke bagian tertentu dari dokumen dengan mengiterasi bagian‑bagian tersebut dan menambahkan watermark ke bagian yang diinginkan.

---

**Terakhir Diperbarui:** 2025-12-18  
**Diuji Dengan:** Aspose.Words for Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}