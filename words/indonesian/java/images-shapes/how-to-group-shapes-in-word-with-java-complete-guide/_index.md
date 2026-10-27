---
category: general
date: 2026-10-16
description: Pelajari cara mengelompokkan bentuk di Word menggunakan Java. Tutorial
  ini menunjukkan cara menambahkan bentuk persegi panjang, mengatur ukuran dan dimensi
  bentuk, serta menyimpan dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: id
lastmod: 2026-10-16
og_description: Kelompokkan bentuk di Word menggunakan Java. Tambahkan bentuk persegi
  panjang, atur ukuran dan dimensi bentuk, serta buat dokumen profesional secara programatik.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Mengelompokkan bentuk di Word dengan Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Cara mengelompokkan bentuk di Word dengan Java – panduan lengkap
url: /id/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di Word dengan Java – panduan lengkap

Jika Anda perlu **mengelompokkan bentuk di Word** secara programatis, tutorial ini memberikan solusi siap‑jalankan. Anda akan melihat cara **menambahkan bentuk persegi panjang**, menyesuaikan ukurannya, mengatur dimensi bentuk, dan akhirnya menyimpan file DOCX yang berisi persegi panjang yang dikelompokkan dan sebuah elips.

Mengelompokkan bentuk di Word berguna untuk membuat diagram kompleks, membuat komponen grafis yang dapat digunakan kembali, atau sekadar menjaga objek terkait tetap bersama saat dokumen diedit nanti. Kode ini menggunakan pustaka Aspose.Words for Java, yang bekerja dengan JDK terbaru apa pun dan tidak memerlukan Microsoft Word terpasang.

## Prasyarat

| Persyaratan | Alasan |
|-------------|--------|
| Java 17 (or later) | Perpustakaan menargetkan runtime Java modern. |
| Aspose.Words for Java (latest version) | Menyediakan kelas `Document`, `DocumentBuilder`, `GroupShape`, dan `Shape` yang digunakan dalam contoh. |
| IDE atau alat build (Maven/Gradle) | Untuk mengkompilasi dan menjalankan contoh. |
| Pengetahuan dasar tentang sintaks Java | Diperlukan untuk memahami alur kode. |

Tambahkan dependensi Aspose.Words ke proyek Anda. Untuk Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Atau untuk Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Ikhtisar solusi

Tutorial ini mengikuti pola **masalah → solusi → penjelasan** yang jelas:

1. **Buat dokumen Word baru** dan dapatkan `DocumentBuilder`.  
2. **Sisipkan kontainer `GroupShape`** yang akan menampung beberapa bentuk.  
3. **Tambahkan persegi panjang**, atur lebar/tingginya (langkah **set shape size**), dan lampirkan ke grup.  
4. **Tambahkan elips**, posisikan di dalam grup yang sama, dan juga atur dimensinya.  
5. **Simpan** dokumen ke disk.

Setiap langkah menyertakan **mengapa** di balik kode, sehingga Anda memahami apa yang dilakukan API dan bagaimana Anda dapat menyesuaikannya untuk skenario lain.

## Langkah 1: Buat dokumen dan DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Mengapa ini penting:** `Document` mewakili seluruh file DOCX, sementara `DocumentBuilder` adalah pembantu yang memungkinkan Anda menyisipkan konten tanpa harus mengelola node tingkat rendah. Membuatnya terlebih dahulu memberi Anda kanvas bersih untuk semua operasi bentuk selanjutnya.

## Langkah 2: Sisipkan kontainer GroupShape

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`GroupShape` berfungsi seperti **folder** untuk objek gambar. Ketika Anda memindahkan, memutar, atau menghapus grup, semua bentuk anak akan mengikuti secara otomatis. Ini adalah inti dari **group shapes in word**.

