---
category: general
date: 2026-11-15
description: Buat bentuk persegi panjang di Word dengan Java dan pelajari cara menambahkan
  bentuk ke Word, mengatur dimensi bentuk, serta menyimpan dokumen Word secara efisien.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: id
lastmod: 2026-11-15
og_description: Buat bentuk persegi panjang dalam dokumen Word menggunakan Java. Pelajari
  cara menambahkan bentuk ke Word, mengatur dimensi bentuk, dan menyimpan dokumen
  Word dalam hitungan menit.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Buat bentuk persegi panjang di Word dengan Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Buat bentuk persegi panjang dalam dokumen Word menggunakan Java
url: /id/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang dalam dokumen Word menggunakan Java

Jika Anda perlu **membuat bentuk persegi panjang** di dalam file Word, panduan ini menunjukkan secara tepat cara melakukannya dengan Java. Anda akan melihat cara **menambahkan bentuk ke Word**, mengontrol **set shape dimensions**, dan akhirnya **menyimpan dokumen Word** tanpa meninggalkan IDE Anda.

Di bagian-bagian berikut Anda akan mendapatkan contoh lengkap yang dapat dijalankan, penjelasan setiap baris, dan tip untuk jebakan umum seperti masalah ukuran dan kompatibilitas dokumen. Tidak diperlukan referensi eksternal—hanya pustaka Aspose.Words for Java.

## Apa yang akan Anda pelajari

* Cara menginisialisasi `Document` dan `DocumentBuilder`.
* Cara menyisipkan **group shape** dan menempatkan persegi panjang di dalamnya.
* Cara **define shape size** menggunakan `setWidth` dan `setHeight`.
* Cara **save Word document** dalam format `.docx`.
* Penanganan edge‑case untuk berbagai ukuran halaman dan pengaturan DPI.

### Prasyarat

* Java 17 atau lebih baru (kode juga dapat dikompilasi dengan Java 8).
* Aspose.Words for Java 23.10 atau yang lebih baru – Anda dapat memperolehnya dari Maven Central.
* Pemahaman dasar tentang sintaks Java dan konsep berorientasi objek.

> **Pro tip:** Jika Anda berencana menambahkan lebih banyak bentuk nanti (mis., lingkaran atau kotak teks), simpan mereka di dalam `GroupShape` yang sama. Ini membuat memindahkan, memutar, atau memformat seluruh koleksi menjadi jauh lebih mudah.

## Langkah 1: Inisialisasi dokumen dan builder

Langkah pertama adalah membuat file Word kosong dan `DocumentBuilder` yang memungkinkan Anda menulis konten.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting:* `Document` mewakili seluruh file, sementara `DocumentBuilder` menyediakan metode tingkat tinggi untuk menyisipkan teks, tabel, dan **shapes**. Tanpa builder Anda harus memanipulasi node tingkat rendah secara manual.

## Langkah 2: Sisipkan group shape untuk menampung beberapa bentuk

**Group shape** berfungsi seperti kontainer; Anda dapat menambahkan beberapa bentuk dan memperlakukannya sebagai satu objek kemudian (mis., memindahkan atau memutar bersama).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Mengapa menggunakan group shape?* Jika Anda kemudian memutuskan menambahkan panah, lingkaran, atau label di sekitar persegi panjang, grup akan menjaga semuanya tetap sejajar. Ini juga menyederhanakan alur kerja **add shapes to Word** karena Anda hanya perlu satu panggilan ke `appendChild` untuk setiap bentuk baru.

## Langkah 3: Buat bentuk persegi panjang

Sekarang kita membuat persegi panjang sebenarnya yang akan berada di dalam grup. Konstruktor `Shape` membutuhkan `Document` pemilik dan tipe bentuk yang Anda inginkan.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Mengapa persegi panjang?* `ShapeType.RECTANGLE` adalah primitif paling umum untuk menyorot bagian, membuat placeholder, atau menggambar mock‑up UI sederhana langsung di dalam Word.

## Langkah 4: Tentukan ukuran persegi panjang

