---
category: general
date: 2026-08-14
description: Csoportosítsa az alakzatokat a Wordben Java-val az Aspose.Words segítségével.
  Tanulja meg, hogyan hozhat létre téglalap alakzatot, állíthatja be az alakzat méreteit,
  és csoportosíthat több alakzatot egy üres Word dokumentumban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: hu
lastmod: 2026-08-14
og_description: Csoportosítsa az alakzatokat a Wordben az Aspose.Words for Java segítségével.
  Hozzon létre egy üres Word-dokumentumot, készítsen téglalap alakzatot, állítsa be
  az alakzat méreteit, és percek alatt csoportosítson több alakzatot.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Alakzatok csoportosítása a Wordben – Java példa fejlesztőknek
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Alakzatok csoportosítása a Wordben – teljes programozási útmutató
url: /hu/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alakzatok csoportosítása Word-ben – teljes programozási útmutató

Ha **alakzatokat kell csoportosítania Word-ben**, ez a bemutató végigvezeti a teljes folyamaton Java és Aspose.Words segítségével. Megtanulja, hogyan **hozzon létre üres Word dokumentumot**, **készítsen téglalap alakzatot**, **állítsa be az alakzat méreteit**, és végül **csoportosítsa több alakzatot**, hogy egyetlen objektumként viselkedjenek.

A Word fájlban való alakzatkezelés gyakran olyan, mintha ecset nélkül rajzolna egy vászonra. A leírás végére egy újrahasználható kódrészletet kap, amelyet bármely Java projektbe beilleszthet, legyen szó jelentésgenerálásról, számlákról vagy egyedi sablonokról.

## Amire szüksége lesz

- Java 8 vagy újabb
- Aspose.Words for Java (a legújabb verzió, pl. 24.9)
- IDE, például IntelliJ IDEA vagy Eclipse
- Alapvető ismeretek az objektum‑orientált programozásból

Mindezek a feltételek ingyenesen telepíthetők, és az alábbi kód egyetlen Maven függőséggel fordítható:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 1. lépés: Üres Word dokumentum létrehozása és a builder inicializálása

Az első teendő **üres Word dokumentum létrehozása**. Ez egy tiszta vásznat biztosít, amelyre később alakzatokat helyezhet.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A `Document` a teljes *.docx* fájlt képviseli, míg a `DocumentBuilder` az a segéd, amely bekezdéseket, táblázatokat és alakzatokat szúr be. Mindkét objektum inicializálása a Word‑automatizálás bármely feladatának alapja.

## 2. lépés: Csoportos alakzat konténer beszúrása

Egy **csoportos alakzat** olyan, mint egy mappa, amely más alakzatokat tarthat. Először létrehozzuk a konténert 400 pt × 200 pt fix mérettel.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

Az `insertGroupShape` metódus egy `GroupShape` objektumot ad vissza. Minden további alakzat, amelyet egy egységként szeretnénk kezelni, ehhez az objektumhoz kell hozzáadni.

## 3. lépés: Téglalap alakzatok létrehozása és méretek beállítása

Most **téglalap alakzat** objektumokat hozunk létre, beállítjuk a méretüket, és a csoporton belül elhelyezzük őket. Ez a lépés bemutatja, hogyan **állítsuk be pontosan az alakzat méreteit**.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Mindkét téglalap ugyanazokkal a méretekkel rendelkezik, de a `left` tulajdonságuk különbözik, így egymás mellett jelennek meg. A `setTop` és `setLeft` módosításával bármilyen elrendezést kialakíthat.

## 4. lépés: A csoportosított téglalapokat tartalmazó dokumentum mentése

Miután az alakzatok a csoportban vannak, egyszerűen mentse a `Document`-et. A kapott fájl két téglalapot mutat, amelyek együtt mozognak, ha kiválasztják őket.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

A program futtatása a munkakönyvtárban létrehozza a `GroupShape.docx` fájlt. Nyissa meg a Microsoft Wordben, válasszon ki egy téglalapot, és észre fogja venni, hogy az egész csoport egységként mozog – pontosan ez a **csoportos alakzatok Word-ben** célja.

![Group shapes in Word example](group-shapes.png){alt="Group shapes in Word example"}

*Ábra: Két téglalap alakzat csoportosítva egy Word dokumentumban.*

## Profi tipp: Ugyanannak a csoportos alakzatnak az újrahasználata

Ha később további alakzatokat (például köröket, szövegdobozokat) szeretne hozzáadni, tartsa meg a `groupShape` hivatkozást, és folytassa az `appendChild` hívását. Így elkerülheti a konténer újbóli létrehozását, és minden elem szinkronban marad.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Szélsőséges esetek és gyakori kérdések

- **Mi van, ha az alakzatok átfedik egymást?** Az átfedés megengedett; a Word a hozzáadás sorrendjében jeleníti meg őket. Használja a `setZOrder`‑t, ha explicit rétegezésre van szükség.
- **Csoportosíthatok-e alakzatokat különböző oldalakon?** Nem. A `GroupShape` egyetlen oldalra korlátozódik, mivel koordináta-rendszere oldal‑relatív.
- **A csoportos alakzatok örökölnek-e formázást?** Minden gyermek megtartja saját formázását (kitöltőszín, vonalstílus). Egységes stílus alkalmazásához iteráljon a `groupShape.getChildNodes()` elemein, és programozottan állítsa be a tulajdonságokat.

## Teljes forráskód referenciaként

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

A program futtatása egy DOCX fájlt hoz létre, ahol a két téglalap **csoportosítva** van. Bármelyik téglalap kiválasztása mindkettőt mozgatja, ezzel megerősítve, hogy **sikeresen csoportosította a több alakzatot**.

## Összegzés

Most már tudja, hogyan **csoportosítsa az alakzatokat Word-ben** Java segítségével, a **üres Word dokumentum létrehozásától** a **téglalap alakzat** készítésén, a **méretek beállításán**, egészen a **több alakzat egyetlen, mozgatható objektummá csoportosításáig**. Ez a minta tetszőleges számú alakzatra skálázható, és kombinálható szöveggel, képekkel vagy diagramokkal, hogy gazdag, programozott dokumentumokat hozzon létre.

### Mi a következő lépés?

- Fedezze fel a **több alakzat csoportosítását** különböző típusokkal (ellipszisek, nyilak, szövegdobozok).
- Alkalmazzon kitöltőszíneket vagy szegélyeket a `shape.getFillColor()` és a `shape.getLine().setColor()` hívásokkal.
- Szúrja be a csoportos alakzatot egy táblázatcellába a strukturált jelentésekhez.
- Kombinálja ezt a megközelítést a levélösszevonással, hogy személyre szabott szerződéseket generáljon, amelyek márkázott grafikákat tartalmaznak.

Kísérletezzen nyugodtan, módosítsa a méreteket, vagy ágyazzon be további tartalmakat. Amikor elsajátítja a csoportosítást, a Word‑automatizálási szkriptek sokkal rugalmasabbak és karbantarthatóbbak lesznek. Jó kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsék az API további funkcióinak elsajátítását és alternatív megvalósítási módok felfedezését saját projektjeiben.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}