---
category: general
date: 2026-10-16
description: Tanulja meg, hogyan csoportosíthatja a formákat a Wordben Java használatával.
  Ez az útmutató bemutatja, hogyan adjon hozzá téglalap alakzatot, állítsa be a forma
  méretét és dimenzióit, és mentse el a dokumentumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: hu
lastmod: 2026-10-16
og_description: Csoportosíts alakzatokat a Wordben Java-val. Adj hozzá téglalap alakzatot,
  állítsd be az alakzat méretét és dimenzióit, és programozottan hozz létre professzionális
  dokumentumokat.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Alakzatok csoportosítása a Wordben Java-val – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Hogyan csoportosítsuk az alakzatokat a Wordben Java-val – teljes útmutató
url: /hu/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan csoportosítsunk alakzatokat a Wordben Java‑val – teljes útmutató

Ha **alakzatokat kell csoportosítania a Wordben** programozottan, ez a bemutató egy azonnal futtatható megoldást nyújt. Megmutatjuk, hogyan **adjunk hozzá egy téglalap alakzatot**, állítsuk be a méretét, határozzuk meg az alakzat dimenzióit, és végül mentsünk egy DOCX fájlt, amely egy csoportosított téglalapot és egy ellipszist tartalmaz.

Az alakzatok csoportosítása a Wordben hasznos összetett diagramok építéséhez, újrahasználható grafikus komponensek létrehozásához, vagy egyszerűen a kapcsolódó objektumok együtt tartásához, amikor a dokumentumot később szerkesztik. A kód az Aspose.Words for Java könyvtárat használja, amely bármely friss JDK‑val működik, és nem igényli a Microsoft Word telepítését.

## Előfeltételek

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik a következőkkel:

| Követelmény | Ok |
|-------------|----|
| Java 17 (vagy újabb) | A könyvtár a modern Java futtatókörnyezetekre van optimalizálva. |
| Aspose.Words for Java (legújabb verzió) | Biztosítja a példában használt `Document`, `DocumentBuilder`, `GroupShape` és `Shape` osztályokat. |
| IDE vagy build eszköz (Maven/Gradle) | A minta lefordításához és futtatásához. |
| Alapvető Java szintaxis ismeret | Szükséges a kódfolyamat megértéséhez. |

Adja hozzá az Aspose.Words függőséget a projektjéhez. Maven esetén:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Vagy Gradle esetén:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## A megoldás áttekintése

A bemutató egyértelmű **probléma → megoldás → magyarázat** mintát követ:

1. **Új Word dokumentum létrehozása** és egy `DocumentBuilder` beszerzése.  
2. **`GroupShape` tároló beszúrása**, amely több alakzatot fog tartalmazni.  
3. **Téglalap hozzáadása**, szélesség/magasság beállítása (a **set shape size** lépés), és csatolása a csoporthoz.  
4. **Ellipszis hozzáadása**, elhelyezése ugyanabban a csoportban, és a dimenziók beállítása.  
5. **Mentés** a lemezen.

Minden lépés tartalmazza a **miért** magyarázatát, így megérti, mit csinál az API, és hogyan alkalmazhatja más helyzetekben.

## 1. lépés: Dokumentum és DocumentBuilder létrehozása

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Miért fontos:** A `Document` a teljes DOCX fájlt képviseli, míg a `DocumentBuilder` egy segédeszköz, amely lehetővé teszi a tartalom beszúrását anélkül, hogy alacsony szintű csomópontkezeléssel kellene foglalkozni. Ezek előzetes létrehozása tiszta vásznat biztosít a további alakzatműveletekhez.

## 2. lépés: GroupShape tároló beszúrása

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

A `GroupShape` úgy működik, mint egy **mappa** a rajzobjektumok számára. Ha a csoportot mozgatja, elforgatja vagy törli, az összes gyermekalakzat automatikusan követi. Ez a **group shapes in word** lényege.

## 3. lépés: Téglalap alakzat hozzáadása – a téglalap kódja

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – A `Shape` konstruktor a `ShapeType.RECTANGLE` értéket kapja, amely azt mondja az Aspose.Words‑nek, hogy egy téglalap körvonalat rajzoljon.  
- **set shape size** – A `setWidth` és `setHeight` a **shape dimensions**‑t pontban (1 pt = 1/72 in) definiálja. Ez a leggyakoribb módja a vizuális méret szabályozásának.  
- **Why we use `appendChild`** – Ez csatolja a téglalapot a `GroupShape`‑hez, így együtt mozog a csoporttal.

