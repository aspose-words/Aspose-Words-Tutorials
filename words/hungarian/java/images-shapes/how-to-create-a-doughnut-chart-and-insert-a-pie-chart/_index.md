---
category: general
date: 2026-10-26
description: Készíts fánkdiagramot, és illessz be kördiagramot Java‑ban lépésről‑lépésre
  kóddal. Ismerd meg a teljes munkafolyamatot a rugalmas diagrammegjelenítésekhez.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: hu
lastmod: 2026-10-26
og_description: Készíts fánkdiagramot Java-ban ezzel az útmutatóval, amely megmutatja,
  hogyan lehet beilleszteni kördiagramot a rugalmas vizualizációkhoz.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Készítsen gyűrűdiagramot és szúrjon be kördiagramot – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Hogyan készítsünk gyűrűdiagramot és illesszünk be kördiagramot
url: /hu/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre fánkdiagramot és szúrjunk be kördiagramot

Ha Java-ban **create doughnut chart**-et kell létrehoznod, ez a tutorial pontos lépéseken keresztül vezet. Megmutatjuk, hogyan **insert pie chart**-et használva ugyanazt a builder API-t, így könnyedén válthatsz a vizuális stílusok között. A útmutató végére egy teljes, futtatható programod lesz, amely mindkét diagramtípust előállítja, és bemutatja a gyakori testreszabásokat.

A tutorial a következőket fedi le:

* A kiválasztott könyvtár által biztosított chart builder inicializálása.  
* Fánkdiagram létrehozása és a lyuk méretének beállítása.  
* Kördiagram beszúrása és egy szelet kiemelése (exploding) a hangsúlyozáshoz.  
* Tippek a szélhelyzetek kezelésére, például hiányzó sorozatok vagy nem támogatott diagramtípusok esetén.

Csak egy friss JDK-re (8 vagy újabb) és a chart library JAR-re van szükséged a classpath-odban. Külső szolgáltatások nem szükségesek.

---

## Előfeltételek

| Elem | Indok |
|------|-------|
| Java Development Kit (JDK) 8+ | Szükséges a példa lefordításához és futtatásához. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Biztosítja a `ChartBuilder`, `ChartType` és a sorozatkezelő metódusokat, amelyeket a kódban használunk. |
| IDE vagy szövegszerkesztő | A Java forrásfájl írásához és futtatásához. |

Győződj meg róla, hogy a könyvtár JAR hozzá van adva a projekted build útvonalához. Ha Maven-t használsz, add hozzá a megfelelő függőséget; egyébként helyezd a JAR-t a `libs` mappába, és hivatkozz rá a fordítás során.

## 1. lépés: A chart builder beállítása

Az első lépés egy `ChartBuilder` (vagy ekvivalens) példány létrehozása, amely a diagramobjektumokat generálja. Ez az objektum gyárként működik, és tartalmazza azt a munkalapot vagy vásznat, ahol a diagram elhelyezésre kerül.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Miért fontos ez:**  
A builder a diagramot egy adott munkalaphoz köti, biztosítva, hogy az összes későbbi diagramobjektum ugyanazt a rajzfelületet használja. Ennek a lépésnek a kihagyása azt eredményezné, hogy nincs célhely a vizuális elemek számára.

---

## 2. lépés: **Create doughnut chart**

