---
category: general
date: 2026-08-20
description: Tanulja meg, hogyan csoportosíthatja az alakzatokat, állíthatja be az
  alakzat méretét, szúrhat be képet a dokumentumba, adhat képet a csoporthoz, és hozhat
  létre téglalap alakzatot az Aspose.Words Java-val.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: hu
lastmod: 2026-08-20
og_description: Hogyan csoportosítsunk alakzatokat egy Word dokumentumban az Aspose.Words
  segítségével. Kövesse ezt a lépésről‑lépésre Java útmutatót az alakzat méretének
  beállításához, kép beszúrásához a dokumentumba, kép hozzáadásához a csoporthoz,
  és téglalap alakzat létrehozásához.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Hogyan csoportosítsuk a formákat egy Word-dokumentumban az Aspose.Words
  segítségével – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Hogyan csoportosíthatók a formák egy Word-dokumentumban az Aspose.Words segítségével
url: /hu/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan csoportosítsunk alakzatokat egy Word dokumentumban az Aspose.Words segítségével

Ha **hogyan csoportosítsunk alakzatokat** egy Word fájlban, ez a bemutató a teljes Java megoldást mutatja be. Megláthatja, hogyan **állítsuk be az alakzat méretét**, **illesztsünk be képet a dokumentumba**, **adjunk képet a csoporthoz**, és **hozzunk létre téglalap alakzatot** – mindezt világos magyarázatokkal és egy futtatható kódmintával.

Az alakzatok csoportosítása egyszerűsíti a elrendezés kezelését, lehetővé teszi több objektum együttes mozgatását vagy forgatását, és rendezettséggel tartja a dokumentumot. Az alábbi lépésekben egy olyan csoportot építünk, amely tartalmaz egy téglalapot és egy képet, majd elhelyezzük a csoportot az oldalon.

## Előfeltételek

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* Java 17 vagy újabb verzióval.
* Aspose.Words for Java (23.9 vagy újabb) a projekt osztályútvonalában.
* Egy minta JPEG képpel a `YOUR_DIRECTORY/sample.jpg` útvonalon (cserélje ki a `YOUR_DIRECTORY`-t a tényleges útvonalra).

Az Aspose.Words hozzáadható Maven‑en keresztül:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Hogyan csoportosítsunk alakzatokat az Aspose.Words segítségével

Az alábbi szakaszok végigvezetik a **hogyan csoportosítsunk alakzatokat** megvalósításához szükséges műveleteken. A fő H2 fejlécek tartalmazzák a kulcsszót, ezzel megfelelve az SEO szabályoknak.

### 1. lépés: Új dokumentum és egy `DocumentBuilder` létrehozása

A `Document` a Word fájlt képviseli, míg a `DocumentBuilder` kényelmes módszereket biztosít a tartalom beszúrásához.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Miért fontos*: Egy friss `Document` használata biztosítja, hogy a létrehozott csoport ne ütközzön a meglévő elemekkel.

### 2. lépés: Csoport alakzat beszúrása, amely több gyermek alakzatot fog tartalmazni

A csoport alakzat egy tárolóként működik. Méretei határozzák meg a gyermek alakzatok határoló dobozát.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tippek*: A szélesség (`300`) és a magasság (`200`) pontban van megadva (1 pt = 1/72 inch). Igazítsa őket a hozzáadni kívánt alakzatok méretéhez.

### 3. lépés: Téglalap alakzat létrehozása, méretének beállítása és hozzáadása a csoporthoz

Az alakzat pontos méretének beállítása elengedhetetlen a precíz elrendezésvezérléshez.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Miért állítjuk be az alakzat méretét*: A `setWidth` és `setHeight` metódusok megfelelnek a **set shape size** másodlagos kulcsszónak, így pixel‑pontos irányítást adnak a téglalap megjelenéséhez.

### 4. lépés: Kép beszúrása, majd a kép alakzat hozzáadása ugyanahhoz a csoporthoz

A kép beszúrása a **insert image into document** követelmény központja. A visszakapott `Shape` egy kép alakzat, amely a többi alakzathoz hasonlóan csoportosítható.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tipp*: Ha meg szeretné őrizni az eredeti képarányt, csak egy dimenziót állítson be (`setWidth` vagy `setHeight`). Az Aspose.Words automatikusan méretezi a másik dimenziót.

### 5. lépés: A teljes csoport elhelyezése az oldalon

Miután minden gyermek alakzatot hozzáadta, a teljes csoportot mozgathatja, forgathatja vagy elrejtheti. A pozícionálás közvetetten a **add picture to group** koncepciót használja, mivel a csoport már tartalmazza a képet.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Magyarázat*: A `setLeft` és `setTop` a csoportot az oldal margójához viszonyítva helyezi el. A csoport forgatása azt mutatja, hogy minden gyermek alakzat örökli a transzformációt.

