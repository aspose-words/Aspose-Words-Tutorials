---
category: general
date: 2026-09-11
description: Uložte dokument Word po úpravě prstencového grafu pomocí Aspose.Words
  pro Java. Naučte se, jak změnit velikost díry v prstenci, otočit prstencový graf
  a upravit vlastnosti prstencového grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: cs
lastmod: 2026-09-11
og_description: Uložte dokument Word po úpravě prstencového grafu pomocí Aspose.Words
  pro Java. Tento tutoriál ukazuje, jak změnit velikost díry v prstencovém grafu,
  otočit prstencový graf a přizpůsobit vzhled grafu.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Uložte dokument Word po úpravě prstencového grafu – Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Uložit dokument Word po úpravě prstencového grafu v Javě
url: /cs/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uložení dokumentu Word po úpravě prstencového grafu v Javě

Pokud potřebujete **uložit dokument Word**, který obsahuje přizpůsobený prstencový graf, tento návod vám přesně ukáže, jak na to. Pouhých několik řádků Javy vám umožní změnit velikost díry v prstenci, otočit prstencový graf a poté výsledek zapsat zpět na disk.

Uvidíte kompletní, spustitelný příklad, který používá Aspose.Words for Java, plus tipy pro práci s více grafy, ověřování typů uzlů a vyhýbání se běžným úskalím. Žádné externí odkazy nejsou potřeba — vše, co potřebujete, je zahrnuto.

## Požadavky

- Java 17 nebo novější nainstalována
- Maven nebo Gradle pro správu závislostí
- Aspose.Words for Java (verze 23.9 nebo novější) přidána do vašeho projektu  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Soubor Word (`input.docx`) obsahující jediný prstencový graf

## Krok 1: Načtení dokumentu Word

Prvním krokem je otevřít zdrojový soubor. Tento krok je nezbytný, protože každá následná operace pracuje s objektem `Document` v paměti.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Proč?** Načtení dokumentu vytvoří DOM reprezentaci, která vám umožní procházet tvary, tabulky a grafy. Pokud soubor nelze otevřít, Aspose.Words vyhodí výjimku, takže okamžitě zjistíte, že cesta je špatná.

## Krok 2: Najděte tvar prstencového grafu

Graf je uložen uvnitř uzlu `Shape`. Získáme první tvar, který obsahuje graf, a přetypujeme jeho renderer na `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Proč?** Kontrola `isChart()` zabraňuje `ClassCastException`, pokud dokument obsahuje obrázky nebo jiné tvary před grafem. To činí kód odolným vůči dokumentům s různorodým obsahem.

## Krok 3: Změna velikosti díry v prstenci  

Nyní upravíme díru v prstenci. Metoda `setHoleSize` očekává procento poloměru grafu (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Proč?** Změna díry v prstenci (`change doughnut hole` / `change chart hole size`) vám umožní zdůraznit nebo zmenšit centrální oblast. Hodnoty mimo 10‑90 % jsou API ignorovány.

## Krok 4: Otočení prstencového grafu  

Pro nastavení, kde začíná první výsek, nastavte úhel prvního výseku. Tím se efektivně **otočí prstencový graf**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Proč?** Otočení grafu je užitečné, když chcete, aby konkrétní výsek byl nahoře nebo aby odpovídal designové specifikaci.

## Krok 5: Uložení aktualizovaného dokumentu  

Nakonec zapíšete změny zpět do nového souboru. Toto je okamžik, kdy **uložíte dokument Word** s upraveným grafem.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Očekávaný výsledek:** `output.docx` obsahuje původní obsah, ale prstencový graf nyní má 30 % díru a jeho první výsek začíná při 45 °. Otevření souboru v Microsoft Word zobrazí transformovaný graf.

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkopírovat a vložit do svého IDE. Obsahuje všechny importy a ošetření chyb potřebné k bezpečnému **úpravě prstencového grafu** a **uložení dokumentu Word**.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Očekávaný výstup

Když otevřete `output.docx`:

- Středová díra prstencového grafu zabírá přibližně jednu třetinu poloměru grafu.  
- První výsek začíná při 45‑stupňové pozici, posunuje celý graf po směru hodinových ručiček.  
- Obě vizuální změny jsou okamžitě viditelné ve Wordu.

## Běžné varianty a okrajové případy

| Situace | Jak řešit |
|-----------|----------------|
| **Více grafů** | Iterujte přes `doc.getChildNodes(NodeType.SHAPE, true)` a filtrujte `shape.isChart()`; použijte `setHoleSize` / `setFirstSliceAngle` na každý `Chart`. |
| **Graf není prstencový** | Zkontrolujte `chart.getType()`; volajte `setHoleSize` pouze když `chart.getType() == ChartType.DOUGHNUT`. |
| **Potřeba dynamicky měnit velikost díry** | Vypočítejte požadované procento na základě datových hodnot a poté zavolejte `setHoleSize(computedValue)`. |
| **Ukládání do proudu** | Použijte |

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Jak uložit dokument jako PDF pomocí Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Uložit Word s heslem pomocí Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}