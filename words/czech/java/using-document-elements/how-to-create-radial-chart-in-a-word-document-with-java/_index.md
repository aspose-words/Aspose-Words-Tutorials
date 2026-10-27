---
category: general
date: 2026-09-18
description: Naučte se, jak vytvořit radiální graf v dokumentu Word pomocí Javy, přidat
  popisky dat grafu a vložit data řady s kompletním příkladem kódu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: cs
lastmod: 2026-09-18
og_description: Vytvořte radiální graf v dokumentu Word pomocí Javy, přidejte popisky
  dat grafu a vložte data řady v jednom tutoriálu.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Vytvořte radiální graf ve Wordu pomocí Javy – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Jak vytvořit radiální graf v dokumentu Word pomocí Javy
url: /cs/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit radiální graf v dokumentu Word pomocí Javy

Pokud potřebujete vytvořit radiální graf v dokumentu Word, tento návod vám ukáže přesné kroky. Také se naučíte, jak přidat popisky dat grafu a vložit data řady, aby byl graf připraven k prezentaci.

Generování grafu programově odstraňuje ruční formátování a zaručuje konzistenci napříč reporty. Tutoriál předpokládá základní znalost Javy a nainstalovanou aktuální verzi knihovny Aspose.Words pro Java.

## Co budete potřebovat

* Java 17 nebo novější  
* Aspose.Words pro Java (verze 23.12 nebo novější)  
* IDE nebo nástroj pro sestavení, který dokáže vyřešit Maven/Gradle závislosti  

Mít tyto předpoklady nainstalované vám umožní spustit příklad bez další konfigurace.

## Jak vytvořit radiální graf v dokumentu Word

Prvním krokem je vytvořit prázdný soubor Word, který bude hostit graf. Prázdný dokument poskytuje čisté plátno a zabraňuje nechtěným stylům.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` představuje celý soubor .docx, zatímco `DocumentBuilder` poskytuje metody pro vkládání prvků, jako jsou odstavce, tabulky a grafy.

## Jak vložit graf

Dále vložíte samotný graf. Metoda `insertChart` vytvoří objekt grafu a umístí jej na aktuální pozici kurzoru builderu.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Polární graf vykresluje datové body kolem centrální osy, což je ideální pro zobrazování cyklických informací. Rozměry jsou vyjádřeny v bodech (1 pt ≈ 1/72 palce).

## Přidání dat řady do grafu

Graf bez dat řady je prázdný. Můžete přidat řadu ručně nebo ji svázat s datovým zdrojem. Níže uvedený příklad přidává jednu řadu se třemi datovými body.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` přijímá název řady, seznam štítků kategorií a seznam odpovídajících číselných hodnot. Tento blok můžete opakovat pro přidání dalších řad (`addSeriesData`).

## Přidání popisků dat grafu k první řadě

Popisky dat činí graf čitelným i bez přejetí myší nad body. Následující řádek zapíná popisky hodnot pro první řadu.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Nastavením `showValue` na `true` se hodnota každého bodu zobrazí přímo v grafu. Stejným objektem `DataLabelFormat` můžete také povolit názvy kategorií, procenta nebo čáry ukazatele.

## Uložení souboru Word

Po nakonfigurování grafu zapište dokument na disk. Vyberte umístění, ke kterému má vaše aplikace přístup.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Soubor `RadialChart.docx` nyní obsahuje plně funkční radiální graf s popisky dat.

## Plně funkční příklad

Níže je samostatný program, který můžete zkopírovat, zkompilovat a spustit. Ukazuje kompletní workflow od vytvoření prázdného dokumentu Word až po uložení radiálního grafu s popisky dat.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Očekávaný výsledek**

Když otevřete `output/RadialChart.docx` v Microsoft Word, uvidíte radiální graf s názvem *Quarterly Sales*. Každý bod zobrazuje svou číselnou hodnotu (např. „15000“) vedle značky.

## Běžné varianty a okrajové případy

| Situace | Doporučená změna |
|-----------|--------------------|
| Potřebujete jiný typ grafu | Nahraďte `ChartType.POLAR` libovolnou jinou hodnotou výčtu `ChartType` (např. `ChartType.COLUMN`). |
| Graf musí používat externí oblast v Excelu | Použijte `chart.setDataRange("Sheet1!A1:B5")` po vytvoření grafu a načtení sešitu. |
| Chcete skrýt legendu | `chart.getLegend().setVisible(false);` |
| Dokument má být uložen jako PDF | Zavolejte `doc.save("RadialChart.pdf");` – Aspose.Words automaticky převede graf. |

Tyto úpravy zachovávají hlavní logiku, zatímco přizpůsobují výstup konkrétním požadavkům.

## Profesionální tipy

* **Znovupoužití builderu** – Můžete vkládat více grafů do stejného dokumentu opakovaným voláním `builder.insertChart`.
* **Výkon** – Při generování mnoha grafů vytvořte jedinou instanci `DocumentBuilder` a znovu ji použijte, abyste snížili režii alokace objektů.
* **Styling** – Vzhled grafu (barvy, tloušťka čáry) je řízen metodami objektu `Chart` přes `getSeries().get(i).getFormat()`. Experimentujte s těmito nastaveními, aby graf odpovídal firemní identitě.

## Závěr

Nyní víte, jak vytvořit radiální graf v dokumentu Word pomocí Javy, přidat data řady a popisky dat před uložením souboru. Kompletní příklad lze rozšířit o další řady, vlastní styly nebo alternativní výstupní formáty.

Prozkoumejte související témata, jako je **how to insert chart** z externích datových zdrojů, **create blank word** dokumenty s předdefinovanými šablonami a **add series data** dynamicky z databází. Vyzkoušejte různé typy grafů a zjistěte, který vizuál nejlépe komunikuje vaše data.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}