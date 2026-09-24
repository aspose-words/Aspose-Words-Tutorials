---
date: 2026-02-19
description: Pelajari cara membuat dokumen dengan watermark menggunakan Aspose.Words
  untuk Java dan menambahkan watermark gambar Java untuk dokumen yang tampak profesional.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Buat dokumen dengan watermark menggunakan Aspose.Words untuk Java
url: /id/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

 translation.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen dengan watermark menggunakan Aspose.Words untuk Java

Dalam tutorial ini Anda akan **membuat dokumen dengan watermark** menggunakan API Aspose.Words untuk Java. Watermark—baik berupa teks maupun gambar—membantu Anda memberi label pada file sebagai rahasia, draf, atau disetujui, dan dapat diterapkan secara programatik pada dokumen Word apa pun. Kami akan memandu Anda menyiapkan pustaka, menambahkan watermark teks dan gambar, menyesuaikan tampilannya, serta menghapusnya ketika tidak lagi diperlukan.

## Jawaban Cepat
- **Apa yang dilakukan watermark?** Watermark menempatkan teks atau gambar di setiap halaman untuk menyampaikan status atau merek.  
- **Pustaka mana yang menambahkan watermark di Java?** Aspose.Words untuk Java menyediakan dukungan watermark bawaan.  
- **Bisakah saya menambahkan watermark gambar?** Ya—gunakan kelas `Shape` dan pendekatan `add image watermark java`.  
- **Apakah watermark semi‑transparan?** Anda dapat mengontrol opasitas melalui `setSemitransparent` untuk watermark teks.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi komersial diperlukan untuk produksi.

## Apa itu watermark dan mengapa menggunakannya?

Watermark adalah lapisan tipis—teks atau grafis—yang ditambahkan ke setiap halaman dokumen. Umumnya digunakan untuk menunjukkan **kerahasiaan**, **status draf**, atau **merek** tanpa mengubah konten utama. Menambahkan watermark secara programatik memastikan konsistensi pada sejumlah besar file dan menghemat waktu dibandingkan dengan penyuntingan manual.

## Menyiapkan Aspose.Words untuk Java

Sebelum menambahkan watermark, pastikan pustaka sudah siap di proyek Anda:

1. Unduh Aspose.Words untuk Java dari [here](https://releases.aspose.com/words/java/).  
2. Tambahkan JAR yang diunduh (atau dependensi Maven/Gradle) ke classpath proyek Anda.  
3. Impor kelas yang diperlukan dalam file sumber Java Anda:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Setelah pustaka terpasang, mari kita selami kode watermark yang sesungguhnya.

## Cara menambahkan watermark teks

Watermark teks ideal untuk memberi label dokumen sebagai “CONFIDENTIAL” atau “DRAFT”. Cuplikan berikut menunjukkan cara **membuat dokumen dengan watermark** yang bersih menggunakan `TextWatermarkOptions`.

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

### Menyesuaikan watermark teks
- **Font family & size** – ubah `setFontFamily` dan `setFontSize`.  
- **Color** – gunakan `java.awt.Color` apa saja.  
- **Layout** – pilih `HORIZONTAL`, `DIAGONAL`, dll.  
- **Transparency** – aktifkan `setSemitransparent(true)` untuk tampilan yang lebih ringan.

## Cara menambahkan watermark gambar (add image watermark java)

Watermark gambar sempurna untuk logo atau grafis khusus. Di bawah ini contoh **add image watermark java** yang menyisipkan file PNG ke tengah setiap halaman.

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

### Tips untuk watermark gambar
- **Resize** menggunakan `setWidth` / `setHeight` agar sesuai dengan halaman.  
- **Position** dapat dipusatkan atau disejajarkan ke margin mana pun menggunakan `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparency** dapat diterapkan dengan menyesuaikan kanal alfa gambar sebelum dimuat.

## Cara menghapus watermark

Ketika sebuah dokumen tidak lagi memerlukan watermark, Anda dapat menghapusnya secara programatik. Kode di bawah ini menelusuri semua shape dan menghapus yang namanya mengandung “Watermark”.

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

## Kesulitan umum dan pemecahan masalah

- **Missing watermark after saving** – pastikan Anda memanggil `doc.save()` setelah mengatur watermark.  
- **Image not appearing** – periksa kembali jalur gambar dan pastikan file berformat yang didukung (PNG, JPEG, BMP).  
- **Transparency not applied** – `setSemitransparent(true)` hanya berfungsi untuk watermark teks; untuk gambar, edit kanal alfa PNG terlebih dahulu.  
- **Multiple sections** – jika dokumen Anda memiliki beberapa bagian, tambahkan watermark ke body masing‑masing bagian atau gunakan `doc.getWatermark().setText(...)` yang berlaku secara global.

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara mengubah font watermark teks?**  
A: Modifikasi properti `setFontFamily` pada `TextWatermarkOptions`, misalnya `options.setFontFamily("Times New Roman");`.

**Q: Bisakah saya menambahkan beberapa watermark pada satu dokumen?**  
A: Ya. Buat beberapa objek `Shape` (untuk gambar) atau panggil `doc.getWatermark().setText(...)` dengan opsi berbeda untuk setiap watermark.

**Q: Apakah memungkinkan memutar watermark?**  
A: Untuk watermark gambar, atur rotasi pada objek `Shape` dengan `watermark.setRotation(angle)`. Untuk watermark teks, gunakan properti `setLayout` (misalnya `WatermarkLayout.DIAGONAL`).

**Q: Bagaimana cara membuat watermark semi‑transparent?**  
A: Setel `options.setSemitransparent(true)` pada `TextWatermarkOptions`. Untuk gambar, sesuaikan opasitas gambar sebelum dimuat.

**Q: Bisakah saya menambahkan watermark ke bagian tertentu dari dokumen?**  
A: Ya. Iterasi melalui `doc.getSections()` dan tambahkan watermark hanya pada bagian yang diinginkan.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Terakhir Diperbarui:** 2026-02-19  
**Diuji Dengan:** Aspose.Words untuk Java 24.12 (latest)  
**Penulis:** Aspose