---
category: general
date: 2026-08-23
description: Pelajari cara menyisipkan tombol perintah dalam dokumen Word menggunakan
  Java dan Aspose.Words. Panduan ini menunjukkan cara menambahkan kontrol formulir,
  mengatur nama tombol, dan menyematkan tombol ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: id
lastmod: 2026-08-23
og_description: Sisipkan tombol perintah dalam dokumen Word menggunakan Java. Ikuti
  panduan ini untuk menambahkan kontrol formulir, mengatur nama tombol, dan menyematkan
  tombol ActiveX dengan Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Menyisipkan tombol perintah di Word dengan Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Cara menyisipkan tombol perintah dalam dokumen Word menggunakan Java
url: /id/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan tombol perintah dalam dokumen Word menggunakan Java

Jika Anda perlu **menyisipkan tombol perintah** ke dalam file Word, tutorial ini menunjukkan solusi lengkap dengan Aspose.Words untuk Java. Anda akan melihat cara menambahkan kontrol formulir, mengonfigurasi caption‑nya, dan menetapkan nama tombol tanpa meninggalkan IDE Anda.

Panduan ini mencakup semua yang Anda perlukan untuk membuat file `.docx` yang berisi tombol ActiveX siap pakai di Microsoft Word. Tidak diperlukan alat tambahan, dan contoh ini berjalan pada Java 8+.

## Apa yang akan Anda pelajari

* Cara menambahkan kontrol formulir tipe **CommandButton** ke dokumen Word.  
* Langkah‑langkah tepat untuk **menetapkan nama tombol** dan **menambahkan properti tombol activex**.  
* Cara menyimpan dokumen sehingga tombol muncul dengan benar saat dibuka di Word.  

Anda sebaiknya memiliki lingkungan pengembangan Java dasar serta proyek Maven atau Gradle yang dapat mengimpor pustaka Aspose.Words.

## Prasyarat

| Persyaratan | Alasan |
|-------------|--------|
| Java 8 atau lebih baru | Aspose.Words untuk Java berjalan pada Java 8+. |
| Alat build Maven atau Gradle | Mempermudah penambahan dependensi Aspose.Words. |
| Lisensi Aspose.Words untuk Java (atau percobaan gratis) | Diperlukan untuk set fitur lengkap; API berfungsi dalam mode evaluasi. |
| IDE seperti IntelliJ IDEA atau Eclipse | Memudahkan pengeditan dan menjalankan contoh. |

## Langkah 1: Tambahkan Aspose.Words ke proyek Anda

Jika Anda menggunakan Maven, tambahkan dependensi berikut ke `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Untuk Gradle, letakkan baris ini di `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Setelah dependensi ter‑resolve, Anda dapat mengimpor kelas pustaka di file sumber Java Anda.

## Langkah 2: Sisipkan tombol perintah – kode inti

Buat kelas Java baru bernama `InsertCommandButtonDemo`. Kode di bawah ini melakukan keempat aksi yang diperlukan untuk **menyisipkan tombol perintah**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Mengapa setiap baris penting

* **Document & DocumentBuilder** – Menyediakan representasi memori dari file Word dan API untuk memodifikasi isinya.  
* **insertForms2OleControl** – Metode ini **menambahkan kontrol formulir** tipe `COMMAND_BUTTON`. Objek `Forms2OleControl` yang dikembalikan mewakili kontrol ActiveX.  
* **setName** – Menetapkan pengidentifikasi programatik (`btnSubmit`). Makro Word atau VBA dapat merujuk nama ini nanti.  
* **setCaption** – Menentukan teks yang dilihat pengguna pada tombol, menjawab pertanyaan “bagaimana menambahkan tombol”.  
* **save** – Menulis file `.docx` ke disk, mempertahankan tombol ActiveX yang disematkan.

Menjalankan program akan membuat `CommandButtonDemo.docx` di direktori kerja. Membuka file tersebut di Microsoft Word menampilkan tombol berlabel **Submit** yang dapat Anda klik (akan menampilkan dialog ActiveX default dalam mode evaluasi).

## Langkah 3: Verifikasi tombol yang disisipkan di Word

1. Buka `CommandButtonDemo.docx` dengan Microsoft Word (2016 atau lebih baru).  
2. Tombol **Submit** muncul di tempat kursor berada saat penyisipan.  
3. Klik kanan tombol dan pilih **Properties** untuk melihat bahwa bidang **Name** berisi `btnSubmit`.  

Jika tombol tidak muncul, pastikan **ActiveX controls** diaktifkan pada pengaturan Trust Center Word.

## Langkah 4: Menyesuaikan tombol (opsional)

Anda dapat menyesuaikan tombol lebih lanjut dengan mengubah ukuran, posisi, atau menambahkan makro VBA. Kelas `Forms2OleControl` menyediakan properti tambahan seperti `setWidth`, `setHeight`, dan `setLeft`. Berikut contoh yang membuat tombol menjadi lebih besar:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Baris‑baris ini dapat ditempatkan setelah pemanggilan `setCaption`. Mereka menunjukkan **penyesuaian add activex button** di luar penyisipan dasar.

## Kesulitan umum dan cara mengatasinya

| Gejala | Penyebab | Solusi |
|--------|----------|--------|
| Tombol tidak muncul di Word | Dokumen disimpan sebelum kontrol ditambahkan | Pastikan `insertForms2OleControl` dipanggil sebelum `doc.save`. |
| Caption tombol kosong | `setCaption` tidak dipanggil atau dipanggil dengan string kosong | Berikan string yang tidak kosong, misalnya `"Submit"`. |
| VBA tidak dapat menemukan tombol | Nama tidak cocok antara kode VBA dan nilai `setName` | Jaga konsistensi nama; gunakan `setName("btnSubmit")` dan referensikan `btnSubmit` di VBA. |
| Peringatan keamanan saat membuka file | Keamanan macro Word memblokir kontrol ActiveX | Sesuaikan Trust Center > Macro Settings, atau tandatangani dokumen dengan sertifikat tepercaya. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah file sumber lengkap, siap untuk disalin‑tempel ke IDE Anda. Termasuk pernyataan impor, penanganan pengecualian, dan blok komentar yang menjelaskan setiap langkah utama.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Hasil yang diharapkan:** Setelah menjalankan program, `CommandButtonDemo.docx` berisi satu tombol **Submit**. Membuka file di Word menampilkan tombol tepat di lokasi kursor `DocumentBuilder`.

## Langkah selanjutnya

* **Tambahkan lebih banyak kontrol formulir** – Gunakan `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, atau `TEXT_BOX` untuk membangun formulir Word lengkap.  
* **Gabungkan dengan mail merge** – Sisipkan tombol ke dalam dokumen hasil mail‑merge untuk membuat formulir interaktif yang dipersonalisasi.  
* **Lampirkan makro VBA** – Sematkan VBA secara programatik yang merespons peristiwa `Click` tombol untuk otomatisasi tingkat lanjut.  

Topik‑topik ini secara alami memperluas teknik **add form control** yang baru saja Anda kuasai.

---

### Ringkasan

Anda kini tahu cara **menyisipkan tombol perintah** ke dalam dokumen Word menggunakan Java, cara **menambahkan kontrol formulir**, cara **menetapkan nama tombol**, dan cara **menambahkan kustomisasi activex button**. Contoh lengkap dapat dijalankan langsung, dan Anda dapat menyesuaikannya untuk alur kerja generasi dokumen apa pun. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Combo Box Form Field in Word Document](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}