---
category: general
date: 2026-07-29
description: 'tutorial mengatur ukuran tombol java: pelajari cara menyisipkan tombol
  perintah ActiveX dalam dokumen Word menggunakan Java dan Aspose.Words, serta pengaturan
  ukuran dan pembuatan dokumen kosong.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: id
lastmod: 2026-07-29
og_description: Panduan mengatur ukuran tombol Java menunjukkan cara menyisipkan tombol
  perintah ActiveX dalam file Word menggunakan Java, menyesuaikan ukurannya, dan menyimpan
  dokumen secara programatis.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: atur ukuran tombol java – Tambahkan Tombol Perintah ActiveX ke Word dengan
  Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Atur ukuran tombol java – Sisipkan Tombol Perintah ActiveX di Word
url: /id/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Sisipkan Tombol Perintah ActiveX di Word

Pernah bertanya-tanya **how to set button size java** saat Anda mengotomatisasi dokumen Word? Mungkin Anda sedang membangun alat pelaporan yang memerlukan tombol “Submit” yang dapat diklik langsung di dalam file .docx. Dalam tutorial ini kami akan membahas seluruh proses—membuat dokumen Word kosong, menyisipkan tombol perintah ActiveX, dan secara eksplisit mengatur lebar serta tinggi—semuanya dengan Java dan Aspose.Words.

Kami juga akan menjawab pertanyaan “how to insert activex” yang sering muncul di kalangan pengembang. Pada akhir tutorial Anda akan memiliki program yang dapat dijalankan dan menghasilkan file Word berisi tombol perintah berukuran tepat, siap untuk kustomisasi lebih lanjut.

---

## Apa yang Anda Butuhkan

Sebelum kita mulai, pastikan Anda memiliki hal‑hal berikut:

