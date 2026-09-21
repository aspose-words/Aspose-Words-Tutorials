---
category: general
date: 2026-09-21
description: Buat dokumen Word secara programatis menggunakan Java. Pelajari cara
  mengelompokkan bentuk di Word, menyisipkan bentuk persegi panjang, mengatur ukuran
  bentuk, dan menambahkan bentuk ke dokumen Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: id
lastmod: 2026-09-21
og_description: 'Buat dokumen Word secara programatis dengan Java: panduan ini menunjukkan
  cara mengelompokkan bentuk di Word, menyisipkan bentuk persegi panjang, mengatur
  ukuran bentuk, dan menambahkan bentuk ke dokumen Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Buat dokumen Word secara programatis, grupkan bentuk di Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Buat dokumen Word secara programatik, grupkan bentuk di Java
url: /id/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat dokumen Word secara programatis, mengelompokkan bentuk di Java

Jika Anda perlu **membuat dokumen Word secara programatis**, panduan ini akan membawa Anda melalui solusi lengkap. Anda akan melihat cara **mengelompokkan bentuk di Word**, menyisipkan persegi panjang, mengatur ukurannya, dan menambahkan bentuk lain—semua menggunakan Java dan pustaka Aspose.Words for Java.

Tutorial ini mencakup setiap langkah mulai dari penyiapan proyek hingga menyimpan file .docx akhir. Pada akhir tutorial Anda akan dapat menghasilkan dokumen Word yang berisi persegi panjang dan gambar yang dibungkus dalam satu grup, sehingga mudah dipindahkan atau diubah ukurannya secara bersamaan. Tidak diperlukan pengalaman sebelumnya dengan API Aspose.Words, tetapi Anda harus memiliki lingkungan pengembangan Java dasar.

## Prasyarat

* Java Development Kit (JDK) 8 atau yang lebih baru  
* Maven atau Gradle untuk manajemen dependensi  
* Aspose.Words for Java 23.9 (atau versi terbaru) – perpustakaan ini gratis untuk evaluasi  
* Sebuah file gambar (misalnya `sample.jpg`) yang ditempatkan di direktori yang diketahui  

Menyiapkan hal‑hal ini memastikan kode dapat dijalankan tanpa konfigurasi tambahan.

## Langkah 1: Siapkan proyek dan impor Aspose.Words

Buat proyek Maven (atau tambahkan dependensi ke `pom.xml` Anda yang sudah ada):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Jika Anda lebih suka Gradle, tambahkan berikut ke `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Setelah dependensi terpasang, impor kelas‑kelas yang diperlukan di file sumber Java Anda:

```java
import com.aspose.words.*;
import java.io.File;
```

## Langkah 2: Buat dokumen Word secara programatis

Operasi pertama dalam skenario otomasi apa pun adalah menginstansiasi objek `Document` dan `DocumentBuilder`. Builder mempermudah penyisipan teks, gambar, dan bentuk.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Pada titik ini dokumen hanya ada di memori. Anda kini dapat mulai menambahkan bentuk.

## Langkah 3: Sisipkan bentuk persegi panjang – cara menyisipkan bentuk persegi panjang

Persegi panjang adalah `Shape` dasar dengan `ShapeType.RECTANGLE`. Anda mengontrol dimensinya dengan `setWidth`, `setHeight`, dan menempatkannya dengan `setTop` serta `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Mengapa ini penting:** Menetapkan ukuran dan posisi secara eksplisit (`set shape size word`) menjamin persegi panjang muncul tepat di tempat yang Anda harapkan, terlepas dari tata letak default dokumen.

## Langkah 4: Sisipkan gambar – tambahkan bentuk ke dokumen word

`DocumentBuilder` dapat menyisipkan gambar langsung dari jalur file. Setelah penyisipan, Anda dapat memposisikan kembali gambar seperti bentuk lainnya.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Baik persegi panjang maupun gambar kini menjadi bentuk independen di dalam dokumen.

## Langkah 5: Kelompokkan bentuk – cara mengelompokkan bentuk di word

Mengelompokkan bentuk berguna ketika Anda ingin memindahkan atau mengubah ukuran mereka sebagai satu unit. Aspose.Words menyediakan kontainer `GroupShape` untuk tujuan ini.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Saat grup disimpan, Word memperlakukan dua anak tersebut sebagai satu objek logis. Anda kemudian dapat memilih grup dan menyeretnya, dan baik persegi panjang maupun gambar akan mengikuti.

## Langkah 6: Simpan dokumen

Akhirnya, tulis dokumen ke disk. Jalur harus dapat ditulisi oleh proses Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Menjalankan metode `main` menghasilkan file bernama **GroupShapeExample.docx**. Buka file tersebut di Microsoft Word untuk melihat persegi panjang dan gambar yang terkunci bersama di dalam grup. Memilih grup memungkinkan Anda memindahkan kedua objek secara bersamaan, menegaskan bahwa pengelompokan berhasil.

## Output yang diharapkan

* Sebuah file Word (`GroupShapeExample.docx`) yang terletak di direktori yang Anda tentukan.  
* Di dalam file, sebuah persegi panjang (isi abu‑abu terang) muncul di sudut kiri‑atas, dan gambar berada tepat di bawahnya.  
* Kedua objek merupakan bagian dari satu grup, sehingga menyeret satu akan memindahkan yang lain.

## Variasi umum dan kasus tepi

| Situasi | Rekomendasi |
|-----------|----------------|
| **Berbagai format gambar** | Aspose.Words mendukung PNG, BMP, GIF, dan TIFF. Gunakan ekstensi file yang sesuai pada `insertImage`. |
| **Dimensi negatif** | API akan melempar `ArgumentException`. Selalu validasi lebar dan tinggi sebelum memanggil `setWidth` / `setHeight`. |
| **Dokumen besar** | Mengelompokkan banyak bentuk dapat meningkatkan ukuran file. Pertimbangkan menggabungkan bentuk menjadi satu gambar ketika kinerja menjadi faktor. |
| **Kompatibilitas versi Word** | GroupShape bekerja dengan Word 2007 (`.docx`) dan versi selanjutnya. Untuk file `.doc` yang lebih lama, grup akan diluruskan. |
| **Posisi dinamis** | Gunakan perhitungan berdasarkan ukuran halaman (`doc.getFirstSection().getPageSetup().getPageWidth()`) jika Anda memerlukan penempatan adaptif. |

**Tips pro:** Setelah membuat grup, Anda dapat mengubah

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Buat bentuk persegi panjang di Word dengan Java – Panduan Lengkap](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Buat Group Shape di Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}