---
category: general
date: 2026-10-04
description: Pelajari cara menginisialisasi DocumentBuilder untuk dokumen baru dan
  menambahkan tombol ActiveX dengan Aspose.Words di Java. Panduan langkah demi langkah
  dengan kode lengkap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: id
lastmod: 2026-10-04
og_description: Inisialisasi DocumentBuilder untuk dokumen baru dan sematkan tombol
  perintah ActiveX menggunakan Aspose.Words Java API. Ikuti tutorial singkat ini.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Inisialisasi DocumentBuilder untuk dokumen baru – panduan lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Cara menginisialisasi DocumentBuilder untuk dokumen baru menggunakan Aspose.Words
url: /id/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menginisialisasi DocumentBuilder untuk dokumen baru menggunakan Aspose.Words

Jika Anda perlu **menginisialisasi DocumentBuilder untuk dokumen baru** dalam proyek Java, tutorial ini menunjukkan langkah‑langkah tepatnya. Anda akan melihat cara membuat file Word kosong, menambahkan tombol perintah ActiveX, dan menyimpan hasilnya—semua dengan satu contoh kode yang berdiri sendiri.

Bekerja dengan dokumen Word secara programatik sering berarti menangani detail tingkat rendah seperti kontrol formulir. Pada akhir panduan ini Anda akan dapat menyematkan tombol ActiveX tanpa meninggalkan IDE Anda, yang berguna untuk menghasilkan templat, laporan otomatis, atau formulir interaktif.

## Prasyarat

* Java 17 atau lebih baru terpasang  
* Maven 3.8+ (atau Gradle jika Anda lebih suka)  
* Lisensi Aspose.Words untuk Java (versi percobaan gratis dapat digunakan untuk pengujian)  
* Pemahaman dasar tentang sintaks Java  

Jika Anda baru mengenal Aspose.Words, perpustakaan ini menyediakan API tingkat tinggi untuk membuat, mengedit, dan menyimpan dokumen Word. Kelas `DocumentBuilder` adalah titik masuk utama untuk membangun konten dokumen.

## Langkah 1: Siapkan proyek Maven

Buat proyek Maven baru (atau tambahkan ke proyek yang sudah ada) dan sertakan dependensi Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Tips profesional:** Jaga versi perpustakaan tetap terbaru; rilis yang lebih baru menambahkan dukungan untuk kontrol formulir tambahan dan meningkatkan kinerja.

## Langkah 2: Inisialisasi `DocumentBuilder` untuk dokumen baru

Inti tutorial ini adalah operasi **menginisialisasi DocumentBuilder untuk dokumen baru**. Anda pertama‑tama membuat instance `Document` yang kosong, lalu memberikannya ke konstruktor `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting:* Menginisialisasi `DocumentBuilder` mengikat builder ke objek `Document` tertentu, memungkinkan Anda menambahkan paragraf, tabel, atau kontrol formulir secara langsung ke dokumen tersebut. Tanpa langkah ini, builder tidak memiliki target untuk bekerja.

## Langkah 3: Sisipkan kontrol tombol perintah ActiveX

Aspose.Words menyediakan kelas `Forms2OleControl` untuk menyematkan kontrol ActiveX lama. Kode berikut menambahkan **tombol perintah Forms2OleControl** ke posisi kursor saat ini.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Apa itu tombol perintah ActiveX?

Tombol perintah ActiveX adalah elemen UI lama yang dapat menjalankan makro atau memicu peristiwa ketika pengguna mengkliknya di dalam dokumen Word. Meskipun versi Office modern lebih menyukai Content Controls, banyak templat perusahaan masih mengandalkan ActiveX untuk kompatibilitas mundur.

## Langkah 4: Simpan dokumen

Setelah menyisipkan kontrol, Anda cukup memanggil `save`. File tersebut akan berisi tombol ActiveX dan dapat dibuka di Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Saat Anda membuka `ActiveXButton.docx` di Word, Anda akan melihat tombol berlabel **Click Me**. Mengklik tombol tidak akan melakukan apa‑apa kecuali Anda melampirkan makro, tetapi kontrol itu sendiri berfungsi penuh.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke `src/main/java/com/example/ActiveXButtonDemo.java`. Program ini mencakup semua impor dan penanganan error yang diperlukan untuk pengujian cepat.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Output yang diharapkan**

```
Document saved to output/ActiveXButton.docx
```

Buka file yang dihasilkan di Microsoft Word 2016 atau yang lebih baru; Anda akan melihat tombol berlabel *Click Me* yang ditempatkan di bagian atas halaman pertama.

## Variasi umum dan kasus tepi

| Skenario | Penyesuaian |
|----------|------------|
| **Tambahkan tombol ke paragraf tertentu** | Pindahkan kursor builder dengan `builder.moveToParagraph(index, NodeType.PARAGRAPH);` sebelum memanggil `insertForms2OleControl`. |
| **Atur ukuran tombol** | Gunakan `commandButton.setWidth(100);` dan `commandButton.setHeight(30);` untuk menentukan dimensi dalam poin. |
| **Tambahkan makro ke tombol** | Setelah menyimpan dokumen, buka di Word, aktifkan tab Developer, dan lampirkan makro VBA ke tombol secara manual (kontrol ActiveX tidak dapat diprogram langsung dari Aspose.Words). |
| **Target format .doc (biner)** | Ubah `doc.save(outputPath, SaveFormat.DOC);` untuk menghasilkan file Word 97‑2003 lama. |
| **Jalankan di Android** | Gunakan Aspose.Words untuk Android melalui API Java‑nya; kode yang sama berfungsi selama perpustakaan disertakan dalam APK. |

## Tips pemecahan masalah

* **`java.lang.NoClassDefFoundError`** – Pastikan JAR Aspose.Words berada di classpath. Maven menambahkannya secara otomatis; untuk build manual, letakkan JAR di `libs/` dan tambahkan ke perpustakaan IDE Anda.  
* **Tombol tidak muncul di Word** – Pastikan opsi *Show legacy forms* diaktifkan di Trust Center Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **Pengecualian lisensi** – Jika Anda menjalankan kode tanpa lisensi yang valid, Aspose.Words akan menyisipkan watermark. Daftarkan percobaan gratis atau beli lisensi untuk menghilangkannya.

## Kesimpulan

Anda kini tahu cara **menginisialisasi DocumentBuilder untuk dokumen baru**, menyisipkan tombol perintah ActiveX, dan menyimpan hasilnya dengan Aspose.Words untuk Java. Pola ini memungkinkan Anda menghasilkan templat Word interaktif secara programatik, yang sangat berguna untuk pelaporan otomatis atau alur kerja berbasis formulir.

Dari sini Anda dapat menjelajahi kontrol formulir tambahan (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, dll.), menggabungkan tombol dengan makro VBA khusus, atau menghasilkan dokumen lengkap yang mencakup tabel, gambar, dan gaya—semua menggunakan alur kerja `DocumentBuilder` yang sama.

---

*Siap membangun otomatisasi Word yang lebih kompleks? Lihat panduan kami tentang **menyisipkan tabel dengan DocumentBuilder**, **menerapkan gaya secara programatik**, dan **mengekspor ke PDF dengan Aspose.Words**.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cara menyimpan dokumen sebagai pdf dengan Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Menambahkan watermark ke dokumen menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}