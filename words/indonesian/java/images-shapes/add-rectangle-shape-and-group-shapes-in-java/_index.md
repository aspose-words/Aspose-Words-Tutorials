---
category: general
date: 2026-11-22
description: Tambahkan bentuk persegi panjang ke dokumen Word dengan Java, atur ukuran
  bentuk, kelompokkan beberapa bentuk, dan tambahkan bentuk ke grup secara efisien.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: id
lastmod: 2026-11-22
og_description: Tambahkan bentuk persegi panjang dalam dokumen Word menggunakan Java,
  kemudian atur ukuran bentuk, kelompokkan beberapa bentuk, dan tambahkan bentuk ke
  grup dalam satu alur kerja.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Menambahkan bentuk persegi panjang dan mengelompokkan bentuk di Java – panduan
  lengkap
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Tambahkan bentuk persegi panjang dan grupkan bentuk di Java
url: /id/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menambahkan bentuk persegi panjang dan mengelompokkan bentuk dalam Java

Jika Anda perlu **menambahkan bentuk persegi panjang** ke dokumen Word dengan Java, panduan ini akan memandu Anda melalui langkah‑langkah yang tepat. Anda juga akan belajar cara **mengatur ukuran bentuk**, **mengelompokkan beberapa bentuk**, dan **menambahkan bentuk ke grup** tanpa meninggalkan IDE.

Bekerja dengan grafik vektor di dalam file DOCX sering terasa seperti menyeimbangkan beberapa API. Pada akhir tutorial ini Anda akan memiliki program tunggal yang berdiri sendiri yang membuat sebuah persegi panjang, sebuah elips, dan bentuk tambahan apa pun yang Anda perlukan, kemudian mengelompokkannya sehingga mereka bergerak sebagai satu objek. Tidak ada alat eksternal yang diperlukan selain Aspose.Words for Java.

## Prasyarat

* Java 17 atau yang lebih baru terpasang.
* Maven 3.8+ (atau Gradle) untuk mengelola dependensi.
* Lisensi Aspose.Words for Java yang valid (evaluasi dapat digunakan untuk pengujian).
* IDE seperti IntelliJ IDEA atau VS Code, meskipun editor teks apa pun dapat digunakan.

Persyaratan ini memungkinkan kode dikompilasi dan dijalankan pada lingkungan pengembangan modern apa pun.

## Langkah 1: Menyiapkan proyek Maven

Buat proyek Maven baru atau tambahkan dependensi Aspose.Words ke `pom.xml` yang sudah ada:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Dependensi tersebut mengimpor semua kelas yang diperlukan untuk manipulasi dokumen, termasuk `Document`, `DocumentBuilder`, `Shape`, dan `GroupShape`. Maven akan mengunduh JAR secara otomatis saat Anda menjalankan `mvn compile`.

## Langkah 2: Memuat dokumen dan membuat DocumentBuilder

`DocumentBuilder` menyediakan API fluens untuk menyisipkan konten. Muat DOCX yang ada atau mulai dari dokumen kosong:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Membuat builder lebih awal memberi Anda kursor yang diposisikan di awal dokumen, siap untuk penyisipan bentuk.

## Menambahkan bentuk persegi panjang ke dokumen Word

### Langkah 3: Menyisipkan bentuk persegi panjang

Persegi panjang adalah elemen visual pertama yang ingin kami tempatkan di dalam dokumen. Dengan menggunakan konstruktor `Shape` dengan `ShapeType.RECTANGLE`, Anda mendapatkan objek yang sepenuhnya dapat diedit.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Menambahkan persegi panjang pada titik ini tidak memengaruhi tata letak sampai ukurannya ditentukan dan ditambahkan ke sebuah kontainer.

### Mengatur ukuran dan dimensi bentuk

#### Langkah 4: Menentukan lebar dan tinggi

