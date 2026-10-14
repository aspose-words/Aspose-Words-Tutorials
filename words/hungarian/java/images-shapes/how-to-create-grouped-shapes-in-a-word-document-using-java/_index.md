---
category: general
date: 2026-10-13
description: Tanulja meg, hogyan hozhat létre csoportosított alakzatokat a Wordben
  Java‑val. Ez az útmutató megmutatja, hogyan szúrjon be csoportos alakzatot, hogyan
  adjon vonalat a csoporthoz, és hogyan csoportosítson több alakzatot az egész Word
  dokumentumban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: hu
lastmod: 2026-10-13
og_description: Csoportos alakzatok létrehozása Wordben Java-val. Kövesd ezt a teljes
  útmutatót a csoportos alakzat beszúrásához, vonal hozzáadásához a csoporthoz, és
  több alakzat csoportosításához Word dokumentumokban.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Csoportos alakzatok létrehozása a Wordben Java-val – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hogyan hozhatunk létre csoportosított alakzatokat egy Word-dokumentumban Java
  használatával
url: /hu/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre csoportos alakzatokat egy Word dokumentumban Java-val

Ha Java-ból szeretne **create grouped shapes** egy Microsoft Word fájlban, ez az útmutató végigvezeti a teljes folyamaton. Megmutatjuk, hogyan **insert group shape**, helyezzen el egy téglalapot és egy vonalat ugyanabban a tárolóban, és végül mentse a dokumentumot a csoportos grafikákkal.

Az alakzatok csoportosítása megkönnyíti több rajzobjektum mozgatását, átméretezését vagy stílusozását egyetlen egységként – tökéletes diagramokhoz, folyamatábrákhoz vagy egyedi oldaldekorációkhoz. A útmutató végére képes lesz **add line to group**, **group multiple shapes word** dokumentumokba vonal hozzáadására, és ugyanazt a technikát bármennyi alakzatra újra felhasználni.

## Előfeltételek

- Java 17 vagy újabb telepítve a fejlesztői gépén.  
- Aspose.Words for Java licenc (vagy ingyenes értékelés).  
- Maven vagy Gradle projekt, ahol hozzáadhatja az Aspose.Words függőséget:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Nem szükséges további könyvtár.

## 1. lépés: A csoport alakzat tároló beszúrása

Az első lépés a **insert group shape** beszúrása a dokumentumba. Ez a tároló fogja tartalmazni az összes későbbi alakzatot.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` egy üres `Shape` objektumot hoz létre `GROUPSHAPE` típusúként. Tekintse átlátszó vászonként, amely más rajzobjektumokat is tartalmazhat.

## 2. lépés: Téglalap hozzáadása a csoporthoz

A téglalap gyakran szolgál a csoport alakzatainak vizuális háttérként.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

`Left` és `Top` értékének `0`-ra állítása a téglalapot a csoport bal‑felső sarkába helyezi. Ezeket az értékeket módosíthatja, hogy eltolja az alakzatot a csoporton belül.

## 3. lépés: **Add line to group** – vonal alakzat létrehozása

Most **add line to group**. A vonal a téglalap alatt jelenik meg.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

A `Top` tulajdonság a vonalat 60 ponttal a téglalap alá helyezi, egyszerű rétegezett elrendezést hozva létre. Ha vízszintes eltolásra van szükség, beállíthatja a `Left` értéket is.

## 4. lépés: Dokumentum mentése a csoportos alakzatokkal

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Amikor megnyitja a `GroupShapeDemo.docx` fájlt a Microsoft Wordben, egyetlen csoportot lát, amely tartalmazza a téglalapot és a vonalat is. A csoport kiválasztása lehetővé teszi mindkét alakzat együttes mozgatását, ami azt mutatja, hogy sikeresen **group multiple shapes word**.

## Teljes, futtatható példa

Az alábbiakban a teljes program látható, minden importtal és hibakezeléssel. Másolja be a fejlesztői környezetébe, cserélje le a `YOUR_DIRECTORY`-t egy létező mappára, és futtassa.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Várt kimenet

- A `GroupShapeDemo.docx` nevű fájl megjelenik a célmappában.  
- A fájl Wordben való megnyitása egyetlen csoportos objektumot mutat, amely tetején egy téglalapot, alatta egy vonalat tartalmaz.  
- A csoport húzása mindkét alakzatot együtt mozgatja, megerősítve, hogy sikeresen **created grouped shapes**.

## Tippek és gyakori buktatók

- **Pro tip:** Ha a csoporton belüli egyes alakzatokat el kell forgatni vagy stílusozni, hívja meg a megfelelő beállítókat (`setRotation`, `getFill().setForeColor`, stb.) a csoporthoz való hozzáadás előtt. A csoport megőrzi ezeket a vizuális tulajdonságokat.
- **Figyeljen:** Ha elfelejti beállítani a vonal `Top` tulajdonságát, az átfedheti a téglalapot, és a csoport zsúfoltnak tűnhet.
- **Szélsőséges eset:** Ha kétnél több alakzatot ad hozzá, ne feledje, hogy minden gyermek koordinátái a csoport (0,0) kiindulópontjához képest relatívak. Ennek megfelelően tervezze meg az elrendezést.
- **Teljesítményjegyzet:** Nagy számú alakzat (százak) csoportosítása kissé növelheti a fájlméretet, de egyszerűsíti a későbbi szerkesztést a Wordben.

## Hogyan **group multiple shapes word** dokumentumokat programozottan

A fent bemutatott minta – csoport tároló létrehozása, minden gyermek alakzat konfigurálása és hozzáadása – bármennyi alakzatra működik: körök, képek, szövegdobozok stb. Egyszerűen ismételje meg a „create shape → set properties → append” lépéseket a `doc.save()` hívása előtt.

Ha a csoport már tartalmaz más alakzatokat, és **add line to group** kell hozzáadni, a meglévő csoportot a következő módon kérheti le:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Ez azt mutatja, hogy a csoportot a dokumentum életciklusának bármely pontján módosíthatja.

## Következtetés

Most már tudja, hogyan **create grouped shapes** egy Word dokumentumban Java és Aspose.Words segítségével. A **inserting group shape**, **adding line to group**, és **group multiple shapes word** használatával összetett rajzokat hozhat létre, amelyek egyetlen objektumként viselkednek – ideális diagramokhoz, sablonokhoz és automatizált jelentéskészítéshez.

Ezután fedezze fel a kapcsolódó témákat:

- **Applying styles to grouped shapes** – tanulja meg, hogyan állíthat be kitöltőszíneket, szegélyeket és effektusokat egyszerre minden gyermekre.  
- **Exporting grouped shapes to PDF** – nézze meg, hogyan marad meg ugyanaz a csoport a dokumentum konvertálásakor.  
- **Animating shapes with VBA** – kombinálja a Java‑val generált csoportokat Word makrókkal interaktív dokumentumokhoz.

Nyugodtan kísérletezzen különböző alakzat típusokkal, méretekkel és pozíciókkal. A csoportosítás rugalmasságot biztosít, hogy sok objektumot egyként kezeljen, egyszerűsítve a kódot és a felhasználói interakciót. Jó kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}