---
category: general
date: 2026-07-16
description: hogyan szúrjunk be csoport alakzatot Java-ban az Aspose.Words használatával
  – adjunk hozzá téglalap alakzatot, állítsuk be az alakzat méreteit, és hozzunk létre
  színes téglalapot és kört.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: hu
lastmod: 2026-07-16
og_description: 'Hogyan szúrjunk be csoport alakzatot Java-ban: gyakorlati útmutató
  a téglalap alakzat hozzáadásához, az alakzat méreteinek beállításához, valamint
  színes téglalap és kör létrehozásához az Aspose.Words segítségével.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Csoport alakzat beillesztése Java-ban – Teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Hogyan szúrj be csoport alakzatot Java-ban – Teljes útmutató
url: /hu/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hogyan szúrjunk be csoport alakzatot Java‑ban – Teljes útmutató

Gondolkodtál már azon, **hogyan szúrjunk be csoport alakzatot** egy Word dokumentumba Java‑val? Nem vagy egyedül. Akár jelentésgenerátort, akár dinamikus szórólapkészítőt építesz, az alakzatok csoportosítása rendezetten tartja a megjelenést és a kódot is kezelhetővé teszi.

Ebben az útmutatóban végigvezetünk a pontos lépéseken, hogy **add rectangle shape**, **set shape dimensions**, és **create colored rectangle** valamint **create colored circle** használva az Aspose.Words könyvtárat. A végére egy futtatható programod lesz, amely egy .docx fájlt hoz létre egy kék téglalappal és egy piros körrel, melyek szép módon egy csoportba vannak csomagolva.

## Előfeltételek

- Java 17 (vagy bármely friss JDK) telepítve és konfigurálva.
- Maven vagy Gradle a függőségek kezeléséhez.
- Aspose.Words for Java 23.9 vagy újabb – letöltheted a Maven Central‑ról.
- Alapvető Java szintaxis ismeret – semmi különleges nem szükséges.

Ha valamelyik hiányzik, szerezd be a JDK‑t az Oracle weboldaláról, és add hozzá az Aspose.Words függőséget a `pom.xml`‑hez:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Most, hogy az alapok megvannak, vágjunk bele.

## how to insert group shape – Áttekintés

Az alapötlet egyszerű: hozz létre egy `Document`‑et, nyiss egy `DocumentBuilder`‑t, szúrj be egy **group shape**‑t, majd helyezz el egyedi alakzatokat (egy téglalapot és egy kört) ebben a csoportban. A csoport egy tárolóként működik, így később a mozgatása minden benne lévőt eltol, ami ideális összetett elrendezésekhez.

Az alábbiakban a teljes, azonnal futtatható kód található. Nyugodtan másold be egy új Java osztályba, amelynek neve `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro tip:** A `setLeft` és `setTop` értékek a csoport kiindulópontjához viszonyulnak, nem az oldalhoz. Ez később könnyedén lehetővé teszi a teljes csoport áthelyezését.

### Mi történt most?

1. **Document & Builder** – Létrehozunk egy üres Word fájlt és egy `DocumentBuilder`‑t, amely lehetővé teszi a tartalom beszúrását.
2. **Group Shape** – A `builder.insertGroupShape()` egy tárolót hoz létre. Gondolj rá úgy, mint egy mappára a rajzobjektumok számára.
3. **Blue Rectangle** – Létrehozunk egy `RECTANGLE` típusú `Shape`‑t, beállítjuk a méretét, pozícióját, és kék színnel töltjük – ez a **create colored rectangle** lépés.
4. **Red Circle** – Ugyanaz a minta, de `ELLIPSE`‑t használunk a tökéletes körhöz, majd pirosra töltjük – ez a **create colored circle** rész.
5. **Saving** – Végül mindent elmentünk a `GroupShapeDemo.docx`‑be.

Futtasd a programot (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) és nyisd meg a keletkezett fájlt. Bal oldalon egy kék téglalapot, jobb oldalon egy piros kört kell látnod, mindkettő egyetlen csoportdobozban rögzítve.

## Téglalap alakzat hozzáadása

Ha csak egy téglalapra van szükséged csoportosítás nélkül, kihagyhatod a `insertGroupShape()` hívást, és közvetlenül a dokumentum törzséhez fűzheted a téglalapot. A csoportosítás azonban rugalmasságot biztosít, hogy egyszerre több alakzatot mozgass, forgass vagy törölj.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Vedd észre, hogy itt a **add rectangle shape** logikát használtuk. A téglalap független objektumként jelenik meg az oldalon. A legtöbb valós esetben a csoportot szeretnéd, mivel megőrzi a relatív elhelyezkedést.

## Alakzat méreteinek beállítása

Amikor olyan metódusokat látsz, mint a `setWidth` és a `setHeight`, tartsd észben, hogy **pont**-ban (1/72 hüvelyk) várják az értékeket. Ha millimétert részesítesz előnyben, előbb konvertálj:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Ez a kódrészlet bemutatja a **set shape dimensions** egységkonverzióval – hasznos, ha a tervezési specifikációk metrikus egységeket tartalmazó UI makettből származnak.

## Színes téglalap létrehozása

Egy alakzat színezése olyan egyszerű, mint a `getFill().setForeColor()` meghívása. Bármilyen `java.awt.Color`‑t átadhatsz. Gradiensre van szükséged? Használd a `setForeColor`‑t a kezdőszínhez és a `setBackColor`‑t a végszínhez.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Ez egy gyors módja a **create colored rectangle** létrehozásának egy színátmenetes kitöltéssel a homogén szín helyett.

## Színes kör létrehozása

A körök egyszerűen olyan ellipszisek, amelyek szélessége és magassága egyenlő. Ugyanaz a színlogika érvényes:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Ha átlátszó kitöltésre van szükséged, állítsd be az alfa csatornát:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Most már elsajátítottad a **create colored circle** technikát.

## Dokumentum mentése

Az Aspose.Words számos formátumba képes exportálni: DOCX, PDF, HTML, PNG, bármit. Ebben a demóban a DOCX‑et használjuk, mivel tökéletesen megőrzi a vektoros alakzatokat.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

A `SaveFormat` módosítása elegendő ahhoz, hogy ugyanazt a csoportosított grafikát PDF‑ként is előállítsd.

## Gyakori hibák és elkerülésük

- **Elfelejtetted az alakzatot a csoporthoz adni?** Az alakzat megjelenik az oldalon, de nem mozog együtt a csoporttal. Mindig hívd meg a `group.appendChild(yourShape)`‑t.

## Mit érdemes legközelebb megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Java‑ban – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Űrlapmezők létrehozása és tartalom hozzáadása DocumentBuilder segítségével az Aspose.Words for Java‑ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Téglalap alakzat létrehozása Word‑ben az Aspose.Words‑szal – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}