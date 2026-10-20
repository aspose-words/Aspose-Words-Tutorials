---
category: general
date: 2026-10-20
description: Hogyan csoportosítsunk alakzatokat az Aspose.Words for Java-ban – tanulja
  meg, hogyan szúrjon be téglalap alakzatot, csoportosítsa őket, és mentse el a dokumentumot
  egyetlen útmutatóban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: hu
lastmod: 2026-10-20
og_description: Hogyan csoportosítsunk alakzatokat az Aspose.Words for Java-ban. Ez
  az útmutató bemutatja, hogyan szúrjunk be téglalap alakzatot, csoportosítsuk őket,
  és exportáljuk az eredményt.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Hogyan csoportosítsuk az alakzatokat az Aspose.Words for Java-ban – lépésről
  lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Hogyan csoportosítsuk az alakzatokat az Aspose.Words for Java-ban
url: /hu/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan csoportosítsunk alakzatokat az Aspose.Words for Java-ban

Ha **hogyan csoportosítsunk alakzatokat** kell egy Word-dokumentumban az Aspose.Words for Java használatával, ez az útmutató bemutatja a teljes munkafolyamatot. Megtanulja, hogyan **szúrjon be téglalap alakzatot**, adjon hozzá egy második téglalapot, csoportosítsa a két alakzatot, és végül mentse a fájlt – mindezt egyértelmű, futtatható kóddal.

Az alakzatok csoportosítása akkor hasznos, ha több rajzot szeretne egy egységként mozgatni, forgatni vagy formázni. Legyen szó jelentés sablonról, diagramról vagy egyedi szórólapról, a csoportosítás elsajátítása időt takarít meg, és biztosítja a konzisztens elrendezést.

Ebben az oktatóanyagban Ön:

* Létrehoz egy új `Document`‑et és egy `DocumentBuilder`‑t.
* **Hogyan szúrjon be téglalap** alakzatokat pontos méretekkel.
* Csoportosítja a téglalapokat egy `GroupShape`‑be.
* Elmenti a dokumentumot és ellenőrzi az eredményt.

> **Előfeltétel** – Telepítve kell legyen az Aspose.Words for Java (v23.12 vagy újabb) a projektben. Maven‑felhasználók a lent látható függőséget adhatják hozzá.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Amire szüksége lesz

| Elem | Indoklás |
|------|----------|
| Java 17+ | Modern nyelvi funkciók és jobb teljesítmény |
| Aspose.Words for Java | Biztosítja a `DocumentBuilder`, `Shape` és `GroupShape` API‑kat |
| Fejlesztői környezet (IntelliJ IDEA, Eclipse, VS Code, stb.) | A példa lefordításához és futtatásához |
| Írási jogosultság egy mappához | A dokumentumot le kell menteni a lemezen |

---

## Hogyan szúrjon be téglalap alakzatot

Az első lépés egy `Document` és egy `DocumentBuilder` létrehozása. A builder olyan metódusokat kínál, mint az `insertShape`, amely a rajzobjektumok elhelyezésére szolgál.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Miért fontos** – Az `insertShape` használata a szabványos módja **hogyan szúrjon be téglalap** objektumokat az Aspose.Words‑ben. Automatikusan a dokumentum aktuális bekezdésébe helyezi az alakzatot, így nem kell alacsony szintű OpenXML‑et kezelnie.

---

## Téglalap pozíciók módosítása (opcionális)

Ha a második téglalapnak egyedi helyzetre van szüksége az elsőhöz képest, módosíthatja a `left` és `top` tulajdonságait. Ez a lépés opcionális, de gyakran szükséges a pontos diagramelrendezéshez.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tipp:** Minden mérés pontban (1 pt ≈ 1/72 in) történik. Használja a `convertPointsToPixels`‑t, ha pixelértékekre van szüksége UI‑alapú számításokhoz.

---

## Hogyan csoportosítsunk alakzatokat

