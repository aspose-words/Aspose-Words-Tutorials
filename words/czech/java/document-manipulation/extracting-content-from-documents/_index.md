---
"description": "Naučte se, jak snadno extrahovat obsah z dokumentů pomocí Aspose.Words pro Javu. Náš podrobný návod a ukázky kódu vám celý proces zjednoduší."
"linktitle": "Extrakce obsahu z dokumentů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Extrakce obsahu z dokumentů v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/extracting-content-from-documents/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Extrakce obsahu z dokumentů v Aspose.Words pro Javu


## Úvod do extrakce obsahu z dokumentů v Aspose.Words pro Javu

Ve světě zpracování dokumentů je extrakce obsahu z dokumentů běžným požadavkem. Ať už potřebujete extrahovat text, tabulky, obrázky nebo konkrétní prvky dokumentu, Aspose.Words pro Javu poskytuje výkonné nástroje, které tento úkol usnadňují. V této komplexní příručce vás provedeme procesem extrakce obsahu z dokumentů pomocí Aspose.Words pro Javu. 

## Předpoklady

Než se pustíme do procesu extrakce, ujistěte se, že máte splněny následující předpoklady:

1. Aspose.Words pro Javu: Měli byste mít Aspose.Words pro Javu nainstalovaný a nastavený ve vašem vývojovém prostředí Java. Můžete si ho stáhnout z [zde](https://releases.aspose.com/words/java/).

2. Dokument pro extrakci obsahu: V této příručce použijeme vzorový dokument s názvem „Extrahovat obsah.docx“. Ujistěte se, že máte připravený podobný dokument pro extrakci.

## Extrakce obsahu mezi uzly na úrovni bloků

```java
// Ukázka kódu v Javě pro extrakci obsahu mezi uzly na úrovni bloků
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

## Extrakce obsahu mezi záložkami

```java
// Ukázka kódu v Javě pro extrakci obsahu mezi záložkami
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

## Extrakce obsahu mezi rozsahy komentářů

```java
// Ukázka kódu v Javě pro extrakci obsahu mezi rozsahy komentářů
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

## Extrakce obsahu mezi odstavci

```java
// Ukázka kódu v Javě pro extrakci obsahu mezi odstavci
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Extrakce obsahu mezi styly odstavců

```java
// Ukázka kódu v Javě pro extrakci obsahu mezi styly odstavců
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Extrakce obsahu mezi spuštěními

```java
// Ukázka kódu Java pro extrakci obsahu mezi spuštěními
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Extrakce obsahu pomocí DocumentVisitor

```java
// Ukázka kódu v Javě pro extrakci obsahu pomocí DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Extrakce obsahu pomocí pole

```java
// Ukázka kódu Java pro extrakci obsahu pomocí Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Extrahování obsahu

```java
// Ukázka kódu v Javě pro extrakci obsahu
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

## Extrahování pouze textu

```java
// Ukázka kódu v Javě pro extrakci pouze textu
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Extrakce obsahu na základě stylů

```java
// Ukázka kódu v Javě pro extrakci obsahu na základě stylů
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

## Extrakce a tisk textu

```java
// Ukázka kódu v Javě pro extrakci a tisk textu
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Extrahování obrázků do souborů

```java
// Ukázka kódu v Javě pro extrakci obrázků do souborů
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

## Závěr

Gratulujeme! Naučili jste se, jak extrahovat obsah z dokumentů pomocí Aspose.Words pro Javu. Tato příručka pokrývala různé techniky extrakce, včetně obsahu mezi uzly na úrovni bloků, záložkami, rozsahy komentářů, odstavci a dalšími. Nyní jste vybaveni k efektivní extrakci obsahu dokumentů ve vašich aplikacích Java.

## Často kladené otázky

### Jak extrahovat obsah z konkrétních sekcí dokumentu?

Chcete-li extrahovat obsah z konkrétních sekcí dokumentu, můžete identifikovat počáteční a koncové body sekcí a použít příslušné metody Aspose.Words pro Javu k extrakci obsahu mezi nimi.

### Mohu extrahovat obsah z dokumentů chráněných heslem?

Ano, Aspose.Words pro Javu nabízí funkce pro extrakci obsahu z dokumentů chráněných heslem. Heslo můžete zadat při otevírání dokumentu pomocí `Document` konstruktor třídy.

### Jak mohu extrahovat obsah a uložit ho v různých formátech, například jako prostý text nebo HTML?

Pomocí Aspose.Words pro Javu můžete extrahovat obsah z dokumentu a ukládat jej v různých formátech. Po extrahování obsahu můžete použít `Document` metody třídy pro uložení ve formátech jako prostý text, HTML nebo jiné.

### Existuje způsob, jak extrahovat obsah z konkrétních prvků dokumentu, jako jsou tabulky nebo obrázky?

Ano, pomocí Aspose.Words pro Javu můžete extrahovat obsah z konkrétních prvků dokumentu, jako jsou tabulky nebo obrázky. Identifikujte prvky, které chcete extrahovat, a poté použijte vhodné metody k extrakci jejich obsahu.

### Jak mohu automatizovat proces extrakce obsahu v mé aplikaci Java?

Chcete-li automatizovat proces extrakce obsahu ve vaší aplikaci Java, můžete si vytvořit vlastní kód založený na technikách popsaných v této příručce. Můžete také implementovat logiku pro iteraci více dokumentů a extrakci obsahu podle potřeby.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}