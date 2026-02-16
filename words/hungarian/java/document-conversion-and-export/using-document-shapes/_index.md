---
date: 2026-02-16
description: Tanulja meg, hogyan hozhat létre szövegdobozt, adhat hozzá vízjel szót,
  csoportosíthat több alakzatot, beállíthatja az alakzat méretarányát, és elhelyezheti
  az alakzatot egy táblázat cellájában az Aspose.Words for Java segítségével.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Hogyan hozhatunk létre szövegdobozt és használhatjuk a dokumentum alakzatokat
  az Aspose.Words for Java-ban
url: /hu/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

-backtop-button >}}

Now translate each piece.

We must keep code block placeholders unchanged.

Let's produce final translation.

Be careful with markdown formatting.

Also note "FAQ's" maybe "GYIK". Keep as heading but translate.

Let's produce.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentum alakzatok használata az Aspose.Words for Java-ban

## Bevezetés a dokumentum alakzatok használatába az Aspose.Words for Java-ban

Ebben az átfogó útmutatóban **meg fogod tanulni, hogyan hozhatsz létre text box** objektumokat és más erőteljes alakzatokat az Aspose.Words for Java segítségével. Az alakzatok lehetővé teszik, hogy a Word dokumentumokat felhívásokkal, gombokkal, vízjelekkel, SmartArt‑tal és még sok mással gazdagítsd – vizuálisan vonzóvá és interaktívvá téve őket. Valós példákon keresztül mutatjuk be a egyszerű text box beszúrásától a több alakzat csoportosításáig, az arányok beállításáig és az alakzatok táblázatcellákba helyezéséig tartó folyamatot.

## Gyors válaszok
- **Mi a leggyakoribb módja egy text box hozzáadásának?** Használd a `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)` metódust.
- **Csoportosíthatok több alakzatot?** Igen – hozd létre a `GroupShape`‑t, és fűzd hozzá a gyermekalakzatokat.
- **Hogyan zárolhatom vagy oldhatom fel egy alakzat arányait?** Hívd meg a `shape.setAspectRatioLocked(true/false)` metódust.
- **Lehet-e vízjelet hozzáadni egy alakzattal?** Természetesen – szúrj be egy `Shape`‑t `TEXT_PLAIN_TEXT` típussal, és állítsd be a kitöltést/keretet.
- **Működnek a SmartArt diagramok az Aspose.Words‑ben?** Igen – detektáld a `shape.hasSmartArt()` metódussal, és frissítsd a `shape.updateSmartArtDrawing()` segítségével.

## Mi az a text box és miért hozunk létre text box alakzatokat?

A text box egy olyan tároló, amely formázott szöveget, képeket vagy más alakzatokat tartalmazhat. A **text box létrehozása** az automatizálás során lehetővé teszi, hogy lebegő tartalmat helyezz el a lap bármely pontján, ami tökéletes megjegyzésekhez, felhívásokhoz vagy díszítő elemekhez anélkül, hogy megváltoztatná a dokumentum fő áramlását.

## Hogyan adjunk hozzá alakzatot

Mielőtt a kódba merülnél, győződj meg róla, hogy az Aspose.Words for Java hivatkozásként szerepel a projektedben. Ha még nem adtad hozzá, töltsd le a könyvtárat a hivatalos oldalról:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Alakzatok hozzáadása a dokumentumokhoz

## Hogyan csoportosítsunk több alakzatot

A `GroupShape` lehetővé teszi, hogy több egyedi alakzatot egy egységként kezelj – hasznos azok mozgatásához vagy forgatásához együtt.

### GroupShape beszúrása

Az alábbiakban egy komplett példát láthatsz, amely létrehoz egy csoportot, két különböző alakzatot ad hozzá, majd a csoportot beilleszti a dokumentumba.

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

## Hogyan hozzunk létre egy text box‑ot (create text box)

### Text Box alakzat beszúrása

Az `insertShape` metódus egyszerűvé teszi a text box hozzáadását. Az alábbi példa két módot mutat be a text box pozicionálására és forgatására.

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

## Hogyan állítsuk be az alakzat arányait

### Arányok kezelése

