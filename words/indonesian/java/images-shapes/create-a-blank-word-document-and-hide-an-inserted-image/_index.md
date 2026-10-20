---
category: general
date: 2026-10-20
description: Buat dokumen Word kosong, sisipkan gambar, sembunyikan bentuknya, dan
  simpan file sebagai DOCX. Pelajari cara menyembunyikan gambar di Word dengan panduan
  langkah demi langkah yang jelas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- how to hide image
- save document as docx
- hide shape in word
language: id
lastmod: 2026-10-20
og_description: Buat dokumen Word kosong, lalu sembunyikan gambar yang dimasukkan
  dan simpan sebagai DOCX dengan tutorial lengkap ini.
og_image_alt: Screenshot of a blank Word document with a hidden image shape
og_title: Buat dokumen Word kosong dan sembunyikan gambar – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank Word document, insert an image, hide the shape, and
    save the file as DOCX. Learn how to hide image in Word with a clear step‑by‑step
    guide.
  headline: Create a blank Word document and hide an inserted image
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- Java
- Document processing
title: Buat dokumen Word kosong dan sembunyikan gambar yang dimasukkan
url: /id/java/images-shapes/create-a-blank-word-document-and-hide-an-inserted-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan sembunyikan gambar yang dimasukkan

Jika Anda perlu **create blank word document** yang kemudian berisi gambar yang tidak ingin muncul dalam tata letak, tutorial ini menunjukkan cara melakukannya secara tepat. Anda akan belajar cara menyisipkan gambar ke dalam Word, menyembunyikan shape, dan akhirnya **save document as docx** sehingga gambar tersembunyi tetap tidak terlihat oleh pembaca.

Panduan ini menelusuri setiap baris kode, menjelaskan mengapa setiap pemanggilan penting, dan mencakup jebakan umum seperti file gambar yang hilang atau beberapa shape tersembunyi. Pada akhir tutorial Anda akan memiliki metode yang dapat digunakan kembali yang bekerja dengan Aspose.Words for Java (versi 23.10 atau lebih baru).

## Prasyarat

* Java 17 atau yang lebih baru terinstal.
* Perpustakaan Aspose.Words for Java (artefak Maven `com.aspose:aspose-words:23.10`).
* File gambar (misalnya `logo.png`) ditempatkan di direktori yang diketahui.
* Pemahaman dasar tentang struktur proyek Java.

## Langkah 1: Buat dokumen Word kosong

Operasi pertama adalah menginstansiasi objek `Document` yang kosong. Objek ini mewakili seluruh file DOCX dan dimulai tanpa bagian atau konten apa pun.

```java
import com.aspose.words.*;

public class WordImageHider {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();          // <-- primary action
        // Continue with the remaining steps
        insertAndHideImage(doc, "YOUR_DIRECTORY/logo.png");
        doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX);
    }
}
```

**Mengapa ini penting:**  
Dokumen kosong memberi Anda kanvas bersih. Aspose.Words secara otomatis menambahkan bagian default dan satu badan kosong, sehingga Anda dapat mulai menambahkan shape tanpa khawatir tentang pengaturan halaman.

## Langkah 2: Sisipkan gambar ke dalam Word

Untuk menempatkan gambar, Anda memerlukan `DocumentBuilder`. Builder bekerja pada node saat ini (badan dokumen) dan menyediakan metode `insertImage`, yang mengembalikan objek `Shape` yang mewakili gambar.

```java
private static void insertAndHideImage(Document doc, String imagePath) throws Exception {
    // Initialize a DocumentBuilder to work with the document
    DocumentBuilder builder = new DocumentBuilder(doc);

    // Insert the image and capture the Shape object
    Shape imageShape = builder.insertImage(imagePath);   // <-- secondary keyword
    // Proceed to hide the shape
    hideShape(imageShape);
}
```

**Mengapa ini penting:**  
`insertImage` menyisipkan gambar sebagai **shape**. `Shape` yang dikembalikan memungkinkan Anda menyesuaikan properti seperti ukuran, tata letak, dan visibilitas. Jika jalur file tidak benar, Aspose akan melempar `IllegalArgumentException`, jadi Anda mungkin ingin membungkus pemanggilan tersebut dalam blok try‑catch untuk kode produksi.

## Langkah 3: Sembunyikan shape di Word

Sebuah shape dapat disembunyikan dengan mengatur properti `Hidden` menjadi `true`. Ketika dokumen dibuka di Microsoft Word, shape tidak berpartisipasi dalam tata letak atau pencetakan, namun tetap ada dalam file.

```java
private static void hideShape(Shape shape) {
    // Hide the shape so it does not appear in the layout
    shape.setHidden(true);               // <-- how to hide image
}
```

