---
category: general
date: 2026-09-27
description: Vytvořte radiální graf v Javě a vložte graf do Wordu. Naučte se, jak
  nastavit velikost grafu, přidat datové řady a vygenerovat prázdný dokument Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: cs
lastmod: 2026-09-27
og_description: Vytvořte radiální graf v Javě a poté jej vložte do Wordu. Tento návod
  ukazuje, jak nastavit velikost grafu, přidat datové řady a vytvořit prázdný dokument
  Word.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Vytvořte radiální graf a vložte graf do Wordu pomocí Javy
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Vytvořte radiální graf a vložte graf do Wordu pomocí Javy
url: /cs/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření radiálního grafu a vložení grafu do Wordu pomocí Javy

Pokud potřebujete **vytvořit radiální graf** v souboru Word pomocí Javy, tento tutoriál vám přesně ukáže, jak na to. Uvidíte, jak **vložit graf do Wordu**, nastavit rozměry grafu a vytvořit **prázdný dokument Word** od nuly.

Provedeme vás všemi potřebnými kroky, od inicializace dokumentu po přidání datové řady a uložení finálního `.docx`. Na konci budete mít plně funkční soubor Word obsahující radiální graf a budete rozumět **jak nastavit velikost grafu** a **přidat datovou řadu do grafu** pro budoucí úpravy.

## Požadavky

* Java 17 nebo novější (kód se kompiluje s libovolným moderním JDK)
* Aspose.Words pro Java 24.9 nebo novější – metoda `setShowGraduations` je k dispozici až od této verze
* IDE nebo nástroj pro sestavení (Maven/Gradle), který může zahrnout JAR Aspose.Words
* Základní znalost syntaxe Javy a správy závislostí v Maven/Gradle

> **Tip:** Pokud používáte Maven, přidejte následující do svého `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Krok 1: Vytvořit prázdný dokument Word

Prázdný dokument je plátno, na které bude graf umístěn. Třída `Document` představuje celý soubor `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Vytvoření prázdného dokumentu zajišťuje, že žádný předchozí obsah nezasahuje do rozvržení grafu.

## Krok 2: Inicializovat DocumentBuilder

`DocumentBuilder` poskytuje pohodlné metody pro vkládání objektů, textu a dalších prvků do dokumentu.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder bude později použit k **vložit graf do Wordu**.

## Krok 3: Vytvořit radiální graf

Aspose.Words podporuje mnoho typů grafů; `ChartType.RADIAL` vytváří radiální (polární) graf.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

V tomto okamžiku graf existuje, ale nemá žádná data, velikost ani vizuální možnosti.

## Krok 4: Přidat datovou řadu do grafu

Graf bez datové řady je prázdný. Metoda `add` přijímá název řady a pole hodnot.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Můžete přidat více řad voláním `add` opakovaně. Tím se splňuje požadavek **add data series chart**.

## Krok 5: Povolit mřížky (volitelné)

Mřížky jsou radiální čáry, které zlepšují čitelnost. Jsou k dispozici až od verze 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Pokud používáte starší verzi Aspose.Words, tento řádek vyvolá výjimku – proto nejprve ověřte verzi knihovny.

## Krok 6: Nastavit rozměry grafu

Řízení velikosti grafu vám umožní jej dobře umístit do okrajů stránky. To řeší **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Můžete upravit hodnoty šířky a výšky tak, aby odpovídaly potřebám rozvržení. Pamatujte, že 1 bod ≈ 1/72 palce.

## Krok 7: Vložit graf do dokumentu Word

Nyní je graf připraven k umístění. Metoda `insertChart` třídy `DocumentBuilder` provádí vložení.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Toto je jádro operace **insert chart into word**.

## Krok 8: Uložit dokument

Nakonec zapíšete dokument na disk. Soubor bude obsahovat radiální graf, který jste právě vytvořili.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Spuštěním programu se v pracovním adresáři projektu vytvoří `RadialChart.docx`. Otevřením souboru v Microsoft Word se zobrazí radiální graf se třemi datovými body a viditelnými mřížkami.

### Očekávaný výstup

* Word soubor pojmenovaný `RadialChart.docx`
* V souboru jedna stránka obsahující radiální graf o rozměrech 400 × 300 bodů
* Graf zobrazuje jednu řadu s názvem **Series 1** a hodnotami **10, 20, 30**
* Mřížky (radiální čáry) jsou kolem grafu viditelné

## Běžné varianty a okrajové případy

| Situace | Co změnit | Důvod |
|-----------|----------------|--------|
| **Více řad** | Zavolejte `chart.getSeries().add(...)` pro každou řadu | Umožňuje srovnávací vizualizaci dat |
| **Jiný typ grafu** | Nahraďte `ChartType.RADIAL` za `ChartType.COLUMN` (nebo jiný) | Použijte typ grafu, který nejlépe reprezentuje vaše data |
| **Vlastní barvy** | Přistupte k `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Zlepšuje vizuální identitu |
| **Starší verze Aspose.Words** | Vynechejte řádek `setShowGraduations` nebo aktualizujte knihovnu | Zabraňuje `NoSuchMethodError` |
| **Ukládání do jiného formátu** | Použijte `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Vytvoří PDF místo DOCX |

## Kompletní spustitelný příklad

Níže je kompletní, samostatný Java program. Zkopírujte jej do souboru pojmenovaného `RadialChartExample.java`, přidejte závislost Aspose.Words a spusťte jej.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Závěr

Nyní víte, jak programově **vytvořit radiální graf**, **přidat datovou řadu do grafu**, řídit **how to set chart size** a **vložit graf do Wordu**, přičemž začínáte s **prázdným dokumentem Word**. Příklad používá Aspose.Words pro Java 24.9, ale stejné koncepty platí i pro jiné knihovny grafů, které poskytují podobné API.

### Další kroky

* Prozkoumejte další typy grafů (`ChartType.PIE`, `ChartType.LINE`, atd.) – to se vztahuje k sekundárnímu klíčovému slovu **insert chart into word**.
* Přizpůsobte popisky os, legendy a barvy tak, aby odpovídaly vašim firemním směrnicím.
* Generujte grafy dynamicky z databázových dotazů nebo CSV souborů.
* Převádějte výsledný `.docx` do PDF pro distribuci (`doc.save("output.pdf", SaveFormat.PDF)`).

Neváhejte experimentovat s rozměry, daty řad a možnostmi stylování, abyste vytvořili přesně ten vizuál, který potřebujete. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar se stínovým efektem](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vložit plošný graf do Word dokumentu](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}