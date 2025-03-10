---
title: Použití značek strukturovaného dokumentu (SDT) v Aspose.Words pro Javu
linktitle: Používání značek strukturovaného dokumentu (SDT)
second_title: Aspose.Words Java Document Processing API
description: Naučte se, jak používat Structured Document Tags (SDT) v Aspose.Words for Java, pomocí tohoto komplexního průvodce. Vytvářejte, upravujte a spojujte SDT s vlastními daty XML.
weight: 19
url: /cs/java/document-manipulation/using-structured-document-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití značek strukturovaného dokumentu (SDT) v Aspose.Words pro Javu


## Úvod do používání značek strukturovaného dokumentu (SDT) v Aspose.Words pro Javu

Structured Document Tags (SDT) jsou výkonnou funkcí v Aspose.Words for Java, která vám umožní vytvářet a manipulovat se strukturovaným obsahem ve vašich dokumentech. V tomto komplexním průvodci vás provedeme různými aspekty používání SDT v Aspose.Words for Java. Ať už jste začátečník nebo zkušený vývojář, v tomto článku najdete cenné postřehy a praktické příklady.

## Začínáme

Než se ponoříme do detailů, nastavíme naše prostředí a vytvoříme základní SDT. V této části se budeme zabývat následujícími tématy:

- Vytvoření nového dokumentu
- Přidání štítku strukturovaného dokumentu
- Ukládání dokumentu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vytvořte značku strukturovaného dokumentu typu CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Uložte dokument
doc.save("WorkingWithSDT.docx");
```

## Kontrola aktuálního stavu zaškrtávacího políčka SDT

Jakmile do dokumentu přidáte zaškrtávací políčko SDT, možná budete chtít programově zkontrolovat jeho aktuální stav. To může být užitečné, když potřebujete ověřit uživatelský vstup nebo provést konkrétní akce na základě stavu zaškrtávacího políčka.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Zaškrtávací políčko je zaškrtnuté
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Úprava ovládacích prvků obsahu

V této části prozkoumáme, jak upravit ovládací prvky obsahu v dokumentu. Probereme tři typy ovládacích prvků obsahu: Prostý text, Rozbalovací seznam a Obrázek.

### Úprava ovládacího prvku obsahu prostého textu

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Vymažte stávající obsah
    sdtPlainText.removeAllChildren();

    // Přidat nový text
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Úprava ovládacího prvku obsahu rozevíracího seznamu

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Vyberte druhou položku ze seznamu
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Úprava ovládání obsahu obrázku

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Nahraďte obrázek novým
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Vytvoření ovládacího prvku obsahu ComboBox

ComboBox Content Control umožňuje uživatelům vybírat z předdefinovaného seznamu možností. Vytvořme jeden v našem dokumentu.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Práce s řízením obsahu RTF

Ovládací prvky obsahu RTF jsou ideální pro přidávání formátovaného textu do vašich dokumentů. Pojďme si jeden vytvořit a nastavit jeho obsah.

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## Nastavení stylů ovládání obsahu

Na ovládací prvky obsahu můžete použít styly a vylepšit tak vizuální vzhled dokumentu. Podívejme se, jak nastavit styl ovládacího prvku obsahu.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Použijte vlastní styl
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Vazba SDT na vlastní data XML

V některých scénářích může být nutné svázat SDT s vlastními daty XML pro generování dynamického obsahu. Pojďme prozkoumat, jak toho dosáhnout.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Vytvoření tabulky s opakujícími se sekcemi namapovanými na uživatelská data XML

Tabulky s opakujícími se sekcemi mohou být velmi užitečné pro prezentaci strukturovaných dat. Vytvořme si takovou tabulku a namapujme ji na vlastní XML data.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## Práce s víceoddílovými strukturovanými štítky dokumentu

Značky strukturovaného dokumentu mohou zahrnovat více oddílů v dokumentu. V této části prozkoumáme, jak pracovat s vícedílnými SDT.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Závěr

Structured Document Tags v Aspose.Words pro Java poskytují všestranný způsob správy a formátování obsahu ve vašich dokumentech. Ať už potřebujete vytvářet šablony, formuláře nebo dynamické dokumenty, SDT nabízejí flexibilitu a kontrolu, kterou požadujete. Podle příkladů a pokynů uvedených v tomto článku můžete využít výkon SDT k vylepšení úloh zpracování dokumentů.

## FAQ

### Jaký je účel značek strukturovaných dokumentů (SDT)?

Značky strukturovaného dokumentu (SDT) slouží k uspořádání a formátování obsahu v dokumentech, což usnadňuje vytváření šablon, formulářů a strukturovaných dokumentů.

### Jak mohu zkontrolovat aktuální stav Checkbox SDT?

 Aktuální stav Checkbox SDT můžete zkontrolovat pomocí`setChecked` způsobem, jak je ukázáno v článku.

### Mohu použít styly na Ovládací prvky obsahu?

Ano, můžete použít styly na Ovládací prvky obsahu a přizpůsobit jejich vzhled v dokumentu.

### Je možné svázat SDT s vlastními daty XML?

Ano, SDT můžete svázat s vlastními daty XML, což umožňuje dynamické generování obsahu a mapování dat.

### Co jsou opakující se sekce v SDT?

Opakující se sekce v SDT umožňují vytvářet tabulky s dynamickými daty, kde se mohou řádky opakovat na základě mapovaných dat XML.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
