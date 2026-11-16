---
category: general
date: 2026-11-15
description: Hozzon létre téglalap alakzatot a Wordben Java-val, és tanulja meg, hogyan
  adjon hozzá alakzatokat a Wordhöz, állítsa be az alakzat méreteit, valamint hatékonyan
  mentse a Word-dokumentumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: hu
lastmod: 2026-11-15
og_description: Hozzon létre téglalap alakzatot egy Word dokumentumban Java-val. Tanulja
  meg, hogyan adjon hozzá alakzatokat a Wordhöz, állítsa be az alakzat méreteit, és
  mentse el a Word dokumentumot percek alatt.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Téglalap alakzat létrehozása Wordben Java‑val – lépésről‑lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Téglalap alakzat létrehozása egy Word-dokumentumban Java-val
url: /hu/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Word dokumentumban Java segítségével

Ha szükséged van **create rectangle shape** létrehozására egy Word fájlban, ez az útmutató pontosan megmutatja, hogyan teheted ezt Java-val. Meg fogod látni, hogyan **add shapes to Word**, a **set shape dimensions** szabályozását, és végül hogyan **save Word document** anélkül, hogy elhagynád az IDE-det.

Az ezt követő szakaszokban egy teljes, futtatható példát, minden sor magyarázatát és tippeket kapsz a gyakori buktatókhoz, például a méretezési problémákhoz és a dokumentum kompatibilitáshoz. Külső hivatkozásokra nincs szükség – csak az Aspose.Words for Java könyvtárra.

## Amit megtanulsz

* Hogyan inicializáld a `Document` és a `DocumentBuilder` objektumokat.
* Hogyan szúrj be egy **group shape**-t, és helyezz el benne egy téglalapot.
* Hogyan **define shape size**-t használva a `setWidth` és `setHeight` metódusokat.
* Hogyan **save Word document**-ot `.docx` formátumban.
* Edge‑case kezelése különböző oldalméretek és DPI beállítások esetén.

### Előfeltételek

* Java 17 vagy újabb (a kód Java 8-cal is lefordítható).
* Aspose.Words for Java 23.10 vagy újabb – letöltheted a Maven Centralból.
* Alapvető ismeretek a Java szintaxisról és az objektum‑orientált koncepciókról.

> **Pro tip:** Ha később több alakzat (például köröket vagy szövegdobozokat) szeretnél hozzáadni, tartsd őket ugyanabban a `GroupShape`-ben. Ez sokkal könnyebbé teszi a teljes gyűjtemény mozgatását, forgatását vagy formázását.

## 1. lépés: A dokumentum és a builder inicializálása

Az első lépés egy üres Word fájl és egy `DocumentBuilder` létrehozása, amely lehetővé teszi a tartalom írását.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* A `Document` az egész fájlt képviseli, míg a `DocumentBuilder` magas szintű metódusokat biztosít szöveg, táblázatok és **shapes** beszúrásához. A builder nélkül alacsony szintű csomópontokat kellene manuálisan kezelni.

## 2. lépés: Csoport alakzat (group shape) beszúrása több alakzat tárolásához

A **group shape** egy tárolóként működik; több alakzatot adhatsz hozzá, és később egyetlen objektumként kezelheted őket (például együtt mozgatva vagy forgatva).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use a group shape?* Ha később nyilakat, köröket vagy címkéket szeretnél hozzáadni a téglalap köré, a csoport mindent igazítva tart. Emellett leegyszerűsíti a **add shapes to Word** munkafolyamatot, mivel minden új alakzathoz csak egy `appendChild` hívásra van szükség.

## 3. lépés: A téglalap alakzat létrehozása

Most létrehozzuk a tényleges téglalapot, amely a csoporton belül lesz. A `Shape` konstruktorhoz szükség van a tulajdonos `Document`-ra és a kívánt alakzat típusára.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Why a rectangle?* A `ShapeType.RECTANGLE` a leggyakoribb primitív a szakaszok kiemeléséhez, helyőrzők létrehozásához vagy egyszerű UI makettek rajzolásához közvetlenül a Wordben.

## 4. lépés: A téglalap méretének meghatározása