Néha szükség van arra, hogy egy alakzat nyúljon anélkül, hogy megtartaná eredeti arányait. Az alábbi kódrészlet bemutatja, hogyan oldhatod fel egy kép alakzat arányzárát.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Hogyan helyezzünk el alakzatot egy táblázatcellában

### Alakzat elhelyezése egy táblázatcellában

Az alábbi lépésről‑lépésre példában egy táblázatot építünk fel, majd egy vízjel alakzatot szúrunk be, amely a laphoz viszonyítva helyezkedik el, de cellába is beilleszthető.

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

## Munka SmartArt alakzatokkal

### SmartArt alakzatok detektálása

Programozottan megtalálhatod a SmartArt objektumokat egy dokumentumban a `hasSmartArt()` metódus használatával.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt rajzok frissítése

Miután megtaláltad a SmartArt alakzatokat, a `updateSmartArtDrawing()` segítségével frissítheted a belső rajzadatokat.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Összegzés

Ebben az útmutatóban áttekintettük, hogyan **hozhatsz létre text box** objektumokat, csoportosíthatsz több alakzatot, állíthatod be az arányokat, ágyazhatsz be alakzatokat táblázatcellákba, adhatsz hozzá vízjeleket, és dolgozhatsz SmartArt diagramokkal az Aspose.Words for Java segítségével. Ezek a technikák lehetővé teszik, hogy programozottan gazdag formázású, interaktív Word dokumentumokat építs.

## GYIK

### Mi az Aspose.Words for Java?

Az Aspose.Words for Java egy Java könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, módosítsanak és konvertáljanak Word dokumentumokat. Széles körű funkciókat és eszközöket kínál a különböző formátumú dokumentumok kezeléséhez.

### Hogyan tölthetem le az Aspose.Words for Java‑t?

Az Aspose.Words for Java‑t az Aspose weboldaláról töltheted le a következő hivatkozáson keresztül: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Mik az előnyei a dokumentum alakzatok használatának?

A dokumentum alakzatok vizuális elemeket és interaktivitást adnak a dokumentumaidhoz, így azok vonzóbbak és informatívabbak lesznek. Alakzatokkal felhívásokat, gombokat, képeket, vízjeleket és még sok mást hozhatsz létre, javítva a felhasználói élményt.

### Testreszabhatom az alakzatok megjelenését?

Igen, az alakzatok megjelenését testreszabhatod a tulajdonságaik, például méret, pozíció, forgatás és kitöltőszín módosításával. Az Aspose.Words for Java kiterjedt lehetőségeket biztosít az alakzatok testreszabásához.

### Az Aspose.Words for Java kompatibilis a SmartArt‑dal?

Igen, az Aspose.Words for Java támogatja a SmartArt alakzatokat, lehetővé téve komplex diagramok és grafikák kezelését a dokumentumokban.

## Gyakran Ismételt Kérdések

**Q: Kombinálhatok egy text box‑ot képpel ugyanabban az alakzatban?**  
A: Igen. Szúrj be egy képet a text box alakzatba a `builder.insertImage()` használatával a forma létrehozása után, majd állítsd be a kívánt elrendezést.

**Q: Hogyan biztosíthatom, hogy a vízjel a dokumentum minden tartalma mögött jelenjen meg?**  
A: Állítsd be az alakzat `WrapType` értékét `NONE`‑ra, és a `RelativeHorizontalPosition` valamint a `RelativeVerticalPosition` értékét `PAGE`‑re. Így a vízjel a fő áramlás mögött helyezkedik el.

**Q: Lehet-e animálni egy csoportosított alakzatot a Word‑ben?**  
A: Bár az Aspose.Words képes alakzatok létrehozására és csoportosítására, az animációs funkciók nem támogatottak, mivel azok a Word felhasználói felületének képességeire támaszkodnak.

**Q: Mely Aspose.Words verzió szükséges a SmartArt támogatásához?**  
A: A SmartArt detektálás és frissítés a Aspose.Words 20.9 for Java verziótól és újabbaktól érhető el.

**Q: Kezeli-e a könyvtár a sok alakzatot tartalmazó nagy dokumentumokat hatékonyan?**  
A: Igen. Használd a `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` vagy magasabb beállítást a sok alakzatot tartalmazó dokumentumok teljesítményének javításához.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}