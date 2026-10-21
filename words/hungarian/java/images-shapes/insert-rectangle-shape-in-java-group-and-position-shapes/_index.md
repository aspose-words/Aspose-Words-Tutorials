---
category: general
date: 2026-07-26
description: Téglalap alakzat beszúrása Java-ban az Aspose.Words használatával. Tanulja
  meg, hogyan állíthatja be az alakzat méretét, pozícióját, és hogyan csoportosíthatja
  az alakzatokat egy DOCX fájlban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: hu
lastmod: 2026-07-26
og_description: Helyezzen be egy téglalap alakzatot Java-ban, hogy gazdag DOCX grafikákat
  hozzon létre. Kövesse ezt a lépésről‑lépésre útmutatót a forma méretének beállításához,
  a forma pozicionálásához és a formák könnyed csoportosításához.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Téglalap alakzat beszúrása Java-ban – A csoportosítás és pozicionálás mestere
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Téglalap alakzat beszúrása Java-ban – Alakzatok csoportosítása és elhelyezése
url: /hu/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rectangle alakzat beszúrása Java‑ban – Alakzatok csoportosítása és pozicionálása

Szükséged volt már **rectangle alakzat beszúrására** egy Word dokumentumba Java kód írása közben? Nem vagy egyedül – a jelentéseket, számlákat vagy egyedi sablonokat készítő fejlesztők gyakran ütköznek ebbe a problémába. A jó hír, hogy néhány sor Aspose.Words for Java‑val könnyedén **beszúrhatod a rectangle alakzatot**, **beállíthatod az alakzat méretét**, **pozicionálhatod az alakzatot**, és még **hogyan csoportosítsuk az alakzatokat**, hogy egy egységként mozogjanak.

Ebben az útmutatóban végigvezetünk a teljes folyamaton, az üres dokumentum létrehozásától egy `.docx` fájl mentéséig, amely két szép módon csoportosított rectangle‑t tartalmaz. A végére megtanulod, **hogyan adjunk hozzá rectangle objektumokat**, hogyan szabályozhatod a méreteiket, hogyan helyezheted őket pontosan a kívánt helyre, és hogyan csomagolhatod őket újrahasználható csoportba. Nem szükséges semmilyen külső könyvtár az Aspose.Words‑en kívül, a kód Java 8‑as vagy újabb verzióval működik.

## Előfeltételek

- Java 8 vagy újabb telepítve (én JDK 17‑et használok, de bármely Maven‑t támogató verzió megfelel)
- Aspose.Words for Java 23.9 vagy későbbi – add hozzá a függőséget a `pom.xml`‑hez vagy töltsd le a JAR‑t
- Alapvető Java szintaxis ismeret (ha tudsz `main` metódust írni, készen állsz)
- Kedvenc IDE‑d vagy szövegszerkesztőd (IntelliJ IDEA, Eclipse, VS Code …)

> **Pro tipp:** Maven‑hez a függőség így néz ki:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Miután felállítottuk az alapokat, merüljünk el a kódban.

## Rectangle alakzat beszúrása és méretének beállítása

Az első lépés egy friss `Document` és egy `DocumentBuilder` létrehozása. A builder a “tollad”, amellyel alakzatokat rajzolsz az oldalra. Az alábbiakban **beszúrunk egy rectangle alakzatot** és azonnal **beállítjuk az alakzat méretét** 100 × 80 pontban.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Vedd észre, hogy a `setWidth`/`setHeight` hívások **pontokban állítják be az alakzat méretét** (1 pt ≈ 1/72 hüvelyk). Használhatod a `setSize` metódust is, ha egyetlen hívást kedvelsz, de a külön hívások egyértelműen kifejezik a szándékot.

## Alakzat pozicionálása az oldalon

Miután megvan az első rectangle, a **második alakzatot** úgy kell **pozicionálni**, hogy ne fedje át az elsőt. A pozicionálás ugyanúgy működik: a `Left` és `Top` tulajdonságokat a csoport origójához képest állítod be.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Ha azon tűnődsz, miért használunk `setLeft`‑t a `setX` helyett, az azért van, mert az Aspose.Words a klasszikus Windows GDI koordináta‑rendszert követi – a `Left` a vízszintes eltolás, a `Top` a függőleges eltolás. Ezeknek az értékeknek a módosításával finomhangolhatod a layout‑ot anélkül, hogy táblázatokkal vagy bekezdésekkel kellene bajlódnod.

## Hogyan csoportosítsuk az alakzatokat

