---
"description": "Pelajari cara mengkloning dan menggabungkan dokumen di Aspose.Words untuk Java. Panduan langkah demi langkah dengan contoh kode sumber."
"linktitle": "Mengkloning dan Menggabungkan Dokumen"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Mengkloning dan Menggabungkan Dokumen di Aspose.Words untuk Java"
"url": "/id/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mengkloning dan Menggabungkan Dokumen di Aspose.Words untuk Java


## Pengantar Pengklonan dan Penggabungan Dokumen di Aspose.Words untuk Java

Dalam tutorial ini, kita akan menjelajahi cara mengkloning dan menggabungkan dokumen menggunakan Aspose.Words untuk Java. Kita akan membahas berbagai skenario, termasuk mengkloning dokumen, memasukkan dokumen pada titik penggantian, bookmark, dan selama operasi penggabungan surat.

## Langkah 1: Mengkloning Dokumen

Untuk mengkloning dokumen di Aspose.Words untuk Java, Anda dapat menggunakan `deepClone()` metode. Berikut contoh sederhananya:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Kode ini akan membuat klon mendalam dari dokumen asli dan menyimpannya sebagai berkas baru.

## Langkah 2: Memasukkan Dokumen di Titik Penggantian

Anda dapat menyisipkan dokumen pada titik penggantian tertentu di dokumen lain. Berikut cara melakukannya:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Dalam contoh ini, kami menggunakan `FindReplaceOptions` objek untuk menentukan penangan panggilan balik untuk penggantian. `InsertDocumentAtReplaceHandler` kelas menangani logika penyisipan.

## Langkah 3: Memasukkan Dokumen ke Bookmark

Untuk menyisipkan dokumen pada penanda tertentu di dokumen lain, Anda dapat menggunakan kode berikut:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Di sini kita menemukan penanda berdasarkan nama dan menggunakan `insertDocument` metode untuk memasukkan konten `subDoc` dokumen di lokasi penanda.

## Langkah 4: Memasukkan Dokumen Selama Mail Merge

Anda dapat menyisipkan dokumen selama operasi penggabungan surat di Aspose.Words untuk Java. Berikut caranya:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

Dalam contoh ini, kami menetapkan panggilan balik penggabungan bidang menggunakan `InsertDocumentAtMailMergeHandler` kelas untuk menangani penyisipan dokumen yang ditentukan oleh bidang "Document_1".

## Kesimpulan

Pengklonan dan penggabungan dokumen di Aspose.Words untuk Java dapat dilakukan dengan menggunakan berbagai teknik. Baik Anda perlu mengkloning dokumen, menyisipkan konten di titik penggantian, bookmark, atau selama penggabungan surat, Aspose.Words menyediakan fitur canggih untuk memanipulasi dokumen dengan lancar.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara mengkloning dokumen di Aspose.Words untuk Java?

Anda dapat mengkloning dokumen di Aspose.Words untuk Java menggunakan `deepClone()` metode. Berikut contohnya:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Bagaimana cara menyisipkan dokumen pada penanda halaman?

Untuk memasukkan dokumen ke dalam bookmark di Aspose.Words untuk Java, Anda dapat menemukan bookmark berdasarkan nama dan kemudian menggunakan `insertDocument` metode untuk memasukkan konten. Berikut contohnya:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Bagaimana cara menyisipkan dokumen selama gabungan surat di Aspose.Words untuk Java?

Anda dapat menyisipkan dokumen selama penggabungan surat di Aspose.Words untuk Java dengan menyetel panggilan balik penggabungan bidang dan menentukan dokumen yang akan disisipkan. Berikut contohnya:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

Dalam contoh ini, `InsertDocumentAtMailMergeHandler` kelas menangani logika penyisipan untuk "DocumentField" selama penggabungan surat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}