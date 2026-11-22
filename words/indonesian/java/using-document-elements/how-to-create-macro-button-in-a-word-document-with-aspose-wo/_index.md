---
category: general
date: 2026-11-22
description: Buat tombol makro dalam dokumen Word menggunakan Java. Pelajari cara
  menyisipkan tombol perintah, mengatur teks tombol, dan menautkan makro ke tombol
  untuk dokumen interaktif.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: id
lastmod: 2026-11-22
og_description: Buat tombol makro dalam dokumen Word menggunakan Java. Tutorial ini
  menunjukkan cara menyisipkan tombol perintah, mengatur teks tombol, dan menautkan
  makro ke tombol untuk interaktivitas penuh.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Buat tombol makro di dokumen Word dengan Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Cara membuat tombol makro dalam dokumen Word dengan Aspose.Words untuk Java
url: /id/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat tombol makro dalam dokumen Word dengan Aspose.Words untuk Java

Jika Anda perlu **membuat tombol makro** dalam file Word, panduan ini akan memandu Anda melalui langkah‑langkah yang tepat. Anda akan belajar cara **menyisipkan tombol perintah**, **mengatur teks tombol**, dan **menautkan makro ke tombol** sehingga dokumen menjadi sepenuhnya interaktif.

Pengembang sering menyematkan kontrol OLE untuk memicu makro VBA dari dalam dokumen. Tutorial ini mencakup alur kerja lengkap, mulai dari penyiapan proyek hingga contoh Java yang dapat dijalankan yang menambahkan **tombol interaktif** ke file .docx. Tidak diperlukan skrip eksternal—semua berjalan di dalam proses Java.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* JDK 17 atau yang lebih baru terpasang.
* Maven 3.8+ (atau Gradle) untuk manajemen dependensi.
* Aspose.Words for Java 23.9 atau yang lebih baru – perpustakaan ini menyediakan API `DocumentBuilder` dan kontrol OLE.
* Pengetahuan dasar tentang Java dan makro VBA.

Jika ada yang belum tersedia, instal terlebih dahulu; sisa tutorial mengasumsikan semua sudah siap.

## Cara membuat tombol makro dengan Aspose.Words untuk Java

Inti solusi terdiri dari empat tindakan:

1. **Menyisipkan kontrol OLE tombol perintah** ke dalam dokumen.
2. **Mengatur teks tombol** (caption) yang dilihat pengguna.
3. **Menautkan makro ke tombol** sehingga klik menjalankan prosedur VBA yang diinginkan.
4. **Menyimpan dokumen** dengan makro yang disematkan.

Setiap tindakan dijelaskan pada bagian masing‑masing di bawah ini.

### Langkah 1: Sisipkan tombol perintah ke dalam dokumen

`DocumentBuilder.insertForms2OleControl` membuat kontrol OLE dengan tipe yang ditentukan. Konstanta `Forms2OleControlType.COMMAND_BUTTON` memberi tahu Aspose.Words untuk menghasilkan tombol perintah yang dapat menampung makro.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Mengapa ini penting:** Kontrol OLE berfungsi sebagai wadah bagi makro. Tanpa menyisipkannya, tidak ada elemen visual yang dapat diklik oleh pengguna.

### Langkah 2: Atur teks tombol (caption)

Caption adalah label yang terlihat pada tombol. Gunakan `setCaption` untuk menentukan apa yang dilihat pengguna.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Mengapa ini penting:** Teks tombol yang jelas meningkatkan kegunaan. Metode `setCaption` memperbarui properti `Caption` pada kontrol OLE, yang dirender Word sebagai label tombol.

### Langkah 3: Tautkan makro ke tombol

Makro diidentifikasi dengan namanya, misalnya `MyMacro`. Metode `setOnClick` menyimpan nama ini pada penangan acara `OnClick` tombol.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Mengapa ini penting:** Menautkan makro menciptakan perilaku interaktif. Ketika pengguna mengklik tombol di Word, prosedur VBA yang terkait akan dijalankan.

### Langkah 4: Tambahkan tombol interaktif ke dokumen Word

