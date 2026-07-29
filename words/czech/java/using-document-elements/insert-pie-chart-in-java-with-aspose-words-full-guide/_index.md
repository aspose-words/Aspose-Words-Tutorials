---
category: general
date: 2026-07-29
description: Vložte koláčový graf pomocí Aspose.Words pro Java a naučte se, jak vytvořit
  prstencový graf, formátovat koláčový graf, formátovat graf ve Wordu a přizpůsobit
  velikost grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: cs
lastmod: 2026-07-29
og_description: Vložte koláčový graf pomocí Aspose.Words pro Java a rychle se naučte
  vytvářet prstencový graf, formátovat koláčový graf, formátovat graf ve Wordu a přizpůsobit
  velikost grafu pro profesionální dokumenty.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Vložení koláčového grafu v Javě – Kompletní tutoriál Aspose.Words
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
title: Vložení koláčového grafu v Javě s Aspose.Words – kompletní průvodce
url: /cs/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení koláčového grafu v Javě s Aspose.Words – Kompletní průvodce

Už jste se někdy zamýšleli, jak **vložit koláčový graf** do dokumentu Word z Java kódu? Nejste jediní — mnoho vývojářů narazí na tento problém, když potřebují rychlý programový způsob vizualizace dat. Dobrá zpráva? S Aspose.Words pro Java to zvládnete během několika řádků a při tom můžete také **vytvořit prstencový graf**, **formátovat koláčový graf**, **formátovat graf ve Wordu** a **přizpůsobit velikost grafu** tak, aby odpovídala vaší značce.

V tomto tutoriálu projdeme reálný příklad, který začíná vytvořením prázdného dokumentu, vložením koláčového grafu, úpravou několika vizuálních vlastností a nakonec uložením souboru. Na konci budete mít znovupoužitelný úryvek, který můžete vložit do libovolného Java projektu potřebujícího automatizaci grafů. Žádné další knihovny, žádné ruční manipulace s Office interop — jen čistá, kompilovaná Java.

## Co budete potřebovat

- **Java 17** (nebo jakýkoli novější JDK; API je zpětně kompatibilní)
- **Aspose.Words for Java** 22.12 nebo novější — můžete si stáhnout Maven artefakt nebo .jar ze stránek Aspose.
- Skromné IDE (IntelliJ IDEA, Eclipse, VS Code…) — cokoliv, co vám umožní spustit metodu `main`.
- Volitelně: licenční soubor, pokud nechcete vodotisk z evaluační verze.

Pokud máte vše připravené, můžeme rovnou přejít k kódu.

## Krok 1: Vložení koláčového grafu s Aspose.Words

První věc, kterou uděláme, je **vložit koláčový graf** do nového dokumentu. Tento krok připraví podmínky pro vše ostatní, protože objekt grafu nám poskytuje přístup k řadám, datovým bodům a vizuálním úpravám.

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

> **Proč je to důležité:** `DocumentBuilder.insertChart` nejenže vytvoří graf, ale také vrátí objekt `Chart`, který můžeme dále manipulovat. Argumenty šířky a výšky vám umožní **přizpůsobit velikost grafu** již při jeho vytvoření, takže později není nutné měnit rozměry.

## Krok 2: Vytvoření prstencového grafu (volitelné)

Pokud váš návrh vyžaduje díru uprostřed — myslete na klasický prstencový graf — Aspose to zvládne jedním řádkem. Stejná instance `Chart` může být přepnuta z běžného koláčového grafu na prstencový úpravou velikosti díry.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** Velikost díry funguje jen pro `ChartType.DONUT`. Pokud ponecháte typ jako `PIE`, volání se ignoruje, takže můžete experimentovat.

## Krok 3: Formátování výsečů koláčového grafu

Dobrá vizualizace často zvýrazní konkrétní výseč. Zde **formátujeme koláčový graf** tak, že první výseč „explodujeme“ o 20 bodů ven. Tím přitáhnete pozornost čtenáře k nejdůležitějšímu datovému bodu.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** Můžete projít `pieChart.getSeries()` pokud máte více řad a nastavit jednotlivé barvy, okraje nebo popisky dat. To je cesta, jak **formátovat graf ve Wordu** s bohatým stylingem.

