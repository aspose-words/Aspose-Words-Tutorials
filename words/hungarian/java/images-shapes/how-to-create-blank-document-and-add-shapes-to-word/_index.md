---
category: general
date: 2026-09-18
description: Hozzon létre egy üres dokumentumot, és szúrjon be alakzatokat a Wordbe
  az Aspose.Words segítségével – tanulja meg, hogyan adjon hozzá háromszög alakzatot
  és még sok mást.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: hu
lastmod: 2026-09-18
og_description: Készítsen üres dokumentumot a Wordben az Aspose.Words használatával,
  és tanulja meg, hogyan illesszen be háromszög alakzatot, csoportosítson alakzatokat
  és egyéb grafikákat. Kövesse ezt a teljes útmutatót.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Üres dokumentum létrehozása és alakzatok hozzáadása a Wordhöz – lépésről
  lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Hogyan hozzunk létre üres dokumentumot, és adjunk hozzá alakzatokat a Wordben
url: /hu/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre üres dokumentumot és adjunk hozzá alakzatokat a Wordhöz

Ha **üres dokumentumot kell létrehoznod** és azt grafikákkal szeretnéd gazdagítani, ez az útmutató pontosan megmutatja, hogyan. Lépésről lépésre végigvezetünk egy Word fájl létrehozásán az elejétől, és **alakzatok hozzáadását a Wordhöz**, beleértve a **háromszög alakzat beillesztésének** módját, az Aspose.Words for Java használatával.

A tutorial végére egy használatra kész *.docx* fájlt kapsz, amely egy csoportosított alakzatot tartalmaz, benne egy háromszöggel. A lépések mindent lefednek a projekt beállításától a végső **create word document** mentéséig. Az Aspose.Words-on kívül nincs szükség külső eszközökre.

## Előfeltételek

* Java 17 vagy újabb telepítve  
* Maven vagy Gradle a függőségkezeléshez  
* Aspose.Words for Java licenc (az ingyenes értékelés működik ebben a demóban)  

Ha más build rendszert részesítesz előnyben, állítsd be ennek megfelelően a függőségi szintaxist. A kód bármely, Java-t támogató platformon működik.

## Üres dokumentum létrehozása az Aspose.Words segítségével

Az első művelet a **üres dokumentum** létrehozása memóriában. Az Aspose.Words egy `Document` osztályt biztosít, amely egy tartalom nélküli Word fájlt képvisel.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

A `new Document()` konstruktor egy üres *.docx* struktúrát hoz létre, amelyet később bekezdésekkel, táblázatokkal vagy grafikákkal tölthetsz fel. Mivel a dokumentum üres, teljes irányítással rendelkezel minden hozzáadott elem felett.

## Alakzatok hozzáadása a Wordhöz – csoportos alakzat beillesztése

