---
category: general
date: 2026-09-24
description: Atur posisi tombol dalam dokumen Word menggunakan Java dan Aspose.Words.
  Pelajari cara menyisipkan tombol, menambahkan kontrol ActiveX, dan membuat dokumen
  Word dengan gaya Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: id
lastmod: 2026-09-24
og_description: Atur posisi tombol dalam dokumen Word menggunakan Java. Panduan ini
  menunjukkan cara menyisipkan tombol, menambahkan kontrol ActiveX, dan membuat dokumen
  Word dengan Java menggunakan Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Mengatur posisi tombol dalam dokumen Word dengan Java – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Cara mengatur posisi tombol dalam dokumen Word dengan Java
url: /id/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengatur posisi tombol dalam dokumen Word dengan Java

Jika Anda perlu **mengatur posisi tombol** di dalam file Word, panduan ini menunjukkan solusi lengkap yang dapat dijalankan. Baik Anda membuat templat yang memerlukan interaksi pengguna atau mengotomatisasi formulir, Anda akan belajar **cara menyisipkan tombol** menggunakan Aspose.Words for Java dan mengontrol penempatannya.

Tutorial ini mencakup semua yang Anda perlukan untuk **menambahkan kontrol ActiveX** ke dokumen Word, menjelaskan **cara menambahkan tombol ke Word**, dan mendemonstrasikan proses lengkap untuk **membuat dokumen Word Java**. Tidak diperlukan referensi eksternal—cukup salin, jalankan, dan verifikasi hasilnya.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Java 17 (atau runtime Java 8+ apa pun) terpasang.
* Maven atau Gradle untuk mengelola dependensi.
* Lisensi Aspose.Words for Java (versi trial gratis dapat digunakan untuk evaluasi).
* Pemahaman dasar tentang sintaks Java.

> **Pro tip:** Simpan JAR Aspose.Words Anda di folder `libs/` dan tambahkan ke classpath proyek Anda untuk menghindari konflik versi.

## Langkah 1: Siapkan proyek Maven

Buat proyek Maven sederhana (atau gunakan Gradle) dan tambahkan dependensi Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Menjalankan `mvn clean compile` akan mengunduh pustaka dan menyiapkan jalur build.

## Langkah 2: Buat dokumen Word baru

Operasi pertama adalah **membuat dokumen Word java**. Anda menginstansiasi objek `Document` dan `DocumentBuilder` yang memungkinkan Anda mengedit file.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Kelas `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` menyediakan API yang fluida untuk menyisipkan konten.

## Langkah 3: Cara menyisipkan tombol – menambahkan kontrol ActiveX

Aspose.Words menyediakan kelas `Forms2OleControl` untuk menyisipkan kontrol ActiveX warisan seperti CommandButton. Langkah ini menunjukkan cara **menyisipkan tombol** ke dalam dokumen secara tepat.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Metode `insertForms2OleControl` mengembalikan instance `Forms2OleControl` yang dapat Anda konfigurasi. Inilah inti dari proses **menambahkan kontrol ActiveX**.

## Langkah 4: Atur posisi tombol

Sekarang kita benar‑benar **mengatur posisi tombol**. Metode `setLeft` dan `setTop` pada kontrol menerima nilai dalam poin (1 pt = 1/72 in). Untuk menyelaraskan tombol dengan koordinat layar tipikal, Anda dapat mengonversi piksel ke poin (1 px ≈ 0.75 pt). Pada contoh ini kami menempatkan tombol 100 px dari tepi kiri dan 150 px dari tepi atas.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Karena logika **mengatur posisi tombol** terenkapsulasi di sini, Anda dapat menggunakan kembali baris‑baris ini kapan saja perlu memindahkan kontrol. Sesuaikan angka‑angka tersebut agar cocok dengan kebutuhan tata letak Anda.

## Langkah 5: Tentukan ukuran dan caption

