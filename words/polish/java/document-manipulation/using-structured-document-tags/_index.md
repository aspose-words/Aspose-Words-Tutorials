---
"description": "Dowiedz się, jak używać Structured Document Tags (SDT) w Aspose.Words for Java dzięki temu kompleksowemu przewodnikowi. Twórz, modyfikuj i wiąż SDT z niestandardowymi danymi XML."
"linktitle": "Korzystanie ze strukturalnych znaczników dokumentu (SDT)"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Korzystanie ze strukturalnych znaczników dokumentu (SDT) w Aspose.Words dla języka Java"
"url": "/pl/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Korzystanie ze strukturalnych znaczników dokumentu (SDT) w Aspose.Words dla języka Java


## Wprowadzenie do korzystania ze strukturalnych znaczników dokumentu (SDT) w Aspose.Words dla języka Java

Structured Document Tags (SDT) to potężna funkcja w Aspose.Words for Java, która umożliwia tworzenie i manipulowanie ustrukturyzowaną zawartością w dokumentach. W tym kompleksowym przewodniku przeprowadzimy Cię przez różne aspekty korzystania z SDT w Aspose.Words for Java. Niezależnie od tego, czy jesteś początkującym, czy doświadczonym programistą, w tym artykule znajdziesz cenne spostrzeżenia i praktyczne przykłady.

## Pierwsze kroki

Zanim przejdziemy do szczegółów, skonfigurujmy nasze środowisko i utwórzmy podstawowy SDT. W tej sekcji omówimy następujące tematy:

- Tworzenie nowego dokumentu
- Dodawanie strukturalnego znacznika dokumentu
- Zapisywanie dokumentu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Utwórz znacznik dokumentu strukturalnego typu POLE WYBORU
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Zapisz dokument
doc.save("WorkingWithSDT.docx");
```

## Sprawdzanie bieżącego stanu pola wyboru SDT

Po dodaniu pola wyboru SDT do dokumentu możesz chcieć sprawdzić jego aktualny stan programowo. Może to być przydatne, gdy musisz zweryfikować dane wejściowe użytkownika lub wykonać określone czynności na podstawie stanu pola wyboru.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Pole wyboru jest zaznaczone
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Modyfikowanie elementów sterujących zawartością

W tej sekcji przyjrzymy się sposobom modyfikowania kontrolek zawartości w dokumencie. Omówimy trzy typy kontrolek zawartości: Zwykły tekst, Lista rozwijana i Obraz.

### Modyfikowanie kontroli zawartości zwykłego tekstu

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Wyczyść istniejącą zawartość
    sdtPlainText.removeAllChildren();

    // Dodaj nowy tekst
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Modyfikowanie kontroli zawartości listy rozwijanej

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Wybierz drugą pozycję z listy
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Modyfikowanie kontroli zawartości obrazu

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Zastąp obraz nowym
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Tworzenie kontrolki zawartości ComboBox

Kontrolka ComboBox Content Control pozwala użytkownikom wybierać z predefiniowanej listy opcji. Utwórzmy jedną w naszym dokumencie.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Praca z kontrolą zawartości w formacie Rich Text

Kontrolki zawartości Rich Text są idealne do dodawania sformatowanego tekstu do dokumentów. Utwórzmy jedną i ustawmy jej zawartość.

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

## Ustawianie stylów kontroli zawartości

Możesz stosować style do kontrolek zawartości, aby poprawić wygląd wizualny dokumentu. Zobaczmy, jak ustawić styl kontrolki zawartości.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Zastosuj niestandardowy styl
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Wiązanie SDT z niestandardowymi danymi XML

W niektórych scenariuszach może być konieczne powiązanie SDT z niestandardowymi danymi XML w celu dynamicznego generowania treści. Przyjrzyjmy się, jak to osiągnąć.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Tworzenie tabeli z powtarzającymi się sekcjami mapowanymi na niestandardowe dane XML

Tabele z powtarzającymi się sekcjami mogą być niezwykle przydatne do prezentowania ustrukturyzowanych danych. Utwórzmy taką tabelę i zmapujmy ją na niestandardowe dane XML.

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

## Praca z wielosekcyjnymi strukturalnymi znacznikami dokumentów

Ustrukturyzowane znaczniki dokumentu mogą obejmować wiele sekcji w dokumencie. W tej sekcji przyjrzymy się, jak pracować z wielosekcyjnymi SDT.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Wniosek

Ustrukturyzowane znaczniki dokumentów w Aspose.Words for Java zapewniają wszechstronny sposób zarządzania i formatowania treści w dokumentach. Niezależnie od tego, czy musisz tworzyć szablony, formularze czy dynamiczne dokumenty, SDT oferują elastyczność i kontrolę, których potrzebujesz. Postępując zgodnie z przykładami i wskazówkami podanymi w tym artykule, możesz wykorzystać moc SDT, aby ulepszyć zadania przetwarzania dokumentów.

## Najczęściej zadawane pytania

### Jaki jest cel stosowania strukturalnych znaczników dokumentów (SDT)?

Ustrukturyzowane Tagi Dokumentów (SDT) służą do organizowania i formatowania treści w dokumentach, dzięki czemu tworzenie szablonów, formularzy i ustrukturyzowanych dokumentów staje się łatwiejsze.

### Jak mogę sprawdzić aktualny stan Checkbox SDT?

Aktualny stan pola wyboru SDT można sprawdzić za pomocą `setChecked` metoda, jak pokazano w artykule.

### Czy mogę stosować style do kontrolek zawartości?

Tak, możesz stosować style do kontrolek zawartości, aby dostosować ich wygląd w dokumencie.

### Czy można powiązać SDT z niestandardowymi danymi XML?

Tak, można powiązać SDT z niestandardowymi danymi XML, co umożliwia dynamiczne generowanie treści i mapowanie danych.

### Czym są sekcje powtarzalne w SDT?

Powtarzalne sekcje w SDT umożliwiają tworzenie tabel z dynamicznymi danymi, w których wiersze mogą być powtarzane na podstawie mapowanych danych XML.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}