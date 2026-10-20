---
date: 2026-01-01
description: Aspose.Words for Java kullanarak metin nasıl çıkarılır öğrenin. Bu adım‑adım
  rehber, çalıştırmaya hazır kod örnekleriyle birden fazla çıkarma tekniğini gösterir.
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java Kullanarak Metin Nasıl Çıkarılır
url: /tr/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java Kullanarak Metin Nasıl Çıkarılır

## Aspose.Words for Java Kullanarak Metin Nasıl Çıkarılır

Belge işleme dünyasında, **Aspose.Words kullanarak metin nasıl çıkarılır** Java geliştiricileri için sık sorulan bir sorudur. Düz metin, tablolar, görüntüler ya da yer imleri veya yorumlar gibi belirli öğeler çekmeniz gerekse, Aspose.Words for Java işi basitleştiren zengin bir API sunar. Bu rehberde onlarca çıkarma senaryosunu inceleyecek, her yaklaşımın neden önemli olduğunu açıklayacak ve projenize ekleyebileceğiniz hazır‑kod örnekleri sağlayacağız.

## Hızlı Yanıtlar
- **Hangi kütüphane gerekiyor?** Aspose.Words for Java (resmi siteden indirin).  
- **Sadece düz metin çıkarabilir miyim?** Evet – `Document.getText()` ya da alanlarla `DocumentBuilder` kullanın.  
- **Yer imleri arasında çıkarım yapmak mümkün mü?** Kesinlikle, `ExtractContentHelper` ile `BookmarkStart`/`BookmarkEnd` kullanın.  
- **Üretim için lisansa ihtiyacım var mı?** Deneme dışı kullanım için ticari lisans gereklidir.  
- **Hangi Java sürümleri destekleniyor?** Java 8 ve üzeri tamamen uyumludur.

## Ön Koşullar

1. **Aspose.Words for Java** – kütüphaneyi kurun ve projenize ekleyin. [buradan](https://releases.aspose.com/words/java/) indirebilirsiniz.  
2. **Örnek bir belge** – örneklerde `Extract content.docx` adlı dosyayı kullanacağız. Kodu içinde referans verebileceğiniz bir klasöre yerleştirin.

## Blok‑Seviye Düğümler Arasında İçerik Çıkarma

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

## Yer İmleri Arasında İçerik Çıkarma

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

## Yorum Aralıkları Arasında İçerik Çıkarma

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

## Paragraflar Arasında İçerik Çıkarma

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Paragraf Stilleri Arasında İçerik Çıkarma

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

## Çalıştırmalar (Runs) Arasında İçerik Çıkarma

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

## DocumentVisitor Kullanarak İçerik Çıkarma

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Field Kullanarak İçerik Çıkarma

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

## İçindekiler Tablosu Çıkarma

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

## Yalnızca Metin Çıkarma

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Stile Göre İçerik Çıkarma

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

## Metni Çıkarma ve Yazdırma

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

## Görüntüleri Dosyalara Çıkarma

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

## Sonuç

Tebrikler! Artık Java'da **Aspose.Words kullanarak metin nasıl çıkarılır** konusunda sağlam bir araç setine sahipsiniz. Blok‑seviyeli düğümlerden yer imlerine, yorumlara, stillere ve hatta görüntülere kadar, API belge içinden neyi çıkaracağınız üzerinde ince kontrol sağlar. Bu kod parçacıklarını temel olarak kullanın, kendi dosya yapınıza uyarlayın ve büyük belge setlerinde çıkarım sürecini otomatikleştirin.

## Sık Sorulan Sorular

**S: Parola korumalı bir belgeden içeriği nasıl çıkarırım?**  
**C:** Belgeyi parola yapıcı ile yükleyin: `new Document(path, new LoadOptions("password"))`, ardından yukarıda gösterilen herhangi bir çıkarım yöntemini çalıştırın.

**S: Tek bir çalıştırmada birden fazla belgelerden içerik çıkarabilir miyim?**  
**C:** Evet. Dosya yolu listesini döngüye alın, her biri için bir `Document` oluşturun ve döngü içinde aynı çıkarım mantığını uygulayın.

**S: Gizli veya alan kodlarını yok sayarak yalnızca görünen metni çıkarma yolu var mı?**  
**C:** Düz görünen metin için `doc.getText()` kullanın. Daha fazla kontrol için düğümler arasında dolaşın ve `NodeType.RUN` ile `Run.getFont().getHidden()` koşuluna göre filtreleyin.

**S: Çıkarılan içeriği hangi formatlarda kaydedebilirim?**  
**C:** Çıkarma işleminden sonra bir `Document`'i DOCX, PDF, HTML, TXT veya Aspose.Words tarafından desteklenen herhangi bir formatta `doc.save("output.pdf")` ile kaydedebilirsiniz.

**S: Aspose.Words büyük (yüzlerce MB) dosyalardan içerik çıkarma desteği sunuyor mu?**  
**C:** Evet, ancak bellek tüketimini azaltmak için `LoadOptions` ile `LoadFormat` ve `MemoryOptimization` kullanmayı düşünün.

**Son Güncelleme:** 2026-01-01  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}