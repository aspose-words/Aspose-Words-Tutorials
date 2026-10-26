---
category: general
date: 2026-10-26
description: Pelajari cara membuat dokumen Word secara programatis, menambahkan bentuk,
  dan menyembunyikan objek di Word menggunakan Aspose.Words untuk Java – panduan langkah
  demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: id
lastmod: 2026-10-26
og_description: Buat dokumen Word secara programatik, pelajari cara menambahkan bentuk
  dan menyembunyikan objek di Word dengan Aspose.Words untuk Java. Contoh lengkap
  yang dapat dijalankan.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Buat dokumen Word secara programatis – tambahkan dan sembunyikan bentuk
  di Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Buat dokumen Word secara programatis dan tambahkan bentuk di Java
url: /id/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word secara programatis dan tambahkan bentuk di Java

Jika Anda perlu **membuat dokumen Word secara programatis**, tutorial ini menunjukkan secara tepat cara melakukannya, menambahkan bentuk, dan kemudian menyembunyikan objek di Word. Baik Anda sedang membangun generator laporan atau sistem kontrak otomatis, Anda akan mendapatkan solusi lengkap yang siap‑jalankan dalam hanya beberapa menit.

Anda akan belajar cara:

* Menginisialisasi dokumen Word dengan Aspose.Words for Java.  
* Menyisipkan elips (atau bentuk lain) menggunakan teknik **how to add shape**.  
* Menyembunyikan bentuk tersebut sehingga tidak pernah muncul saat file dibuka, menjawab pertanyaan **how to hide shape**.  

Tidak diperlukan alat eksternal selain pustaka Aspose.Words, dan kode ini bekerja dengan Java 17 dan yang lebih baru.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Java Development Kit (JDK) 17 atau yang lebih baru terpasang.  
* Maven atau Gradle untuk mengelola dependensi (contoh menggunakan Maven).  
* Lisensi Aspose.Words for Java yang valid (evaluasi gratis dapat digunakan untuk pengujian).  

Jika Anda baru mengenal Aspose.Words, lihat panduan Getting Started resmi, tetapi Anda tidak perlu membacanya untuk mengikuti tutorial ini.

## Dependensi Maven

Tambahkan dependensi berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Jaga nomor versi tetap terbaru; rilis yang lebih baru berisi perbaikan bug untuk penanganan bentuk.

## Langkah 1: Buat dokumen Word secara programatis – menginisialisasi dokumen

Hal pertama yang Anda lakukan ketika **membuat dokumen Word secara programatis** adalah menginstansiasi objek `Document`. Objek ini mewakili seluruh file .docx di memori.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa langkah ini penting*: Kelas `Document` adalah titik masuk untuk semua operasi pengolahan Word. Tanpa itu Anda tidak dapat menambahkan halaman, paragraf, atau bentuk.

## Langkah 2: Cara menambahkan bentuk – menyisipkan elips

Sekarang kita membahas bagian **how to add shape** dalam tutorial. Aspose.Words mendukung banyak tipe bentuk (Ellipse, Rectangle, TextBox, dll.). Di bawah ini kami menyisipkan elips dengan lebar dan tinggi 50 poin.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

Metode `insertShape` mengembalikan objek `Shape` yang dapat Anda sesuaikan lebih lanjut—warna, gaya garis, rotasi, dan lainnya. Koordinat diukur dalam poin (1/72 inci).

*Mengapa Anda mungkin ingin menambahkan bentuk*: Bentuk berguna untuk watermark, elemen dekoratif, atau placeholder yang kemudian Anda sembunyikan atau ganti.

## Langkah 3: Cara menyembunyikan bentuk – membuat objek tidak terlihat di Word

Untuk menjawab pertanyaan **how to hide shape**, cukup set properti `Hidden` pada bentuk menjadi `true`. Ini memberi tahu Word untuk memperlakukan bentuk sebagai objek tersembunyi, sehingga tidak pernah ditampilkan dalam tampilan dokumen atau hasil cetak.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Jika Anda perlu **menyembunyikan objek di Word** untuk pengguna atau kondisi tertentu, Anda dapat mengubah properti ini pada runtime berdasarkan logika bisnis Anda.

> **Catatan:** Bentuk tersembunyi tetap menjadi bagian dari struktur XML dokumen. Mereka dapat ditampilkan kembali nanti dengan mengatur `setHidden(false)`.

## Langkah 4: Simpan dokumen

Setelah menambahkan dan menyembunyikan bentuk, tulis dokumen ke disk.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Saat Anda membuka `HiddenShapeDemo.docx` di Microsoft Word, Anda akan melihat halaman kosong karena elips disembunyikan. Dokumen tetap berperilaku seperti file Word normal lainnya.

## Contoh kerja lengkap

Menggabungkan semua bagian, berikut program lengkap yang dapat dijalankan:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Output yang diharapkan**

```
Document created successfully.
```

Membuka `HiddenShapeDemo.docx` menampilkan halaman kosong; elips yang disembunyikan tidak dirender, mengonfirmasi bahwa operasi **hide object in Word** berhasil.

## Kasus tepi dan variasi

| Situasi | Apa yang diubah | Mengapa |
|-----------|----------------|-----|
| Sembunyikan persegi panjang alih-alih elips | Gunakan `ShapeType.RECTANGLE` dalam `insertShape` | Placeholder visual yang berbeda |
| Sembunyikan beberapa bentuk sekaligus | Loop melalui `doc.getChildNodes(NodeType.SHAPE, true)` dan set `setHidden(true)` | Berguna untuk pemrosesan massal |
| Tampilkan bentuk hanya dalam tampilan cetak | Set `shape.setVisible(false)` dan `shape.setPrint(true)` | Word membedakan antara visibilitas layar dan cetak |
| Gunakan satuan pengukuran yang berbeda | Panggil `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Sesuaikan dengan kebutuhan tata letak Anda |

## Kesalahan umum

* **Lupa memanggil `setHidden(true)`** – bentuk akan muncul seperti biasa.  
* **Menyimpan dokumen sebelum menyembunyikan bentuk** – urutan penting; sembunyikan dulu, lalu simpan.  
* **Menggunakan versi Aspose.Words yang usang** – rilis lama mungkin tidak memiliki API `setHidden`.  

Selalu uji file yang dihasilkan pada versi Microsoft Word target untuk memastikan status tersembunyi berperilaku seperti yang diharapkan.

## Kesimpulan

Dalam panduan ini Anda belajar cara **membuat dokumen Word secara programatis**, **menambahkan bentuk**, dan **menyembunyikan objek di Word** menggunakan Aspose.Words for Java. Contoh lengkap menunjukkan langkah‑langkah tepat, mulai dari menginisialisasi dokumen hingga menyimpan file di mana bentuk tidak pernah muncul.  

Dari sini Anda dapat:

* Bereksperimen dengan tipe bentuk lain (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Menggabungkan bentuk tersembunyi dengan bookmark untuk membuat templat dinamis.  
* Menjelajahi properti `setVisible` dan `setPrint` untuk kontrol visibilitas objek yang lebih detail.

Selamat coding, dan nikmati otomatisasi dokumen Word Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat dokumen word kosong dengan Aspose.Words untuk Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Cara menyembunyikan bentuk dalam dokumen Word menggunakan Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}