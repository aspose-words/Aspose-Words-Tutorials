---
category: general
date: 2026-09-11
description: Hogyan szerkesszünk diagramot egy Word-dokumentumban Java-val – tanulja
  meg a diagram beállításainak frissítését, a rácsvonalak engedélyezését, a diagram
  opcióinak módosítását, és a frissített dokumentum mentését.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: hu
lastmod: 2026-09-11
og_description: Hogyan szerkeszthetünk diagramot egy Word-dokumentumban Java-val.
  Kövesse ezt az útmutatót a diagram beállításainak frissítéséhez, a diagram rácsvonalainak
  engedélyezéséhez, a diagram opcióinak módosításához és a frissített dokumentum mentéséhez.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Hogyan szerkessz diagramot egy Word-dokumentumban Java segítségével – teljes
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Hogyan szerkeszthető diagram egy Word-dokumentumban Java-val
url: /hu/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szerkesszünk diagramot egy Word dokumentumban Java segítségével

Ha **hogyan szerkesszünk diagramot** egy Word fájlban, ez az útmutató pontos lépéseket mutat. Megtanulod, hogyan frissítsd a diagram beállításait, engedélyezd a diagram rácsvonalait, módosítsd a diagram opcióit, és végül **mentsd el a frissített dokumentumot** anélkül, hogy elveszítenéd a formázást.

A diagramok programozott kezelése gyakran fekete dobozként érződik, különösen, ha a vizuális részleteket, például a graduációkat vagy a rácsvonalakat szeretnéd finomhangolni. Ez a tutorial mindent lefed, amit tudnod kell, a dokumentum betöltésétől a módosítások mentéséig. Nincs szükség külső eszközökre – csak az Aspose.Words for Java könyvtárra (24.9 vagy újabb verzió).

A cikk végére képes leszel:

* Betölteni egy `.docx` fájlt, amely diagramot tartalmaz.
* Megtalálni a diagram alakzatát és módosítani a tulajdonságait.
* Engedélyezni a diagram rácsvonalait (graduációkat) és beállítani egyéb opciókat.
* **Menteni a frissített dokumentumot** egy új fájlba.

## Előfeltételek

* Java 17 vagy újabb telepítve a gépeden.  
* Maven vagy Gradle a függőségek kezeléséhez.  
* Aspose.Words for Java 24.9+ (az a verzió, amely bevezette a `setShowGraduations` metódust).  
* Egy Word dokumentum (`input.docx`), amely már tartalmaz legalább egy diagramot.

Ha nem ismered az Aspose.Words-ot, gondolj rá úgy, mint egy teljes körű API-ra, amely lehetővé teszi a Word dokumentumok programozott olvasását, módosítását és írását – hasonlóan ahhoz, ahogy egy DOM-ot manipulálnál egy web böngészőben.

## 1. lépés: A projekt beállítása és a könyvtár importálása

Hozz létre egy új Maven projektet, vagy add hozzá a függőséget egy meglévőhöz:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro tipp:** Használd a legújabb stabil kiadást, hogy rendelkezésedre álljon a `setShowGraduations` metódus. Régebbi verziók nem fognak lefordulni.

## 2. lépés: A diagramot tartalmazó Word dokumentum betöltése

Az első művelet minden **hogyan szerkesszünk diagramot** munkafolyamatban a forrásfájl betöltése. Az Aspose.Words a teljes dokumentumot a `Document` osztállyal reprezentálja.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

A `Document` objektum hozzáférést biztosít a fájl minden csomópontjához, beleértve az alakzatokat, táblázatokat és bekezdéseket.  

## 3. lépés: Az első diagram alakzatának megtalálása a dokumentumban

A diagramok `Shape` csomópontként tárolódnak, amelynek renderere egy `Chart`. Egy diagram szerkesztéséhez először le kell kérned ezt a csomópontot.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Ha a dokumentum több diagramot tartalmaz, iterálj a `shapes` gyűjteményen, és ellenőrizd, hogy `chartShape.getChart() != null` mielőtt átkonvertálnád. Ez megakadályozza a `ClassCastException`-t, és biztosítja, hogy csak érvényes diagram objektumokon **módosítsd a diagram opcióit**.

## 4. lépés: Diagram rácsvonalainak (graduációk) engedélyezése – új tulajdonság a 24.9-es verzióban

