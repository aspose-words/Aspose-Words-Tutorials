---
category: general
date: 2026-09-08
description: Vytvořte prázdný dokument Word a přidejte do Wordu graf pomocí Aspose.Words.
  Naučte se, jak vložit radarový graf, povolit stupnice a uložit soubor.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: cs
lastmod: 2026-09-08
og_description: Vytvořte prázdný dokument Word a přidejte do Wordu graf pomocí Aspose.Words.
  Tento tutoriál ukazuje, jak vložit radarový graf, nastavit osy a uložit dokument.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Vytvořte prázdný dokument Word a přidejte radarový graf – krok za krokem.
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Jak vytvořit prázdný dokument Word a přidat graf do Wordu
url: /cs/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word a přidat do Wordu graf

Pokud potřebujete **vytvořit prázdný dokument Word** pro zprávu, šablonu nebo automatizované hromadné dopisy, tento návod vás provede celým procesem pomocí C# a Aspose.Words. Také se naučíte, jak **přidat graf do Wordu**, konkrétně jak **vložit radarový graf**, zapnout stupnice a výsledek uložit jako soubor .docx.

Tento tutoriál pokrývá vše od nastavení projektu až po finální ověřovací krok. Na konci budete mít znovupoužitelný úryvek kódu, který můžete vložit do jakékoli .NET aplikace. Předchozí zkušenost s Aspose.Words není vyžadována, ale měli byste mít základní znalosti C# a nainstalovaný aktuální .NET SDK.

## Požadavky

- .NET 6.0 SDK nebo novější  
- Aspose.Words pro .NET (NuGet balíček `Aspose.Words`)  
- IDE, např. Visual Studio 2022 nebo VS Code  
- Oprávnění k zápisu do složky, kde bude dokument uložen  

Knihovnu můžete nainstalovat následujícím příkazem:

```bash
dotnet add package Aspose.Words
```

## Krok 1: Vytvořit prázdný dokument Word

Prvním krokem je **vytvořit prázdný dokument Word** v paměti. Třída `Document` představuje celý soubor, zatímco `DocumentBuilder` poskytuje plynulé API pro přidávání obsahu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` začíná prázdný, takže máte čisté plátno, na které můžete umístit graf. Udržení dokumentu v tomto stádiu prázdného usnadňuje opětovné použití stejného kódu pro různé šablony.

## Krok 2: Přidat graf do Wordu

Dále **přidáme graf do Wordu** voláním `InsertChart`. Metoda vyžaduje typ grafu a požadované rozměry v bodech (1 bod = 1/72 palce).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` říká Aspose.Words, aby vygeneroval radiální graf, který je ideální pro zobrazování multivariačních dat v kruhovém uspořádání. Hodnoty velikosti (400 × 300) fungují dobře pro většinu portrétních stránek, ale můžete je upravit podle svého rozvržení.

## Krok 3: Vložit radarový graf a nastavit stupnice

Nyní **vložíme radarový graf** a povolíme stupnice (značky) na obou osách – kategoriální (X) i hodnotové (Y). Stupnice zlepšují čitelnost tím, že ukazují přesné pozice pro každý datový bod.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Nastavením `HasGraduations` na `true` se na osách vykreslí značky. Volitelný parametr `GraduationStep` řídí vzdálenost mezi značkami na radiální ose; krok 10 znamená značku každých 10 stupňů.

### Tip
Pokud potřebujete zobrazit popisky dat, zavolejte `radarChart.Series[0].HasDataLabel = true;`. Tím se přidá číselná hodnota vedle každého bodu, což je užitečné pro prezentace.

## Krok 4: Naplnit graf ukázkovými daty (volitelné)

Radarový graf bez dat je neviditelný. Níže je rychlý způsob, jak přidat sérii ukázkových hodnot. Tento blok můžete nahradit vlastním zdrojem dat.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Každé volání `Add` vloží bod do série. Pořadí bodů odpovídá úhlovým pozicím kolem kruhu.

## Krok 5: Uložit dokument obsahující graf

Nakonec uložte dokument na disk. Metoda `Save` automaticky zapíše soubor .docx, zachová graf i veškeré formátování.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Spuštěním programu se vytvoří **prázdný dokument Word**, který nyní obsahuje plně funkční radarový graf. Otevřete soubor v Microsoft Wordu a podívejte se na výsledek.

![Radar chart in Word document](radar_chart.png){alt="Radarový graf vložený do prázdného dokumentu Word"}

## Běžné varianty a okrajové případy

| Situace | Co změnit |
|-----------|----------------|
| **Jiná velikost grafu** | Adjust the width/height parameters of `InsertChart`. |
| **Jiné typy grafů** | Replace `ChartType.Radar` with `ChartType.Column`, `ChartType.Pie`, etc., and keep the same graduation logic. |
| **Ukládání do proudu** | Use `document.Save(Stream, SaveFormat.Docx)` |

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vložit oblastní graf do dokumentu Word \| Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Vytvořit rozptýlený graf Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Vložit sloupcový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}