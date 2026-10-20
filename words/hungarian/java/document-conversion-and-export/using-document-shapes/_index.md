---
date: 2025-12-14
description: Ismerje meg, hogyan **illeszthet be képalakzatot** az Aspose.Words for
  Java-val. Ez az útmutató bemutatja, hogyan adhat hozzá alakzatokat, hozhat létre
  szövegdoboz alakzatokat, helyezhet el alakzatokat táblázatokban, állíthatja be az
  alakzat méretarányát, és adhat hozzá feliratkozó alakzatokat.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Dokumentum alakzatok használata az Aspose.Words for Java-ban
url: /hu/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan **képalakzat beillesztése** az Aspose.Words for Java-val

Ebben az átfogó útmutatóban megtudja, hogyan **illeszthet be képalakzat objektumokat** a Word dokumentumokba az Aspose.Words for Java segítségével. Akár jelentéseket, marketing anyagokat vagy interaktív űrlapokat készít, az alakzatok lehetővé teszik felhívások, gombok, szövegdobozok, vízjelek és még SmartArt hozzáadását. Lépésről lépésre végigvezetjük, elmagyarázzuk, miért használjon egy adott alakzatot, és kész‑kész kódrészleteket biztosítunk.

## Gyors válaszok
- **Mi a legfőbb módja egy alakzat hozzáadásának?** Használja a `DocumentBuilder.insertShape`‑t vagy hozzon létre egy `Shape` példányt és adja hozzá a dokumentumfához.  
- **Beilleszthetek képet alakzatként?** Igen – hívja a `builder.insertImage`‑t, majd kezelje a visszakapott `Shape`‑t, mint bármelyik másikat.  
- **Hogyan tartom meg egy alakzat méretarányát?** Állítsa be a `shape.setAspectRatioLocked(true)` vagy `false` értéket a szükségleteinek megfelelően.  
- **Lehetséges csoportosítani az alakzatokat?** Teljesen – csomagolja őket egy `GroupShape`‑be és szúrja be a csoportot egyetlen csomópontként.  
- **Működnek a SmartArt diagramok az Aspose.Words‑szal?** Igen, programozottan felismerheti és frissítheti a SmartArt alakzatokat.

## Mi az **képalakzat beillesztése**?
Az *image shape* (képalakzat) egy vizuális elem, amely raszter vagy vektor grafikai adatot tartalmaz egy Word dokumentumban. Az Aspose.Words‑ban egy képet egy `Shape` objektum képviseli, amely teljes ellenőrzést biztosít a méret, pozíció, forgatás és körbefuttatás felett.

## Miért használjunk alakzatokat a dokumentumokban?
- **Vizuális hatás:** Az alakzatok felhívják a figyelmet a kulcsfontosságú információkra.  
- **Interaktivitás:** Gombok és felhívások URL‑ekhez vagy könyvjelzőkhöz kapcsolhatók.  
- **Elrendezési rugalmasság:** A grafikákat pontosan helyezheti el abszolút vagy relatív koordinátákkal.  
- **Automatizálás:** Összetett elrendezéseket hozhat létre manuális szerkesztés nélkül.

## Előfeltételek
- Java Development Kit (JDK 8 vagy újabb)  
- Aspose.Words for Java könyvtár (letöltés a hivatalos oldalról)  
- Alapvető Java és objektum‑orientált programozási ismeretek  

A könyvtárat itt töltheti le: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Hogyan **adjunk hozzá alakzatot** – GroupShape beszúrása
A `GroupShape` lehetővé teszi, hogy több alakzatot egy egységként kezeljen. Ez hasznos több elem együttes mozgatásához vagy formázásához.

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

## Hozzon létre **szövegdoboz alakzatot**
A szövegdoboz egy olyan tároló, amely formázott szöveget tartalmazhat. Dinamikus megjelenés érdekében el is forgathatja.

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

## Állítsa be az **alakzat méretarányát**
Néha szükség van arra, hogy egy alakzat szabadon nyúljon, máskor pedig meg kell őrizni az eredeti arányait. A méretarány vezérlése egyszerű.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Helyezze el az **alakzatot táblázatban**
Alakzat beágyazása egy táblázat cellájába hasznos lehet jelentéselrendezésekhez. Az alábbi példa létrehoz egy táblázatot, majd egy vízjel‑stílusú alakzatot szúr be, amely az egész oldalt lefedi.

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
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
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

## Adj hozzá **felhívás alakzatot**
A felhívás alakzat tökéletes a megjegyzések vagy figyelmeztetések kiemelésére. Bár a fenti kód már bemutat egy `ACCENT_BORDER_CALLOUT_1`‑et, a `ShapeType`‑ot bármely más felhívás változatra cserélheti a tervezéshez illeszkedően.

## SmartArt alakzatok kezelése

### SmartArt alakzatok felismerése
A SmartArt diagramok programozottan azonosíthatók, lehetővé téve azok feldolgozását vagy cseréjét igény szerint.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt rajzok frissítése
Miután felismerte, frissítheti a SmartArt grafikákat, hogy tükrözzék az adatváltozásokat.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Gyakori problémák és tippek
- **Alakzat nem jelenik meg:** Győződjön meg róla, hogy az alakzat a célcsomópont után van beszúrva a `builder.insertNode` használatával.  
- **Váratlan forgatás:** Ne feledje, hogy a forgatás az alakzat középpontja körül történik; szükség esetén állítsa a `setLeft`/`setTop` értékeket.  
- **Méretarány zárolva:** Alapértelmezés szerint sok alakzat zárolja a méretarányt; a szabad nyújtáshoz hívja a `setAspectRatioLocked(false)`‑t.  
- **SmartArt felismerés sikertelen:** Ellenőrizze, hogy az Aspose.Words olyan verzióját használja, amely támogatja a SmartArt‑ot (v24+).

## Gyakran feltett kérdések

**Q: Mi az Aspose.Words for Java?**  
A: Az Aspose.Words for Java egy Java könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, módosítsanak és konvertáljanak Word dokumentumokat. Széles körű funkciókat és eszközöket kínál a különböző formátumú dokumentumok kezeléséhez.

**Q: Hogyan tölthetem le az Aspose.Words for Java‑t?**  
A: Az Aspose.Words for Java‑t letöltheti az Aspose weboldaláról a következő hivatkozáson: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: Mik a dokumentumalakzatok használatának előnyei?**  
A: A dokumentumalakzatok vizuális elemeket és interaktivitást adnak a dokumentumokhoz, így azok vonzóbbak és informatívabbak lesznek. Alakzatokkal felhívásokat, gombokat, képeket, vízjeleket és egyebeket hozhat létre, ezáltal javítva a felhasználói élményt.

**Q: Testreszabhatom az alakzatok megjelenését?**  
A: Igen, az alakzatok megjelenését testreszabhatja a méret, pozíció, forgatás és kitöltőszín tulajdonságainak módosításával. Az Aspose.Words for Java kiterjedt lehetőségeket biztosít az alakzatok testreszabásához.

**Q: Az Aspose.Words for Java kompatibilis a SmartArt‑dal?**  
A: Igen, az Aspose.Words for Java támogatja a SmartArt alakzatokat, lehetővé téve összetett diagramok és grafikák kezelését a dokumentumokban.

---

**Last Updated:** 2025-12-14  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}