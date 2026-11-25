---
category: general
date: 2026-11-25
description: Cara mengelompokkan bentuk di Word menggunakan Java dan cara mengatur
  dimensi bentuk dalam file DOCX dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: id
lastmod: 2026-11-25
og_description: Cara mengelompokkan bentuk di Word dengan Aspose.Words Java API dan
  mengatur ukuran bentuk di Word dengan cepat. Ikuti solusi langkah demi langkah yang
  lengkap.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Cara mengelompokkan bentuk di Word dan mengatur dimensinya – Panduan Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Cara mengelompokkan bentuk di Word dan mengatur dimensinya secara programatik
url: /id/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di Word dan mengatur dimensinya secara programatis

Jika Anda perlu **cara mengelompokkan bentuk di Word** dan mengontrol ukuran tepatnya, panduan ini menunjukkan solusi lengkap yang dapat dijalankan. Dengan menggunakan Aspose.Words for Java Anda dapat membuat sebuah persegi panjang, sebuah elips, menambahkannya ke dalam `GroupShape`, dan kemudian **cara mengatur dimensi bentuk** seperti lebar dan tinggi dalam satu file DOCX.

Anda akan belajar cara:

* Membuat dokumen Word baru dari awal.  
* Menyisipkan `GroupShape` (API baru pada versi 24.9).  
* Menambahkan persegi panjang dan elips ke dalam grup.  
* **Set shape size Word** secara tepat dengan `setWidth` dan `setHeight`.  
* Menyimpan dokumen ke disk.

Tidak diperlukan alat eksternal—hanya Java 17+, Maven, dan pustaka Aspose.Words for Java.

## Prasyarat

* Java Development Kit 17 atau yang lebih baru.  
* Maven (atau Gradle) untuk manajemen dependensi.  
* Aspose.Words for Java 24.9 atau lebih baru (API `GroupShape` diperkenalkan pada 24.9).  
* Familiaritas dasar dengan sintaks Java dan konsep berorientasi objek.

Jika Anda belum menambahkan Aspose.Words ke proyek Anda, sertakan dependensi Maven berikut:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Langkah 1: Buat dokumen baru dan DocumentBuilder

Kelas `Document` mewakili seluruh file Word, sementara `DocumentBuilder` menyediakan cara yang nyaman untuk menambahkan konten.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa langkah ini?*  
Membuat `Document` baru memberi Anda kanvas bersih. `DocumentBuilder` adalah pembantu tingkat tinggi yang memungkinkan Anda menyisipkan paragraf, tabel, dan, dalam kasus ini, bentuk.

## Langkah 2: Sisipkan GroupShape (API baru pada versi 24.9)

`GroupShape` berfungsi seperti wadah; setiap bentuk yang Anda tambahkan menjadi bagian dari grup visual yang sama.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Mengapa menggunakan `GroupShape`?*  
Mengelompokkan bentuk menyederhanakan pemindahan, rotasi, atau penerapan format ke beberapa objek sekaligus. API ini ditambahkan pada 24.9, sehingga versi yang lebih lama tidak akan dapat mengompilasi baris ini.

## Langkah 3: Buat persegi panjang, atur ukurannya, dan tambahkan ke grup

Di sini kami mendemonstrasikan **cara mengatur dimensi bentuk** untuk sebuah persegi panjang.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Mengapa mengatur lebar dan tinggi secara eksplisit?*  
Word menyimpan ukuran bentuk dalam poin. Dengan memanggil `setWidth` dan `setHeight` Anda mengontrol jejak visual yang tepat, yang penting ketika Anda memerlukan tata letak yang presisi atau saat mengekspor ke PDF.

## Langkah 4: Buat elips, atur ukurannya, dan tambahkan ke grup yang sama

Teknik **set shape size word** yang sama berlaku untuk jenis bentuk apa pun.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Mengapa menambahkan elips ke `GroupShape` yang sama?*  
Kedua bentuk akan bergerak bersama sebagai satu unit. Ini berguna untuk membuat ikon, logo, atau diagram kompleks yang harus tetap selaras.

## Langkah 5: Simpan dokumen dengan bentuk yang dikelompokkan

Akhirnya, persistenkan file DOCX ke disk.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Menjalankan program ini menghasilkan file bernama **GroupShape.docx** yang berisi sebuah persegi panjang dan sebuah elips yang dikelompokkan bersama. Saat Anda membuka file tersebut di Microsoft Word, Anda akan melihat dua bentuk berperilaku sebagai satu objek—Anda dapat menyeret, mengubah ukuran, atau memutarnya secara bersamaan.

### Output yang diharapkan

* Sebuah dokumen Word (`GroupShape.docx`) dengan satu halaman.  
* Sebuah `GroupShape` yang berisi persegi panjang 100 × 50 pt dan elips 80 × 80 pt.  
* Memilih salah satu bentuk akan memilih seluruh grup.

## Pertanyaan umum dan kasus tepi

### Bagaimana mengubah posisi bentuk yang dikelompokkan?

Setelah membuat `GroupShape`, Anda dapat mengatur properti `left` dan `top`-nya:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Koordinat ini juga diukur dalam poin.

### Bagaimana jika saya perlu menambahkan lebih dari dua bentuk?

`GroupShape` berfungsi seperti node wadah lainnya. Panggil `groupShape.appendChild(yourShape)` untuk setiap bentuk tambahan. API tidak membatasi jumlah anak.

### Bisakah saya menerapkan gaya (warna isi, ketebalan garis) pada bentuk individual?

Ya. Setiap objek `Shape` mengekspos properti pemformatan:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Apakah kode ini bekerja dengan versi Aspose.Words yang lebih lama?

Metode `insertGroupShape` diperkenalkan pada versi 24.9. Jika Anda menggunakan versi sebelumnya, Anda harus membuat `GroupShape` secara manual melalui pohon node, yang lebih rumit. Memperbarui ke versi terbaru adalah jalur yang disarankan.

## Tips profesional

* **Gunakan poin untuk konsistensi** – Unit internal Word adalah poin (1/72 inci). Mengonversi dari piksel atau sentimeter dapat menghasilkan ukuran yang tidak terduga.  
* **Kelompokkan sebelum memposisikan** – Posisi `GroupShape` setelah Anda menambahkan semua anaknya; jika tidak, Anda mungkin perlu menghitung ulang offset.  
* **Gunakan kembali DocumentBuilder** – Anda dapat menyisipkan beberapa grup dalam dokumen yang sama dengan memindahkan kursor builder (`builder.moveTo`) sebelum setiap pemanggilan `insertGroupShape`.

## Kesimpulan

Anda kini memiliki contoh lengkap dari **cara mengelompokkan bentuk di Word** dan **cara mengatur dimensi bentuk** menggunakan Aspose.Words for Java. Tutorial ini mencakup pembuatan dokumen, penyisipan `GroupShape`, penambahan persegi panjang dan elips, pengaturan ukuran tepat mereka, serta penyimpanan hasilnya.  

Dari sini Anda dapat mengeksplorasi:

* Menambahkan kotak teks atau gambar ke grup yang sama.  
* Menganimasikan bentuk yang dikelompokkan dengan fitur smart art Word (melalui API).  
* Mengekspor bentuk yang dikelompokkan ke PDF atau SVG untuk penggunaan web.

Silakan bereksperimen dengan berbagai jenis bentuk, ukuran, dan posisi—pengelompokan memberi Anda kontrol kuat atas tata letak kompleks dalam dokumen Word.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}