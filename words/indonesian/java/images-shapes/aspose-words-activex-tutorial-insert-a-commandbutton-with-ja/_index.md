---
category: general
date: 2026-08-07
description: Tutorial Aspose.Words ActiveX menunjukkan cara menambahkan kontrol CommandButton
  ke dokumen Word menggunakan Java. Pelajari kode lengkap, konfigurasi, dan langkah-langkah
  penyimpanan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: id
lastmod: 2026-08-07
og_description: Tutorial Aspose.Words ActiveX menjelaskan cara menyisipkan kontrol
  ActiveX CommandButton dalam dokumen Word menggunakan Java. Ikuti contoh lengkap
  untuk membuat, mengonfigurasi, dan menyimpan dokumen.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Tutorial Aspose.Words ActiveX – Panduan Langkah demi Langkah Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Tutorial Aspose.Words ActiveX – menyisipkan CommandButton dengan Java
url: /id/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial Aspose.Words ActiveX – menyisipkan CommandButton dengan Java

Jika Anda perlu menyematkan kontrol ActiveX dalam file Word, **tutorial Aspose.Words ActiveX** ini akan memandu Anda melalui seluruh proses. Anda akan melihat cara membuat dokumen kosong, menyisipkan CommandButton, mengatur propertinya, dan menyimpan hasilnya—semua dengan kode Java biasa.

Contoh ini menggunakan API Aspose.Words for Java, yang menghilangkan kebutuhan akan Microsoft Office di server build. Pada akhir panduan ini Anda dapat menghasilkan file .docx yang berisi kontrol CommandButton yang berfungsi penuh dan siap digunakan di lingkungan Windows.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

- Java Development Kit (JDK) 8 atau yang lebih baru terpasang.
- Maven atau alat build lain untuk mengelola dependensi.
- Lisensi Aspose.Words untuk Java (atau kunci evaluasi sementara) untuk menghindari watermark evaluasi.
- Pemahaman dasar tentang sintaks Java dan pemrograman berorientasi objek.

> **Tip profesional:** Tambahkan dependensi Maven Aspose.Words ke `pom.xml` Anda agar IDE dapat menyelesaikan kelas secara otomatis:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Langkah 1: Buat dokumen kosong baru dan `DocumentBuilder`

Kelas `Document` mewakili file Word dalam memori, sementara `DocumentBuilder` menyediakan API yang fluida untuk mengedit dokumen. Menginisialisasi kedua objek menyiapkan dokumen untuk modifikasi lebih lanjut.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Mengapa ini penting:**  
`DocumentBuilder` melacak posisi kursor saat ini, sehingga setiap operasi sisip berikutnya—seperti menambahkan kontrol—muncul tepat di tempat yang Anda inginkan.

## Langkah 2: Sisipkan kontrol ActiveX CommandButton

