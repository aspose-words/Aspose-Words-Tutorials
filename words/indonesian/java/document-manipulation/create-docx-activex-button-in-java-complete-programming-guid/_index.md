---
category: general
date: 2026-08-14
description: Buat tombol ActiveX docx di Java dengan Aspose.Words. Pelajari cara menambahkan
  tombol formulir di Word secara programatis dan menyimpan dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: id
lastmod: 2026-08-14
og_description: Buat tombol ActiveX docx dalam Java menggunakan Aspose.Words. Panduan
  ini menunjukkan cara menambahkan tombol formulir di Word, mengkonfigurasinya, dan
  menyimpan file.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Buat tombol ActiveX docx di Java – tutorial langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Membuat tombol ActiveX docx di Java – panduan pemrograman lengkap
url: /id/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat tombol ActiveX docx di Java – panduan pemrograman lengkap

Jika Anda perlu **create docx ActiveX button** di Java, panduan ini akan memandu Anda melalui seluruh proses. Anda akan melihat cara menambahkan tombol formulir di Word, mengonfigurasi propertinya, dan menghasilkan file .docx yang siap pakai.

Bekerja dengan kontrol ActiveX adalah kebutuhan umum saat mengotomatisasi formulir Word lama. Dalam tutorial ini Anda akan belajar **add form button word** dokumen menggunakan pustaka Aspose.Words for Java, sehingga Anda dapat menyematkan kontrol interaktif tanpa harus mengedit secara manual.

## Apa yang Anda perlukan

Sebelum memulai, pastikan Anda memiliki:

* Java 17 atau lebih baru (kode dapat dikompilasi dengan versi sebelumnya, tetapi Java 17 disarankan).
* Aspose.Words for Java 23.10 atau yang lebih baru – unduh JAR dari situs Aspose atau tambahkan dependensi Maven.
* IDE (IntelliJ IDEA, Eclipse, atau VS Code) atau editor teks sederhana dan alat build baris perintah.
* Pengetahuan dasar tentang sintaks Java dan pemrograman berorientasi objek.

## Cara membuat tombol ActiveX docx dengan Aspose.Words

Langkah‑langkah berikut menunjukkan urutan tepat yang diperlukan untuk **create docx ActiveX button** objek dan menyematkannya dalam dokumen Word.

### Langkah 1: Siapkan proyek dan impor Aspose.Words

Tambahkan dependensi Aspose.Words ke `pom.xml` Anda jika menggunakan Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Atau, jika Anda lebih suka Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Setelah dependensi terpasang, impor kelas yang diperlukan dalam file sumber Java Anda:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Impor ini memberi Anda akses ke API `Document`, `DocumentBuilder`, dan `Forms2OleControl` yang digunakan untuk menyisipkan kontrol ActiveX.

### Langkah 2: Buat dokumen kosong baru

Instansiasikan objek `Document`, yang mewakili file Word kosong siap menerima konten.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Membuat dokumen terlebih dahulu memastikan bahwa builder berikutnya beroperasi pada kanvas yang bersih.

### Langkah 3: Inisialisasi DocumentBuilder

`DocumentBuilder` menyediakan antarmuka fluida untuk menyisipkan teks, gambar, dan kontrol. Kaitkan builder ini dengan dokumen yang baru saja Anda buat.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder melacak posisi kursor saat ini di dalam dokumen, sehingga penyisipan berikutnya terjadi tepat di tempat yang Anda inginkan.

### Langkah 4: Sisipkan kontrol ActiveX CommandButton

Gunakan metode `insertForms2OleControl` untuk menyematkan ActiveX `CommandButton`. Metode ini mengembalikan instance `Forms2OleControl` yang dapat Anda konfigurasi lebih lanjut.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Pada titik ini file .docx berisi placeholder untuk tombol, tetapi belum memiliki caption visual atau ukuran.

### Langkah 5: Konfigurasikan properti tombol

Atur nama kontrol, caption, dan atribut tata letak. Nilai‑nilai ini menentukan bagaimana tombol muncul di Word dan bagaimana Anda dapat merujuknya nanti melalui VBA atau skrip otomasi.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Tips pro:** Word mengukur posisi dalam poin (1 pt ≈ 1/72 in). Sesuaikan `setTop` dan `setLeft` untuk menyejajarkan tombol dengan konten di sekitarnya.

### Langkah 6: Simpan dokumen

Akhirnya, tulis dokumen ke disk. Gunakan ekstensi `.docx` untuk mempertahankan file dalam format Office Open XML modern.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Saat Anda membuka file hasil di Microsoft Word, Anda akan melihat tombol **Submit** yang ditempatkan pada koordinat yang Anda tentukan. Mengklik tombol di Word tidak akan memicu aksi apa pun kecuali Anda menambahkan kode VBA, tetapi kontrol tersebut berfungsi penuh untuk alur kerja berbasis formulir.

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Apakah saya memerlukan versi Word khusus?** | Kontrol ActiveX didukung di versi desktop Microsoft Word pada Windows. Mereka tidak tersedia di Word untuk Mac atau Word Online. |
| **Bisakah saya menggunakan ini dengan file `.doc`?** | Ya. Simpan dokumen dengan ekstensi `.doc` (`document.save("ActiveXButton.doc")`). API yang sama bekerja untuk format biner lama. |
| **Bagaimana jika tombol tidak muncul?** | Pastikan **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** mengizinkan kontrol ActiveX. Juga pastikan dokumen tidak dibuka dalam “Protected View”. |
| **Bisakah saya menambahkan kontrol ActiveX lain?** | Tentu saja. Ganti `Forms2OleControlType.COMMAND_BUTTON` dengan `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, dll. |
| **Apakah ada batas ukuran?** | Ukuran kontrol hanya dibatasi oleh tata letak halaman. Dimensi yang sangat besar dapat menyebabkan overflow tata letak. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah kelas Java lengkap yang dapat Anda salin, kompilasi, dan jalankan. Kelas ini mencakup semua impor, metode `main`, dan komentar inline untuk kejelasan.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Hasil yang diharapkan:** Setelah menjalankan program, `ActiveXButton.docx` muncul di direktori kerja. Membukanya di Microsoft Word menampilkan tombol **Submit** yang dapat diklik, terletak di dekat kiri‑atas halaman pertama.

## Kesimpulan

Anda kini tahu cara **create docx ActiveX button** objek di Java menggunakan Aspose.Words, dan telah melihat cara **add form button word** dokumen secara programatis. Langkah‑langkah—menyiapkan proyek, membuat dokumen, menyisipkan kontrol, mengonfigurasi propertinya, dan menyimpan—mencakup seluruh alur kerja dari awal hingga akhir.

Selanjutnya, Anda dapat menjelajahi:

* Menambahkan makro VBA yang merespons klik tombol.
* Menyematkan kontrol ActiveX lain seperti kotak centang atau list box.
* Mengotomatisasi pembuatan formulir multi‑halaman dengan beberapa elemen interaktif.

Silakan bereksperimen dengan ukuran, posisi, dan caption untuk menyesuaikan dengan kebutuhan desain formulir Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}