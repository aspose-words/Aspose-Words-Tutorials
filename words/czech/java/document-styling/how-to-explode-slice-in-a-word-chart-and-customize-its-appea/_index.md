---
category: general
date: 2026-10-04
description: Naučte se, jak rozbalit výsek v grafu Wordu, rozbalit výsek koláčového
  grafu a změnit velikost prstencového grafu pomocí podrobného příkladu v Javě.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: cs
lastmod: 2026-10-04
og_description: Jak oddělit výseč v grafu Wordu a přizpůsobit koláčové nebo prstencové
  grafy pomocí Javy. Sledujte kompletní příklad, jak upravit graf ve Wordu.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Jak rozbalit výsek v grafu Word – kompletní Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Jak rozbalit výseč v grafu Wordu a přizpůsobit její vzhled
url: /cs/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak rozšířit výsek v grafu Wordu a přizpůsobit jeho vzhled

Pokud potřebujete **rozšířit výsek** v grafu Wordu, tento průvodce vám přesně ukáže, jak na to. Ať už připravujete prodejní prezentaci nebo finanční zprávu, rozšíření výseku koláčového grafu nebo úprava otvoru v prstenci může zvýraznit nejdůležitější data. V následujících sekcích se také naučíte, jak **upravit graf ve Wordu**, **rozšířit výsek koláčového grafu**, **změnit velikost prstencového grafu** a **přizpůsobit koláčový graf v dokumentech Word** pomocí Aspose.Words for Java.

Na konci tohoto tutoriálu budete mít kompletní, připravený Java program, který načte soubor `.docx`, rozšíří první výsek koláčového grafu, změní velikost otvoru v prstenci a výsledek uloží. Není potřeba žádných externích skriptů ani ruční úpravy.

## Požadavky

- Java 17 nebo novější nainstalovaný na vašem vývojovém počítači.  
- Maven 3.6+ (nebo Gradle) pro správu závislostí.  
- Knihovna Aspose.Words for Java (bezplatná zkušební verze funguje pro vývoj).  
- Dokument Word (`input.docx`), který obsahuje alespoň jeden graf (koláčový nebo prstencový).

## Krok 1: Přidejte Aspose.Words do svého projektu

Pokud používáte Maven, přidejte následující závislost do souboru `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Pro Gradle umístěte toto do souboru `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Tip:** Udržujte verzi knihovny aktuální; novější vydání přidávají podporu pro další typy grafů a zlepšují výkon.

## Krok 2: Načtěte dokument Word, který obsahuje graf

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Proč je to důležité:** Načtení dokumentu vytvoří v‑paměti reprezentaci, kterou může Aspose.Words procházet. Bez tohoto objektu nemůžete přistupovat k uzlům grafu.

## Krok 3: Získejte první graf v dokumentu

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Vysvětlení:** `NodeType.SHAPE` zahrnuje všechny kreslicí objekty, včetně grafů. Argument `true` říká Aspose, aby hledal rekurzivně, čímž zajistí, že první graf bude nalezen i když je vložený v tabulce.

## Krok 4: Rozšířit první výsek koláčového grafu

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Jak to funguje:** Metoda `setExplosion` přijímá číselnou hodnotu, která určuje, jak daleko se výsek posune od středu. Hodnota `20` je vizuálně patrná, aniž by narušila rozvržení grafu.

## Krok 5: Upravit velikost otvoru v prstenci pro prstencový graf

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Proč to pomáhá:** Větší otvor v prstenci může zlepšit čitelnost, když máte mnoho datových bodů. Metoda `setDoughnutHoleSize` očekává procento (0‑100).

## Krok 6: Uložit upravený dokument

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Očekávaný výstup

- První výsek prvního koláčového grafu je posunut ven, čímž vynikne.
- Pokud je graf prstencový, centrální otvor se rozšíří na 40 % poloměru grafu.
- Výsledný soubor `PieChart.docx` lze otevřít v Microsoft Word, LibreOffice nebo jakémkoli kompatibilním prohlížeči, zobrazující vizuální změny provedené programově.

## Kompletní, spustitelný příklad

Níže je celý program v jednom bloku. Zkopírujte jej do souboru `ChartExploder.java`, upravte cesty k souborům a spusťte jej pomocí `mvn compile exec:java` (nebo konfigurace spuštění ve vašem IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Spuštěním tohoto kódu **upravit graf ve Wordu**, **rozšíříte výsek koláčového grafu** a **změníte velikost prstencového grafu** automaticky.

## Časté otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| *Co když dokument obsahuje více grafů?* | Ukázka cílí na **první** graf (`NodeType.SHAPE, 0`). Pro práci s jinými grafy změňte index nebo iterujte přes `doc.getChildNodes(NodeType.SHAPE, true)` a filtrujte podle `shape.getChart() != null`. |
| *Mohu rozšířit výsek jiný než první?* | Ano. Přistupte k požadované sérii pomocí `chart.getSeries().get(seriesIndex)` a zavolejte `setExplosion(value)`. Indexy jsou nulové. |
| *Funguje to se soubory Word 2007‑2021?* | Aspose.Words podporuje `.doc`, `.docx`, `.dot` a `.dotx`. Stejný kód funguje napříč verzemi, protože knihovna abstrahuje formát souboru. |
| *Co když je graf sloupcový nebo čárový?* | `setExplosion` a `setDoughnutHoleSize` jsou použitelné pouze pro koláčové grafy. Kód bezpečně přeskočí tyto operace, pokud je typ grafu jiný. |
| *Potřebuji licenci pro Aspose.Words?* | Bezplatná evaluační licence odstraňuje 30‑denní limit, ale přidává vodoznak. Pro produkční použití zakupte licenci, která vodoznak odstraní a odemkne plnou funkčnost. |

## Závěr

Nyní víte, **jak rozšířit výsek** v grafu Wordu, **jak upravit graf ve Wordu** a **jak změnit velikost prstencového grafu** pomocí Aspose.Words for Java. Kompletní příklad ukazuje celý pracovní postup – od načtení dokumentu, nalezení grafu, aplikování vizuálních úprav až po uložení výsledku – takže můžete tyto kroky integrovat do jakéhokoli reportovacího nebo generovacího pipeline.

**Další kroky**

- Prozkoumejte další úpravy grafů, jako je změna barev, přidání popisků dat nebo přepnutí typu grafu (`chart.setChartType(ChartType.BAR_CLUSTERED)`).
- Kombinujte tuto logiku s Aspose.PDF pro vytvoření PDF verze stejné zprávy.
- Automatizujte proces pro dávku dokumentů pomocí smyčky přes soubory v adresáři.

Neváhejte experimentovat s různými hodnotami rozšíření nebo procenty otvoru v prstenci, aby odpovídaly vašim designovým směrnicím. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Skrýt osu grafu v dokumentu Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Vložit bublinový graf do dokumentu Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}