- **Java Development Kit (JDK) 8 atau yang lebih baru** – kode dapat dikompilasi dengan JDK terbaru apa pun.  
- **Aspose.Words for Java** (versi terbaru per Juli 2026). Unduh JAR dari [Aspose website](https://products.aspose.com/words/java) atau melalui Maven:  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- IDE atau editor teks sederhana—IntelliJ IDEA, Eclipse, atau VS Code sudah cukup.  
- Folder tempat Anda ingin menyimpan **CommandButton.docx** yang dihasilkan.

Itu saja. Tidak ada pustaka interop Office tambahan, tidak ada trik COM, hanya Java murni.

---

## Implementasi Langkah‑per‑Langkah

Kami akan membagi solusi menjadi lima langkah logis. Setiap langkah memiliki header H2 tersendiri; salah satunya berisi **kata kunci utama** untuk keperluan SEO.

### 1. Siapkan Proyek dan Impor Aspose.Words

Pertama, buat proyek Maven (atau Gradle) baru dan tambahkan dependensi Aspose.Words seperti yang ditunjukkan di atas. Kemudian, impor kelas‑kelas yang diperlukan dalam file sumber Java Anda:

```java
import com.aspose.words.*;
```

> **Pro tip:** Jika Anda menggunakan IDE, biarkan IDE meng‑auto‑import kelas‑kelas tersebut. Ini menghemat banyak pengetikan dan mencegah typo.

### 2. java create blank word Document

Sekarang kita benar‑benar **java create blank word** dokumen. Ini adalah fondasi yang nantinya akan kita gunakan untuk **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

Objek `Document` mewakili seluruh file Word dalam memori. Pada titik ini file belum memiliki halaman, belum ada teks—hanya kanvas kosong.

### 3. Inisialisasi DocumentBuilder dan Sisipkan Kontrol ActiveX

`DocumentBuilder` adalah pembantu yang memungkinkan kita menambahkan konten, paragraf, tabel, dan, ya, kontrol ActiveX. Di sinilah kami menjawab **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` adalah pembungkus Aspose untuk objek OLE. Dengan menentukan `COMMANDBUTTON` kita memberi tahu Word untuk menyematkan tombol perintah ActiveX klasik.

### 4. How to Set Button Size Java – Sesuaikan Lebar dan Tinggi

Berikutnya adalah inti tutorial: **how to set button size java**. Kontrol ini menyediakan beberapa properti tata letak—`Left`, `Top`, `Width`, dan `Height`. Mengatur nilai‑nilai tersebut secara langsung mengendalikan tampilan tombol pada halaman.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Mengapa angka‑angka ini? Di Word, satu poin sama dengan 1/72 inci. Jadi lebar `120` poin kira‑kira setara 1,67 inci—cukup besar untuk label yang terbaca, namun tidak berlebihan. Sesuaikan nilai‑nilai tersebut agar cocok dengan tata letak Anda; properti yang sama juga menjawab pertanyaan **how to set button** yang mungkin Anda miliki.

> **Catatan:** Jika Anda memerlukan tipe tombol lain (misalnya kotak centang), ganti `Forms2OleControlType.COMMANDBUTTON` dengan nilai enum yang sesuai.

### 5. Simpan Dokumen

Akhirnya, persistenkan dokumen ke disk:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Ganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif di mesin Anda. Setelah menjalankan program, buka file yang dihasilkan di Microsoft Word. Anda akan melihat tombol berlabel “Click Me” yang ditempatkan 100 pts dari kiri dan 200 pts dari atas, berukuran persis seperti yang kami atur.

---

## Contoh Lengkap yang Siap Dijalan

Berikut adalah kelas Java lengkap yang siap dijalankan. Salin‑tempel ke dalam `CommandButtonActiveX.java`, sesuaikan jalur output, lalu tekan **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Output yang diharapkan:** Membuka `CommandButton.docx` di Word menampilkan satu halaman dengan tombol “Click Me” yang dapat diklik, ditempatkan kira‑kira di tengah halaman. Dimensi tombol sesuai dengan nilai yang Anda tetapkan, membuktikan bahwa **set button size java** berfungsi sebagaimana mestinya.

---

## Pertanyaan Umum & Kasus Khas

### Apa yang harus dilakukan jika tombol tidak muncul di Word?

- **Periksa versi Word.** Kontrol ActiveX memerlukan versi desktop Word; Word Online akan menghapusnya.  
- **Pastikan lisensi Aspose.Words sudah diterapkan** (jika Anda menggunakan edisi berbayar). Versi evaluasi tanpa lisensi mungkin menambahkan watermark tetapi tetap menampilkan kontrol.

### Bisakah saya mengubah font atau warna tombol?

Ya. Setelah menyisipkan kontrol, Anda dapat mengakses objek OLE di bawahnya dan memanipulasi properti VBA. Ini topik yang lebih lanjutan—coba `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` untuk memberi caption berwarna merah, misalnya.

### Bagaimana cara menangani event klik tombol?

Tombol perintah ActiveX memicu event VBA `Click`. Agar tombol berfungsi, Anda perlu menyematkan makro dalam dokumen yang sama. Aspose.Words dapat menambahkan modul makro melalui API `Document.getMacros()`, tetapi kode makro itu sendiri harus ditulis dalam VBA.

### Bagaimana dengan tipe tombol lain?

Aspose.Words mendukung banyak nilai `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, dll. Ganti konstanta enum pada pemanggilan `insertForms2OleControl` untuk bereksperimen.

---

## Tips Pro untuk Kode Siap Produksi

1. **Gunakan konstanta untuk nilai tata letak** – memudahkan penyesuaian di masa mendatang.  
2. **Bungkus jalur penyimpanan dalam objek `Path`** untuk menghindari pemisah yang spesifik platform.  
3. **Dispose objek Document** (atau gunakan try‑with‑resources) bila Anda memproses banyak file dalam loop.  
4. **Validasi folder output** sebelum memanggil `save` untuk menghindari `FileNotFoundException`.

---

## Kesimpulan

Anda kini telah mempelajari **set button size java** dengan membuat file Word kosong, menyisipkan tombol perintah ActiveX, dan mengonfigurasi dimensinya secara tepat—semua dengan beberapa baris kode Java. Ini mencakup inti dari **how to insert activex**, **how to set button**, **java create blank word**, dan **insert command button word** dalam satu contoh yang mandiri.

Langkah selanjutnya? Coba kustomisasi caption tombol, tambahkan makro untuk menanggapi klik, atau sematkan beberapa kontrol pada halaman yang sama. Anda juga dapat mengeksplorasi konversi .docx ke PDF dengan Aspose.Words, menjaga tombol sebagai gambar statis.

Silakan bereksperimen, dan bila menemukan kendala, tinggalkan komentar di bawah. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut membahas topik terkait yang memperluas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}