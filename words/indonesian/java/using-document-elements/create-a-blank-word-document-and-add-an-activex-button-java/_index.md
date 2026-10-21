---
category: general
date: 2026-10-16
description: Buat dokumen Word kosong dengan Java dan pelajari cara menambahkan tombol
  ActiveX, mengatur caption‑nya, serta menyesuaikan dimensinya menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: id
lastmod: 2026-10-16
og_description: Buat dokumen Word kosong dengan Java, kemudian tambahkan tombol ActiveX,
  atur caption‑nya, dan tentukan dimensinya menggunakan Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Buat dokumen Word kosong dan sematkan tombol ActiveX – Panduan Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Buat dokumen Word kosong dan tambahkan tombol ActiveX (Java)
url: /id/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan tambahkan tombol ActiveX (Java)

Jika Anda perlu **membuat dokumen Word kosong** secara programatis, panduan ini menunjukkan cara melakukannya dengan Java dan Aspose.Words. Anda juga akan belajar cara **menambahkan tombol ActiveX**, **mengatur caption tombol**, dan **mengatur dimensi tombol** sehingga kontrol terlihat persis seperti yang Anda harapkan.

Tutorial ini mencakup:

* Menginisialisasi file Word kosong dengan Aspose.Words untuk Java.  
* Menyisipkan kontrol ActiveX `CommandButton`.  
* Mengonfigurasi caption dan ukuran tombol.  
* Menyimpan file `.docx` akhir.

Anda harus memiliki pengetahuan dasar Java dan versi terbaru dari pustaka Aspose.Words untuk Java (kode ini bekerja dengan 23.9 dan yang lebih baru). Tidak ada dependensi tambahan yang diperlukan.

![Buat dokumen Word kosong dengan tombol ActiveX](/images/activex-button-example.png){: .align-center alt="Buat dokumen Word kosong dengan tombol ActiveX"}

## Buat dokumen Word kosong dengan Aspose.Words

Langkah pertama adalah menginstansiasi objek `Document` yang kosong. Objek ini mewakili seluruh file Word di memori dan menyediakan kelas `DocumentBuilder` untuk penyuntingan.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Mengapa ini penting:**  
Membuat dokumen kosong memberi Anda kanvas bersih, menghindari gaya atau bagian tersembunyi yang dapat mengganggu perhitungan tata letak nanti.

## Tambahkan tombol ActiveX ke dokumen

Aspose.Words memungkinkan Anda menyematkan kontrol ActiveX lama melalui kelas `Forms2OleControl`. Kode berikut menyisipkan kontrol `CommandButton` pada posisi kursor saat ini.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Tips:** Nilai `setOleClassName` `"Forms.CommandButton.1"` adalah ProgID untuk tombol Microsoft Forms standar. Menggunakan ProgID yang berbeda (misalnya, `"Forms.CheckBox.1"`) akan menyisipkan jenis kontrol yang lain.

## Atur caption tombol

Caption adalah teks yang muncul pada permukaan tombol. Anda dapat mengubahnya kapan saja sebelum menyimpan dokumen.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Mengapa Anda membutuhkannya:** Pengguna hanya memahami sebuah kontrol ketika tujuannya jelas. Menetapkan caption yang bermakna meningkatkan kegunaan, terutama ketika dokumen dibuka di Word pada Windows.

## Atur dimensi tombol

Posisi dan ukuran ditentukan dalam poin (1 poin = 1/72 inci). Sesuaikan nilai-nilai tersebut agar cocok dengan tata letak Anda.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Variasi umum:**

| Skenario | Penyesuaian |
|----------|------------|
| Tombol lebih besar untuk layar sentuh | Tingkatkan `setWidth` dan `setHeight` secara proporsional |
| Tombol terpusat pada halaman | Hitung `left = (pageWidth - width) / 2` |
| Beberapa tombol dalam satu kolom | Tingkatkan `setTop` untuk setiap tombol baru |

## Simpan dokumen yang berisi tombol ActiveX

Akhirnya, tulis dokumen ke disk. Format `.docx` mempertahankan kontrol ActiveX untuk versi Windows Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Hasil yang diharapkan:** Membuka `ActiveXCommandButton.docx` di Word (Windows) menampilkan halaman kosong dengan tombol yang dapat diklik berlabel **Click Me** yang ditempatkan 100 pt dari margin kiri dan 200 pt dari margin atas.

## Contoh lengkap yang dapat dijalankan

Salin seluruh kelas di bawah ini ke IDE Anda, tambahkan JAR Aspose.Words untuk Java ke classpath proyek, dan jalankan.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Menjalankan program menghasilkan `ActiveXCommandButton.docx` di direktori kerja. Buka dengan Microsoft Word (Windows) untuk memverifikasi bahwa tombol muncul persis seperti yang dikonfigurasi.

## Mengapa pendekatan ini direkomendasikan

* **Kesederhanaan:** Hanya API inti Aspose.Words yang digunakan; tidak diperlukan interop COM atau perpustakaan tambahan.  
* **Portabilitas:** Kode dapat dijalankan di platform apa pun yang mendukung Java, meskipun kontrol ActiveX sendiri hanya berfungsi pada versi Windows Microsoft Word.  
* **Kemudahan pemeliharaan:** Semua properti (caption, dimensi, posisi) diatur melalui metode yang jelas dan self‑documenting, sehingga penyesuaian di masa depan menjadi mudah.

## Jebakan umum dan cara menghindarinya

| Jebakan | Solusi |
|---------|------------|
| Tombol tidak muncul di Word pada macOS atau Linux | Kontrol ActiveX hanya tersedia di Windows. Gunakan kontrol lain (misalnya, content control) untuk dokumen lintas‑platform. |
| Caption terpotong | Pastikan lebar tombol cukup untuk teks; tingkatkan `setWidth` atau gunakan caption yang lebih pendek. |
| Tombol menimpa konten lain | Sesuaikan nilai `setTop` dan `setLeft`, atau sisipkan paragraf baru sebelum kontrol untuk memberi ruang tersendiri. |

## Langkah selanjutnya

Sekarang Anda dapat **membuat dokumen Word kosong**, **menambahkan tombol ActiveX**, **mengatur caption tombol**, dan **mengatur dimensi tombol**, Anda mungkin ingin menjelajahi:

* Menambahkan kode penanganan peristiwa melalui makro VBA (memerlukan penyisipan modul makro).  
* Menyisipkan beberapa kontrol dalam tata letak tabel untuk dokumen berbentuk formulir.  
* Menggunakan API **FormField** Aspose.Words untuk solusi formulir lintas‑platform.

Bereksperimenlah dengan ukuran, posisi, dan caption yang berbeda untuk menyesuaikan desain dokumen Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tambahkan watermark ke dokumen menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}