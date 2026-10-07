---
category: general
date: 2026-10-07
description: Buat tombol perintah ActiveX dalam Java dan tambahkan tombol perintah
  secara programatik ke dokumen Word. Pelajari cara mengatur posisi kiri‑atas tombol.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: id
lastmod: 2026-10-07
og_description: Buat tombol perintah ActiveX dalam Java untuk menyematkan kontrol
  interaktif di dokumen Word Anda. Pelajari cara menambahkan tombol perintah secara
  programatik, mengatur posisinya, dan menyesuaikan tampilannya.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Buat tombol perintah ActiveX di Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Cara membuat tombol perintah ActiveX di Java
url: /id/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat ActiveX command button di Java

Jika Anda perlu **membuat ActiveX command button** dalam dokumen Word menggunakan Java, panduan ini menunjukkan cara melakukannya secara tepat. Anda akan melihat contoh lengkap yang dapat dijalankan yang **menambahkan tombol perintah secara programatik**, menempatkannya dengan `setLeft` dan `setTop`, serta menyimpan hasilnya sebagai file `.docx`.

Menyematkan tombol interaktif memungkinkan Anda membangun formulir, mengotomatisasi alur kerja, atau mengumpulkan masukan pengguna langsung di dalam file Word. Langkah‑langkah di bawah mencakup semua hal mulai dari penyiapan proyek hingga verifikasi akhir, sehingga Anda dapat menyalin kode ke dalam proyek Anda sendiri tanpa melewatkan detail apa pun.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

- JDK 17 atau yang lebih baru terpasang  
- Maven 3.8+ (atau alat build pilihan Anda)  
- Aspose.Words for Java 23.9 atau yang lebih baru – perpustakaan yang menyediakan `DocumentBuilder` dan dukungan kontrol OLE  
- Pengetahuan dasar tentang sintaks Java dan konsep berorientasi objek  

Jika Anda menggunakan Maven, tambahkan dependensi ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Tip profesional:** Gunakan versi Aspose.Words terbaru untuk mendapatkan perbaikan bug dan fitur OLE baru.

## Langkah 1: Buat dokumen kosong baru dan DocumentBuilder

Langkah pertama untuk **membuat ActiveX command button** adalah menginstansiasi `Document` kosong dan `DocumentBuilder`. Builder memberikan API yang fluently untuk menyisipkan konten, termasuk kontrol OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` mewakili file Word di memori, sementara `DocumentBuilder` berfungsi sebagai kursor yang memungkinkan Anda menempatkan elemen secara tepat di lokasi yang diinginkan.

## Langkah 2: Sisipkan kontrol tombol perintah OLE

Kontrol ActiveX disisipkan sebagai objek OLE. Aspose.Words menyediakan kelas `Forms2OleControl` untuk tujuan ini.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Saat Anda memanggil `insertForms2OleControl()`, Aspose secara otomatis membuat bentuk placeholder yang akan menampung tombol ActiveX.

## Langkah 3: Konfigurasikan properti tombol

Sekarang Anda **menambahkan command button secara programatik** dengan detail seperti ProgID, caption, dan ukuran. ProgID yang paling umum untuk tombol perintah adalah `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Cara mengatur posisi kiri‑atas tombol

Menempatkan tombol adalah bagian di mana kata kunci sekunder **how to set button left top** menjadi relevan. Metode `setLeft` dan `setTop` menerima nilai yang diukur dalam poin (1 poin = 1/72 in).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Sesuaikan angka‑angka ini agar cocok dengan tata letak Anda. Misalnya, untuk meratakan tombol dengan sel tabel, hitung koordinat sel tersebut dan berikan ke `setLeft`/`setTop`.

## Langkah 4: Simpan dokumen

Akhirnya, tulis dokumen ke disk. File akan berisi tombol ActiveX yang siap berinteraksi ketika dibuka di Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Menjalankan metode `main` menghasilkan `CommandButton.docx`. Buka file tersebut di Word, aktifkan konten jika diminta, dan Anda akan melihat tombol yang dapat diklik dengan label **Click Me** yang ditempatkan pada koordinat yang Anda tentukan.

![Buat ActiveX command button di Java](/images/activex-button-screenshot.png){.center width=600 alt="Tangkapan layar pembuatan ActiveX command button di Java yang menunjukkan tombol di dalam dokumen Word"}

## Variasi umum dan kasus tepi

### Menambahkan beberapa tombol

Jika Anda memerlukan beberapa tombol, ulangi **Langkah 2** dan **Langkah 3** untuk setiap kontrol. Ingat untuk menyesuaikan `setLeft` dan `setTop` agar tombol tidak saling tumpang tindih.

### Mengubah perilaku tombol

Tombol ActiveX dapat menjalankan makro VBA saat diklik. Untuk melampirkan makro, set properti `setOnAction` dengan nama makro:

```java
commandButton.setOnAction("MyMacro");
```

Pastikan dokumen target berisi modul VBA yang sesuai; jika tidak, Word akan menampilkan error.

### Catatan kompatibilitas

- Tombol ini hanya berfungsi pada versi desktop Word yang mendukung ActiveX (misalnya, Word untuk Windows). Pada Word untuk Mac atau editor daring, tombol akan muncul sebagai gambar statis.  
- Jika Anda menargetkan lingkungan campuran, pertimbangkan menggunakan **content control** (`RichTextContentControl`) alih‑alih kontrol ActiveX.

## Kode sumber lengkap untuk referensi

Berikut adalah contoh lengkap yang berdiri sendiri yang dapat Anda salin ke proyek Maven baru dan jalankan segera.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Output yang diharapkan:** Setelah eksekusi, Anda akan menemukan `CommandButton.docx` di direktori kerja proyek Anda. Membuka file tersebut di Microsoft Word menampilkan tombol pada lokasi yang ditentukan dengan caption “Click Me”.

## Kesimpulan

Anda kini tahu cara **membuat ActiveX command button** di Java, **menambahkan command button secara programatik** ke dokumen Word, dan mengontrol tata letaknya secara tepat menggunakan metode **how to set button left top**. Teknik ini membuka peluang untuk formulir Word interaktif yang dapat memicu makro, meluncurkan aplikasi eksternal, atau mengumpulkan masukan pengguna langsung di dalam dokumen.

### Langkah selanjutnya

- Jelajahi kontrol ActiveX lain seperti `Forms.TextBox.1` atau `Forms.CheckBox.1`.  
- Gabungkan beberapa kontrol dengan modul VBA untuk mengimplementasikan formulir lengkap.  
- Ganti ActiveX dengan content control jika Anda memerlukan kompatibilitas lintas platform.  

Silakan bereksperimen dengan ukuran, caption, dan posisi agar sesuai dengan desain UI Anda. Jika Anda mengalami masalah, periksa kembali bahwa versi Aspose.Words yang Anda gunakan mendukung kontrol OLE, dan pastikan pengaturan keamanan Word mengizinkan eksekusi ActiveX. Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}