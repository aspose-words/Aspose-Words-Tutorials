---
category: general
date: 2026-11-25
description: Hogyan csoportosíthatók alakzatok a Wordben Java használatával, és hogyan
  állíthatók be az alakzatok méretei egy DOCX fájlban az Aspose.Words segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: hu
lastmod: 2026-11-25
og_description: Hogyan csoportosítsunk alakzatokat a Wordben az Aspose.Words Java
  API-val, és állítsuk be gyorsan az alakzat méretét. Kövesse a teljes lépésről‑lépésre
  megoldást.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Hogyan csoportosítsuk a formákat a Wordben, és állítsuk be a méreteiket
  – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Hogyan csoportosítsuk a formákat a Wordben, és programozottan állítsuk be a
  méreteiket
url: /hu/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan csoportosítsuk a formákat a Wordben, és állítsuk be programozottan a méreteiket

Ha szükséged van arra, hogy **how to group shapes in Word** és szabályozd a pontos méretüket, ez az útmutató egy teljes, futtatható megoldást mutat be. Az Aspose.Words for Java segítségével létrehozhatsz egy téglalapot, egy ellipszist, hozzáadhatod őket egy `GroupShape`-hez, majd **how to set shape dimensions**-t, például a szélességet és magasságot egyetlen DOCX fájlban.

Megtanulod, hogyan:

* Új Word dokumentumot hozhatsz létre a semmiből.  
* Beszúrj egy `GroupShape`-t (új API a 24.9-es verzióban).  
* Hozzáadj egy téglalapot és egy ellipszist a csoporthoz.  
* **Set shape size Word** pontosan a `setWidth` és `setHeight` segítségével.  
* Elmented a dokumentumot a lemezre.

Nem szükséges külső eszköz – csak Java 17+, Maven és az Aspose.Words for Java könyvtár.

## Prerequisites

* Java Development Kit 17 vagy újabb.  
* Maven (vagy Gradle) a függőségkezeléshez.  
* Aspose.Words for Java 24.9 vagy későbbi (a `GroupShape` API a 24.9‑ben került bevezetésre).  
* Alapvető ismeretek a Java szintaxisról és az objektum‑orientált koncepciókról.

Ha még nem adtad hozzá az Aspose.Words‑t a projektedhez, helyezd be a következő Maven függőséget:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Step 1: Create a new document and a DocumentBuilder

A `Document` osztály képviseli a teljes Word fájlt, míg a `DocumentBuilder` kényelmes módot biztosít a tartalom hozzáadására.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this step?*  
Egy friss `Document` létrehozása tiszta vásznat biztosít. A `DocumentBuilder` a magas szintű segédeszköz, amely lehetővé teszi bekezdések, táblázatok és ebben az esetben formák beszúrását.

## Step 2: Insert a GroupShape (new API in version 24.9)

A `GroupShape` egy konténerként működik; minden hozzáadott forma a ugyanazon vizuális csoport részévé válik.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use `GroupShape`?*  
A formák csoportosítása egyszerűsíti a mozgatást, forgatást vagy a formázás alkalmazását több objektumon egyszerre. Az API a 24.9‑es verzióban került hozzáadásra, így a régebbi verziók nem tudják lefordítani ezt a sort.

## Step 3: Create a rectangle, set its size, and add it to the group

Itt bemutatjuk, hogyan **how to set shape dimensions** egy téglalap esetén.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Why set width and height explicitly?*  
A Word a forma méretét pontokban tárolja. A `setWidth` és `setHeight` meghívásával pontosan szabályozhatod a vizuális lábnyomot, ami elengedhetetlen, ha precíz elrendezésre vagy PDF‑exportálásra van szükség.

## Step 4: Create an ellipse, set its size, and add it to the same group

Ugyanaz a **set shape size word** technika bármely forma típusra alkalmazható.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Why add the ellipse to the same `GroupShape`?*  
Mindkét forma együtt mozog majd egységként. Ez hasznos ikonok, logók vagy összetett diagramok létrehozásához, amelyeknek össze kell maradniuk.

## Step 5: Save the document with the grouped shapes

Végül a DOCX fájlt lemezre mentjük.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

A program futtatása egy **GroupShape.docx** nevű fájlt hoz létre, amely egy téglalapot és egy ellipszist tartalmaz, csoportosítva. Amikor megnyitod a fájlt a Microsoft Wordben, a két forma egyetlen objektumként viselkedik – együtt húzhatók, átméretezhetők vagy forgathatók.

### Expected output

* Egy Word dokumentum (`GroupShape.docx`) egy oldallal.  
* Egy `GroupShape`, amely egy 100 × 50 pt méretű téglalapot és egy 80 × 80 pt méretű ellipszist tartalmaz.  
* Az egyik forma kiválasztása az egész csoportot kiválasztja.

## Common questions and edge cases

### How to change the position of the grouped shapes?

A `GroupShape` létrehozása után beállíthatod a `left` és `top` tulajdonságait:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Ezek a koordináták is pontokban vannak megadva.

### What if I need to add more than two shapes?

A `GroupShape` bármely más konténer csomóponthoz hasonlóan működik. Hívjad a `groupShape.appendChild(yourShape)`‑t minden további forma esetén. Az API nem korlátozza a gyermekek számát.

### Can I apply style (fill color, line weight) to individual shapes?

Igen. Minden `Shape` objektum formázási tulajdonságokat tesz elérhetővé:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Does the code work with older Aspose.Words versions?

Az `insertGroupShape` metódus a 24.9‑es verzióban került bevezetésre. Ha korábbi verziót használsz, manuálisan kell létrehoznod egy `GroupShape`‑t a csomópontfában, ami bonyolultabb. A frissítés a javasolt út.

## Pro tips

* **Használj pontokat a konzisztencia érdekében** – a Word belső egysége a pont (1/72 inch). A pixelekből vagy centiméterekből történő átváltás váratlan méreteket eredményezhet.  
* **Csoportosíts a pozicionálás előtt** – a `GroupShape` pozícióját a gyermekek hozzáadása után állítsd be; különben újra kell számolnod az eltolásokat.  
* **Használd újra a DocumentBuilder‑t** – több csoportot is beszúrhatsz ugyanabba a dokumentumba a builder kurzorának (`builder.moveTo`) áthelyezésével minden `insertGroupShape` hívás előtt.

## Conclusion

Most már van egy teljes, vég‑től‑végig példád arra, **how to group shapes in Word** és **how to set shape dimensions** használatával az Aspose.Words for Java‑ban. Az útmutató lefedte a dokumentum létrehozását, egy `GroupShape` beszúrását, egy téglalap és egy ellipszis hozzáadását, a pontos méretük beállítását, valamint az eredmény mentését.  

Innen tovább felfedezheted:

* Szövegdobozok vagy képek hozzáadása ugyanahhoz a csoporthoz.  
* A csoportosított formák animálása a Word intelligens ábrák funkcióival (az API‑n keresztül).  
* A csoportosított formák exportálása PDF‑be vagy SVG‑be webes felhasználáshoz.

Nyugodtan kísérletezz különböző forma típusokkal, méretekkel és pozíciókkal – a csoportosítás erőteljes irányítást biztosít a komplex elrendezések felett Word dokumentumokban.

## What Should You Learn Next?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre üres Word dokumentumot és csoportosítsuk a formákat Java‑ban](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [Hogyan csoportosítsuk a formákat a Wordben Java‑val – teljes útmutató](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}