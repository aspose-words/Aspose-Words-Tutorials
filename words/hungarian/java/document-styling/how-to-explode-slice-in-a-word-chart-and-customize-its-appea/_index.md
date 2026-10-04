---
category: general
date: 2026-10-04
description: Tanulja meg, hogyan lehet kibontani egy szeletet egy Word-diagramon,
  kibontani egy kördiagram szeletet, és módosítani a gyűrűdiagram méretét egy lépésről‑lépésre
  bemutatott Java példával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: hu
lastmod: 2026-10-04
og_description: Hogyan lehet szétválasztani egy szeletet egy Word-diagramban, és testre
  szabni a kör- vagy gyűrűdiagramokat Java-val. Kövesse a teljes példát a Word-diagram
  módosításához.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Hogyan szétbontjuk a szeletet egy Word-diagramon – teljes Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Hogyan szétválasszuk a szeletet egy Word-diagramon, és testre szabjuk a megjelenését
url: /hu/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan robbantsuk szét a szeletet egy Word diagramon és testre szabjuk megjelenését

Ha **how to explode slice**-t kell végrehajtania egy Word diagramon, ez az útmutató pontosan megmutatja, hogyan. Akár értékesítési prezentációt, akár pénzügyi jelentést készít, a kördiagram szeletének szétrobbanása vagy a fánk lyukának módosítása kiemelheti a legfontosabb adatokat. Az alábbi szakaszokban megtanulja, hogyan **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, és **customize pie chart word** dokumentumokat használja az Aspose.Words for Java segítségével.

A tutorial befejezésekor egy teljes, azonnal futtatható Java programmal rendelkezik, amely betölti a `.docx` fájlt, szétrobbanja a kördiagram első szeletét, módosítja a fánk lyuk méretét, és elmenti az eredményt. Külső szkriptek vagy manuális szerkesztés nem szükséges.

## Előkövetelmények

- Java 17 vagy újabb telepítve a fejlesztői gépén.  
- Maven 3.6+ (vagy Gradle) a függőségek kezeléséhez.  
- Aspose.Words for Java könyvtár (az ingyenes próba verzió fejlesztéshez használható).  
- Egy Word dokumentum (`input.docx`), amely legalább egy diagramot (kör vagy fánk) tartalmaz.

## 1. lépés: Aspose.Words hozzáadása a projekthez

Ha Maven-t használ, adja hozzá a következő függőséget a `pom.xml`-hez:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Gradle esetén helyezze ezt a `build.gradle` fájlba:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Tartsa naprakészen a könyvtár verzióját; az újabb kiadások további diagramtípusok támogatását és a teljesítmény javítását biztosítják.

## 2. lépés: A diagramot tartalmazó Word dokumentum betöltése

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Why this matters:** A dokumentum betöltése egy memóriában létező reprezentációt hoz létre, amelyet az Aspose.Words bejárhat. Enélkül az objektum nélkül nem férhet hozzá a diagram csomópontjaihoz.

## 3. lépés: Az első diagram lekérése a dokumentumból

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** A `NodeType.SHAPE` minden rajzobjektumot lefed, beleértve a diagramokat is. A `true` argumentum azt mondja az Aspose-nak, hogy rekurzívan keressen, biztosítva, hogy az első diagram megtalálható legyen még akkor is, ha egy táblázatba van ágyazva.

## 4. lépés: A kördiagram első szeletének szétrobbanása

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** A `setExplosion` metódus egy numerikus értéket vesz, amely meghatározza, milyen távolra mozdul el a szelet a középponttól. A `20` érték vizuálisan észrevehető, anélkül, hogy a diagram elrendezését megsértené.

## 5. lépés: A fánk diagram lyukméretének módosítása

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** A nagyobb fánk lyuk javíthatja az olvashatóságot, ha sok adatpont van. A `setDoughnutHoleSize` metódus egy százalékot (0‑100) vár.

## 6. lépés: A módosított dokumentum mentése

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Várható kimenet

- Az első kördiagram első szelete kifelé eltolódik, kiemelve.  
- Ha a diagram fánk, a központi lyuk a diagram sugárának 40 %-ára nő.  
- Az eredményül kapott `PieChart.docx` fájl megnyitható a Microsoft Wordben, LibreOffice-ban vagy bármely kompatibilis megjelenítőben, bemutatva a programozott vizuális módosításokat.

## Teljes, futtatható példa

Az alábbiakban a teljes program egy blokkban látható. Másolja be a `ChartExploder.java` fájlba, állítsa be a fájlutakat, és futtassa a `mvn compile exec:java` paranccsal (vagy az IDE futtatási beállításaival).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

A kód futtatása automatikusan **modify chart in Word**, **explode pie chart slice**, és **change doughnut chart size** műveleteket hajt végre.

## Gyakori kérdések és szélhelyzetek

| Question | Answer |
|----------|--------|
| *Mi van, ha a dokumentum több diagramot tartalmaz?* | A példa a **első** diagramra (`NodeType.SHAPE, 0`) céloz. Más diagramokkal való munka érdekében módosítsa az indexet, vagy iteráljon a `doc.getChildNodes(NodeType.SHAPE, true)` elemein, és szűrje a `shape.getChart() != null` feltétellel. |
| *Robbantathatok egy szeletet, amely nem az első?* | Igen. A kívánt sorozathoz a `chart.getSeries().get(seriesIndex)` segítségével férhet hozzá, és meghívhatja a `setExplosion(value)` metódust. Az indexek nullától kezdődnek. |
| *Működik ez a Word 2007‑2021 fájlokkal?* | Az Aspose.Words támogatja a `.doc`, `.docx`, `.dot` és `.dotx` formátumokat. Ugyanaz a kód minden verzión működik, mivel a könyvtár elrejti a fájlformátum részleteit. |
| *Mi van, ha a diagram oszlop- vagy vonaldiagram?* | A `setExplosion` és a `setDoughnutHoleSize` csak kördiagramokra alkalmazható. A kód biztonságosan kihagyja ezeket a műveleteket, ha a diagram típusa eltér. |
| *Szükségem van licencre az Aspose.Words-hez?* | Az ingyenes értékelő licenc eltávolítja a 30‑napos korlátot, de vízjelet helyez el. Gyártási környezetben licenc vásárlásával távolítható el a vízjel, és aktiválható a teljes funkcionalitás. |

## Következtetés

Most már tudja, hogyan **how to explode slice** egy Word diagramon, hogyan **modify chart in Word**, és hogyan **change doughnut chart size** az Aspose.Words for Java segítségével. A teljes példa bemutatja a teljes munkafolyamatot – a dokumentum betöltésétől, a diagram megtalálásáig, a vizuális módosítások alkalmazásáig, a mentésig – így ezeket a lépéseket bármely jelentés- vagy dokumentum‑generálási csővezetékbe beépítheti.

**Következő lépések**

- Fedezze fel a további diagram testreszabásokat, például a színek módosítását, adatcímkék hozzáadását vagy a diagramtípusok váltását (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Kombinálja ezt a logikát az Aspose.PDF‑vel, hogy PDF verziót generáljon ugyanabból a jelentésből.  
- Automatizálja a folyamatot több dokumentumra, a könyvtárban lévő fájlok ciklikus feldolgozásával.

Nyugodtan kísérletezzen különböző robbantási értékekkel vagy fánk lyuk százalékokkal, hogy megfeleljenek a tervezési irányelveinek. Boldog kódolást!

## Mit érdemes még megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Diagram tengely elrejtése Word dokumentumban](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Buborékdiagram beszúrása Word dokumentumba](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}