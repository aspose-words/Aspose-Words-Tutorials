---
title: Menggunakan Opsi Pembersihan di Aspose.Words untuk Java
linktitle: Menggunakan Opsi Pembersihan
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Tingkatkan Kejelasan Dokumen dengan Opsi Pembersihan Aspose.Words untuk Java. Pelajari cara menghapus paragraf kosong, area yang tidak digunakan, dan banyak lagi.
weight: 10
url: /id/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Opsi Pembersihan di Aspose.Words untuk Java


## Pengantar Penggunaan Opsi Pembersihan di Aspose.Words untuk Java

Dalam tutorial ini, kita akan menjelajahi cara menggunakan opsi pembersihan di Aspose.Words untuk Java untuk memanipulasi dan membersihkan dokumen selama proses penggabungan surat. Opsi pembersihan memungkinkan Anda untuk mengontrol berbagai aspek pembersihan dokumen, seperti menghapus paragraf kosong, area yang tidak digunakan, dan banyak lagi.

## Prasyarat

 Sebelum kita mulai, pastikan Anda telah mengintegrasikan pustaka Aspose.Words for Java ke dalam proyek Anda. Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/java/).

## Langkah 1: Menghapus Paragraf Kosong

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Sisipkan bidang gabungan
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Tetapkan opsi pembersihan
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Aktifkan paragraf pembersihan dengan tanda baca
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Jalankan gabungan surat
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Simpan dokumen
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

Dalam contoh ini, kami membuat dokumen baru, menyisipkan kolom gabungan, dan mengatur opsi pembersihan untuk menghapus paragraf kosong. Selain itu, kami mengaktifkan penghapusan paragraf dengan tanda baca. Setelah menjalankan gabungan surat, dokumen disimpan dengan pembersihan yang ditentukan.

## Langkah 2: Menghapus Wilayah yang Tidak Digabungkan

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Tetapkan opsi pembersihan untuk menghapus wilayah yang tidak digunakan
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Jalankan gabungan surat dengan wilayah
doc.getMailMerge().executeWithRegions(data);

// Simpan dokumen
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

Dalam contoh ini, kami membuka dokumen yang sudah ada dengan penggabungan wilayah, mengatur opsi pembersihan untuk menghapus wilayah yang tidak digunakan, lalu menjalankan penggabungan surat dengan data kosong. Proses ini secara otomatis menghapus wilayah yang tidak digunakan dari dokumen.

## Langkah 3: Menghapus Kolom Kosong

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Tetapkan opsi pembersihan untuk menghapus bidang kosong
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Jalankan gabungan surat
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Simpan dokumen
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

Dalam contoh ini, kami membuka dokumen dengan kolom gabungan, mengatur opsi pembersihan untuk menghapus kolom kosong, dan menjalankan penggabungan surat dengan data. Setelah penggabungan, kolom kosong apa pun akan dihapus dari dokumen.

## Langkah 4: Menghapus Kolom yang Tidak Digunakan

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Tetapkan opsi pembersihan untuk menghapus bidang yang tidak digunakan
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Jalankan gabungan surat
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Simpan dokumen
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

Dalam contoh ini, kami membuka dokumen dengan kolom gabungan, mengatur opsi pembersihan untuk menghapus kolom yang tidak digunakan, dan menjalankan gabungan surat dengan data. Setelah penggabungan, kolom yang tidak digunakan akan dihapus dari dokumen.

## Langkah 5: Menghapus Bidang yang Berisi

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Tetapkan opsi pembersihan untuk menghapus bidang yang berisi
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Jalankan gabungan surat
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Simpan dokumen
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

Dalam contoh ini, kami membuka dokumen dengan kolom gabungan, mengatur opsi pembersihan untuk menghapus kolom yang berisi kolom tersebut, dan menjalankan penggabungan surat dengan data. Setelah penggabungan, kolom itu sendiri akan dihapus dari dokumen.

## Langkah 6: Menghapus Baris Tabel Kosong

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Tetapkan opsi pembersihan untuk menghapus baris tabel kosong
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Jalankan gabungan surat
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Simpan dokumen
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

Dalam contoh ini, kami membuka dokumen dengan tabel dan menggabungkan kolom, mengatur opsi pembersihan untuk menghapus baris tabel yang kosong, dan menjalankan penggabungan surat dengan data. Setelah penggabungan, baris tabel yang kosong akan dihapus dari dokumen.

