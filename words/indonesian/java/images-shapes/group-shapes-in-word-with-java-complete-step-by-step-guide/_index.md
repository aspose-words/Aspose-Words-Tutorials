---
category: general
date: 2026-08-01
description: Kelompokkan bentuk di Word dengan Java menggunakan Aspose.Words. Pelajari
  cara mengelompokkan bentuk dan menyisipkan bentuk persegi panjang dengan cepat menggunakan
  contoh kode lengkap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: id
lastmod: 2026-08-01
og_description: Mengelompokkan bentuk di Word menggunakan Java. Panduan ini menunjukkan
  cara mengelompokkan bentuk, menyisipkan bentuk persegi panjang, dan menyimpan DOCX
  dengan Aspose.Words.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Mengelompokkan Bentuk di Word dengan Java – Panduan Pemrograman Lengkap
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Mengelompokkan Bentuk di Word dengan Java – Panduan Lengkap Langkah demi Langkah
url: /id/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengelompokkan Bentuk di Word dengan Java – Panduan Lengkap Langkah demi Langkah

Jika Anda perlu **mengelompokkan bentuk di Word** menggunakan Java, panduan ini siap membantu. Baik Anda sedang membangun generator laporan atau mesin templat dinamis, mengelompokkan bentuk membuat dokumen Anda tampak rapi dan menjaga grafik yang terkait tetap bersama.

Dalam beberapa menit ke depan Anda akan melihat **cara mengelompokkan bentuk** dan **menyisipkan objek bentuk persegi panjang** dengan Aspose.Words, serta beberapa tips praktis yang menyelamatkan Anda dari jebakan umum. Siap mengubah persegi panjang dan elips yang terpisah menjadi satu grup yang rapi? Mari kita mulai.

## Apa yang Dibahas dalam Tutorial Ini

* Prasyarat minimal (Java 17+, Aspose.Words 24.10 atau lebih baru).  
* Program Java lengkap yang dapat dijalankan, yang membuat dokumen Word, menyisipkan persegi panjang dan elips, mengelompokkannya, menyembunyikan grup jika diinginkan, dan menyimpan file.  
* Mengapa setiap panggilan API penting, bukan hanya apa yang dilakukannya.  
* Penanganan kasus tepi untuk versi Aspose.Words yang lebih lama dan untuk mengelompokkan lebih dari dua bentuk.  
* Output yang diharapkan dan cara cepat memverifikasi hasilnya.

Pada akhir tutorial Anda akan dapat menambahkan potongan kode ini ke proyek Java apa pun dan mulai mengelompokkan bentuk di Word tanpa harus mencari-cari dokumentasi yang tersebar.

---

## Prasyarat

| Persyaratan | Mengapa penting |
|-------------|----------------|
| **Java 17+** | Fitur bahasa modern dan kinerja yang lebih baik. |
| **Aspose.Words for Java 24.10+** | Metode `setHidden` yang digunakan nanti hanya ada mulai versi ini. |
| **Build Maven atau Gradle** | Memudahkan manajemen dependensi. |
| **IDE (IntelliJ, Eclipse, VS Code)** | Membantu untuk pengujian cepat, tetapi editor teks apa pun juga dapat digunakan. |

Tambahkan dependensi Aspose.Words Maven ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Jika Anda lebih suka Gradle, setaraannya adalah:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Langkah 1: Buat Dokumen Baru dan Builder

Pertama kita buat `Document` kosong dan `DocumentBuilder`. Builder adalah mesin utama yang memungkinkan kita menyisipkan bentuk, teks, dan lainnya.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Mengapa langkah ini?*  
`Document` mewakili seluruh file DOCX, sementara `DocumentBuilder` menyediakan API berbasis kursor yang nyaman. Tanpa builder Anda harus memanipulasi koleksi node tingkat rendah secara manual—sesuatu yang mudah salah.

---

## Langkah 2: Sisipkan Bentuk Persegi Panjang (dan Elips)

Sekarang kita tambahkan dua bentuk dasar yang ingin dikelompokkan. Perhatikan panggilan **insert rectangle shape**—ini adalah kata kunci sekunder yang Anda cari.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

Beberapa hal yang perlu diingat:

* Lebar (`100`) dan tinggi (`50`) diukur dalam poin (1 pt ≈ 1/72 in). Sesuaikan sesuai tata letak Anda.  
* Persegi panjang digambar pertama, sehingga berada di belakang elips secara default. Jika Anda memerlukan urutan sebaliknya, sisipkan elips terlebih dahulu.  
* Kedua bentuk mewarisi format builder saat ini (warna, gaya garis). Anda dapat menyesuaikannya sebelum mengelompokkan jika diinginkan.

---

