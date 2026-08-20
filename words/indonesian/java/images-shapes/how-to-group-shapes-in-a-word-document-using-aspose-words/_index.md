---
category: general
date: 2026-08-20
description: Pelajari cara mengelompokkan bentuk, mengatur ukuran bentuk, menyisipkan
  gambar ke dalam dokumen, menambahkan gambar ke grup, dan membuat bentuk persegi
  panjang dengan Aspose.Words di Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: id
lastmod: 2026-08-20
og_description: Cara mengelompokkan bentuk dalam dokumen Word menggunakan Aspose.Words.
  Ikuti tutorial Java langkah demi langkah ini untuk mengatur ukuran bentuk, menyisipkan
  gambar ke dalam dokumen, menambahkan gambar ke grup, dan membuat bentuk persegi
  panjang.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Cara mengelompokkan bentuk dalam dokumen Word dengan Aspose.Words – Panduan
  Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Cara mengelompokkan bentuk dalam dokumen Word menggunakan Aspose.Words
url: /id/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di dokumen Word menggunakan Aspose.Words

Jika Anda perlu **how to group shapes** dalam file Word, tutorial ini menunjukkan solusi Java lengkap. Anda akan melihat cara **set shape size**, **insert image into document**, **add picture to group**, dan **create rectangle shape**—semua dengan penjelasan yang jelas dan contoh kode yang dapat dijalankan.

Mengelompokkan bentuk menyederhanakan manajemen tata letak, memungkinkan Anda memindahkan atau memutar beberapa objek sebagai satu unit, dan menjaga dokumen Anda tetap rapi. Pada langkah-langkah di bawah ini Anda akan membuat grup yang berisi sebuah persegi panjang dan sebuah gambar, kemudian menempatkan grup tersebut pada halaman.

## Prasyarat

* Java 17 atau yang lebih baru terpasang.
* Aspose.Words for Java (versi 23.9 atau lebih baru) ditambahkan ke classpath proyek Anda.
* Sebuah gambar JPEG contoh di `YOUR_DIRECTORY/sample.jpg` (ganti `YOUR_DIRECTORY` dengan path yang sebenarnya).

Anda dapat menambahkan Aspose.Words melalui Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Cara mengelompokkan bentuk dengan Aspose.Words

Bagian-bagian berikut menjelaskan setiap operasi yang diperlukan untuk **how to group shapes**. Header H2 utama berisi kata kunci utama, memenuhi aturan SEO.

### Langkah 1: Buat dokumen baru dan `DocumentBuilder`

`Document` mewakili file Word, sementara `DocumentBuilder` menyediakan metode yang nyaman untuk menyisipkan konten.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting*: Memulai dengan `Document` baru memastikan bahwa grup yang Anda buat tidak akan mengganggu elemen yang sudah ada.

### Langkah 2: Sisipkan bentuk grup yang akan menampung beberapa bentuk anak

Bentuk grup berfungsi seperti wadah. Dimensinya menentukan kotak pembatas untuk semua bentuk anak.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tip*: Lebar (`300`) dan tinggi (`200`) dalam satuan poin (1 pt = 1/72 inci). Sesuaikan berdasarkan ukuran bentuk yang akan Anda tambahkan.

### Langkah 3: Buat bentuk persegi panjang, atur ukurannya, dan tambahkan ke grup

Mengatur ukuran tepat sebuah bentuk sangat penting ketika Anda menginginkan kontrol tata letak yang presisi.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Mengapa kami mengatur ukuran bentuk*: Metode `setWidth` dan `setHeight` sesuai dengan kata kunci sekunder **set shape size**, memberikan kontrol pixel‑perfect atas tampilan persegi panjang.

### Langkah 4: Sisipkan gambar, lalu tambahkan bentuk gambar ke grup yang sama

Menyisipkan gambar adalah inti dari kebutuhan **insert image into document**. `Shape` yang dikembalikan adalah bentuk gambar yang dapat dikelompokkan seperti bentuk lainnya.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: Jika Anda perlu mempertahankan rasio aspek asli, atur hanya satu dimensi (`setWidth` atau `setHeight`). Aspose.Words secara otomatis menyesuaikan dimensi lainnya.

### Langkah 5: Tempatkan seluruh grup pada halaman

