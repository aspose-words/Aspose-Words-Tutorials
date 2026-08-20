---
category: general
date: 2026-08-20
description: Rychle přidejte vodící čáry do koláčového grafu v Javě. Naučte se vkládat,
  rozbalovat, přebarvovat a označovat výseče pomocí Chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: cs
lastmod: 2026-08-20
og_description: Přidejte vodící čáry do koláčového grafu v Javě pomocí stručného příkladu.
  Řiďte se tímto návodem, jak vložit, roztrhnout, přebarvit a popsat výseky pomocí
  Chart API.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Přidejte vodící čáry do koláčového grafu v Javě – krok za krokem průvodce
  Chart API
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Jak přidat vodící čáry do koláčového grafu v Javě pomocí Chart API
url: /cs/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat vodící čáry do koláčového grafu v Javě pomocí Chart API

Pokud potřebujete **přidat vodící čáry do koláčového grafu** v Javě, tento návod vás provede celým procesem. Uvidíte, jak vložit koláčový graf, „explodovat“ výsek pro zdůraznění, změnit jeho barvu a nakonec povolit vodící čáry, které označují explodovaný segment.

Příklad používá standardní Chart API, které se nachází v mnoha Java knihovnách pro reportování. Není potřeba žádné externí nástroje a kód běží v jakémkoli prostředí JDK 8+.

## Co dosáhnete

Na konci tohoto tutoriálu budete schopni:

* Vytvořit `Chart` typu `ChartType.PIE` s vlastní velikostí.  
* „Explodovat“ první výsek, aby upoutal pozornost.  
* Nastavit barvu sektoru explodovaného výseku na modrou.  
* **Přidat vodící čáry do koláčového grafu**, aby byl popisek výseku jasně spojen.

Měli byste již mít Java projekt s knihovnou Chart na classpathu. Pokud používáte Maven, přidejte závislost uvedenou v sekci Požadavky.

## Požadavky

* Nainstalovaný JDK 8 nebo novější.  
* Knihovna Chart (např. `com.example.chart:chart-api:2.5.0`).  
* Základní znalost Java tříd a volání metod.

---

## Jak přidat vodící čáry do koláčového grafu

Níže je kompletní spustitelný program, který demonstruje každý krok. Kód je úmyslně samostatný, takže jej můžete zkopírovat, vložit a spustit bez úprav.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Vysvětlení jednotlivých kroků

| Krok | Co kód dělá | Proč je to důležité |
|------|-------------|---------------------|
| **1️⃣ Vložení koláčového grafu** | `builder.insertChart(ChartType.PIE, 400, 300)` vytvoří 400 × 300 pixelový koláčový graf. | Vytvoří kontejner grafu a určuje jeho rozměry, které ovlivňují umístění popisků a délku vodících čar. |
| **2️⃣ Explodovat první výsek** | `setExplosion(20)` posune výsek o 20 % poloměru. | Explodovaný výsek upoutá pozornost diváka a učiní vodící čáru viditelnou. |
| **3️⃣ Nastavit barvu sektoru** | `setSectorColor(Color.BLUE)` změní výplň výseku na modrou. | Kontrast barev zlepšuje čitelnost, zejména když je výsek zvýrazněn. |
| **4️⃣ Povolit vodící čáry** | `setLeaderLines(true)` zapne spojovací čáry, které propojují výsek s jeho popiskem. | Vodící čáry zajišťují, že popisek zůstane čitelný i když je výsek posunut ven. |

Volání `saveAsPng` je volitelné, ale užitečné pro ověření vizuálního výsledku. Po spuštění programu byste měli vidět obrázek podobný tomu níže.

![Přidat vodící čáry do koláčového grafu](https://example.com/assets/pie-leader-lines.png "Přidat vodící čáry do koláčového grafu – explodovaný výsek s modrou barvou a vodícími čarami")

*Obrázek: Koláčový graf, kde je první výsek explodovaný, zbarvený modře a spojený s popiskem vodící čárou.*

## Přizpůsobení vodících čar (pokročilé)

Základní volání `setLeaderLines(true)` používá výchozí styl knihovny. Můžete dále řídit vzhled:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Tyto možnosti jsou užitečné, když potřebujete sladit s firemní identitou nebo zlepšit přístupnost.

### Zpracování více sérií

Pokud váš koláčový graf obsahuje více než jednu sérii, můžete chtít vodící čáry jen pro konkrétní výsek. Použijte index série k cílení na správný prvek:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Když výsek není explodován, vodící čára je obvykle automaticky skryta, ale můžete ji vynutit pomocí `setLeaderLineEnabled(true)`.

## Časté úskalí a jak se jim vyhnout

| Problém | Příznak | Řešení |
|--------|---------|--------|
| **Vodící čáry nejsou viditelné** | Graf se vykreslí bez spojovacích čar. | Ujistěte se, že je výsek explodován (`setExplosion` > 0) nebo explicitně povolte vodící čáry na výseku. |
| **Překrývající se popisky** | Popisky se navzájem překrývají. | Zvětšete velikost grafu nebo nastavte `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Barva se nepoužije** | Výsek zůstává ve výchozí barvě. | Ověřte, že cílíte na správný index série (`getSeries().get(0)`). |
| **Obrázek se neuloží** | `saveAsPng` vyhodí výjimku. | Zkontrolujte oprávnění k zápisu do výstupního adresáře a že knihovna podporuje export do PNG. |

## Úplný výpis zdrojového kódu

Pro pohodlí zde znovu uvádíme kompletní soubor zdrojového kódu, včetně importů a komentářů:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Spuštěním tohoto programu se vygeneruje `pie-with-leader-lines.png`, který zobrazuje koláčový graf s explodovaným modrým výsekem a jasnými vodícími čarami ukazujícími na popisek výseku.

## Závěr

Nyní víte, jak **přidat vodící čáry do koláčového grafu** v Javě pomocí Chart API. Proces spočívá ve vložení `ChartType.PIE`, explodování požadovaného výseku, úpravě jeho barvy a povolení vodících čar. S volitelnými možnostmi stylování můžete doladit barvu čáry, tloušťku a umístění popisků tak, aby vyhovovaly jakýmkoli vizuálním požadavkům.

Dále zvažte prozkoumání souvisejících témat, jako jsou **pie chart explosion Java**, **set sector color Chart API** a **builder.insertChart usage**, abyste vytvořili pokročilejší vizualizace, jako jsou donut grafy, vrstvené koláče nebo interaktivní dashboardy.

Klidně experimentujte s různými indexy výseků, barvami a styly vodících čar – vaše grafy budou s každým vylepšením informativnější a vizuálně atraktivnější. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Přidat hodnoty data a času na osu grafu](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Vložit sloupcový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}