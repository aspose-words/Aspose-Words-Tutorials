---
"description": "Tanuld meg, hogyan kinyerhetsz tartalmat könnyedén dokumentumokból az Aspose.Words for Java segítségével. Lépésről lépésre útmutatónk és kódpéldáink leegyszerűsítik a folyamatot."
"linktitle": "Tartalom kinyerése dokumentumokból"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Tartalom kinyerése dokumentumokból az Aspose.Words for Java programban"
"url": "/hu/java/document-manipulation/extracting-content-from-documents/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tartalom kinyerése dokumentumokból az Aspose.Words for Java programban


## Bevezetés a dokumentumok tartalmának kinyerésébe az Aspose.Words for Java programban

dokumentumfeldolgozás világában a dokumentumokból való tartalom kinyerése gyakori követelmény. Akár szöveget, táblázatokat, képeket vagy meghatározott dokumentumelemeket kell kinyernie, az Aspose.Words for Java hatékony eszközöket kínál, amelyek megkönnyítik ezt a feladatot. Ebben az átfogó útmutatóban végigvezetjük Önt a dokumentumokból való tartalom kinyerésének folyamatán az Aspose.Words for Java használatával. 

## Előfeltételek

Mielőtt belevágnánk a kitermelési folyamatba, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

1. Aspose.Words for Java: Az Aspose.Words for Java-nak telepítve és beállítva kell lennie a Java fejlesztői környezetedben. Letöltheted innen: [itt](https://releases.aspose.com/words/java/).

2. Tartalom kinyeréséhez szükséges dokumentum: Ebben az útmutatóban egy „Tartalom kinyerése.docx” nevű mintadokumentumot fogunk használni. Győződjön meg róla, hogy van egy hasonló dokumentuma a kinyeréshez.

## Tartalom kinyerése blokk szintű csomópontok között

```java
// Java kódminta blokk szintű csomópontok közötti tartalom kinyerésére
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

## Tartalom kinyerése könyvjelzők között

```java
// Java kódminta könyvjelzők közötti tartalom kinyeréséhez
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

## Tartalom kinyerése a megjegyzéstartományok között

```java
// Java kódminta a megjegyzéstartományok közötti tartalom kinyeréséhez
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

## Tartalom kinyerése a bekezdések között

```java
// Java kódminta bekezdések közötti tartalom kinyerésére
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Tartalom kinyerése a bekezdésstílusok között

```java
// Java kódminta bekezdésstílusok közötti tartalom kinyeréséhez
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Tartalom kinyerése a futtatások között

```java
// Java kódminta tartalom kinyerésére a futtatások között
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Tartalom kinyerése a DocumentVisitor használatával

```java
// Java kódminta tartalom kinyeréséhez a DocumentVisitor használatával
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Tartalom kinyerése mező használatával

```java
// Java kódminta tartalom kinyerésére Field használatával
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Tartalomjegyzék kibontása

```java
// Java kódminta tartalomjegyzék kinyeréséhez
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

## Csak szöveg kinyerése

```java
// Java kódminta csak szöveg kinyeréséhez
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Tartalom kinyerése stílusok alapján

```java
// Java kódminta tartalom kinyeréséhez stílusok alapján
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

## Szöveg kinyerése és nyomtatása

```java
// Java kódminta szöveg kinyeréséhez és nyomtatásához
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Képek kibontása fájlokba

```java
// Java kódminta képek fájlokba kinyeréséhez
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

## Következtetés

Gratulálunk! Megtanultad, hogyan kinyerhetsz tartalmat dokumentumokból az Aspose.Words for Java segítségével. Ez az útmutató különféle kinyerési technikákat ismertetett, beleértve a blokk szintű csomópontok közötti tartalmat, könyvjelzőket, megjegyzéstartományokat, bekezdéseket és egyebeket. Most már felkészült vagy arra, hogy hatékonyan kezeld a dokumentumok tartalmának kinyerését Java alkalmazásaidban.

## GYIK

### Hogyan kinyerhetek tartalmat a dokumentum adott szakaszaiból?

A dokumentum adott szakaszaiból való tartalom kinyeréséhez azonosíthatja a szakaszok kezdő- és végpontjait, és a megfelelő Aspose.Words for Java metódusokkal kinyerheti a köztük lévő tartalmat.

### Ki tudom nyerni a tartalmat jelszóval védett dokumentumokból?

Igen, az Aspose.Words for Java funkciót biztosít a jelszóval védett dokumentumok tartalmának kinyerésére. A jelszót a dokumentum megnyitásakor megadhatja a következő használatával: `Document` osztály konstruktor.

### Hogyan tudom kinyerni a tartalmat, és hogyan menthetem el különböző formátumokban, például sima szövegként vagy HTML-ként?

Az Aspose.Words for Java segítségével kinyerhet tartalmat egy dokumentumból, és különböző formátumokban mentheti el. A tartalom kinyerése után használhatja a `Document` osztálymetódusokat, hogy olyan formátumokban mentse el, mint a sima szöveg, HTML vagy más.

### Van mód tartalom kinyerésére adott dokumentumelemekből, például táblázatokból vagy képekből?

Igen, az Aspose.Words for Java segítségével kinyerhet tartalmat adott dokumentumelemekből, például táblázatokból vagy képekből. Azonosítsa a kinyerni kívánt elemeket, majd a megfelelő metódusokkal kinyerje a tartalmukat.

### Hogyan automatizálhatom a tartalom kinyerésének folyamatát a Java alkalmazásomban?

tartalomkinyerési folyamat automatizálásához a Java-alkalmazásban egyéni kódot hozhat létre az ebben az útmutatóban leírt technikák alapján. Logikát is implementálhat, hogy több dokumentumon keresztül is végighaladhasson, és szükség szerint kinyerhesse a tartalmat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}