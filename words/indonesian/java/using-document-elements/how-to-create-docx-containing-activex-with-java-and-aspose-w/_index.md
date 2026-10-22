---
category: general
date: 2026-09-27
description: Buat docx yang berisi ActiveX dalam Java menggunakan Aspose.Words. Pelajari
  cara menyisipkan tombol perintah ActiveX langkah demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: id
lastmod: 2026-09-27
og_description: Buat file docx yang berisi ActiveX dalam Java dengan Aspose.Words.
  Ikuti panduan ini untuk menyisipkan tombol perintah ActiveX dan menyimpan dokumen.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Buat docx yang berisi ActiveX di Java – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Cara membuat docx yang berisi ActiveX dengan Java dan Aspose.Words
url: /id/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat docx yang berisi ActiveX dengan Java dan Aspose.Words

Jika Anda perlu **membuat docx yang berisi ActiveX**, panduan ini menunjukkan solusi lengkap. Anda akan belajar cara **menyisipkan tombol perintah ActiveX** ke dalam file Word menggunakan Aspose.Words untuk Java, kemudian menyimpan hasilnya sebagai .docx yang dapat dibuka di Microsoft Word.

Membuat dokumen Word secara programatik menghemat Anda dari penyuntingan manual dan menjamin konsistensi di seluruh laporan, kontrak, atau templat formulir. Langkah‑langkah di bawah ini mencakup semua hal mulai dari penyiapan proyek hingga penanganan masalah umum, sehingga Anda dapat mengintegrasikan teknik ini ke dalam aplikasi Java apa pun.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java Development Kit (JDK) 8 atau yang lebih baru terpasang.  
* Maven 3.6+ (atau alat build lain yang Anda sukai).  
* File lisensi Aspose.Words untuk Java (evaluasi gratis dapat digunakan untuk pengujian).  
* Microsoft Word terpasang pada mesin target jika Anda ingin memverifikasi kontrol ActiveX secara visual.

Item‑item ini diperlukan karena Aspose.Words menyediakan API yang membuat dokumen, sementara Word dibutuhkan untuk merender kontrol ActiveX.

## Langkah 1: Siapkan proyek Maven

Buat proyek Maven baru atau tambahkan dependensi Aspose.Words ke `pom.xml` yang sudah ada:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Tips pro:** Jaga versi Aspose.Words tetap selaras dengan catatan rilis resmi untuk mendapatkan perbaikan bug dan fitur ActiveX terbaru.

## Langkah 2: Tulis kode Java yang membuat dokumen

Buat kelas bernama `ActiveXDocxCreator`. Kode di bawah ini mencakup semua impor yang diperlukan, metode `main`, dan komentar terperinci yang menjelaskan setiap operasi.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Mengapa setiap baris penting

* `Document` adalah kontainer untuk semua konten Word. Membuat instance baru memberikan kanvas yang bersih.  
* `DocumentBuilder` menyediakan API yang fluida untuk menyisipkan elemen; ia secara otomatis melacak titik penyisipan.  
* `insertForms2OleControl()` membuat placeholder kontrol OLE generik. Aspose.Words memperlakukannya sebagai kontainer ActiveX.  
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` memberi tahu Word bahwa placeholder harus dirender sebagai CommandButton.  
* `setCaption("Click Me")` menentukan teks yang ditampilkan pada tombol.  
* `setLeft` dan `setTop` menempatkan tombol relatif terhadap margin halaman. Sesuaikan nilai‑nilai ini agar cocok dengan tata letak Anda.  
* `setWidth` dan `setHeight` bersifat opsional tetapi meningkatkan tampilan tombol, terutama bila ukuran default terlalu kecil.  
* `doc.save` menulis struktur dalam memori ke file .docx fisik yang dapat dibuka oleh Word.

## Langkah 3: Verifikasi dokumen yang dihasilkan

Buka `output/ActiveXCommandButton.docx` di Microsoft Word:

1. Dokumen harus menampilkan satu halaman dengan tombol berlabel **Click Me** yang berada di dekat sudut kiri‑atas.  
2. Jika tombol tidak muncul, periksa bahwa **kontrol ActiveX diaktifkan** di Trust Center Word (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).  
3. Tombol hanya berfungsi pada versi Windows Word yang mendukung ActiveX. Pada macOS atau Word berbasis web, kontrol akan ditampilkan sebagai gambar statis.

## Langkah 4: Menangani kasus tepi umum

| Situasi | Alasan | Tindakan yang disarankan |
|-----------|--------|--------------------|
| Tombol tidak muncul setelah membuka file | Pengaturan keamanan Word memblokir ActiveX | Aktifkan “Run all controls without restrictions” untuk lokasi tepercaya. |
| .docx yang dihasilkan tidak dapat dibuka | Versi Aspose.Words tidak kompatibel | Tingkatkan ke rilis Aspose.Words terbaru; versi lama mungkin tidak menyematkan bagian OLE yang diperlukan dengan benar. |
| Anda memerlukan tombol untuk mengeksekusi makro | ActiveX saja tidak berisi kode makro | Gabungkan kontrol ActiveX dengan makro VBA yang menangani peristiwa `Click`. Gunakan metode `DocumentBuilder.insertOleObject` untuk menyematkan templat yang mendukung makro. |
| Tata letak tidak tepat pada ukuran halaman yang berbeda | Koordinat menggunakan titik absolut | Gunakan `builder.getPageSetup().setPageWidth` dan `setPageHeight` untuk menstandarisasi ukuran halaman sebelum memposisikan kontrol. |

## Langkah 5: Memperluas solusi

Anda dapat menyisipkan kontrol ActiveX lain dengan mengubah enum `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words juga mendukung penyisipan **kotak teks ActiveX**, **list box**, dan **combo box**. Metode penempatan yang sama (`setLeft`, `setTop`, `setWidth`, `setHeight`) berlaku.

Jika Anda perlu menempatkan beberapa kontrol, panggil `builder.insertForms2OleControl()` berulang kali dan sesuaikan koordinat masing‑masing kontrol sesuai kebutuhan.

## File sumber lengkap

Berikut adalah seluruh file `ActiveXDocxCreator.java` yang siap untuk disalin‑tempel:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Menjalankan program ini menghasilkan **docx yang berisi ActiveX** yang dapat Anda distribusikan kepada pengguna akhir yang memerlukan formulir interaktif.

## Kesimpulan

Anda kini tahu cara **membuat docx yang berisi ActiveX** menggunakan Java dan Aspose.Words, serta cara **menyisipkan tombol perintah ActiveX** secara programatik. Tutorial ini mencakup penyiapan proyek, kode sumber lengkap, langkah verifikasi, dan strategi untuk mengatasi masalah umum.

Dari sini Anda dapat menjelajahi:

* Menambahkan makro VBA untuk menanggapi klik tombol.  
* Menyematkan kontrol ActiveX lain seperti kotak centang atau combo box.  
* Mengotomatiskan pembuatan formulir multi‑halaman dengan data dinamis.

Bereksperimenlah dengan koordinat, ukuran, dan tipe kontrol yang berbeda untuk menyesuaikan tata letak dokumen Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menggunakan OLE Objects dan Kontrol ActiveX di Aspose.Words untuk Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Membuat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}