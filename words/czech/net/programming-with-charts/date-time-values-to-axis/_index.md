---
title: Přidejte hodnoty data a času na osu grafu
linktitle: Přidejte hodnoty data a času na osu grafu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak přidat hodnoty data a času na osu grafu pomocí Aspose.Words for .NET v tomto komplexním podrobném průvodci.
weight: 10
url: /cs/net/programming-with-charts/date-time-values-to-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidejte hodnoty data a času na osu grafu

## Zavedení

Vytváření grafů v dokumentech může být účinným způsobem vizualizace dat. Při práci s daty časových řad je přidání hodnot data a času na osu grafu zásadní pro přehlednost. V tomto tutoriálu vás provedeme procesem přidávání hodnot data a času na osu grafu pomocí Aspose.Words for .NET. Tento podrobný průvodce vám pomůže nastavit vaše prostředí, napsat kód a porozumět každé části procesu. Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1. Visual Studio nebo jakékoli .NET IDE: K psaní a spouštění kódu .NET potřebujete vývojové prostředí.
2.  Aspose.Words for .NET: Měli byste mít nainstalovanou knihovnu Aspose.Words for .NET. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
3. Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti o programování v C#.
4.  Platná licence Aspose: Můžete získat dočasnou licenci od[zde](https://purchase.aspose.com/temporary-license/).

## Importovat jmenné prostory

Nejprve se ujistěte, že máte do projektu importovány potřebné jmenné prostory. Tento krok je zásadní pro přístup k třídám a metodám Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Nastavte adresář dokumentů

Nejprve musíte definovat adresář, kam bude dokument uložen. To je důležité pro uspořádání souborů a zajištění správného chodu kódu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvořte nový dokument a DocumentBuilder

 Dále vytvořte novou instanci souboru`Document` třída a a`DocumentBuilder` objekt. Tyto objekty vám pomohou vytvořit a manipulovat s dokumentem.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložte graf do dokumentu

 Nyní vložte graf do dokumentu pomocí`DocumentBuilder` objekt. V tomto příkladu používáme sloupcový graf, ale můžete si vybrat i jiné typy.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Krok 4: Vymažte existující sérii

Vymažte všechny existující řady v grafu, abyste měli jistotu, že začínáte s prázdným listem. Tento krok je nezbytný pro vlastní data.

```csharp
chart.Series.Clear();
```

## Krok 5: Přidejte do série hodnoty data a času

Přidejte své hodnoty data a času do řady grafů. Tento krok zahrnuje vytvoření polí pro data a odpovídající hodnoty.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Krok 6: Nakonfigurujte osu X

Nastavte měřítko a značky pro osu X. Tím zajistíte, že se vaše data zobrazí správně a ve vhodných intervalech.

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

Nakonec uložte dokument do určeného adresáře. Tento krok ukončí proces a váš dokument by nyní měl obsahovat graf s hodnotami data a času na ose X.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Závěr

Přidání hodnot data a času na osu grafu v dokumentu je s Aspose.Words pro .NET jednoduchý proces. Podle kroků uvedených v tomto kurzu můžete vytvořit jasné a informativní grafy, které efektivně vizualizují data časových řad. Ať už připravujete zprávy, prezentace nebo jakýkoli dokument vyžadující detailní reprezentaci dat, Aspose.Words poskytuje nástroje, které potřebujete k úspěchu.

## FAQ

### Mohu s Aspose.Words pro .NET používat jiné typy grafů?

Ano, Aspose.Words podporuje různé typy grafů, včetně čárových, pruhových, koláčových a dalších.

### Jak mohu přizpůsobit vzhled svého grafu?

Vzhled můžete přizpůsobit přístupem k vlastnostem grafu a nastavením stylů, barev a dalších.

### Je možné do grafu přidat více řad?

 Absolutně! Do grafu můžete přidat více řad voláním`Series.Add` metoda vícekrát s různými údaji.

### Co když potřebuji dynamicky aktualizovat data grafu?

Data grafu můžete aktualizovat dynamicky úpravou vlastností řad a os programově na základě vašich požadavků.

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?

 Můžete najít podrobnější dokumentaci[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
