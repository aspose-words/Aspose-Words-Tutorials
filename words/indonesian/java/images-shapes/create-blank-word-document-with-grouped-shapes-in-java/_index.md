---
category: general
date: 2026-08-07
description: Buat dokumen Word kosong dengan bentuk yang dikelompokkan dalam Java
  menggunakan Aspose.Words. Pelajari cara mengelompokkan bentuk, mengatur ukuran bentuk,
  dan menambahkan bentuk ke Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: id
lastmod: 2026-08-07
og_description: Buat dokumen Word kosong dengan bentuk yang dikelompokkan dalam Java.
  Ikuti panduan ini untuk mengatur ukuran bentuk, menambahkan bentuk ke Word, dan
  menguasai cara mengelompokkan bentuk.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Buat dokumen Word kosong dengan bentuk yang dikelompokkan – Tutorial Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Buat dokumen Word kosong dengan bentuk yang dikelompokkan di Java
url: /id/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dengan bentuk yang dikelompokkan di Java

Jika Anda perlu **create blank Word document** yang berisi beberapa shape yang diatur sebagai satu unit, tutorial ini menunjukkan cara melakukannya secara tepat. Anda akan melihat contoh lengkap yang dapat dijalankan yang mendemonstrasikan **how to group shape** objek, menyesuaikan dimensinya, dan **add shapes to Word** menggunakan Aspose.Words for Java.

Panduan ini melangkah melalui setiap langkah—dari penyiapan proyek hingga menyimpan file .docx akhir—sehingga Anda dapat menyalin kode langsung ke aplikasi Anda sendiri. Tidak diperlukan referensi eksternal, dan solusi ini bekerja dengan Aspose.Words 23.9 atau yang lebih baru.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Java 17 (atau JDK yang didukung lainnya)
* Maven atau Gradle untuk manajemen dependensi
* Lisensi Aspose.Words for Java (atau kunci evaluasi sementara)
* File gambar contoh (misalnya `sample.jpg`) ditempatkan di direktori yang diketahui

Jika salah satu dari item ini belum ada, instal terlebih dahulu; sisanya tutorial mengasumsikan lingkungan sudah siap.

## Langkah 1: Tambahkan Aspose.Words ke proyek Anda

Tambahkan dependensi Aspose.Words ke `pom.xml` Anda (Maven) atau `build.gradle` (Gradle). Perpustakaan ini menyediakan kelas `Document`, `DocumentBuilder`, `GroupShape`, dan `Shape` yang akan digunakan nanti.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Mengapa ini penting:** Tanpa perpustakaan tersebut, tidak ada API pemrosesan Word yang tersedia, dan Anda tidak dapat **create blank Word document** secara programatis.

## Langkah 2: Buat dokumen Word kosong

Tindakan konkret pertama adalah menginstansiasi objek `Document`, yang mewakili **blank Word document** dalam memori.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* membuat **blank Word document** dengan pengaturan default (halaman A4, margin default). `DocumentBuilder` yang menyertainya memungkinkan Anda menyisipkan konten pada posisi kursor saat ini.

## Langkah 3: Sisipkan group shape (how to group shape)

Sebuah *group shape* berfungsi sebagai wadah untuk shape lain. Pada langkah ini Anda belajar **how to group shape** objek sehingga mereka bergerak bersama.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Metode `insertGroupShape` menempatkan kontainer pada lokasi kursor builder. Pengelompokan penting ketika Anda ingin memperlakukan beberapa gambar sebagai satu entitas—ini adalah inti dari fungsionalitas **group shapes word**.

## Langkah 4: Buat persegi panjang dan atur ukurannya

Sekarang tambahkan persegi panjang ke grup. Ini mendemonstrasikan **set shape size**, yang diperlukan untuk tata letak yang tepat.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Mengapa mengatur dimensi?* Memanggil secara eksplisit `setWidth` dan `setHeight` menjamin bahwa persegi panjang muncul persis seperti yang diinginkan, terlepas dari gaya shape default dokumen.

## Langkah 5: Sisipkan gambar dan tambahkan ke grup

Menambahkan gambar menunjukkan contoh penggunaan umum lain untuk **add shapes to word**. Gambar menjadi bagian dari grup yang sama, bergerak bersama persegi panjang.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Jika file gambar tidak ada, Aspose.Words akan melemparkan pengecualian. Tips praktis adalah memverifikasi jalur terlebih dahulu:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Langkah 6: Simpan dokumen yang berisi grup shape

Akhirnya, simpan **blank Word document** (sekarang berisi grup shape) ke disk.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Saat Anda membuka `GroupShapeDemo.docx` di Microsoft Word, Anda akan melihat satu objek grup yang berisi persegi panjang dan gambar. Memilih bagian mana pun dari grup akan memindahkan seluruh kontainer, mengonfirmasi bahwa shape telah **grouped** dengan benar.

### Output yang Diharapkan

* File bernama `GroupShapeDemo.docx` di direktori yang ditentukan.
* Membuka file menampilkan kontainer 300 × 200‑point dengan:
  * Persegi panjang 100 × 50‑point yang diposisikan pada (20, 20).
  * Gambar yang diposisikan pada (150, 30) di dalam kontainer yang sama.

## Kasus tepi dan variasi

| Situasi | Cara menanganinya |
|-----------|-----------------|
| **Ukuran halaman berbeda** | Panggil `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` sebelum menyisipkan grup. |
| **Beberapa grup** | Ulangi langkah 3‑5 dengan instance `GroupShape` baru; setiap grup dapat diposisikan secara independen. |
| **Memutar shape** | Gunakan `shape.setRotationAngle(45.0);` untuk memutar persegi panjang atau gambar sebelum menambahkannya ke grup. |
| **Shape bukan gambar** | Buat objek `Shape` dengan tipe `ShapeType.ELLIPSE`, `ShapeType.LINE`, dll., dan tambahkan seperti persegi panjang. |
| **Gambar besar** | Skala gambar dengan `picture.setWidth(80.0); picture.setHeight(60.0);` agar grup tetap dalam batas aslinya. |

## Tips praktis dari pengalaman

* **Pro tip:** Atur `RelativeHorizontalPosition` dan `RelativeVerticalPosition` grup ke `RelativeHorizontalPosition.PAGE` dan `RelativeVerticalPosition.PAGE` jika Anda ingin grup tetap terjangkar pada halaman bukan pada kursor.
* **Watch out for:** Menambahkan shape yang melebihi dimensi grup; shape akan terpotong di Word. Sesuaikan ukuran grup dengan `group.setWidth()` dan `group.setHeight()` sesuai kebutuhan.
* **Performance note:** Jika Anda menghasilkan banyak dokumen dalam loop, gunakan kembali satu instance `DocumentBuilder` dan panggil `doc.clone()` untuk mengurangi beban pembuatan objek.

## Kesimpulan

Anda kini tahu cara **create blank Word document** yang berisi kumpulan shape yang dikelompokkan menggunakan Aspose.Words for Java. Tutorial ini mencakup alur kerja lengkap: menyiapkan perpustakaan, membuat dokumen, menyisipkan grup, **set shape size**, **add shapes to word**, dan menyimpan hasilnya.

Dari sini Anda dapat menjelajahi fitur lebih lanjut seperti mengelompokkan chart, menerapkan gaya pada shape individual, atau mengekspor dokumen ke PDF. Setiap topik ini dibangun di atas prinsip yang sama yang ditunjukkan dalam panduan ini.

---


## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat Dokumen Word Java – Tambahkan Shape Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Sisipkan Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}