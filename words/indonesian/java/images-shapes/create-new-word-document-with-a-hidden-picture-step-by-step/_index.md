---
category: general
date: 2026-09-27
description: Buat dokumen Word baru dan sisipkan bentuk gambar yang tetap tersembunyi.
  Pelajari cara menyembunyikan bentuk dan menambahkan gambar tersembunyi menggunakan
  Aspose.Words untuk Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert image shape
- how to hide shape
- how to insert image
- add hidden picture
language: id
lastmod: 2026-09-27
og_description: Buat dokumen Word baru dan sisipkan bentuk gambar yang tetap tersembunyi.
  Pelajari cara menyembunyikan bentuk dan menambahkan gambar tersembunyi menggunakan
  Aspose.Words untuk Java.
og_image_alt: Screenshot showing a Word document with a hidden picture inserted using
  Java
og_title: Buat dokumen Word baru dengan gambar tersembunyi – Panduan Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create new Word document and insert an image shape that stays hidden.
    Learn how to hide shape and add hidden picture using Aspose.Words for Java.
  headline: Create new Word document with a hidden picture – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- hidden image
title: Buat dokumen Word baru dengan gambar tersembunyi – panduan langkah demi langkah
url: /id/java/images-shapes/create-new-word-document-with-a-hidden-picture-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word baru dengan gambar tersembunyi – panduan langkah demi langkah

Jika Anda perlu **create new Word document** yang berisi logo tetapi tidak ingin logo tersebut memengaruhi tata letak halaman, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan belajar cara **insert image shape**, memahami **how to hide shape**, dan akhirnya **add hidden picture** ke file tanpa dampak visual apa pun.

Tutorial ini mencakup semua hal mulai dari penyiapan proyek hingga langkah verifikasi akhir. Pada akhir tutorial, Anda akan memiliki program Java yang berfungsi penuh yang membuat file Word, menyisipkan image shape, menyembunyikannya, dan menyimpan hasilnya. Tidak ada alat tambahan yang diperlukan selain pustaka Aspose.Words for Java.

## Prasyarat

* Java 17 (atau lebih baru) terpasang.
* Proyek Maven atau Gradle di mana Anda dapat menambahkan dependensi.
* Aspose.Words for Java 23.9 (atau versi terbaru) – lihat repositori Maven resmi untuk koordinat yang tepat.
* File gambar (mis., `logo.png`) ditempatkan di folder yang dapat Anda referensikan dari kode Anda.

> **Pro tip:** Simpan gambar di direktori yang sama dengan file sumber Anda selama pengembangan; ini menyederhanakan penanganan path.

## Langkah 1: Siapkan proyek dan impor Aspose.Words

Tambahkan dependensi Aspose.Words ke `pom.xml` Anda (Maven) atau `build.gradle` (Gradle). Berikut adalah cuplikan Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Sekarang buat kelas Java bernama `HiddenPictureDemo`. Baris pertama mengimpor kelas yang diperlukan dan **create new Word document**:

```java
import com.aspose.words.*;

public class HiddenPictureDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder
        Document doc = new Document();               // creates new Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting:* `Document` mewakili seluruh file `.docx`, sementara `DocumentBuilder` menyediakan API yang fluently untuk menambahkan konten seperti paragraf, tabel, dan shape.

## Langkah 2: Sisipkan image shape ke dalam dokumen Word

Operasi berikut menunjukkan **how to insert image** sebagai shape. Menggunakan `DocumentBuilder.insertImage` mengembalikan objek `Shape` yang dapat Anda manipulasi lebih lanjut.

```java
        // Step 2: Insert an image shape (the picture will act as a shape)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");
        // Optional: set the shape size if needed
        imageShape.setWidth(100);
        imageShape.setHeight(50);
```

*Mengapa Anda menggunakan shape:* Gambar yang disisipkan sebagai shape memberi Anda akses ke properti tata letak seperti visibility, wrapping, dan positioning, yang penting untuk menyembunyikan gambar nanti.

## Langkah 3: Sembunyikan shape agar tidak muncul dalam tata letak

Sekarang kami menjawab **how to hide shape**. Menetapkan properti `Hidden` ke `true` menghapus shape dari tata letak visual sambil tetap mempertahankannya dalam struktur dokumen.

```java
        // Step 3: Hide the shape – this is the core of "add hidden picture"
        imageShape.setHidden(true);
        // You can also set the shape's wrap type to NONE to avoid affecting surrounding text
        imageShape.setWrapType(WrapType.NONE);
