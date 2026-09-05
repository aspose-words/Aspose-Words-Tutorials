---
category: general
date: 2026-09-05
description: Vytvořte radarový graf ve Wordu pomocí C#. Naučte se rychle vytvořit
  prázdný dokument Word, přidat radarový graf, nastavit velikost grafu a povolit značky
  os.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: cs
lastmod: 2026-09-05
og_description: Vytvořte radarový graf ve Wordu pomocí C#. Tento návod vám ukáže,
  jak vytvořit prázdný dokument Word, přidat radarový graf, nastavit velikost grafu
  a povolit značky os – vše během několika minut.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Vytvořte radarový graf ve Wordu – krok za krokem průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Jak vytvořit radarový graf a přidat graf do Wordu pomocí C#
url: /cs/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit radarový graf a přidat graf do Wordu pomocí C#

Pokud potřebujete **vytvořit radarový graf** v souboru Word, tento návod vás provede celým procesem. Naučíte se **vytvořit prázdný dokument Word**, vložit radarový graf, **nastavit velikost grafu ve Wordu** a povolit stupnice osy – vše pomocí několika řádků kódu v C#.

Přidávání vizuálních dat do zpráv je běžná potřeba a s Aspose.Words je to jednoduché. V následujících krocích také ukážeme, jak **přidat graf do Wordu** programově, takže můžete automatizovat dashboardy, finanční souhrny nebo jakýkoli obsah založený na datech.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 nebo novější nainstalovaný  
* Licenci Aspose.Words pro .NET (nebo bezplatnou zkušební verzi) – knihovna poskytuje třídy `Document`, `DocumentBuilder` a API pro grafy použité v tomto tutoriálu  
* Visual Studio 2022 (nebo jakékoli jiné IDE pro C#)  

> **Tip:** Pokud testujete, umístěte DLL Aspose.Words do složky `bin` vašeho projektu a odkažte ji přes NuGet (`Install-Package Aspose.Words`).

## Jak vytvořit radarový graf v dokumentu Word

Prvním krokem je **vytvořit prázdný dokument Word**, který bude hostit graf. To vám poskytne čisté plátno a umožní nastavit metadata dokumentu před přidáním jakéhokoli obsahu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Proč je to důležité:* Prázdný objekt `Document` zajišťuje, že žádné skryté styly nebo sekce nebudou ovlivňovat rozvržení grafu. Také vám umožní později nastavit vlastnosti dokumentu (autor, název) podle potřeby.

## Jak přidat graf do Wordu pomocí Aspose.Words

Dále vytvořte `DocumentBuilder`. Builder je hlavní nástroj, který vám umožní vkládat text, obrázky i grafy do dokumentu.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Nyní můžete **přidat radarový graf** přímo na místo, kde je kurzor umístěn. Metoda `InsertChart` přijímá výčtový typ `ChartType`, šířku a výšku v bodech.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Proč 400 × 300?* Tyto rozměry poskytují přehledný, čitelný graf na standardní stránce A4. Velikost můžete později upravit pomocí kroku **nastavit velikost grafu ve Wordu**, pokud váš rozvrh vyžaduje jiný poměr stran.

## Nastavení velikosti grafu ve Wordu

Pokud potřebujete po vložení velikost doladit, můžete upravit vlastnosti `Width` a `Height` grafu. To je užitečné, když okolní text nebo okraje stránky vyžadují jinou vizuální rovnováhu.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Poznámka:** Přetížení `InsertChart` již nastavuje velikost, takže výše uvedený kód je volitelný a slouží pro úplnost.

## Povolení značek na radiální ose

Radarový graf je nejvíce užitečný, když radiální osa zobrazuje jasné stupnice. Následující nastavení zapíná značky a nastavuje interval na 30 stupňů, což odpovídá typickému kompasovému zobrazení radaru.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Proč je to důležité:* Stupnice pomáhají čtenářům odhadnout hodnoty podél každého úhlu, čímž zvyšují čitelnost pro zainteresované strany, které nejsou s daty obeznámeny.

## Uložení dokumentu obsahujícího graf

Nakonec zapište dokument na disk. Můžete zvolit libovolnou složku; jen se ujistěte, že cesta existuje.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Když otevřete `RadialChart.docx` v Microsoft Word, uvidíte plně vykreslený radarový graf uprostřed stránky, ve specifikované velikosti a se značkami každých 30 stupňů.

### Očekávaný výstup

* Soubor `.docx` pojmenovaný **RadialChart.docx**  
* První stránka obsahuje radarový graf o rozměrech 400 × 300 bodů  
* X‑osa (radiální osa) zobrazuje značky při 0°, 30°, 60°, …, 330°  

Nyní můžete nahradit zástupnou sérii dat vlastními hodnotami pomocí `radarChart.Series` – ale to už přesahuje rámec tohoto základního **přidat radarový graf** tutoriálu.

## Běžné varianty a okrajové případy

| Scénář | Úprava |
|----------|------------|
| **Jiný typ grafu** | Nahraďte `ChartType.Radar` za `ChartType.Column`, `ChartType.Pie` atd. |
| **Více grafů** | Volajte `InsertChart` opakovaně; každý volání umístí nový graf za předchozí. |
| **Velké datové sady** | Použijte `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` pro naplnění mnoha bodů. |
| **Ukládání jako PDF** | Zavolejte `document.Save("RadialChart.pdf", SaveFormat.Pdf);` po přidání grafu. |
| **Běh na .NET Core** | Ujistěte se, že odkazujete na balíček `Aspose.Words.NETCore`; použití API je identické. |

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do konzolové aplikace. Obsahuje všechny kroky, volitelné úpravy velikosti a komentáře pro přehlednost.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Spusťte program, otevřete vzniklý soubor a uvidíte radarový graf přesně tak, jak je popsáno.

## Závěr

Nyní víte, jak **vytvořit radarový graf** a **přidat graf do Wordu** pomocí C#. Tutoriál pokrýval generování **prázdného dokumentu Word**, vložení radarového grafu, **nastavení velikosti grafu ve Wordu** a povolení stupnic osy. S tímto základem můžete rozšířit řešení o více grafů, vlastní datové série nebo export do PDF.

### Další kroky

* Prozkoumejte další typy grafů pomocí `ChartType` (např. `Bar`, `Line`) – viz klíčové slovo **add radar chart** pro související příklady.

## Co byste se měli naučit dál?

Následující tutoriály se zabývají úzce souvisejícími tématy, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}