---
category: general
date: 2026-09-24
description: Tanulja meg, hogyan hozhat létre üres Word-dokumentumot Java nyelven,
  és hogyan csoportosíthatja a téglalapok és vonalak alakzatát az Aspose.Words segítségével.
  Lépésről lépésre kódot tartalmaz.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: hu
lastmod: 2026-09-24
og_description: Hozzon létre egy üres Word-dokumentumot Java-ban, és tanulja meg,
  hogyan csoportosíthatja az alakzatokat, adhat hozzá egy téglalap alakzatot, valamint
  állíthatja be az alakzat méretét az Aspose.Words segítségével.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Üres Word-dokumentum létrehozása és alakzatok csoportosítása Java-ban –
  lépésről‑lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hogyan hozhatunk létre üres Word-dokumentumot, és csoportosíthatunk alakzatokat
  Java-ban
url: /hu/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozhatunk létre üres Word dokumentumot és csoportosíthatunk alakzatokat Java-ban

Ha **üres Word dokumentumot** kell létrehoznod, majd több rajzobjektumot szeretnél rendezni, ez az útmutató pontosan megmutatja, hogyan. Az Aspose.Words for Java segítségével beilleszthetsz egy csoport alakzatot, hozzáadhatsz egy téglalap alakzatot, rajzolhatsz egy vonalat, és vezérelheted minden alakzat méretét és pozícióját – mindezt egyetlen, futtatható programban.

Minden lépésen végig fogsz menni, a dokumentum inicializálásától a végleges `.docx` mentéséig. A végére megérted, hogyan **csoportosíthatók alakzatok**, hogyan **adhatsz hozzá téglalap alakzatot**, és hogyan **állítható be az alakzat mérete**, hogy a Word fájljaid pontosan úgy nézzenek ki, ahogy szeretnéd.

## Előfeltételek

