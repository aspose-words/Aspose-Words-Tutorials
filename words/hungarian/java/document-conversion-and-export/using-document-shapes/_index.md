---
"description": "Engedd szabadjára a dokumentumalakzatok erejét az Aspose.Words for Java programban. Tanulj meg vizuálisan lebilincselő dokumentumokat létrehozni lépésről lépésre bemutatott példákkal."
"linktitle": "Dokumentumformák használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumformák használata az Aspose.Words Java-ban"
"url": "/hu/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumformák használata az Aspose.Words Java-ban


## Bevezetés a dokumentumalakzatok használatába az Aspose.Words Java-ban

Ebben az átfogó útmutatóban elmerülünk az Aspose.Words for Java dokumentumformák világában. Az alakzatok elengedhetetlen elemek a vizuálisan vonzó és interaktív dokumentumok létrehozásához. Akár feliratokat, gombokat, képeket vagy vízjeleket kell hozzáadnia, az Aspose.Words for Java biztosítja az ehhez szükséges eszközöket. Fedezzük fel lépésről lépésre, forráskódpéldákkal bemutatva, hogyan használhatja ezeket az alakzatokat.

## Dokumentumformák használatának első lépései

Mielőtt belevágnánk a kódba, állítsuk be a környezetünket. Győződjünk meg róla, hogy az Aspose.Words for Java integrálva van a projektünkbe. Ha még nem tetted meg, letöltheted az Aspose weboldaláról. [Aspose.Words letöltése Java-hoz](https://releases.aspose.com/words/java/)

## Alakzatok hozzáadása dokumentumokhoz

### Csoportalakzat beszúrása

Egy `GroupShape` lehetővé teszi több alakzat csoportosítását. Így hozhat létre és szúrhat be egyet `GroupShape`:

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

Szövegdoboz alakzat beszúrásához használhatja a `insertShape` a módszer, ahogy az az alábbi példában látható:

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

## Alakzattulajdonságok manipulálása

### Képarány kezelése

Beállíthatja, hogy egy alakzat képaránya zárolva legyen-e vagy sem. Így oldhatja fel egy alakzat képarányának feloldását:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Alakzat elhelyezése egy táblázatcellában

Ha egy alakzatot kell elhelyezned egy táblázatcellában, ezt a következő kóddal teheted meg:

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
watermark.isLayoutInCell(true); // Jelenítse meg az alakzatot a táblázatcellán kívül, ha az egy cellába kerül.
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

## SmartArt alakzatok használata

### SmartArt alakzatok felismerése

A következő kóddal észlelheti a SmartArt alakzatokat egy dokumentumban:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt-rajzok frissítése

A SmartArt-rajzok frissítéséhez egy dokumentumon belül használja a következő kódot:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Következtetés

Ebben az útmutatóban az Aspose.Words for Java dokumentumalakzatainak világát fedeztük fel. Megtanultad, hogyan adhatsz hozzá különféle alakzatokat a dokumentumokhoz, hogyan kezelheted a tulajdonságaikat, és hogyan dolgozhatsz SmartArt alakzatokkal. Ezzel a tudással könnyedén készíthetsz vizuálisan vonzó és interaktív dokumentumokat.

## GYIK

### Mi az Aspose.Words Java-hoz?

Az Aspose.Words for Java egy Java könyvtár, amely lehetővé teszi a fejlesztők számára Word dokumentumok programozott létrehozását, módosítását és konvertálását. Számos funkciót és eszközt kínál a különféle formátumú dokumentumokkal való munkához.

### Hogyan tudom letölteni az Aspose.Words programot Java-hoz?

Az Aspose.Words for Java programot letöltheted az Aspose weboldaláról a következő linkre kattintva: [Aspose.Words letöltése Java-hoz](https://releases.aspose.com/words/java/)

### Milyen előnyei vannak a dokumentumalakzatok használatának?

A dokumentumalakzatok vizuális elemeket és interaktivitást adnak a dokumentumokhoz, így azok vonzóbbak és informatívabbak. Az alakzatok segítségével feliratokat, gombokat, képeket, vízjeleket és egyebeket hozhat létre, ami javítja az általános felhasználói élményt.

### Testreszabhatom az alakzatok megjelenését?

Igen, testreszabhatja az alakzatok megjelenését olyan tulajdonságok módosításával, mint a méret, pozíció, forgatás és kitöltési szín. Az Aspose.Words for Java széleskörű lehetőségeket kínál az alakzatok testreszabásához.

### Kompatibilis az Aspose.Words for Java a SmartArt-tal?

Igen, az Aspose.Words for Java támogatja a SmartArt alakzatokat, lehetővé téve az összetett diagramok és grafikák használatát a dokumentumokban.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}