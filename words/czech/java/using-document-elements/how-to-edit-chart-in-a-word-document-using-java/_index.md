---
category: general
date: 2026-09-11
description: Jak upravit graf v dokumentu Word pomocí Javy – naučte se aktualizovat
  nastavení grafu, povolit mřížku grafu, změnit možnosti grafu a uložit aktualizovaný
  dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: cs
lastmod: 2026-09-11
og_description: Jak upravit graf v dokumentu Word pomocí Javy. Postupujte podle tohoto
  návodu a aktualizujte nastavení grafu, povolte mřížku grafu, změňte možnosti grafu
  a uložte aktualizovaný dokument.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Jak upravit graf v dokumentu Word pomocí Javy – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Jak upravit graf v dokumentu Word pomocí Javy
url: /cs/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak upravit graf v dokumentu Word pomocí Javy

Pokud potřebujete **jak upravit graf** v souboru Word, tento průvodce vám ukáže přesné kroky. Naučíte se, jak aktualizovat nastavení grafu, povolit mřížky grafu, změnit možnosti grafu a nakonec **uložit aktualizovaný dokument** bez ztráty formátování.

Práce s grafy programově se často připadá jako operace s černou skříní, zejména když chcete doladit vizuální detaily, jako jsou stupnice nebo mřížky. Tento tutoriál pokrývá vše, co potřebujete vědět, od načtení dokumentu po uložení změn. Není potřeba žádných externích nástrojů – stačí knihovna Aspose.Words pro Java (verze 24.9 nebo novější).

Na konci tohoto článku budete schopni:

* Načíst soubor `.docx`, který obsahuje graf.
* Najít tvar grafu a upravit jeho vlastnosti.
* Povolit mřížky grafu (stupnice) a upravit další možnosti.
* **Uložit aktualizovaný dokument** do nového souboru.

## Požadavky

* Java 17 nebo novější nainstalovaný na vašem počítači.  
* Maven nebo Gradle pro správu závislostí.  
* Aspose.Words pro Java 24.9+ (verze, která zavedla `setShowGraduations`).  
* Dokument Word (`input.docx`), který již obsahuje alespoň jeden graf.

Pokud nejste obeznámeni s Aspose.Words, představte si ji jako plnohodnotné API, které vám umožňuje číst, upravovat a zapisovat dokumenty Word programově – podobně jako manipulujete s DOM v webovém prohlížeči.

## Krok 1: Nastavte projekt a importujte knihovnu

Vytvořte nový Maven projekt nebo přidejte závislost do existujícího projektu:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Tip:** Použijte nejnovější stabilní verzi, abyste měli k dispozici metodu `setShowGraduations`. Starší verze se nebudou kompilovat.

## Krok 2: Načtěte dokument Word, který obsahuje graf

Prvním krokem v jakémkoli **jak upravit graf** pracovním postupu je načíst zdrojový soubor. Aspose.Words představuje celý dokument pomocí třídy `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

Objekt `Document` vám poskytuje přístup ke každému uzlu v souboru, včetně tvarů, tabulek a odstavců.  

## Krok 3: Najděte první tvar grafu v dokumentu

Grafy jsou uloženy jako uzly `Shape`, jejichž renderer je `Chart`. Pro úpravu grafu musíte nejprve získat tento uzel.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Pokud dokument obsahuje více grafů, iterujte přes `shapes` a před přetypováním zkontrolujte `chartShape.getChart() != null`. Tím zabráníte `ClassCastException` a zajistíte, že **měníte možnosti grafu** pouze u platných objektů grafu.

## Krok 4: Povolit mřížky grafu (stupnice) – nová vlastnost ve verzi 24.9

Vlastnost `setShowGraduations` přepíná viditelnost menších mřížek na hodnotové ose. Jejich povolení často zlepšuje čitelnost u hustých datových sad.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Proč je to důležité:** Mřížky poskytují divákům vizuální referenci pro každý datový bod, což usnadňuje rozpoznání trendů. Výchozí hodnota je `false`, takže je musíte explicitně povolit, když je to potřeba.

Můžete také přizpůsobit další aspekty, jako jsou hlavní mřížky, názvy os nebo umístění legendy. Níže je příklad změny názvu grafu a pozice legendy – obojí je součástí **změny možností grafu**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Krok 5: Uložte dokument s aktualizovanými nastaveními grafu

Po úpravě grafu uložte změny. Tento krok dokončuje fázi **uložení aktualizovaného dokumentu**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Spuštěním programu vznikne soubor `output.docx`, ve kterém graf nyní zobrazuje mřížky, nový název a přesunutou legendu. Otevřete soubor v Microsoft Word a ověřte vizuální změny.

## Kompletní zdrojový kód (spustitelný)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Očekávaný výsledek

Když otevřete `output.docx`:

* Graf zobrazuje menší mřížky na hodnotové ose.  
* Název zní **“Sales Overview 2026”**.  
* Legenda se zobrazuje ve spodní části grafu.

Pokud původní graf již měl mřížky, vizuální vzhled zůstane nezměněn, což potvrzuje, že kód je **idempotentní**.

## Časté otázky a řešení okrajových případů

### Co když dokument neobsahuje žádný graf?

Pokus o přetypování tvaru, který není grafem, vyvolá `ClassCastException`. Ochráníte se tím, že zkontrolujete typ tvaru:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Jak upravit konkrétní graf místo prvního?

Iterujte přes `shapes` a porovnejte známý název nebo alternativní identifikátor:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Můžu mřížky později znovu zakázat?

Ano, stačí nastavit vlastnost na `false`:

```java
chart.setShowGraduations(false);
```

### Funguje to i se soubory `.doc` (binárními)?

Aspose.Words abstrahuje formát souboru, takže stejný kód funguje pro `.doc` i `.docx`. Nicméně některé novější funkce grafu (jako stupnice) jsou uloženy pouze v formátu OOXML, takže efekt uvidíte jen při ukládání jako `.docx`.

## Tipy pro produkční kód

* **Ověřte vstupní cesty** – před načtením použijte `Files.exists(Paths.get(inputPath))`.  
* **Zabalte volání API** do bloků try‑catch, aby se zobrazily podrobnosti `Exception`, zejména při práci s poškozenými dokumenty.  
* **Uvolněte prostředky** – i když Aspose.Words spravuje paměť, volání `doc.close()` (nebo použití try‑with‑resources, pokud je k dispozici) může dříve uvolnit nativní handle.  
* **Kontrola verze** – ujistěte se, že verze runtime knihovny je ≥ 24.9 před voláním `setShowGraduations`. Můžete dotazovat `License.getVersion()`, pokud potřebujete programovou ochranu.

## Závěr

Nyní víte **jak upravit graf** v dokumentu Word pomocí Javy. Proces – načíst dokument, najít graf, povolit mřížky grafu, změnit možnosti grafu a **uložit aktualizovaný dokument** – pokrývá nejčastější scénáře programové manipulace s grafy.

Odtud můžete zkoumat další úpravy, jako je změna barev datových sérií, použití stylů grafu nebo export grafu jako obrázku. Každý z těchto úkolů následuje stejný vzor: získat instanci `Chart`, upravit její vlastnosti a **uložit aktualizovaný dokument**.

Šťastné programování a neváhejte experimentovat s dalšími nastaveními grafu, aby vyhovovaly vašim potřebám reportování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Jak uložit dokument jako PDF s Aspose.Words pro Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Nastavit výchozí možnosti pro popisky dat v grafu](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}