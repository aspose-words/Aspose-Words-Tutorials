---
category: general
date: 2026-09-11
description: Kelompokkan bentuk di Word dan tambahkan bentuk persegi panjang menggunakan
  Aspose.Words untuk Java. Pelajari cara mengatur ukuran bentuk, mengelompokkan objek,
  dan menyimpan dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: id
lastmod: 2026-09-11
og_description: Kelompokkan bentuk di Word dan tambahkan bentuk persegi panjang menggunakan
  Aspose.Words untuk Java. Tutorial ini menunjukkan cara mengatur ukuran bentuk, mengelompokkan
  bentuk, dan mengekspor dokumen.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Kelompokkan bentuk di Word – tambahkan persegi panjang dengan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Kelompokkan bentuk di Word dan tambahkan persegi panjang dengan Aspose.Words
url: /id/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengelompokkan bentuk di Word dan menambahkan persegi panjang dengan Aspose.Words

Jika Anda perlu **mengelompokkan bentuk di Word** sambil menambahkan persegi panjang secara programatik, panduan ini memberikan solusi lengkap yang siap dijalankan. Anda akan melihat secara tepat cara menyisipkan grup bentuk, menambahkan bentuk persegi panjang, mengatur ukuran bentuk, dan akhirnya menyimpan dokumen sehingga Anda dapat melihat hasilnya secara langsung.

Bekerja dengan dokumen Word sering berarti menyusun beberapa objek—gambar, diagram, atau bentuk geometris sederhana—ke dalam satu unit logis. Mengelompokkan objek‑objek tersebut memudahkan untuk memindahkan, memutar, atau memberi gaya secara bersamaan. Dalam tutorial ini kami juga akan membahas **cara menambahkan persegi panjang** dan **mengatur ukuran bentuk** untuk kontrol tata letak yang sempurna.

## Apa yang akan Anda pelajari

* Cara membuat dokumen Word baru dengan Aspose.Words for Java.  
* **Cara mengelompokkan bentuk** sehingga berperilaku sebagai satu objek.  
* **Menambahkan bentuk persegi panjang** ke dalam grup dan menyisipkan gambar ke grup yang sama.  
* **Mengatur ukuran bentuk** untuk baik persegi panjang maupun gambar.  
* Menyimpan dokumen dan membukanya di Microsoft Word untuk memverifikasi hasilnya.

### Prasyarat

* Java 17 atau yang lebih baru terpasang.  
* Maven atau Gradle untuk mengelola dependensi.  
* Lisensi Aspose.Words for Java yang valid (atau kunci evaluasi gratis).  
* File gambar (`sample.png`) ditempatkan di direktori yang diketahui (ganti `YOUR_DIRECTORY` dengan jalur aktual Anda).

---

## Cara mengelompokkan bentuk di Word menggunakan Aspose.Words

Langkah pertama adalah membuat `Document` dan `DocumentBuilder`. Builder memberikan API yang nyaman untuk menyisipkan bentuk, teks, dan elemen lainnya.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Mengapa ini penting:** `DocumentBuilder` bekerja langsung dengan objek `Document` di bawahnya, memungkinkan Anda menyisipkan bentuk tanpa harus menangani koleksi node tingkat rendah secara manual.

### Menambahkan grup bentuk

Grup bentuk adalah wadah yang dapat menampung bentuk‑bentuk lain. Anggap saja sebagai folder untuk objek gambar.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Metode `insertGroupShape()` membuat node `GroupShape` dan mengembalikannya sehingga Anda dapat menambahkan bentuk anak nanti.  

---

## Menambahkan bentuk persegi panjang ke grup

Sekarang kami akan **menambahkan bentuk persegi panjang** ke grup yang telah dibuat sebelumnya. Persegi panjang akan berfungsi sebagai latar belakang atau bingkai untuk gambar.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Tip:** Menetapkan `FillColor` dan `StrokeColor` membuat persegi panjang terlihat di dokumen akhir. Jika Anda mengabaikan properti ini, bentuk mungkin muncul transparan.

### Cara menambahkan persegi panjang