## Krok 4: Přidání dat do grafu

Graf bez dat je jen dekorativní tvar. Přidáme mu jednoduchý datový soubor — například čtvrtletní prodeje.

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

> **Proč to děláme:** Explicitním přidáním objektů `ChartPoint` zajistíme, že graf odráží naši obchodní logiku. Volání `setShowCategoryName` a `setShowValue` jsou součástí **formátování koláčového grafu**, aby se zobrazovaly jak štítky kategorií, tak hodnoty.

## Krok 5: Doladění vzhledu (přizpůsobení velikosti a stylu grafu)

Kromě počátečních rozměrů můžete chtít upravit legendu, název nebo i písmo použité pro popisky dat. Všechny tyto úpravy spadají pod **přizpůsobení velikosti grafu** a celkové formátování.

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

> **Hraniční případ:** Pokud se později rozhodnete exportovat dokument do PDF, vektorová data grafu zůstanou ostrá, protože velikost je definována v bodech, ne v pixelech. To je výhoda pro **formátování grafu ve Wordu** a následné formáty.

## Krok 6: Uložení a zobrazení dokumentu

Poslední krok je tak jednoduchý jako volání `doc.save`. Tím se vytvoří soubor `.docx`, který můžete otevřít v Microsoft Word, LibreOffice nebo jakémkoli prohlížeči podporujícím formát OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Výsledek:** Otevřete `PieChart.docx` a uvidíte pěkně velikostně nastavený koláčový (nebo prstencový) graf s explodovanou výsečí, názvem a legendou — vše vygenerováno bez jakéhokoli zásahu do UI.

### Očekávaný výstup

| Prvek | Co uvidíte |
|-------|------------|
| Typ grafu | Koláčový graf (nebo prstencový, pokud je `holeSize` > 0) |
| Exploze výseče | První výseč posunutá o 20 bodů |
| Legenda | Umístěná vpravo |
| Název | “Quarterly Sales Distribution” tučně, 14 pt |
| Popisky dat | Název kategorie a hodnota zobrazené na každé výseči |
| Dokument | Standardní Word `.docx` soubor připravený ke sdílení |

## Časté otázky a úskalí

- **Potřebuji licenci?**  
  Evaluační verze funguje pro testování, ale přidává vodotisk. Umístěte soubor `aspose.words.lic` do classpath pro čistý výstup.

- **Mohu to použít s Mavenem?**  
  Rozhodně. Přidejte následující závislost do svého `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Co když mám více než jednu řadu?**  
  Projděte `pieChart.getSeries()` a použijte `setExplosion`, `setFillColor` nebo jiné formátování pro každou řadu. To je způsob, jak **formátovat koláčový graf** pro vícerozměrná data.

- **Lze graf po vygenerování upravovat ve Wordu?**  
  Ano — po uložení můžete dokument otevřít a ručně měnit barvy, písma nebo dokonce převést koláčový graf na sloupcový, pokud to potřebujete.

## Závěr

Právě jsme **vložením koláčového grafu** do Word dokumentu pomocí Aspose.Words pro Java ukázali, jak **vytvořit prstencový graf**, demonstrovali různé způsoby **formátování koláčového grafu**, probrali nejlepší postupy **formátování grafu ve Wordu** a naučili se **přizpůsobit velikost grafu** pro profesionální vzhled. Kompletní, spustitelný příklad výše můžete vložit do libovolného Java projektu a získat okamžitou automatizaci grafů bez zátěže COM interopu nebo instalace Office.

Co dál? Zkuste nahradit zdroj dat živou databází, přidejte podmíněné barvy podle prahových hodnot nebo exportujte stejný dokument do PDF pro tiskovou verzi. Každý z těchto kroků staví na základech, které jsme vytvořili, takže přechod bude plynulý.

Pokud narazíte na problémy nebo máte nápady na další vylepšení — třeba vrstvený sloupcový graf nebo čárový graf — zanechte komentář níže. Šťastné grafování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}