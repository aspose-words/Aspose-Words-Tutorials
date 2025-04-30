---
"description": "Leer hoe u Structured Document Tags (SDT) in Aspose.Words voor Java gebruikt met deze uitgebreide handleiding. Maak, wijzig en koppel SDT's aan aangepaste XML-gegevens."
"linktitle": "Het gebruik van gestructureerde documenttags (SDT)"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Het gebruik van gestructureerde documenttags (SDT) in Aspose.Words voor Java"
"url": "/nl/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Het gebruik van gestructureerde documenttags (SDT) in Aspose.Words voor Java


## Inleiding tot het gebruik van gestructureerde documenttags (SDT) in Aspose.Words voor Java

Structured Document Tags (SDT) zijn een krachtige functie in Aspose.Words voor Java waarmee u gestructureerde inhoud in uw documenten kunt maken en bewerken. In deze uitgebreide handleiding leiden we u door de verschillende aspecten van het gebruik van SDT's in Aspose.Words voor Java. Of u nu een beginner of een ervaren ontwikkelaar bent, u vindt waardevolle inzichten en praktische voorbeelden in dit artikel.

## Aan de slag

Voordat we in de details duiken, gaan we onze omgeving opzetten en een basis-SDT creëren. In deze sectie behandelen we de volgende onderwerpen:

- Een nieuw document maken
- Een gestructureerde documenttag toevoegen
- Het document opslaan

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Maak een gestructureerde documenttag van het type CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Sla het document op
doc.save("WorkingWithSDT.docx");
```

## De huidige status van een selectievakje SDT controleren

Nadat u een selectievakje-SDT aan uw document hebt toegevoegd, wilt u de huidige status mogelijk programmatisch controleren. Dit kan handig zijn wanneer u gebruikersinvoer moet valideren of specifieke acties moet uitvoeren op basis van de status van het selectievakje.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Selectievakje is aangevinkt
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Inhoudsbesturingselementen wijzigen

In deze sectie bespreken we hoe u inhoudselementen in uw document kunt wijzigen. We behandelen drie soorten inhoudselementen: platte tekst, vervolgkeuzelijst en afbeelding.

### Wijzigen van de inhoud van platte tekst

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // De bestaande inhoud wissen
    sdtPlainText.removeAllChildren();

    // Nieuwe tekst toevoegen
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Het wijzigen van de inhoud van de vervolgkeuzelijst

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Selecteer het tweede item uit de lijst
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Het wijzigen van de afbeeldinginhoudsbesturing

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Vervang de afbeelding door een nieuwe
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Een ComboBox-inhoudsbesturingselement maken

Met een ComboBox-inhoudsbesturingselement kunnen gebruikers kiezen uit een vooraf gedefinieerde lijst met opties. Laten we er een maken in ons document.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Werken met Rich Text Content Control

Rich Text Content Controls zijn perfect om opgemaakte tekst aan je documenten toe te voegen. Laten we er een maken en de inhoud ervan instellen.

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

## Inhoudsbesturingsstijlen instellen

U kunt stijlen toepassen op inhoudsbesturingselementen om de visuele weergave van uw document te verbeteren. Laten we eens kijken hoe u de stijl van een inhoudsbesturingselement instelt.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Een aangepaste stijl toepassen
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Een SDT binden aan aangepaste XML-gegevens

In sommige scenario's moet u mogelijk een SDT koppelen aan aangepaste XML-gegevens voor dynamische contentgeneratie. Laten we eens kijken hoe u dit kunt bereiken.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Een tabel maken met herhalende secties die zijn toegewezen aan aangepaste XML-gegevens

Tabellen met herhalende secties kunnen zeer nuttig zijn voor het presenteren van gestructureerde data. Laten we zo'n tabel maken en deze koppelen aan aangepaste XML-gegevens.

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

## Werken met gestructureerde documenttags met meerdere secties

Gestructureerde documenttags kunnen meerdere secties in een document beslaan. In deze sectie bespreken we hoe u met SDT's met meerdere secties kunt werken.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Conclusie

Gestructureerde documenttags in Aspose.Words voor Java bieden een veelzijdige manier om de inhoud van uw documenten te beheren en op te maken. Of u nu sjablonen, formulieren of dynamische documenten wilt maken, SDT's bieden de flexibiliteit en controle die u nodig hebt. Door de voorbeelden en richtlijnen in dit artikel te volgen, kunt u de kracht van SDT's benutten om uw documentverwerking te verbeteren.

## Veelgestelde vragen

### Wat is het doel van Structured Document Tags (SDT's)?

Met Structured Document Tags (SDT's) kunt u de inhoud van documenten organiseren en opmaken. Hierdoor kunt u gemakkelijker sjablonen, formulieren en gestructureerde documenten maken.

### Hoe kan ik de huidige status van een Checkbox SDT controleren?

U kunt de huidige status van een Checkbox SDT controleren met behulp van de `setChecked` methode, zoals gedemonstreerd in het artikel.

### Kan ik stijlen toepassen op inhoudsbesturingselementen?

Ja, u kunt stijlen toepassen op inhoudsbesturingselementen om hun weergave in het document aan te passen.

### Is het mogelijk om een SDT te koppelen aan aangepaste XML-gegevens?

Ja, u kunt een SDT koppelen aan aangepaste XML-gegevens, waardoor dynamische generatie van inhoud en gegevenstoewijzing mogelijk is.

### Wat zijn herhalende secties in SDT's?

Met herhalende secties in SDT's kunt u tabellen met dynamische gegevens maken, waarbij rijen kunnen worden herhaald op basis van de toegewezen XML-gegevens.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}