Talán felteszed: „Miért is kell egy csoport?” A csoportosítás akkor hasznos, ha az alakzatoknak együtt kell mozogniuk, egy egységként kell forgatniuk, vagy közös stílust kell megosztaniuk. A fenti kódrészletben már létrehoztunk egy `GroupShape`‑t a `builder.insertGroupShape` segítségével. Ez az objektum lényegében egy tároló – gondolj rá úgy, mint egy mappára, amely más alakzat‑fájlokat tartalmaz.

> **Miért fontos:** Ha később fel szeretnél venni egy feliratot vagy elforgatni az egész diagramot, csak a csoportot kell módosítanod, nem pedig minden egyes rectangle‑t külön‑külön.

## Hogyan adjunk rectangle‑t egy csoporthoz

A **hogyan adjunk rectangle‑t a csoporthoz** egyszerűen a `group.appendChild(rectangle)` meghívása. A háttérben az Aspose.Words frissíti a csoport belső gyűjteményét, és automatikusan újraszámolja a határoló keretet, hogy a csoport továbbra is illeszkedjen a megadott szélességhez és magassághoz.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Kísérletezhetsz más `ShapeType`‑okkal – `ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` stb. – és ugyanaz a `appendChild` minta működik.

## Dokumentum mentése

Végül a dokumentumot lemezre írjuk. Az útvonal lehet abszolút vagy relatív; csak győződj meg róla, hogy a mappa létezik.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Amikor megnyitod a `GroupShape.docx`‑et a Microsoft Word‑ben, két egymás mellett elhelyezkedő rectangle‑t látsz, mindkettő egy világosszürke keretbe van zárva. A szürke keret kiválasztása egyszerre kiemeli mindkét rectangle‑t – bizonyíték arra, hogy a **hogyan csoportosítsuk az alakzatokat** valóban működik.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Rectangle alakzatok példája, amely két rectangle‑t csoportosít egy Java‑val generált DOCX fájlban"}

*Image alt text (SEO):* **rectangle alakzatok példája, amely két rectangle‑t csoportosít egy Java‑val generált DOCX fájlban**.

## Várt kimenet

- Egy `GroupShape.docx` fájl az `output` mappában.
- A dokumentumban egy 400 × 200 pt méretű csoport, amely két rectangle‑t (100 × 80 pt és 120 × 60 pt) tartalmaz, a (20, 30) és (150, 50) koordinátákon elhelyezve.
- A csoport vékony fekete kerettel és világosszürke kitöltéssel rendelkezik, így a csoportosítás vizuálisan is egyértelmű.

Nyisd meg a fájlt, és próbáld meg húzni a szürke keretet – mindkét rectangle‑nek együtt kell mozognia. Ha nem, ellenőrizd, hogy minden alakzathoz meghívtad-e a `group.appendChild`‑t.

## Gyakori hibák és széljegyek

| Probléma | Miért fordul elő | Javítás |
|----------|------------------|---------|
| **A rectangle‑ok az oldal kívülre kerülnek** | A `Left`/`Top` értékek meghaladják a csoport méreteit | Növeld a csoport méretét (`insertGroupShape(width, height)`) vagy csökkentsd az eltolásokat |
| **A csoport eltűnik mentés után** | A csoport `Width`/`Height` értéke 0‑ra van állítva | Adj meg nem‑nulla méreteket a `insertGroupShape` hívásakor |
| **Az alakzat színei helytelenek** | Alapértelmezett kitöltés átlátszó; a Word fehérként jeleníti meg | Állítsd be explicit módon a `setFillColor`‑t vagy használd a `ShapeStyle`‑t |
| **`ArgumentOutOfRangeException` kivétel** | Negatív koordináták használata | Tartsd a `Left` és `Top` értékeket nem‑negatívként |

Ezeknek a korai kezelése megakadályozza a “miért tűnik el az alakzatom?” típusú fejfájásokat, amelyekkel sok újonc szembesül.

## Összefoglalás és következő lépések

Áttekintettük a **rectangle alakzat beszúrásának** teljes életciklusát Java‑ban: dokumentum létrehozása, **alakzat méretének beállítása**, **alakzat pozicionálása**, **alakzatok csoportosítása**, és **rectangle hozzáadása** a csoporthoz. A teljes, futtatható példakód a fenti kódrészletben található, és egyszerűen beilleszthető egy Maven projektbe a végeredmény megtekintéséhez.

Mi a következő? Próbálj ki például:

- Szöveg hozzáadása minden rectangle‑hez via


## Mit érdemes még megtanulni?


Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, segítve, hogy további API‑funkciókat saját projektjeidben is elsajátítsd és alternatív megvalósítási megközelítéseket fedezz fel.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}