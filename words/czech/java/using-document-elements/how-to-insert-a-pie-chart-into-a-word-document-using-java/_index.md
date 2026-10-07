---
category: general
date: 2026-09-27
description: Naučte se, jak vložit koláčový graf do dokumentu Word pomocí Javy, vytvořit
  koláčový graf ve Wordu a zobrazit procenta na koláčovém grafu pro jasný přehled
  o datech.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: cs
lastmod: 2026-09-27
og_description: Jak vložit koláčový graf do dokumentu Word pomocí Javy. Tento průvodce
  vám ukáže, jak vytvořit koláčový graf ve Wordu, zobrazit procenta na koláčovém grafu
  a přidat čáry spojující.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Jak vložit koláčový graf do dokumentu Word pomocí Javy
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Jak vložit koláčový graf do dokumentu Word pomocí Javy
url: /cs/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit koláčový graf do dokumentu Word pomocí Javy

Pokud potřebujete **jak vložit koláčový graf** do souboru Word, tento průvodce vás provede celým procesem. Ukážeme vám, jak **vytvořit koláčový graf ve Wordu**, zobrazit procenta na každém výseku a přidat vodící čáry pro profesionální vzhled.

Automatizace Wordu se často zdá těžkopádná, ale s Aspose.Words pro Java můžete programově generovat plně formátované dokumenty. Na konci tohoto tutoriálu budete mít spustitelný úryvek Javy, který vytvoří dokument Word obsahující stylizovaný koláčový graf.

## Požadavky

Než začnete, ujistěte se, že máte:

- Java 17 nebo novější nainstalovanou
- Maven nebo Gradle pro správu závislostí
- Aspose.Words pro Java (verze 23.11 nebo novější) přidanou do vašeho projektu
- Základní znalosti syntaxe Javy

Nemusíte mít předchozí zkušenosti s API grafů; níže uvedené kroky pokrývají vše od nastavení projektu až po finální výstup.

## Krok 1: Nastavte Maven závislost

Přidejte knihovnu Aspose.Words do souboru `pom.xml`. Tato jediná závislost vám poskytne přístup k třídám `Document`, `DocumentBuilder` a grafům.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Pokud používáte Gradle, ekvivalent je:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Tip:** Použijte nejnovější stabilní verzi, abyste získali opravy chyb a nové funkce grafů.

## Krok 2: Vytvořte nový dokument a builder

Objekt `Document` představuje soubor Word, zatímco `DocumentBuilder` vám umožní vkládat obsah. Toto je základ pro **přidat graf do dokumentu Word**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder je nyní připraven umístit objekty kdekoliv v dokumentu.

## Krok 3: Vložte koláčový graf

Aspose.Words podporuje několik typů grafů; zvolíme `ChartType.PIE`. Velikost se udává v bodech (1 bod = 1/72 palce).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

V tomto okamžiku graf obsahuje výchozí datovou sérii s placeholder hodnotami. Tyto hodnoty můžete později nahradit, pokud bude potřeba.

## Krok 4: Přístup k sérii grafu

Koláčový graf má jedinou sérii, která drží hodnoty výseků. Získejte ji pro aplikaci formátování.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Krok 5: Explodujte první výsek

Explodování výseku přitahuje pozornost k určitému datovému bodu. Jedná se o běžný vizuální prvek, když chcete zdůraznit klíčovou metriku.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Krok 6: Zobrazte procenta na každém výseku

Zobrazení procent přímo na grafu zlepšuje přehlednost dat. Tím splňujete požadavek **zobrazit procenta na koláčovém grafu**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Krok 7: Přidejte vodící čáry pro přehlednější popisky

Vodící čáry spojují popisky výseků s jejich odpovídajícími částmi, čímž odstraňují nejasnosti. Tím se naplňuje **jak přidat vodící čáry**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Krok 8: Uložte dokument

Nakonec zapište dokument na disk. Můžete zvolit libovolnou složku, do které máte právo zápisu.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Po spuštění programu se vytvoří `output/PieFormatted.docx`. Otevřete soubor v Microsoft Word a uvidíte koláčový graf, kde:

- První výsek je explodován.
- Každý výsek zobrazuje svou procentuální hodnotu.
- Vodící čáry ukazují z procent na odpovídající výseky.

### Očekávaný výstup

![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image alt="Formátovaný koláčový graf vložený do dokumentu Word"}

Snímek obrazovky (alt text používá primární klíčové slovo) ilustruje finální vzhled: čistý, datově řízený koláčový graf připravený pro zprávy, návrhy nebo dashboardy.

## Běžné varianty a okrajové případy

### Změna hodnot výseků

Pokud potřebujete vlastní data, nahraďte výchozí hodnoty série:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Více sérií (donut graf)

Zatímco jednoduchý koláčový graf má jednu sérii, Aspose.Words také podporuje donut grafy s více sériemi. Přepněte `ChartType.PIE` na `ChartType.DONUT` a opakujte kroky konfigurace sérií.

### Export do PDF

Pokud váš následný workflow vyžaduje PDF, zavolejte `doc.save("output/PieFormatted.pdf");` po vytvoření grafu. Vizuální rozložení zůstane totožné.

## Kompletní výpis zdrojového kódu

Níže je kompletní, samostatný soubor Java, který můžete zkopírovat a vložit do svého IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Zkompilujte a spusťte program pomocí `mvn compile exec:java -Dexec.mainClass=PieChartExample` (nebo ekvivalentního příkazu Gradle). Vygenerovaný soubor Word bude obsahovat plně formátovaný koláčový graf.

## Závěr

Nyní víte, **jak vložit koláčový graf** do dokumentu Word pomocí Javy, **jak vytvořit koláčový graf ve Wordu**, **jak zobrazit procenta na koláčovém grafu** a **jak přidat graf do dokumentu Word** s vodícími čarami. Kompletní příklad demonstruje každý krok, vysvětluje, proč je kód napsán tak, jak je, a poskytuje tipy pro přizpůsobení.

Dále můžete zkoumat:

- Přidání popisků dat s vlastními fonty (**zobrazit procenta na koláčovém grafu** varianty)
- Kombinování více grafů v jednom dokumentu (**přidat graf do dokumentu Word** případy použití)
- Automatizaci generování zpráv s tabulkami a grafy dohromady

Neváhejte experimentovat s barvami, pořadím výseků nebo exportem do PDF. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Javu](/words/english/java/document-conversion-and-export/using-charts/)
- [Skrýt osu grafu v dokumentu Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Vytvořit čárový graf ve Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}