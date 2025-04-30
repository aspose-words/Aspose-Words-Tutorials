---
"description": "Tanuld meg, hogyan használd a strukturált dokumentumcímkéket (SDT) az Aspose.Words for Java programban ezzel az átfogó útmutatóval. Hozz létre, módosíts és köss SDT-ket egyéni XML adatokhoz."
"linktitle": "Strukturált dokumentumcímkék (SDT) használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Strukturált dokumentumcímkék (SDT) használata az Aspose.Words Java-ban"
"url": "/hu/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Strukturált dokumentumcímkék (SDT) használata az Aspose.Words Java-ban


## Bevezetés a strukturált dokumentumcímkék (SDT) használatába az Aspose.Words Java-ban

A strukturált dokumentumcímkék (SDT) az Aspose.Words for Java hatékony funkciói, amelyek lehetővé teszik strukturált tartalom létrehozását és kezelését a dokumentumokban. Ebben az átfogó útmutatóban végigvezetjük az SDT-k Aspose.Words for Java-ban való használatának különböző aspektusain. Akár kezdő, akár tapasztalt fejlesztő vagy, értékes betekintést és gyakorlati példákat találsz ebben a cikkben.

## Első lépések

Mielőtt belemerülnénk a részletekbe, állítsuk be a környezetünket, és hozzunk létre egy alapvető SDT-t. Ebben a szakaszban a következő témákat fogjuk tárgyalni:

- Új dokumentum létrehozása
- Strukturált dokumentumcímke hozzáadása
- A dokumentum mentése

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Hozzon létre egy CHECKBOX típusú strukturált dokumentumcímkét
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Mentse el a dokumentumot
doc.save("WorkingWithSDT.docx");
```

## Jelölőnégyzet SDT aktuális állapotának ellenőrzése

Miután hozzáadott egy jelölőnégyzet SDT-jét a dokumentumához, érdemes lehet programozottan ellenőrizni annak aktuális állapotát. Ez akkor lehet hasznos, ha felhasználói bevitelt kell érvényesítenie, vagy a jelölőnégyzet állapota alapján meghatározott műveleteket kell végrehajtania.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Jelölőnégyzet be van jelölve
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Tartalomvezérlők módosítása

Ebben a részben azt vizsgáljuk meg, hogyan módosíthatja a tartalomvezérlőket a dokumentumban. Háromféle tartalomvezérlőt fogunk megvizsgálni: sima szöveg, legördülő lista és kép.

### Egyszerű szöveges tartalomvezérlő módosítása

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Töröld a meglévő tartalmat
    sdtPlainText.removeAllChildren();

    // Új szöveg hozzáadása
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Legördülő lista tartalomvezérlőjének módosítása

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Válassza ki a második elemet a listából
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Képtartalom-vezérlés módosítása

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Cserélje ki a képet egy újra
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## ComboBox tartalomvezérlő létrehozása

A ComboBox tartalomvezérlő lehetővé teszi a felhasználók számára, hogy egy előre definiált listából válasszanak. Hozzunk létre egyet a dokumentumunkban.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Rich Text tartalomvezérlő használata

Rich Text tartalomvezérlők tökéletesek formázott szöveg dokumentumokhoz való hozzáadásához. Hozzunk létre egyet, és állítsuk be a tartalmát.

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

## Tartalomvezérlési stílusok beállítása

Stílusokat alkalmazhat a tartalomvezérlőkre a dokumentum vizuális megjelenésének javítása érdekében. Nézzük meg, hogyan állíthatja be egy tartalomvezérlő stílusát.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Egyéni stílus alkalmazása
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## SDT kötése egyéni XML adatokhoz

Bizonyos esetekben előfordulhat, hogy egy SDT-t egyéni XML-adatokhoz kell kötni a dinamikus tartalomgeneráláshoz. Nézzük meg, hogyan érhető el ez.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Egyéni XML-adatokhoz leképezett ismétlődő szakaszokat tartalmazó táblázat létrehozása

Az ismétlődő szakaszokat tartalmazó táblázatok rendkívül hasznosak lehetnek strukturált adatok megjelenítéséhez. Hozzunk létre egy ilyen táblázatot, és képezzük le egyéni XML-adatokra.

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

## Többszakaszos strukturált dokumentumcímkék használata

A strukturált dokumentumcímkék több szakaszra is kiterjedhetnek egy dokumentumban. Ebben a szakaszban azt vizsgáljuk meg, hogyan lehet több szakaszból álló SDT-kkel dolgozni.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Következtetés

Az Aspose.Words for Java strukturált dokumentumcímkéi sokoldalú módot kínálnak a dokumentumok tartalmának kezelésére és formázására. Akár sablonokat, űrlapokat, akár dinamikus dokumentumokat kell létrehoznia, az SDT-k biztosítják a szükséges rugalmasságot és kontrollt. Az ebben a cikkben bemutatott példák és irányelvek követésével kihasználhatja az SDT-k erejét a dokumentumfeldolgozási feladatok javítására.

## GYIK

### Mi a strukturált dokumentumcímkék (SDT-k) célja?

A strukturált dokumentumcímkék (SDT-k) a dokumentumokon belüli tartalom rendszerezésére és formázására szolgálnak, megkönnyítve a sablonok, űrlapok és strukturált dokumentumok létrehozását.

### Hogyan tudom ellenőrizni egy Checkbox SDT aktuális állapotát?

A Checkbox SDT aktuális állapotát a következővel ellenőrizheti: `setChecked` módszer, ahogy a cikkben is látható.

### Alkalmazhatok stílusokat a tartalomvezérlőkre?

Igen, stílusokat alkalmazhat a tartalomvezérlőkre, hogy testreszabhassa azok megjelenését a dokumentumban.

### Lehetséges egy SDT-t egyéni XML adatokhoz kötni?

Igen, egyéni XML adatokhoz köthetsz egy SDT-t, ami lehetővé teszi a dinamikus tartalomgenerálást és az adatleképezést.

### Mik azok az ismétlődő szakaszok az SDT-kben?

Az SDT-k ismétlődő szakaszai lehetővé teszik dinamikus adatokkal rendelkező táblázatok létrehozását, ahol a sorok a leképezett XML adatok alapján ismétlődhetnek.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}