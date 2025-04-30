---
"description": "Naučte se v tomto komplexním návodu krok za krokem, jak přidat hodnoty data a času na osu grafu pomocí Aspose.Words pro .NET."
"linktitle": "Přidání hodnot data a času na osu grafu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidání hodnot data a času na osu grafu"
"url": "/cs/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidání hodnot data a času na osu grafu

## Zavedení

Vytváření grafů v dokumentech může být účinným způsobem vizualizace dat. Při práci s časovými řadami dat je pro přehlednost klíčové přidávání hodnot data a času na osu grafu. V tomto tutoriálu vás provedeme procesem přidávání hodnot data a času na osu grafu pomocí Aspose.Words pro .NET. Tento podrobný návod vám pomůže nastavit prostředí, napsat kód a porozumět jednotlivým částem procesu. Pojďme se na to pustit!

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1. Visual Studio nebo jakékoli .NET IDE: Pro psaní a spouštění kódu .NET potřebujete vývojové prostředí.
2. Aspose.Words pro .NET: Měli byste mít nainstalovanou knihovnu Aspose.Words pro .NET. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/net/).
3. Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti programování v C#.
4. Platná licence Aspose: Dočasnou licenci můžete získat od [zde](https://purchase.aspose.com/temporary-license/).

## Importovat jmenné prostory

Nejprve se ujistěte, že máte v projektu importovány potřebné jmenné prostory. Tento krok je klíčový pro přístup ke třídám a metodám Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Nastavení adresáře dokumentů

Nejprve je třeba definovat adresář, kam bude váš dokument uložen. To je důležité pro organizaci souborů a zajištění správného fungování kódu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvořte nový dokument a nástroj DocumentBuilder

Dále vytvořte novou instanci `Document` třída a `DocumentBuilder` objekt. Tyto objekty vám pomohou s tvorbou a manipulací s dokumentem.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložení grafu do dokumentu

Nyní vložte graf do dokumentu pomocí `DocumentBuilder` objekt. V tomto příkladu používáme sloupcový graf, ale můžete zvolit i jiné typy.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Krok 4: Vymazat existující sérii

Vymažte všechny existující řady v grafu, abyste měli jistotu, že začínáte s prázdným listem. Tento krok je nezbytný pro vlastní data.

```csharp
chart.Series.Clear();
```

## Krok 5: Přidání hodnot data a času do série

Přidejte hodnoty data a času do série grafů. Tento krok zahrnuje vytvoření polí pro data a odpovídající hodnoty.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Krok 6: Konfigurace osy X

Nastavte měřítko a značky pro osu X. Tím zajistíte, že se data zobrazí správně a ve vhodných intervalech.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Krok 7: Uložte dokument

Nakonec uložte dokument do zadaného adresáře. Tímto krokem je proces ukončen a váš dokument by nyní měl obsahovat graf s hodnotami data a času na ose X.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Závěr

Přidání hodnot data a času na osu grafu v dokumentu je s Aspose.Words pro .NET přímočarý proces. Dodržováním kroků popsaných v tomto tutoriálu můžete vytvářet přehledné a informativní grafy, které efektivně vizualizují časové řady dat. Ať už připravujete zprávy, prezentace nebo jakýkoli dokument vyžadující podrobnou reprezentaci dat, Aspose.Words poskytuje nástroje, které potřebujete k úspěchu.

## Často kladené otázky

### Mohu s Aspose.Words pro .NET používat i jiné typy grafů?

Ano, Aspose.Words podporuje různé typy grafů, včetně čárových, sloupcových, koláčových a dalších.

### Jak si mohu přizpůsobit vzhled svého grafu?

Vzhled si můžete přizpůsobit přístupem k vlastnostem grafu a nastavením stylů, barev a dalších parametrů.

### Je možné do grafu přidat více sérií?

Rozhodně! Do grafu můžete přidat více sérií voláním funkce `Series.Add` metodu několikrát s různými daty.

### Co když potřebuji dynamicky aktualizovat data grafu?

Data grafu můžete dynamicky aktualizovat programově manipulací s vlastnostmi řad a os na základě vašich požadavků.

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?

Podrobnější dokumentaci naleznete [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}