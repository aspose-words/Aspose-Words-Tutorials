---
title: Menambahkan Konten menggunakan DocumentBuilder di Aspose.Words untuk Java
linktitle: Menambahkan Konten menggunakan DocumentBuilder
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Kuasai Pembuatan Dokumen dengan Aspose.Words untuk Java. Panduan Langkah demi Langkah untuk Menambahkan Teks, Tabel, Gambar, dan Lainnya. Buat Dokumen Word yang Menakjubkan dengan Mudah.
weight: 26
url: /id/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menambahkan Konten menggunakan DocumentBuilder di Aspose.Words untuk Java


## Pengantar Menambahkan Konten menggunakan DocumentBuilder di Aspose.Words untuk Java

Dalam panduan langkah demi langkah ini, kita akan menjelajahi cara menggunakan Aspose.Words untuk DocumentBuilder Java guna menambahkan berbagai jenis konten ke dokumen Word. Kita akan membahas penyisipan teks, tabel, aturan horizontal, kolom formulir, HTML, hyperlink, daftar isi, gambar sebaris dan mengambang, paragraf, dan banyak lagi. Mari kita mulai!

## Prasyarat

 Sebelum memulai, pastikan Anda telah menyiapkan pustaka Aspose.Words untuk Java di proyek Anda. Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/java/).

## Menambahkan Teks

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Masukkan paragraf teks sederhana
builder.write("This is a simple text paragraph.");

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Menambahkan Tabel

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//Mulai tabel
Table table = builder.startTable();

// Sisipkan sel dan konten
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Akhiri tabel
builder.endTable();

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Menambahkan Aturan Horizontal

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Masukkan penggaris horizontal
builder.insertHorizontalRule();

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Menambahkan Bidang Formulir

### Bidang Formulir Input Teks

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Masukkan bidang formulir input teks
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

### Formulir Kotak Centang

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Masukkan bidang formulir kotak centang
builder.insertCheckBox("CheckBox", true, true, 0);

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

### Bidang Formulir Kotak Kombo

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Tentukan item untuk kotak kombo
String[] items = { "Option 1", "Option 2", "Option 3" };

// Masukkan bidang formulir kotak kombo
builder.insertComboBox("DropDown", items, 0);

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Menambahkan HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Masukkan konten HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Menambahkan Hyperlink

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Masukkan hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", salah);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Menambahkan Daftar Isi

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Masukkan daftar isi
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Tambahkan konten dokumen
// ...

// Perbarui daftar isi
doc.updateFields();

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Menambahkan Gambar

### Gambar Sebaris

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Sisipkan gambar sebaris
builder.insertImage("path/to/your/image.png");

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

### Gambar Mengambang

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Sisipkan gambar mengambang
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Menambahkan Paragraf

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Mengatur format paragraf
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

// Sisipkan paragraf
builder.writeln("This is a formatted paragraph.");

// Simpan dokumen
doc.save("path/to/your/document.docx");
```

## Langkah 10: Memindahkan Kursor

 Anda dapat mengontrol posisi kursor dalam dokumen menggunakan berbagai metode seperti`moveToParagraph`, `moveToCell`dan masih banyak lagi. Berikut contohnya:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Pindahkan kursor ke paragraf tertentu
builder.moveToParagraph(2, 0);

// Tambahkan konten di posisi kursor baru
builder.writeln("This is the 3rd paragraph.");
```

Berikut ini adalah beberapa operasi umum yang dapat Anda lakukan menggunakan Aspose.Words untuk Java's DocumentBuilder. Jelajahi dokumentasi pustaka untuk fitur dan opsi penyesuaian yang lebih canggih. Selamat membuat dokumen!


## Kesimpulan

Dalam panduan lengkap ini, kami telah mengeksplorasi kemampuan Aspose.Words untuk DocumentBuilder Java guna menambahkan berbagai jenis konten ke dokumen Word. Kami telah membahas teks, tabel, aturan horizontal, kolom formulir, HTML, hyperlink, daftar isi, gambar, paragraf, dan pergerakan kursor.

## Pertanyaan yang Sering Diajukan

### T: Apa itu Aspose.Words untuk Java?

J: Aspose.Words untuk Java adalah pustaka Java yang memungkinkan pengembang membuat, memodifikasi, dan memanipulasi dokumen Microsoft Word secara terprogram. Pustaka ini menyediakan berbagai fitur untuk pembuatan dokumen, pemformatan, dan penyisipan konten.

### T: Bagaimana cara menambahkan daftar isi ke dokumen saya?

A: Untuk menambahkan daftar isi, gunakan`DocumentBuilder` untuk memasukkan kolom daftar isi ke dalam dokumen Anda. Pastikan untuk memperbarui kolom dalam dokumen setelah menambahkan konten untuk mengisi daftar isi. Berikut contohnya:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Masukkan bidang daftar isi
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Tambahkan konten dokumen
// ...

// Perbarui daftar isi
doc.updateFields();
```

### T: Bagaimana cara menyisipkan gambar ke dalam dokumen menggunakan Aspose.Words untuk Java?

 A: Anda dapat menyisipkan gambar, baik inline maupun floating, menggunakan`DocumentBuilder`Berikut adalah contoh keduanya:

#### Gambar Sebaris:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Sisipkan gambar sebaris
builder.insertImage("path/to/your/image.png");
```

#### Gambar Mengambang:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Sisipkan gambar mengambang
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### T: Dapatkah saya memformat teks dan paragraf saat menambahkan konten?

 A: Ya, Anda dapat memformat teks dan paragraf menggunakan`DocumentBuilder`Anda dapat mengatur properti font, perataan paragraf, indentasi, dan banyak lagi. Berikut contohnya:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Mengatur font dan format paragraf
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

// Masukkan paragraf yang diformat
builder.writeln("This is a formatted paragraph.");
```

### T: Bagaimana cara memindahkan kursor ke lokasi tertentu dalam dokumen?

 A: Anda dapat mengontrol posisi kursor menggunakan metode seperti`moveToParagraph`, `moveToCell`dan masih banyak lagi. Berikut contohnya:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Pindahkan kursor ke paragraf tertentu
builder.moveToParagraph(2, 0);

// Tambahkan konten di posisi kursor baru
builder.writeln("This is the 3rd paragraph.");
```

Berikut ini adalah beberapa pertanyaan umum dan jawaban untuk membantu Anda memulai dengan Aspose.Words untuk Java's DocumentBuilder. Jika Anda memiliki pertanyaan lebih lanjut atau memerlukan bantuan lebih lanjut, lihat[dokumentasi perpustakaan](https://reference.aspose.com/words/java/) atau mencari bantuan dari komunitas Aspose.Words dan sumber daya dukungan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
