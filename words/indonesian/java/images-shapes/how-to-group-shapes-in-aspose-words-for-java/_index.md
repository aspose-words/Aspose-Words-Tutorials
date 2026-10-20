---
category: general
date: 2026-10-20
description: Cara mengelompokkan bentuk di Aspose.Words untuk Java – pelajari cara
  menyisipkan bentuk persegi panjang, mengelompokkannya, dan menyimpan dokumen dalam
  satu panduan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: id
lastmod: 2026-10-20
og_description: Cara mengelompokkan bentuk di Aspose.Words untuk Java. Tutorial ini
  menunjukkan cara menyisipkan bentuk persegi panjang, mengelompokkannya, dan mengekspor
  hasilnya.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Cara mengelompokkan bentuk di Aspose.Words untuk Java – panduan langkah
  demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Cara mengelompokkan bentuk di Aspose.Words untuk Java
url: /id/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di Aspose.Words for Java

Jika Anda perlu **cara mengelompokkan bentuk** dalam dokumen Word menggunakan Aspose.Words for Java, panduan ini menunjukkan alur kerja lengkap. Anda akan belajar cara **menyisipkan bentuk persegi panjang**, menambahkan persegi panjang kedua, mengelompokkan kedua bentuk, dan akhirnya menyimpan file—semua dengan kode yang jelas dan dapat dijalankan.

Mengelompokkan bentuk berguna ketika Anda ingin memindahkan, memutar, atau memberi gaya pada beberapa gambar sebagai satu unit. Baik Anda membuat templat laporan, diagram, atau selebaran khusus, menguasai pengelompokan bentuk menghemat waktu dan menjaga tata letak tetap konsisten.

Dalam tutorial ini Anda akan:

* Membuat `Document` baru dan `DocumentBuilder`.
* **Cara menyisipkan persegi panjang** dengan dimensi yang tepat.
* Mengelompokkan persegi panjang ke dalam `GroupShape`.
* Menyimpan dokumen dan memverifikasi hasilnya.

> **Prasyarat** – Anda harus memiliki Aspose.Words for Java (v23.12 atau lebih baru) yang ditambahkan ke proyek Anda. Pengguna Maven dapat menyertakan dependensi yang ditunjukkan di bawah ini.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Apa yang Anda perlukan

| Item | Alasan |
|------|--------|
| Java 17+ | Fitur bahasa modern dan kinerja yang lebih baik |
| Aspose.Words for Java | Menyediakan API `DocumentBuilder`, `Shape`, dan `GroupShape` |
| Sebuah IDE (IntelliJ IDEA, Eclipse, VS Code, dll.) | Untuk mengompilasi dan menjalankan contoh |
| Izin menulis ke sebuah folder | Dokumen akan disimpan ke disk |

---

## Cara menyisipkan bentuk persegi panjang

Langkah pertama adalah membuat `Document` dan `DocumentBuilder`. Builder memberi Anda metode seperti `insertShape` untuk menempatkan objek gambar.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Mengapa ini penting** – Menggunakan `insertShape` adalah cara standar **cara menyisipkan persegi panjang** dalam Aspose.Words. Metode ini secara otomatis menambahkan bentuk ke paragraf saat ini dalam dokumen, sehingga Anda tidak perlu mengelola OpenXML tingkat rendah.

---

## Menyesuaikan posisi persegi panjang (opsional)

Jika persegi panjang kedua memerlukan lokasi khusus relatif terhadap yang pertama, Anda dapat mengubah properti `left` dan `top`‑nya. Langkah ini opsional tetapi sering diperlukan untuk tata letak diagram yang presisi.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Tip pro:** Semua ukuran dalam poin (1 pt ≈ 1/72 in). Gunakan `convertPointsToPixels` bila Anda memerlukan nilai piksel untuk perhitungan berbasis UI.

---

## Cara mengelompokkan bentuk

Sekarang persegi panjang sudah ada, Anda dapat menempatkannya di dalam `GroupShape`. Pengelompokan membuat dua persegi panjang berperilaku seperti satu objek—memindahkan, memutar, atau memformat grup akan memengaruhi kedua bentuk.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Mengapa pengelompokan berhasil** – `GroupShape` mewarisi dari `Shape`, sehingga Anda dapat memperlakukan grup persis seperti objek gambar lainnya. Saat Anda memanggil `appendChild`, bentuk‑bentuk tersebut dihapus dari lokasi asalnya dan menjadi anak dari grup.

---

## Menyimpan dokumen yang berisi bentuk yang dikelompokkan

Akhirnya, tulis dokumen ke disk. File akan berisi satu `GroupShape` dengan dua persegi panjang di dalamnya.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Hasil yang diharapkan

Buka `GroupShape.docx` di Microsoft Word:

* Anda akan melihat dua persegi panjang (biru dan hijau) yang ditempatkan berdampingan.
* Memilih salah satu persegi panjang akan memilih seluruh grup—menyeret akan memindahkan keduanya bersama.
* Grup memiliki batas merah tipis, mengonfirmasi bahwa properti `GroupShape` telah diterapkan.

Jika Anda mengklik kanan grup dan memilih **Group → Ungroup**, persegi panjang akan kembali menjadi bentuk independen, menunjukkan bahwa operasi pengelompokan dapat dibalik.

---

## Variasi umum dan kasus tepi

| Situasi | Cara menanganinya |
|-----------|------------------|
| **Lebih dari dua bentuk** | Sisipkan setiap bentuk, lalu tambahkan semuanya ke `GroupShape` yang sama. |
| **Jenis bentuk berbeda** (mis., elips, gambar) | Gunakan `builder.insertShape(ShapeType.ELLIPSE, …)` atau `builder.insertImage(...)` sebelum menambahkan. |
| **Menskalakan grup** | Panggil `group.setWidth(newWidth)` atau `group.setHeight(newHeight)`; anak‑anak akan berskala secara proporsional. |
| **Memutar grup** | `group.setRotationAngle(45);` memutar seluruh koleksi di sekitar pusatnya. |
| **Mempertahankan posisi asli** | Simpan `left`/`top` masing‑masing bentuk sebelum pengelompokan dan pulihkan setelah pembongkaran bila diperlukan. |

---

## Contoh lengkap yang dapat dijalankan

Berikut adalah kelas Java lengkap yang dapat Anda salin‑tempel ke IDE Anda. Kelas ini mencakup semua impor, penanganan error, dan komentar untuk kejelasan.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Jalankan program, buka `GroupShape.docx` yang dihasilkan, dan Anda akan melihat persegi panjang yang dikelompokkan persis seperti yang dijelaskan.

---

## Kesimpulan

Anda kini tahu **cara mengelompokkan bentuk** di Aspose.Words for Java, mulai dari membuat dokumen, menyisipkan bentuk persegi panjang, menyesuaikan posisinya, hingga akhirnya mengelompokkannya dengan `GroupShape`. Teknik ini memungkinkan Anda memperlakukan beberapa gambar sebagai satu entitas, menyederhanakan penyesuaian tata letak dan konsistensi visual.

**Langkah selanjutnya**

* Jelajahi **cara menyisipkan persegi panjang** dengan pola isi atau batas yang berbeda.
* Gabungkan **menyisipkan bentuk persegi panjang** dengan kotak teks untuk membuat diagram berlabel.
* Bereksperimen dengan memutar atau menskalakan grup untuk menghasilkan grafik yang lebih kompleks.

Silakan sesuaikan kode untuk jenis bentuk lain, grup yang lebih besar, atau skenario pembuatan dokumen dinamis. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [how to insert group shape in Java – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [How to Set Shadow on a Shape in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}