## Langkah 3: Tambahkan bentuk persegi panjang – kode bentuk persegi panjang

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – Konstruktor `Shape` menerima `ShapeType.RECTANGLE`, yang memberi tahu Aspose.Words untuk menggambar outline persegi panjang.  
- **set shape size** – `setWidth` dan `setHeight` menentukan **dimensi bentuk** dalam poin (1 pt = 1/72 in). Ini adalah cara paling umum untuk mengontrol ukuran visual.  
- **Why we use `appendChild`** – Ini melampirkan persegi panjang ke `GroupShape` sehingga bergerak bersama grup.

## Langkah 4: Tambahkan elips dan posisikan di dalam grup

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

Elips ini menunjukkan **set shape dimensions** di luar persegi panjang sederhana. Dengan memanggil `setLeft`, kami mengontrol offset horizontal di dalam grup, yang berguna saat menyusun beberapa objek.

## Langkah 5: Simpan dokumen

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Saat Anda membuka *GroupShapeDemo.docx* di Microsoft Word, Anda akan melihat sebuah persegi panjang dan sebuah elips yang terkunci bersama di dalam satu grup. Memilih salah satu bentuk akan memilih seluruh grup—tepat seperti yang Anda harapkan ketika **group shapes in word**.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut adalah file sumber lengkap yang dapat Anda salin ke IDE Anda:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Output yang diharapkan

- Sebuah file bernama **GroupShapeDemo.docx** muncul di folder proyek.  
- Membuka file di Word menampilkan dua bentuk (sebuah persegi panjang dan sebuah elips) yang dikelompokkan bersama.  
- Menyeret salah satu bentuk memindahkan seluruh grup, mengonfirmasi bahwa **group shapes in word** berfungsi sebagaimana mestinya.

## Variasi umum dan kasus tepi

| Skenario | Apa yang diubah | Mengapa |
|----------|----------------|-----|
| **Berbagai tipe bentuk** (mis., segitiga) | Use `ShapeType.TRIANGLE` or any other enum value when constructing `Shape`. | Memungkinkan Anda membangun diagram yang lebih kompleks. |
| **Mengatur warna isi** | Call `shape.getFillColor().setColor(Color.BLUE);` after creating the shape. | Meningkatkan tampilan visual tanpa memengaruhi pengelompokan. |
| **Memutar grup** | `groupShape.setRotationAngle(45);` | Memutar semua bentuk anak bersama-sama, berguna untuk ikon. |
| **Menambahkan teks di dalam bentuk** | `shape.appendChild(new Paragraph(document));` then add a `Run` with text. | Membuat bentuk berfungsi sebagai label atau callout. |
| **Menyimpan ke stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Berguna untuk layanan web yang mengembalikan dokumen secara langsung. |

### Tips profesional

Ketika Anda perlu **set shape dimensions** berdasarkan data dinamis (mis., panjang barcode), hitung lebar/tinggi dalam poin terlebih dahulu:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

## Kesimpulan

Anda sekarang tahu cara **group shapes in Word** menggunakan Java, cara **add rectangle shape**, dan cara **set shape size** serta **set shape dimensions** dengan kode yang ringkas dan siap produksi. Dengan mengikuti langkah-langkah di atas, Anda dapat membuat grup grafis yang dapat digunakan kembali, menyematkannya dalam laporan otomatis, atau membangun alat diagram khusus tanpa pernah membuka Word secara manual.

### Apa selanjutnya?

- Jelajahi variasi **add rectangle shape** seperti sudut melengkung (`ShapeType.RECTANGLE` dengan `setCornerRadius`).  
- Gabungkan **group shapes in word** dengan tabel atau diagram untuk dokumen yang lebih kaya.  
- Pelajari API Aspose.Words untuk **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) guna mengontrol bagaimana teks di sekitar berinteraksi dengan grafik yang dikelompokkan.

Silakan bereksperimen, sesuaikan **rectangle shape code**, dan bagikan hasil Anda


## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Buat bentuk persegi panjang di Word dengan Java – Panduan Lengkap](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Buat Group Shape di Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}