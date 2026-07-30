---
date: 2026-01-01
description: Ismerje meg, hogyan lehet szöveget kinyerni az Aspose.Words for Java
  segítségével. Ez a lépésről‑lépésre útmutató több kinyerési technikát mutat be kész‑futtatható
  kódrészletekkel.
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Hogyan lehet szöveget kinyerni az Aspose.Words for Java segítségével
url: /hu/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan lehet szöveget kinyerni az Aspose.Words for Java segítségével

## Hogyan lehet szöveget kinyerni az Aspose.Words for Java segítségével

A dokumentumfeldolgozás világában a **hogyan lehet szöveget kinyerni az Aspose.Words segítségével** gyakori kérdés a Java fejlesztők körében. Akár egyszerű szöveget, táblázatokat, képeket, vagy specifikus elemeket, például könyvjelzőket vagy megjegyzéseket szeretne kinyerni, az Aspose.Words for Java gazdag API-t kínál, amely egyszerűvé teszi a feladatot. Ebben az útmutatóban több tucat kinyerési forgatókönyvet mutatunk be, elmagyarázzuk, miért fontos minden megközelítés, és kész‑kód mintákat biztosítunk, amelyeket egyszerűen beilleszthet a projektjébe.

## Gyors válaszok
- **Milyen könyvtárra van szükségem?** Aspose.Words for Java (töltse le a hivatalos oldalról).  
- **Kizárólag egyszerű szöveget tudok kinyerni?** Igen – használja a `Document.getText()` vagy a `DocumentBuilder` mezőkkel.  
- **Lehetőség van könyvjelzők közötti tartalom kinyerésére?** Természetesen, használja a `BookmarkStart`/`BookmarkEnd` kombinációt az `ExtractContentHelper`‑rel.  
- **Szükség van licencre a termeléshez?** Igen, kereskedelmi licenc szükséges a nem‑próba használathoz.  
- **Mely Java verziók támogatottak?** A Java 8 és újabb verziók teljesen kompatibilisek.

## Előfeltételek

1. **Aspose.Words for Java** – telepítse a könyvtárat és adja hozzá a projektjéhez. Letöltheti **[itt](https://releases.aspose.com/words/java/)**.  
2. **Minta dokumentum** – a példákhoz egy `Extract content.docx` nevű fájlt használunk. Helyezze el egy olyan mappába, amelyre a kódból hivatkozni tud.

## Tartalom kinyerése blokk‑szintű csomópontok között

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

## Tartalom kinyerése könyvjelzők között

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

## Tartalom kinyerése megjegyzés‑tartományok között

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

## Tartalom kinyerése bekezdések között

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Tartalom kinyerése bekezdés‑stílusok között

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

## Tartalom kinyerése futások (run) között

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

## Tartalom kinyerése DocumentVisitor használatával

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Tartalom kinyerése mező (Field) segítségével

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

## Tartalomjegyzék kinyerése

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

## Csak szöveg kinyerése

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Tartalom kinyerése stílusok alapján

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

## Szöveg kinyerése és kiírása

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

## Képek kinyerése fájlokba

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

## Összegzés

Gratulálunk! Most már egy átfogó eszköztárral rendelkezik a **hogyan lehet szöveget kinyerni az Aspose.Words segítségével** Java-ban. A blokk‑szintű csomópontoktól a könyvjelzőkön, megjegyzéseken, stílusokon és még a képeken át, az API finomhangolt vezérlést biztosít a dokumentumból kinyerhető tartalom felett. Használja ezeket a kódrészleteket kiindulási pontként, igazítsa őket saját fájlszerkezetéhez, és automatizálja a kinyerési folyamatot nagy dokumentumkészletek esetén.

## Gyakran Ismételt Kérdések

**Q: Hogyan tudok tartalmat kinyerni egy jelszóval védett dokumentumból?**  
A: Töltse be a dokumentumot a jelszó‑konstruktorral: `new Document(path, new LoadOptions("password"))`, majd futtassa a fent bemutatott bármelyik kinyerési módszert.

**Q: Lehet egyszerre több dokumentumból tartalmat kinyerni?**  
A: Igen. Iteráljon egy fájlútvonal‑listán, minden egyes elemhez hozza létre a `Document` példányt, és alkalmazza ugyanazt a kinyerési logikát a cikluson belül.

**Q: Van mód csak a látható szöveget kinyerni (elrejtett vagy mezőkódok figyelmen kívül hagyása)?**  
A: Használja a `doc.getText()`‑t a egyszerű látható szöveghez. Finomabb vezérléshez járjon végig a csomópontokon, és szűrje a `NodeType.RUN` és a `Run.getFont().getHidden()` alapján.

**Q: Milyen formátumokba menthetem a kinyert tartalmat?**  
A: Kinyerés után a `Document`‑et mentheti DOCX, PDF, HTML, TXT vagy bármely, az Aspose.Words által támogatott formátumba a `doc.save("output.pdf")` segítségével.

**Q: Az Aspose.Words képes nagy (több száz MB) fájlok tartalmát kinyerni?**  
A: Igen, de érdemes `LoadOptions`‑t használni a `LoadFormat`‑mal és a `MemoryOptimization`‑nal a memóriafogyasztás csökkentése érdekében.

---

**Utoljára frissítve:** 2026-01-01  
**Tesztelve a következővel:** Aspose.Words for Java 24.12  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}