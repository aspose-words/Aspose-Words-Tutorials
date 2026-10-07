---
category: general
date: 2026-09-27
description: Buat dokumen Word kosong di Java dan grupkan bentuk menggunakan Aspose.Words.
  Pelajari cara mengatur ukuran bentuk, mengatur warna isi bentuk, dan menambahkan
  anak ke grup.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: id
lastmod: 2026-09-27
og_description: Buat dokumen Word kosong dalam Java dengan Aspose.Words. Tutorial
  ini menunjukkan cara mengelompokkan bentuk di Word, mengatur ukuran bentuk, mengatur
  warna isi bentuk, dan menambahkan anak ke grup.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Buat dokumen Word kosong dan grupkan bentuk di Java – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cara membuat dokumen Word kosong dan mengelompokkan bentuk di Java
url: /id/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dan mengelompokkan bentuk di Java

Jika Anda perlu **create blank word document** secara programatis, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words for Java. Anda juga akan belajar **group shapes in word**, mengatur ukuran setiap bentuk, menerapkan warna isi, dan **append child to group** sehingga objek berperilaku sebagai satu unit.

Bekerja dengan file Word dari kode menghemat Anda dari pemformatan manual dan memungkinkan Anda menghasilkan laporan, kontrak, atau brosur pemasaran secara otomatis. Pada akhir tutorial ini Anda akan memiliki program Java yang dapat dijalankan yang menghasilkan file `.docx` berisi persegi panjang biru dan sebuah gambar, keduanya dikelompokkan bersama.

## Prasyarat

- Java 17 (atau JDK terbaru apa pun) terinstal.
- Maven atau Gradle untuk mengelola dependensi.
- Lisensi Aspose.Words for Java (evaluasi gratis dapat digunakan untuk pengujian).
- File gambar contoh (misalnya `sample.jpg`) ditempatkan dalam folder yang dapat Anda referensikan dari kode.

> **Pro tip:** Simpan file gambar Anda dalam direktori `resources` dan muat mereka dengan `ClassLoader.getResourceAsStream` untuk menghindari jalur absolut yang dikodekan keras.

## Langkah 1: Buat dokumen Word kosong dan tambahkan GroupShape

Langkah pertama adalah menginstansiasi objek `Document` baru, yang mewakili file Word kosong, lalu menyisipkan `GroupShape`. Grup ini akan berfungsi sebagai wadah untuk semua bentuk yang Anda tambahkan nanti.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Mengapa ini penting:* `GroupShape` memungkinkan Anda memindahkan, memutar, atau memformat beberapa bentuk sekaligus, yang penting untuk tata letak kompleks seperti diagram atau watermark.

## Langkah 2: Sisipkan persegi panjang dan **set shape size**

Selanjutnya, buat sebuah persegi panjang, tentukan dimensinya, dan tambahkan ke grup. Ini mendemonstrasikan operasi **set shape size**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Penjelasan:* `setWidth` dan `setHeight` mengontrol ukuran tepat bentuk dalam poin (1 poin = 1/72 inci). Sesuaikan nilai-nilai ini untuk memenuhi kebutuhan tata letak Anda.

## Langkah 3: **Set shape fill color** untuk persegi panjang

Latar belakang persegi panjang diatur menjadi biru menggunakan `setFillColor`. Anda dapat menggunakan konstanta `java.awt.Color` apa pun atau membuat warna RGB khusus.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Mengapa ini berguna:* Warna isi membantu membedakan objek secara visual, terutama ketika Anda mengekspor dokumen ke PDF atau mencetaknya.

## Langkah 4: Sisipkan gambar dan **append child to group**

Sekarang tambahkan gambar ke `GroupShape` yang sama. Gambar disisipkan melalui `DocumentBuilder.insertImage`, kemudian ditambahkan ke grup sehingga bergerak bersama persegi panjang.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Kasus tepi:* Jika jalur gambar salah, Aspose.Words akan melempar `FileNotFoundException`. Gunakan jalur relatif atau muat gambar dari resources untuk menghindari masalah ini.

## Langkah 5: **Save the document with the grouped shapes**

Akhirnya, tulis dokumen ke disk. File yang dihasilkan akan berisi persegi panjang dan gambar yang dikelompokkan bersama.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Output yang diharapkan

- Sebuah file bernama `GroupShape.docx` muncul di direktori yang ditentukan.
- Membuka file di Microsoft Word menampilkan halaman kosong dengan persegi panjang biru dan gambar yang dipilih, keduanya dipilih sebagai satu objek (Anda dapat memindahkan atau mengubah ukuran mereka bersama-sama).

![buat dokumen word kosong dengan bentuk yang dikelompokkan](/images/grouped-shapes.png "buat dokumen word kosong dengan bentuk yang dikelompokkan")

*Tangkapan layar di atas menunjukkan bentuk yang dikelompokkan akhir di dalam dokumen Word yang baru dibuat.*

## Variasi umum dan tips tambahan

| Situation | How to handle it |
|-----------|-----------------|
| **Beberapa gambar** | Sisipkan setiap gambar dengan `builder.insertImage` dan panggil `group.appendChild(picture)` untuk masing-masing. |
| **Berbagai jenis bentuk** | Gunakan `ShapeType.OVAL`, `ShapeType.LINE`, dll., saat membangun objek `Shape`. |
| **Mengubah posisi grup** | Setelah menambahkan semua anak, atur `group.setLeft(x)` dan `group.setTop(y)` untuk memindahkan seluruh grup. |
| **Ekspor ke PDF** | Panggil `doc.save("output.pdf")` setelah mengelompokkan; PDF akan mempertahankan pengelompokan. |
| **Penegakan lisensi** | Jika Anda menjalankan versi evaluasi, watermark akan muncul. Pasang lisensi yang valid untuk menghilangkannya. |

## Kesimpulan

Anda sekarang tahu cara **create blank word document**, menyisipkan **GroupShape**, **set shape size**, **set shape fill color**, dan **append child to group** menggunakan Aspose.Words for Java. Pola ini memungkinkan Anda membangun tata letak kompleks secara programatis yang dapat diedit nanti di Word atau diekspor ke format lain.

Selanjutnya, jelajahi cara **group shapes in word** dengan kotak teks, menambahkan hyperlink ke bentuk, atau mengotomatiskan pembuatan laporan multi‑halaman. Prinsip yang sama berlaku—hanya buat bentuk tambahan, konfigurasikan propertinya, dan tambahkan ke grup yang sama.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat bentuk persegi panjang di Word dengan Java – Panduan Lengkap](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Buat Group Shape di Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}