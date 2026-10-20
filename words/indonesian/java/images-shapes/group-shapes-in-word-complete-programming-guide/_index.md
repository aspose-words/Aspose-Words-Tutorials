---
category: general
date: 2026-08-14
description: Kelompokkan bentuk di Word dengan Java menggunakan Aspose.Words. Pelajari
  cara membuat bentuk persegi panjang, mengatur dimensi bentuk, dan mengelompokkan
  beberapa bentuk dalam dokumen Word kosong.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: id
lastmod: 2026-08-14
og_description: Kelompokkan bentuk di Word menggunakan Aspose.Words untuk Java. Buat
  dokumen Word kosong, buat bentuk persegi panjang, atur dimensi bentuk, dan kelompokkan
  beberapa bentuk dalam hitungan menit.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Mengelompokkan bentuk di Word – contoh Java untuk pengembang
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Mengelompokkan bentuk di Word – panduan pemrograman lengkap
url: /id/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengelompokkan bentuk di Word – panduan pemrograman lengkap

Jika Anda perlu **mengelompokkan bentuk di Word**, tutorial ini akan memandu Anda melalui seluruh proses dengan Java dan Aspose.Words. Anda akan belajar cara **membuat dokumen Word kosong**, **membuat rectangle shape**, **mengatur dimensi bentuk**, dan akhirnya **mengelompokkan beberapa bentuk** sehingga mereka berperilaku sebagai satu objek.

Bekerja dengan bentuk dalam file Word sering terasa seperti menggambar di kanvas tanpa kuas. Pada akhir panduan ini Anda akan memiliki potongan kode yang dapat digunakan kembali yang dapat Anda sisipkan ke dalam proyek Java apa pun, baik Anda sedang menghasilkan laporan, faktur, atau templat khusus.

## Apa yang Anda perlukan

- Java 8 atau lebih baru
- Aspose.Words for Java (versi terbaru, misalnya, 24.9)
- IDE seperti IntelliJ IDEA atau Eclipse
- Familiaritas dasar dengan pemrograman berorientasi objek

Semua prasyarat ini dapat diinstal secara gratis, dan kode di bawah ini dapat dikompilasi dengan satu dependensi Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Langkah 1: Membuat dokumen Word kosong dan menginisialisasi builder

Hal pertama yang harus Anda lakukan adalah **membuat dokumen Word kosong**. Ini memberi Anda kanvas bersih yang kemudian dapat Anda sisipkan bentuk.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` mewakili seluruh file *.docx*, sementara `DocumentBuilder` adalah pembantu yang menyisipkan paragraf, tabel, dan bentuk. Menginisialisasi kedua objek ini adalah dasar untuk setiap tugas otomasi Word.

## Langkah 2: Menyisipkan kontainer group shape

**Group shape** berfungsi seperti folder yang dapat menampung bentuk lain. Pertama kita membuat kontainer dengan ukuran tetap 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

Metode `insertGroupShape` mengembalikan objek `GroupShape`. Semua bentuk berikutnya yang ingin Anda perlakukan sebagai satu unit harus ditambahkan ke objek ini.

## Langkah 3: Membuat bentuk persegi panjang dan mengatur dimensi bentuk

Sekarang kita **membuat objek rectangle shape**, mengonfigurasi ukurannya, dan menempatkannya di dalam grup. Langkah ini juga menunjukkan cara **mengatur dimensi bentuk** secara tepat.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Kedua persegi panjang memiliki dimensi yang sama, tetapi properti `left` mereka berbeda, sehingga muncul berdampingan. Anda dapat mengubah `setTop` dan `setLeft` untuk mengatur tata letak apa pun yang Anda perlukan.

## Langkah 4: Menyimpan dokumen yang berisi persegi panjang yang dikelompokkan

Setelah bentuk berada di dalam grup, Anda cukup menyimpan `Document`. File yang dihasilkan akan menampilkan dua persegi panjang yang bergerak bersama saat dipilih.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Menjalankan program akan membuat `GroupShape.docx` di direktori kerja. Buka di Microsoft Word, pilih satu persegi panjang, dan Anda akan melihat bahwa seluruh grup bergerak sebagai satu unit—tepat seperti yang dimaksud dengan **group shapes in Word**.

![Contoh group shapes di Word](group-shapes.png){alt="Contoh group shapes di Word"}

*Gambar: Dua bentuk persegi panjang yang dikelompokkan bersama dalam dokumen Word.*

## Tips profesional: Menggunakan kembali group shape yang sama

Jika Anda perlu menambahkan lebih banyak bentuk nanti (mis., lingkaran, kotak teks), pertahankan referensi ke `groupShape` dan terus panggil `appendChild`. Ini menghindari pembuatan ulang kontainer dan memastikan semua anggota tetap sinkron.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Kasus tepi dan pertanyaan umum

- **Bagaimana jika bentuk saling tumpang tindih?** Tumpang tindih diizinkan; Word akan merendernya dalam urutan penambahan. Gunakan `setZOrder` jika Anda memerlukan penumpukan eksplisit.
- **Apakah saya dapat mengelompokkan bentuk di beberapa halaman?** Tidak. `GroupShape` terbatas pada satu halaman karena sistem koordinatnya relatif terhadap halaman.
- **Apakah bentuk yang dikelompokkan mewarisi pemformatan?** Setiap anak mempertahankan pemformatannya sendiri (warna isi, gaya garis). Untuk menerapkan gaya seragam, iterasi melalui `groupShape.getChildNodes()` dan atur properti secara programatis.

## Kode sumber lengkap untuk referensi

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Menjalankan program menghasilkan file DOCX di mana kedua persegi panjang **dikelompokkan**. Memilih salah satu persegi panjang akan memindahkan keduanya, mengonfirmasi bahwa Anda telah berhasil **mengelompokkan beberapa bentuk**.

## Kesimpulan

Anda sekarang tahu cara **mengelompokkan bentuk di Word** menggunakan Java, mulai dari **membuat dokumen Word kosong** hingga **membuat rectangle shape**, **mengatur dimensi bentuk**, dan akhirnya **mengelompokkan beberapa bentuk** menjadi satu objek yang dapat dipindahkan. Pola ini dapat diperluas ke jumlah bentuk apa pun dan dapat digabungkan dengan teks, gambar, atau diagram untuk membangun dokumen yang kaya dan terprogram.

### Apa selanjutnya?

- Jelajahi **mengelompokkan beberapa bentuk** dengan tipe berbeda (elips, panah, kotak teks).
- Terapkan warna isi atau batas dengan memanggil `shape.getFillColor()` dan `shape.getLine().setColor()`.
- Sisipkan group shape ke dalam sel tabel untuk laporan terstruktur.
- Gabungkan pendekatan ini dengan mail‑merge untuk menghasilkan kontrak pribadi yang menyertakan grafik bermerk.

Silakan bereksperimen, menyesuaikan dimensi, atau menyematkan konten tambahan. Ketika Anda menguasai pengelompokan, skrip otomasi Word Anda menjadi jauh lebih fleksibel dan mudah dipelihara. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menggunakan Bentuk Dokumen di Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Membuat Dokumen Word Java – Menambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Membuat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}