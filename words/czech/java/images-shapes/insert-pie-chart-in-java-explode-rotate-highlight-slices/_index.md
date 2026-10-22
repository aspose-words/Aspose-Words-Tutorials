---
category: general
date: 2026-07-20
description: Vložte koláčový graf v Javě s podrobným návodem krok za krokem. Naučte
  se, jak rozdělit výsek, jak otočit koláčový graf, zvýraznit výsek koláčového grafu
  a přizpůsobit výsek koláčového grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: cs
lastmod: 2026-07-20
og_description: Vložte koláčový graf v Javě a naučte se, jak rozdělit výseč, jak otáčet
  koláčový graf, zvýraznit výseč koláčového grafu a přizpůsobit výseč koláčového grafu
  pro profesionální vizuální zprávy.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Vložení koláčového grafu v Javě – rozdělit, otočit a zvýraznit
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Vložení koláčového grafu v Javě – rozdělení, otáčení a zvýraznění výsečů
url: /cs/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení koláčového grafu v Javě – Rozbalení, otočení a zvýraznění výsečů

Už jste někdy potřebovali **vložit koláčový graf** do Java reportu, ale nebyli jste si jisti, jak jednu výseč vyčlenit? Nejste v tom sami. Ať už vytváříte dashboard, generujete fakturu nebo jen vizualizujete výsledky průzkumu, dobře stylizovaný koláčový graf může proměnit surová čísla v okamžitě pochopitelný přehled.

V tomto tutoriálu uvidíte kompletní, připravený příklad, který vám ukáže, jak **vložit koláčový graf**, **rozbalit výseč**, **otočit koláčový graf** a dokonce **zvýraznit výseč koláčového grafu** pomocí vlastních barev. Na konci budete mít znovupoužitelný úryvek, který můžete vložit do jakéhokoli Java projektu používajícího populární *JFreeChart* knihovnu (nebo jakékoli podobné API).

## Požadavky

- Java 17 nebo novější (kód se kompiluje i se staršími verzemi, ale pro stručnost použijeme moderní syntaxi `var`).
- Maven nebo Gradle pro stažení závislosti `org.jfree:jfreechart`.
- Základní pochopení Java tříd a konceptu tvůrce grafu.

Pokud jste nikdy nepřidávali knihovnu do Maven projektu, stačí vložit toto do vašeho `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

A to je vše—žádné další nastavení není potřeba.

## Krok 1: Vložení koláčového grafu – Vytvoření builderu a objektu grafu

Nejprve potřebujeme *builder* (považujte ho za továrnu), který umí vytvářet grafy. V JFreeChart za těžkou práci zodpovídá `ChartFactory`.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Proč začínáme datovým souborem? Protože samotný graf je jen vizuální obálkou čísel. **Vložením koláčového grafu** zde již máme plátno o rozměrech 400 × 300 (velikost bude aplikována později při vykreslování do obrázku).

## Krok 2: Jak rozbalit výseč – Zvýraznění první segmentu

Nyní, když graf existuje, udělejme první výseč výraznější. Rozbalení výseče ji mírně oddělí od kruhu, čímž upoutá pozornost čtenáře.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Všimněte si, že v názvu metody používáme frázi **how to explode slice**; to jasně vyjadřuje záměr. Metoda `setExplodePercent` přijímá klíč (popisek výseče) a procento, takže můžete podle potřeby upravit vzdálenost „vyčlenění“.

## Krok 3: Jak otočit koláčový graf – Změna výchozího úhlu

Výchozí koláčový graf začíná v pozici 12 hodin. Někdy chcete, aby první výseč začínala jinde – možná aby odpovídala návrhu nebo jinému grafu.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Volání `rotateChart(chart, 45)` otočí celý koláč tak, aby výseč „Apples“ začínala pod úhlem 45 stupňů, což přesně odpovídá požadavku **how to rotate pie chart**.

## Krok 4: Zvýraznění výseče koláčového grafu – Vlastní barvy a popisky

Kromě rozbalení můžete výseč chtít přiřadit jedinečnou barvu nebo tučný popisek, abyste skutečně **zvýraznili výseč koláčového grafu**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Zde jsme **customize pie chart slice** změnou barvy a stylu popisku. Klidně změňte barvu nebo písmo, aby odpovídaly vaší firemní paletě.

## Krok 5: Vykreslení grafu do obrázku (volitelné, ale užitečné)

Většina reálných aplikací potřebuje graf jako PNG, JPEG nebo dokonce PDF. Níže je rychlý způsob, jak graf zapsat do souboru.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Spuštěním celého postupu vznikne PNG o rozměrech 400 × 300, které vypadá zhruba takto:

![Příklad vložení koláčového grafu](image.png){: alt="Příklad vložení koláčového grafu ukazující rozbalenou a otočenou výseč"}

## Kompletní funkční příklad

Spojením všech částí zde máte metodu `main`, kterou můžete zkopírovat do nové Java třídy a spustit:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Očekávaný výstup

Spuštěním programu se vytvoří soubor s názvem **fruit-pie.png**. Otevřete jej a uvidíte:

- Koláčový graf o rozměrech 400 × 300 s názvem „Fruit Distribution“.
- Výseč „Apples“ rozbalená ven o 15 %.
- Celý graf otočený tak, aby „Apples“ začínala na 45‑stupňové pozici.
- Rozbalená

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Vložit rozptylový graf](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Vložit plošný graf](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}