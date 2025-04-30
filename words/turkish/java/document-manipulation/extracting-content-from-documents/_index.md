---
"description": "Aspose.Words for Java kullanarak belgelerden içerikleri kolayca nasıl çıkaracağınızı öğrenin. Adım adım kılavuzumuz ve kod örneklerimiz süreci basitleştirir."
"linktitle": "Belgelerden İçerik Çıkarma"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belgelerden İçerik Çıkarma"
"url": "/tr/java/document-manipulation/extracting-content-from-documents/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belgelerden İçerik Çıkarma


## Java için Aspose.Words'de Belgelerden İçerik Çıkarmaya Giriş

Belge işleme dünyasında, belgelerden içerik çıkarmak yaygın bir gerekliliktir. Metin, tablo, resim veya belirli belge öğelerini çıkarmanız gerekip gerekmediğine bakılmaksızın, Aspose.Words for Java bu görevi kolaylaştırmak için güçlü araçlar sunar. Bu kapsamlı kılavuzda, Aspose.Words for Java kullanarak belgelerden içerik çıkarma sürecini adım adım anlatacağız. 

## Ön koşullar

Çıkarma işlemine başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

1. Java için Aspose.Words: Java geliştirme ortamınızda Java için Aspose.Words'ün yüklü ve ayarlanmış olması gerekir. Bunu şuradan indirebilirsiniz: [Burada](https://releases.aspose.com/words/java/).

2. İçeriği Çıkarmak İçin Bir Belge: Bu kılavuz için "İçeriği çıkar.docx" adlı örnek bir belge kullanacağız. Çıkarmak için benzer bir belgenizin hazır olduğundan emin olun.

## Blok Düzeyindeki Düğümler Arasında İçerik Çıkarma

```java
// Blok düzeyindeki düğümler arasında içerik çıkarmak için Java kod örneği
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

## Yer İşaretleri Arasındaki İçeriği Çıkarma

```java
// Yer imleri arasındaki içeriği çıkarmak için Java kod örneği
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

## Yorum Aralıkları Arasındaki İçeriği Çıkarma

```java
// Yorum aralıkları arasındaki içeriği çıkarmak için Java kod örneği
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

## Paragraflar Arası İçerik Çıkarma

```java
// Paragraflar arasındaki içeriği çıkarmak için Java kod örneği
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Paragraf Stilleri Arasındaki İçeriği Çıkarma

```java
// Paragraf stilleri arasındaki içeriği çıkarmak için Java kod örneği
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Çalıştırmalar Arasında İçerik Çıkarma

```java
// Çalıştırmalar arasında içerik çıkarmak için Java kod örneği
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
// DocumentVisitor kullanarak içerik çıkarmak için Java kod örneği
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Alan Kullanarak İçerik Çıkarma

```java
// Field kullanarak içerik çıkarmak için Java kod örneği
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## İçindekiler Tablosunu Çıkarma

```java
// İçindekiler tablosunu çıkarmak için Java kod örneği
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
// Yalnızca metin çıkarmak için Java kod örneği
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Stillere Dayalı İçerik Çıkarma

```java
// Stillere dayalı içerik çıkarmak için Java kod örneği
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

## Metin Çıkarma ve Yazdırma

```java
// Metin çıkarma ve yazdırma için Java kod örneği
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
// Görüntüleri dosyalara çıkarmak için Java kod örneği
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

## Çözüm

Tebrikler! Java için Aspose.Words kullanarak belgelerden içerik çıkarmayı öğrendiniz. Bu kılavuz, blok düzeyindeki düğümler, yer imleri, yorum aralıkları, paragraflar ve daha fazlası arasındaki içerik dahil olmak üzere çeşitli çıkarma tekniklerini ele aldı. Artık Java uygulamalarınızda belge içeriği çıkarmayı verimli bir şekilde halletmek için donanımlısınız.

## SSS

### Belirli belge bölümlerinden içerik nasıl çıkarabilirim?

Belirli belge bölümlerinden içerik çıkarmak için bölümlerin başlangıç ve bitiş noktalarını belirleyebilir ve aralarındaki içeriği çıkarmak için uygun Aspose.Words for Java yöntemlerini kullanabilirsiniz.

### Parola korumalı belgelerden içerik çıkarabilir miyim?

Evet, Aspose.Words for Java, parola korumalı belgelerden içerik çıkarma işlevi sağlar. Belgeyi açarken parolayı şu şekilde sağlayabilirsiniz: `Document` sınıf oluşturucusu.

### İçeriği nasıl çıkarabilirim ve düz metin veya HTML gibi farklı formatlarda nasıl kaydedebilirim?

Aspose.Words for Java kullanarak bir belgeden içerik çıkarabilir ve farklı biçimlerde kaydedebilirsiniz. İçeriği çıkardıktan sonra, `Document` düz metin, HTML veya diğerleri gibi formatlarda kaydetmek için sınıf yöntemleri.

### Tablolar veya resimler gibi belirli belge öğelerinden içerik çıkarmanın bir yolu var mı?

Evet, tablolar veya resimler gibi belirli belge öğelerinden Aspose.Words for Java kullanarak içerik çıkarabilirsiniz. Çıkarmak istediğiniz öğeleri belirleyin ve ardından içeriklerini çıkarmak için uygun yöntemleri kullanın.

### Java uygulamamda içerik çıkarma sürecini nasıl otomatikleştirebilirim?

Java uygulamanızda içerik çıkarma sürecini otomatikleştirmek için, bu kılavuzda açıklanan tekniklere dayalı özel kod oluşturabilirsiniz. Ayrıca, birden fazla belgede yineleme yapmak ve gerektiğinde içerik çıkarmak için mantığı uygulayabilirsiniz.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}