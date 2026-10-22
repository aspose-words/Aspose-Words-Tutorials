---
category: general
date: 2026-09-18
description: Buat dokumen kosong dan sisipkan bentuk ke Word dengan Aspose.Words –
  pelajari cara menambahkan bentuk segitiga dan lainnya.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: id
lastmod: 2026-09-18
og_description: Buat dokumen kosong di Word menggunakan Aspose.Words dan pelajari
  cara menyisipkan bentuk segitiga, mengelompokkan bentuk, serta grafik lainnya. Ikuti
  panduan lengkap ini.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Buat dokumen kosong dan tambahkan bentuk ke Word – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Cara membuat dokumen kosong dan menambahkan bentuk ke Word
url: /id/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen kosong dan menambahkan bentuk ke Word

Jika Anda perlu **create blank document** dan kemudian memperkaya dengan grafik, panduan ini menunjukkan secara tepat cara melakukannya. Kami akan memandu pembuatan file Word dari awal dan **add shapes to Word**, termasuk **how to insert triangle** shape, menggunakan Aspose.Words for Java.

Anda akan menyelesaikan tutorial dengan file *.docx* siap‑pakai yang berisi sebuah grouped shape yang memegang sebuah segitiga. Langkah‑langkah mencakup semuanya mulai dari penyiapan proyek hingga menyimpan **create word document** akhir. Tidak ada alat eksternal yang diperlukan selain Aspose.Words.

## Prasyarat

* Java 17 atau lebih baru terpasang  
* Maven atau Gradle untuk manajemen dependensi  
* Lisensi Aspose.Words for Java (evaluasi gratis dapat digunakan untuk demo ini)  

Jika Anda lebih suka sistem build lain, sesuaikan sintaks dependensi sesuai kebutuhan. Kode ini bekerja pada platform apa pun yang mendukung Java.

## Membuat dokumen kosong dengan Aspose.Words

Operasi pertama adalah **create blank document** di memori. Aspose.Words menyediakan kelas `Document` yang mewakili file Word tanpa konten apa pun.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()` constructor membangun struktur *.docx* kosong, yang kemudian dapat Anda isi dengan paragraf, tabel, atau grafik. Karena dokumen kosong, Anda memiliki kontrol penuh atas setiap elemen yang Anda tambahkan.

## Menambahkan bentuk ke Word – menyisipkan group shape

Group shape memungkinkan Anda memperlakukan beberapa grafik sebagai satu unit. Ini berguna ketika Anda ingin memindahkan atau mengubah ukuran beberapa bentuk sekaligus.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` adalah API utama untuk menambahkan konten. Pemanggilan `insertGroupShape` membuat sebuah kontainer berukuran 300 × 300 poin (sekitar 4 × 4 inci). Setelah pemanggilan ini, kursor berada *di dalam* grup, siap untuk bentuk tambahan.

### Mengapa menggunakan group shape?

Pengelompokan menjaga grafik terkait tetap sejajar dan memudahkan penerapan format seragam. Jika Anda kemudian memutuskan memindahkan segitiga, seluruh grup akan bergerak bersama, mempertahankan tata letak.

## Cara menyisipkan bentuk segitiga di dalam grup

Sekarang kita membahas **how to insert triangle** shape. Segitiga adalah salah satu nilai `ShapeType` bawaan.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

Pemanggilan `moveTo` memastikan titik sisip builder berada pada paragraf pertama grup. `insertShape` kemudian menambahkan segitiga berukuran 60 × 60 poin. Karena kursor berada di dalam grup, segitiga menjadi anak dari group shape.

**Add triangle shape** tips:
* Ukuran diukur dalam poin; 72 poin sama dengan satu inci. Sesuaikan dimensi sesuai tata letak Anda.  
* Jika Anda memerlukan orientasi berbeda, gunakan `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` untuk menyelaraskan bentuk di dalam grup.  
* Segitiga mewarisi gaya isi dan garis grup kecuali Anda menimpanya dengan `shape.getFillColor()` atau `shape.getStrokeColor()`.

## Simpan dokumen – create word document

Setelah membangun grafik, Anda menyimpan file. Langkah ini menyelesaikan operasi **create word document**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` menulis representasi dalam memori ke disk sebagai dokumen Word standar. Anda dapat membuka `ExtendedGroup.docx` di Microsoft Word, LibreOffice, atau penampil apa pun yang mendukung format OOXML. File akan menampilkan sebuah grouped shape yang berisi segitiga, persis seperti yang dibangun oleh kode.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut program lengkap yang dapat Anda salin, kompilasi, dan jalankan:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Hasil yang diharapkan

Saat Anda membuka `ExtendedGroup.docx`, Anda akan melihat satu group shape yang menempati tengah halaman. Di dalam grup tersebut, sebuah segitiga kecil muncul pada posisi default. Segitiga dapat dipilih dan dipindahkan sebagai bagian dari grup, mengonfirmasi bahwa **add shapes to word** berfungsi sebagaimana mestinya.

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| *Bisakah saya menambahkan lebih dari satu bentuk di dalam grup?* | Ya. Setelah menyisipkan segitiga, tetap biarkan kursor di dalam grup dan panggil `builder.insertShape` lagi dengan `ShapeType` yang berbeda. |
| *Bagaimana jika saya membutuhkan segitiga berwarna merah?* | Ambil `Shape` yang dikembalikan oleh `insertShape` dan panggil `shape.getFillColor().setColor(Color.RED)`. |
| *Apakah ini bekerja dengan file .doc lama?* | Aspose.Words menyimpan dalam format yang Anda tentukan. Gunakan `doc.save("file.doc", SaveFormat.DOC)` untuk membuat dokumen Word lama. |
| *Bagaimana cara mengubah border grup?* | Gunakan `group.getStrokeColor().setColor(Color.BLUE)` dan `group.setLineWeight(2.0)` untuk menyesuaikan outline. |
| *Apakah ada cara untuk memutar segitiga?* | Panggil `shape.getRotation()` untuk mengatur sudut dalam derajat. |

## Tips profesional

* **Reuse the builder** – membuat `DocumentBuilder` baru untuk setiap bentuk menambah beban. Pertahankan satu builder per dokumen.  
* **Unit conversion** – jika Anda bekerja dengan milimeter, konversikan ke poin (`points = mm * 2.83465`).  
* **Performance** – untuk dokumen besar, panggil `doc.updatePageLayout()` hanya sekali setelah semua bentuk ditambahkan.

## Kesimpulan

Anda sekarang tahu cara **create blank document**, **add shapes to Word**, dan khususnya **how to insert triangle** shape menggunakan Aspose.Words for Java. Contoh lengkap menunjukkan alur kerja penuh dari file kosong hingga **create word document** yang disimpan yang berisi sebuah grouped triangle.

Dari sini Anda dapat menjelajahi nilai `ShapeType` tambahan, menerapkan gaya khusus, atau menggabungkan beberapa grup untuk membuat diagram kompleks. Bereksperimen dengan ukuran, warna, dan posisi yang berbeda untuk menguasai otomatisasi Word dalam Java.

--- 

*Siap mengotomatisasi laporan berikutnya? Kloning contoh, sesuaikan dimensi, dan integrasikan kode ke dalam aplikasi Anda sendiri hari ini.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayang – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Buat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}