Setelah mengonfigurasi kontrol OLE, Anda mungkin ingin memposisikannya, mengubah ukurannya, atau menambahkan teks di sekitarnya. `DocumentBuilder` terus beroperasi pada dokumen, sehingga Anda dapat menyisipkan paragraf sebelum atau sesudah tombol.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Mengapa ini penting:** Menyimpan sebagai `.docm` mempertahankan kode makro. Jika disimpan sebagai `.docx`, referensi makro akan hilang.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program Java lengkap, termasuk impor, penanganan pengecualian, dan komentar yang menjelaskan setiap langkah. Salin kode ke dalam proyek Maven dengan dependensi Aspose.Words dan jalankan.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Output yang diharapkan

Menjalankan program menghasilkan `MacroButtonDemo.docm`. Membuka file tersebut di Microsoft Word menampilkan:

* Sebuah paragraf yang berisi *“Press the button to execute the macro:”*.
* Sebuah tombol berlabel **Run Report** tepat di bawah paragraf.
* Saat Anda mengklik tombol, Word berusaha menjalankan makro `MyMacro`. (Anda harus menambahkan kode VBA sebenarnya ke dokumen secara manual atau melalui langkah otomatisasi lain.)

Jika makro tidak ada, Word menampilkan peringatan keamanan, yang merupakan perilaku standar untuk dokumen yang mendukung makro.

## Variasi umum dan kasus tepi

| Skenario | Cara menyesuaikan kode |
|----------|------------------------|
| **Caption tombol yang berbeda** | Ubah string yang diberikan ke `setCaption`. |
| **Beberapa tombol** | Panggil `insertForms2OleControl` berulang kali, masing‑masing dengan `setCaption` dan `setOnClick` sendiri. |
| **Nama makro khusus** | Ganti `"MyMacro"` dengan nama prosedur VBA yang valid, misalnya `"ExportToExcel"`. |
| **Keterbatasan ukuran tombol** | Sesuaikan nilai `setWidth` dan `setHeight`; Word menghormati poin yang Anda berikan. |
| **Menyematkan makro secara programatik** | Gunakan `Document.getBuiltInDocumentProperties().add("Macros", …)` atau langkah injeksi VBA terpisah; Aspose.Words tidak menulis kode VBA secara langsung. |

**Tips profesional:** Selalu uji `.docm` yang dihasilkan pada mesin dengan keamanan makro diatur ke *Enable all macros* untuk pengembangan. Pada produksi, tanda tangani makro dengan sertifikat tepercaya untuk menghindari prompt keamanan.

## Daftar periksa pemecahan masalah

* **Tombol tidak muncul** – Pastikan dokumen disimpan sebagai `.docm` dan dibuka di versi Word yang mendukung kontrol OLE.
* **Makro tidak berjalan** – Pastikan nama makro cocok persis, termasuk huruf besar/kecil, dan makro memang ada dalam proyek VBA dokumen.
* **Caption tombol terpotong** – Tingkatkan lebar tombol menggunakan `setWidth` untuk menampung teks yang lebih panjang.
* **Perubahan tata letak tak terduga** – Gunakan `builder.moveTo` untuk memposisikan kursor secara tepat sebelum menyisipkan kontrol.

## Kesimpulan

Anda kini tahu cara **membuat tombol makro** dalam dokumen Word menggunakan Java, **menyisipkan tombol perintah**, **mengatur teks tombol**, dan **menautkan makro ke tombol** untuk interaktivitas penuh. Contoh lengkap menunjukkan setiap panggilan API yang diperlukan, menjelaskan mengapa setiap langkah penting, dan memberikan panduan untuk variasi umum.

Selanjutnya, Anda dapat menjelajahi:

* **Menambahkan tombol interaktif** ke templat yang sudah ada alih‑alih dokumen baru.
* **Menyuntikkan kode VBA secara programatik** menggunakan Open XML SDK atau alat otomatisasi sekunder.
* **Menggabungkan beberapa kontrol OLE** (checkbox, list box) untuk membangun formulir yang kaya.

Cobalah berbagai caption, nama makro, dan ukuran tombol untuk menyesuaikan dengan kebutuhan spesifik Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara menyisipkan tombol perintah dalam dokumen Word menggunakan Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Cara mengatur posisi tombol dalam dokumen Word dengan Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Cara Menyisipkan Tombol ActiveX di Word – Mengatur Caption Tombol](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}