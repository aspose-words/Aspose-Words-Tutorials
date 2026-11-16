---
category: general
date: 2026-11-15
description: Edit dokumen Word secara programatik untuk menyisipkan tombol perintah.
  Pelajari cara menambahkan tombol, mengatur nama tombol perintah, dan membuat tombol
  formulir Word dalam hitungan menit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: id
lastmod: 2026-11-15
og_description: Edit dokumen Word secara programatis dan sisipkan tombol perintah.
  Panduan ini menunjukkan cara menambahkan tombol, mengatur nama tombol perintah,
  dan membuat tombol formulir Word dengan cepat.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Edit dokumen Word secara programatis – tambahkan tombol perintah
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Sunting dokumen Word secara programatis dan tambahkan tombol perintah
url: /id/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Edit dokumen Word secara programatis dan tambahkan tombol perintah

Jika Anda perlu **edit dokumen Word secara programatis**, cara tercepat adalah menggunakan API Aspose.Words. Tutorial ini menunjukkan secara tepat **cara menambahkan tombol** kontrol, mengonfigurasi caption‑nya, dan **menetapkan nama tombol perintah** sehingga dokumen dapat berfungsi sebagai formulir sederhana. Pada akhir tutorial Anda akan memiliki *.docx* yang dapat diedit sepenuhnya yang berisi tombol perintah fungsional siap untuk pemrosesan lanjutan.

Anda akan belajar cara **menyisipkan kata tombol perintah**, **membuat kata tombol formulir**, dan mengelola properti tombol tanpa membuka Word secara manual. Prasyarat satu‑satunya adalah lingkungan pengembangan Java dasar dan pustaka Aspose.Words untuk Java.

## Prasyarat