## 4. lépés: Ellipszis hozzáadása és elhelyezése a csoporton belül

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

Az ellipszis bemutatja a **set shape dimensions** használatát egy egyszerű téglalapon túl. A `setLeft` hívásával a vízszintes eltolást szabályozzuk a csoporton belül, ami több objektum elrendezésekor hasznos.

## 5. lépés: Dokumentum mentése

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Amikor megnyitja a *GroupShapeDemo.docx* fájlt a Microsoft Wordben, egy téglalapot és egy ellipszist lát, amelyek egyetlen csoportba vannak zárva. Bármelyik alakzat kiválasztása az egész csoportot kiválasztja – pontosan azt, amit elvárunk a **group shapes in word** esetén.

## Teljes, futtatható példa

Az összes részt egyesítve, itt a teljes forrásfájl, amelyet átmásolhat az IDE‑jébe:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Várt kimenet

- A projekt mappájában megjelenik egy **GroupShapeDemo.docx** nevű fájl.  
- A fájl megnyitása Wordben két alakzatot (téglalap és ellipszis) mutat, amelyek együtt vannak csoportosítva.  
- Bármelyik alakzat húzása az egész csoportot mozgatja, bizonyítva, hogy a **group shapes in word** a várt módon működik.

## Gyakori variációk és szélhelyzetek

| Forgatókönyv | Mit kell módosítani | Miért |
|--------------|---------------------|-------|
| **Eltérő alakzat típusok** (pl. háromszög) | Használja a `ShapeType.TRIANGLE` vagy bármely más enum értéket a `Shape` konstruktorában. | Lehetővé teszi összetettebb diagramok építését. |
| **Kitöltő szín beállítása** | Hívja a `shape.getFillColor().setColor(Color.BLUE);`‑t az alakzat létrehozása után. | Javítja a vizuális megjelenést anélkül, hogy a csoportosítást befolyásolná. |
| **A csoport forgatása** | `groupShape.setRotationAngle(45);` | Az összes gyermekalakzatot együtt forgatja, ami ikonoknál hasznos. |
| **Szöveg hozzáadása egy alakzathoz** | `shape.appendChild(new Paragraph(document));` majd egy `Run` szöveggel. | Az alakzatot címkévé vagy felhívássá alakítja. |
| **Mentés stream‑be** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Hasznos webszolgáltatásoknál, ahol a dokumentumot közvetlenül kell visszaadni. |

### Profi tipp

Amikor **set shape dimensions**‑t kell dinamikus adatok alapján meghatározni (pl. vonalkód hossza), először számolja ki a szélességet/magasságot pontban:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

Ez elkerüli a keménykódolt értékeket, és rugalmasabbá teszi a kódot.

## Összegzés

Most már tudja, hogyan **csoportosítsa az alakzatokat a Wordben** Java‑val, hogyan **adjunk hozzá téglalap alakzatot**, és hogyan **állítsuk be az alakzat méretét** valamint **az alakzat dimenzióit** egy tömör, termelés‑kész kóddal. A fenti lépéseket követve újrahasználható grafikus csoportokat hozhat létre, beágyazhatja őket automatizált jelentésekbe, vagy saját diagramkészítő eszközöket építhet anélkül, hogy a Wordet manuálisan megnyitná.

### Mi a következő?

- Fedezze fel a **add rectangle shape** variációkat, például a lekerekített sarkokat (`ShapeType.RECTANGLE` `setCornerRadius`‑el).  
- Kombinálja a **group shapes in word**‑t táblázatokkal vagy diagramokkal a gazdagabb dokumentumokért.  
- Tekintse meg az Aspose.Words API‑t a **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) kezeléséhez, hogy szabályozza a környező szöveg viselkedését a csoportosított grafikák körül.

Kísérletezzen, módosítsa a **rectangle shape code**‑ot, és ossza meg az eredményeket.


## Mit érdemes legközelebb megtanulni?


Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}