A méretek beállítása az a pont, ahol a **set shape dimensions** fontos szerepet kap. Bármely, az Aspose.Words által támogatott mértékegységet használhatod; az alapértelmezett a pont (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Note:** Ha millimétert részesítesz előnyben, hívd a `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` metódust, ahol a `1.39 in ≈ 35 mm`. Ez bemutatja a **define shape size** rugalmasságát.

## 5. lépés: A téglalap hozzáadása a csoport alakzathoz

A téglalap hozzáfűzése az előzőleg létrehozott csoporthoz megjeleníti azt a dokumentumban.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

Ekkor a téglalap a csoport bal‑felső sarkában helyezkedik el. Később a `rectangle.setLeft(...)` és `rectangle.setTop(...)` metódusokkal mozgathatod, ha pontos elhelyezésre van szükség.

## 6. lépés: (Opcionális) A dokumentum mentése az eredmény megtekintéséhez

Végül írd a dokumentumot a lemezre. Ez a **save Word document** lépés, amely egy `.docx` fájlt hoz létre, amelyet megnyithatsz a Microsoft Word, a LibreOffice vagy a Google Docs segítségével.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

A program futtatása létrehozza a `RectangleShapeDemo.docx` fájlt, amely egyetlen téglalapot tartalmaz egy csoport alakzaton belül. A fájl megnyitása egy egyszerű fehér téglalapot mutat – pontosan a megadott mérettel.

### Várható kimenet

* Egy `RectangleShapeDemo.docx` nevű Word fájl.
* Az első bekezdésben egy csoport alakzat, amely egy 100 pt × 50 pt méretű téglalapot tartalmaz.
* Szöveg nincs hozzáadva, így a téglalap egy üres oldalon jelenik meg.

## Gyakori változatok és szélhelyzetek

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Different page size** (pl. A4) | Hívja meg a `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` metódust a shape beszúrása előtt. |
| **Higher DPI for printing** | Szorzold meg a szélességet/magasságot a kívánt DPI tényezővel, például `rectangle.setWidth(200 * 2);` a dupla felbontáshoz. |
| **Adding a text label inside the rectangle** | Hozz létre egy `TEXT_BOX` típusú `Shape`-t, állítsd be a `setWidth`/`setHeight` értékeket a téglalaphoz igazítva, majd add hozzá ugyanahhoz a `GroupShape`-hez. |
| **Rotating the rectangle** | Használd a `rectangle.setRotationAngle(45);` metódust a téglalap 45 fokos óramutató járásával megegyező forgatásához. |
| **Saving as PDF instead of DOCX** | Cseréld le a `document.save("output.docx");`-t `document.save("output.pdf");`-ra – ugyanaz az API működik PDF esetén is, megőrizve a téglalapot. |

## Pro tippek egy robusztus megvalósításhoz

1. **Reuse the builder** – a csoport alakzat beszúrása után folytathatod bekezdések vagy táblázatok hozzáadását új builder példány létrehozása nélkül.
2. **Dispose resources** – bár a Java szemétgyűjtője a legtöbb objektumot kezeli, a `document.close();` (ha stream-eket használsz) explicit hívása megakadályozza a fájl‑kezelő szivárgásokat.
3. **Validate dimensions** – a `setWidth`/`setHeight` hívása előtt győződj meg arról, hogy az értékek pozitívak; negatív értékek `IllegalArgumentException`-t dobnak.
4. **Version compatibility** – a kód az Aspose.Words 23.x és újabb verziókkal működik. Korábbi verziók esetén a `Shape.setSize(width, height)` használata szükséges lehet a különálló setterek helyett.

## Teljes, futtatható példa

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Result verification:** Nyisd meg a `output/RectangleShapeDemo.docx` fájlt a Microsoft Wordben. Egy a megadott méretű téglalapot kell látnod, amely az első oldal tetején középen helyezkedik el. Ha a téglalap túl kicsi, állítsd a `setWidth` és `setHeight`-nek átadott értékeket.

## Összegzés

Most már tudod, hogyan **create rectangle shape** egy Word fájlban Java-val, hogyan **add shapes to Word** egy `GroupShape` segítségével, hogyan **set shape dimensions** és **define shape size**, és végül hogyan **save Word document** a további terjesztéshez. Ugyanaz a minta más alakzat típusokra is működik, lehetővé téve összetett diagramok programozott létrehozását.

### Mi a következő?

* Fedezd fel a **add shapes to Word** lehetőséget körök, nyilak vagy szövegdobozok beszúrásával.
* Több alakzatot egyesíts egy `GroupShape`-be, és alkalmazz transzformációkat (forgatás, tükrözés).
* Készíts jelentéseket, amelyek diagramokat ágyaznak be alakzatként, majd **save Word document**-ot PDF-ként a megosztáshoz.

Nyugodtan kísérletezz a méretekkel, színekkel és elhelyezéssel, hogy a saját szituációdhoz illeszkedjen. Boldog kódolást!

## Mit érdemes még megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Téglalap alakzat létrehozása Java Word dokumentumban – Teljes lépésről‑lépésre útmutató](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Word dokumentum létrehozása Java – alakzat elrejtése és kitöltőszín beállítása](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}