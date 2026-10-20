---
date: 2026-01-01
description: Pelajari cara mengekstrak teks menggunakan Aspose.Words untuk Java. Panduan
  langkah demi langkah ini menunjukkan berbagai teknik ekstraksi dengan contoh kode
  siap dijalankan.
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Cara Mengekstrak Teks Menggunakan Aspose.Words untuk Java
url: /id/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengekstrak Teks Menggunakan Aspose.Words untuk Java

## Cara Mengekstrak Teks Menggunakan Aspose.Words untuk Java

Dalam dunia pemrosesan dokumen, **bagaimana cara mengekstrak teks menggunakan Aspose.Words** adalah pertanyaan yang sering muncul bagi pengembang Java. Baik Anda perlu mengambil teks biasa, tabel, gambar, atau elemen spesifik seperti bookmark atau komentar, Aspose.Words untuk Java menawarkan API yang kaya sehingga pekerjaan menjadi mudah. Dalam panduan ini kami akan membahas puluhan skenario ekstraksi, menjelaskan mengapa setiap pendekatan penting, dan menyediakan contoh kode siap‑jalankan yang dapat Anda masukkan ke dalam proyek Anda.

## Jawaban Cepat
- **Perpustakaan apa yang saya perlukan?** Aspose.Words untuk Java (unduh dari situs resmi).  
- **Bisakah saya mengekstrak hanya teks biasa?** Ya – gunakan `Document.getText()` atau `DocumentBuilder` dengan fields.  
- **Apakah memungkinkan mengekstrak antara bookmark?** Tentu saja, gunakan `BookmarkStart`/`BookmarkEnd` dengan `ExtractContentHelper`.  
- **Apakah saya memerlukan lisensi untuk produksi?** Lisensi komersial diperlukan untuk penggunaan non‑trial.  
- **Versi Java mana yang didukung?** Java 8 dan yang lebih baru sepenuhnya kompatibel.

## Prasyarat

1. **Aspose.Words untuk Java** – instal perpustakaan dan tambahkan ke proyek Anda. Anda dapat mengunduhnya dari [here](https://releases.aspose.com/words/java/).  
2. **Dokumen contoh** – untuk contoh kami akan menggunakan file bernama `Extract content.docx`. Letakkan file tersebut di folder yang dapat direferensikan dari kode Anda.

## Mengekstrak Konten Antara Node Tingkat‑Blok

```java
// Java code sample for extracting content between block-level nodes
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getLastSection().getChild(NodeType.PARAGRAPH, 2, true);
Table endTable = (Table) doc.getLastSection().getChild(NodeType.TABLE, 0, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endTable, true);
Collections.reverse(extractedNodes);
while (extractedNodes.size() > 0) {
    endTable.getParentNode().insertAfter((Node) extractedNodes.get(0), endTable);
    extractedNodes.remove(0);
}
doc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBlockLevelNodes.docx");
```

## Mengekstrak Konten Antara Bookmark

```java
// Java code sample for extracting content between bookmarks
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("Bookmark1");
BookmarkStart bookmarkStart = bookmark.getBookmarkStart();
BookmarkEnd bookmarkEnd = bookmark.getBookmarkEnd();
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.IncludingBookmark.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.WithoutBookmark.docx");
```

## Mengekstrak Konten Antara Rentang Komentar

```java
// Java code sample for extracting content between comment ranges
Document doc = new Document("Your Directory Path" + "Extract content.docx");
CommentRangeStart commentStart = (CommentRangeStart) doc.getChild(NodeType.COMMENT_RANGE_START, 0, true);
CommentRangeEnd commentEnd = (CommentRangeEnd) doc.getChild(NodeType.COMMENT_RANGE_END, 0, true);
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.IncludingComment.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.WithoutComment.docx");
```

## Mengekstrak Konten Antara Paragraf

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Mengekstrak Konten Antara Gaya Paragraf

```java
// Java code sample for extracting content between paragraph styles
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Mengekstrak Konten Antara Run

```java
// Java code sample for extracting content between runs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Mengekstrak Konten Menggunakan DocumentVisitor

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Mengekstrak Konten Menggunakan Field

```java
// Java code sample for extracting content using Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Mengekstrak Daftar Isi

```java
// Java code sample for extracting table of contents
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
for (Field field : doc.getRange().getFields()) {
    if (field.getType() == FieldType.FIELD_HYPERLINK) {
        FieldHyperlink hyperlink = (FieldHyperlink) field;
        if (hyperlink.getSubAddress() != null && hyperlink.getSubAddress().startsWith("_Toc")) {
            Paragraph tocItem = (Paragraph) field.getStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(tocItem.toString().trim());
            System.out.println("------------------");
            Bookmark bm = doc.getRange().getBookmarks().get(hyperlink.getSubAddress());
            Paragraph pointer = (Paragraph) bm.getBookmarkStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(pointer.toString());
        }
    }
}
```

## Mengekstrak Hanya Teks

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Mengekstrak Konten Berdasarkan Gaya

```java
// Java code sample for extracting content based on styles
Document doc = new Document("Your Directory Path" + "Styles.docx");
final String PARA_STYLE = "Heading 1";
final String RUN_STYLE = "Intense Emphasis";
ArrayList<Paragraph> paragraphs = paragraphsByStyleName(doc, PARA_STYLE);
System.out.println("Paragraphs with \"{paraStyle}\" styles ({paragraphs.Count}):");
for (Paragraph paragraph : paragraphs)
    System.out.println(paragraph.toString(SaveFormat.TEXT));
ArrayList<Run> runs = runsByStyleName(doc, RUN_STYLE);
System.out.println("\nRuns with \"{runStyle}\" styles ({runs.Count}):");
for (Run run : runs)
    System.out.println(run.getRange().getText());
}

public ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}

public ArrayList<Run> runsByStyleName(Document doc, String styleName) {
    ArrayList<Run> runsWithStyle = new ArrayList<Run>();
    NodeCollection runs = doc.getChildNodes(NodeType.RUN, true);
    for (Run run : (Iterable<Run>) runs) {
        if (run.getFont().getStyle().getName().equals(styleName))
            runsWithStyle.add(run);
    }
    return runsWithStyle;
}
```

## Mengekstrak dan Mencetak Teks

```java
// Java code sample for extracting and printing text
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Mengekstrak Gambar ke File

```java
// Java code sample for extracting images to files
Document doc = new Document("Your Directory Path" + "Images.docx");
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
int imageIndex = 0;
for (Shape shape : (Iterable<Shape>) shapes) {
    if (shape.hasImage()) {
        String imageFileName = MessageFormat.format("Image.ExportImages.{0}_{1}",
                imageIndex, FileFormatUtil.imageTypeToExtension(shape.getImageData().getImageType()));
        shape.getImageData().save("Your Directory Path" + imageFileName);
        imageIndex++;
    }
}
```

## Kesimpulan

Selamat! Anda kini memiliki kotak peralatan yang solid untuk **bagaimana cara mengekstrak teks menggunakan Aspose.Words** di Java. Dari node tingkat‑blok hingga bookmark, komentar, gaya, dan bahkan gambar, API memberikan kontrol yang sangat detail atas apa yang Anda ambil dari dokumen. Gunakan potongan kode ini sebagai dasar, sesuaikan dengan struktur file Anda sendiri, dan otomatisasikan proses ekstraksi pada kumpulan dokumen yang besar.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara mengekstrak konten dari dokumen yang dilindungi kata sandi?**  
J: Muat dokumen dengan konstruktor kata sandi: `new Document(path, new LoadOptions("password"))`, kemudian jalankan metode ekstraksi apa pun yang ditunjukkan di atas.

**T: Bisakah saya mengekstrak konten dari beberapa dokumen dalam satu kali proses?**  
J: Ya. Lakukan loop melalui daftar jalur file, buat instance `Document` untuk masing‑masing, dan terapkan logika ekstraksi yang sama di dalam loop.

**T: Apakah ada cara mengekstrak hanya teks yang terlihat (mengabaikan teks tersembunyi atau kode field)?**  
J: Gunakan `doc.getText()` untuk teks biasa yang terlihat. Untuk kontrol lebih, iterasi melalui node dan filter berdasarkan `NodeType.RUN` serta `Run.getFont().getHidden()`.

**T: Format apa saja yang dapat saya simpan untuk konten yang diekstrak?**  
J: Setelah mengekstrak, Anda dapat menyimpan `Document` sebagai DOCX, PDF, HTML, TXT, atau format apa pun yang didukung Aspose.Words melalui `doc.save("output.pdf")`.

**T: Apakah Aspose.Words mendukung ekstraksi konten dari file besar (ratusan MB)?**  
J: Ya, tetapi pertimbangkan menggunakan `LoadOptions` dengan `LoadFormat` dan `MemoryOptimization` untuk mengurangi konsumsi memori.

---

**Terakhir Diperbarui:** 2026-01-01  
**Diuji Dengan:** Aspose.Words untuk Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}