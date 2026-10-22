---
category: general
date: 2026-09-21
description: Naučte se, jak v C# vytvořit dokument Word a vložit sloupcový graf, nastavit
  pozici popisků a zobrazit hodnoty pomocí Aspose.Words v průvodci krok za krokem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: cs
lastmod: 2026-09-21
og_description: Vytvořte Word dokument v C# s Aspose.Words. Tento tutoriál ukazuje,
  jak vložit sloupcový graf, nastavit pozici popisků a zobrazit hodnoty.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Vytvořit Word dokument v C# – vložit sloupcový graf, nastavit popisek, zobrazit
  hodnoty
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Jak vytvořit Word dokument v C# se sloupcovým grafem a formátovanými popisky
url: /cs/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit Word dokument v C# s sloupcovým grafem a formátovanými popisky

Pokud potřebujete **create Word document C#**, který obsahuje graf, tento průvodce vám přesně ukáže, jak na to. Naučíte se, jak vložit sloupcový graf, umístit jeho popisek dat a zobrazit hodnoty popisku – vše pomocí Aspose.Words pro .NET.

Vytvoření Word souboru s grafem dříve vyžadovalo ruční práci v Microsoft Wordu. S kroky **how to insert chart** popsanými zde můžete automatizovat celý proces z kódu, což umožní rychlé a opakovatelné generování reportů. Tutoriál také pokrývá **how to set label** vlastnosti a **how to display values**, takže graf je připraven pro koncové uživatele.

Na konci tohoto článku budete mít kompletní, spustitelný C# program, který vytvoří soubor `.docx` obsahující sloupcový graf, jehož datové popisky jsou umístěny uvnitř každého sloupce a zobrazují jejich číselné hodnoty.

## Požadavky

* .NET 6.0 SDK nebo novější nainstalováno  
* Licencovaná kopie **Aspose.Words for .NET** (bezplatná zkušební verze funguje pro testování)  
* IDE, například Visual Studio 2022 nebo Visual Studio Code  

Kromě `Aspose.Words` nejsou vyžadovány žádné další balíčky NuGet.

## Krok 1: Nastavení projektu a přidání Aspose.Words

Vytvořte nový konzolový projekt a přidejte balíček Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

Příkaz `dotnet add package` stáhne nejnovější stabilní verzi **Aspose.Words**, která obsahuje API pro grafy použité v příkladu **insert column chart word**.

## Krok 2: Vytvoření nového prázdného Word dokumentu

První část kódu vytvoří prázdný dokument a `DocumentBuilder`, který umožňuje vkládat obsah. Toto je základ pro **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` představuje celý soubor `.docx`, zatímco `DocumentBuilder` poskytuje metody jako `InsertParagraph`, `InsertImage` a, co je pro tento tutoriál klíčové, `InsertChart`.

## Krok 3: Vložení sloupcového grafu (how to insert chart)

Nyní vložíme **column chart**. Metoda `InsertChart` přijímá typ grafu, šířku a výšku v bodech.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

V tomto okamžiku graf obsahuje výchozí datovou řadu s hodnotami zástupných znaků. Pokud potřebujete vlastní čísla, můžete nahradit data řady, ale pro demonstraci **how to set label** a **how to display values** jsou výchozí data dostačující.

## Krok 4: Umístění datového popisku uvnitř každého sloupce (how to set label)

Datové popisky jsou text, který se zobrazuje u každého sloupce. Aby byl graf čitelnější, přesuneme popisek dovnitř sloupce a povolíme jeho číselnou hodnotu.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` umístí popisek na vrchol sloupce, ale stále uvnitř tvaru sloupce, což je běžný vizuální styl pro reporty. Nastavení `ShowValue` na `true` splňuje požadavek **how to display values**.

## Krok 5: Uložení dokumentu

Nakonec zapíšeme dokument na disk. Soubor lze otevřít v Microsoft Word, LibreOffice nebo v jakémkoli prohlížeči, který podporuje formát Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Spuštěním programu vznikne `output.docx`, který obsahuje sloupcový graf s datovými popisky umístěnými uvnitř každého sloupce a zobrazujícími jejich hodnoty.

### Očekávaný výsledek

Když otevřete `output.docx`, měli byste vidět jediný sloupcový graf podobný obrázku níže. Každý sloupec má číselný popisek na vrcholu, uvnitř sloupce, zobrazující hodnotu řady.

![Graf ve Word dokumentu vytvořeném pomocí C#](/images/word-chart-example.png "Graf ve Word dokumentu vytvořeném pomocí C# – create word document C#")

*Alt text:* *Graf ve Word dokumentu vytvořeném pomocí C#, který demonstruje, jak vložit sloupcový graf do Wordu a zobrazit hodnoty.*

## Běžné varianty a okrajové případy

### Přidání vlastních dat do grafu

Pokud potřebujete nahradit data zástupných znaků, můžete upravit kolekci `Series` grafu:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Změna písma a barvy popisku

Můžete dále přizpůsobit vzhled popisku:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Vkládání více grafů

`DocumentBuilder` může vložit tolik grafů, kolik potřebujete. Stačí znovu zavolat `InsertChart` po přesunutí kurzoru pomocí `builder.Writeln()` nebo `builder.InsertParagraph()`.

## Pro tipy

* **Pro tip:** Nastavte `chart.HasTitle = true` a přiřaďte `chart.Title.Text`, aby graf získal popisný nadpis. To zlepšuje přístupnost pro čtečky obrazovky.  
* **Watch out for:** Při ukládání na síťové úložiště se ujistěte, že aplikace má oprávnění k zápisu; jinak `doc.Save` vyhodí `UnauthorizedAccessException`.  
* **Performance tip:** Znovu použijte jedinou instanci `DocumentBuilder` pro více vkládání; vytvoření nového builderu pro každou operaci přidává zbytečnou zátěž.

## Závěr

Nyní víte, jak **create Word document C#**, který obsahuje sloupcový graf, jak **insert chart** prvky, **set label** pozice a **display values** uvnitř každého sloupce. Kompletní ukázkový kód výše je připraven ke spuštění a můžete jej rozšířit o vlastní data, stylování nebo další grafy.

Dále prozkoumejte související témata, jako je **how to insert picture**, **how to generate tables** nebo **how to apply document themes**, abyste svým automatizovaným reportům přidali ještě více bohatství. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vložit sloupcový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Vložit jednoduchý sloupcový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Vložit oblastní graf do Word dokumentu | Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}