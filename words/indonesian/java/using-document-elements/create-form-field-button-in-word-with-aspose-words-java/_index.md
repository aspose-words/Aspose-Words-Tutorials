---
category: general
date: 2026-10-13
description: Buat tombol bidang formulir di Word menggunakan Aspose.Words untuk Java.
  Pelajari cara menyisipkan bidang formulir tombol perintah Word dan mengatur caption
  tombol perintah dalam beberapa langkah mudah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: id
lastmod: 2026-10-13
og_description: Buat tombol bidang formulir di Word dengan Aspose.Words untuk Java.
  Tutorial ini menunjukkan cara menyisipkan bidang tombol perintah Word dan mengatur
  caption tombol perintah dengan cepat.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Buat tombol bidang formulir di Word – Panduan Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Buat tombol bidang formulir di Word dengan Aspose.Words Java
url: /id/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat tombol bidang formulir di Word dengan Aspose.Words Java

Jika Anda perlu **create form field button** dalam dokumen Word, panduan ini akan membawa Anda melalui proses lengkap menggunakan Aspose.Words for Java. Baik Anda sedang membuat templat formulir isian atau menambahkan kontrol interaktif ke laporan, Anda akan belajar cara **insert command button word** form fields dan **set command button caption** dengan kode minimal.

Tutorial ini mencakup semuanya mulai dari penyiapan Maven hingga contoh yang dapat dijalankan sepenuhnya, sehingga Anda dapat menyalin‑tempel kode, menjalankannya, dan melihat file `.docx` yang berisi tombol dapat‑klik siap untuk penyesuaian lebih lanjut.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

- Java 17 (atau lebih baru) terpasang dan dikonfigurasi di mesin Anda.
- Maven 3.6+ untuk manajemen dependensi.
- IDE atau editor teks pilihan Anda (mis., IntelliJ IDEA, VS Code).
- Lisensi Aspose.Words for Java yang valid (versi percobaan gratis dapat digunakan untuk evaluasi).

## Langkah 1: Tambahkan Aspose.Words ke proyek Maven Anda

Buat file `pom.xml` (atau edit yang sudah ada) dan sertakan dependensi Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Pro tip:** Jaga nomor versi tetap terbaru. Rilis baru menambahkan dukungan untuk fitur Word terbaru dan meningkatkan kinerja.

## Langkah 2: Inisialisasi dokumen kosong dan `DocumentBuilder`

Kelas `DocumentBuilder` menyediakan API yang fluida untuk mengedit dokumen Word. Pada langkah ini kami membuat `Document` kosong dan melampirkan builder padanya.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Membuat dokumen adalah fondasi untuk **create form field button** objek nanti dalam tutorial.

## Langkah 3: Sisipkan bidang formulir tombol perintah

Aspose.Words mengekspos kelas `Forms2OleControl` untuk kontrol formulir OLE. Untuk **insert command button word** form fields, panggil `insertForms2OleControl` dengan nilai enum `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metode ini mengembalikan instance `Forms2OleControl` yang dapat kami konfigurasikan sebelum disimpan.

## Langkah 4: Tentukan ukuran dan posisi tombol

Tombol perintah memerlukan dimensi dan penempatan eksplisit pada halaman. Sesuaikan lebar, tinggi, dan koordinat agar cocok dengan tata letak Anda.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Penyetelan nilai‑nilai ini memastikan tombol muncul tepat di tempat yang Anda inginkan dalam dokumen akhir.

## Langkah 5: **Set command button caption**

Teks yang terlihat pada tombol dikendalikan oleh metode `setCaption`. Di sinilah kami **set command button caption** untuk memandu pengguna.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Anda dapat mengganti `"Click Me"` dengan label apa pun yang sesuai dengan tujuan formulir Anda, seperti `"Submit"` atau `"Approve"`.

## Langkah 6: Simpan dokumen

Akhirnya, tulis dokumen ke disk. File yang dihasilkan berisi tombol interaktif dan dapat dibuka di Microsoft Word atau LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Menjalankan program menghasilkan `CommandButtonDemo.docx`. Membukanya di Word menampilkan tombol berlabel **Click Me** yang ditempatkan 50 pts dari kiri dan 100 pts dari atas halaman.

### Output yang diharapkan

- File `.docx` bernama `CommandButtonDemo.docx`.
- Dokumen berisi satu halaman dengan bidang formulir tombol perintah.
- Tombol menampilkan caption yang Anda set (mis., **Click Me**).

## Variasi umum dan kasus tepi

| Situasi | Cara menyesuaikan |
|-----------|--------------|
| **Multiple buttons** | Panggil `insertForms2OleControl` berulang kali, sesuaikan `setLeft`/`setTop` untuk setiap tombol baru. |
| **Different caption per button** | Gunakan `setCaption` dengan string unik setelah setiap penyisipan. |
| **Button inside a table cell** | Pindahkan kursor ke sel yang diinginkan dengan `builder.moveTo(cell.getFirstParagraph())` sebelum menyisipkan kontrol. |
| **Legacy Word formats (.doc)** | Simpan menggunakan `doc.save("Demo.doc", SaveFormat.DOC);` – tombol perintah tetap dipertahankan. |
| **Read‑only forms** | Setelah penyisipan, set `commandButton.setEnabled(false);` untuk mencegah interaksi pengguna. |

## Tips untuk implementasi yang kuat

- **Validasi dimensi**: Lebar yang sangat besar dapat menyebabkan tombol melampaui margin halaman.
- **Penegakan lisensi**: Tanpa lisensi yang valid, Aspose.Words menambahkan watermark pada dokumen yang dihasilkan. Terapkan lisensi Anda lebih awal dengan `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Pengujian**: Buka file yang dihasilkan di Word dan aktifkan **Design Mode** (Developer → Design Mode) untuk melihat properti tombol.

## Rekap kode sumber lengkap

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Salin kode ke file bernama `InsertCommandButtonDemo.java`, kompilasi dengan Maven (`mvn compile`), dan jalankan (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Dokumen yang dihasilkan akan muncul di folder root proyek Anda.

## Kesimpulan

Anda kini tahu cara **create form field button** di Word menggunakan Aspose.Words for Java, cara **insert command button word** form fields, dan cara **set command button caption** secara programatis. Contoh end‑to‑end ini memberi Anda dasar yang kuat untuk membangun dokumen Word yang lebih kaya dan interaktif—baik Anda membutuhkan satu tombol kirim atau rangkaian lengkap kontrol formulir.

### Apa selanjutnya?

- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Menambahkan Form Field Combo Box ke Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Menambahkan Form Field Check Box ke Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}