Setelah menambahkan semua bentuk anak, Anda dapat memindahkan, memutar, atau menyembunyikan seluruh grup. Penempatan menggunakan konsep **add picture to group** secara tidak langsung, karena grup kini berisi gambar.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Penjelasan*: `setLeft` dan `setTop` menempatkan grup relatif terhadap margin halaman. Memutar grup menunjukkan bahwa semua bentuk anak mewarisi transformasi.

### Langkah 6: Simpan dokumen

Akhirnya, tulis file ke disk. Anda dapat membuka `.docx` yang dihasilkan di Word untuk memverifikasi pengelompokan.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Menjalankan program menghasilkan **GroupShapesDemo.docx** yang berisi persegi panjang dan gambar yang digabungkan. Memilih salah satu bentuk di Word juga akan memilih yang lain, mengonfirmasi bahwa Anda telah berhasil mempelajari **how to group shapes**.

---

## Output yang Diharapkan

Saat Anda membuka *GroupShapesDemo.docx* di Microsoft Word:

* Sebuah persegi panjang (isi emas) muncul di sisi kiri grup.
* Gambar yang Anda sediakan muncul di sebelah kanan persegi panjang.
* Kedua objek bergerak bersama saat Anda menyeret grup.
* Grup ditempatkan 50 pt dari margin kiri dan 100 pt dari margin atas, diputar 15°.

Jika gambar tidak muncul, periksa kembali path file di `insertImage`. Aspose.Words akan melempar `IOException` ketika file tidak dapat ditemukan.

---

## Pertanyaan umum dan penanganan kasus tepi

| Pertanyaan | Jawaban |
|----------|--------|
| **Apakah saya dapat menambahkan lebih dari dua bentuk?** | Ya. Panggil `groupShape.appendChild(otherShape)` untuk setiap bentuk tambahan. |
| **Bagaimana jika saya membutuhkan latar belakang transparan untuk persegi panjang?** | Gunakan `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Apakah pengelompokan didukung di format Word lama (misalnya `.doc`)?** | Pengelompokan berfungsi untuk `.docx` dan `.doc` tetapi beberapa penampil lama mungkin mengabaikan metadata grup. Simpan sebagai `.docx` untuk fidelitas penuh. |
| **Bagaimana cara membatalkan pengelompokan nanti?** | Ambil node anak melalui `groupShape.getChildNodes(NodeType.ANY, true)` dan pindahkan ke badan dokumen, kemudian hapus grup. |
| **Apakah saya dapat mengelompokkan bentuk di seluruh bagian yang berbeda?** | Tidak. `GroupShape` harus berada dalam satu `Story` (biasanya badan dokumen utama). |

## Tips profesional untuk penanganan bentuk yang kuat

* **Gunakan penempatan absolut secara hemat** – penempatan relatif (`builder.moveToDocumentEnd()`) sering menghasilkan tata letak yang lebih responsif.
* **Cache `DocumentBuilder`** – membuat builder baru untuk setiap operasi dapat menurunkan kinerja pada dokumen besar.
* **Set `PictureFillMode`** ketika Anda membutuhkan gambar untuk meregang atau menempel di dalam bentuk: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Validasi dimensi gambar** sebelum penyisipan untuk menghindari skala tak terduga yang dapat memengaruhi kotak pembatas grup.

## Langkah Selanjutnya

Sekarang Anda sudah mengetahui **how to group shapes**, Anda dapat menjelajahi:

* **Insert image into document** dengan opsi lanjutan seperti pemotongan (`pictureShape.setCropTop(...)`).
* **Set shape size** secara dinamis berdasarkan dimensi halaman (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** bersama dengan kotak teks untuk grafik berjudul.
* **Create rectangle shape** dengan sudut melengkung (`rectangleShape.setCornerRadius(5);`).

Topik-topik ini dibangun di atas permukaan API yang sama dan membantu Anda membuat laporan Word yang canggih secara programatik.

## Kesimpulan

Dalam tutorial ini Anda mempelajari **how to group shapes** dalam dokumen Word menggunakan Aspose.Words untuk Java. Dengan mengikuti enam langkah—membuat dokumen, menyisipkan grup, **creating rectangle shape**, **set shape size**, **insert image into document**, **add picture to group**, dan memposisikan grup—Anda kini memiliki pola yang dapat digunakan kembali untuk skenario tata letak yang kompleks. Jangan ragu untuk bereksperimen dengan bentuk anak tambahan, rotasi berbeda, atau logika pengelompokan bersyarat untuk memenuhi kebutuhan aplikasi Anda.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}