## Langkah 3: Cara Mengelompokkan Bentuk dengan Aspose.Words

Berikut inti tutorial—**cara mengelompokkan bentuk**. API `insertGroupShape` menerima array bentuk yang sudah ada dan mengembalikan `Shape` baru yang mewakili grup.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Mengapa menggunakan grup?  

* Grup bergerak sebagai satu unit, mempertahankan posisi relatif.  
* Anda dapat menerapkan transformasi (rotasi, skala) ke seluruh set dengan satu panggilan.  
* Pengelompokan menyederhanakan penyuntingan selanjutnya—bisa melakukan un‑group bila perlu mengubah elemen individual.

---

## Langkah 4 (Opsional): Sembunyikan Grup dari Tampilan Dokumen

Jika Anda tidak ingin grup muncul ketika pengguna membuka dokumen di Word, Anda dapat menyembunyikannya. Langkah ini opsional tetapi berguna untuk grafik latar belakang atau watermark.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**Bagaimana jika Anda menggunakan versi Aspose.Words yang lebih lama?**  
Metode `setHidden` tidak akan dapat dikompilasi. Dalam kasus ini Anda dapat mencapai efek serupa dengan mengatur `WrapType` bentuk menjadi `NONE` dan memindahkannya ke belakang lapisan teks:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

Metode ini sedikit lebih panjang, tetapi tetap membuat grup tidak mengganggu pembaca.

---

## Langkah 5: Simpan Dokumen

Akhirnya, tuliskan dokumen ke disk. Ubah jalur sesuai tempat Anda ingin file disimpan.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

Saat Anda membuka `GroupShapeResult.docx` di Microsoft Word, Anda akan melihat persegi panjang dan elips yang terkelompok rapi. Jika Anda mengatur `setHidden(true)`, grup akan tidak terlihat di editor tetapi tetap ada dalam file (berguna untuk pemrosesan programatik nanti).

---

## Contoh Kerja Lengkap

Menggabungkan semuanya, berikut kelas Java lengkap yang dapat Anda salin‑tempel ke proyek Anda:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Output yang diharapkan:** Sebuah file bernama `GroupShapeResult.docx` yang berisi satu grup yang memuat persegi panjang berisi biru dan elips berpinggiran merah (warna default). Jika Anda membuka dokumen, pilih grup, dan klik kanan → **Group → Ungroup**, Anda akan melihat dua bentuk asli muncul kembali.

---

## Pertanyaan Umum & Kasus Tepi

### 1. Bisakah saya mengelompokkan lebih dari dua bentuk?

Tentu saja. Cukup kirim array yang lebih besar ke `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

API berskala secara linear; satu‑satunya batasan adalah memori untuk grup yang sangat besar.

### 2. Bagaimana jika saya perlu mengubah posisi grup setelah dibuat?

Gunakan metode `setLeft` dan `setTop` pada grup, sama seperti pada bentuk lainnya:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Karena grup berperilaku seperti satu bentuk, semua bentuk anak bergerak bersama.

### 3. Bagaimana cara menerapkan border atau isi pada seluruh grup?

Grup itu sendiri dapat memiliki format, tetapi tidak memengaruhi anak secara langsung. Jika Anda menginginkan border bersama, bungkus bentuk-bentuk dalam bentuk persegi panjang terlebih dahulu, lalu kelompokkan semuanya. Alternatifnya, iterasi setiap bentuk anak dan atur `fillColor` atau `strokeWeight` yang sama.

### 4. Apakah `setHidden(true)` memengaruhi pencetakan?

Bentuk tersembunyi **tidak** dicetak secara default di Word, yang dapat berguna untuk watermark atau penanda templat. Jika Anda membutuhkan bentuk tetap tercetak tetapi tidak terlihat di layar, Anda harus menggunakan pendekatan lain (misalnya, atur opacity menjadi 0%).

---

## Tips Pro dari Pengalaman Lapangan

* **Berikan nama pada bentuk Anda** – `groupShape.setName("HeaderGraphics");` memudahkan debugging ketika Anda nanti mengambil bentuk berdasarkan nama.  
* **Gunakan kembali builder** – Setelah menyisipkan grup, kursor builder tetap berada di tempat grup ditempatkan, sehingga Anda dapat melanjutkan menambahkan paragraf tepat setelah grup tanpa mengatur ulang posisi.  
* **Guard versi** – Jika Anda mendistribusikan pustaka yang mungkin dijalankan pada versi Aspose.Words yang lebih lama, bungkus pemanggilan `setHidden` dalam try‑catch untuk `NoSuchMethodError` dan gunakan trik `WrapType.NONE` yang ditunjukkan sebelumnya.  
* **Tip kinerja** – Saat menghasilkan ribuan  

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rendering Shapes in Aspose.Words for Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}