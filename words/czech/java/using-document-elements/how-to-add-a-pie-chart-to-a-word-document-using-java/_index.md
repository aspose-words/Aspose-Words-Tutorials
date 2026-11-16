---
category: general
date: 2026-11-15
description: Naučte se, jak přidat koláčový graf do dokumentu Word pomocí Aspose.Words
  pro Javu. Obsahuje převod na prstencový graf, oddělený výsek a kompletní ukázkový
  kód.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: cs
lastmod: 2026-11-15
og_description: Přidejte koláčový graf do dokumentu Word pomocí Aspose.Words pro Java.
  Tento tutoriál ukazuje, jak oddělit výseč a převést graf na prstencový diagram.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Přidejte koláčový graf do dokumentu Word pomocí Javy – průvodce krok za
  krokem
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Jak přidat koláčový graf do dokumentu Word pomocí Javy
url: /cs/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání koláčového grafu do dokumentu Word – kompletní průvodce v Javě

Pokud potřebujete **přidat koláčový graf do dokumentu Word** programově, tento tutoriál vám ukáže přesně, jak na to s Aspose.Words pro Java. Uvidíte celý postup: načtení DOCX, vytvoření koláčového grafu, „explodování“ první výseče a převod grafu na prstencový nastavením velikosti díry.

Průvodce také zahrnuje běžné varianty – například přidání více sérií, úpravu barev a práci s dokumenty, které již grafy obsahují – takže můžete kód přizpůsobit reálným projektům, jako je automatizované reportování nebo dynamické prezentace.

## Požadavky

Než začnete, ujistěte se, že máte:

* Java 17 nebo novější (kód se také kompiluje s JDK 11+)
* Maven 3.6+ nebo Gradle pro správu závislostí
* Licenci Aspose.Words pro Java (bezplatná zkušební verze stačí pro testování)
* Základní znalost syntaxe Javy a struktury Maven projektu

## Krok 1: Nastavení Maven projektu a import Aspose.Words

Vytvořte nový Maven projekt (nebo jej přidejte do existujícího) a zahrňte závislost Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Tip:** Pokud používáte Gradle, ekvivalentní zápis je `implementation 'com.aspose:aspose-words:24.9'`.

Závislost přinese třídy `Document`, `Chart` a `ChartType`, které budete potřebovat pro manipulaci s grafy.

## Krok 2: Načtení cílového dokumentu

Můžete začít s existujícím souborem `.docx` nebo vytvořit nový prázdný dokument. V příkladu níže se načítá šablona `input.docx` umístěná ve složce `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Pokud soubor neexistuje, Aspose.Words automaticky vytvoří nový prázdný dokument při volání `new Document()` bez názvu souboru.

## Krok 3: Vytvoření koláčového grafu a vložení do dokumentu

Aspose.Words považuje graf za tvar, který lze umístit kamkoli, kde může být odstavec. Následující kód vytvoří **koláčový graf**, přidá jedinou datovou sérii a vloží graf za první odstavec.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Proč je tento krok důležitý:**  
* `ChartType.PIE` říká Aspose.Words, aby vykreslil tradiční koláčový graf.  
* Přidání série s kategoriemi i číselnými hodnotami automaticky naplní výseče.  
* Vložení grafu jako potomka `Paragraph` zachová tok dokumentu.

## Krok 4: Explodování první výseče pro zvýraznění

*Explodovaná výseč* upoutá pozornost na konkrétní datový bod. API poskytuje metodu `setExplode(boolean)` na objektu `ChartSeries`. Nastavením této metody na první sérii (index 0) se první výseč odtrhne.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Často kladená otázka:** *Co když mám více sérií?*  
> Můžete cílit na konkrétní sérii podle jejího indexu, např. `pieChart.getSeries().get(1).setExplode(true)` pro druhou sérii.

## Krok 5: Převod koláčového grafu na prstencový nastavením velikosti díry

Prstencový graf je v podstatě koláčový graf s prázdným středem. Aspose.Words umožňuje definovat velikost díry jako procento poloměru grafu.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

Metoda `setHoleSize` přijímá hodnoty od **0** (běžný koláč) do **100** (zcela prázdný). Hodnota kolem **30‑40** poskytuje vizuálně vyvážený prstenec.

## Krok 6: Uložení a ověření výsledku

Po všech úpravách dokument uložte. Následující řádek zapíše soubor do složky `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Očekávaný výstup

Otevřete `final-pie-doughnut.docx` v Microsoft Word:

* Na místě prvního odstavce se objeví prstencový graf.
* Výseč „Apples“ je explodovaná (lehce oddělená od ostatních).
* Graf zobrazuje čtyři výseče označené *Apples*, *Bananas*, *Cherries*, *Dates* s procenty, které jste zadali.

Pokud chcete výstup v PDF, změňte `SaveFormat` na `SaveFormat.PDF`.

## Řešení okrajových případů a variant

### Přidání více sérií

Pokud potřebujete několik sérií (např. vrstvený prstenec), přidejte je postupně:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Vlastní barvy

Barvu můžete přiřadit každé výseči pomocí `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Práce s existujícím grafem

Pokud dokument již obsahuje graf a chcete jej jen upravit, najděte tvar grafu:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Správa licence

Aspose.Words vyžaduje licenci pro produkční použití. Umístěte soubor `Aspose.Words.lic` do classpath a načtěte jej při startu aplikace:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Nastavení licence je povinné – bez ní se do vygenerovaného dokumentu vloží vodoznak.

## Kompletní spustitelný příklad

Níže je kompletní třída Java, která zahrnuje všechny probírané kroky. Zkopírujte ji do `src/main/java/com/example/AddPieChart.java` a spusťte `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Po spuštění programu se vytvoří popsaný prstencový graf. Upravit můžete `categories`, `values` nebo `holeSize` podle svých dat.

## Závěr

Nyní víte, jak **přidat koláčový graf do dokumentu Word** pomocí Javy a Aspose.Words. Tutoriál pokryl načtení dokumentu, vytvoření koláčového grafu, explodování výseče, převod grafu na prstenec a řešení běžných variant, jako jsou více sérií, vlastní barvy a existující grafy. S tímto základem můžete budovat automatizované nástroje pro reportování, generovat dynamické prezentace nebo vkládat bohaté vizualizace přímo do souborů Word.

### Co zkusit dál

* **add bar chart to Word document** – podobné kroky, ale použijte `ChartType.BAR`.  
* **customize chart legends and titles** – použijte `pieChart.getTitle().setText("...")` a `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **export the Word document as PDF** – změňte `SaveFormat` na `PDF` pro soubory připravené k distribuci.  
* **populate chart data from a database** – nahraďte statické pole výsledky dotazu JDBC.

Neváhejte experimentovat s různými typy grafů, zdroji dat a možnostmi stylování. Šťastné programování!

## Co se naučíte dál?

Následující tutoriály se věnují úzce souvisejícím tématům, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}