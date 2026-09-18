---
category: general
date: 2026-09-18
description: Naučte se vytvořit dokument Word a vložit koláčový graf pomocí Aspose.Words
  pro Javu. Zahrnuje otáčení koláčového grafu a kroky pro generování souboru Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: cs
lastmod: 2026-09-18
og_description: Vytvořte dokument Word a vložte koláčový graf pomocí Javy. Postupujte
  podle tohoto návodu, jak otočit koláčový graf, rozdělit výseče a vygenerovat soubor
  Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Vytvořte dokument Word s koláčovým grafem – krok za krokem průvodce v Javě
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Jak vytvořit dokument Word s koláčovým grafem v Javě
url: /cs/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit dokument Word s koláčovým grafem v Javě

Pokud potřebujete **vytvořit dokument Word**, který vizualizuje data, tento návod vám ukáže, jak to provést pomocí Aspose.Words for Java. Naučíte se vložit koláčový graf, „explodovat“ výsek, otočit graf a nakonec **vygenerovat soubor Word**, který můžete otevřít v Microsoft Word.

Vytváření zpráv, které kombinují text a grafy, nevyžaduje samostatný grafický nástroj. Na konci tohoto tutoriálu budete mít kompletní, spustitelný program, který vytvoří soubor .docx obsahující plně nakonfigurovaný koláčový graf.

## Předpoklady

- Java 17 nebo novější (kód se také kompiluje s Java 8+)
- Maven nebo Gradle pro správu závislostí
- Licence Aspose.Words for Java (bezplatná zkušební verze funguje pro tento příklad)
- Základní znalost syntaxe Javy

## Krok 1: Nastavení Maven projektu

Vytvořte nový Maven projekt a přidejte závislost Aspose.Words do souboru `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Tip:** Udržujte číslo verze aktuální; novější vydání přidávají vylepšení typů grafů a opravy chyb.

## Krok 2: Vytvoření nového dokumentu Word

První operací, když **vytváříte dokument Word** programově, je vytvořit objekt `Document`. Tento objekt představuje celý soubor .docx v paměti.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

Třída `Document` je vstupním bodem pro všechny funkce zpracování Wordu. V tomto okamžiku se žádný soubor neukládá na disk; vše probíhá v RAM, dokud nevyvoláte `save`.

## Krok 3: Jak vložit koláčový graf

`DocumentBuilder` vám umožňuje přidávat obsah do dokumentu. Pomocí `insertChart` můžete **vložit koláčový graf** přímo.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` říká Aspose.Words, aby vytvořil koláčový graf. Rozměry jsou vyjádřeny v bodech (1 pt ≈ 1/72 palce). Po tomto volání se graf objeví v novém odstavci.

## Krok 4: Naplnění grafu daty

Koláčový graf potřebuje sérii hodnot. Zde přidáváme tři kategorie: „Apples“, „Bananas“ a „Cherries“.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Metoda `add` vytváří sérii a automaticky vytváří položky legendy. Tento vzor můžete znovu použít pro jakýkoli číselný dataset.

## Krok 5: Zvýraznění první výseky

„Explodování“ výseky přitahuje pozornost k určité hodnotě. První výsek (index 0) je „explodován“ o 20 bodů.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Nastavení `explode` na sérii ovlivňuje celý graf, takže pouze první datový bod je posunut.

## Krok 6: Jak otočit koláčový graf

Otočení grafu zlepšuje vizuální rovnováhu, zejména když největší výsek není nahoře. Metoda `setRotationAngle` očekává úhly ve stupních.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Otočení o 45° posune počáteční úhel po směru hodinových ručiček, což usnadňuje čtení grafu v mnoha rozvrženích.

## Krok 7: Uložení dokumentu a vygenerování souboru Word

Nakonec zapíšete dokument na disk. Tento krok **vygeneruje soubor Word**, který lze otevřít v Microsoft Word, LibreOffice nebo v jakémkoli kompatibilním prohlížeči.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Metoda `save` automaticky rozpozná příponu .docx a zapíše Word‑kompatibilní balíček. Složka `output` musí existovat, nebo ji můžete vytvořit programově.

### Očekávaný výstup

Po spuštění programu otevřete `output/PieChart.docx`. Měli byste vidět:

- Jednu stránku obsahující koláčový graf o rozměrech 400 × 300 pt.
- Výsek „Apples“ „explodovaný“ ven o 20 pt.
- Celý graf otočený o 45° po směru hodinových ručiček.
- Legendu odpovídající třem kategoriím ovoce.

## Běžné varianty a okrajové případy

### Vkládání více grafů

Pokud potřebujete více než jeden graf, zavolejte `builder.insertChart` znovu po přesunutí kurzoru:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Změna barev grafu

Barvy výsek můžete přizpůsobit pomocí kolekce `getPoints()` ze série:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Práce s velkými datovými sadami

Pro datové sady s více než 10 výseky zvažte použití prstencového grafu (`ChartType.DOUGHNUT`), aby byl vizuál přehledný.

## Závěr

Nyní víte, jak **vytvořit dokument Word**, **vložit koláčový graf**, **otočit koláčový graf** a **vygenerovat soubor Word** pomocí Aspose.Words for Java. Kompletní řešení ukazuje celý pracovní postup od inicializace dokumentu až po finální výstup souboru, pokrývající jak „jak“, tak „proč“ každého kroku.

Dále prozkoumejte související témata, jako je **vytvoření dat pro koláčový graf** z databáze, přidání popisků dat nebo export grafu jako obrázku. Experimentujte s různými typy grafů (sloupcový, čárový, prstencový), abyste rozšířili svou sadu nástrojů pro automatizaci Wordu.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}