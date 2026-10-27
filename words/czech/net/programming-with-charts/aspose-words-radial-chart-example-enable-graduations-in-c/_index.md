---
category: general
date: 2026-10-13
description: Příklad radiálního grafu Aspose.Words, který ukazuje, jak povolit graduace
  na radiálním grafu pomocí C# a Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: cs
lastmod: 2026-10-13
og_description: Aspose.Words příklad radiálního grafu, který demonstruje povolení
  graduací na radiálním grafu pomocí C# a nejnovější knihovny 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words – příklad radiálního grafu – povolit stupnice v C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Příklad radiálního grafu Aspose.Words: povolit graduace v C#'
url: /cs/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Příklad radiálního grafu Aspose.Words: povolení stupnic v C#

Pokud hledáte **aspose.words radial chart example**, jste na správném místě. Tento tutoriál vás provede přesnými kroky, jak zapnout stupnice pro radiální graf pomocí Aspose.Words pro .NET API.

Radiální grafy jsou užitečné pro vizualizaci cyklických dat, jako jsou metriky času během dne nebo sezónní trendy. Ve výchozím nastavení jsou stupnice (značky na kruhové ose) skryté, což může ztížit čtení grafu. Povolení je jednorázová změna v jednom řádku, ale musíte znát správný objektový model a verzi, která tuto funkci podporuje.

V tomto průvodci se naučíte, jak:

* Načíst dokument Word, který již obsahuje radiální graf.  
* Přistupovat k tvaru grafu přes Aspose.Words chart API.  
* Zapnout **graduations visibility** (k dispozici od **Aspose.Words version 24.9**).  
* Uložit upravený dokument a ověřit výsledek.

Kompletní spustitelný kód je zahrnut, takže jej můžete zkopírovat a vložit do nového konzolového projektu a okamžitě vidět výsledek.

![Aspose.Words radial chart example with graduations](https://example.com/images/radial-chart-graduations.png "Aspose.Words radial chart example showing graduations enabled")

## Požadavky

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 or later | Aspose.Words pro .NET 24.9+ cílí na .NET Standard 2.0 a funguje na .NET 6+. |
| Aspose.Words for .NET **24.9** or newer | Vlastnost `IsGraduationsVisible` byla zavedena ve verzi 24.9. Starší verze vyhodí `MissingMemberException`. |
| A Word document (`RadialChart.docx`) that contains a radial chart | Příklad upravuje existující graf; vytvoření grafu od nuly je samostatné téma. |
| A C# IDE (Visual Studio, Rider, VS Code) | Jakékoli IDE, které dokáže kompilovat .NET projekty, bude fungovat. |
| NuGet package `Aspose.Words` | Nainstalujte pomocí `dotnet add package Aspose.Words --version 24.9.0` (nebo novější). |

> **Tip:** Pokud nemůžete upgradovat na 24.9, můžete stále upravovat jiné vlastnosti grafu, ale stupnice zůstanou skryté, protože API tuto vlajku neexponovalo.

## Příklad radiálního grafu Aspose.Words – krok za krokem průvodce

Následující sekce rozdělují proces na jednotlivé, snadno sledovatelné kroky. Každý krok obsahuje přesný kód, který potřebujete, a krátké vysvětlení, *proč* krok existuje.

### Krok 1: Načíst dokument, který obsahuje radiální graf

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Proč je to důležité:**  
`Document` je vstupní bod **Aspose.Words chart API**. Načte soubor DOCX do paměti a poskytne vám přístup ke všem uzlům — odstavcům, tabulkám a tvarům grafů. Pokud soubor nelze najít, `Document` vyhodí `FileNotFoundException`, kterou byste měli v produkčním kódu ošetřit.

### Krok 2: Získat první tvar grafu z dokumentu

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Proč je to důležité:**  
Grafy jsou uloženy jako uzly `Shape`. Metoda `GetChild` s parametrem `NodeType.Shape` prochází DOM a vrací první odpovídající tvar. Přetypování na `Chart` vám poskytne přístup ke grafům specifickým vlastnostem, jako je `RadialChart`. Kontrola na null zajišťuje jasnou chybu, pokud dokument neobsahuje graf, což je častý okrajový případ při opětovném použití šablon.

### Krok 3: Povolit stupnice na radiálním grafu

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Proč je to důležité:**  
`IsGraduationsVisible` řídí značky na kruhové ose. Když je nastaven na `true`, graf vykreslí stupnice, což zlepšuje čitelnost pro uživatele, kteří potřebují přesně odhadnout hodnoty. Vlastnost se nachází pod `RadialChart`, což je podtyp `Chart`. Pokud to zkusíte na ne‑radiálním grafu (např. sloupcovém grafu), vlastnost `RadialChart` bude `null`, takže byste měli nejprve ověřit typ grafu v komplexnějších scénářích.

#### Zpracování ne‑radiálních grafů (volitelné)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Tato ochrana činí kód robustním, pokud zdrojový dokument může obsahovat různé typy grafů.

### Krok 4: Uložit upravený dokument

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Proč je to důležité:**  
Volání `Save` zapíše DOM v paměti zpět do souboru .docx, čímž uloží změnu provedenou v grafu. Výstupní soubor lze otevřít v Microsoft Word, LibreOffice nebo jakémkoli prohlížeči podporujícím DOCX. Uvidíte radiální graf se zobrazujícími stupnicemi.

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete vložit do `Program.cs` .NET konzolového projektu.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Očekávaný výstup

Když otevřete `RadialChart_Graduations.docx` ve Wordu, radiální graf zobrazí značky (stupnice) kolem kruhové osy, podobně jako na předchozím snímku obrazovky. Zbytek grafu (datové řady, legenda, název) zůstane beze změny.

## Běžné varianty a okrajové případy

| Situation | Solution |
|-----------|----------|
| **Older Aspose.Words version (< 24.9)** | Aktualizujte na nejnovější NuGet balíček. Vlastnost `IsGraduationsVisible` v dřívějších verzích neexistuje. |
| **Multiple charts in the same document** | Použijte `doc.GetChild(NodeType.Shape, index, true)` s odpovídajícím `index` nebo iterujte přes `doc.GetChildNodes(NodeType.Shape, true)` a filtrujte podle `ChartType.Radial`. |
| **Chart created programmatically** | Použijte `DocumentBuilder` k vložení grafu a poté nastavte `RadialChart.IsGraduationsVisible` na |

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok za krokem vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Remove a Chart Series from a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Hide Plot Area Border in a Column Chart with Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}