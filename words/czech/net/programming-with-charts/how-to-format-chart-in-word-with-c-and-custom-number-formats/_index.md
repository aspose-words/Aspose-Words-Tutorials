---
category: general
date: 2026-10-13
description: Jak naformátovat graf ve Wordu pomocí C# aplikací vlastního číselného
  formátu, například měny, na osy grafu. Krok‑za‑krokem ukázkový kód zahrnut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: cs
lastmod: 2026-10-13
og_description: Jak formátovat graf ve Wordu pomocí C# vám umožní použít vlastní číselný
  formát na osy grafu, aby se hodnoty zobrazovaly jako měna, procenta nebo jakýkoli
  jiný vzor, který potřebujete. Postupujte podle podrobného návodu.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Jak formátovat graf ve Wordu pomocí C# – vlastní číselné formáty
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Jak formátovat graf ve Wordu pomocí C# a vlastních číselných formátů
url: /cs/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak formátovat graf ve Wordu pomocí C# a vlastních číselných formátů

Formátování grafu ve Wordu pomocí C# je častý požadavek, když potřebujete prezentovat data profesionálně. Tento průvodce vám ukáže, jak pomocí **Aspose.Words for .NET** použít vlastní číselný formát na osu grafu, aby se hodnoty zobrazovaly přesně tak, jak očekáváte.

Naučíte se, jak načíst soubor DOCX, najít první graf, přečíst aktuální formát a poté nastavit nový vzor, například měnu se dvěma desetinnými místy. Tutoriál také popisuje, jak změnit formát osy grafu pro další řady a jak v případě potřeby formát resetovat.

## Požadavky

* .NET 6.0 nebo novější nainstalovaný  
* Projekt ve Visual Studio 2022 (nebo jakémkoli IDE podporujícím .NET)  
* NuGet balíček **Aspose.Words for .NET** (`Aspose.Words`)  
* Word dokument (`input.docx`), který obsahuje alespoň jeden graf

Balíček můžete přidat následujícím příkazem:

```bash
dotnet add package Aspose.Words
```

## Jak formátovat graf ve Wordu pomocí Aspose.Words

Následující kompletní program demonstruje každý krok potřebný k **formátování** hodnot osy grafu. Uložte soubor jako `Program.cs` a spusťte jej z příkazové řádky nebo z vašeho IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Vysvětlení jednotlivých kroků

| Krok | Proč je důležité | Klíčový kód |
|------|-------------------|-------------|
| **Načíst dokument** | Potřebujete objekt `Document` pro práci se souborem Word. | `new Document("input.docx")` |
| **Získat graf** | Objekty `Chart` jsou uloženy jako uzly `Shape`; přetypování vám umožní použít API specifické pro graf. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Přístup k X‑hodnotám** | Formátování osy se aplikuje na kolekci hodnot datové řady. | `chart.ChartData.Series[0].XValues` |
| **Přečíst aktuální formát** | Znalost existujícího `FormatCode` vám pomůže rozhodnout, zda jej nahradit nebo rozšířit. | `xValues.FormatCode` |
| **Nastavit vlastní formát** | Vlastnost `FormatCode` přijímá libovolný vzor kompatibilní s Excelem, což umožňuje měny, procenta, data atd. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Uložit dokument** | Uložení změn zapíše nový formát osy zpět do souboru DOCX. | `doc.Save("output_formatted.docx")` |

Spuštěním programu vznikne soubor `output_formatted.docx`. Otevřete jej ve Wordu a uvidíte, že hodnoty X‑osy grafu jsou zobrazeny jako **$1,234.00**, **$2,345.00**, … místo prostých čísel.

## Použití vlastního číselného formátu na osu grafu

Pokud potřebujete **použít vlastní číselný formát** na osu Y nebo na další řady, postup je stejný – stačí cílit na jinou kolekci:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Tip:** Použijte dvojité uvozovky uvnitř formátovacího řetězce k vložení doslovných znaků (např. `"$"` pro měnu). Uvozovky escapujte, jak je ukázáno výše.

## Vlastní číselný formát – práce s locale ve Wordu

Word respektuje locale dokumentu při interpretaci číselných formátů. Pokud dokument používá locale odlišné od US, možná budete muset upravit formátovací řetězec:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Testování formátu v dokumentu s nastavením německého jazyka potvrzuje, že hodnoty se zobrazují jako **€ 1.234,00**.

## Jak nastavit vlastnosti grafu programově

Kromě formátování osy často chcete **nastavit** názvy grafu, legendy nebo popisky dat. Zde je rychlý úryvek, který ukazuje nastavení názvu grafu po formátování osy:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Kombinací s vlastním číselným formátem získáte plně vyladěný graf připravený pro reportování.

## Dynamická změna formátu osy grafu na základě vstupu uživatele

V reálných aplikacích můžete uživatelům umožnit vybrat formát za běhu. Následující metoda zapouzdřuje logiku formátování:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Můžete zavolat `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` pro měnu nebo `SetAxisFormat(chart, 0, "0%")` pro procenta. Tento přístup udržuje hlavní kód čistý a podporuje budoucí rozšíření.

## Okrajové případy a běžné úskalí

| Situace | Na co si dát pozor | Navrhované řešení |
|-----------|-------------------|-------------------|
| Dokument neobsahuje **žádný graf** | `GetChild` vrací `null`, což způsobí výjimku při přetypování. | Zkontrolujte `null` před přetypováním (viz příklad). |
| Více grafů ve stejném dokumentu | Kód vždy získá první graf (`index 0`). | Procházejte `doc.GetChildNodes(NodeType.Shape, true)` a filtrujte podle `ShapeType.Chart`. |
| Řady **bez X‑hodnot** (např. koláčové grafy) | Přístup k `XValues` může vyvolat `ArgumentOutOfRangeException`. | Ověřte, že `Series[i].XValues` není prázdná před formátováním. |
| Neshoda locale | Symbol měny se může zobrazit nesprávně. | Explicitně nastavte `xValues.FormatCode` s odpovídajícími symboly locale. |

## Očekávaný výstup

Po spuštění ukázkového programu otevřete **output_formatted.docx**. X‑osa grafu by měla zobrazovat čísla ve zvoleném vlastním formátu. Pro příklad s měnou vypadají popisky osy takto:

```
$1,000.00
$2,000.00
$3,000.00
```

Pokud jste použili formát procent na hodnoty Y, popisky Y‑osy se zobrazí jako:

```
10%
20%
30%
```

## Závěr

Tento tutoriál vám ukázal, **jak formátovat graf** ve Wordu pomocí C# tím, že **aplikujete vlastní číselný formát** na hodnoty osy. Nyní máte znovupoužitelný vzor pro nastavení měny, procent nebo jakéhokoli jiného číselného vzoru, stejně jako návod, jak pracovat s locale, více řadami a dynamickým vstupem uživatele.

Dále můžete prozkoumat **jak nastavit** názvy grafu, popisky dat nebo dokonce exportovat graf jako obrázek pomocí `ChartRenderer`. Tyto témata navazují přímo na zde probírané koncepty a pomohou vám vytvořit plně automatizovaná řešení pro reportování.

---

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Formát čísel pro osu v grafu](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Formát čísla datové popisky v grafu](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Formát sekundární X‑osy a nastavení zobrazovacích jednotek na tisíce v čárových grafech Wordu pomocí Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}