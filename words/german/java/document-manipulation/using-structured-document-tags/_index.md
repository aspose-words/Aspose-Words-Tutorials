---
title: Verwenden von Structured Document Tags (SDT) in Aspose.Words für Java
linktitle: Verwenden strukturierter Dokument-Tags (SDT)
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie in diesem umfassenden Handbuch, wie Sie Structured Document Tags (SDT) in Aspose.Words für Java verwenden. Erstellen, ändern und binden Sie SDTs an benutzerdefinierte XML-Daten.
weight: 19
url: /de/java/document-manipulation/using-structured-document-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Structured Document Tags (SDT) in Aspose.Words für Java


## Einführung in die Verwendung strukturierter Dokument-Tags (SDT) in Aspose.Words für Java

Structured Document Tags (SDT) sind eine leistungsstarke Funktion in Aspose.Words für Java, mit der Sie strukturierte Inhalte in Ihren Dokumenten erstellen und bearbeiten können. In diesem umfassenden Leitfaden führen wir Sie durch die verschiedenen Aspekte der Verwendung von SDTs in Aspose.Words für Java. Egal, ob Sie Anfänger oder erfahrener Entwickler sind, in diesem Artikel finden Sie wertvolle Einblicke und praktische Beispiele.

## Erste Schritte

Bevor wir in die Details eintauchen, richten wir unsere Umgebung ein und erstellen ein grundlegendes SDT. In diesem Abschnitt behandeln wir die folgenden Themen:

- Neues Dokument erstellen
- Hinzufügen eines strukturierten Dokument-Tags
- Speichern des Dokuments

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Erstellen Sie ein strukturiertes Dokument-Tag vom Typ CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Speichern des Dokuments
doc.save("WorkingWithSDT.docx");
```

## Überprüfen des aktuellen Status eines Kontrollkästchen-SDT

Nachdem Sie Ihrem Dokument ein Kontrollkästchen-SDT hinzugefügt haben, möchten Sie möglicherweise dessen aktuellen Status programmgesteuert überprüfen. Dies kann nützlich sein, wenn Sie Benutzereingaben validieren oder bestimmte Aktionen basierend auf dem Kontrollkästchenstatus ausführen müssen.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Kontrollkästchen ist aktiviert
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Ändern von Inhaltssteuerelementen

In diesem Abschnitt erfahren Sie, wie Sie Inhaltssteuerelemente in Ihrem Dokument ändern. Wir behandeln drei Arten von Inhaltssteuerelementen: Nur Text, Dropdown-Liste und Bild.

### Ändern des Inhaltssteuerelements für Nur-Text

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Löschen Sie den vorhandenen Inhalt
    sdtPlainText.removeAllChildren();

    // Neuen Text hinzufügen
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Ändern des Inhaltssteuerelements für Dropdown-Listen

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Wählen Sie das zweite Element aus der Liste
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Ändern der Bildinhaltssteuerung

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Ersetzen Sie das Bild durch ein neues
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Erstellen eines ComboBox-Inhaltssteuerelements

Mit einem ComboBox-Inhaltssteuerelement können Benutzer aus einer vordefinierten Liste von Optionen auswählen. Lassen Sie uns eines in unserem Dokument erstellen.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Arbeiten mit Rich Text Content Control

Rich-Text-Inhaltssteuerelemente eignen sich perfekt zum Hinzufügen formatierten Textes zu Ihren Dokumenten. Lassen Sie uns eines erstellen und seinen Inhalt festlegen.

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

## Festlegen von Inhaltssteuerelementstilen

Sie können Inhaltssteuerelementen Stile zuweisen, um die visuelle Darstellung Ihres Dokuments zu verbessern. Sehen wir uns an, wie Sie den Stil eines Inhaltssteuerelements festlegen.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Anwenden eines benutzerdefinierten Stils
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Binden eines SDT an benutzerdefinierte XML-Daten

In einigen Szenarien müssen Sie möglicherweise ein SDT an benutzerdefinierte XML-Daten binden, um dynamische Inhalte zu generieren. Sehen wir uns an, wie das geht.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Erstellen einer Tabelle mit sich wiederholenden Abschnitten, die benutzerdefinierten XML-Daten zugeordnet sind

Tabellen mit sich wiederholenden Abschnitten können für die Darstellung strukturierter Daten äußerst nützlich sein. Lassen Sie uns eine solche Tabelle erstellen und sie benutzerdefinierten XML-Daten zuordnen.

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

## Arbeiten mit strukturierten Dokument-Tags mit mehreren Abschnitten

Strukturierte Dokument-Tags können mehrere Abschnitte in einem Dokument umfassen. In diesem Abschnitt erfahren Sie, wie Sie mit mehrteiligen SDTs arbeiten.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Abschluss

Strukturierte Dokument-Tags in Aspose.Words für Java bieten eine vielseitige Möglichkeit, Inhalte in Ihren Dokumenten zu verwalten und zu formatieren. Egal, ob Sie Vorlagen, Formulare oder dynamische Dokumente erstellen müssen, SDTs bieten die Flexibilität und Kontrolle, die Sie benötigen. Indem Sie den Beispielen und Richtlinien in diesem Artikel folgen, können Sie die Leistungsfähigkeit von SDTs nutzen, um Ihre Dokumentverarbeitungsaufgaben zu verbessern.

## Häufig gestellte Fragen

### Was ist der Zweck von Structured Document Tags (SDTs)?

Strukturierte Dokument-Tags (SDTs) dienen der Organisation und Formatierung von Inhalten in Dokumenten und erleichtern das Erstellen von Vorlagen, Formularen und strukturierten Dokumenten.

### Wie kann ich den aktuellen Status eines Checkbox-SDT überprüfen?

 Sie können den aktuellen Status eines Checkbox-SDT überprüfen mit dem`setChecked` Methode, wie im Artikel gezeigt.

### Kann ich Stile auf Inhaltssteuerelemente anwenden?

Ja, Sie können Stile auf Inhaltssteuerelemente anwenden, um deren Erscheinungsbild im Dokument anzupassen.

### Ist es möglich, ein SDT an benutzerdefinierte XML-Daten zu binden?

Ja, Sie können ein SDT an benutzerdefinierte XML-Daten binden und so eine dynamische Inhaltsgenerierung und Datenzuordnung ermöglichen.

### Was sind sich wiederholende Abschnitte in SDTs?

Durch sich wiederholende Abschnitte in SDTs können Sie Tabellen mit dynamischen Daten erstellen, in denen Zeilen basierend auf den zugeordneten XML-Daten wiederholt werden können.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
