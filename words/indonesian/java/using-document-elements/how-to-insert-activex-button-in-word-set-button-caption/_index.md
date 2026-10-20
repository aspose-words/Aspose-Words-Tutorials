---
category: general
date: 2026-07-26
description: Cara menyisipkan tombol ActiveX dalam dokumen Word menggunakan Aspose.Words
  – pelajari cara mengatur caption tombol, posisi, dan ukuran hanya dalam beberapa
  baris.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: id
lastmod: 2026-07-26
og_description: Cara menyisipkan tombol ActiveX dalam dokumen Word dengan Aspose.Words.
  Ikuti tutorial langkah demi langkah ini untuk mengatur keterangan tombol, posisi,
  dan ukuran.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Cara Menyisipkan Tombol ActiveX di Word – Panduan Cepat
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Cara Menyisipkan Tombol ActiveX di Word – Atur Keterangan Tombol
url: /id/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyisipkan Tombol ActiveX di Word – Mengatur Caption Tombol

Pernah bertanya-tanya **bagaimana cara menyisipkan ActiveX** ke dalam file Word tanpa membuka UI? Anda bukan satu-satunya. Dalam banyak aplikasi perusahaan Anda memerlukan tombol yang dapat diklik yang menjalankan macro, dan melakukannya secara programatik menghemat jam kerja. Panduan ini menunjukkan secara tepat **bagaimana cara menyisipkan ActiveX** CommandButton menggunakan Aspose.Words for Java, dan—ya—bagaimana **mengatur caption tombol** sehingga pengguna tahu apa yang harus diklik.

Kami akan membahas seluruh proses: mulai dari menyiapkan pustaka, membuat dokumen baru, menambahkan tombol, menyesuaikan ukuran dan lokasinya, memberi caption yang ramah, dan akhirnya menyimpan file. Pada akhir tutorial Anda akan memiliki file `.docx` yang dapat dijalankan dan terbuka di Word dengan tombol ActiveX yang berfungsi penuh siap memicu macro Anda.

---

## Apa yang Akan Anda Pelajari

- Instal dan referensikan Aspose.Words dalam proyek Java.  
- Buat `Document` dan `DocumentBuilder` baru.  
- **Sisipkan ActiveX** kontrol CommandButton dengan satu baris kode.  
- **Atur caption tombol**, sesuaikan posisinya, dan tentukan dimensinya.  
- Simpan dokumen dan buka di Word untuk melihat hasil.

Tidak diperlukan pengalaman sebelumnya dengan ActiveX; cukup pengetahuan dasar Java dan salinan Aspose.Words.

## Prasyarat

- Java 8 atau yang lebih baru terpasang di mesin Anda.  
- Maven atau Gradle untuk manajemen dependensi (kami akan menunjukkan contoh Maven).  
- Salinan berlisensi atau evaluasi **Aspose.Words for Java** (versi percobaan gratis cukup untuk demo ini).  
- Microsoft Word (versi terbaru apa pun) untuk menguji file yang dihasilkan.

## Langkah 1: Siapkan Aspose.Words di Proyek Anda

