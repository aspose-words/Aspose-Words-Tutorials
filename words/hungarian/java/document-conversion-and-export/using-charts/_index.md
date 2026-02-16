---
date: 2026-02-16
description: Ismerje meg, hogyan adhat hozzá több sorozatot a diagramokhoz az Aspose.Words
  for Java-ban, módosíthatja a tengely jelöléseit, alkalmazhat egyéni számformátumot,
  és generálhat diagramokat tartalmazó Word-dokumentumokat vonal- és oszlopdiagramokkal.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Több sorozat hozzáadása a diagramokhoz az Aspose.Words for Java-ban
url: /hu/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Több sorozat hozzáadása diagramokhoz az Aspose.Words for Java-ban

## Bevezetés a diagramok használatába az Aspose.Words for Java-ban

Ebben az útmutatóban megtanulja, **hogyan adjon hozzá több sorozatot** egy diagramhoz az Aspose.Words for Java segítségével, miért fontos a tengely jelölők testreszabása és egyedi számformátum alkalmazása, valamint hogyan generáljon diagramokkal gazdag Word dokumentumot. Akár pénzügyi adatokhoz vonaldiagramra, akár értékesítési adatokhoz oszlopdiagramra van szüksége, az alábbi lépések végigvezetik a diagramok programozott létrehozásán, formázásán és finomhangolásán.

## Gyors válaszok
- **Hogyan adhatok hozzá több sorozatot?** Használja a `chart.getSeries().add(...)` metódust minden megjeleníteni kívánt sorozathoz.  
- **Módosíthatom a tengely jelölőit?** Igen – használja a `setMajorTickMark()` és `setMinorTickMark()` metódusokat a tengely objektumokon.  
- **Milyen formátumot alkalmazhatok az adatcímkékre?** Bármely Excel‑kompatibilis számformátum, például `"$"#,##0.00` vagy `0.00%`.  
- **Mely diagramtípusok támogatottak?** Vonal, oszlop, terület, buborék, szórt, és még sok más a `ChartType` segítségével.  
- **Szükséges licenc a termeléshez?** Egy érvényes Aspose.Words for Java licenc szükséges a teljes funkcionalitáshoz.

## Mi az a „több sorozat hozzáadása” egy diagramhoz?
A több sorozat hozzáadása azt jelenti, hogy egy diagramterületen több adatkészletet helyezünk el, lehetővé téve különböző kategóriák vagy időszakok egymás melletti összehasonlítását. Minden sorozat saját vonalként, oszlopként vagy jelölőcsoportként jelenik meg, gazdagabb vizuális történetet nyújtva az olvasónak.

## Miért használjuk az Aspose.Words for Java-t diagramokkal ellátott Word dokumentumok generálásához?
- **Teljes irányítás** a diagram típusára, elrendezésére és stílusára anélkül, hogy manuálisan megnyitná a Word-öt.  
- **Programozott generálás** illeszkedik az automatizált jelentéskészítési folyamatokba.  
- **Keresztplatformos** – működik bármely Java‑kompatibilis környezetben.  
- **Gazdag API** a tengelyek, adatcímkék és számformátumok testreszabásához.

## Előfeltételek
- Java Development Kit (JDK) 8 vagy újabb.  
- Aspose.Words for Java könyvtár hozzáadva a projekthez (Maven/Gradle vagy JAR).  
- Érvényes Aspose licenc a termeléshez (értékeléshez opcionális).

## Lépésről‑lépésre útmutató

### 1. lépés: Hozzon létre egy vonaldiagramot és **adj hozzá több sorozatot**
Az alábbi kódrészlet a lényegi részt mutatja, amely létrehozza a vonaldiagramot, törli az alapértelmezett sorozatot, majd három különálló sorozatot ad hozzá egyedi adatcímkékkel.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

> **Pro tip:** Hívja meg a `chart.getSeries().add(...)` metódust annyiszor, ahányszor szükséges a **több sorozat hozzáadásához** – minden hívás egy új vonalat (vagy oszlopot, stb.) hoz létre ugyanazon a diagramon.

