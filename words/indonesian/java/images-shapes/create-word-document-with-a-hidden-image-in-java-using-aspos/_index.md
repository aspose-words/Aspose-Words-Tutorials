---
category: general
date: 2026-09-24
description: Buat dokumen Word di Java dan pelajari cara menyembunyikan gambar, menambahkan
  gambar ke Word, serta menyisipkan gambar tersembunyi dengan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to hide image
- add image word
- how to hide shape
- insert hidden picture
language: id
lastmod: 2026-09-24
og_description: Buat dokumen Word dalam Java dan temukan cara menyembunyikan gambar,
  menambahkan gambar ke Word, serta menyisipkan gambar tersembunyi menggunakan Aspose.Words.
og_image_alt: Screenshot of a create word document example with a hidden image
og_title: Buat dokumen Word dengan gambar tersembunyi – panduan Java langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Create word document in Java and learn how to hide image, add image
    word, and insert hidden picture with Aspose.Words.
  headline: Create word document with a hidden image in Java using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Buat dokumen Word dengan gambar tersembunyi di Java menggunakan Aspose.Words
url: /id/java/images-shapes/create-word-document-with-a-hidden-image-in-java-using-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word dengan gambar tersembunyi di Java menggunakan Aspose.Words

Jika Anda perlu **membuat dokumen Word** secara programatis, Aspose.Words for Java mempermudahnya. Tutorial ini menunjukkan **cara menyembunyikan gambar**, **menambahkan gambar ke Word**, dan **menyisipkan gambar tersembunyi** dalam satu dokumen sambil menjaga tata letak tetap bersih.

Otomatisasi dokumen sering memerlukan penyematan logo, watermark, atau placeholder yang tidak boleh mengganggu konten yang terlihat. Dengan menandai sebuah shape sebagai tersembunyi, Anda menyimpan gambar dalam file untuk penggunaan nanti (mis., untuk pembuatan konten bersyarat) tanpa menampilkannya kepada pengguna akhir. Anda akan mengikuti alur kerja lengkap, mulai dari menginisialisasi dokumen hingga menyimpan file `.docx` akhir.

## Apa yang akan Anda pelajari

* Bagaimana cara **membuat dokumen Word** dari awal menggunakan `Document` dan `DocumentBuilder`.
* Langkah tepat untuk **menambahkan gambar ke Word** dan kemudian menyembunyikan gambar tersebut dengan metode `setHidden(true)`.
* Cara kerja teknik **cara menyembunyikan shape** di balik layar dan mengapa teknik ini dapat diandalkan di semua versi Word.
* Cara **menyisipkan gambar tersembunyi** sehingga gambar tetap berada dalam file tetapi tidak terlihat dalam tata letak.
* Kesulitan umum seperti jalur file yang salah, format gambar yang tidak didukung, dan cara memverifikasi bahwa gambar benar‑benar tersembunyi.

> **Prasyarat** – Anda memerlukan Java 8+ terpasang, proyek Maven atau Gradle, dan lisensi Aspose.Words for Java yang valid (atau lisensi evaluasi gratis). Tidak diperlukan pustaka eksternal lainnya.

## Buat dokumen Word dan sisipkan gambar tersembunyi

Langkah pertama adalah membuat instance objek `Document` baru. Objek ini mewakili seluruh file Word dalam memori.

```java
import com.aspose.words.*;

public class HiddenShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting*: `Document` adalah kontainer untuk semua bagian file Word (gaya, seksi, gambar, dll.). `DocumentBuilder` menyediakan API yang fluently untuk menambahkan konten tanpa harus berurusan dengan struktur Open XML tingkat rendah.

## Cara menyembunyikan gambar menggunakan properti shape

Gambar dalam dokumen Word disimpan sebagai objek `Shape`. Menetapkan flag `Hidden` memberi tahu Word untuk mengecualikan shape dari tata letak sambil tetap mempertahankannya dalam file.

```java
        // Step 3: Insert an image into the document
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // Step 4: Mark the inserted shape as hidden so it won't appear in the layout
        imageShape.setHidden(true);
```

*Penjelasan*:
* `insertImage` membuat `Shape` bertipe `Picture`.
* `setHidden(true)` mengaktifkan atribut “Hidden” pada Word, yang dihormati oleh mesin tata letak. Gambar tetap tersemat, sehingga Anda dapat kemudian menampilkannya kembali secara programatis atau melalui UI Word.

> **Tip profesional**: Gunakan PNG untuk kualitas lossless, dan jaga ukuran gambar tetap kecil (di bawah 200 KB) untuk menghindari pembesaran file `.docx`.

## Tambahkan gambar ke Word dan verifikasi status tersembunyi

Meskipun gambar tersembunyi, Anda mungkin masih ingin merujuknya dalam teks dokumen (mis., “Logo perusahaan”). Anda dapat menambahkan caption atau paragraf placeholder sebelum menyembunyikan shape.

```java
        // Optional: Add a caption that explains the hidden image
        builder.moveToDocumentEnd();
        builder.writeln("Company logo (hidden)"); // This text is visible
