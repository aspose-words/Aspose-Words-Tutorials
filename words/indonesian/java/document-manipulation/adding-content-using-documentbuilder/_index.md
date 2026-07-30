---
date: 2026-01-01
description: Pelajari cara membuat bidang formulir dan menambahkan teks, tabel, gambar,
  tautan, serta lainnya menggunakan Aspose.Words for Java DocumentBuilder. Panduan
  langkah demi langkah untuk pengembang.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder
  di Aspose.Words untuk Java
url: /id/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menambahkan Konten menggunakan DocumentBuilder di Aspose.Words untuk Java

## Pendahuluan tentang Menambahkan Konten menggunakan DocumentBuilder di Aspose.Words untuk Java

Dalam panduan langkah‑demi‑langkah ini, Anda akan **membuat bidang formulir** dan menambahkan berbagai jenis konten—teks, tabel, garis horizontal, HTML, tautan, gambar, dan lainnya—ke dalam dokumen Word dengan Aspose.Words untuk Java. Baik Anda sedang membuat laporan, templat kontrak, atau formulir interaktif, kelas `DocumentBuilder` memberi Anda kontrol detail atas setiap elemen. Mari kita mulai!

## Jawaban Cepat
- **Bagaimana cara membuat bidang formulir?** Gunakan `insertTextInput`, `insertCheckBox`, atau `insertComboBox` pada sebuah `DocumentBuilder`.
- **Metode apa yang menambahkan teks biasa?** Panggil `builder.write("Your text")` atau `builder.writeln("Your text")`.
- **Apakah saya dapat menyisipkan garis horizontal?** Ya—`builder.insertHorizontalRule()` menambahkan pemisah garis.
- **Bagaimana cara menyisipkan HTML?** Gunakan `builder.insertHtml("<p>HTML content</p>")`.
- **Bagaimana cara menambahkan gambar inline?** `builder.insertImage("path/to/image.png")` menempatkan gambar di dalam alur teks.

## Apa itu DocumentBuilder dan mengapa menggunakannya untuk membuat bidang formulir?

`DocumentBuilder` adalah API fluida Aspose.Words untuk membangun dan mengedit dokumen Word secara programatis. Ia menyembunyikan struktur OpenXML tingkat rendah, memungkinkan Anda fokus pada *apa* yang ingin Anda tambahkan—seperti **bidang formulir**—bukan pada *bagaimana* XML terlihat. Ini menjadikannya ideal untuk menghasilkan formulir dinamis, kontrak, atau dokumen apa pun yang memerlukan interaksi pengguna.

## Prasyarat

Sebelum memulai, pastikan Anda telah menginstal pustaka Aspose.Words untuk Java dalam proyek Anda. Anda dapat mengunduhnya dari [here](https://releases.aspose.com/words/java/).

## Menambahkan Teks (cara menambahkan teks)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Menambahkan Tabel

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Menambahkan Garis Horizontal (menambahkan garis horizontal)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Menambahkan Bidang Formulir (membuat bidang formulir)

### Bidang Formulir Input Teks

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Bidang Formulir Kotak Centang

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Bidang Formulir Kotak Kombinasi

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Menambahkan HTML (menyisipkan html)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Menambahkan Tautan (cara menambahkan tautan)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Menambahkan Daftar Isi

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Menambahkan Gambar

### Gambar Inline (menyisipkan gambar inline)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Gambar Mengambang

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Menambahkan Paragraf

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Memindahkan Kursor (Langkah 10)

Anda dapat mengontrol posisi kursor dalam dokumen menggunakan metode seperti `moveToParagraph`, `moveToCell`, dll.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Ini adalah beberapa operasi umum yang dapat Anda lakukan menggunakan `DocumentBuilder` Aspose.Words untuk Java. Jelajahi dokumentasi pustaka untuk fitur lanjutan dan opsi penyesuaian. Selamat membuat dokumen!

## Kesimpulan

Dalam panduan komprehensif ini, kami telah menunjukkan cara **membuat bidang formulir** dan menambahkan berbagai jenis konten—teks, tabel, garis horizontal, HTML, tautan, daftar isi, gambar, paragraf yang diformat, dan navigasi kursor—menggunakan `DocumentBuilder` Aspose.Words untuk Java. Anda kini memiliki dasar yang kuat untuk menghasilkan dokumen Word dinamis dan interaktif secara programatis.

## FAQ's

### Q: Apa itu Aspose.Words untuk Java?

A: Aspose.Words untuk Java adalah pustaka Java yang memungkinkan pengembang membuat, memodifikasi, dan memanipulasi dokumen Microsoft Word secara programatis. Ia menyediakan beragam fitur untuk pembuatan dokumen, pemformatan, dan penyisipan konten.

### Q: Bagaimana cara menambahkan daftar isi ke dokumen saya?

A: Untuk menambahkan daftar isi, gunakan `DocumentBuilder` untuk menyisipkan bidang TOC dan kemudian panggil `doc.updateFields()` setelah menambahkan konten Anda.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Bagaimana cara menyisipkan gambar ke dalam dokumen menggunakan Aspose.Words untuk Java?

A: Anda dapat menyisipkan gambar, baik inline maupun mengambang, menggunakan `DocumentBuilder`.

#### Gambar Inline:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Gambar Mengambang:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Apakah saya dapat memformat teks dan paragraf saat menambahkan konten?

A: Ya, Anda dapat memformat teks dan paragraf menggunakan `DocumentBuilder`. Atur properti font, perataan paragraf, indentasi, dan lainnya sebelum menulis konten.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: Bagaimana cara memindahkan kursor ke lokasi tertentu dalam dokumen?

A: Gunakan metode seperti `moveToParagraph`, `moveToCell`, dll., untuk menempatkan kursor sebelum menyisipkan konten baru.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Jawaban‑jawaban ini mencakup skenario paling umum saat bekerja dengan `DocumentBuilder` Aspose.Words untuk Java. Untuk detail lebih mendalam, lihat [library's documentation](https://reference.aspose.com/words/java/) atau bergabung dengan komunitas Aspose.Words untuk dukungan.

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}