### 2. lépés: **Oszlopdiagram létrehozása** (create column chart java)
A következő kódrészlet bemutatja, hogyan illesszen be egy egyszerű oszlopdiagramot, amely hasznos a kategóriák oldalról‑oldalra történő összehasonlításához.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### 3. lépés: **Tengely jelölők módosítása** (change axis tick marks)
Az X‑ és Y‑tengely testreszabása javítja az olvashatóságot. Az alábbi kód bemutatja, hogyan változtassuk meg a jelölőket, fordítsuk meg a sorrendet, és állítsunk be egyedi metszéspontokat.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### 4. lépés: **Egyedi számformátum alkalmazása** (apply custom number format)
A tengely számokat vagy adatcímkéket bármely, az Excel által támogatott mintával formázhatja. Az alábbi rövid példa a Y‑tengelyt ezres elválasztóval formázza.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### 5. lépés: A végleges Word dokumentum generálása (generate chart word document)
A sorozatok, tengelyek és címkék beállítása után egyszerűen hívja meg a `doc.save(...)` metódust, ahogy a fenti kódrészletekben látható. A létrehozott `.docx` fájl teljesen működőképes diagramokat tartalmaz, amelyeket a Microsoft Word-ben megnyithat és szerkeszthet.

## Gyakori felhasználási esetek
- **Pénzügyi műszerfalak** – vonaldiagramok több sorozattal a bevétel, kiadás és profit számára.  
- **Értékesítési jelentések** – oszlopdiagramok a negyedéves eladások régiók szerinti összehasonlításához.  
- **Projektkövetés** – terület- vagy szórt diagramok a haladás időbeli megjelenítéséhez.  

## További diagram testreszabások
Az alapok mellett beállíthatja a határokat, elrejtheti a tengelyeket (`axis.setHidden(true)`), módosíthatja a színeket, hozzáadhat legendákat és még sok mást. Tekintse meg az Aspose.Words for Java API referenciát a teljes opciólistáért.

## Következtetés
Ebben az útmutatóban bemutattuk, hogyan **adjunk hozzá több sorozatot** diagramokhoz, hogyan hozzunk létre vonal- és oszlopdiagramokat, **módosítsuk a tengely jelölőit**, **alkalmazzunk egyedi számformátumot**, és végül **generáljunk diagramokkal gazdag Word dokumentumot**. Az Aspose.Words for Java egy erőteljes, kódelő elsődleges megoldást kínál a professzionális adatvizualizációk közvetlen beágyazásához dokumentumaiba.

## Gyakran Ismételt Kérdések

**K: Hogyan adhatok hozzá több sorozatot egy diagramhoz?**  
V: Hívja meg a `chart.getSeries().add()` metódust minden megjeleníteni kívánt sorozathoz. Minden hívás egy új adatkészletet hoz létre, amely saját vonalként, oszlopként vagy jelölőcsoportként jelenik meg.

**K: Hogyan formázhatom az adatcímkéket egyedi számformátummal?**  
V: Hozzáférhet a sorozat `DataLabels` objektumához, és a `getNumberFormat().setFormatCode("az ön mintája")` metódussal állíthat be formátumot. A formátumot összekapcsolhatja egy forráscellával is a `isLinkedToSource(true)` beállítással.

**K: Hogyan módosíthatom a tengely jelölőit?**  
V: Használja a `setMajorTickMark()` és `setMinorTickMark()` metódusokat a `ChartAxis` objektumokon. Lehetséges opciók: `CROSS`, `INSIDE`, `OUTSIDE`, és `NONE`.

**K: Létrehozhatok más diagramtípusokat, például szórt vagy terület diagramot?**  
V: Igen – a kívánt `ChartType` (például `ChartType.SCATTER`, `ChartType.AREA`) megadásával a `builder.insertChart(...)` hívás során.

**K: Hogyan rejthetek el egy nem szükséges tengelyt?**  
V: Hívja meg az `axis.setHidden(true)` metódust azon a `ChartAxis` objektumon, amelyet el szeretne rejteni.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}