Langkah pertama—tambahkan dependensi Aspose.Words. Jika Anda menggunakan Maven, letakkan ini ke dalam `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Pengguna Gradle dapat menambahkan:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Setelah menjalankan `mvn clean install` (atau `gradle build`) pustaka akan berada di classpath Anda dan Anda siap menulis kode.

## Langkah 2: Buat Dokumen Baru dan Builder

`Document` mewakili seluruh file Word, sementara `DocumentBuilder` memungkinkan Anda mengeditnya. Anggap builder sebagai pena yang menggambar di kanvas baru.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Mengapa memulai dengan dokumen kosong? Ini menjamin Anda memiliki kontrol penuh atas setiap elemen yang ditambahkan, dan tidak ada pemformatan tersembunyi yang akan mengejutkan Anda kemudian.

## Langkah 3: Sisipkan Kontrol ActiveX CommandButton

Sekarang untuk bintang utama. Aspose.Words menyediakan `insertForms2OleControl` yang dapat menempatkan kontrol ActiveX apa pun yang Anda tentukan. Di sini kami meminta sebuah **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metode ini mengembalikan objek `Forms2OleControl`, memberi Anda akses programatik ke properti tombol. Di sinilah **cara menyisipkan activex** menjadi satu baris kode—tanpa harus berurusan dengan API COM tingkat rendah.

## Langkah 4: Posisi, Ukuran, dan Atur Caption Tombol

Tombol yang mengambang di tengah halaman tidak terlalu berguna. Anda ingin menempatkannya di tempat yang diharapkan pengguna, memberi ukuran yang wajar, dan—yang paling penting—**atur caption tombol** sehingga mereka tahu apa yang terjadi saat mengklik.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Mengapa angka-angka ini?** Word menggunakan poin (1 pt ≈ 1/72 inci). `100 pt` ≈ 1,4 inci dari kiri, `150 pt` ≈ 2,1 inci dari atas—sekitar tengah halaman A4 standar. Sesuaikan sesuai tata letak Anda.

Mengatur caption sangat penting; tanpa itu tombol terlihat seperti persegi kosong. Metode `setCaption` menerima string apa pun, sehingga Anda dapat melokalisasinya nanti jika diperlukan.

## Langkah 5: Simpan Dokumen

Akhirnya, tulis dokumen ke disk. Anda dapat memilih folder mana saja; pastikan jalur tersebut ada.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Saat Anda membuka `ActiveXButton.docx` di Word, Anda akan melihat tombol yang ditempatkan dengan baik berlabel **“Click Me.”** Jika Anda mengklik ganda, Word akan meminta Anda mengaktifkan macro (karena kontrol ActiveX dianggap macro‑enabled). Dari sana Anda dapat mengaitkan rutin VBA ke event `Click` tombol.

## Kasus Khusus & Tips yang Mungkin Terlewat

- **Format Macro‑Enabled**: Word menonaktifkan kontrol ActiveX dalam file `.docx` biasa kecuali pengguna mengaktifkan macro. Jika Anda membutuhkan tombol berfungsi langsung, pertimbangkan menyimpan sebagai `.docm` (macro‑enabled) dengan menggunakan `doc.save(outputPath, SaveFormat.DOCM);`.
- **Kompatibilitas**: Versi Word lama (sebelum‑2007) menggunakan format biner `.doc`. Aspose.Words dapat menyimpan ke format tersebut, tetapi properti kontrol mungkin terlihat sedikit berbeda.
- **Pengaturan Keamanan**: Beberapa lingkungan korporat mengunci ActiveX. Jika tombol Anda tidak muncul, periksa Trust Center Word → Pengaturan ActiveX.
- **Beberapa Tombol**: Ingin lebih dari satu? Cukup ulangi pemanggilan `insertForms2OleControl` dan sesuaikan nilai `Left`/`Top` masing‑masing tombol. Simpan referensi objek yang dikembalikan agar Anda dapat mengatur caption masing‑masing.
- **Menata Caption**: Caption mewarisi font default. Untuk mengubahnya, Anda harus mengedit XML dasar atau menerapkan style Word setelah penyisipan—di luar cakupan panduan singkat ini, tetapi dapat dilakukan dengan API `ParagraphFormat` Aspose.Words.

## Contoh Lengkap yang Berfungsi

Berikut adalah kelas Java lengkap yang siap dijalankan. Salin‑tempel ke IDE Anda, sesuaikan jalur output, dan tekan **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Output yang diharapkan**: Setelah dijalankan, konsol mencetak lokasi penyimpanan. Membuka file yang dihasilkan di Word menampilkan tombol yang ditempatkan kira‑kira di tengah halaman, berlabel “Click Me”. Mengkliknya akan memicu event klik ActiveX standar (Anda perlu melampirkan macro VBA untuk menanggapi).

## Kesimpulan

Anda kini tahu **cara menyisipkan ActiveX** kontrol CommandButton ke dalam dokumen Word secara programatik dengan Aspose.Words, dan Anda telah melihat secara tepat bagaimana **mengatur caption tombol**, posisi, dan ukuran kontrol. Pendekatan ini menghilangkan pekerjaan UI manual, terintegrasi bersih ke dalam generator laporan otomatis, dan memberi Anda kontrol penuh atas

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menyisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Menyisipkan Gambar Inline dalam Dokumen Word menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Menyisipkan Gambar ke Header Dokumen Word | Aspose.Words untuk .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}