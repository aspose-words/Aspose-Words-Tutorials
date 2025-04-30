---
"description": "Naučte se, jak definovat vlastnosti osy XY v grafu pomocí Aspose.Words pro .NET v tomto podrobném návodu. Ideální pro vývojáře .NET."
"linktitle": "Definování vlastností osy XY v grafu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Definování vlastností osy XY v grafu"
"url": "/cs/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Definování vlastností osy XY v grafu

## Zavedení

Grafy jsou mocným nástrojem pro vizualizaci dat. Pokud potřebujete vytvářet profesionální dokumenty s dynamickými grafy, Aspose.Words pro .NET je neocenitelná knihovna. Tento článek vás provede procesem definování vlastností osy XY v grafu pomocí Aspose.Words pro .NET a rozebere každý krok pro zajištění přehlednosti a snadného pochopení.

## Předpoklady

Než se pustíte do kódování, je třeba splnit několik předpokladů:

1. Aspose.Words pro .NET: Ujistěte se, že máte knihovnu Aspose.Words pro .NET. Můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Potřebujete integrované vývojové prostředí (IDE), jako je Visual Studio.
3. .NET Framework: Ujistěte se, že vaše vývojové prostředí je nastaveno pro vývoj v .NET.
4. Základní znalost C#: Tato příručka předpokládá, že máte základní znalosti programování v C#.

## Importovat jmenné prostory

Nejprve je třeba do projektu importovat potřebné jmenné prostory. Tím zajistíte přístup ke všem třídám a metodám potřebným pro vytváření a manipulaci s dokumenty a grafy.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Rozdělíme proces do jednoduchých kroků, z nichž každý se zaměří na specifickou část definování vlastností osy XY v grafu.

## Krok 1: Inicializace dokumentu a nástroje DocumentBuilder

Nejprve je třeba inicializovat nový dokument a `DocumentBuilder` Objekt. Ten `DocumentBuilder` pomáhá s vkládáním obsahu do dokumentu.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložení grafu

Dále vložíte do dokumentu graf. V tomto příkladu použijeme plošný graf. Rozměry grafu můžete podle potřeby upravit.

```csharp
// Vložit graf
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Krok 3: Vymazání výchozích sérií a přidání vlastních dat

Ve výchozím nastavení bude graf obsahovat několik předdefinovaných řad. Tyto řad vymažeme a přidáme vlastní datové řady.

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

## Krok 4: Definování vlastností osy X

Nyní je čas definovat vlastnosti osy X. To zahrnuje nastavení typu kategorie, přizpůsobení křížení os a úpravu značek a popisků.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // Měřeno v jednotkách zobrazení osy Y (stovky).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Krok 5: Definování vlastností osy Y

Podobně nastavíte vlastnosti pro osu Y. To zahrnuje nastavení polohy popisku, hlavních a vedlejších jednotek, zobrazovaných jednotek a měřítka.

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

Nakonec dokument uložte do vámi určeného adresáře. Tím se vygeneruje dokument Word s upraveným grafem.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Závěr

Vytváření a úprava grafů v dokumentech Wordu pomocí Aspose.Words pro .NET je jednoduchá, jakmile pochopíte jednotlivé kroky. Tato příručka vás provede procesem definování vlastností osy XY v grafu, od inicializace dokumentu až po uložení konečného produktu. S těmito dovednostmi můžete vytvářet detailní, profesionálně vypadající grafy, které vylepší vaše dokumenty.

## Často kladené otázky

### Jaké typy grafů mohu vytvářet pomocí Aspose.Words pro .NET?
Můžete vytvářet různé typy grafů, včetně plošných, sloupcových, spojnicových, koláčových a dalších.

### Jak nainstaluji Aspose.Words pro .NET?
Aspose.Words pro .NET si můžete stáhnout z [zde](https://releases.aspose.com/words/net/) a postupujte podle přiložených pokynů k instalaci.

### Mohu si přizpůsobit vzhled svých grafů?
Ano, Aspose.Words pro .NET umožňuje rozsáhlé úpravy grafů, včetně barev, písem a vlastností os.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
Ano, můžete získat bezplatnou zkušební verzi [zde](https://releases.aspose.com/).

### Kde najdu další návody a dokumentaci?
Další návody a podrobnou dokumentaci naleznete na [Dokumentace k Aspose.Words pro .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}