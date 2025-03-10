---
title: Menemukan dan Mengganti Teks di Aspose.Words untuk Java
linktitle: Menemukan dan Mengganti Teks
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Pelajari cara mencari dan mengganti teks dalam dokumen Word dengan Aspose.Words untuk Java. Panduan langkah demi langkah dengan contoh kode. Tingkatkan keterampilan manipulasi dokumen Java Anda.
weight: 15
url: /id/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menemukan dan Mengganti Teks di Aspose.Words untuk Java


## Pengantar Menemukan dan Mengganti Teks di Aspose.Words untuk Java

Aspose.Words untuk Java adalah API Java yang canggih yang memungkinkan Anda bekerja dengan dokumen Word secara terprogram. Salah satu tugas umum saat menangani dokumen Word adalah menemukan dan mengganti teks. Apakah Anda perlu memperbarui placeholder dalam template atau melakukan manipulasi teks yang lebih rumit, Aspose.Words untuk Java dapat membantu Anda mencapai tujuan secara efisien.

## Prasyarat

Sebelum kita menyelami detail tentang mencari dan mengganti teks, pastikan Anda memiliki prasyarat berikut:

- Lingkungan Pengembangan Java
- Aspose.Words untuk pustaka Java
- Contoh dokumen Word untuk digunakan

 Anda dapat mengunduh pustaka Aspose.Words untuk Java dari[Di Sini](https://releases.aspose.com/words/java/).

## Menemukan dan Mengganti Teks Sederhana

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Membuat DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Temukan dan ganti teks
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

 Dalam contoh ini, kita memuat dokumen Word, membuat`DocumentBuilder` , dan gunakan`replace` metode untuk menemukan dan mengganti "teks lama" dengan "teks baru" dalam dokumen.

## Menggunakan Ekspresi Reguler

Ekspresi reguler menyediakan kemampuan pencocokan pola yang canggih untuk pencarian dan penggantian teks. Aspose.Words untuk Java mendukung ekspresi reguler untuk operasi pencarian dan penggantian yang lebih canggih.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Membuat DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Gunakan ekspresi reguler untuk menemukan dan mengganti teks
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Dalam contoh ini, kami menggunakan pola ekspresi reguler untuk menemukan dan mengganti teks dalam dokumen.

## Mengabaikan Teks di Dalam Kolom

Anda dapat mengonfigurasi Aspose.Words untuk mengabaikan teks di dalam kolom saat melakukan operasi temukan dan ganti.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Buat instance FindReplaceOptions dan atur IgnoreFields menjadi true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Gunakan opsi saat mengganti teks
doc.getRange().replace("text-to-replace", "new-text", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Ini berguna saat Anda ingin mengecualikan teks di dalam bidang, seperti bidang gabungan, agar tidak diganti.

## Mengabaikan Teks Di Dalam Hapus Revisi

Anda dapat mengonfigurasi Aspose.Words untuk mengabaikan teks di dalam revisi penghapusan selama operasi pencarian dan penggantian.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Buat instance FindReplaceOptions dan atur IgnoreDeleted menjadi true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Gunakan opsi saat mengganti teks
doc.getRange().replace("text-to-replace", "new-text", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Ini memungkinkan Anda untuk mengecualikan teks yang telah ditandai untuk dihapus dalam perubahan yang dilacak agar tidak diganti.

## Mengabaikan Teks Di Dalam Sisipan Revisi

Anda dapat mengonfigurasi Aspose.Words untuk mengabaikan teks di dalam revisi penyisipan selama operasi temukan dan ganti.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Buat instance FindReplaceOptions dan atur IgnoreInserted menjadi true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Gunakan opsi saat mengganti teks
doc.getRange().replace("text-to-replace", "new-text", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Ini memungkinkan Anda untuk mengecualikan teks yang telah ditandai sebagai dimasukkan dalam perubahan yang dilacak agar tidak diganti.

## Mengganti Teks dengan HTML

Anda dapat menggunakan Aspose.Words untuk Java untuk mengganti teks dengan konten HTML.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Buat instance FindReplaceOptions dengan panggilan balik penggantian kustom
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Gunakan opsi saat mengganti teks
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

 Dalam contoh ini, kami menggunakan custom`ReplaceWithHtmlEvaluator` untuk mengganti teks dengan konten HTML.

## Mengganti Teks di Header dan Footer

Anda dapat menemukan dan mengganti teks dalam header dan footer dokumen Word Anda.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Dapatkan koleksi header dan footer
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Pilih jenis header atau footer yang ingin Anda ganti teksnya (misalnya, HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Buat instance FindReplaceOptions dan terapkan ke rentang footer
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Hal ini memungkinkan Anda untuk melakukan penggantian teks khususnya pada header dan footer.

## Menampilkan Perubahan untuk Urutan Header dan Footer

Anda dapat menggunakan Aspose.Words untuk memperlihatkan perubahan susunan header dan footer pada dokumen Anda.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Dapatkan bagian pertama
Section firstPageSection = doc.getFirstSection();

//Buat instance FindReplaceOptions dan terapkan ke rentang dokumen
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Ganti teks yang memengaruhi urutan header dan footer
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Ini memungkinkan Anda memvisualisasikan perubahan yang terkait dengan urutan header dan footer pada dokumen Anda.

## Mengganti Teks dengan Kolom

Anda dapat mengganti teks dengan bidang menggunakan Aspose.Words untuk Java.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Buat instance FindReplaceOptions dan tetapkan panggilan balik penggantian khusus untuk bidang
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Gunakan opsi saat mengganti teks
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

 Dalam contoh ini, kami mengganti teks dengan bidang dan menentukan jenis bidang (misalnya,`FieldType.FIELD_MERGE_FIELD`).

## Mengganti dengan Evaluator

Anda dapat menggunakan evaluator khusus untuk menentukan teks pengganti secara dinamis.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Buat instance FindReplaceOptions dan tetapkan panggilan balik penggantian kustom
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Gunakan opsi saat mengganti teks
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Dalam contoh ini, kami menggunakan evaluator khusus (`MyReplaceEvaluator`) untuk mengganti teks.

## Mengganti dengan Regex

Aspose.Wors untuk Java memungkinkan Anda mengganti teks menggunakan ekspresi reguler.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Gunakan ekspresi reguler untuk menemukan dan mengganti teks
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Dalam contoh ini, kami menggunakan pola ekspresi reguler untuk menemukan dan mengganti teks dalam dokumen.

## Mengenali dan Substitusi dalam Pola Penggantian

Anda dapat mengenali dan membuat substitusi dalam pola penggantian menggunakan Aspose.Words untuk Java.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Buat instance FindReplaceOptions dengan UseSubstitutions yang disetel ke true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Gunakan opsi saat mengganti teks dengan pola
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Hal ini memungkinkan Anda untuk melakukan penggantian dalam pola penggantian untuk penggantian yang lebih lanjut.

## Mengganti dengan String

Anda dapat mengganti teks dengan string sederhana menggunakan Aspose.Words untuk Java.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Ganti teks dengan string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Dalam contoh ini, kami mengganti "teks-yang-akan-diganti" dengan "string-baru" dalam dokumen.

## Menggunakan Legacy Order

Anda dapat menggunakan perintah lama saat melakukan operasi temukan dan ganti.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Buat instance FindReplaceOptions dan tetapkan UseLegacyOrder menjadi true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Gunakan opsi saat mengganti teks
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Hal ini memungkinkan Anda menggunakan perintah lama untuk operasi pencarian dan penggantian.

## Mengganti Teks dalam Tabel

Anda dapat menemukan dan mengganti teks dalam tabel di dokumen Word Anda.

```java
// Muat dokumen
Document doc = new Document("your-document.docx");

// Dapatkan tabel tertentu (misalnya, tabel pertama)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//Gunakan FindReplaceOptions untuk mengganti teks dalam tabel
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Simpan dokumen yang dimodifikasi
doc.save("modified-document.docx");
```

Hal ini memungkinkan Anda untuk melakukan penggantian teks khusus dalam tabel.

## Kesimpulan

Aspose.Words untuk Java menyediakan kemampuan komprehensif untuk menemukan dan mengganti teks dalam dokumen Word. Baik Anda perlu melakukan penggantian teks sederhana atau operasi yang lebih canggih menggunakan ekspresi reguler, manipulasi bidang, atau evaluator khusus, Aspose.Words untuk Java telah menyediakannya untuk Anda. Pastikan untuk menjelajahi dokumentasi dan contoh ekstensif yang disediakan oleh Aspose untuk memanfaatkan potensi penuh dari pustaka Java yang hebat ini.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara mengunduh Aspose.Words untuk Java?

 Anda dapat mengunduh Aspose.Words untuk Java dari situs web dengan mengunjungi[tautan ini](https://releases.aspose.com/words/java/).

### Dapatkah saya menggunakan ekspresi reguler untuk penggantian teks?

Ya, Anda dapat menggunakan ekspresi reguler untuk penggantian teks di Aspose.Words untuk Java. Ini memungkinkan Anda untuk melakukan operasi pencarian dan penggantian yang lebih canggih dan fleksibel.

### Bagaimana saya bisa mengabaikan teks di dalam kolom selama penggantian?

Untuk mengabaikan teks di dalam bidang selama penggantian, Anda dapat mengatur`IgnoreFields` milik`FindReplaceOptions` ke`true`Ini memastikan bahwa teks dalam bidang, seperti bidang gabungan, dikecualikan dari penggantian.

### Bisakah saya mengganti teks di dalam header dan footer?

 Ya, Anda dapat mengganti teks di dalam header dan footer dokumen Word Anda. Cukup akses header atau footer yang sesuai dan gunakan`replace` metode dengan yang diinginkan`FindReplaceOptions`.

### Apa fungsi opsi UseLegacyOrder?

 Itu`UseLegacyOrder` pilihan di`FindReplaceOptions` memungkinkan Anda menggunakan perintah lama saat melakukan operasi pencarian dan penggantian. Ini dapat berguna dalam skenario tertentu di mana perilaku perintah lama diinginkan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