- Java 17 vagy újabb (a kód bármely friss JDK-val fordítható)
- Aspose.Words for Java könyvtár (letölthető az [Aspose weboldaláról](https://products.aspose.com/words/java))
- Egy IDE vagy build eszköz (Maven/Gradle), amely hozzá tudja adni az Aspose.Words JAR-t az osztályútvonalhoz
- Alapvető Java szintaxis ismeretek

> **Pro tipp:** Használd a Maven-t a függőségkezeléshez; add hozzá a `com.aspose:aspose-words:23.12` (vagy a legújabb verzió) a `pom.xml`-hez.

## 1. lépés: Üres Word dokumentum létrehozása

Az első feladat a **üres Word dokumentum** létrehozása. Ez egy tiszta vásznat biztosít, amelyre később alakzatokat illeszthetsz.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Miért fontos:* A `Document` objektum képviseli a teljes `.docx` fájlt. Egy üres dokumentummal kezdve biztosítható, hogy semmilyen rejtett formázás ne befolyásolja a hozzáadott alakzatokat.

## 2. lépés: Csoport alakzat beszúrása – a több objektumot tartalmazó tároló

A **csoport alakzat** olyan tárolóként működik, amely lehetővé teszi több alakzat együttes mozgatását, átméretezését vagy forgatását. Ez a **alakzatok csoportosításának** alapja a Wordben.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Magyarázat:* Az `insertGroupShape` metódus létrehoz egy `GroupShape` objektumot, és a jelenlegi kurzorpozícióba helyezi. Minden későbbi alakzat, amelyet a `appendChild`-el ebbe a csoportba illesztesz, egy egységként lesz kezelve.

## 3. lépés: Téglalap alakzat hozzáadása és méretének beállítása

Most **téglalap alakzatot adunk hozzá** a csoporthoz, és **pontosan beállítjuk az alakzat méretét**.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Miért kell beállítani az alakzat méretét:* A szélesség és magasság szabályozza, hogyan jelenik meg a téglalap az oldalon. A `setLeft` és `setTop` metódusok a téglalapot a csoport origójához képest pozicionálják, így pixel‑pontos elrendezés‑vezérlést kapsz.

## 4. lépés: Vonal alakzat hozzáadása és méretének beállítása

A vonal egy másik gyakori rajzobjektum. **Téglalap alakzat**‑szerű logikát alkalmazunk egy vonalra, bemutatva, hogy ugyanazok az méretezési elvek érvényesek.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Fontos pont:* Bár a vonalnak nincs magassága, továbbra is a `setWidth`-et használod a hosszának meghatározásához. A pozicionálás (`setLeft`, `setTop`) ugyanazt a koordináta rendszert követi, mint a többi alakzat.

## 5. lépés: Dokumentum mentése csoportosított alakzatokkal

Végül, a változtatásokat a dokumentum mentésével rögzíted. Ez egy `.docx` fájlt hoz létre, amelyet megnyithatsz a Microsoft Wordben az eredmény ellenőrzéséhez.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Várható kimenet:** A `GroupShapeDemo.docx` megnyitása egy üres oldalt mutat, amely egy csoportosított téglalapot és vonalat tartalmaz. Bármelyik alakzat kiválasztása a teljes csoportot jelöli ki, lehetővé téve azok együttes mozgatását.

## Gyakori kérdések és szél‑esetek kezelése

| Kérdés | Válasz |
|----------|--------|
| *Hozzáadhatok több mint két alakzatot a csoporthoz?* | Igen. Hívd meg a `group.appendChild(yourShape)`-t minden további alakzatra. |
| *Mi van, ha más egységre (pl. centiméter) van szükség a mérethez?* | Az Aspose.Words pontokat használ (1 pont = 1/72 hüvelyk). Átváltás: `Points = centimeters * 28.3465`. |
| *Megőrzi-e a csoport az elrendezését, ha a dokumentumot más gépen nyitják meg?* | Teljesen. Minden méret- és pozícióadat a `.docx` fájlban tárolódik, így az elrendezés hordozható. |
| *Hogyan bontsam fel később a csoportot?* | Szerezd meg a `GroupShape` objektumot, majd iterálj a `group.getChildNodes(NodeType.SHAPE, true)`-en, és helyezd át minden gyereket a csoportból. |
| *Mi van, ha az egész csoportot el kell forgatni?* | Használd a `group.setRotationAngle(double angleInDegrees)` metódust a mentés előtt. |

## Teljes, futtatható példa

Az alábbiakban a teljes programot találod, amelyet kimásolhatsz és beilleszthetsz az IDE-dbe. Tartalmazza az összes szükséges importot és megjegyzést.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Futtasd a programot, nyisd meg a `GroupShapeDemo.docx`-et a Microsoft Wordben, és a leírtaknak megfelelően csoportosított alakzatokat fogsz látni.

## Következtetés

Most már tudod, hogyan **hozz létre üres Word dokumentumot**, **csoportosíts alakzatokat Wordben**, **adj hozzá téglalap alakzatot**, és **állítsd be az alakzat méretét** az Aspose.Words for Java használatával. Alakzatok `GroupShape`-ba helyezésével teljes irányítást kapsz a közös pozicionálás, méretezés és forgatás felett – tökéletes diagramok, folyamatábrák vagy egyedi grafikák beágyazásához automatizált jelentésekbe.

**Következő lépések:**  
- Fedezd fel, hogyan **csoportosíthatók alakzatok** összetettebb objektumokkal, például képekkel vagy szövegdobozokkal.  
- Kísérletezz a `setRotationAngle` használatával az egész csoport forgatásához.  
- Kombináld ezt a technikát a levélösszevonással (mail‑merge), hogy személyre szabott dokumentumokat generálj, amelyek márkázott grafikákat tartalmaznak.

Nyugodtan adaptáld a kódot a saját projektjeidhez, és oszd meg az eredményeidet a megjegyzésekben!

## Mit érdemes következőként megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat, és alternatív megvalósítási megközelítéseket fedezhess fel saját projektjeidben.

- [Téglalap alakzat létrehozása Wordben Java-val – Teljes útmutató](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Word dokumentum létrehozása Java-val – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Csoport alakzat létrehozása Word dokumentumban Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}