Kode di atas memperlihatkan **cara menambahkan persegi panjang** dengan membuat instance `Shape` menggunakan `ShapeType.RECTANGLE` dan kemudian menambahkannya ke `GroupShape`. Pola ini berlaku untuk jenis bentuk lain (misalnya `ELLIPSE`, `POLYLINE`).

---

## Mengatur ukuran bentuk untuk persegi panjang dan gambar

Pengaturan ukuran yang tepat memastikan bahwa persegi panjang dan gambar selaras dengan benar. Di sini kami juga **mengatur ukuran bentuk** untuk gambar yang akan disisipkan selanjutnya.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Baik persegi panjang maupun gambar kini memiliki dimensi yang sama (100 × 50 point). Karena keduanya berada dalam grup yang sama, memindahkan atau memutar grup akan memengaruhi kedua bentuk secara bersamaan.

> **Mengapa mencocokkan ukuran?** Menyamakan dimensi menjamin gambar berada rapi di dalam persegi panjang, menciptakan efek “gambar berbingkai” yang bersih.

---

## Menyimpan dokumen dan melihat hasilnya

Akhirnya, kami menulis dokumen ke disk. Membuka file tersebut di Microsoft Word menampilkan bentuk‑bentuk yang dikelompokkan sebagai satu objek yang dapat dipilih.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Saat Anda membuka `output.docx`, Anda akan melihat sebuah persegi panjang dengan gambar di dalamnya. Mengklik bentuk tersebut akan memilih baik persegi panjang maupun gambar karena mereka **dikelompokkan**.

![contoh mengelompokkan bentuk di word](https://example.com/images/group-shapes-word.png "contoh mengelompokkan bentuk di word")

*Teks alt gambar:* *contoh mengelompokkan bentuk di word* – sebuah dokumen Word yang menampilkan persegi panjang dan gambar yang dikelompokkan.

---

## Pertanyaan umum dan penanganan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika saya memerlukan ukuran berbeda untuk gambar?** | Sesuaikan `picture.setWidth()` dan `picture.setHeight()` setelah penyisipan. Persegi panjang dapat mempertahankan ukuran aslinya, atau Anda juga dapat mengubah ukurannya agar cocok. |
| **Apakah saya dapat menambahkan lebih banyak bentuk ke grup yang sama?** | Ya. Panggil `group.appendChild(newShape)` untuk setiap objek `Shape` tambahan. |
| **Bagaimana cara memutar seluruh grup?** | Gunakan `group.setRotationAngle(double angleInRadians)`. Rotasi akan diterapkan pada setiap bentuk anak. |
| **Bagaimana jika file gambar tidak ditemukan?** | `insertImage` akan melempar `FileNotFoundException`. Bungkus pemanggilan dalam blok try‑catch dan sediakan bentuk placeholder sebagai cadangan. |
| **Apakah memungkinkan untuk mengeluarkan grup nanti?** | Panggil `group.removeAllChildren()` untuk memisahkan anak‑anaknya, lalu sisipkan kembali ke dokumen satu per satu. |

---

## Kesimpulan

Anda kini memiliki contoh lengkap yang dapat dijalankan yang menunjukkan **cara mengelompokkan bentuk di Word**, **menambahkan bentuk persegi panjang**, **mengatur ukuran bentuk**, dan **menyimpan** dokumen menggunakan Aspose.Words for Java. Dengan mengelompokkan persegi panjang dan gambar, Anda dapat memindahkan, mengubah ukuran, atau memutar keduanya sebagai satu unit—tepat apa yang dibutuhkan banyak skenario otomatisasi dokumen.

Dari sini Anda dapat menjelajahi:

* Menambahkan kotak teks ke grup yang sama (`cara menambahkan persegi panjang`‑style teks).  
* Menerapkan pola isi atau gradien berbeda (`mengatur ukuran bentuk` dikombinasikan dengan styling).  
* Menggunakan teknik yang sama untuk mengelompokkan diagram, tabel, atau SmartArt (`cara mengelompokkan bentuk` pada tipe objek lain).  

Silakan bereksperimen dengan jenis bentuk, warna, dan opsi tata letak lainnya. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut membahas topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}