---
category: general
date: 2026-09-27
description: Készítsen egy üres Word-dokumentumot Java-ban, és csoportosítsa az alakzatokat
  az Aspose.Words használatával. Tanulja meg beállítani az alakzat méretét, a kitöltő
  színt, és gyermekelemet hozzáadni a csoporthoz.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: hu
lastmod: 2026-09-27
og_description: Üres Word-dokumentum létrehozása Java-ban az Aspose.Words segítségével.
  Ez az útmutató bemutatja, hogyan lehet csoportosítani alakzatokat a Wordben, beállítani
  az alakzat méretét, kitöltőszínét, és gyermekelemet hozzáadni a csoporthoz.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Üres Word-dokumentum létrehozása és alakzatok csoportosítása Java-ban –
  lépésről‑lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hogyan készítsünk üres Word-dokumentumot és csoportosítsunk alakzatokat Java-ban
url: /hu/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre üres Word-dokumentumot és csoportosítsunk alakzatokat Java‑ban

Ha programból **üres Word-dokumentumot** kell létrehoznod, ez az útmutató pontosan megmutatja, hogyan teheted meg az Aspose.Words for Java segítségével. Emellett megtanulod, hogyan **csoportosíts alakzatokat a Wordben**, hogyan állítsd be az egyes alakzatok méretét, alkalmazz kitöltőszínt, és hogyan **adj gyermekelemet a csoporthoz**, hogy az objektumok egy egységként viselkedjenek.

A Word‑fájlok kódból történő kezelése megkímél a kézi formázástól, és lehetővé teszi jelentések, szerződések vagy marketing anyagok automatikus generálását. A tutorial végére egy futtatható Java‑programod lesz, amely egy `.docx` fájlt hoz létre, benne egy kék téglalappal és egy képpel, mindkettő egy csoportba rendezve.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következők rendelkezésre állnak:

- Java 17 (vagy bármely friss JDK) telepítve.
- Maven vagy Gradle a függőségek kezeléséhez.
- Aspose.Words for Java licenc (az ingyenes értékelő verzió teszteléshez elegendő).
- Egy minta képállomány (pl. `sample.jpg`), amelyet egy olyan mappában helyeztél el, ahonnan a kódból hivatkozhatsz rá.

> **Pro tip:** Tedd a képfájlokat egy `resources` könyvtárba, és töltsd be őket a `ClassLoader.getResourceAsStream` segítségével, hogy elkerüld a keményen kódolt abszolút útvonalakat.

## 1. lépés: Üres Word-dokumentum létrehozása és GroupShape hozzáadása

Az első lépés egy új `Document` objektum példányosítása, amely egy üres Word‑fájlt képvisel, majd egy `GroupShape` beszúrása. A csoport a később hozzáadott alakzatok tárolójaként szolgál.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Miért fontos:* A `GroupShape` lehetővé teszi több alakzat együttes mozgatását, forgatását vagy formázását, ami elengedhetetlen összetett elrendezésekhez, például diagramokhoz vagy vízjelekhez.

## 2. lépés: Téglalap beszúrása és **alakzatméret beállítása**

Ezután hozz létre egy téglalapot, definiáld a méreteit, és add hozzá a csoporthoz. Ezzel demonstrálod a **alakzatméret beállítása** műveletet.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Magyarázat:* A `setWidth` és a `setHeight` pontosan a pontokban (1 pont = 1/72 hüvelyk) határozza meg az alakzat méretét. Igazítsd ezeket az értékeket a kívánt elrendezéshez.

## 3. lépés: **Alakzat kitöltőszínének beállítása** a téglalaphoz

A téglalap háttérszíne kék, a `setFillColor` segítségével. Bármely `java.awt.Color` konstans vagy egy egyedi RGB‑szín használható.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Miért hasznos:* A kitöltőszínek vizuálisan elkülönítik az objektumokat, különösen akkor, ha a dokumentumot később PDF‑be exportálod vagy nyomtatod.

## 4. lépés: Kép beszúrása és **gyermekelem hozzáadása a csoporthoz**

Most adj egy képet ugyanahhoz a `GroupShape`‑hez. A képet a `DocumentBuilder.insertImage` helyezi be, majd a csoporthoz csatoljuk, hogy a téglalappal együtt mozogjon.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Szélsőséges eset:* Ha a kép útvonala hibás, az Aspose.Words `FileNotFoundException`‑t dob. Használj relatív útvonalat vagy töltsd be a képet erőforrásként, hogy elkerüld ezt a problémát.

## 5. lépés: **Dokumentum mentése a csoportosított alakzatokkal**

Végül írd a dokumentumot a lemezre. A kapott fájlban a téglalap és a kép együtt lesz csoportosítva.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Várt kimenet

- Egy `GroupShape.docx` nevű fájl jelenik meg a megadott könyvtárban.
- A Microsoft Word‑ben megnyitva egy üres oldal látható, amelyen egy kék téglalap és a kiválasztott kép egyetlen objektumként van kijelölve (együtt mozgatható vagy átméretezhető).

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*A fenti képernyőkép a végső, csoportosított alakzatokat mutatja az újonnan létrehozott Word‑dokumentumban.*

## Gyakori variációk és további tippek

| Helyzet | Hogyan kezeljük |
|-----------|-----------------|
| **Több kép** | Minden képet szúrj be a `builder.insertImage`‑vel, és minden egyeshez hívd meg a `group.appendChild(picture)`‑t. |
| **Különböző alakzattípusok** | Használd a `ShapeType.OVAL`, `ShapeType.LINE` stb. értékeket a `Shape` objektum létrehozásakor. |
| **A csoport pozíciójának módosítása** | A gyermekek hozzáadása után állítsd be a `group.setLeft(x)` és `group.setTop(y)` értékeket a teljes csoport eltolásához. |
| **Exportálás PDF‑be** | A csoportosítás után hívd meg a `doc.save("output.pdf")`‑t; a PDF megőrzi a csoportosítást. |
| **Licenc érvényesítése** | Ha az értékelő verziót használod, vízjel jelenik meg. Telepíts érvényes licencet a vízjel eltávolításához. |

## Összegzés

Most már tudod, hogyan **hozz létre üres Word-dokumentumot**, hogyan szúrj be egy **GroupShape‑ot**, hogyan **állítsd be az alakzat méretét**, **állítsd be az alakzat kitöltőszínét**, és hogyan **adj gyermekelemet a csoporthoz** az Aspose.Words for Java segítségével. Ez a minta lehetővé teszi összetett, programozott elrendezések építését, amelyeket később a Wordben szerkeszthetsz vagy más formátumokba exportálhatsz.

Ezután fedezd fel, hogyan **csoportosíthatsz alakzatokat a Wordben** szövegdobozokkal, hogyan adhatsz hiperhivatkozásokat alakzatokhoz, vagy hogyan automatizálhatod többoldalas jelentések generálását. Ugyanazok a elvek érvényesek – csak hozz létre további alakzatokat, konfiguráld a tulajdonságaikat, és csatold őket ugyanahhoz a csoporthoz.

Jó kódolást!

## Mit érdemes még megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy könnyedén elsajátíthasd az API további funkcióit és alternatív megvalósítási módokat a saját projektjeidben.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}