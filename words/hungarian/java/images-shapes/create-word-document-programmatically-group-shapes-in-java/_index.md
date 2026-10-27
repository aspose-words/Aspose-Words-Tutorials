---
category: general
date: 2026-09-21
description: Word dokumentum létrehozása programozott módon Java-val. Tanulja meg,
  hogyan csoportosíthatók alakzatok a Wordben, hogyan szúrjon be egy téglalap alakzatot,
  hogyan állítsa be az alakzat méretét, és hogyan adjon hozzá alakzatokat egy Word
  dokumentumhoz.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: hu
lastmod: 2026-09-21
og_description: 'Word dokumentum létrehozása programozottan Java-val: ez az útmutató
  bemutatja, hogyan csoportosíthatók alakzatok a Wordben, hogyan szúrhatók be téglalap
  alakzatok, hogyan állítható be az alakzat mérete, és hogyan adhatók hozzá alakzatok
  egy Word dokumentumhoz.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Word dokumentum programozott létrehozása, alakzatok csoportosítása Java-ban
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Word dokumentum létrehozása programozott módon, alakzatok csoportosítása Java-ban
url: /hu/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása programozottan, alakzatok csoportosítása Java-ban

Ha **programozottan szeretnél Word dokumentumot létrehozni**, ez az útmutató egy teljes megoldáson keresztül vezet végig. Megmutatja, hogyan **csoportosíthatók alakzatok a Wordben**, hogyan szúrj be egy téglalapot, állítsd be a méretét, és adj hozzá további alakzatokat – mindezt Java és az Aspose.Words for Java könyvtár segítségével.

Az oktatóanyag minden lépést lefed a projekt beállításától a végleges .docx fájl mentéséig. A végére képes leszel olyan Word dokumentumot generálni, amely egy téglalapot és egy képet tartalmaz egyetlen csoportban, így könnyen mozgathatók vagy átméretezhetők együtt. Nem szükséges előzetes tapasztalat az Aspose.Words API-val, de alapvető Java fejlesztői környezettel kell rendelkezned.

## Prerequisites

* Java Development Kit (JDK) 8 vagy újabb  
* Maven vagy Gradle a függőségkezeléshez  
* Aspose.Words for Java 23.9 (vagy a legújabb verzió) – a könyvtár ingyenes kiértékeléshez  
* Egy képfájl (pl. `sample.jpg`) egy ismert könyvtárban elhelyezve  

Ezeknek az elemeknek a rendelkezésre állása biztosítja, hogy a kód további konfiguráció nélkül fusson.

## Step 1: Set up the project and import Aspose.Words

Hozz létre egy Maven projektet (vagy add hozzá a függőséget a meglévő `pom.xml`-hez):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Ha Gradlet részesítesz előnyben, add hozzá a következőt a `build.gradle`-hez:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

A függőség feloldása után importáld a szükséges osztályokat a Java forrásfájlodba:

```java
import com.aspose.words.*;
import java.io.File;
```

## Step 2: Create the Word document programmatically

Az első művelet bármely automatizálási szcenárióban egy `Document` objektum és egy `DocumentBuilder` példányosítása. A builder egyszerűsíti a szöveg, képek és alakzatok beszúrását.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Ezen a ponton a dokumentum csak a memóriában létezik. Most már elkezdhetsz alakzatokat hozzáadni.

## Step 3: Insert a rectangle shape – how to insert rectangle shape

A téglalap egy alap `Shape` a `ShapeType.RECTANGLE` típussal. Méreteit a `setWidth`, `setHeight` segítségével, pozícióját pedig a `setTop` és `setLeft` metódusokkal szabályozhatod.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Why this matters:** A méret és pozíció explicit beállítása (`set shape size word`) garantálja, hogy a téglalap pontosan ott jelenik meg, ahol elvárod, függetlenül a dokumentum alapértelmezett elrendezésétől.

## Step 4: Insert an image – add shapes to word document

A `DocumentBuilder` közvetlenül egy fájl útvonaláról tud képet beszúrni. Beszúrás után a képet ugyanúgy áthelyezheted, mint bármely másik alakzatot.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

A téglalap és a kép most már önálló alakzatok a dokumentumban.

## Step 5: Group the shapes – how to group shapes in word

Az alakzatok csoportosítása akkor hasznos, ha egy egységként szeretnéd őket mozgatni vagy átméretezni. Az Aspose.Words egy `GroupShape` tárolót biztosít erre a célra.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

A csoport mentésekor a Word a két gyermeket egy logikai objektumként kezeli. Később kiválaszthatod a csoportot és húzhatod, ekkor a téglalap és a kép is követi.

## Step 6: Save the document

Végül írd a dokumentumot a lemezre. Az útvonalnak írhatóvá kell válnia a Java folyamat számára.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

A `main` metódus futtatása egy **GroupShapeExample.docx** nevű fájlt hoz létre. Nyisd meg Microsoft Wordben, hogy egy téglalapot és egy képet láss, amelyek egy csoportban vannak összekapcsolva. A csoport kiválasztása lehetővé teszi mindkét objektum egyidejű mozgatását, ezzel megerősítve, hogy a csoportosítás sikeres volt.

## Expected output

* Egy Word fájl (`GroupShapeExample.docx`) a megadott könyvtárban.  
* A fájlban egy téglalap (világosszürke kitöltéssel) a bal‑felső sarokban jelenik meg, és a kép közvetlenül alatta helyezkedik el.  
* Mindkét objektum egyetlen csoport része, így az egyik húzása a másikat is mozgatja.

## Common variations and edge cases

| Situation | Recommendation |
|-----------|----------------|
| **Különböző képformátumok** | Az Aspose.Words támogatja a PNG, BMP, GIF és TIFF formátumokat. Használd a megfelelő fájlkiterjesztést az `insertImage`‑nél. |
| **Negatív méretek** | Az API `ArgumentException`‑t dob. Mindig ellenőrizd a szélességet és magasságot, mielőtt meghívod a `setWidth` / `setHeight` metódusokat. |
| **Nagy dokumentumok** | Sok alakzat csoportosítása növelheti a fájlméretet. Ha a teljesítmény fontos, fontold meg az alakzatok egyetlen képpé egyesítését. |
| **Word verzió kompatibilitás** | A GroupShape működik a Word 2007 (`.docx`) és újabb verzióival. Régebbi `.doc` fájlok esetén a csoport laposítva lesz. |
| **Dinamikus pozicionálás** | Használj számításokat az oldal mérete alapján (`doc.getFirstSection().getPageSetup().getPageWidth()`), ha adaptív elhelyezésre van szükség. |

**Pro tip:** A csoport létrehozása után módosíthatod

## What Should You Learn Next?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Téglalap alakzat létrehozása Wordben Java-val – Teljes útmutató](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}