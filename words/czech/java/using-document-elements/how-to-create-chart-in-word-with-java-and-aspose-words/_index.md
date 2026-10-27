---
category: general
date: 2026-09-24
description: Naučte se, jak vytvořit graf ve Wordu pomocí Javy, vložit radiální graf
  a uložit dokument jako DOCX pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: cs
lastmod: 2026-09-24
og_description: Vytvořte graf ve Wordu pomocí Javy a Aspose.Words. Tento tutoriál
  vám ukáže, jak přidat radiální graf, přizpůsobit data a uložit dokument jako docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Vytvořte graf ve Wordu pomocí Javy – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Jak vytvořit graf ve Wordu pomocí Javy a Aspose.Words
url: /cs/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit graf ve Wordu pomocí Javy a Aspose.Words

Pokud potřebujete **create chart in Word** z Java aplikace, tento průvodce vás provede celým procesem. Uvidíte, jak přidat radiální graf, volitelně naplnit jeho řady a nakonec **save document as docx** pomocí knihovny Aspose.Words for Java.

Generování vizuálních dat uvnitř souboru Word je běžná potřeba pro reportování, fakturaci nebo automatizovanou tvorbu dokumentů. Na konci tohoto tutoriálu budete schopni **create word document java** projekty, které **add chart to Word** soubory bez jakékoli ruční úpravy.

## Požadavky

* Java Development Kit (JDK) 8 nebo novější.
* Maven nebo Gradle pro správu závislostí.
* IDE jako IntelliJ IDEA, Eclipse nebo VS Code.
* Platná licence Aspose.Words for Java (bezplatná zkušební verze funguje pro vývoj).

Tyto nástroje poskytují základ pro následující ukázky kódu.

## Krok 1: Nastavení Maven projektu

Vytvořte nový Maven projekt (nebo aktualizujte existující) a přidejte závislost Aspose.Words do vašeho `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Spuštěním `mvn clean install` se stáhne knihovna a třídy jako `Document`, `DocumentBuilder` a `ChartType` budou k dispozici na classpath.

> **Tip:** Udržujte verzi knihovny aktuální. Nová vydání přidávají typy grafů a zlepšují výkon vykreslování.

## Krok 2: Vytvoření nového Word dokumentu

Prvním programovým krokem k **create chart in Word** je vytvořit prázdný objekt `Document`. Tento objekt představuje celý balíček `.docx`.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funguje jako kurzor; zná aktuální vkládací bod a poskytuje metody pro text, tabulky a grafy. V tomto okamžiku máte **created word document java** styl – čisté plátno připravené pro obsah.

## Krok 3: Vložení radiálního grafu

Aspose.Words podporuje mnoho typů grafů. Pro **insert radial chart** zavolejte `insertChart` s `ChartType.RADIAL`. Metoda také vyžaduje šířku a výšku v bodech (1 bod ≈ 1/72 palce).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

Vrácený objekt `Shape` obsahuje podkladový objekt grafu. Graf automaticky vykresluje stupnice pro rozložení 24,9°, což je výchozí nastavení pro radiální grafy ve Wordu.

### Proč použít radiální graf?

Radiální graf vizualizuje data, která se obalují kolem kruhu, což ho činí ideálním pro zobrazování cyklických vzorců (např. měsíční prodeje, metriky ve tvaru ciferníku). Stejná API může vložit sloupcové, koláčové nebo čárové grafy, ale radiální typ přidává charakteristický vzhled bez dalšího kódu pro stylování.

## Krok 4: (Volitelné) Naplnění dat řad grafu

Pokud chcete, aby graf zobrazoval skutečné hodnoty, musíte přidat řady a body. Následující úryvek přidává jednu řadu se třemi datovými body:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Můžete opakovat volání `add` pro libovolný počet bodů. Aspose.Words automaticky aktualizuje vizuální reprezentaci, takže vidíte, jak se radiální výseče přizpůsobují novým hodnotám.

> **Často kladená otázka:** *Co když potřebuji svázat data z databáze?*  
> Získejte řádky, projděte je ve smyčce a uvnitř smyčky zavolejte `series.getDataPoints().add(value, label)`. API je bezpečné pro více vláken a funguje s jakýmkoli `ResultSet`, který poskytnete.

## Krok 5: Uložení dokumentu jako DOCX

Když je graf připraven, posledním krokem je **save document as docx**. Metoda `save` určuje výstupní formát podle přípony souboru.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Vygenerovaný soubor obsahuje plně funkční radiální graf, který lze otevřít v Microsoft Word, LibreOffice nebo jakémkoli prohlížeči podporujícím formát DOCX. Protože jsme použili příponu `.docx`, Word uloží soubor ve formátu Open XML, což je moderní standard pro Word dokumenty.

### Ověření výsledku

Otevřete `RadialChartDemo.docx` ve Wordu:

1. Měli byste vidět jednu stránku se středěným radiálním grafem.
2. Pokud jste přidali data řad, graf zobrazí čtyři výseče označené Q1‑Q4.
3. Klikněte pravým tlačítkem na graf → **Edit Data** pro potvrzení podkladové datové tabulky.

Pokud se graf zobrazí prázdný, dvakrát zkontrolujte, že jste zavolali `chart.getChart()` před přidáním řad, a ujistěte se, že kurzor dokumentového builderu je umístěn tam, kde chcete graf.

## Krok 6: Pokročilé tipy pro práci s grafy

| Tip | Proč je to důležité |
|-----|---------------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Zlepšuje vizuální konzistenci bez ručního formátování každého prvku. |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | Umožňuje jemně doladit velikost grafu podle rozvržení stránky. |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | Poskytuje kontext čtenářům, kteří prohlížejí dokument bez okolního textu. |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | Užitečné, když potřebujete needitovatelnou verzi pro distribuci. |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Zabraňuje vodotisku z evaluační verze v produkčních sestaveních. |

Tyto vylepšení jsou volitelná, ale ukazují, jak můžete dále přizpůsobit graf poté, co se naučíte **add chart to Word**.

## Závěr

Nyní máte kompletní, samostatný příklad, který ukazuje, jak **create chart in Word** pomocí Javy, **insert radial chart**, volitelně jej naplnit daty a **save document as docx**. Stejný vzor funguje i pro jiné typy grafů, takže můžete tento tutoriál rozšířit na sloupcové, čárové nebo koláčové grafy podle potřeby.

Dále můžete zkoumat:

* **create word document java** projekty, které kombinují tabulky, obrázky a více grafů.
* Použití **save document as docx** spolu s **save document as pdf** pro vícero formátové reportování.
* Přidávání dynamických dat z REST API nebo databází do vašich grafů.

Neváhejte experimentovat s možnostmi stylování, rozměry grafu a zdroji dat. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Vytvoření prázdného Word dokumentu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Vytvoření Word dokumentu v Javě – Přidání obdélníkového tvaru se stínovým efektem](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}