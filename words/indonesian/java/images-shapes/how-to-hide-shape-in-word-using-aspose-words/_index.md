---
category: general
date: 2026-11-25
description: Sembunyikan bentuk di Word dengan Aspose.Words dan pelajari cara membuat
  dokumen Word Aspose saat Anda menyisipkan bentuk persegi panjang hanya dengan beberapa
  baris kode.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: id
lastmod: 2026-11-25
og_description: Sembunyikan bentuk di Word menggunakan Aspose.Words. Tutorial ini
  menunjukkan cara membuat dokumen Word dengan Aspose, menyisipkan bentuk persegi
  panjang di Word, dan menyembunyikannya secara programatis.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Sembunyikan bentuk di Word dengan Aspose.Words – panduan langkah demi langkah
  cepat
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Cara menyembunyikan bentuk di Word menggunakan Aspose.Words
url: /id/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyembunyikan shape di Word menggunakan Aspose.Words

Jika Anda perlu **menyembunyikan shape di Word** saat menghasilkan dokumen secara programatis, Aspose.Words membuatnya menjadi sangat mudah. Dalam panduan ini Anda akan melihat secara tepat cara membuat dokumen Word aspose, menyisipkan rectangle shape word, dan kemudian menyembunyikan shape tersebut sehingga tidak muncul di tata letak. Contoh lengkap yang dapat dijalankan disediakan sehingga Anda dapat menyalin‑tempelnya ke IDE Anda dan melihat hasilnya segera.

Anda akan menyelesaikan tutorial ini dengan file Word yang berisi rectangle tersembunyi—berguna untuk placeholder, konten bersyarat, atau metadata yang harus tetap tidak terlihat oleh pembaca. Tidak ada alat eksternal yang diperlukan selain pustaka Aspose.Words untuk Java (atau .NET).

## Apa yang akan Anda pelajari

* Cara **membuat dokumen Word aspose** dari awal.  
* Cara **menyisipkan rectangle shape word** menggunakan `DocumentBuilder`.  
* Cara mengatur properti `hidden` pada shape sehingga tidak dirender dalam tata letak akhir.  
* Cara memverifikasi bahwa shape tersembunyi dan cara menampilkannya kembali bila diperlukan.  

### Prasyarat

