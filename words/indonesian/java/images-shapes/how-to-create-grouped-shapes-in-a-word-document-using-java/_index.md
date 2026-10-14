---
category: general
date: 2026-10-13
description: Pelajari cara membuat bentuk berkelompok di Word dengan Java. Panduan
  ini menunjukkan cara menyisipkan bentuk grup, menambahkan garis ke grup, dan mengelompokkan
  beberapa bentuk di seluruh dokumen Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: id
lastmod: 2026-10-13
og_description: Buat bentuk yang dikelompokkan di Word dengan Java. Ikuti tutorial
  lengkap ini untuk menyisipkan bentuk grup, menambahkan garis ke grup, dan mengelompokkan
  beberapa bentuk dalam dokumen Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Buat bentuk terkelompok di Word dengan Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cara membuat grup bentuk dalam dokumen Word menggunakan Java
url: /id/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat grouped shapes dalam dokumen Word menggunakan Java

Jika Anda perlu **create grouped shapes** dalam file Microsoft Word dari Java, tutorial ini akan memandu Anda melalui seluruh proses. Anda akan melihat cara **insert group shape**, menempatkan sebuah persegi panjang dan sebuah garis di dalam kontainer yang sama, dan akhirnya menyimpan dokumen dengan grafik yang dikelompokkan.

Mengelompokkan bentuk memudahkan untuk memindahkan, mengubah ukuran, atau memberi gaya pada beberapa objek gambar sebagai satu unit—sempurna untuk diagram, flowcharts, atau dekorasi halaman khusus. Pada akhir panduan ini Anda akan dapat **add line to group**, **group multiple shapes word** dokumen, dan menggunakan kembali teknik yang sama untuk sejumlah bentuk apa pun.

## Prasyarat

- Java 17 atau yang lebih baru terpasang pada mesin pengembangan Anda.  
- Lisensi Aspose.Words for Java (atau evaluasi gratis).  
- Proyek Maven atau Gradle di mana Anda dapat menambahkan dependensi Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Tidak diperlukan pustaka tambahan.

## Langkah 1: Sisipkan kontainer group shape

Langkah pertama adalah **insert group shape** ke dalam dokumen. Kontainer ini akan menampung setiap bentuk berikutnya.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` membuat objek `Shape` kosong bertipe `GROUPSHAPE`. Anggaplah ini sebagai kanvas transparan yang dapat menampung objek gambar lainnya.

## Langkah 2: Tambahkan persegi panjang ke grup

Persegi panjang sering berfungsi sebagai latar visual untuk sekumpulan bentuk.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Mengatur `Left` dan `Top` ke `0` menempatkan persegi panjang di sudut kiri‑atas grup. Anda dapat mengubah nilai-nilai ini untuk menggeser bentuk di dalam grup.

## Langkah 3: **Add line to group** – buat bentuk garis

Sekarang kita **add line to group**. Garis akan muncul di bawah persegi panjang.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

Properti `Top` memindahkan garis 60 point di bawah persegi panjang, menciptakan tata letak bertumpuk sederhana. Anda juga dapat mengatur `Left` jika memerlukan offset horizontal.

## Langkah 4: Simpan dokumen dengan bentuk yang dikelompokkan

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Saat Anda membuka `GroupShapeDemo.docx` di Microsoft Word, Anda akan melihat satu grup yang berisi baik persegi panjang maupun garis. Memilih grup memungkinkan Anda memindahkan kedua bentuk sekaligus, yang menunjukkan bahwa Anda telah berhasil **group multiple shapes word**.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap dengan semua impor dan penanganan error. Salin ke IDE Anda, ganti `YOUR_DIRECTORY` dengan jalur folder yang ada, dan jalankan.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Output yang diharapkan

- Sebuah file bernama `GroupShapeDemo.docx` muncul di folder target.  
- Membuka file di Word menampilkan satu objek yang dikelompokkan berisi persegi panjang di atas dan garis di bawahnya.  
- Menyeret grup memindahkan kedua bentuk sekaligus, mengonfirmasi bahwa Anda telah **created grouped shapes** dengan sukses.

## Tips dan jebakan umum

- **Pro tip:** Jika Anda perlu memutar atau memberi gaya pada bentuk individual di dalam grup, panggil setter yang bersangkutan (`setRotation`, `getFill().setForeColor`, dll.) sebelum menambahkannya ke grup. Grup akan mempertahankan properti visual tersebut.
- **Watch out for:** Lupa mengatur properti `Top` untuk garis dapat menyebabkan tumpang tindih dengan persegi panjang, membuat grup terlihat berantakan.
- **Edge case:** Saat Anda menambahkan lebih dari dua bentuk, ingat bahwa koordinat setiap anak relatif terhadap asal grup (0,0). Rencanakan tata letak sesuai.
- **Performance note:** Mengelompokkan sejumlah besar bentuk (ratusan) dapat sedikit meningkatkan ukuran file, tetapi menyederhanakan penyuntingan selanjutnya di Word.

## Cara **group multiple shapes word** dokumen secara programatis

Pola yang ditunjukkan di atas—membuat kontainer grup, mengonfigurasi setiap bentuk anak, dan menambahkannya—berfungsi untuk jumlah bentuk apa pun: lingkaran, gambar, kotak teks, dll. Cukup ulangi langkah “create shape → set properties → append” sebelum memanggil `doc.save()`.

Jika Anda perlu **add line to group** setelah grup sudah berisi bentuk lain, Anda dapat mengambil grup yang ada dengan:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Ini menunjukkan bahwa Anda dapat memodifikasi grup pada titik mana pun dalam siklus hidup dokumen.

## Kesimpulan

Anda sekarang tahu cara **create grouped shapes** dalam dokumen Word menggunakan Java dan Aspose.Words. Dengan **inserting group shape**, **adding line to group**, dan **group multiple shapes word**, Anda dapat membuat gambar kompleks yang berperilaku sebagai satu objek—ideal untuk diagram, templat, dan pembuatan laporan otomatis.

Selanjutnya, jelajahi topik terkait berikut:

- **Applying styles to grouped shapes** – pelajari cara mengatur warna isi, batas, dan efek untuk semua anak sekaligus.  
- **Exporting grouped shapes to PDF** – lihat bagaimana grup yang sama tetap ada saat Anda mengonversi dokumen.  
- **Animating shapes with VBA** – gabungkan grup yang dihasilkan Java dengan makro Word untuk dokumen interaktif.

Silakan bereksperimen dengan berbagai tipe bentuk, ukuran, dan posisi. Pengelompokan memberi Anda fleksibilitas untuk memperlakukan banyak objek sebagai satu, menyederhanakan baik kode maupun interaksi pengguna. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}