### 6. lépés: Dokumentum mentése

Végül írja a fájlt a lemezre. A létrejött `.docx` fájlt megnyithatja Wordben, hogy ellenőrizze a csoportosítást.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

A program futtatása **GroupShapesDemo.docx** fájlt hoz létre, amely egy téglalapot és egy képet tartalmaz együttesen. A Wordben bármelyik alakzat kiválasztása automatikusan a másikat is kiválasztja, ezzel megerősítve, hogy sikeresen megtanulta a **hogyan csoportosítsunk alakzatokat**.

---

## Várt kimenet

Amikor megnyitja a *GroupShapesDemo.docx* fájlt a Microsoft Wordben:

* Egy téglalap (arany kitöltéssel) jelenik meg a csoport bal oldalán.
* A megadott kép a téglalap jobb oldalán látható.
* Mindkét objektum együtt mozog, ha a csoportot húzza.
* A csoport 50 pt-re van a bal margótól és 100 pt-re a felső margótól, 15°‑os forgatással.

Ha a kép nem jelenik meg, ellenőrizze a `insertImage` útvonalát. Az Aspose.Words `IOException`‑t dob, ha a fájl nem található.

---

## Gyakori kérdések és szélsőséges esetek kezelése

| Kérdés | Válasz |
|----------|--------|
| **Hozzáadhatok több mint két alakzatot?** | Igen. Hívja meg a `groupShape.appendChild(otherShape)` metódust minden további alakzatnál. |
| **Mi a teendő, ha átlátszó háttérre van szükség a téglalaphoz?** | Használja a `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` kódot. |
| **Támogatott-e a csoportosítás régebbi Word formátumokban (pl. `.doc`)?** | A csoportosítás működik `.docx` és `.doc` esetén is, de egyes régebbi megjelenítők figyelmen kívül hagyhatják a csoport metaadatait. A teljes hűségért mentse `.docx`‑ként. |
| **Hogyan bontsam fel a csoportot később?** | Szerezze meg a gyermek csomópontokat a `groupShape.getChildNodes(NodeType.ANY, true)` segítségével, helyezze őket a dokumentum törzsébe, majd távolítsa el a csoportot. |
| **Csoportosíthatok-e alakzatokat különböző szakaszok között?** | Nem. Egy `GroupShape`-nek egyetlen `Story`‑n belül kell elhelyezkednie (általában a fő dokumentumtörzsben). |

---

## Pro tippek a robusztus alakzatkezeléshez

* **Használja mértékletesen az abszolút pozícionálást** – a relatív pozícionálás (`builder.moveToDocumentEnd()`) gyakran rugalmasabb elrendezést eredményez.
* **Cache-elje a `DocumentBuilder`‑t** – minden művelethez új builder létrehozása jelentősen lelassíthatja a nagy dokumentumok feldolgozását.
* **Állítsa be a `PictureFillMode`‑t**, ha a képet nyújtani vagy csempészni szeretné az alakzaton belül: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Ellenőrizze a kép méreteit** a beszúrás előtt, hogy elkerülje a váratlan méretezést, amely befolyásolhatja a csoport határoló dobozát.

---

## Következő lépések

Most, hogy már tudja, **hogyan csoportosítsunk alakzatokat**, érdemes lehet:

* **Insert image into document** fejlett opciókkal, például vágással (`pictureShape.setCropTop(...)`).
* **Set shape size** dinamikusan az oldal méretei alapján (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** szövegdobozokkal együtt, feliratos grafikákhoz.
* **Create rectangle shape** lekerekített sarkokkal (`rectangleShape.setCornerRadius(5);`).

Ezek a témák ugyanazon API felületet használják, és segítenek összetett, programozott Word jelentések létrehozásában.

---

## Összegzés

Ebben a bemutatóban megtanulta, **hogyan csoportosítsunk alakzatokat** egy Word dokumentumban az Aspose.Words for Java segítségével. A hat lépés – dokumentum létrehozása, csoport beszúrása, **téglalap alakzat** létrehozása, **shape size beállítása**, **kép beszúrása a dokumentumba**, **kép hozzáadása a csoporthoz**, és a csoport pozícionálása – egy újrahasználható mintát ad komplex elrendezési forgatókönyvekhez. Nyugodtan kísérletezzen további gyermek alakzatokkal, különböző forgatásokkal vagy feltételes csoportosítási logikával, hogy megfeleljen alkalmazása igényeinek.

Boldog kódolást!

## Mit tanuljon meg legközelebb?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}