---
title: Definujte vlastnosti osy XY v grafu
linktitle: Definujte vlastnosti osy XY v grafu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se definovat vlastnosti osy XY v grafu pomocí Aspose.Words for .NET pomocí tohoto podrobného průvodce. Ideální pro .NET vývojáře.
weight: 10
url: /cs/net/programming-with-charts/define-xyaxis-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definujte vlastnosti osy XY v grafu

## Zavedení

Grafy jsou mocným nástrojem pro vizualizaci dat. Když potřebujete vytvořit profesionální dokumenty s dynamickými grafy, Aspose.Words for .NET je neocenitelná knihovna. Tento článek vás provede procesem definování vlastností osy XY v grafu pomocí Aspose.Words for .NET, přičemž každý krok rozebere, aby byla zajištěna srozumitelnost a snadná srozumitelnost.

## Předpoklady

Než se ponoříte do kódování, musíte mít splněno několik předpokladů:

1. Aspose.Words for .NET: Ujistěte se, že máte knihovnu Aspose.Words for .NET. Můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Potřebujete integrované vývojové prostředí (IDE), jako je Visual Studio.
3. .NET Framework: Ujistěte se, že je vaše vývojové prostředí nastaveno pro vývoj .NET.
4. Základní znalost C#: Tato příručka předpokládá, že máte základní znalosti o programování v C#.

## Importovat jmenné prostory

Chcete-li začít, musíte do projektu importovat potřebné jmenné prostory. To zajišťuje, že máte přístup ke všem třídám a metodám potřebným pro vytváření a manipulaci s dokumenty a grafy.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Proces rozdělíme do jednoduchých kroků, z nichž každý se zaměří na určitou část definování vlastností osy XY v grafu.

## Krok 1: Inicializujte Document a DocumentBuilder

 Nejprve musíte inicializovat nový dokument a a`DocumentBuilder` objekt. The`DocumentBuilder` pomáhá při vkládání obsahu do dokumentu.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložte graf

Dále do dokumentu vložíte graf. V tomto příkladu použijeme plošný graf. Rozměry grafu si můžete přizpůsobit podle potřeby.

```csharp
// Vložit graf
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Krok 3: Vymažte výchozí sérii a přidejte vlastní data

Ve výchozím nastavení bude mít graf nějaké předdefinované řady. Vymažeme je a přidáme naše vlastní datové řady.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Krok 4: Definujte vlastnosti osy X

Nyní je čas definovat vlastnosti pro osu X. To zahrnuje nastavení typu kategorie, přizpůsobení křížení os a úpravu značek a štítků.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; //Měřeno v zobrazovacích jednotkách osy Y (stovky).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Krok 5: Definujte vlastnosti osy Y

Podobně nastavíte vlastnosti pro osu Y. To zahrnuje nastavení polohy štítku, hlavních a vedlejších jednotek, zobrazovací jednotky a měřítka.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Krok 6: Uložte dokument

Nakonec dokument uložte do určeného adresáře. Tím se vygeneruje dokument aplikace Word s přizpůsobeným grafem.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Závěr

Vytváření a přizpůsobení grafů v dokumentech aplikace Word pomocí Aspose.Words for .NET je jednoduché, jakmile pochopíte příslušné kroky. Tato příručka vás provede procesem definování vlastností osy XY v grafu, od inicializace dokumentu až po uložení konečného produktu. S těmito dovednostmi můžete vytvářet podrobné, profesionálně vypadající grafy, které vylepší vaše dokumenty.

## FAQ

### Jaké typy grafů mohu vytvořit pomocí Aspose.Words pro .NET?
Můžete vytvářet různé typy grafů, včetně plošných, sloupcových, spojnicových, výsečových a dalších.

### Jak nainstaluji Aspose.Words for .NET?
 Aspose.Words for .NET si můžete stáhnout z[zde](https://releases.aspose.com/words/net/) postupujte podle dodaných pokynů k instalaci.

### Mohu si přizpůsobit vzhled svých grafů?
Ano, Aspose.Words for .NET umožňuje rozsáhlé přizpůsobení grafů, včetně barev, písem a vlastností os.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
 Ano, můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Kde najdu další návody a dokumentaci?
 Další návody a podrobnou dokumentaci naleznete na[Stránka dokumentace Aspose.Words for .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