## Kesimpulan

Dalam tutorial ini, Anda telah mempelajari cara menggunakan opsi pembersihan di Aspose.Words untuk Java untuk memanipulasi dan membersihkan dokumen selama proses penggabungan surat. Opsi ini menyediakan kontrol yang lebih rinci atas pembersihan dokumen, sehingga Anda dapat membuat dokumen yang disempurnakan dan disesuaikan dengan mudah.

## Pertanyaan yang Sering Diajukan

### Apa saja pilihan pembersihan di Aspose.Words untuk Java?

Opsi pembersihan di Aspose.Words untuk Java adalah pengaturan yang memungkinkan Anda mengontrol berbagai aspek pembersihan dokumen selama proses penggabungan surat. Opsi ini memungkinkan Anda menghapus elemen yang tidak diperlukan seperti paragraf kosong, area yang tidak digunakan, dan lainnya, sehingga dokumen akhir Anda terstruktur dengan baik dan rapi.

### Bagaimana cara menghapus paragraf kosong dari dokumen saya?

 Untuk menghapus paragraf kosong dari dokumen Anda menggunakan Aspose.Words untuk Java, Anda dapat mengatur`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` opsi ke true. Ini akan secara otomatis menghilangkan paragraf yang tidak memiliki konten, sehingga menghasilkan dokumen yang lebih bersih.

###  Apa tujuan dari`REMOVE_UNUSED_REGIONS` cleanup option?

 Itu`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Opsi ini digunakan untuk menghapus area dalam dokumen yang tidak memiliki data terkait selama proses penggabungan surat. Opsi ini membantu menjaga dokumen Anda tetap rapi dengan membuang placeholder yang tidak digunakan.

### Bisakah saya menghapus baris tabel kosong dari dokumen menggunakan Aspose.Words untuk Java?

 Ya, Anda dapat menghapus baris tabel kosong dari dokumen dengan mengatur`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`opsi pembersihan ke true. Ini akan secara otomatis menghapus baris tabel yang tidak berisi data, memastikan tabel terstruktur dengan baik dalam dokumen Anda.

###  Apa yang terjadi ketika saya mengatur`REMOVE_CONTAINING_FIELDS` option?

 Pengaturan`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` Opsi ini akan menghapus seluruh bidang gabungan, termasuk paragraf yang memuatnya, dari dokumen selama proses penggabungan surat. Ini berguna saat Anda ingin menghilangkan bidang gabungan dan teks terkaitnya.

### Bagaimana cara menghapus kolom gabungan yang tidak terpakai dari dokumen saya?

 Untuk menghapus bidang gabungan yang tidak digunakan dari dokumen, Anda dapat mengatur`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` opsi ke true. Ini akan secara otomatis menghilangkan kolom gabungan yang tidak terisi selama penggabungan surat, sehingga menghasilkan dokumen yang lebih bersih.

###  Apa perbedaan antara`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 Itu`REMOVE_EMPTY_FIELDS` opsi menghapus bidang gabungan yang tidak memiliki data atau kosong selama proses gabungan surat. Di sisi lain,`REMOVE_UNUSED_FIELDS`Opsi menghapus bidang gabungan yang tidak diisi dengan data selama penggabungan. Pilihan di antara keduanya bergantung pada apakah Anda ingin menghapus bidang tanpa konten atau bidang yang tidak digunakan dalam operasi penggabungan tertentu.

### Bagaimana cara mengaktifkan penghapusan paragraf dengan tanda baca?

 Untuk mengaktifkan penghapusan paragraf dengan tanda baca, Anda dapat mengatur`cleanupParagraphsWithPunctuationMarks` opsi ke true dan tentukan tanda baca yang akan dipertimbangkan untuk dibersihkan. Ini memungkinkan Anda membuat dokumen yang lebih baik dengan menghapus paragraf yang hanya berisi tanda baca yang tidak perlu.

### Dapatkah saya menyesuaikan opsi pembersihan di Aspose.Words untuk Java?

Ya, Anda dapat menyesuaikan opsi pembersihan sesuai dengan kebutuhan spesifik Anda. Anda dapat memilih opsi pembersihan mana yang akan diterapkan dan mengonfigurasinya sesuai dengan persyaratan pembersihan dokumen Anda, untuk memastikan bahwa dokumen akhir Anda memenuhi standar yang Anda inginkan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
