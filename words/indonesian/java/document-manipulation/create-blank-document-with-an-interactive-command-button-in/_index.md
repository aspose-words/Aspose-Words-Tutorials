---
category: general
date: 2026-09-18
description: Buat dokumen kosong di Java dan tambahkan tombol ActiveX. Pelajari cara
  menyisipkan tombol perintah, membuat formulir interaktif, dan menyimpan dokumen
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: id
lastmod: 2026-09-18
og_description: Buat dokumen kosong di Java dan sematkan tombol perintah ActiveX.
  Ikuti panduan langkah demi langkah ini untuk membuat formulir interaktif dan menyimpan
  file Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Buat dokumen kosong dengan tombol perintah interaktif di Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Buat dokumen kosong dengan tombol perintah interaktif di Word menggunakan Java
url: /id/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen kosong dengan tombol perintah interaktif di Word menggunakan Java

Jika Anda perlu **membuat dokumen kosong** yang berisi tombol yang dapat diklik, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words for Java. Anda akan belajar membuat formulir interaktif, menambahkan tombol ActiveX, dan akhirnya menyimpan file Word—semua dalam beberapa langkah singkat.

Menyematkan tombol perintah mengubah .docx statis menjadi formulir fungsional yang dapat berinteraksi langsung oleh pengguna akhir di dalam Microsoft Word. Tutorial ini juga mencakup **how to insert command button**, penanganan jebakan umum, dan memperluas solusi untuk formulir yang lebih kompleks.

## Prasyarat

* Java 17 atau lebih baru (kode dikompilasi dengan JDK 17+)
* Aspose.Words for Java 23.9 atau lebih baru – perpustakaan menyediakan `Document`, `DocumentBuilder`, dan `Forms2OleControl`.
* IDE atau alat build (Maven/Gradle) yang dapat menambahkan dependensi Aspose.Words.
* Pengetahuan dasar tentang sintaks Java dan konsep dokumen Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Langkah 1: Buat dokumen kosong

Operasi pertama adalah menginstansiasi objek `Document` baru. Objek ini mewakili file Word kosong yang siap diisi konten.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Membuat dokumen kosong memberi Anda kanvas bersih, yang penting ketika Anda ingin **create word document** secara programatis tanpa templat yang sudah ada.

## Langkah 2: Inisialisasi DocumentBuilder

`DocumentBuilder` adalah kelas utama untuk menambahkan teks, tabel, dan kontrol formulir. Ia bekerja pada `Document` yang baru saja Anda buat.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder mempertahankan titik sisipan saat ini, sehingga perintah berikutnya memengaruhi lokasi yang tepat dalam file.

## Langkah 3: Sisipkan kontrol tombol perintah Forms2Ole

Aspose.Words menyediakan kelas `Forms2OleControl` untuk kontrol ActiveX. Untuk **add activex button**, Anda meminta tipe `COMMANDBUTTON` dari builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Metode `insertForms2OleControl` menyisipkan kontrol pada lokasi kursor builder saat ini. Karena kontrol tersebut adalah objek ActiveX, ia hanya berfungsi di versi desktop Microsoft Word, bukan di Word Online.

## Langkah 4: Konfigurasikan tampilan dan posisi tombol

Anda dapat mengatur caption, ukuran, dan lokasi tombol menggunakan setter pada kontrol. Nilai posisi diukur dalam poin (1 poin = 1/72 inci).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Mengapa mengonfigurasi properti ini?* Mengatur `Top` dan `Left` memastikan tombol muncul di tempat yang Anda harapkan pada halaman, sementara `Caption` menentukan label yang terlihat oleh pengguna. Jika Anda melewatkan lebar/tinggi, Word akan menetapkan dimensi default, yang mungkin tidak cocok dengan desain Anda.

### Tips Pro
Jika Anda berencana menambahkan beberapa kontrol, panggil `builder.moveToDocumentEnd()` sebelum setiap penyisipan untuk menghindari objek yang saling tumpang tindih.

## Langkah 5: Simpan dokumen dengan tombol perintah yang disematkan

Akhirnya, tulis dokumen ke disk. Ekstensi file harus `.docx` (atau `.doc` untuk versi Word yang lebih lama) untuk mempertahankan kontrol ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Saat Anda membuka `CommandButton.docx` di Microsoft Word, Anda akan melihat tombol berlabel **Click Me**. Mengkliknya akan memicu aksi ActiveX default (yang secara default tidak melakukan apa‑apa). Anda dapat kemudian melampirkan makro atau skrip VBA untuk mendefinisikan perilaku khusus.

## Cara menyisipkan tombol perintah ke dalam formulir yang ada (opsional)

Jika Anda sudah memiliki formulir dengan bidang teks dan ingin **create interactive form** yang mencakup tombol, ikuti langkah tambahan berikut:

1. Load the existing document: `Document doc = new Document("ExistingForm.docx");`
2. Move the builder to the desired location: `builder.moveToParagraph(5, 0); // 6th paragraph, first node`
3. Insert the button as shown in Step 3.
4. Adjust the button’s `Top`/`Left` based on the paragraph’s layout.

Pendekatan ini memungkinkan Anda memperkaya templat Word yang sudah ada dengan tombol ActiveX tanpa harus membuat ulang seluruh file.

## Kasus tepi dan pemecahan masalah

| Situasi | Apa yang harus diperiksa | Perbaikan yang disarankan |
|-----------|---------------|-----------------|
| Tombol tidak muncul di Word | Pastikan Anda membuka file di versi desktop Word (Word Online menghapus ActiveX). | Buka file di Word 2016+ desktop. |
| Caption terpotong | Verifikasi bahwa lebar tombol cukup besar untuk menampung teks. | Tingkatkan `setWidth` hingga caption muat. |
| Simpan melempar `IOException` | Pastikan direktori output ada dan Anda memiliki izin menulis. | Buat direktori atau jalankan program dengan hak istimewa. |
| Beberapa tombol tumpang tindih | Kursor builder mungkin belum bergerak setelah penyisipan sebelumnya. | Panggil `builder.moveToDocumentEnd()` sebelum menyisipkan setiap kontrol baru. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program Java lengkap yang berdiri sendiri yang dapat Anda salin, kompilasi, dan jalankan. Program ini mendemonstrasikan **create blank document**, **add activex button**, dan **save word document** dalam satu alur.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Output yang diharapkan**

```
Document created: CommandButton.docx
```

Membuka `CommandButton.docx` menampilkan satu halaman dengan tombol berlabel **Click Me** yang ditempatkan 100 pt dari tepi atas dan kiri.

## Kesimpulan

Anda kini tahu cara **create blank document**, menyematkan **ActiveX button**, dan mengubah file Word biasa menjadi **interactive form**. Dengan menguasai **how to insert command button**, Anda dapat memperluas pola ini untuk menambahkan kotak centang, kotak kombo, atau bahkan logika khusus yang digerakkan VBA.

Selanjutnya, pertimbangkan untuk menjelajahi topik terkait berikut:

* **Create interactive form** dengan bidang teks (`builder.insertField`)  
* **Add activex button** yang menjalankan makro VBA (`builder.insertOleObject`)  
* **Create word document** dari templat menggunakan `Document(docTemplatePath)`  
* Mengonversi .docx yang dihasilkan ke PDF sambil mempertahankan tombol (catatan: PDF akan menampilkan tombol sebagai gambar statis).

Silakan bereksperimen dengan ukuran tombol, posisi, dan caption untuk menyesuaikan desain UI Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Buat Proyek VBA di Dokumen Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Buat Dokumen Word Baru](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}