A csoportos alakzat lehetővé teszi, hogy több grafikát egy egységként kezelj. Ez akkor hasznos, ha egyszerre szeretnél több alakzatot mozgatni vagy átméretezni.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` az elsődleges API a tartalom hozzáadásához. Az `insertGroupShape` hívás egy 300 × 300 pont (kb. 4 × 4 hüvelyk) méretű konténert hoz létre. Ezután a kurzor a *csoporton belül* helyezkedik el, készen állva további alakzatok hozzáadására.

### Miért használjunk csoportos alakzatot?

A csoportosítás a kapcsolódó grafikákat igazítva tartja, és megkönnyíti az egységes formázás alkalmazását. Ha később úgy döntesz, hogy a háromszöget áthelyezed, az egész csoport együtt mozog, megőrizve az elrendezést.

## Háromszög alakzat beillesztése a csoporton belül

Most a **háromszög beillesztésének** módját tárgyaljuk. A háromszög az egyik beépített `ShapeType` érték.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

A `moveTo` hívás biztosítja, hogy a builder beszúrási pontja a csoport első bekezdése legyen. Az `insertShape` ezután egy 60 × 60 pont méretű háromszöget ad hozzá. Mivel a kurzor a csoporton belül van, a háromszög a csoportos alakzat gyermekeként jelenik meg.

**Háromszög alakzat hozzáadása** tippek:

* A méret pontban van megadva; 72 pont egy hüvelyknek felel meg. Állítsd a méreteket a saját elrendezésedhez.  
* Ha más orientációra van szükséged, használd a `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` metódust az alakzat csoporton belüli igazításához.  
* A háromszög örökli a csoport kitöltési és vonalstílusát, hacsak nem felülírod őket a `shape.getFillColor()` vagy `shape.getStrokeColor()` segítségével.

## Dokumentum mentése – create word document

A grafikák összeállítása után mented a fájlt. Ez a lépés befejezi a **create word document** műveletet.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

A `doc.save` a memóriában lévő reprezentációt lemezre írja szabványos Word dokumentumként. Megnyithatod a `ExtendedGroup.docx` fájlt a Microsoft Wordben, LibreOffice-ban vagy bármely, az OOXML formátumot támogató megjelenítőben. A fájl egy csoportosított alakzatot mutat, amely háromszöget tartalmaz, pontosan úgy, ahogy a kód felépítette.

## Teljes futtatható példa

Az összes részt összevonva, itt a teljes program, amelyet másolhatsz, lefordíthatsz és futtathatsz:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Várható eredmény

Amikor megnyitod a `ExtendedGroup.docx` fájlt, egyetlen csoportos alakzatot látsz, amely az oldal közepét foglalja. A csoporton belül egy kis háromszög jelenik meg az alapértelmezett pozícióban. A háromszög kiválasztható és a csoport részeként mozgatható, ami megerősíti, hogy a **add shapes to word** megfelelően működött.

## Gyakori kérdések és speciális esetek

| Question | Answer |
|----------|--------|
| *Hozzáadhatok több mint egy alakzatot a csoporton belül?* | Igen. A háromszög beillesztése után tartsd a kurzort a csoporton belül, és hívd meg újra a `builder.insertShape`-t egy másik `ShapeType`-tal. |
| *Mi van, ha a háromszöget pirosra szeretném?* | Szerezd meg az `insertShape` által visszaadott `Shape` objektumot, és hívd a `shape.getFillColor().setColor(Color.RED)` metódust. |
| *Működik ez régebbi .doc fájlokkal?* | Az Aspose.Words a megadott formátumban ment. Használd a `doc.save("file.doc", SaveFormat.DOC)` parancsot egy régi Word dokumentum létrehozásához. |
| *Hogyan változtathatom meg a csoport szegélyét?* | Használd a `group.getStrokeColor().setColor(Color.BLUE)` és a `group.setLineWeight(2.0)` metódusokat a körvonal testreszabásához. |
| *Van mód a háromszög elforgatására?* | Hívd a `shape.getRotation()` metódust, hogy fokban állíts be egy szöget. |

## Pro tippek

* **Használd újra a builder-t** – minden alakzathoz új `DocumentBuilder` létrehozása többletterhet jelent. Tarts egyetlen builder-t dokumentumonként.  
* **Mértékegység átváltás** – ha milliméterrel dolgozol, konvertáld pontokra (`points = mm * 2.83465`).  
* **Teljesítmény** – nagy dokumentumok esetén hívd a `doc.updatePageLayout()`-t csak egyszer, miután az összes alakzat hozzá lett adva.

## Következtetés

Most már tudod, hogyan **hozz létre üres dokumentumot**, **adj hozzá alakzatokat a Wordhöz**, és konkrétan **hogyan illessz be háromszög** alakzatot az Aspose.Words for Java használatával. A teljes példa bemutatja a teljes munkafolyamatot egy üres fájltól a mentett **create word document**-ig, amely egy csoportosított háromszöget tartalmaz.

Innen tovább felfedezheted a további `ShapeType` értékeket, alkalmazhatsz egyedi stílusokat, vagy több csoportot kombinálhatsz összetett diagramok építéséhez. Kísérletezz különböző méretekkel, színekkel és pozíciókkal, hogy mesterré válj a Word automatizálásában Java-ban.

--- 

*Készen állsz a következő jelentésed automatizálására? Klónozd a példát, módosítsd a méreteket, és integráld a kódot saját alkalmazásodba még ma.*

## Mit érdemes legközelebb megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}