* Java 17+ (atau .NET 6+ jika Anda lebih suka C#—panggilan API-nya serupa).  
* Aspose.Words untuk Java 24.x (versi terbaru pada saat penulisan).  
* Sebuah IDE seperti IntelliJ IDEA, Eclipse, atau VS Code.  

> **Pro tip:** Gunakan lisensi sementara gratis dari Aspose jika Anda belum memiliki lisensi komersial. Pustaka ini dapat bekerja tanpa lisensi untuk evaluasi, tetapi lisensi menghilangkan watermark evaluasi.

## Menyembunyikan shape di Word dengan Aspose.Words

Langkah‑langkah inti adalah:

1. **Buat `Document` baru.**  
2. **Sisipkan rectangle shape** menggunakan `DocumentBuilder`.  
3. **Tandai shape sebagai tersembunyi** sehingga tidak muncul saat file dibuka.  

Setiap langkah dijelaskan di bawah ini dengan kode dan penjelasannya.

### Langkah 1: Buat dokumen Word aspose

Pertama, buat instance `Document` kosong dan `DocumentBuilder`. Builder menyediakan API yang fluida untuk menambahkan konten, termasuk shape.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:**  
Membuat `Document` baru memberi Anda kanvas yang bersih. `DocumentBuilder` adalah cara yang direkomendasikan untuk memodifikasi dokumen karena secara otomatis melacak titik penyisipan saat ini dan menangani manajemen section/halaman untuk Anda.

### Langkah 2: Sisipkan rectangle shape word

Sekarang kita menambahkan rectangle shape. Metode `insertShape` memerlukan tipe shape dan dimensinya dalam point (1 point = 1/72 inci).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Mengapa ini penting:**  
`insertShape` membuat objek gambar yang berada di bagian *drawing* dokumen. Dengan menentukan ukuran, Anda mengontrol berapa banyak ruang yang akan ditempati shape jika terlihat. Styling opsional membantu Anda memverifikasi shape sebelum menyembunyikannya.

### Langkah 3: Sembunyikan shape sehingga tidak muncul di tata letak

Aspose.Words mencerminkan atribut *Hidden* Microsoft Word. Menetapkannya ke `true` memberi tahu Word untuk tidak merender shape, sambil tetap mempertahankan objek dalam struktur dokumen.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Mengapa ini penting:**  
Shape yang tersembunyi masih dapat diakses secara programatis (misalnya untuk pemrosesan bersyarat) dan dapat ditampilkan kembali nanti dengan mengubah properti tersebut. Ini ideal untuk skenario seperti **placeholder bersyarat** yang hanya muncul untuk audiens tertentu.

### Langkah 4: Simpan dan verifikasi hasilnya

Akhirnya, tulis dokumen ke disk. Buka file tersebut di Microsoft Word untuk memastikan rectangle tidak terlihat. Anda juga dapat memeriksa XML dasar untuk melihat flag tersembunyi.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Output yang diharapkan:**  
Menjalankan program mencetak:

```
Document saved to HideShapeResult.docx
```

Saat Anda membuka *HideShapeResult.docx* di Word, halaman tampak kosong (atau berisi konten lain yang Anda tambahkan sebelum shape). Rectangle ada dalam XML file (`<w:hidden>` attribute) tetapi tidak dirender.

### Langkah 5: (Opsional) Tampilkan kembali shape nanti

Jika Anda perlu membuat shape terlihat kembali, muat dokumen, temukan shape tersebut, dan set `hidden` ke `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Mengapa ini penting:**  
Kemampuan untuk mengubah flag tersembunyi memberi Anda kontrol penuh atas pembuatan dokumen dinamis—misalnya, Anda dapat menghasilkan dokumen master dengan semua elemen opsional tersembunyi, lalu menampilkannya secara selektif berdasarkan preferensi pengguna.

## Contoh lengkap yang dapat dijalankan (buat dokumen word aspose, sisipkan rectangle shape word, sembunyikan shape)

Berikut adalah program lengkap yang dapat Anda kompilasi dan jalankan langsung.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Menjalankan kode**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Ganti `aspose-words-24.10.jar` dengan versi aktual yang Anda unduh.

### Apa yang terkandung dalam file output

* **HideShapeResult.docx** – rectangle tersembunyi; halaman tampak kosong.  
* **UnhiddenShape.docx** – rectangle yang sama terlihat, menampilkan kotak merah dengan outline hitam.

## Pertanyaan umum & penanganan kasus tepi

| Pertanyaan | Jawaban |
|----------|--------|
| *Apakah shape tersembunyi memengaruhi pagination?* | Tidak. Objek tersembunyi diabaikan oleh mesin tata letak, sehingga tidak memindahkan teks ke halaman baru. |
| *Bisakah saya menyembunyikan objek Word lain (misalnya gambar, tabel)?* | Ya. Sebagian besar subclass `Node` (termasuk `Shape`, `Paragraph`, `Run`) menyediakan metode `setHidden(boolean)`. |
| *Bagaimana jika dokumen sudah berisi shape?* | Gunakan `doc.getChildNodes(NodeType.SHAPE, true)` untuk mengiterasi dan menyembunyikan hanya shape yang Anda targetkan. |
| *Apakah menyembunyikan shape meningkatkan ukuran file?* | Sedikit, karena XML shape tetap ada. Dampaknya dapat diabaikan untuk dokumen biasa. |
| *Apakah flag tersembunyi tetap ada saat dokumen disimpan sebagai PDF?* | Saat mengonversi ke PDF, shape tersembunyi secara default diabaikan. Anda dapat mengontrolnya dengan `PdfSaveOptions` bila diperlukan. |

## Praktik terbaik saat bekerja dengan objek tersembunyi

* **Berikan nama pada shape** menggunakan `setName("MyPlaceholder")`. Ini memudahkan pencarian nanti.  
* **Kelompokkan objek tersembunyi terkait** di dalam `GroupShape` jika Anda perlu mengubah visibilitas beberapa elemen sekaligus.  
* **Dokumentasikan tujuan** elemen tersembunyi dalam komentar atau file spesifikasi terpisah—pemelihara di masa depan akan menghargai konteksnya.  
* **Hindari penggunaan berlebihan** objek tersembunyi; mereka menambah kompleksitas dokumen dan dapat membingungkan pengguna yang memeriksa XML secara manual.

## Kesimpulan

Anda kini tahu cara **menyembunyikan shape di Word** menggunakan Aspose.Words, cara **membuat dokumen Word aspose**, dan cara **menyisipkan rectangle shape word** sebelum menyembunyikannya. Contoh ini menunjukkan siklus lengkap: pembuatan, penyisipan, penyembunyian, penyimpanan, dan opsional menampilkan kembali. Terapkan teknik ini untuk membangun laporan dinamis, template bersyarat, atau alur kerja Word otomatis lainnya di mana placeholder tak terlihat diperlukan.

### Langkah selanjutnya

* Jelajahi **konten bersyarat** dengan menggabungkan shape tersembunyi dan field mail‑merge.  
* Pelajari cara **menyembunyikan run teks** (`Run.setHidden(true)`) untuk kontrol yang lebih granular.  
* Lihat dokumentasi Aspose.Words tentang **perlindungan dokumen** untuk mencegah pengguna secara tidak sengaja menampilkan kembali shape.

Selamat coding, dan biarkan file Word yang Anda hasilkan tetap bersih sambil tetap membawa data tersembunyi yang Anda perlukan!

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}