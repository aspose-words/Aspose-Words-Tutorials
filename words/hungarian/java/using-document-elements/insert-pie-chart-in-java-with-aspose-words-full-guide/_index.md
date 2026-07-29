---
category: general
date: 2026-07-29
description: Helyezzen be kördiagramot az Aspose.Words for Java segítségével, és tanulja
  meg, hogyan generáljon gyűrűdiagramot, formázza a kördiagramot, formázza a diagramot
  Wordben, és testreszabja a diagram méretét.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: hu
lastmod: 2026-07-29
og_description: Illessze be a kördiagramot az Aspose.Words for Java segítségével,
  és gyorsan tanulja meg a gyűrűdiagram létrehozását, a kördiagram formázását, a diagram
  Wordben való formázását, valamint a diagram méretének testreszabását professzionális
  dokumentumokhoz.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Kördiagram beszúrása Java-ban – Teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Kördiagram beszúrása Java-ban az Aspose.Words segítségével – Teljes útmutató
url: /hu/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kördiagram beszúrása Java-ban az Aspose.Words segítségével – Teljes útmutató

Valaha is elgondolkodtál, hogyan **insert pie chart**‑t lehet beilleszteni egy Word‑dokumentumba Java‑kódból? Nem vagy egyedül – sok fejlesztő ütközik ebbe a problémába, amikor gyors, programozott módra van szükségük az adatok megjelenítéséhez. A jó hír? Az Aspose.Words for Java segítségével mindezt néhány sorban megteheted, és közben **generate doughnut chart**, **format pie chart**, **format chart Word**, és **customize chart size** funkciókat is használhatsz a márkádhoz igazodó megjelenéshez.

Ebben a tutorialban egy valós példán keresztül vezetünk végig, amely egy üres dokumentum létrehozásával kezdődik, beilleszt egy kördiagramot, finomít néhány vizuális tulajdonságot, majd elmenti a fájlt. A végére egy újrahasználható kódrészletet kapsz, amelyet bármely Java‑projektbe beilleszthetsz, ha diagram‑automatizálásra van szükség. Nincs szükség extra könyvtárakra, nincs kézi Office‑interop – csak tiszta, lefordított Java.

## Amire szükséged lesz

- **Java 17** (vagy bármely friss JDK; az API visszafelé kompatibilis)
- **Aspose.Words for Java** 22.12 vagy újabb – a Maven‑artifactet vagy a .jar‑t letöltheted az Aspose weboldaláról.
- Egy egyszerű IDE (IntelliJ IDEA, Eclipse, VS Code…) – bármi, ami lehetővé teszi a `main` metódus futtatását.
- Opcionális: licencfájl, ha nem szeretnéd a kiértékelő vízjelet.

Ha ezek megvannak, ugorjunk egyenesen a kódba.

## 1. lépés: Kördiagram beszúrása az Aspose.Words segítségével

