---
category: general
date: 2026-11-15
description: Naučte se, jak vytvořit koláčový graf ve Word dokumentu a uložit soubor
  DOCX jako PDF pomocí Javy. Tento průvodce také zahrnuje převod Wordu na PDF a jak
  přidat graf.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: cs
lastmod: 2026-11-15
og_description: Vytvořte koláčový graf ve Wordu a uložte soubor DOCX jako PDF pomocí
  Javy. Postupujte podle tohoto krok‑za‑krokem návodu, jak převést Word na PDF a přidat
  grafy.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Vytvořte koláčový graf ve Wordu a uložte docx jako PDF – Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Jak vytvořit koláčový graf ve Wordu a uložit soubor docx jako PDF
url: /cs/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit koláčový graf ve Wordu a uložit docx jako PDF

Pokud potřebujete **create pie chart** uvnitř dokumentu Word a následně **save docx as PDF**, tento tutoriál vám přesně ukáže, jak na to. Uvidíte kompletní, spustitelný příklad, který převádí soubor .docx na PDF a zároveň do něj vkládá koláčový graf, takže můžete odpovědět na otázku „how to add chart“ bez hledání roztroušených útržků kódu.

V tomto průvodci se naučíte:

* Načíst existující *.docx* (nebo začít od nuly)  
* Použít Aspose.Words pro Java k **create pie chart** a naplnit data  
* **Save docx as PDF** s grafem správně vykresleným  
* Pochopit nuance **convert word to pdf**, když jsou v dokumentu grafy  

Postupy fungují s Aspose.Words 2024‑x.x a Java 17, ale koncepty platí pro jakoukoli knihovnu podporující manipulaci s grafy ve Wordu.

## Požadavky

Než začnete, ujistěte se, že máte:

| Požadavek | Proč je to důležité |
|-------------|----------------|
| Java 17 (nebo novější) | Vyžadováno nejnovějším JAR souborem Aspose.Words |
| Maven nebo Gradle build tool | Zjednodušuje správu závislostí |
| Aspose.Words for Java (nejnovější verze) | Poskytuje `Document`, `Chart` a `ChartType` třídy |
| Vstupní **.docx** soubor (nebo prázdný dokument) | Graf bude do tohoto souboru vložen |

Přidejte závislost Aspose.Words do svého `pom.xml` (Maven) nebo `build.gradle` (Gradle). Příklad pro Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Krok 1: Načíst dokument Word (nebo vytvořit nový)

Prvním krokem je získat instanci `Document`. Pokud již máte šablonu, předáte její cestu; jinak vytvoříte prázdný dokument.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Proč tento krok?* Objekt `Document` je kontejner pro veškerý obsah Wordu, včetně grafů. Načtením existujícího souboru si zachováte okolní text a styly a můžete přidat nový vizuální prvek.

## Krok 2: **Create pie chart** – jádro “how to create chart”

Nyní vytvoříme objekt `Chart` s typem `ChartType.PIE`. Tím se automaticky vytvoří zástupný koláčový graf, který můžete později naplnit daty.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Vysvětlení*: `ChartType.PIE` říká Aspose.Words, aby použil šablonu koláčového grafu. Graf je přidán do těla dokumentu, takže se objeví tam, kde ho potřebujete. Tím se jedním voláním splní požadavek “how to add chart”.

## Krok 3: Vyplnit graf – odpověď na “how to add chart” pomocí dat

Koláčový graf je bez datové řady bezvýznamný. Použijte kolekci `Series` k přidání kategorií a hodnot.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Proč je to důležité*: Každé volání `add` vytvoří výseč koláče. První argument je popisek, druhý číselná hodnota. Můžete je nahradit dynamickými daty z databáze nebo CSV souboru.

### Volitelné: Přizpůsobit vzhled (není povinné, ale užitečné)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Tyto úpravy ukazují, jak můžete **how to create chart** s profesionálním vzhledem, aniž byste opustili Java kód.

## Krok 4: **Save docx as PDF** – závěrečná část “convert word to pdf”

Jakmile je graf vložen, exportujte dokument do PDF. Aspose.Words vykreslí graf jako vektorovou grafiku a zachová kvalitu.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Klíčový bod*: Metoda `save` automaticky převádí soubor Word do PDF, řeší rasterizaci grafu, vkládání fontů a rozvržení stránek. Tím se splní cíl **save docx as pdf** a ukazuje spolehlivý způsob **convert word to pdf**, když jsou v dokumentu grafy přítomny.

### Očekávaný výstup

Spuštěním programu vznikne `output.pdf`, který obsahuje:

* Původní obsah `input.docx` (pokud existuje)  
* Plně vykreslený koláčový graf s názvem *Sales Distribution Q1*  
* Přesné procentuální podíly výsečů odpovídající datům (40 %, 30 %, 30 %)

Otevřete PDF v libovolném prohlížeči a měli byste vidět ostrý koláčový graf, identický s tím ve Wordu.

## Časté problémy a jak se jim vyhnout

| Problém | Příčina | Řešení |
|-------|-------|-----|
| Graf se v PDF zobrazuje prázdně | Chybějící nastavení fontu nebo vykreslování grafu | Ujistěte se, že používáte nejnovější verzi Aspose.Words; obsahuje potřebné vykreslovací knihovny. |
| Hodnoty jsou zaokrouhleny nesprávně | Použití celočíselných hodnot s velkými čísly | Poskytněte `double` hodnoty nebo před přidáním do řady čísla škálujte. |
| Výstupní PDF je obrovské | Obrázky vložené s vysokým DPI | Nastavte `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)`, pokud také vkládáte obrázky. |
| “convert word to pdf” vyhazuje `UnsupportedOperationException` | Použití starší verze Javy (< 11) | Upgradujte na Java 17 nebo novější, kterou vyžaduje Aspose.Words 24.x. |

## Tip: Znovu‑použít logiku vytváření grafu

Pokud potřebujete do stejného dokumentu přidat více grafů, vytáhněte kód pro tvorbu grafu do pomocné metody:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Nyní můžete volat `doc.getFirstSection().getBody().appendChild(createPieChart(...));` pro každý datový soubor a udržet svůj kód DRY (Don’t Repeat Yourself).

## Závěr

Nyní víte, jak **create pie chart** uvnitř dokumentu Word, naplnit jej daty a **save docx as PDF** pomocí Javy. Tento end‑to‑end příklad pokrývá celý workflow **convert word to pdf**, odpovídá na **how to add chart** a demonstruje **how to create chart** programově.  

Od semene můžete dále zkoumat:

* Přidání sloupcových nebo čárových grafů (`ChartType.BAR`, `ChartType.LINE`) – další scénář **how to create chart**.  
* Export do dalších formátů, jako PNG nebo HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Dynamické generování vstupního dokumentu s tabulkami nebo zástupnými znaky před vložením grafů.

Neváhejte experimentovat s různými datovými sadami, možnostmi stylování nebo dokonce vložit více grafů na stránku. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Jak vložit koláčový graf do dokumentu Word pomocí Javy](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Jak uložit Word jako PDF a vytvořit přístupný PDF v Javě](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Jak vytvořit graf ve Wordu s Javou a Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}