```

*Penjelasan:* `setHidden(true)` memberi tahu Word untuk memperlakukan shape sebagai tidak terlihat. `setWrapType(WrapType.NONE)` tambahan memastikan bahwa hidden picture tidak memesan ruang apa pun, mempertahankan alur dokumen asli.

## Langkah 4: Simpan dokumen dan verifikasi hidden picture

Akhirnya, simpan file ke disk. Hidden picture tetap menjadi bagian dari dokumen tetapi tidak ditampilkan saat file dibuka di Microsoft Word.

```java
        // Step 4: Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx");
        System.out.println("Document created successfully with a hidden picture.");
    }
}
```

Saat Anda membuka `HiddenShape.docx` di Word, Anda akan melihat halaman normal yang bersih tanpa logo yang terlihat, namun gambar disimpan di dalam file. Anda dapat memverifikasi keberadaannya dengan membuka `.docx` sebagai arsip zip dan memeriksa folder `word/media`.

### Output yang Diharapkan

Running the program prints:

```
Document created successfully with a hidden picture.
```

Membuka `HiddenShape.docx` yang dihasilkan menunjukkan halaman kosong (atau konten apa pun yang Anda tambahkan di tempat lain) dan tidak ada gambar yang terlihat. Jika Anda mengekstrak `.docx`, Anda akan menemukan `logo.png` di dalam `word/media`, mengonfirmasi bahwa gambar tersebut telah **add hidden picture** dengan benar.

## Cara menyisipkan image dalam konteks lain

Jika Anda perlu **insert image shape** ke dalam paragraf tertentu bukan pada posisi kursor saat ini, Anda dapat memindahkan builder terlebih dahulu:

```java
builder.moveToParagraph(0, 0); // moves to the first paragraph
Shape anotherShape = builder.insertImage("YOUR_DIRECTORY/banner.jpg");
anotherShape.setHidden(true);
```

Pola ini bekerja untuk header, footer, atau tabel—cukup pindahkan builder ke node target sebelum memanggil `insertImage`.

## Variasi umum dan kasus tepi

| Skenario | Apa yang harus disesuaikan |
|----------|----------------------------|
| **Multiple hidden pictures** | Ulangi langkah 2‑3 untuk setiap gambar. Setiap `Shape` dapat disembunyikan secara independen. |
| **Different image formats** | Aspose.Words mendukung PNG, JPEG, BMP, GIF, dan TIFF. Gunakan ekstensi file yang sesuai dalam path. |
| **Large documents** | Buat dokumen sekali, lalu gunakan kembali `DocumentBuilder` yang sama untuk menyisipkan hidden pictures di berbagai lokasi. |
| **Conditional visibility** | Gunakan `shape.setVisible(false)` bersama dengan `shape.setHidden(true)` jika Anda perlu mengubah visibilitas melalui makro Word nanti. |
| **Compatibility with older Word versions** | Simpan sebagai `doc.save("file.doc", SaveFormat.DOC)` jika Anda harus mendukung Word 2003‑2007. Hidden shapes berperilaku sama. |

## Tips praktis dari pengalaman

* **Path handling:** Gunakan `Paths.get("...").toAbsolutePath().toString()` untuk menghindari kejutan path relatif saat menjalankan dari IDE dibandingkan dengan JAR yang dipaketkan.
* **Performance:** Menyisipkan banyak gambar besar dapat meningkatkan penggunaan memori. Pertimbangkan untuk mengubah skala gambar (`setWidth`/`setHeight`) sebelum menyembunyikannya.
* **Testing:** Otomatiskan pemeriksaan cepat dengan memuat dokumen yang disimpan dan memanggil `doc.getChildNodes(NodeType.SHAPE, true).getCount()` untuk memastikan jumlah shape yang diharapkan ada, meskipun mereka tersembunyi.

## Kesimpulan

Anda sekarang tahu cara **create new Word document**, **insert image shape**, dan **how to hide shape** sehingga gambar tetap tidak terlihat—secara efektif **add hidden picture** ke file Word apa pun menggunakan Aspose.Words for Java. Teknik ini berguna untuk menyematkan watermark, aset merek, atau gambar metadata yang tidak boleh mengganggu tata letak dokumen.

### Langkah selanjutnya

* Jelajahi properti shape lainnya seperti rotasi, border, dan hyperlink.
* Gabungkan hidden pictures dengan properti dokumen khusus untuk menyimpan metadata tambahan.
* Pelajari **how to insert image** ke dalam header atau footer untuk branding konsisten di seluruh halaman.

Silakan bereksperimen dengan berbagai ukuran gambar, posisi, dan pengaturan visibilitas. Jika Anda mengalami masalah, dokumentasi Aspose.Words for Java menyediakan referensi API detail dan contoh proyek. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}