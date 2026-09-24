---
category: general
date: 2026-09-24
description: Pelajari cara membuat dokumen Word kosong dalam Java dan mengelompokkan
  bentuk seperti persegi panjang serta garis menggunakan Aspose.Words. Termasuk kode
  langkah demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: id
lastmod: 2026-09-24
og_description: Buat dokumen Word kosong di Java dan pelajari cara mengelompokkan
  bentuk, menambahkan bentuk persegi panjang, serta mengatur ukuran bentuk dengan
  Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Buat dokumen Word kosong dan grupkan bentuk di Java – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cara membuat dokumen Word kosong dan mengelompokkan bentuk di Java
url: /id/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dan mengelompokkan shape di Java

Jika Anda perlu **membuat dokumen Word kosong** dan kemudian mengatur beberapa objek gambar, panduan ini menunjukkan cara melakukannya secara tepat. Dengan menggunakan Aspose.Words for Java Anda dapat menyisipkan group shape, menambahkan rectangle shape, menggambar garis, dan mengontrol ukuran serta posisi setiap shape—semua dalam satu program yang dapat dijalankan.

Anda akan melalui setiap langkah, mulai dari menginisialisasi dokumen hingga menyimpan `.docx` akhir. Pada akhir tutorial Anda akan memahami **cara mengelompokkan shape**, **menambahkan rectangle shape**, dan **mengatur ukuran shape** sehingga file Word Anda terlihat persis seperti yang diinginkan.

## Prasyarat

- Java 17 atau lebih baru (kode ini dapat dikompilasi dengan JDK terbaru apa pun)
- Perpustakaan Aspose.Words for Java (unduh dari [Aspose website](https://products.aspose.com/words/java))
- IDE atau alat build (Maven/Gradle) yang dapat menambahkan JAR Aspose.Words ke classpath
- Pengetahuan dasar tentang sintaks Java

> **Pro tip:** Gunakan Maven untuk manajemen dependensi; tambahkan `com.aspose:aspose-words:23.12` (atau versi terbaru) ke `pom.xml` Anda.

## Langkah 1: Membuat dokumen Word kosong

Tugas pertama adalah **membuat dokumen Word kosong**. Ini memberi Anda kanvas bersih yang nantinya dapat Anda sisipkan shape.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting:* Objek `Document` mewakili seluruh file `.docx`. Memulai dengan dokumen kosong memastikan tidak ada format tersembunyi yang mengganggu shape yang akan Anda tambahkan.

## Langkah 2: Menyisipkan group shape – wadah untuk beberapa objek

Sebuah **group shape** berfungsi seperti wadah yang memungkinkan Anda memindahkan, mengubah ukuran, atau memutar beberapa shape sekaligus. Ini adalah inti dari **cara mengelompokkan shape** di Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Penjelasan:* Metode `insertGroupShape` membuat objek `GroupShape` dan menempatkannya pada lokasi kursor saat ini. Semua shape berikutnya yang Anda `appendChild` ke grup ini akan diperlakukan sebagai satu unit.

## Langkah 3: Menambahkan rectangle shape dan mengatur ukurannya

Sekarang kita **menambahkan rectangle shape** ke grup dan **mengatur ukuran shape** secara tepat.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Mengapa Anda perlu mengatur ukuran shape:* Lebar dan tinggi mengontrol bagaimana rectangle muncul di halaman. Metode `setLeft` dan `setTop` memposisikan rectangle relatif terhadap asal grup, memberi Anda kontrol tata letak pixel‑perfect.

## Langkah 4: Menambahkan line shape dan mengonfigurasi dimensinya

Garis adalah objek gambar umum lainnya. Kami akan menerapkan logika **menambahkan rectangle shape**‑like pada sebuah line, menunjukkan bahwa prinsip pengukuran yang sama berlaku.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Poin penting:* Meskipun sebuah line tidak memiliki tinggi, Anda tetap menggunakan `setWidth` untuk menentukan panjangnya. Penempatan (`setLeft`, `setTop`) mengikuti sistem koordinat yang sama seperti shape lainnya.

## Langkah 5: Menyimpan dokumen dengan shape yang dikelompokkan

Akhirnya, simpan perubahan dengan menyimpan dokumen. Ini menghasilkan file `.docx` yang dapat Anda buka di Microsoft Word untuk memverifikasi hasilnya.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Output yang diharapkan:** Membuka `GroupShapeDemo.docx` menampilkan halaman kosong yang berisi rectangle dan line yang dikelompokkan. Memilih salah satu shape akan memilih seluruh grup, memungkinkan Anda memindahkannya bersama.

## Pertanyaan umum dan penanganan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| *Apakah saya dapat menambahkan lebih dari dua shape ke grup?* | Ya. Panggil `group.appendChild(yourShape)` untuk setiap shape tambahan. |
| *Bagaimana jika saya membutuhkan satuan berbeda (misalnya sentimeter) untuk ukuran?* | Aspose.Words menggunakan poin (1 poin = 1/72 inci). Konversi menggunakan `Points = centimeters * 28.3465`. |
| *Apakah grup akan mempertahankan tata letaknya ketika dokumen dibuka di mesin lain?* | Tentu saja. Semua data ukuran dan posisi disimpan dalam file `.docx`, sehingga tata letak dapat dipindahkan. |
| *Bagaimana cara mengeluarkan grup shape nanti?* | Ambil objek `GroupShape`, lalu iterasi `group.getChildNodes(NodeType.SHAPE, true)` dan pindahkan setiap child keluar dari grup. |
| *Bagaimana jika saya perlu memutar seluruh grup?* | Gunakan `group.setRotationAngle(double angleInDegrees)` sebelum menyimpan. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke IDE Anda. Program ini mencakup semua import yang diperlukan dan komentar.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Jalankan program, buka `GroupShapeDemo.docx` di Microsoft Word, dan Anda akan melihat shape yang dikelompokkan persis seperti yang dijelaskan.

## Kesimpulan

Anda sekarang tahu cara **membuat dokumen Word kosong**, **mengelompokkan shape di Word**, **menambahkan rectangle shape**, dan **mengatur ukuran shape** menggunakan Aspose.Words for Java. Dengan menempatkan shape di dalam `GroupShape`, Anda mendapatkan kontrol penuh atas posisi kolektif, skala, dan rotasi—sempurna untuk diagram, flowchart, atau grafik khusus yang disematkan dalam laporan otomatis.

**Langkah selanjutnya:**  
- Jelajahi **cara mengelompokkan shape** dengan objek yang lebih kompleks seperti gambar atau kotak teks.  
- Bereksperimen dengan `setRotationAngle` untuk memutar seluruh grup.  
- Gabungkan teknik ini dengan mail‑merge untuk menghasilkan dokumen pribadi yang menyertakan grafik bermerk.

Silakan sesuaikan kode untuk proyek Anda sendiri, dan bagikan hasil Anda di komentar!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Membuat rectangle shape di Word dengan Java – Panduan Lengkap](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Membuat Dokumen Word Java – Tambahkan Rectangle Shape dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Membuat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}