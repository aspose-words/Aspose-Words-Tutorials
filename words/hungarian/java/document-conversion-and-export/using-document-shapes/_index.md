---
title: Dokumentum alakzatok használata az Aspose.Words for Java programban
linktitle: Dokumentumformák használata
second_title: Aspose.Words Java Document Processing API
description: Fedezze fel a dokumentumalakzatok erejét az Aspose.Words for Java programban. Ismerje meg, hogyan hozhat létre vizuálisan lebilincselő dokumentumokat lépésről lépésre példákkal.
weight: 14
url: /hu/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentum alakzatok használata az Aspose.Words for Java programban


## Bevezetés a dokumentumalakzatok használatába az Aspose.Words for Java programban

Ebben az átfogó útmutatóban elmélyülünk az Aspose.Words for Java dokumentumformáinak világában. A formák elengedhetetlenek a tetszetős és interaktív dokumentumok létrehozásához. Függetlenül attól, hogy feliratokat, gombokat, képeket vagy vízjeleket kell hozzáadnia, az Aspose.Words for Java eszközöket biztosít a hatékony végrehajtáshoz. Fedezze fel, hogyan használhatja ezeket az alakzatokat lépésről lépésre forráskód-példákkal.

## Ismerkedés a dokumentumalakzatokkal

 Mielőtt belevágnánk a kódba, állítsuk be a környezetünket. Győződjön meg arról, hogy az Aspose.Words for Java integrálva van a projektjébe. Ha még nem tette meg, letöltheti az Aspose webhelyéről[Töltse le az Aspose.Words for Java programot](https://releases.aspose.com/words/java/)

## Alakzatok hozzáadása a dokumentumokhoz

### Csoportalakzat beszúrása

 A`GroupShape` lehetővé teszi több alakzat csoportosítását. Így hozhat létre és illeszthet be a`GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### Szövegdoboz alakzat beszúrása

 Szövegdoboz alakzat beszúrásához használhatja a`insertShape` módszer az alábbi példában látható módon:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Az alak tulajdonságainak manipulálása

### Képarány kezelése

Beállíthatja, hogy egy alakzat képaránya zárolva legyen-e vagy sem. A következőképpen oldhatja fel egy alakzat képarányát:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Alakzat elhelyezése táblázatcellában

Ha egy alakzatot el kell helyeznie egy táblázat cellájába, ezt a következő kóddal érheti el:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Az alakzat megjelenítése a táblázatcellán kívül, ha cellába kerül.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Munkavégzés SmartArt alakzatokkal

### SmartArt alakzatok észlelése

A SmartArt alakzatokat a következő kód segítségével észlelheti egy dokumentumban:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt rajzok frissítése

A SmartArt-rajzok dokumentumon belüli frissítéséhez használja a következő kódot:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Következtetés

Ebben az útmutatóban az Aspose.Words for Java dokumentumformáinak világát fedeztük fel. Megtanulta, hogyan adhat hozzá különféle alakzatokat a dokumentumokhoz, hogyan kezelheti tulajdonságaikat, és hogyan dolgozhat SmartArt-alakzatokkal. Ezzel a tudással könnyedén készíthet tetszetős és interaktív dokumentumokat.

## GYIK

### Mi az Aspose.Words for Java?

Az Aspose.Words for Java egy Java-könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, módosítását és konvertálását. Funkciók és eszközök széles skáláját kínálja a különféle formátumú dokumentumok kezeléséhez.

### Hogyan tölthetem le az Aspose.Words for Java programot?

 Az Aspose.Words for Java fájlt az Aspose webhelyéről töltheti le, ha követi ezt a hivatkozást:[Töltse le az Aspose.Words for Java programot](https://releases.aspose.com/words/java/)

### Milyen előnyei vannak a dokumentumformák használatának?

A dokumentumformák vizuális elemeket és interaktivitást adnak a dokumentumokhoz, így vonzóbbá és informatívabbá teszik azokat. Az alakzatokkal kiemeléseket, gombokat, képeket, vízjeleket és egyebeket hozhat létre, javítva az általános felhasználói élményt.

### Testreszabhatom az alakzatok megjelenését?

Igen, testreszabhatja az alakzatok megjelenését a tulajdonságaik, például a méret, a helyzet, az elforgatás és a kitöltési szín módosításával. Az Aspose.Words for Java kiterjedt lehetőségeket kínál az alakzatok testreszabásához.

### Az Aspose.Words for Java kompatibilis a SmartArt-tal?

Igen, az Aspose.Words for Java támogatja a SmartArt alakzatokat, lehetővé téve a dokumentumok összetett diagramjaival és grafikáival való munkát.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
