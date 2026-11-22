---
category: general
date: 2026-11-22
description: Pelajari cara menambahkan bentuk ke Word menggunakan Aspose.Words for
  Java – sisipkan sebuah persegi panjang dan sembunyikan secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: id
lastmod: 2026-11-22
og_description: Tambahkan bentuk ke Word menggunakan Aspose.Words untuk Java. Tutorial
  ini menunjukkan cara menyisipkan persegi panjang, menyembunyikan bentuk, dan menyimpan
  dokumen.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Tambahkan bentuk ke Word dengan Aspose.Words – Panduan Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Cara menambahkan bentuk ke dokumen Word dengan Aspose.Words untuk Java
url: /id/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan shape ke dokumen Word dengan Aspose.Words untuk Java

Jika Anda perlu **menambahkan shape ke Word** secara programatis, Aspose.Words untuk Java mempermudahnya. Dalam panduan ini Anda akan belajar **cara menyisipkan shape**, mengontrol visibilitasnya, dan **cara menyembunyikan shape** sehingga file akhir terlihat persis seperti yang Anda harapkan.

Anda akan menjalani contoh lengkap yang dapat dijalankan yang memuat `.docx` yang ada, menyisipkan sebuah persegi panjang, menyembunyikannya, dan menyimpan hasilnya. Tidak diperlukan skrip eksternal atau langkah manual, dan tutorial ini mencakup variasi umum seperti membuat dokumen baru dari awal atau menyembunyikan shape hanya saat mencetak.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java 17 (atau lebih baru) terpasang – versi sebelumnya masih dapat bekerja tetapi LTS terbaru memberikan kinerja yang lebih baik.  
* Maven 3.8+ untuk manajemen dependensi.  
* Lisensi Aspose.Words untuk Java yang valid (evaluasi gratis dapat digunakan untuk belajar).  
* IDE atau editor teks pilihan Anda (misalnya, IntelliJ IDEA, VS Code).

## Langkah 1: Tambahkan Aspose.Words ke proyek Maven Anda

