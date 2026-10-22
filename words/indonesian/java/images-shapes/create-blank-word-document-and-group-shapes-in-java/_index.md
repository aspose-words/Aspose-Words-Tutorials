---
category: general
date: 2026-08-23
description: Buat dokumen Word kosong dengan Aspose.Words untuk Java, pelajari cara
  mengelompokkan bentuk, memberi warna pada bentuk persegi panjang, dan menyimpan
  dokumen sebagai docx dalam hitungan menit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: id
lastmod: 2026-08-23
og_description: Buat dokumen Word kosong dengan Aspose.Words untuk Java, kemudian
  lihat cara mengelompokkan bentuk, memberi warna pada bentuk persegi panjang, dan
  menyimpan dokumen sebagai docx secara efisien.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Buat dokumen Word kosong dan grupkan bentuk di Java – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Buat dokumen Word kosong dan grupkan bentuk di Java
url: /id/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan grup bentuk di Java

Jika Anda perlu **create blank Word document** secara programatis, Aspose.Words for Java mempermudahnya. Tutorial ini menunjukkan secara tepat cara **create blank Word document**, menyisipkan **group shapes in Word**, menerapkan **color rectangle shape**, dan akhirnya **save document as docx**. Pada akhir Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat dimasukkan ke proyek Java mana pun.

Anda akan belajar:

* Dependensi Maven/Gradle yang diperlukan untuk Aspose.Words.
* Cara menginstansiasi dokumen kosong dan `DocumentBuilder`.
* Langkah-langkah tepat untuk **how to group shapes** di dalam `GroupShape`.
* Cara mengatur warna isi pada bentuk persegi panjang.
* Praktik terbaik untuk **save document as docx** dan di mana menemukan file output.

Tidak ada asumsi pengalaman sebelumnya dengan Aspose.Words, tetapi Anda sebaiknya nyaman dengan pengembangan Java dasar dan telah menginstal JDK 8 atau yang lebih baru.

---

## Prasyarat

| Persyaratan | Versi / Detail |
|-------------|-------------------|
| Java Development Kit | 8 atau lebih tinggi |
| Build tool | Maven 3+ atau Gradle 6+ |
| Aspose.Words for Java | 23.12 atau lebih baru (versi terbaru pada saat penulisan) |
| IDE (opsional) | IntelliJ IDEA, Eclipse, VS Code, atau editor Java‑compatible lainnya |

---

## Langkah 1: Tambahkan Aspose.Words ke proyek Anda

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Jika Anda menggunakan proxy perusahaan, konfigurasikan Maven/Gradle untuk mengambil paket dari repositori Aspose seperti yang dijelaskan dalam dokumentasi resmi.

---

## Langkah 2: **Create blank Word document** dengan builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` constructor membuat kontainer `.docx` kosong di memori. `DocumentBuilder` memberikan API yang fluently untuk menambahkan konten, termasuk bentuk.

---

## Langkah 3: Sisipkan kontainer **group shapes in Word**

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape` berfungsi seperti mini‑canvas. Semua bentuk yang ditambahkan ke dalamnya bergerak bersama, yang tepat merupakan **how to group shapes** untuk konsistensi tata letak.

---

## Langkah 4: Tambahkan **color rectangle shape** pertama (merah)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

Konstanta `ShapeType.RECTANGLE` membuat persegi panjang sederhana. Dengan memanggil `getFill().setForeColor(...)` Anda mengontrol **color rectangle shape**. Anda dapat mengganti `java.awt.Color.RED` dengan konstanta `java.awt.Color` apa pun atau nilai RGB khusus.

---

## Langkah 5: Tambahkan **color rectangle shape** kedua (hijau) dan posisikan

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Mengatur `setLeft` (atau `setTop`) memindahkan bentuk relatif terhadap sudut kiri‑atas dari kontainer **group shapes in Word**. Ini menunjukkan **how to group shapes** dengan penempatan yang tepat.

---

## Langkah 6: **Save document as docx** dan verifikasi hasilnya

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Metode `save` secara otomatis menulis file `.docx` karena ekstensi file adalah `.docx`. Jika Anda memerlukan format lain (mis., PDF), berikan enum `SaveFormat` yang sesuai.

> **Tip:** Pastikan direktori target (`output/` dalam contoh ini) ada atau buat secara programatis dengan `new File("output").mkdirs();`.

---

## Kode sumber lengkap untuk salin‑tempel cepat

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Output yang diharapkan:** Membuka `GroupShapeDemo.docx` di Microsoft Word menampilkan satu halaman yang berisi dua persegi panjang berwarna (merah di kiri, hijau di kanan) yang bergerak bersama ketika Anda memilih grup.

---

## Pertanyaan umum dan penanganan kasus‑tepi

| Pertanyaan | Jawaban |
|----------|--------|
| *Bisakah saya menambahkan lebih dari dua bentuk ke grup yang sama?* | Ya. Panggil `groupShape.appendChild(yourShape)` untuk setiap bentuk tambahan. Grup akan secara otomatis mengubah ukuran untuk menyesuaikan dengan ekstensi terjauh, atau Anda dapat menyesuaikan lebar/tinggi secara manual. |
| *Bagaimana jika saya membutuhkan tipe bentuk lain (mis., elips)?* | Ganti `ShapeType.RECTANGLE` dengan `ShapeType.ELLIPSE`. Logika warna isi yang sama tetap berlaku. |
| *Apakah saya perlu membuang (dispose) objek `Document`?* | Aspose.Words mengelola sumber daya native secara internal. Saat JVM keluar, sumber daya dilepaskan. Untuk aplikasi yang berjalan lama, panggil `doc.dispose();` jika Anda menggunakan versi **Aspose.Words for Java (Native)**. |
| *Bagaimana cara mengubah urutan Z sehingga satu persegi panjang muncul di atas?* | Gunakan `groupShape.insertAfter(shape, referenceShape);` atau `groupShape.insertBefore(shape, referenceShape);` untuk mengubah urutan anak dalam grup. |
| *Bisakah saya mengelompokkan bentuk di beberapa seksi berbeda?* | Tidak. `GroupShape` harus berada dalam satu paragraf atau kontainer bentuk. Untuk mengelompokkan lintas seksi, buat grup terpisah di setiap seksi. |

---

## Kesimpulan

Anda sekarang tahu cara **create blank Word document** dengan Aspose.Words for Java, **group shapes in Word**, menerapkan gaya **color rectangle shape**, dan **save document as docx**. Pola ini dapat diperluas ke tata letak yang lebih kompleks—cukup tambahkan bentuk tambahan, sesuaikan offset, dan secara opsional atur teks, gambar, atau hyperlink di dalam grup.

**Langkah selanjutnya** yang dapat Anda jelajahi:

* Gunakan **group shapes in Word** untuk membuat diagram alur atau mock‑up UI.
* Bereksperimen dengan **save document as docx** yang digabungkan dengan konversi PDF (`doc.save("out.pdf")`).
* Terapkan gradien atau pola pada **color rectangle shape** untuk desain visual yang lebih kaya.
* Gabungkan bentuk yang dikelompokkan dengan tabel atau grafik untuk dokumen pelaporan tingkat lanjut.

Silakan ubah dimensi, warna, atau tipe bentuk untuk menyesuaikan merek proyek Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara menyimpan dokumen sebagai pdf dengan Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Menggunakan Bentuk Dokumen di Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}