**Mengapa ini penting:**  
Menyembunyikan shape berguna untuk watermark, grafik latar belakang, atau gambar metadata yang tidak boleh mengganggu pembaca. Bendera tersembunyi disimpan dalam XML dasar (`<w:hidden/>`), membuat gambar tidak terlihat tanpa menghapusnya.

### Kasus khusus: beberapa gambar tersembunyi

Jika Anda memerlukan beberapa gambar tak terlihat, ulangi urutan insert‑and‑hide untuk setiap gambar. Pemanggilan `setHidden(true)` bekerja secara independen pada setiap instance `Shape`.

```java
// Example for inserting two hidden logos
builder.insertImage("logo1.png").setHidden(true);
builder.insertImage("logo2.png").setHidden(true);
```

## Langkah 4: Simpan dokumen sebagai DOCX

Akhirnya, simpan `Document` yang berada di memori ke file fisik. Konstanta `SaveFormat.DOCX` memastikan file disimpan dalam format Office Open XML modern.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX); // <-- save document as docx
```

**Mengapa ini penting:**  
Menyimpan sebagai DOCX mempertahankan semua properti shape, termasuk bendera tersembunyi. Jika Anda menyimpan dalam format lama (mis., `.doc`), beberapa atribut shape mungkin hilang.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semuanya, berikut adalah program mandiri yang dapat Anda kompilasi dan jalankan:

```java
import com.aspose.words.*;

public class WordImageHider {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();

        // 2️⃣ Insert an image and obtain the Shape object
        DocumentBuilder builder = new DocumentBuilder(doc);
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // 3️⃣ Hide the shape so it does not appear in the layout
        imageShape.setHidden(true);

        // 4️⃣ Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX);

        System.out.println("Document created and saved successfully.");
    }
}
```

**Hasil yang diharapkan:**  
Membuka `HiddenShape.docx` di Microsoft Word menampilkan halaman yang sepenuhnya kosong. File gambar ada dalam paket dokumen (Anda dapat memverifikasinya dengan membuka DOCX sebagai zip), tetapi tidak ditampilkan karena shape disembunyikan.

## Pertanyaan umum dan pemecahan masalah

| Question | Answer |
|----------|--------|
| *Bagaimana jika file gambar tidak ada?* | Aspose.Words melempar `FileNotFoundException`. Bungkus `insertImage` dalam blok try‑catch dan catat pesan yang membantu. |
| *Apakah saya dapat menampilkan kembali gambar tersebut nanti?* | Ya. Dapatkan shape (`doc.getChildNodes(NodeType.SHAPE, true)`) dan panggil `setHidden(false)`. |
| *Apakah menyembunyikan memengaruhi konversi ke PDF?* | Saat mengonversi ke PDF, shape tersembunyi secara default diabaikan. Gunakan `PdfSaveOptions.setExportHiddenObjects(true)` jika Anda membutuhkannya. |
| *Apakah bendera tersembunyi didukung di versi Word yang lebih lama?* | Word 2007+ (DOCX) mendukungnya sepenuhnya. Format legacy `.doc` mungkin menghilangkan bendera tersebut. |

## Tips profesional

* **Reuse the builder:** Jika Anda berencana menambahkan lebih banyak konten setelah gambar, pertahankan instance `DocumentBuilder` yang sama; ia mempertahankan posisi kursor.
* **Set shape size before hiding:** Sesuaikan `imageShape.setWidth(100); imageShape.setHeight(50);` untuk mengontrol dimensi gambar tersembunyi, yang dapat memengaruhi ukuran file.
* **Batch processing:** Untuk batch besar, buat dokumen sekali, sisipkan semua gambar tersembunyi, lalu simpan—ini mengurangi beban I/O.

## Kesimpulan

Anda sekarang tahu cara **create blank word document**, **insert image into word**, **hide shape in word**, dan **save document as docx** menggunakan Aspose.Words for Java. Gambar tersembunyi tetap tidak terlihat oleh pengguna akhir sekaligus menjadi bagian dari file, memungkinkan skenario seperti watermark tak terlihat atau penyimpanan metadata.

**Langkah selanjutnya:**  
* Jelajahi properti shape lainnya seperti rotasi, flip, dan pembungkus teks.  
* Pelajari cara menambahkan watermark yang terlihat dengan `Shape.setWrapType(WrapType.NONE)`.  
* Integrasikan rutinitas ini ke dalam layanan web yang menghasilkan laporan khusus secara dinamis.

Silakan bereksperimen dengan beberapa shape tersembunyi, format gambar berbeda (PNG, JPEG, SVG), dan gabungkan teknik ini dengan penggabungan dokumen untuk pipeline dokumen otomatis yang kuat. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Kosong dengan Shape Elips Tersembunyi – Panduan Lengkap C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)
- [Sisipkan Gambar Mengambang dalam Dokumen Word](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Buat dokumen word kosong dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}