Aspose.Words mengekspos `Forms2OleControl` untuk objek ActiveX. Metode `insertForms2OleControl` memerlukan tipe kontrol, yang Anda tentukan melalui enumerasi `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Penjelasan:**  
Kontrol yang disisipkan adalah objek berbasis COM yang akan dirender Word sebagai tombol yang dapat diklik ketika dokumen dibuka di lingkungan Windows.

## Langkah 3: Konfigurasikan properti tombol

Setelah penyisipan, Anda dapat menyesuaikan nama, caption, ukuran, dan posisi tombol. Properti‑properti ini memengaruhi tampilan dan perilaku kontrol di dalam Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Mengapa pengaturan ini penting:**  

- **Name** – Memungkinkan makro VBA merujuk ke kontrol (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Menentukan label yang terlihat yang diklik pengguna.
- **Left / Top** – Mengontrol penempatan relatif terhadap margin halaman.
- **Width / Height** – Menjamin ukuran visual yang konsisten di berbagai resolusi layar.

## Langkah 4: Simpan dokumen

Memanggil `save` menulis representasi dalam memori ke file fisik. Anda dapat memilih format apa pun yang didukung (`.docx`, `.doc`, `.pdf`, dll.). Untuk tutorial ini kami tetap menggunakan format Word asli.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Hasil:**  
Membuka `ActiveXDemo.docx` di Microsoft Word menampilkan CommandButton berlabel **Submit** yang ditempatkan pada koordinat yang ditentukan. Mengklik tombol memicu perilaku default (tidak ada kode VBA yang terlampir secara default).

## Kode sumber lengkap

Menggabungkan semua bagian, program lengkap yang dapat dijalankan terlihat seperti ini:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Output yang diharapkan

- File bernama **ActiveXDemo.docx** yang terletak di folder `output`.
- Saat dibuka di Microsoft Word (Windows), dokumen menampilkan tombol **Submit** yang dapat diklik pada posisi yang ditentukan.
- Tombol dapat dipilih, dipindahkan, atau dihubungkan ke kode VBA melalui UI Word (Developer → Properties).

## Menangani variasi umum

| Skenario | Penyesuaian |
|----------|------------|
| **Simpan sebagai .doc** (format lama) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Tambahkan penangan acara** | Word tidak mengekspos acara ActiveX melalui Aspose.Words. Anda harus menambahkan kode VBA secara manual setelah dokumen dihasilkan. |
| **Beberapa kontrol** | Ulangi blok insert/configure dengan nilai `setName` dan `setCaption` yang berbeda. |
| **Jenis kontrol berbeda (mis., CheckBox)** | Gunakan `Forms2OleControlType.CHECKBOX` dalam pemanggilan `insertForms2OleControl`. |
| **Platform non‑Windows** | Kontrol ActiveX hanya dirender pada Word Windows. Untuk solusi lintas‑platform, pertimbangkan content controls (`StructuredDocumentTag`). |

## Praktik terbaik dan jebakan

- **Lisensi lebih awal** – Daftarkan lisensi Aspose.Words Anda sebelum membuat `Document` untuk menghindari prompt evaluasi.
- **Sistem koordinat** – Posisi diukur dalam poin (1 pt = 1/72 in). Konversi dari piksel atau sentimeter jika desain UI Anda menggunakan satuan tersebut.
- **Path file** – Gunakan path absolut atau API `Paths` Java untuk menghindari `FileNotFoundException` ketika direktori output tidak ada.
- **Keamanan thread** – `Document` dan `DocumentBuilder` tidak thread‑safe. Buat instance terpisah per thread jika Anda menghasilkan dokumen secara paralel.
- **Pengujian** – Verifikasi dokumen yang dihasilkan pada versi Word target (mis., Word 2016, Word 365) karena versi lama mungkin menampilkan kontrol ActiveX secara berbeda.

## Kesimpulan

Tutorial **Aspose.Words ActiveX** ini menunjukkan cara menambahkan kontrol CommandButton secara programatis ke dokumen Word menggunakan Java. Anda telah mempelajari cara:

1. Menginisialisasi `Document` dan `DocumentBuilder`.
2. Menyisipkan `Forms2OleControl` dengan tipe `COMMAND_BUTTON`.
3. Mengatur nama, caption, ukuran, dan posisi tombol.
4. Menyimpan dokumen sebagai file .docx yang berisi kontrol ActiveX.

Dari sini Anda dapat menjelajahi tipe kontrol tambahan, mengotomatisasi penyisipan makro VBA, atau menggabungkan kontrol ActiveX dengan fitur Aspose.Words lainnya seperti mail‑merge dan content controls. Bereksperimenlah dengan tata letak yang berbeda dan integrasikan dokumen yang dihasilkan ke dalam pipeline pelaporan berbasis Java yang lebih besar.

---


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menggunakan OLE Objects dan Kontrol ActiveX dalam Aspose.Words untuk Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder dalam Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Mengonversi Word ke RTF dengan Tutorial Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}