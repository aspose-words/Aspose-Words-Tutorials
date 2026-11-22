---
category: general
date: 2026-11-22
description: Adj hozzá egy téglalap alakzatot egy Word-dokumentumhoz Java-val, állítsd
  be az alakzat méretét, csoportosíts több alakzatot, és hatékonyan illeszd be az
  alakzatot a csoportba.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: hu
lastmod: 2026-11-22
og_description: Adjunk hozzá egy téglalap alakzatot egy Word-dokumentumhoz Java-val,
  majd állítsuk be az alakzat méretét, csoportosítsunk több alakzatot, és egyetlen
  munkafolyamatban fűzzük hozzá az alakzatot a csoporthoz.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Téglalap alakzat hozzáadása és alakzatok csoportosítása Java-ban – teljes
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Téglalap alakzat hozzáadása és alakzatok csoportosítása Java-ban
url: /hu/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat hozzáadása és alakzatok csoportosítása Java-ban

Ha **téglalap alakzatot** szeretne hozzáadni egy Word dokumentumhoz Java-val, ez az útmutató lépésről lépésre végigvezet a folyamaton. Megtanulja, hogyan **állítsa be az alakzat méretét**, **csoportosítson több alakzatot**, és hogyan **csatolja az alakzatot a csoporthoz** anélkül, hogy elhagyja az IDE-t.

A vektorgrafikával való munka egy DOCX fájlban gyakran olyan, mintha különálló API-kkal kellene birkózni. A tutorial végére egy önálló, egyetlen programmal rendelkezik, amely létrehozza a téglalapot, egy ellipszist és bármilyen további alakzatot, majd csoportosítja őket, hogy egy objektumként mozogjanak. Külső eszközökre nincs szükség, csak az Aspose.Words for Java-ra.

## Előfeltételek

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* Java 17 vagy újabb telepítve.
* Maven 3.8+ (vagy Gradle) a függőségek kezeléséhez.
* Érvényes Aspose.Words for Java licenc (értékelő verzió teszteléshez is megfelelő).
* IDE, például IntelliJ IDEA vagy VS Code, bár bármely szövegszerkesztő is megfelel.

Ezek a követelmények biztosítják, hogy a kód lefordul és futtatható legyen bármely modern fejlesztői környezetben.

## 1. lépés: Maven projekt beállítása

Hozzon létre egy új Maven projektet, vagy adja hozzá az Aspose.Words függőséget egy meglévő `pom.xml`-hez:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

A függőség letölti a dokumentummanipulációhoz szükséges összes osztályt, beleértve a `Document`, `DocumentBuilder`, `Shape` és `GroupShape` osztályokat. A Maven automatikusan letölti a JAR-okat, amikor a `mvn compile` parancsot futtatja.

## 2. lépés: Dokumentum betöltése és DocumentBuilder létrehozása

A `DocumentBuilder` biztosítja a folyékony API-t a tartalom beszúrásához. Töltsön be egy meglévő DOCX-et, vagy kezdjen egy üres dokumentummal:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A builder korai létrehozása egy olyan kurzort ad, amely a dokumentum elején helyezkedik el, készen áll az alakzatok beszúrására.

## Téglalap alakzat hozzáadása egy Word dokumentumhoz

### 3. lépés: Téglalap alakzat beszúrása

A téglalap az első vizuális elem, amelyet a dokumentumba szeretnénk helyezni. A `Shape` konstruktor `ShapeType.RECTANGLE` paraméterrel való használata egy teljesen szerkeszthető objektumot ad.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

A téglalap ebben a pontban történő hozzáadása nem befolyásolja a layoutot, amíg a mérete nincs meghatározva és nem kerül egy tárolóba.

### Alakzat méretének és dimenzióinak beállítása

#### 4. lépés: Szélesség és magasság meghatározása

