---
category: general
date: 2026-09-24
description: Vložte koláčový graf do souboru DOCX pomocí Aspose.Words pro Java. Naučte
  se nastavit velikost díry, rozbalit výseč koláče, zvýraznit výseč koláčového grafu
  a snadno vytvořit graf v DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: cs
lastmod: 2026-09-24
og_description: Vložte koláčový graf do DOCX pomocí Aspose.Words pro Java. Ovládněte
  nastavení velikosti díry, roztržení výseče koláče, zvýraznění výseče koláčového
  grafu a vytvořte DOCX graf během několika minut.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Vložení koláčového grafu v Javě – krok za krokem návod
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Vložení koláčového grafu v Javě – kompletní průvodce
url: /cs/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení koláčového grafu do Wordu v Javě – kompletní průvodce

Pokud potřebujete **vložit koláčový graf** do souboru DOCX, tento tutoriál vám přesně ukáže, jak to provést pomocí Aspose.Words pro Java. Uvidíte celý postup od vytvoření dokumentu po přizpůsobení grafu tak, aby byl výsek explodován, velikost díry nastavena na nulu a výsek zvýrazněn.

Práce s grafy v dokumentech Word často působí jako samostatná oblast oproti běžnému zpracování textu, ale Aspose.Words je sjednocuje. V následujících krocích se také naučíte, jak **vytvořit DOCX graf** soubory, které lze otevřít v Microsoft Word, Google Docs nebo v jakémkoli jiném prohlížeči kompatibilním s DOCX.

## Co dosáhnete

* **Vložit koláčový graf** do prázdného dokumentu  
* **Nastavit velikost díry** pro převod grafu na celý koláč (bez donutu)  
* **Explodovat výsek koláče** pro zvýraznění konkrétního segmentu  
* **Zvýraznit výsek koláčového grafu** pomocí vlastního formátování  
* **Vytvořit DOCX graf**, který lze sdílet nebo dále upravovat  

### Požadavky

* Java 17 nebo novější (kód se také kompiluje s Java 8)  
* Knihovna Aspose.Words pro Java (verze 23.9 nebo novější)  
* IDE nebo nástroj pro sestavení (Maven/Gradle), který dokáže vyřešit závislost Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Jak vložit koláčový graf do DOCX pomocí Aspose.Words

Prvním krokem je vytvořit nový prázdný dokument a získat `DocumentBuilder`. Builder vám poskytuje přímý přístup k proudu obsahu dokumentu, což usnadňuje **vložit koláčový graf**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Proč je to důležité
`Document` představuje celý soubor Word, zatímco `DocumentBuilder` je vysoce‑úrovňové API, které vám umožňuje vkládat odstavce, tabulky a grafy, aniž byste se museli zabývat nízko‑úrovňovým XML. Začátek s čistým dokumentem zajišťuje, že přidaný graf bude jediným obsahem, což je ideální pro učení nebo generování zpráv založených na šablonách.

## Nastavte velikost díry pro vytvoření plného koláče

Ve výchozím nastavení Aspose.Words vytváří donut graf, když požadujete koláčový graf. Aby byl graf skutečným kruhem, musíte **nastavit velikost díry** na `0`. Tím se odstraní vnitřní díra a získá se klasický vzhled koláče.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Praktický tip
Pokud se později rozhodnete přepnout na donut graf, stačí změnit hodnotu `holeSize` na procento (např. `30`). Stejné API funguje pro oba typy grafů.

## Explodovat výsek koláče pro zvýraznění segmentu

Explodování výseku jej vizuálně zvýrazní. Operace **explodovat výsek koláče** posune vybraný výsek ven podle procenta poloměru grafu.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Proč explodovat?
Explodovaný výsek přitahuje pozornost čtenáře k nejdůležitějšímu datovému bodu—ideální pro dashboardy nebo výkonné souhrny. Hodnota `20` znamená 20 % poloměru; můžete ji nastavit mezi `0` (žádná exploze) a `100` (zcela oddělený).

## Zvýraznit výsek koláčového grafu pomocí vlastního formátování

Kromě explodování můžete chtít **zvýraznit výsek koláčového grafu** změnou barvy výplně nebo okraje. Zatímco demonstrační kód se zaměřuje na explozi, můžete jej rozšířit následovně:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Poznámka experta
Změna barvy výplně konkrétního výseku vyžaduje přístup k objektu `DataPoint`. Pokud máte více sérií, iterujte přes `series.getDataPoints()` a podmíněně aplikujte styly.

## Uložení a ověření vytvořeného DOCX grafu

Nakonec **vytvoříte DOCX graf** uložením `Document`. Výsledný soubor lze otevřít v Microsoft Word a zobrazit tak naformátovaný koláčový graf.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Očekávaný výstup
Otevření `PieChartFormatted.docx` zobrazí jediný koláčový graf:

* Graf zabírá oblast 400 × 300 pt.  
* Velikost díry je `0`, takže graf je celý koláč.  
* První výsek je explodován o 20 % a obarven červeně (pokud jste přidali volitelné formátování).  

Nyní máte **vytvořený DOCX graf**, který lze distribuovat, vložit do e‑mailů nebo dále programově upravovat.

---

## Běžné varianty a okrajové případy

| Scénář | Jak upravit kód |
|----------|----------------------|
| **Více sérií** | Procházejte `pieChart.getChart().getSeries()` a nastavte `Explosion` nebo `FillColor` pro každou sérii. |
| **Dynamická data** | Naplněte sérii hodnotami z databáze nebo CSV před voláním `setExplosion`. |
| **Různá velikost grafu** | Změňte argumenty šířky/výšky v `insertChart(ChartType.PIE, width, height)`. |
| **Export do PDF** | Po uložení DOCX zavolejte `doc.save("output.pdf")` pro vytvoření PDF verze stejného grafu. |
| **Lokalizace** | Použijte `DocumentBuilder.insertChart` s formátem čísel specifickým pro locale pro popisky. |

### Pro tip
Vždy volejte `setHoleSize(0)` **po** `insertChart`. Pokud ji nastavíte před vložením, Aspose.Words se po vytvoření grafu vrátí k výchozí velikosti donut grafu.

## Shrnutí

Nyní víte, jak **vložit koláčový graf** do dokumentu Word pomocí Javy, jak **nastavit velikost díry** pro vzhled celého koláče, jak **explodovat výsek koláče** pro upoutání pozornosti a jak **zvýraznit výsek koláčového grafu** pomocí vlastních barev. Kompletní příklad také ukazuje, jak **vytvořit DOCX graf** soubory, které jsou připravené k distribuci.

## Další kroky

* Prozkoumejte další typy grafů (`BAR`, `LINE`, `SCATTER`) pomocí `ChartType`.  
* Kombinujte generování grafů s hromadnou korespondencí pro tvorbu personalizovaných zpráv.  
* Integrujte vygenerovaný DOCX do webové služby, která soubor vrací na požádání.  

Pokud narazíte na problémy, nezapomeňte ověřit, že používáte kompatibilní verzi Aspose.Words a že výstupní adresář existuje a je zapisovatelný.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Použití Word Chart API](/words/english/net/programming-with-charts/)
- [Vložení bublinového grafu do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}