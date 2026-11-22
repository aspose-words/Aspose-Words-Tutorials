---
category: general
date: 2026-11-22
description: Vytvořte koláčový graf v Javě a naučte se, jak nastavit velikost grafu,
  přidat popisky dat, zobrazit procenta a otočit první výseč pro jasný vizuální dopad.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: cs
lastmod: 2026-11-22
og_description: Vytvořte koláčový graf v Javě, nastavte velikost grafu, zobrazte procenta
  na popiscích dat a otočte první výsek – vše v jednom spustitelném příkladu.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Vytvořte koláčový graf s vlastní velikostí, popisky a rotací v Javě
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Vytvořte koláčový graf s vlastní velikostí, popisky dat a rotací v Javě
url: /cs/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření koláčového grafu s vlastní velikostí, popisky dat a rotací v Javě

Pokud potřebujete **create pie chart** v Javě, tento návod vás provede celým procesem. Naučíte se, jak **set chart size**, povolit **show percentages pie chart**, přidat **data labels pie chart** a **rotate pie chart slice**, aby první výsek začínal pod úhlem 45 stupňů.

Příklad používá **Aspose.Slides for Java**, široce používanou knihovnu pro manipulaci se soubory PowerPoint. Stejné koncepty platí i pro jiné knihovny pro tvorbu grafů; stačí nahradit volání API ekvivalenty ve vašem nástroji.

## Požadavky

* Java 17 nebo novější nainstalováno  
* Maven 3.8+ (nebo Gradle) pro správu závislostí  
* Základní znalost syntaxe Javy  
* Přístup k binárnímu souboru Aspose.Slides for Java (můžete získat bezplatnou zkušební verzi na oficiálních stránkách)

Přidejte závislost do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Vytvoření koláčového grafu – kompletní příklad

Následující program vytvoří snímek PowerPointu, který obsahuje koláčový graf s vlastní velikostí, procentuálními popisky dat a otočeným prvním výsekem.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Proč je každý krok důležitý

| Krok | Účel | Jak souvisí s klíčovými slovy |
|------|------|------------------------------|
| **Insert chart** | **Create pie chart** – hlavní objekt, který vykreslí vizuál. | Přímo splňuje požadavek *create pie chart*. |
| **Set dimensions** | Volání `addChart(..., 400, 300)` demonstruje **set chart size**. | Řídí šířku (400 px) a výšku (300 px). |
| **Show percentages** | `setShowPercentage(true)` způsobí, že graf **show percentages pie chart** na každém výseku. | Uživatelé často potřebují procenta místo surových hodnot. |
| **Add data labels** | Konfigurace `DataLabelFormat` přidává **data labels pie chart** s požadovanou viditelností. | Popisky zlepšují čitelnost a jsou přizpůsobitelné. |
| **Rotate slice** | `setFirstSliceAngle(45)` otáčí graf tak, aby první výsek začínal pod úhlem 45 stupňů, čímž splňuje **rotate pie chart slice**. | Zlepšuje vizuální důraz na konkrétní výsek. |

## Rozbor krok po kroku

### 1. Vložení koláčového grafu a nastavení velikosti grafu

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Metoda `addChart` vytváří graf a současně **set chart size** na 400 × 300 bodů.*  
Pokud potřebujete jinou velikost, upravte poslední dva argumenty.

### 2. Naplnění grafu daty

Demo přidává tři kategorie a jedinou sérii. V případě potřeby nahraďte pevně zakódovaná čísla daty z databáze, CSV nebo vstupu od uživatele.

### 3. Zobrazení procent na každém výseku

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Povolení `setShowPercentage(true)` zajišťuje, že graf **show percentages pie chart** automaticky vypočítá podíl každého výseku na celku.*

### 4. Přidání podrobných popisků dat

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Můžete přepínat další možnosti popisků (`setShowValue`, `setShowSeriesName`, atd.) a přizpůsobit tak zážitek **add data labels pie chart**.

### 5. Otočení prvního výseku

```java
chart.setFirstSliceAngle(45);
```

*Volání `setFirstSliceAngle(45)` **rotate pie chart slice** tak, aby první segment začínal pod úhlem 45 stupňů, čímž jej zvýrazní.*

### 6. Uložení a zobrazení výsledku

Spuštěním programu vznikne `output/PieChartDemo.pptx`. Otevřete jej v PowerPointu nebo jakémkoli kompatibilním prohlížeči a uvidíte finální koláčový graf:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Snímek obrazovky vytvořeného koláčového grafu s vlastní velikostí, procentuálními popisky a otočeným prvním výsekem"}

Obrázek výše demonstruje výsledek **create pie chart**, potvrzující, že velikost, popisky, procenta a rotace jsou aplikovány správně.

## Běžné varianty a okrajové případy

| Situace | Úprava |
|---------|--------|
| **Různé rozměry grafu** | Změňte parametry šířky/výšky v `addChart`. |
| **Více sérií** | Přidejte další objekty `IChartSeries`; každá série může mít vlastní nastavení popisků. |
| **Vlastní formát popisku** | Použijte `series.getDataLabelFormat().setNumberFormat("0.0%")` pro kontrolu desetinných míst. |
| **Rotace na jiný úhel** | Předávejte libovolné celé číslo (0‑360) metodě `setFirstSliceAngle`. |
| **Export jako obrázek** | Po uložení zavolejte `chart.writeAsSvg(outPath)` nebo `chart.writeAsPng(outPath)` pro rastrovou verzi. |

> **Tip:** Pokud plánujete generovat mnoho grafů ve smyčce, znovu použijte stejný objekt `Presentation` a pouze nahraďte data grafu. Tím se sníží paměťová zátěž a zrychlí zpracování.

## Závěr

Nyní víte, jak **create pie chart** v Javě, **set chart size**, povolit **show percentages pie chart**, **add data labels pie chart** a **rotate pie chart slice** pro lepší vizuální důraz. Kompletní, spustitelný příklad demonstruje každý krok od inicializace po uložení finálního souboru PowerPoint.

### Co dál?

* Prozkoumejte další typy grafů (Bar, Line, Area) pomocí stejného výčtu `ChartType`.  
* Kombinujte více grafů na jednom snímku pro dashboardy.  
* Exportujte grafy do PNG nebo SVG pro použití ve webových aplikacích.  

Neváhejte experimentovat s barvami, legendami a animačními efekty—vaše vizualizace dat jsou omezeny jen představivostí. Šťastné grafování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [jak vložit koláčový graf do Wordu – přidat procentuální popisek dat](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Jak rozdělit výsek koláčového grafu v Javě – tutoriál Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Vložení koláčového grafu v Javě – rozdělení, rotace a zvýraznění výseků](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}