A `setShowGraduations` tulajdonság a kisebb rácsvonalak láthatóságát állítja be az értéktengelyen. Engedélyezésük gyakran javítja az olvashatóságot sűrű adathalmazok esetén.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Miért fontos:** A rácsvonalak vizuális referenciát nyújtanak minden adatponthoz, így a trendek könnyebben felismerhetők. Alapértelmezés szerint `false`, ezért explicit módon kell engedélyezned, ha szükséges.

Testreszabhatod továbbá a fő rácsvonalakat, tengelycímeket vagy a jelmagyarázat elhelyezését is. Az alábbi példa a diagram címének és a jelmagyarázat pozíciójának módosítását mutatja – mindkettő a **diagram opciók módosítása** része.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## 5. lépés: A dokumentum mentése a frissített diagram beállításokkal

A diagram módosítása után menteni kell a változtatásokat. Ez a lépés fejezi be a **frissített dokumentum mentése** fázist.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

A program futtatása `output.docx` fájlt hoz létre, ahol a diagram most már rácsvonalakat, új címet és áthelyezett jelmagyarázatot mutat. Nyisd meg a fájlt a Microsoft Wordben, hogy ellenőrizd a vizuális változásokat.

## Teljes forráskód (futtatható)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Várt eredmény

Amikor megnyitod a `output.docx`-et:

* A diagram kisebb rácsvonalakat jelenít meg az értéktengelyen.  
* A cím **„Sales Overview 2026”** lesz.  
* A jelmagyarázat a diagram alján jelenik meg.

Ha az eredeti diagram már tartalmazott rácsvonalakat, a megjelenés változatlan marad, ami azt mutatja, hogy a kód **idempotens**.

## Gyakori kérdések és szélsőséges esetek kezelése

### Mi a teendő, ha a dokumentumnak nincs diagramja?

Egy nem‑diagram alakzat átkonvertálása `ClassCastException`-t eredményez. Védd le ezt a helyzetet úgy, hogy ellenőrzöd az alakzat típusát:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Hogyan szerkesszünk egy konkrét diagramot az első helyett?

Iterálj a `shapes` gyűjteményen, és egyeztesd egy ismert címmel vagy alternatív azonosítóval:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Később le szeretném tiltani a rácsvonalakat, lehetséges?

Igen, egyszerűen állítsd a tulajdonságot `false`-ra:

```java
chart.setShowGraduations(false);
```

### Működik ez `.doc` (bináris) fájlokkal is?

Az Aspose.Words elrejti a fájlformátum részleteit, így ugyanaz a kód működik `.doc` és `.docx` esetén is. Azonban egyes újabb diagram funkciók (például a graduációk) csak az OOXML formátumban tárolódnak, ezért a hatás csak `.docx` mentéskor lesz látható.

## Tippek a termelés‑kész kódhoz

* **Érvényesítsd a bemeneti útvonalakat** – használj `Files.exists(Paths.get(inputPath))` ellenőrzést a betöltés előtt.  
* **Tekerj API hívásokat** try‑catch blokkokba, hogy a `Exception` részletei láthatóak legyenek, különösen sérült dokumentumok esetén.  
* **Szabadítsd fel az erőforrásokat** – bár az Aspose.Words kezeli a memóriát, a `doc.close()` (vagy a try‑with‑resources használata, ha elérhető) korábban felszabadíthatja a natív handle‑eket.  
* **Verzióellenőrzés** – győződj meg róla, hogy a futási könyvtár verziója ≥ 24.9, mielőtt meghívod a `setShowGraduations` metódust. Programból a `License.getVersion()` segítségével kérdezheted le a verziót.

## Összegzés

Most már tudod, **hogyan szerkesszünk diagram** objektumokat egy Word dokumentumban Java segítségével. A folyamat – dokumentum betöltése, diagram megtalálása, rácsvonalak engedélyezése, diagram opciók módosítása, és **a frissített dokumentum mentése** – lefedi a leggyakoribb programozott diagramkezelési szituációkat.  

Innen tovább felfedezheted a további testreszabásokat, például az adat sorok színeinek módosítását, diagramstílusok alkalmazását vagy a diagram képként való exportálását. Mindegyik feladat ugyanazt a mintát követi: lekérdezed a `Chart` példányt, beállítod a tulajdonságait, és **mented a frissített dokumentumot**.

Boldog kódolást, és nyugodtan kísérletezz más diagrambeállításokkal, hogy a jelentéseid a lehető legjobban megfeleljenek az igényeidnek!

## Mit érdemes még megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy könnyedén elsajátíthasd az API további funkcióit és alternatív megvalósítási megközelítéseket saját projektjeidben.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}