Most egy meghatározott méretű fánkdiagramot generálunk. A lyuk mérete határozza meg, hogy a diagram középpontjának mekkora része üres, így egy hagyományos kördiagram fánkdiagrammá alakul.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Magyarázat:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` létrehozza a diagramobjektumot és helyet foglal a munkalapon.  
* `setHoleSize(30)` egy 30 %-os üres középpontú fánkdiagrammá alakítja a kördiagramot.  
* `add("{10, 20, 30, 40}", true)` négy adatpontot ad meg; a `true` jelző azt mondja a könyvtárnak, hogy az értékeket egyetlen sorozatként kezelje.

**Szélhelyzet:** Ha a kiválasztott diagramtípus nem támogat lyukat (például oszlopdiagram), a `getDoughnutChart()` hívás kivételt dob. Mindig ellenőrizd a diagramtípust a lyukméret módosítása előtt.

---

## 3. lépés: **Insert pie chart**

Miután a fánkdiagram készen áll, bemutatjuk, hogyan **insert pie chart**-et használva ugyanazt a builder-t. Ez a lépés kiemeli a két diagramtípus közötti hasonlóságot, és megmutatja, hogyan lehet egy szeletet hangsúlyozni.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Magyarázat:**  

* `ChartType.PIE` azt mondja a buildernek, hogy klasszikus kördiagramot hozzon létre.  
* `setExplode(10)` az első szeletet a sugár 10 %-ával tolja el, ami gyakori technika egy kulcsfontosságú adatpont kiemelésére.  

**Tipp:** A `setExplode` metódus csak a kördiagram első sorozatán működik. Ha több sorozatod van, a megfelelő indexet kell megcéloznod.

---

## 4. lépés: A munkafüzet mentése

Végül írd a munkafüzetet egy fájlba, hogy megtekintsd a diagramokat Excelben vagy bármely kompatibilis megjelenítőben.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Miért mentsd most:** A munkafüzet mentése befejezi az összes rajzolási műveletet. A fájl mentés előtti megtekintés üres vagy hiányos dokumentumot eredményez.

**Eredmény:** A *DoughnutAndPieChart.xlsx* megnyitása bal oldalon egy 30 %-os lyukú fánkdiagramot, jobb oldalon pedig egy kiemelt első szelettel rendelkező kördiagramot mutat.

---

## 5. lépés: Gyakori variációk és hibaelhárítás

| Helyzet | Módosítás |
|-----------|------------|
| **Different chart dimensions** | `insertChart`-ben módosítsd a szélesség és magasság argumentumokat. |
| **Multiple data series** | Hívd meg többször az `add`-ot, vagy adj át egy 2‑D tömb karakterláncot. |
| **Dynamic hole size** | Számítsd ki a lyuk méretét az adatintervallum alapján, majd hívd meg a `setHoleSize`-t. |
| **Explode multiple slices** | Iterálj a `chart.getSeries().get(i).setExplode(percent)`-on minden olyan szeletnél, amelyet el szeretnél tolni. |
| **Library not supporting doughnut** | Használj kördiagramot, és manuálisan rajzolj fehér kör átfedést, bár ez kevésbé pontos. |

**Pro tipp:** Nagy munkafüzetek esetén a diagramok beszúrása után mindig hívd meg a `builder.flush()`-t (ha elérhető). Ez felszabadítja a belső puffereket és megakadályozza a memória szivárgásokat.

![Java kód, amely fánkdiagramot hoz létre és kördiagramot szúr be](https://example.com/images/doughnut-pie-java.png "fánkdiagram példa létrehozása Java-ban")

*A kép a végső munkafüzet elrendezését mutatja, ahol mindkét diagram egymás mellett helyezkedik el.*

---

## Következtetés

Most már tudod, hogyan **create doughnut chart**-et és **insert pie chart**-et készíts Java-ban egy fluent builder API segítségével. A teljes példa lefedi az inicializálást, a méretbeállítást, a lyukméretet, a szelet kiemelést és a fájl kimenetet. Innen további testreszabásokat fedezhetsz fel, például színeket, jelmagyarázatokat és adatcímkéket, hogy megfeleljenek a jelentési igényeidnek.

**Következő lépések**

* Kísérletezz a **chart customization Java** funkciókkal, például színátmenetes kitöltésekkel és adatcímkékkel.  
* Integráld a diagramgenerálást egy webszolgáltatásba, amely igény szerint visszaadja a munkafüzetet.  
* Hasonlítsd össze a builder megközelítést más könyvtárakkal (például JFreeChart), hogy a projektedhez leginkább illeszkedőt válaszd.

Boldog diagramkészítést!

## Mit érdemes legközelebb megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről-lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre fánkdiagramot egy Word dokumentumban Java-val](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Word dokumentum mentése a fánkdiagram Java-ban történő szerkesztése után](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Kördiagram beszúrása Java-ban – Kiugrás, Forgatás és Szeletek kiemelése](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}