- Java 17 atau lebih baru (kode juga bekerja dengan Java 8+)
- Aspose.Words for Java (unduh dari [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Dokumen Word yang sudah ada (`input.docx`) yang ingin Anda modifikasi
- Familiaritas dengan Maven atau Gradle untuk menambahkan dependensi Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Langkah 1: Muat dokumen Word

Operasi pertama ketika Anda **edit dokumen Word secara programatis** adalah memuat file sumber ke dalam objek `Document`. Objek ini mewakili seluruh file Word dalam memori, memungkinkan Anda memanipulasi isinya.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Mengapa ini penting:** Memuat dokumen membuat struktur mirip DOM yang dapat dijelajahi dan dimodifikasi oleh Aspose.Words. Melewatkan langkah ini akan membuat Anda tidak memiliki target untuk penyisipan tombol.

## Langkah 2: Buat `DocumentBuilder` untuk mengedit dokumen

`DocumentBuilder` berfungsi seperti kursor di dalam file Word. Ia memungkinkan Anda menyisipkan teks, gambar, dan kontrol formulir pada posisi saat ini.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tip:** Jika Anda membutuhkan tombol di paragraf tertentu, pindahkan builder terlebih dahulu dengan `builder.moveToParagraph(index, true);`.

## Langkah 3: Sisipkan Forms2OleControl (tombol perintah)

Sekarang kami menjawab pertanyaan utama **cara menambahkan tombol** dalam file Word. Metode `insertForms2OleControl()` membuat tombol perintah *Forms2.0* warisan, yang merupakan kontrol paling kompatibel di semua versi Word.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Kasus khusus:** Kontrol Forms2.0 hanya terlihat dalam *Design Mode* Word. Jika Anda membutuhkan tombol ActiveX yang lebih baru, pertimbangkan `insertOleControl()` sebagai gantinya, tetapi kontrol warisan ini berfungsi untuk kebanyakan skenario otomasi.

## Langkah 4: Konfigurasikan properti tombol

Setelah menyisipkan kontrol, Anda dapat **menetapkan nama tombol perintah** dan **menyisipkan kata tombol perintah** (caption) agar lebih ramah pengguna.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Mengapa properti ini?**  
> - `setName` memberikan tombol sebuah pengenal yang dapat direferensikan oleh VBA atau alat eksternal.  
> - `setCaption` adalah label yang terlihat, secara efektif **membuat kata tombol formulir** yang diklik oleh pengguna akhir.

Anda juga dapat menyesuaikan ukuran, posisi, atau menambahkan makro dengan mengakses objek OLE yang mendasarinya, tetapi topik tersebut berada di luar cakupan panduan singkat ini.

## Langkah 5: Simpan dokumen yang dimodifikasi

Akhirnya, simpan perubahan ke file baru. Langkah ini **membuat kata tombol formulir** dalam dokumen output.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Hasil:** Membuka `output.docx` di Microsoft Word, Anda akan melihat tombol berlabel “Submit”. Saat Anda mengubah Word ke *Design Mode* (Developer → Design Mode), Anda dapat mengklik ganda tombol untuk melampirkan makro atau sekadar menggunakannya sebagai placeholder dalam formulir.

### Output yang diharapkan

Ketika Anda membuka file yang disimpan:

- Titik sisipan kursor digantikan oleh tombol.
- Tombol menampilkan caption **Submit**.
- Nama internal tombol adalah **cmdSubmit**, yang dapat Anda referensikan dalam skrip VBA atau otomasi eksternal.

## Pertanyaan umum dan variasi

### Cara menambahkan tombol ke paragraf tertentu?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Cara menyisipkan tombol di dalam sel tabel?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Bagaimana jika saya membutuhkan tombol yang lebih besar?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Cara **menyisipkan kata tombol perintah** menggunakan bahasa lain (misalnya, C#)?

Logika yang sama berlaku; ganti sintaks Java dengan padanan C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Tips profesional dan jebakan

- **Tips pro:** Selalu panggil `builder.moveToDocumentEnd()` sebelum menyisipkan tombol jika Anda menginginkannya di akhir dokumen.  
- **Waspada:** Menyimpan ke file yang sama dengan yang Anda buka dapat merusak dokumen jika terjadi pengecualian. Gunakan jalur output terpisah seperti yang ditunjukkan.  
- **Kompatibilitas:** Tombol Forms2.0 warisan bekerja di Word 2007‑2021. Untuk Word di web, pertimbangkan menggunakan kontrol konten sebagai gantinya.  
- **Kinerja:** Memuat dokumen yang sangat besar (>100 MB) dapat mengonsumsi memori yang signifikan. Gunakan `Document.load(InputStream, LoadOptions)` dengan `LoadOptions.setLoadFormat(LoadFormat.DOCX)` untuk membatasi penggunaan sumber daya.

## Contoh lengkap yang berfungsi

Berikut adalah program Java lengkap yang siap dijalankan. Salin ke dalam kelas bernama `WordButtonDemo.java`, sesuaikan jalur file, dan jalankan `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Jalankan program dan buka `output.docx` untuk memverifikasi tombol muncul seperti yang diharapkan.

## Kesimpulan

Anda kini tahu cara **edit dokumen Word secara programatis** untuk **menyisipkan kata tombol perintah**, **membuat kata tombol formulir**, dan **menetapkan nama tombol perintah** menggunakan Aspose.Words untuk Java. Pendekatan ini menghilangkan pengeditan manual, memungkinkan pemrosesan batch formulir, dan terintegrasi mulus dengan alur kerja otomatis.

Selanjutnya, Anda mungkin ingin menjelajahi:

- Menambahkan makro VBA ke tombol (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Menggunakan **kontrol konten** untuk pengalaman formulir yang lebih kaya (`builder.insertCheckBox()` dll.)  
- Mengotomatisasi penyisipan massal di banyak dokumen dengan loop  

Silakan bereksperimen dengan ukuran tombol, posisi, dan penanganan acara untuk menyesuaikan skenario spesifik Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Create word document programmatically and add ActiveX button](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}