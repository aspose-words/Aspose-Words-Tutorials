---
category: general
date: 2026-07-16
description: cara menyisipkan grup bentuk di Java menggunakan Aspose.Words – tambahkan
  bentuk persegi panjang, atur dimensi bentuk, dan buat persegi panjang serta lingkaran
  berwarna
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: id
lastmod: 2026-07-16
og_description: 'cara menyisipkan grup shape di Java: panduan praktis untuk menambahkan
  bentuk persegi panjang, mengatur dimensi shape, dan membuat persegi panjang serta
  lingkaran berwarna dengan Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Menyisipkan Group Shape di Java – Tutorial Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Cara Menyisipkan Grup Bentuk di Java – Panduan Lengkap
url: /id/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara menyisipkan group shape di Java – Panduan Lengkap

Pernah bertanya-tanya **bagaimana cara menyisipkan group shape** dalam dokumen Word menggunakan Java? Anda bukan satu-satunya. Baik Anda sedang membuat generator laporan atau pembuat flyer dinamis, mengelompokkan shape membuat tata letak Anda rapi dan kode Anda mudah dikelola.

Dalam tutorial ini kami akan menjelaskan langkah‑langkah tepat untuk **add rectangle shape**, **set shape dimensions**, dan **create colored rectangle** serta **create colored circle** menggunakan library Aspose.Words. Pada akhir tutorial Anda akan memiliki program yang dapat dijalankan yang menghasilkan file .docx dengan persegi panjang biru dan lingkaran merah yang rapi terbungkus di dalam sebuah grup.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- Java 17 (atau JDK terbaru lainnya) terpasang dan terkonfigurasi.
- Maven atau Gradle untuk mengelola dependensi.
- Aspose.Words for Java 23.9 atau yang lebih baru – Anda dapat mengunduhnya dari Maven Central.
- Pemahaman dasar tentang sintaks Java – tidak memerlukan hal yang rumit.

Jika Anda belum memiliki salah satu dari ini, unduh JDK dari situs Oracle dan tambahkan dependensi Aspose.Words ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Sekarang setelah dasar-dasar sudah siap, mari kita mulai.

## cara menyisipkan group shape – Ikhtisar

Ide dasarnya sederhana: buat sebuah `Document`, buka `DocumentBuilder`, sisipkan **group shape**, lalu letakkan shape individu (sebuah persegi panjang dan sebuah lingkaran) ke dalam grup tersebut. Grup berfungsi seperti kontainer, sehingga memindahkannya nanti akan memindahkan semua yang ada di dalamnya – ideal untuk tata letak yang kompleks.

Di bawah ini adalah kode lengkap yang siap dijalankan. Silakan salin‑tempel ke kelas Java baru bernama `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro tip:** Nilai `setLeft` dan `setTop` bersifat relatif terhadap asal grup, bukan halaman. Ini membuat pemindahan seluruh grup menjadi sangat mudah nanti.

### Apa yang baru saja terjadi?

1. **Document & Builder** – Kami membuat file Word kosong dan `DocumentBuilder` yang memungkinkan kami menyisipkan konten.
2. **Group Shape** – `builder.insertGroupShape()` membuat sebuah kontainer. Anggap saja ini sebagai folder untuk objek gambar.
3. **Blue Rectangle** – Kami menginstansiasi `Shape` tipe `RECTANGLE`, mengatur ukuran, posisinya, dan mengisinya dengan biru – itulah langkah **create colored rectangle**.
4. **Red Circle** – Pola yang sama, tetapi menggunakan `ELLIPSE` untuk lingkaran sempurna, lalu mengisinya merah – itulah bagian **create colored circle**.
5. **Saving** – Akhirnya kami menyimpan semuanya ke `GroupShapeDemo.docx`.

Jalankan program (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) dan buka file yang dihasilkan. Anda akan melihat persegi panjang biru di sebelah kiri dan lingkaran merah di sebelah kanan, keduanya terkunci di dalam satu kotak grup.

## Menambahkan Shape Persegi Panjang

Jika Anda hanya membutuhkan persegi panjang tanpa pengelompokan, Anda dapat melewatkan pemanggilan `insertGroupShape()` dan menambahkan persegi panjang langsung ke body dokumen. Namun, pengelompokan memberi Anda fleksibilitas untuk memindahkan, memutar, atau menghapus beberapa shape sekaligus.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Perhatikan bagaimana kami menggunakan logika **add rectangle shape** di sini. Persegi panjang muncul di halaman sebagai objek independen. Dalam kebanyakan skenario dunia nyata Anda akan menginginkan grup, karena ia mempertahankan posisi relatif.

## Menetapkan Dimensi Shape

Saat Anda melihat metode seperti `setWidth` dan `setHeight`, ingat bahwa mereka menerima **points** (1/72 inci). Jika Anda lebih suka milimeter, konversikan dulu:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Potongan kode ini menunjukkan **set shape dimensions** dengan konversi satuan – berguna ketika spesifikasi desain Anda berasal dari mockup UI yang menggunakan satuan metrik.

## Membuat Persegi Panjang Berwarna

Memberi warna pada shape semudah memanggil `getFill().setForeColor()`. Anda dapat memberikan warna apa pun dari `java.awt.Color`. Ingin gradien? Gunakan `setForeColor` untuk warna awal dan `setBackColor` untuk warna akhir.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Itulah cara cepat **create colored rectangle** dengan isian gradien alih-alih warna solid.

## Membuat Lingkaran Berwarna

Lingkaran hanyalah elips dengan lebar dan tinggi yang sama. Logika pewarnaan yang sama berlaku:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Jika Anda memerlukan isian transparan, atur kanal alfa:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Sekarang Anda telah menguasai teknik **create colored circle**.

## Menyimpan Dokumen

Aspose.Words memungkinkan Anda mengekspor ke banyak format: DOCX, PDF, HTML, PNG, dan lain‑lain. Untuk demo ini kami tetap menggunakan DOCX karena mempertahankan shape vektor dengan sempurna.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Mengganti `SaveFormat` saja sudah cukup untuk menghasilkan versi PDF dari karya grup yang sama.

## Kesalahan Umum & Cara Menghindarinya

- **Lupa menambahkan shape ke grup?** Shape akan muncul di halaman tetapi tidak akan bergerak bersama grup. Selalu panggil `group.appendChild(yourShape)`.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Shape Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara membuat field formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Buat shape persegi panjang di Word dengan Aspose.Words – Panduan langkah demi langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}