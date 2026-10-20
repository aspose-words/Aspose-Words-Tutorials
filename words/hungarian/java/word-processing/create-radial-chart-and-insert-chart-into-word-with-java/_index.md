---
category: general
date: 2026-09-27
description: Készíts radiális diagramot Java-ban, és illeszd be a diagramot a Word
  dokumentumba. Tanuld meg, hogyan állítsd be a diagram méretét, adj hozzá adat sorozatot,
  és generálj egy üres Word dokumentumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: hu
lastmod: 2026-09-27
og_description: Készíts radiális diagramot Java-ban, majd illeszd be a diagramot Word-be.
  Ez az útmutató bemutatja, hogyan állítsd be a diagram méretét, adj hozzá adat sorozatot,
  és hozz létre egy üres Word dokumentumot.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Sugárdiagram létrehozása és beillesztése Word-be Java-val
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Sugárdiagram készítése és beillesztése Word-be Java-val
url: /hu/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Radiális diagram létrehozása és diagram beszúrása Word-be Java-val

Ha Java-val kell **radiális diagramot** létrehozni egy Word fájlban, ez a bemutató pontosan megmutatja, hogyan. Megtanulod, hogyan **szúrj be diagramot Word-be**, állítsd be a diagram méreteit, és építs **üres Word dokumentumot** a semmiből.

Lépésről‑lépésre végigvezetünk minden szükséges lépésen, a dokumentum inicializálásától az adat sor hozzáadásáig és a végleges `.docx` mentéséig. A végére egy teljesen működő Word fájlod lesz, amely tartalmaz egy radiális diagramot, és megérted, **hogyan állítsd be a diagram méretét** és **hogyan adj hozzá adat sorokat a diagramhoz** a későbbi testreszabásokhoz.

## Előfeltételek

* Java 17 vagy újabb (a kód bármely modern JDK-val lefordítható)
* Aspose.Words for Java 24.9 vagy újabb – a `setShowGraduations` metódus csak ettől a verziótól érhető el
* IDE vagy build eszköz (Maven/Gradle), amely képes beilleszteni az Aspose.Words JAR‑t
* Alapvető ismeretek a Java szintaxisról és a Maven/Gradle függőségkezelésről

> **Pro tipp:** Ha Maven‑t használsz, add hozzá a következőt a `pom.xml`‑hez:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## 1. lépés: Üres Word dokumentum létrehozása

Egy üres dokumentum a vászon, amelyre a diagram kerül. A `Document` osztály képviseli a teljes `.docx` fájlt.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Üres dokumentum létrehozásával biztosítod, hogy semmilyen előre létező tartalom ne zavarja a diagram elrendezését.

## 2. lépés: DocumentBuilder inicializálása

A `DocumentBuilder` kényelmes módszereket biztosít objektumok, szöveg és egyéb elemek beszúrására a dokumentumba.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A builder később a **diagram Word-be való beszúrásához** lesz használva.

## 3. lépés: Radiális diagram felépítése

Az Aspose.Words számos diagramtípust támogat; a `ChartType.RADIAL` egy radiális (polár) diagramot hoz létre.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Ezen a ponton a diagram létezik, de még nincs adat, méret vagy vizuális beállítás.

## 4. lépés: Adatsor hozzáadása a diagramhoz

Egy diagram adat sor nélkül üres. Az `add` metódus egy sornevet és egy értéktömböt vár.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Több sor hozzáadható az `add` többszöri meghívásával. Ez teljesíti a **add data series chart** követelményt.

## 5. lépés: Rácsvonalak engedélyezése (opcionális)

A rácsvonalak (graduations) a radiális hálóvonalak, amelyek javítják az olvashatóságot. Csak a 24.9‑es verziótól érhetők el.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Ha régebbi Aspose.Words verziót használsz, ez a sor kivételt dob – ezért először ellenőrizd a könyvtár verzióját.

## 6. lépés: A diagram méretének beállítása