Tambahkan dependensi berikut ke `pom.xml` Anda. Ini akan mengambil versi stabil terbaru (per November 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Tip profesional:** Gunakan klausa `<scope>provided</scope>` jika Anda berencana mendistribusikan JAR dengan logika lisensi Anda sendiri.

## Tambahkan shape ke Word – menginisialisasi dokumen

Langkah fungsional pertama adalah memperoleh objek `Document`. Anda dapat memuat file yang ada atau membuat yang baru.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Mengapa ini penting*: Kelas `Document` adalah titik masuk untuk semua manipulasi Word. Memuat file yang ada mempertahankan gaya, header, dan footer, sementara dokumen baru memberi Anda kanvas bersih.

## Cara menyisipkan shape dalam dokumen Word

Selanjutnya, buat `DocumentBuilder` untuk memodifikasi konten dokumen. Builder menyediakan metode untuk menyisipkan teks, tabel, dan **shape**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

Pemanggilan `insertShape` mengembalikan objek `Shape` yang dapat Anda konfigurasikan lebih lanjut (warna, border, teks, dll.). Dimensi dinyatakan dalam poin (1 pt = 1/72 in).

*Mengapa Anda mungkin menggunakan persegi panjang*: Persegi panjang adalah kontainer paling umum untuk anotasi, watermark, atau placeholder. Anda dapat mengganti `ShapeType.RECTANGLE` dengan `ShapeType.ELLIPSE`, `ShapeType.LINE`, dll., untuk memenuhi kebutuhan visual yang berbeda.

## Cara menyembunyikan shape di Word

Terkadang Anda memerlukan shape yang ada untuk perhitungan tata letak tetapi tidak muncul dalam rendering akhir. Aspose.Words menyediakan metode `setHidden(true)` untuk mencapainya.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Flag tersembunyi berfungsi seperti opsi format **Hidden** di Microsoft Word: shape diabaikan dari tata letak visual tetapi tetap berpartisipasi dalam model objek dokumen. Ini berguna untuk:

* Menyimpan metadata atau penanda yang dibaca aplikasi Anda nanti.  
* Membuat placeholder yang dihapus tepat sebelum publikasi.  
* Mengontrol visibilitas untuk format output yang berbeda (mis., sembunyikan di HTML tetapi pertahankan di PDF).

**Catatan:** Shape tersembunyi masih diekspor ke PDF secara default. Jika Anda ingin mereka diabaikan dari PDF juga, setel `rectangle.getWrapType( ) = WrapType.NONE` dan sesuaikan properti `Hidden` sesuai.

## Langkah 4: Simpan dokumen yang dimodifikasi

Akhirnya, simpan perubahan ke file baru.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Saat Anda membuka `output.docx` di Microsoft Word, persegi panjang tidak akan terlihat, tetapi tetap menjadi bagian dari pohon dokumen. Anda dapat memverifikasi keberadaannya secara programatis dengan memuat ulang file dan memeriksa `Shape.isHidden()`.

### Output yang Diharapkan

* File `output.docx` terbuka tanpa shape yang terlihat.  
* Jika Anda memeriksa dokumen dengan Aspose.Words (mis., `doc.getChildNodes(NodeType.SHAPE, true).size()`), jumlah shape akan **1**, mengonfirmasi bahwa shape ada tetapi tersembunyi.

## Variasi lanjutan dan kasus tepi

### 1. Membuat shape dalam dokumen baru

Jika Anda memulai dari awal, ganti baris load dengan:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Memposisikan shape secara tepat

Secara default, `insertShape` menempatkan shape pada lokasi kursor saat ini. Untuk memposisikannya secara absolut:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Mengontrol visibilitas per format output

Jika Anda memerlukan shape terlihat di UI Word tetapi tersembunyi saat mengekspor ke PDF, gunakan `Shape.setWrapType(WrapType.NONE)` bersama dengan `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Menambahkan teks di dalam shape

Sebuah persegi panjang dapat berisi bingkai teks:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Anda kemudian dapat menyembunyikan kotak teks dengan pemanggilan `setHidden(true)` yang sama.

## Kesalahan umum dan cara menghindarinya

| Gejala | Penyebab | Solusi |
|---------|-------|-----|
| Shape muncul meskipun setelah `setHidden(true)` | Dokumen disimpan sebelum flag tersembunyi diatur. | Pastikan Anda memanggil `setHidden(true)` **sebelum** `doc.save()`. |
| Ukuran shape tampak terdistorsi | Kebingungan antara poin dan piksel pada layar high‑DPI. | Gunakan poin (72 pt = 1 in) untuk ukuran konsisten di semua platform. |
| Shape tersembunyi masih tercetak | Beberapa printer mengabaikan flag tersembunyi. | Setel `Shape.setWrapType(WrapType.NONE)` dan juga bersihkan `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Kesimpulan

Anda kini tahu cara **menambahkan shape ke Word** dokumen menggunakan Aspose.Words untuk Java, **cara menyisipkan shape**, dan **cara menyembunyikan shape** sehingga tetap tidak terlihat oleh pengguna akhir namun tetap menjadi bagian dari struktur dokumen. Contoh lengkap di atas memuat file, menyisipkan persegi panjang, menyembunyikannya, dan menyimpan hasilnya, mencakup baik kasus penggunaan umum maupun beberapa kasus tepi.

Mulai dari sini Anda dapat menjelajahi topik terkait seperti **cara menyisipkan shape** dengan warna isi khusus, **cara menyembunyikan shape di Word** untuk pencetakan kondisional, atau mengotomatisasi pemrosesan dokumen massal dengan Aspose.Words. Bereksperimenlah dengan nilai `ShapeType` yang berbeda, opsi penempatan, dan flag visibilitas untuk menyesuaikan alur kerja Anda.

Selamat coding, dan nikmati fleksibilitas yang dibawa manipulasi Word secara programatis ke aplikasi Java Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat dokumen Word secara programatis, tambahkan dan sembunyikan shape di Java menggunakan Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Cara menyembunyikan shape dalam dokumen Word menggunakan Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Buat dokumen Word .docx kosong dan tambahkan shape persegi panjang tersembunyi dengan Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}