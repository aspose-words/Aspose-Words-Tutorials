---
title: Formát Počet Datových štítků V Grafu
linktitle: Formát Počet Datových štítků V Grafu
second_title: Aspose.Words API pro zpracování dokumentů
description: Pomocí tohoto podrobného průvodce se dozvíte, jak formátovat štítky dat v grafech pomocí Aspose.Words for .NET. Vylepšete své dokumenty Word bez námahy.
weight: 10
url: /cs/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formát Počet Datových štítků V Grafu

## Zavedení

Vytváření poutavých a informativních dokumentů často zahrnuje zahrnutí grafů s dobře formátovanými datovými štítky. Pokud jste vývojář .NET a chcete vylepšit své dokumenty aplikace Word pomocí sofistikovaných grafů, Aspose.Words for .NET je fantastická knihovna, která vám toho pomůže dosáhnout. Tento tutoriál vás krok za krokem provede procesem formátování číselných štítků v grafu pomocí Aspose.Words for .NET.

## Předpoklady

Než se ponoříte do kódu, musíte mít splněno několik předpokladů:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words for .NET. Pokud jste jej ještě nenainstalovali, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Měli byste mít nastavené vývojové prostředí .NET. Visual Studio je vysoce doporučeno.
- Základní znalost C#: Znalost programování v C# je nezbytná, protože tento tutoriál zahrnuje psaní a porozumění kódu C#.
-  Dočasná licence: Chcete-li používat Aspose.Words bez jakýchkoli omezení, můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/).

Nyní se pojďme ponořit do procesu formátování číselných štítků v grafu krok za krokem.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory pro práci s Aspose.Words pro .NET. Přidejte následující řádky na začátek souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Nastavte adresář dokumentů

Než budete moci začít manipulovat s dokumentem aplikace Word, musíte určit adresář, do kterého bude dokument uložen. To je nezbytné pro pozdější operaci ukládání.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři dokumentů.

## Krok 2: Inicializujte Document a DocumentBuilder

 Dalším krokem je inicializace nového`Document` a a`DocumentBuilder` . The`DocumentBuilder` je pomocná třída, která nám umožňuje sestavit obsah dokumentu.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložte graf do dokumentu

 Nyní vložíme graf do dokumentu pomocí`DocumentBuilder`. V tomto tutoriálu použijeme jako příklad spojnicový graf.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Zde vložíme spojnicový graf s konkrétní šířkou a výškou a nastavíme název grafu.

## Krok 4: Vymažte výchozí sérii a přidejte novou sérii

Ve výchozím nastavení bude mít graf nějaké předem vygenerované řady. Musíme je vymazat a přidat vlastní řadu s konkrétními datovými body.

```csharp
// Smazat výchozí vygenerované série.
chart.Series.Clear();

// Přidejte novou řadu s vlastními datovými body.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Krok 5: Povolte štítky dat

Chcete-li zobrazit štítky dat v grafu, musíme je povolit pro naši řadu.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Krok 6: Formátování datových štítků

Jádrem tohoto kurzu je formátování datových štítků. Na každý datový štítek můžeme použít různé formáty čísel jednotlivě.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Formát měny
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Formát data
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Formát procent
```

 Navíc můžete propojit formát datového štítku se zdrojovou buňkou. Po propojení se`NumberFormat` bude resetováno na obecné a zděděno ze zdrojové buňky.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Krok 7: Uložte dokument

Nakonec dokument uložte do určeného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Tím se dokument uloží se zadaným názvem a zajistí se zachování grafu s formátovanými datovými štítky.

## Závěr

Formátování štítků dat v grafu pomocí Aspose.Words for .NET může výrazně zlepšit čitelnost a profesionalitu vašich dokumentů aplikace Word. Podle tohoto podrobného průvodce byste nyní měli být schopni vytvořit graf, přidat datové řady a formátovat štítky dat tak, aby vyhovovaly vašim potřebám. Aspose.Words for .NET je výkonný nástroj, který umožňuje rozsáhlé přizpůsobení a automatizaci dokumentů aplikace Word, což z něj činí neocenitelný přínos pro vývojáře .NET.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro vytváření, manipulaci a konverzi dokumentů Wordu programově pomocí C#.

### Mohu pomocí Aspose.Words for .NET formátovat jiné typy grafů?
Ano, Aspose.Words for .NET podporuje různé typy grafů, včetně pruhových, sloupcových, výsečových a dalších.

### Jak získám dočasnou licenci pro Aspose.Words for .NET?
Můžete získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

### Je možné propojit datové štítky se zdrojovými buňkami v Excelu?
Ano, můžete propojit datové štítky se zdrojovými buňkami, což umožňuje zdědění číselného formátu ze zdrojové buňky.

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?
 Můžete najít komplexní dokumentaci[zde](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