A diagram méretének szabályozásával könnyen elhelyezhető a lap margóin belül. Ez a **how to set chart size** kérdésre ad választ.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

A szélesség és magasság értékeket a saját elrendezésedhez igazíthatod. Ne feledd, hogy 1 pont ≈ 1/72 hüvelyk.

## 7. lépés: Diagram beszúrása a Word dokumentumba

Most a diagram készen áll a helyére. A `DocumentBuilder` `insertChart` metódusa végzi a beszúrást.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Ez a **insert chart into word** művelet központi része.

## 8. lépés: Dokumentum mentése

Végül írd a dokumentumot a lemezre. A fájl tartalmazni fogja a most létrehozott radiális diagramot.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

A program futtatása `RadialChart.docx`‑t hoz létre a projekt munkakönyvtárában. A fájl Microsoft Word‑ben megnyitva egy radiális diagramot látsz három adatponttal és látható rácsvonalakkal.

### Várt kimenet

* Egy `RadialChart.docx` nevű Word fájl
* A fájlban egyetlen oldal, amelyen egy 400 × 300 pont méretű radiális diagram található
* A diagram egy **Series 1** nevű sorozatot jelenít meg a **10, 20, 30** értékekkel
* A rácsvonalak (radiális hálóvonalak) láthatóak a diagram körül

## Gyakori variációk és szélhelyzetek

| Helyzet | Mit kell módosítani | Ok |
|-----------|----------------|--------|
| **Több sorozat** | Hívjuk meg a `chart.getSeries().add(...)`‑t minden sorozathoz | Lehetővé teszi az összehasonlító adatvizualizációt |
| **Másik diagramtípus** | Cseréljük le a `ChartType.RADIAL`‑t `ChartType.COLUMN`‑ra (vagy bármely másra) | A legmegfelelőbb diagramtípus használata az adataidhoz |
| **Egyedi színek** | Hozzáférés: `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Javítja a vizuális márkázást |
| **Régebbi Aspose.Words verzió** | Hagyjuk el a `setShowGraduations` sort vagy frissítsük a könyvtárat | Megakadályozza a `NoSuchMethodError` hibát |
| **Mentés más formátumba** | Használjuk a `doc.save("RadialChart.pdf", SaveFormat.PDF)`‑t | PDF‑et generál a DOCX helyett |

## Teljes, futtatható példa

Az alábbiakban a teljes, önálló Java program látható. Másold be egy `RadialChartExample.java` nevű fájlba, add hozzá az Aspose.Words függőséget, és futtasd.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Összegzés

Most már tudod, hogyan **hozz létre radiális diagramot** programozottan, hogyan **adj hozzá adat sorozatot a diagramhoz**, hogyan **állítsd be a diagram méretét**, és hogyan **szúrd be a diagramot Word-be**, miközben egy **üres Word dokumentumból** indulsz. A példa az Aspose.Words for Java 24.9‑et használja, de ugyanazok a koncepciók más diagramkönyvtárakra is alkalmazhatók, amelyek hasonló API‑t biztosítanak.

### Következő lépések

* Fedezz fel más diagramtípusokat (`ChartType.PIE`, `ChartType.LINE`, stb.) – ez visszavezet a másodlagos kulcsszó **insert chart into word**‑re.
* Testreszabhatod a tengelycímkéket, jelmagyarázatot és színeket a márka irányelveinek megfelelően.
* Generálj diagramokat dinamikusan adatbázis‑lekérdezések vagy CSV fájlok alapján.
* Konvertáld a létrehozott `.docx`‑t PDF‑re a terjesztéshez (`doc.save("output.pdf", SaveFormat.PDF)`).

Nyugodtan kísérletezz a méretekkel, sorozatadatokkal és stílusbeállításokkal, hogy pontosan azt a vizuális megjelenést hozd létre, amire szükséged van. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket és lépésről‑lépésre magyarázatot tartalmaz, hogy könnyedén elsajátíthasd az API további funkcióit és alternatív megvalósítási módokat a saját projektjeidben.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}