Tombol tanpa label akan membingungkan. Gunakan `setWidth`, `setHeight`, dan `setCaption` untuk memberi tampilan yang terlihat.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Ukuran juga dinyatakan dalam poin, jadi kami mengonversi dari piksel untuk konsistensi.

## Langkah 6: Simpan dokumen – selesaikan alur **create Word document java**

Akhirnya, persistenkan file ke disk. Path dapat berupa absolut atau relatif terhadap root proyek.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Menjalankan program menghasilkan `CommandButtonDemo.docx` di dalam folder `output`. Membuka file tersebut di Microsoft Word menampilkan tombol yang dapat diklik tepat pada posisi yang Anda tentukan.

### Output yang diharapkan

* File `.docx` bernama **CommandButtonDemo.docx**.
* Di dalam dokumen, sebuah **CommandButton** dengan label “Click Me” muncul 100 px dari margin kiri dan 150 px dari margin atas.
* Tombol merespons klik ketika dokumen dibuka di Word (akan menampilkan pesan ActiveX default kecuali Anda menambahkan kode VBA khusus).

## Langkah 7: Variasi umum dan kasus tepi

### Menambahkan beberapa tombol

Jika Anda perlu **menambahkan tombol ke Word** lebih dari satu kali, ulangi langkah 3‑5 dengan instance `Forms2OleControl` baru setiap kali. Ingat untuk menyesuaikan nilai `setTop` agar tombol tidak saling tumpang tindih.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Bekerja tanpa lisensi

Aspose.Words menambahkan watermark ketika digunakan tanpa lisensi. Untuk kode produksi, beli lisensi dan terapkan di awal `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Kompatibilitas dengan versi Office lama

Kontrol ActiveX didukung dalam format `.doc` (Word 97‑2003). Untuk membuat file legacy, ubah format penyimpanan:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Kode sumber lengkap (dapat dijalankan)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Simpan file sebagai `src/main/java/CommandButtonDemo.java`, jalankan `mvn exec:java -Dexec.mainClass=CommandButtonDemo`, dan buka dokumen yang dihasilkan untuk melihat hasilnya.

## Pertanyaan yang sering diajukan

**T: Apakah ini bekerja dengan OpenJDK?**  
J: Ya. Aspose.Words adalah Java murni dan berjalan pada implementasi JDK 8+ apa pun, termasuk OpenJDK.

**T: Bisakah saya mengubah font atau warna tombol?**  
J: Penampilan tombol ActiveX dikendalikan oleh aplikasi host (Word). Anda dapat melampirkan kode VBA untuk mengubah properti saat runtime, tetapi penampilan statis terbatas pada gaya default.

**T: Bagaimana jika saya perlu menempatkan tombol di dalam sel tabel?**  
J: Pindahkan kursor `DocumentBuilder` ke dalam sel sebelum memanggil `insertForms2OleControl`. Kontrol akan mewarisi tata letak sel, dan Anda masih dapat menggunakan `setLeft`/`setTop` untuk penyetelan halus.

## Kesimpulan

Anda kini tahu cara **mengatur posisi tombol** dalam dokumen Word menggunakan Java, cara **menyisipkan tombol**, cara **menambahkan kontrol ActiveX**, dan cara **menambahkan tombol ke Word** sambil mengikuti praktik terbaik untuk proyek **create Word document java**. Contoh lengkap memperlihatkan seluruh alur kerja—dari penyiapan proyek hingga file `.docx` yang disimpan berisi CommandButton yang berfungsi.

### Langkah selanjutnya

* Jelajahi nilai `Forms2OleControl.ControlType` lainnya (mis., `CHECKBOX`, `TEXTBOX`) untuk membangun formulir yang lebih kaya.
* Gabungkan tombol dengan makro VBA untuk penanganan klik khusus.
* Manfaatkan fitur mail‑merge Aspose.Words untuk menghasilkan dokumen yang dipersonalisasi dan sudah berisi kontrol interaktif.

Selamat coding, dan nikmati mengotomatisasi dokumen Word dengan Java!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}