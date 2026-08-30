---
category: general
date: 2026-08-07
description: Jak rozdělit výseč koláčového grafu v Javě pomocí Aspose.Words. Naučte
  se přidávat vodící čáry k výsečím, vytvářet grafy ve Wordu a přizpůsobovat výseče
  koláčového grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: cs
lastmod: 2026-08-07
og_description: Jak oddělit výseč koláčového grafu v Javě pomocí Aspose.Words. Tento
  průvodce vám ukáže, jak přidat vodící čáry k výsečím, vytvořit grafy ve Wordu a
  přizpůsobit výseče koláčového grafu pro jasný vizuální dopad.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Jak vytáhnout výseč koláče v Javě – průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Jak explodovat výseč koláčového grafu v Javě – tutoriál grafu Aspose.Words
url: /cs/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak rozdělit výseč koláče v Java – tutoriál k diagramům Aspose.Words

Pokud potřebujete vědět **jak rozdělit výseč koláče** v dokumentu Word pomocí Javy, tento tutoriál vás provede. Také vám ukážeme **jak přidat vodící čáry k výsečovým** grafům, **java create word chart** objekty a **přizpůsobit výseče koláčového grafu** pro profesionální výsledek. Na konci tohoto průvodce budete mít kompletní, spustitelný příklad, který můžete vložit do libovolného Java projektu.

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## Požadavky

* Java Development Kit (JDK) 8 nebo vyšší.
* Maven nebo Gradle pro správu závislostí.
* Licence Aspose.Words pro Java (bezplatná zkušební verze funguje pro výukové účely).
* Základní znalost syntaxe Javy a objektově orientovaných konceptů.

> **Tip:** I když Aspose.Words nabízí bezplatnou zkušební verzi, zakoupení licence odstraní vodoznak z generovaných dokumentů.

## Co tento tutoriál pokrývá

* Vytvoření nového dokumentu Word od nuly.  
* Vložení **pie chart** pomocí `DocumentBuilder`.  
* **Exploding a pie slice** pro zvýraznění datového bodu.  
* **Adding leader lines to pie** pro jasnější popisky.  
* Přizpůsobení vzhledu výseč, například barvy a okraje.  
* Uložení dokumentu na disk a ověření výsledku.

---

## Jak rozdělit výseč koláče pomocí Aspose.Words v Java

Prvním krokem je nastavit objekt grafu a rozdělit požadovanou výseč. Aspose.Words zpřístupňuje graf pomocí třídy `Shape` a každá výseč je `ChartPoint`. Nastavením vlastnosti `Explosion` řídíte, jak daleko se výseč posune ven.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Proč to funguje:**  
`setExplosion(20)` říká motoru grafu, aby posunul výseč o 20 bodů od středu grafu. Hodnota je relativní; větší čísla vytvářejí dramatický efekt. Můžete rozdělit libovolnou výseč změnou indexu (`get(1)`, `get(2)`, …).

## Přidání vodících čar k výsečovému grafu pro jasnější popisky

Vodící čáry spojují popisek výseče s jejím okrajem, což je zvláště užitečné, když jsou výseče rozděleny nebo když graf obsahuje mnoho malých částí. Volání `setLeaderLines(true)` tuto funkci povolí pro celou sérii.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Proč potřebujete vodící čáry:**  
Když je výseč rozdělená, výchozí popisek může překrývat jiné prvky. Vodící čáry udržují popisek čitelný tím, že nakreslí krátkou čáru od výseče k textovému poli.

## Java create Word chart – vkládání datových sérií

Graf bez dat není příliš užitečný. Musíte naplnit sérii kategoriemi a hodnotami. Níže přidáváme tři kategorie představující podíl na trhu.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Vysvětlení:**  
`ChartSeries` obsahuje jak kategorie (názvy výsečí), tak číselné hodnoty. Povolení `ShowCategoryName` a `ShowPercentage` dělá graf samovysvětlujícím, což se dobře doplňuje s vodícími čarami, které jsme přidali dříve.

## Přizpůsobení výsečí koláčového grafu nad rámec rozdělení

Kromě rozdělení výseče často chcete upravit barvy, okraje nebo dokonce výseč úplně skrýt. Následující úryvek ukazuje tři běžné úpravy:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Proč přizpůsobovat výseče:**  
Vlastní barvy umožňují, aby graf odpovídal firemnímu brandingu, zatímco okraje zlepšují čitelnost na tištěných stránkách. Skrytí výseče je užitečné, když chcete zachovat datový model nedotčený, ale dočasně vynechat kategorii z vizuálního výstupu.

## Uložení dokumentu a ověření výsledku

Nakonec zapište dokument na disk. Vygenerovaný `.docx` můžete otevřít v Microsoft Word, LibreOffice nebo v jakémkoli prohlížeči, který podporuje tento formát.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Očekávaný výstup:**  
Když otevřete `PieChartDemo.docx`, uvidíte koláčový graf, kde je první výseč (Product A) rozdělená ven, vodící čáry ukazují z každé výseče na její popisek a výseče jsou zobrazeny ve vlastních zelených, modrých a oranžových barvách. Skrytá výseč (Product C) nebude viditelná, ale procenta se stále sečtou na 100 %, protože data zůstávají v sérii grafu.

---

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit po přidání závislosti Aspose.Words do vašeho projektu.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Závislost (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Jak načíst Word dokumenty s Aspose.Words Java: komplexní průvodce](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}