Menetapkan dimensi bentuk menentukan bagaimana bentuk tersebut muncul di halaman. Nilai lebar dan tinggi diukur dalam poin (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Anda dapat menyesuaikan angka-angka ini agar sesuai dengan kebutuhan desain Anda. Metode yang sama berlaku untuk setiap instance `Shape`, sehingga Anda dapat menggunakannya kembali untuk lingkaran, panah, atau gambar khusus.

#### Langkah 5: Menyisipkan persegi panjang ke dalam dokumen

Sekarang persegi panjang memiliki ukuran, tempatkan di halaman. Metode `insertShape` dari `DocumentBuilder` menambahkan bentuk pada posisi kursor saat ini.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

Pada tahap ini persegi panjang muncul sendiri di halaman. Langkah selanjutnya menunjukkan cara menggabungkannya dengan bentuk lain.

## Mengelompokkan beberapa bentuk bersama-sama

Mengelompokkan bentuk memungkinkan Anda memindahkan, memutar, atau mengubah ukuran mereka sebagai satu unit. Ini sangat berguna untuk membuat diagram yang kompleks.

### Langkah 6: Membuat kontainer grup bentuk

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Pemanggilan `insertGroupShape` menambahkan kontainer kosong ke dokumen. Setiap bentuk yang ditambahkan ke kontainer ini menjadi bagian dari grup.

### Menambahkan bentuk ke grup

#### Langkah 7: Menambahkan persegi panjang ke grup

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Penambahan memindahkan persegi panjang dari badan dokumen ke dalam koleksi internal grup. Persegi panjang kini menghormati transformasi grup.

#### Langkah 8: Menambahkan elips untuk demonstrasi

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Elips berbagi ruang koordinat yang sama dengan persegi panjang, sehingga Anda dapat menyelaraskannya secara visual dengan menyesuaikan properti `setLeft` dan `setTop` jika diperlukan.

### Langkah 9: Menyimpan dokumen

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Menjalankan program menghasilkan `output.docx`. Buka file tersebut di Microsoft Word atau LibreOffice; Anda akan melihat persegi panjang dan elips yang dikelompokkan bersama. Memilih salah satu bentuk menyorot seluruh grup, mengonfirmasi bahwa **menambahkan bentuk ke grup** berhasil.

![Contoh menambahkan bentuk persegi panjang dalam Java](image.png){alt="Contoh menambahkan bentuk persegi panjang dalam Java"}

*Tangkapan layar menunjukkan persegi panjang dan elips di dalam satu grup, siap untuk manipulasi bersama.*

## Mengapa pendekatan ini penting

* **Single source of truth** – Semua properti bentuk diatur sebelum grup dibuat, mencegah gangguan tata letak.
* **Reusability** – Metode `setWidth`/`setHeight` yang sama bekerja untuk bentuk apa pun, sehingga Anda dapat memperluas contoh ke panah, bintang, atau SVG khusus.
* **Performance** – Pengelompokan mengurangi jumlah objek gambar yang harus ditangani renderer Word, yang meningkatkan kecepatan membuka dokumen besar.
* **Maintainability** – Dengan menjaga pembuatan bentuk dan logika pengelompokan bersama, pengembang di masa depan dapat mengubah dimensi atau menambahkan bentuk baru tanpa mencari melalui kode yang tidak terkait.

## Variasi umum dan kasus tepi

| Skenario | Penyesuaian |
|----------|------------|
| **Berbeda satuan** | Gunakan konversi `PointsToPixels` atau set `Shape.setWrapType(WrapType.INLINE)` untuk penempatan inline. |
| **Memutar grup** | Panggil `groupShape.setRotation(45);` untuk memutar semua bentuk anak sebesar 45°. |
| **Menambahkan teks ke bentuk** | Gunakan `Shape.setText("Label");` setelah mengatur ukuran. |
| **Ukuran dinamis** | Ambil dimensi halaman melalui `doc.getFirstSection().getPageSetup().getPageWidth()` dan hitung ukuran bentuk secara proporsional. |

Variasi ini menggambarkan bagaimana pola inti—**menambahkan bentuk persegi panjang**, **mengatur ukuran bentuk**, **mengelompokkan beberapa bentuk**, **menambahkan bentuk ke grup**—beradaptasi dengan banyak kebutuhan dunia nyata.

## Kesimpulan

Anda sekarang tahu cara **menambahkan bentuk persegi panjang** ke dokumen Word menggunakan Java, **mengatur ukuran bentuk**, **mengelompokkan beberapa bentuk**, dan **menambahkan bentuk ke grup** dengan cara yang bersih dan dapat dipelihara. Contoh lengkap dikompilasi menjadi satu kelas yang dapat dijalankan, dan file DOCX yang dihasilkan menunjukkan output yang diharapkan.

Dari sini Anda dapat menjelajahi:

* Menambahkan label teks atau hyperlink ke setiap bentuk.
* Menyusun grup secara bersarang untuk membangun diagram hierarkis.
* Mengekspor dokumen ke PDF sambil mempertahankan grup bentuk.

Silakan bereksperimen dengan dimensi, warna, dan jenis bentuk tambahan yang berbeda. Menguasai manipulasi bentuk membuka pintu untuk pembuatan laporan otomatis, diagram dinamis, dan pengalaman dokumen yang kaya—semua langsung dari kode Java.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}