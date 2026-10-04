---
category: general
date: 2026-10-04
description: Buat dokumen Word menggunakan Java yang mencakup kontrol konten teks
  biasa dan placeholder. Pelajari cara menambahkan placeholder ke tag dan cara menyisipkan
  sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: id
lastmod: 2026-10-04
og_description: Buat dokumen Word dengan kontrol konten teks biasa dan placeholder.
  Tutorial ini menunjukkan cara menambahkan placeholder ke tag dan cara menyisipkan
  sdt menggunakan Aspose.Words for Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Buat dokumen Word dengan kontrol konten – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Buat dokumen Word dengan kontrol konten teks biasa
url: /id/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word dengan kontrol konten teks biasa

Jika Anda perlu **create word document** yang berisi wilayah yang dapat diedit pengguna, kontrol konten teks biasa adalah pendekatan yang paling dapat diandalkan. Tutorial ini menunjukkan secara tepat cara menyisipkan Structured Document Tag (SDT), mengatur placeholder, dan menyimpan hasilnya sebagai **docx with placeholder**. Anda akan melihat contoh Java lengkap yang dapat dijalankan yang bekerja dengan Aspose.Words for Java 23.8.

Panduan ini mencakup semua prasyarat, menjelaskan mengapa setiap panggilan API penting, dan memberikan tip untuk menangani kasus tepi seperti placeholder multibahasa atau tag bersarang. Pada akhir tutorial Anda dapat menghasilkan file Word yang meminta pengguna untuk “Enter text…” langsung di dalam dokumen.

## Prasyarat

* Java 17 (atau lebih baru) terinstal dan dikonfigurasi pada PATH Anda.  
* Maven 3.8+ untuk mengelola dependensi.  
* Lisensi Aspose.Words for Java (evaluasi dapat digunakan untuk pengujian).  
* IDE pengembangan (IntelliJ IDEA, Eclipse, atau VS Code).

Tambahkan Aspose.Words ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Buat dokumen Word dengan kontrol konten teks biasa

Alur kerja inti terdiri dari empat langkah logis. Setiap langkah dibungkus dalam metode yang diberi nama jelas sehingga Anda dapat menggunakan kembali logika tersebut dalam proyek yang lebih besar.

### Langkah 1: Inisialisasi dokumen dan builder

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Mengapa ini penting:** `Document` mewakili file Word dalam memori. `DocumentBuilder` adalah API fluens yang memungkinkan Anda menyisipkan paragraf, tabel, dan SDT. Memulai dengan dokumen kosong memastikan placeholder muncul di awal, yang berguna untuk templat.

### Langkah 2: Sisipkan Structured Document Tag (SDT) teks‑biasa

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Mengapa ini penting:** `StructuredDocumentTagType.PLAIN_TEXT` membuat kontrol konten yang hanya menerima karakter biasa, mencegah pemformatan tidak sengaja. Pemanggilan `setPlaceholderName` mengisi teks petunjuk abu‑abu yang dilihat pengguna sebelum mengetik—ini adalah operasi **add placeholder to tag** yang membuat dokumen terasa seperti formulir.

### Langkah 3: Tambahkan konten reguler setelah SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Mengapa ini penting:** Menambahkan konten setelah kontrol memverifikasi bahwa SDT tidak mengonsumsi seluruh alur dokumen. Ini juga menunjukkan cara mencampur tag terstruktur dengan paragraf biasa, kebutuhan umum saat membuat templat.

### Langkah 4: Simpan file hasil

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Mengapa ini penting:** Metode `save` menulis model dalam memori ke file fisik **docx with placeholder**. File yang dihasilkan dapat dibuka di Microsoft Word, LibreOffice, atau perpustakaan apa pun yang mendukung format OpenXML.

## Kode sumber lengkap

Menggabungkan semua bagian memberikan Anda program mandiri yang dapat Anda kompilasi dan jalankan:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Output yang diharapkan

Menjalankan program membuat `SdtDemo.docx`. Membuka file di Word menampilkan:

* Placeholder abu‑abu “Enter text…” di dalam kontrol konten teks‑biasa yang diberi label **MyTag**.  
* Baris **After SDT** tepat di bawah kontrol.

Placeholder menghilang begitu pengguna mengetik, mempertahankan pemformatan asli.

## Variasi umum dan kasus tepi

| Skenario | Perubahan yang disarankan |
|----------|---------------------------|
| **Placeholder multibahasa** | Gunakan karakter Unicode dalam `setPlaceholderName`, misalnya `sdt.setPlaceholderName("Введите текст…");`. |
| **Kontrol konten bersarang** | Sisipkan SDT kedua di dalam yang pertama dengan memanggil `builder.moveTo(sdt.getParagraph());` sebelum `insertStructuredDocumentTag` kedua. |
| **Kontrol hanya-baca** | Panggil `sdt.setLockContentControl(true);` untuk mencegah pengguna menghapus tag. |
| **Rich‑text alih-alih teks biasa** | Ganti `StructuredDocumentTagType.PLAIN_TEXT` dengan `StructuredDocumentTagType.RICH_TEXT`. |
| **Menyimpan ke aliran** | Gunakan `doc.save(OutputStream, SaveFormat.DOCX);` ketika Anda perlu mengirim file melalui HTTP. |

## Tips profesional

* **Reuse tag IDs** – Jika Anda menghasilkan banyak dokumen dari templat yang sama, pertahankan nama tag (`"MyTag"`) konsisten sehingga proses hilir (mis., mail‑merge) dapat menemukannya dengan andal.  
* **Performance** – Untuk templat besar, buat `DocumentBuilder` sekali dan gunakan kembali; menyisipkan banyak SDT dalam loop lebih cepat daripada membuat ulang builder setiap iterasi.  
* **Testing** – Setelah menghasilkan DOCX, verifikasi secara programatik bahwa placeholder ada dengan `doc.getRange().getStructuredDocumentTags().getCount()`.

## Kesimpulan

Anda sekarang tahu cara **create word document** yang berisi **plain text content control** dengan placeholder khusus, secara efektif menghasilkan **docx with placeholder** yang siap untuk input pengguna. Contoh ini menunjukkan siklus lengkap mulai dari inisialisasi dokumen, **how to insert sdt**, **add placeholder to tag**, menambahkan konten reguler, dan akhirnya menyimpan file.

### Langkah selanjutnya

* Jelajahi **how to insert sdt** di dalam tabel untuk tata letak seperti formulir.  
* Gabungkan teknik ini dengan penggabungan **docx with placeholder** untuk membangun pembuat laporan otomatis.  
* Bereksperimen dengan tipe kontrol lain (`RICH_TEXT`, `CHECKBOX`) untuk membuat formulir Word yang lebih kaya.

Silakan sesuaikan kode untuk mesin templat Anda sendiri, dan bagikan hasil Anda di komentar!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cara Membuat Dokumen PDF dengan Aspose.Words untuk Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}