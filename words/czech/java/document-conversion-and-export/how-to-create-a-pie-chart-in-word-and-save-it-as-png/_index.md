---
category: general
date: 2026-10-07
description: Naučte se, jak vytvořit koláčový graf ve Wordu, přidat datové řady a
  uložit graf jako PNG pomocí Javy. Postupujte podle krok‑za‑krokem průvodce pro rychlé
  výsledky.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: cs
lastmod: 2026-10-07
og_description: 'Rychle vytvořte koláčový graf ve Wordu: tento tutoriál ukazuje, jak
  přidat datové řady, vygenerovat graf a uložit graf ve Wordu jako obrázek (PNG).
  Postupujte podle kompletního příkladu kódu.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Vytvořte koláčový graf ve Wordu a exportujte jako PNG – průvodce
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Jak vytvořit koláčový graf ve Wordu a uložit jej jako PNG
url: /cs/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit koláčový graf ve Wordu a uložit jej jako PNG

Pokud potřebujete **vytvořit koláčový graf** objektů uvnitř souboru Microsoft Word, tento průvodce vám přesně ukáže, jak to provést pomocí Javy. Také se naučíte, jak **přidat datové řady** do grafu a **uložit graf jako PNG**, aby bylo vizuální zobrazení možné znovu použít mimo Word.

Generování grafu přímo v dokumentu vám ušetří exportování dat do samostatného grafického nástroje. Na konci tohoto tutoriálu budete mít plně funkční soubor Word, který obsahuje koláčový graf a odpovídající PNG obrázek na disku.

## Požadavky

* Java 17 nebo novější nainstalována.
* Knihovna **GroupDocs.Viewer for Java** (nebo kompatibilní knihovna, která poskytuje třídy `Document`, `Chart`, `ChartType` a `ImageSaveOptions`).
* Projekt Maven nebo Gradle, kde můžete přidat závislost knihovny.
* Vstupní Word dokument (`input.docx`) umístěný ve složce, na kterou můžete odkazovat z kódu.

Pokud používáte Maven, přidejte závislost (nahraďte `VERSION` nejnovější verzí):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Jak vytvořit koláčový graf ve Wordu

Jádro řešení se točí kolem tří akcí:

1. Načíst zdrojový soubor `.docx`.
2. **Přidat datové řady** do nového objektu `Chart` typu `PIE`.
3. **Uložit graf jako PNG**, abyste získali soubor s obrázkem vedle dokumentu Word.

Níže je každý krok podrobně vysvětlen, následovaný přesným Java kódem, který potřebujete.

### Krok 1: Načíst zdrojový dokument

Musíte otevřít soubor Word, který bude hostit graf. Třída `Document` načte obsah `.docx` do paměti.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Proč je to důležité*: Načtení dokumentu vytvoří měnitelný model. Všechny následné operace s grafem upravují tuto reprezentaci v paměti, kterou později uložíte zpět na disk.

### Krok 2: Přidat datové řady do grafu

Vytvoření **koláčového grafu** začíná instancí `Chart`. Konstruktor přijímá nadřazený `Document` a typ grafu (`ChartType.PIE`). Po vytvoření objektu grafu jej naplníte číselnými hodnotami a volitelnými popisky.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Proč je to důležité*: Metoda `add` **přidává datové řady** do grafu. Každý záznam v `values` se stane částí koláče, zatímco `categories` poskytují popisky legendy. Můžete zadat libovolný počet bodů; knihovna automaticky vypočítá úhly částí.

### Krok 3: Uložit graf jako PNG

Jakmile je graf součástí dokumentu, můžete exportovat vizuální reprezentaci. Metoda `save` na podkladovém objektu grafu zapíše soubor PNG do souborového systému.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Proč je to důležité*: Uložení grafu jako PNG vám poskytne rastrový obrázek, který lze vložit do webových stránek, e‑mailů nebo reportů, aniž byste potřebovali původní soubor Word. Objekt `ImageSaveOptions` vám umožňuje řídit formát, rozlišení a další nastavení exportu.

## Vytvoření koláčového grafu ve Wordu – přizpůsobení vzhledu

Mimo základní kroky můžete chtít přizpůsobit barvy, nadpisy nebo popisky dat. Většina knihoven poskytuje objekt `ChartOptions` nebo podobný. Zde je rychlý příklad, který přidá nadpis a změní barvy částí:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Tato přizpůsobení jsou volitelná, ale ukazují, jak můžete **vytvořit koláčový graf ve Wordu**, který odpovídá vaší značce.

## Uložení grafu Word jako obrázku – alternativní přístupy

Pokud potřebujete pouze obrázek a ne graf uvnitř dokumentu, můžete vynechat vložení tvaru grafu do souboru Word a přímo po vytvoření grafu zavolat metodu `save`. Kód zůstane stejný; jednoduše vynecháte kroky, které přidávají graf do těla dokumentu.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Tato technika je užitečná, když generujete mnoho grafů v dávkovém procesu a zajímá vás jen výstup PNG.

## Kompletní spustitelný příklad

Zkopírujte následující třídu do svého projektu, upravte cesty k souborům a spusťte ji. Program:

1. Načíst `input.docx`.
2. **Vytvořit koláčový graf**, **přidat datové řady** a vložit jej do dokumentu.
3. **Uložit graf jako PNG** (`radial.png`).
4. Uložit upravený soubor Word jako `output.docx`.



## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Vytvořit rozptylový graf ve Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Vložit sloupcový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}