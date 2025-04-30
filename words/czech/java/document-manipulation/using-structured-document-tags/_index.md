---
"description": "Naučte se, jak používat tagy strukturovaných dokumentů (SDT) v Aspose.Words pro Javu s tímto komplexním průvodcem. Vytvářejte, upravujte a vazebejte SDT k vlastním XML datům."
"linktitle": "Používání tagů strukturovaných dokumentů (SDT)"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Používání tagů strukturovaných dokumentů (SDT) v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání tagů strukturovaných dokumentů (SDT) v Aspose.Words pro Javu


## Úvod do používání tagů strukturovaných dokumentů (SDT) v Aspose.Words pro Javu

Štítky strukturovaných dokumentů (SDT) jsou výkonnou funkcí v Aspose.Words pro Javu, která vám umožňuje vytvářet a manipulovat se strukturovaným obsahem ve vašich dokumentech. V této komplexní příručce vás provedeme různými aspekty používání SDT v Aspose.Words pro Javu. Ať už jste začátečník nebo zkušený vývojář, v tomto článku najdete cenné poznatky a praktické příklady.

## Začínáme

Než se ponoříme do detailů, nastavme si naše prostředí a vytvořme základní SDT. V této části se budeme zabývat následujícími tématy:

- Vytvoření nového dokumentu
- Přidání tagu strukturovaného dokumentu
- Uložení dokumentu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vytvořte tag strukturovaného dokumentu typu CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Uložit dokument
doc.save("WorkingWithSDT.docx");
```

## Kontrola aktuálního stavu zaškrtávacího políčka SDT

Jakmile do dokumentu přidáte zaškrtávací políčko SDT, můžete chtít programově zkontrolovat jeho aktuální stav. To může být užitečné, když potřebujete ověřit vstup uživatele nebo provést konkrétní akce na základě stavu zaškrtávacího políčka.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Zaškrtávací políčko je zaškrtnuto
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Úprava ovládacích prvků obsahu

V této části se podíváme na to, jak upravit ovládací prvky obsahu v dokumentu. Probereme tři typy ovládacích prvků obsahu: prostý text, rozevírací seznam a obrázek.

### Úprava ovládacího prvku obsahu prostého textu

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Vymazat stávající obsah
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

### Úprava ovládacího prvku obsahu obrázku

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

Ovládací prvek obsahu ComboBox umožňuje uživatelům vybírat z předdefinovaného seznamu možností. Vytvořme si jeden v našem dokumentu.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Práce s ovládacím prvkem obsahu RTF

Ovládací prvky obsahu RTF jsou ideální pro přidávání formátovaného textu do dokumentů. Pojďme si jeden vytvořit a nastavit jeho obsah.

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

## Nastavení stylů ovládacích prvků obsahu

Styly můžete použít na ovládací prvky obsahu pro vylepšení vizuálního vzhledu dokumentu. Podívejme se, jak nastavit styl ovládacího prvku obsahu.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Použití vlastního stylu
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Vazba SDT na vlastní XML data

V některých scénářích může být nutné pro generování dynamického obsahu navázat SDT na vlastní XML data. Pojďme se podívat, jak toho dosáhnout.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Vytvoření tabulky s opakujícími sekcemi namapovanými na vlastní XML data

Tabulky s opakujícími se sekcemi mohou být mimořádně užitečné pro prezentaci strukturovaných dat. Vytvořme si takovou tabulku a namapujeme ji na vlastní XML data.

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

## Práce s vícesekčními strukturovanými tagy dokumentů

Štítky strukturovaných dokumentů mohou zahrnovat více sekcí v dokumentu. V této části se podíváme na to, jak pracovat s vícesekčními tagy SDT.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Závěr

Strukturované tagy dokumentů v Aspose.Words pro Javu poskytují všestranný způsob správy a formátování obsahu ve vašich dokumentech. Ať už potřebujete vytvářet šablony, formuláře nebo dynamické dokumenty, SDT nabízejí flexibilitu a kontrolu, kterou potřebujete. Dodržováním příkladů a pokynů uvedených v tomto článku můžete využít sílu SDT ke zlepšení vašich úkolů zpracování dokumentů.

## Často kladené otázky

### Jaký je účel tagů strukturovaných dokumentů (SDT)?

Štítky strukturovaných dokumentů (SDT) slouží k organizaci a formátování obsahu v dokumentech, což usnadňuje vytváření šablon, formulářů a strukturovaných dokumentů.

### Jak mohu zkontrolovat aktuální stav SDT zaškrtávacího políčka?

Aktuální stav zaškrtávacího pole SDT můžete zkontrolovat pomocí `setChecked` metoda, jak je ukázáno v článku.

### Mohu použít styly na ovládací prvky obsahu?

Ano, na ovládací prvky obsahu můžete použít styly a přizpůsobit tak jejich vzhled v dokumentu.

### Je možné svázat SDT s vlastními XML daty?

Ano, SDT můžete navázat na vlastní XML data, což umožňuje dynamické generování obsahu a mapování dat.

### Co jsou opakující se sekce v SDT?

Opakující se sekce v SDT umožňují vytvářet tabulky s dynamickými daty, kde se řádky mohou opakovat na základě mapovaných XML dat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}