Miután a téglalapok léteznek, elhelyezhetjük őket egy `GroupShape`‑ben. A csoportosítás miatt a két téglalap egyetlen objektumként viselkedik – a csoport mozgatása, forgatása vagy formázása mindkét alakzatot érinti.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Miért működik a csoportosítás** – A `GroupShape` a `Shape`‑ből örököl, így a csoportot ugyanúgy kezelheti, mint bármely más rajzobjektumot. Amikor az `appendChild`‑et hívja, az alakzatok eltávolításra kerülnek az eredeti helyükről, és a csoport gyermekei lesznek.

---

## A csoportosított alakzatokat tartalmazó dokumentum mentése

Végül írja a dokumentumot a lemezre. A fájl egyetlen `GroupShape`‑t fog tartalmazni, amelyben két téglalap található.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Várt eredmény

Nyissa meg a `GroupShape.docx` fájlt a Microsoft Word‑ben:

* Két téglalapot (kék és zöld) lát, amelyek egymás mellett helyezkednek el.
* Bármelyik téglalap kiválasztása az egész csoportot jelöli – a húzás mindkettőt egyszerre mozgatja.
* A csoport vékony piros kerettel rendelkezik, ami megerősíti, hogy a `GroupShape` tulajdonságai alkalmazásra kerültek.

Ha jobb‑kattint a csoportra, és a **Group → Ungroup** lehetőséget választja, a téglalapok visszatérnek önálló alakzatokká, ami azt mutatja, hogy a csoportosítás művelete visszafordítható.

---

## Gyakori variációk és szélhelyzetek

| Helyzet | Hogyan kezelje |
|-----------|------------------|
| **Több mint két alakzat** | Szúrjon be minden alakzatot, majd mindet fűzze hozzá ugyanahhoz a `GroupShape`‑hez. |
| **Különböző alakzattípusok** (pl. ellipszis, kép) | Használja a `builder.insertShape(ShapeType.ELLIPSE, …)`‑t vagy a `builder.insertImage(...)`‑t a hozzáfűzés előtt. |
| **A csoport méretezése** | Hívja a `group.setWidth(newWidth)` vagy `group.setHeight(newHeight)` metódust; a gyermekek arányosan skálázódnak. |
| **A csoport forgatása** | `group.setRotationAngle(45);` elforgatja az egész gyűjteményt a középpontja körül. |
| **Eredeti pozíciók megőrzése** | Tárolja el minden alakzat `left`/`top` értékét a csoportosítás előtt, és szükség esetén állítsa vissza a csoport felbontása után. |

---

## Teljes, futtatható példa

Az alábbiakban a teljes Java‑osztály látható, amelyet egyszerűen másolhat és beilleszthet a fejlesztői környezetébe. Tartalmazza az összes importot, hibakezelést és a magyarázó megjegyzéseket.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Futtassa a programot, nyissa meg a keletkezett `GroupShape.docx` fájlt, és a leírtaknak megfelelően csoportosított téglalapokat fog látni.

---

## Összegzés

Most már tudja, **hogyan csoportosítsunk alakzatokat** az Aspose.Words for Java‑ban, a dokumentum létrehozásától a téglalap alakzatok beszúrásáig, azok pozíciójának finomhangolásáig, és végül a `GroupShape`‑el való csoportosításig. Ez a technika lehetővé teszi, hogy több rajzot egyetlen entitásként kezeljen, egyszerűsítve az elrendezés módosítását és a vizuális konzisztenciát.

**Következő lépések**

* Fedezze fel, hogyan szúrjon be téglalap alakzatokat különböző kitöltési mintákkal vagy szegélyekkel.
* Kombinálja a **insert rectangle shape**‑t szövegdobozokkal címkézett diagramok létrehozásához.
* Kísérletezzen a csoport forgatásával vagy méretezésével összetettebb grafikák előállításához.

Nyugodtan módosítsa a kódot más alakzattípusok, nagyobb csoportok vagy dinamikus dokumentumgenerálási forgatókönyvek esetén. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy további API‑funkciókat saját projektjeiben is könnyedén alkalmazhassa.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [how to insert group shape in Java – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [How to Set Shadow on a Shape in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}