Menetapkan dimensi adalah saat **set shape dimensions** menjadi penting. Anda dapat menggunakan satuan ukuran apa pun yang didukung oleh Aspose.Words; defaultnya adalah poin (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Catatan:** Jika Anda lebih suka milimeter, panggil `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` dimana `1.39 in ≈ 35 mm`. Ini menunjukkan fleksibilitas **define shape size**.

## Langkah 5: Tambahkan persegi panjang ke group shape

Menambahkan persegi panjang ke grup yang sebelumnya dibuat membuatnya muncul di dokumen.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

Pada titik ini persegi panjang diposisikan di sudut kiri‑atas grup. Anda dapat memindahkannya nanti dengan `rectangle.setLeft(...)` dan `rectangle.setTop(...)` jika memerlukan penempatan yang tepat.

## Langkah 6: (Opsional) Simpan dokumen untuk melihat hasilnya

Akhirnya, tulis dokumen ke disk. Ini adalah langkah **save Word document** yang menghasilkan file `.docx` yang dapat Anda buka di Microsoft Word, LibreOffice, atau Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Menjalankan program membuat `RectangleShapeDemo.docx` yang berisi satu persegi panjang di dalam group shape. Membuka file menampilkan persegi panjang putih polos—tepat dengan ukuran yang Anda definisikan.

### Output yang Diharapkan

* File Word bernama `RectangleShapeDemo.docx`.
* Di dalam paragraf pertama, group shape yang berisi persegi panjang 100 pt × 50 pt.
* Tidak ada teks yang ditambahkan, sehingga persegi panjang muncul pada halaman kosong.

## Variasi umum dan kasus tepi

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Ukuran halaman berbeda** (mis., A4) | Panggil `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` sebelum menyisipkan bentuk. |
| **DPI lebih tinggi untuk pencetakan** | Kalikan lebar/tinggi dengan faktor DPI yang diinginkan, mis., `rectangle.setWidth(200 * 2);` untuk resolusi dua kali lipat. |
| **Menambahkan label teks di dalam persegi panjang** | Buat `Shape` tipe `TEXT_BOX`, set `setWidth`/`setHeight`-nya agar cocok dengan persegi panjang, lalu tambahkan ke `GroupShape` yang sama. |
| **Memutar persegi panjang** | Gunakan `rectangle.setRotationAngle(45);` untuk memutar 45 derajat searah jarum jam. |
| **Menyimpan sebagai PDF alih-alih DOCX** | Ganti `document.save("output.docx");` dengan `document.save("output.pdf");` – API yang sama bekerja untuk PDF, mempertahankan persegi panjang. |

## Tips profesional untuk implementasi yang kuat

1. **Gunakan kembali builder** – setelah menyisipkan group shape, Anda dapat melanjutkan menambahkan paragraf atau tabel tanpa membuat instance builder baru.
2. **Bebaskan sumber daya** – meskipun garbage collector Java menangani sebagian besar objek, memanggil secara eksplisit `document.close();` (jika menggunakan stream) mencegah kebocoran handle file.
3. **Validasi dimensi** – sebelum memanggil `setWidth`/`setHeight`, pastikan nilai positif; nilai negatif akan melempar `IllegalArgumentException`.
4. **Kompatibilitas versi** – kode ini bekerja dengan Aspose.Words 23.x dan lebih baru. Versi sebelumnya mungkin memerlukan `Shape.setSize(width, height)` alih-alih setter terpisah.

## Contoh lengkap yang dapat dijalankan

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Verifikasi hasil:** Buka `output/RectangleShapeDemo.docx` di Microsoft Word. Anda harus melihat persegi panjang dengan ukuran yang ditentukan berada di tengah bagian atas halaman pertama. Jika persegi panjang terlihat terlalu kecil, sesuaikan nilai yang diberikan ke `setWidth` dan `setHeight`.

## Kesimpulan

Anda kini tahu cara **create rectangle shape** dalam file Word menggunakan Java, cara **add shapes to Word** melalui `GroupShape`, cara **set shape dimensions** dan **define shape size**, serta akhirnya cara **save Word document** untuk distribusi lebih lanjut. Pola yang sama berlaku untuk tipe bentuk lain, memungkinkan Anda membangun diagram kompleks secara programatis.

### Apa selanjutnya?

* Jelajahi **add shapes to Word** dengan menyisipkan lingkaran, panah, atau kotak teks.
* Gabungkan beberapa bentuk menjadi satu `GroupShape` dan terapkan transformasi (memutar, membalik).
* Hasilkan laporan yang menyematkan diagram sebagai bentuk, lalu **save Word document** sebagai PDF untuk dibagikan.

Silakan bereksperimen dengan dimensi, warna, dan penempatan untuk menyesuaikan skenario spesifik Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Buat Bentuk Persegi Panjang dalam Dokumen Word Java – Panduan Langkah‑per‑Langkah Lengkap](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Buat dokumen word java – sembunyikan bentuk dan atur warna isi](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}