Az első dolog, amit teszünk, **insert pie chart** egy friss dokumentumba. Ez a lépés alapozza meg a többit, mivel a diagramobjektum hozzáférést biztosít a sorozatokhoz, adatpontokhoz és a vizuális finomhangoláshoz.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart` nem csak létrehozza a diagramot, hanem egy `Chart` objektumot is visszaad, amelyet manipulálhatunk. A szélesség‑ és magasság‑argumentumok lehetővé teszik a **customize chart size** beállítását már a létrehozáskor, így később nem kell átméretezni.

## 2. lépés: Donut diagram (opcionális) generálása

Ha a tervezésed középen egy lyukat igényel – gondolj egy klasszikus donut diagramra – az Aspose ezt egyetlen sorban megoldja. Ugyanaz a `Chart` példány átkapcsolható egy normál kördiagramról donut diagramra a lyukméret módosításával.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** A lyukméret csak `ChartType.DONUT` esetén lép életbe. Ha a típust `PIE`‑re hagyod, a hívás figyelmen kívül marad, szóval nyugodtan kísérletezhetsz.

## 3. lépés: Kördiagram szeletek formázása

Egy jó vizuális gyakran kiemel egy adott szeletet. Itt **format pie chart**‑t alkalmazunk úgy, hogy az első szeletet 20 ponttal kifújjuk kifelé. Ez a szemlélet a legfontosabb adatpontra irányítja a figyelmet.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** Ha több sorozatod van, végigiterálhatsz a `pieChart.getSeries()`‑en, és egyedi színeket, szegélyeket vagy adatcímkéket állíthatsz be. Így tudod **format chart Word** dokumentumokat gazdag stílusokkal ellátni.

## 4. lépés: Adatok hozzáadása a diagramhoz

Egy diagram adat nélkül csak egy díszítő alakzat. Töltsük fel egy egyszerű adathalmazzal – például negyedéves értékesítési számokkal.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** A `ChartPoint` objektumok explicit hozzáadásával biztosítjuk, hogy a diagram tükrözze az üzleti logikánkat. A `setShowCategoryName` és `setShowValue` hívások a **formatting the pie chart** részei, amelyek mind a címkéket, mind a számokat megjelenítik.

## 5. lépés: Megjelenés finomhangolása (diagram méretének és stílusának testreszabása)

A kezdeti méretek mellett érdemes lehet a diagram legendáját, címét vagy akár az adatcímkék betűtípusát is módosítani. Ezek mind a **customize chart size** és az általános formázás részei.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** Ha később PDF‑be exportálod a dokumentumot, a diagram vektoradata éles marad, mivel a méret pontban, nem pixelben van definiálva. Ez előny a **format chart Word** és a további formátumok számára.

## 6. lépés: Dokumentum mentése és megtekintése

Az utolsó lépés olyan egyszerű, mint a `doc.save` meghívása. Ez egy `.docx` fájlt ír, amelyet megnyithatsz a Microsoft Word‑ben, LibreOffice‑ban vagy bármely, az OpenXML‑formátumot támogató megjelenítőben.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** Nyisd meg a `PieChart.docx`‑t, és egy szépen méretezett kör (vagy donut) diagramot látsz, egy kifújt szelettel, címmel és legendával – mindezt anélkül, hogy a felhasználói felületet érintettük volna.

### Várható kimenet

| Elem | Mit fogsz látni |
|---------|-----------------|
| Diagram típusa | Kördiagram (vagy donut, ha a `holeSize` > 0) |
| Szelet kitüntetése | Az első szelet 20 pt távolságra kitüntetve |
| Jelmagyarázat | Jobb oldalon elhelyezve |
| Cím | “Quarterly Sales Distribution” félkövér 14 pt méretben |
| Adatcímkék | Kategória neve és értéke minden szeleten |
| Dokumentum | Standard Word `.docx` fájl, készen a megosztásra |

## Gyakori kérdések és buktatók

- **Szükségem van licencre?**  
  A kiértékelő verzió teszteléshez megfelelő, de vízjelet ad hozzá. Helyezd a `aspose.words.lic` fájlt a classpath‑ba a tiszta kimenethez.

- **Használhatom Maven‑nel?**  
  Természetesen. Add hozzá a következő függőséget a `pom.xml`‑hez:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Mi van, ha több sorozatom is van?**  
  Iterálj a `pieChart.getSeries()`‑en, és alkalmazd a `setExplosion`, `setFillColor` vagy egyéb formázásokat sorozatonként. Így tudod **format pie chart**‑ot többdimenziós adatokhoz.

- **A diagram szerkeszthető Word‑ben a generálás után?**  
  Igen – a mentés után megnyithatod a dokumentumot, és manuálisan módosíthatod a színeket, betűtípusokat, vagy akár átalakíthatod a kördiagramot oszlopdiagrammá, ha szükséges.

## Összegzés

Most már **insert pie chart**‑t tudsz beilleszteni egy Word‑dokumentumba az Aspose.Words for Java segítségével, megmutattuk, hogyan **generate doughnut chart**, bemutattuk a különféle **format pie chart** módszereket, áttekintettük a **format chart Word** legjobb gyakorlatait, és megtanultuk, hogyan **customize chart size** a professzionális megjelenésért. A fenti, futtatható példa bármely Java‑projektbe beilleszthető, így azonnali diagram‑automatizálást kapsz COM‑interop vagy Office‑telepítések nélkül.

Mi a következő? Próbáld meg a forrásadatokat élő adatbázisra cserélni, adj hozzá feltételes színeket küszöbértékek alapján, vagy exportáld ugyanazt a dokumentumot PDF‑be egy nyomtatásra kész jelentéshez. Mindezek a lépések az általunk felépített alapra épülnek, így a váltás zökkenőmentes lesz.

Ha bármilyen problémába ütközöl, vagy ötleteid vannak további fejlesztésekhez – például egy halmozott oszlop vagy vonaldiagram – írj egy megjegyzést alább. Boldog diagramkészítést!

## Mit érdemes még megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy további API‑funkciókat saját projektjeidben is elsajátíthasd és alternatív megvalósítási módokat felfedezhess.

- [Hogyan készítsünk oszlopdiagramot az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Adatcímke számának formázása diagramon](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Számformátum a tengelyen diagramon](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}