```

*Mengapa Anda mungkin melakukan ini*: Beberapa alur kerja memerlukan penanda teks sehingga proses hilir dapat menemukan gambar tersembunyi tanpa harus mem-parsing bagian biner dokumen.

## Sisipkan gambar tersembunyi dan simpan file

Akhirnya, simpan dokumen ke disk. Gambar tersembunyi tetap tersemat tetapi tidak terlihat ketika file dibuka di Microsoft Word.

```java
        // Step 5: Save the document with the hidden shape
        document.save("YOUR_DIRECTORY/HiddenShapeDemo.docx");
    }
}
```

*Verifikasi*: Buka `HiddenShapeDemo.docx` di Word. Anda akan melihat caption “Company logo (hidden)” tetapi tidak ada gambar yang terlihat. Untuk memastikan gambar ada, buka file sebagai arsip ZIP (`.docx` adalah kontainer ZIP) dan periksa `word/media`. PNG yang Anda tambahkan akan ada.

## Kasus tepi umum dan cara menanganinya

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **Jalur gambar tidak valid** | `FileNotFoundException` pada `insertImage` | Gunakan `Paths.get(...).toAbsolutePath()` atau periksa `Files.exists()` sebelum penyisipan. |
| **Format gambar tidak didukung** (mis., BMP) | Aspose melempar `UnsupportedImageFormatException` | Konversi gambar ke PNG atau JPEG sebelum memanggil `insertImage`. |
| **Flag hidden diabaikan** (versi Word yang jarang) | Gambar masih muncul dalam tata letak | Pastikan Anda menggunakan Aspose.Words 22.9+ di mana `setHidden` memetakan ke atribut OOXML yang tepat (`<w:hidden/>`). |
| **Ukuran gambar besar** | Dokumen menjadi lambat | Ubah ukuran gambar menggunakan `imageShape.setWidth(100); imageShape.setHeight(50);` sebelum menyembunyikannya. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, sesuaikan jalurnya, dan jalankan langsung.

```java
import com.aspose.words.*;

public class HiddenShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document document = new Document();

        // 2. Prepare a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Insert the image (replace with your actual file)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // 4. Hide the shape so it doesn't affect layout
        imageShape.setHidden(true);

        // 5. (Optional) Add a visible caption for context
        builder.moveToDocumentEnd();
        builder.writeln("Company logo (hidden)");

        // 6. Save the result
        document.save("YOUR_DIRECTORY/HiddenShapeDemo.docx");
    }
}
```

**Output yang diharapkan**: Saat Anda membuka `HiddenShapeDemo.docx` di Microsoft Word, dokumen berisi teks “Company logo (hidden)” dan tidak ada gambar yang terlihat. PNG tersembunyi dapat dikonfirmasi di dalam folder `word/media` dari file `.docx` yang di‑zip.

## Cara menyembunyikan shape vs. cara menyembunyikan gambar

Dalam terminologi Word, baik gambar maupun gambar vektor diperlakukan sebagai **shape**. Metode `setHidden(true)` berfungsi untuk semua tipe shape, sehingga pendekatan yang sama berlaku untuk grafik vektor, kotak teks, atau diagram. Jika Anda perlu menyembunyikan shape yang bukan gambar, cukup dapatkan referensi `Shape` (mis., melalui `builder.insertShape(ShapeType.LINE, 100, 0)`) dan panggil `setHidden(true)`.

## Langkah selanjutnya dan topik terkait

* **Ganti gambar tersembunyi saat runtime** – Muat dokumen nanti, temukan shape tersembunyi berdasarkan `Name` atau `AlternativeText`, dan ganti data gambar.  
* **Konten bersyarat** – Gabungkan shape tersembunyi dengan Mail Merge untuk menampilkan atau menyembunyikan gambar berdasarkan bidang data.  
* **Bekerja dengan WordprocessingML** – Periksa XML dasar (`<w:pict>` dan `<w:hidden/>`) jika Anda memerlukan penyesuaian tingkat rendah.  

Ekstensi ini memungkinkan Anda membangun pipeline pembuatan dokumen yang canggih sambil menjaga logika inti **membuat dokumen Word** tetap bersih dan dapat dipelihara.

---

*Anda kini tahu cara membuat dokumen Word, menambahkan gambar, dan menyembunyikan gambar tersebut menggunakan Aspose.Words for Java. Bereksperimenlah dengan menyisipkan beberapa gambar tersembunyi, mengubah visibilitasnya, atau mengintegrasikan teknik ini ke dalam sistem pelaporan yang lebih besar.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Inline Image In Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert Floating Image In Word Document](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}