Az alakzat méretének beállítása határozza meg, hogyan jelenik meg az oldalon. A szélesség és magasság értékeket pontban mérik (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Ezeket a számokat a tervezési igényeknek megfelelően módosíthatja. Ugyanezek a módszerek minden `Shape` példányra alkalmazhatók, így újra felhasználhatók körök, nyilak vagy egyedi rajzok esetén is.

#### 5. lépés: Téglalap beszúrása a dokumentumba

Miután a téglalap mérete megvan, helyezze el az oldalon. A `DocumentBuilder` `insertShape` metódusa a jelenlegi kurzorpozícióba szúrja be az alakzatot.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

Ebben a szakaszban a téglalap egyedül jelenik meg az oldalon. A következő lépések bemutatják, hogyan kombinálható más alakzatokkal.

## Több alakzat csoportosítása

Az alakzatok csoportosítása lehetővé teszi, hogy egy egységként mozgassuk, forgassuk vagy méretezzük őket. Ez különösen hasznos összetett diagramok létrehozásakor.

### 6. lépés: Csoport alakzat tároló létrehozása

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

A `insertGroupShape` hívás egy üres tárolót ad a dokumentumhoz. Az ebbe a tárolóba hozzáadott alakzatok a csoport részévé válnak.

### Alakzat csatolása a csoporthoz

#### 7. lépés: Téglalap hozzáadása a csoporthoz

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

A csatolás a téglalapot a dokumentum törzséből a csoport belső gyűjteményébe helyezi. A téglalap most már a csoport transzformációit követi.

#### 8. lépés: Ellipszis hozzáadása demonstrációként

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Az ellipszis ugyanabban a koordináta-rendszerben osztozik a téglalappal, így vizuálisan igazítható a `setLeft` és `setTop` tulajdonságok módosításával, ha szükséges.

### 9. lépés: Dokumentum mentése

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

A program futtatása létrehozza az `output.docx` fájlt. Nyissa meg a Microsoft Word vagy LibreOffice programban; egy téglalap és egy ellipszis lesz csoportosítva együtt. Bármelyik alakzat kiválasztása kiemeli az egész csoportot, ami megerősíti, hogy a **csatolás a csoporthoz** sikeres volt.

![Add rectangle shape example in Java](image.png){alt="Téglalap alakzat hozzáadása példája Java-ban"}

*A képernyőkép a téglalapot és az ellipszist egyetlen csoportban mutatja, készen állva a közös manipulációra.*

## Miért fontos ez a megközelítés

* **Egyetlen igazságforrás** – Minden alakzat tulajdonságát a csoport létrehozása előtt állítjuk be, ezáltal elkerülve a layout hibákat.
* **Újrahasználhatóság** – Ugyanazok a `setWidth`/`setHeight` metódusok minden alakzatra alkalmazhatók, így a példát nyilakra, csillagokra vagy egyedi SVG-re is kiterjesztheti.
* **Teljesítmény** – A csoportosítás csökkenti a Word renderelőnek kezelendő rajzobjektumok számát, ami javítja a nagy dokumentumok megnyitási sebességét.
* **Karbantarthatóság** – Az alakzat létrehozási és csoportosítási logika egy helyen tartásával a jövőbeni fejlesztők könnyen módosíthatják a méreteket vagy új alakzatokat adhatnak hozzá anélkül, hogy keresgélniük kellene a kódban.

## Gyakori variációk és szélhelyzetek

| Szenárió | Módosítás |
|----------|------------|
| **Eltérő egységek** | Használja a `PointsToPixels` konverziót vagy állítsa be a `Shape.setWrapType(WrapType.INLINE)`-t az inline elhelyezéshez. |
| **A csoport forgatása** | Hívja meg a `groupShape.setRotation(45);` metódust, hogy az összes gyermek alakzatot 45°-kal forgassa. |
| **Szöveg hozzáadása egy alakzathoz** | Használja a `Shape.setText("Label");` metódust a méret beállítása után. |
| **Dinamikus méretezés** | Szerezze be az oldal méreteit a `doc.getFirstSection().getPageSetup().getPageWidth()` segítségével, és számolja ki az alakzat méreteket arányosan. |

Ezek a variációk azt mutatják, hogyan alkalmazható az alapminta – **téglalap alakzat hozzáadása**, **alakzat méretének beállítása**, **több alakzat csoportosítása**, **alakzat csatolása a csoporthoz** – számos valós igényhez.

## Következtetés

Most már tudja, hogyan **adjunk hozzá téglalap alakzatot** egy Word dokumentumhoz Java-val, hogyan **állítsuk be az alakzat méretét**, hogyan **csoportosítsunk több alakzatot**, és hogyan **csatoljuk az alakzatot a csoporthoz** tiszta, karbantartható módon. A teljes példa egyetlen futtatható osztályba fordítható, és a keletkezett DOCX fájl bemutatja a várt eredményt.

Innen tovább felfedezheti:

* Szövegcímkék vagy hiperhivatkozások hozzáadása az egyes alakzatokhoz.
* Csoportok egymásba ágyazása hierarchikus diagramok építéséhez.
* A dokumentum PDF‑be exportálása a formai csoportok megőrzésével.

Kísérletezzen különböző méretekkel, színekkel és további alakzat típusokkal. Az alakzatkezelés elsajátítása lehetővé teszi az automatizált jelentéskészítést, dinamikus diagramok és gazdag dokumentumélményeket – mindezt közvetlenül Java kódból.

## Mit tanuljon meg legközelebb?


Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}