---
"description": "Naučte se, jak formátovat popisky dat v grafech pomocí Aspose.Words pro .NET s tímto podrobným návodem. Vylepšete své dokumenty Word bez námahy."
"linktitle": "Formátování čísla popisku dat v grafu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Formátování čísla popisku dat v grafu"
"url": "/cs/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formátování čísla popisku dat v grafu

## Zavedení

Vytváření poutavých a informativních dokumentů často zahrnuje vkládání grafů s dobře formátovanými popisky dat. Pokud jste vývojář v .NET a chcete vylepšit své dokumenty Wordu sofistikovanými grafy, Aspose.Words for .NET je fantastická knihovna, která vám s tím pomůže. Tento tutoriál vás krok za krokem provede procesem formátování číselných popisků v grafu pomocí Aspose.Words for .NET.

## Předpoklady

Než se ponoříme do kódu, je třeba splnit několik předpokladů:

- Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words pro .NET. Pokud jste ji ještě nenainstalovali, můžete... [stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Měli byste mít nastavené vývojové prostředí .NET. Důrazně se doporučuje Visual Studio.
- Základní znalost C#: Znalost programování v C# je nezbytná, protože tento tutoriál zahrnuje psaní a pochopení kódu v C#.
- Dočasná licence: Chcete-li používat Aspose.Words bez jakýchkoli omezení, můžete získat [dočasná licence](https://purchase.aspose.com/temporary-license/).

Nyní se ponoříme do podrobného procesu formátování číselných popisků v grafu.

## Importovat jmenné prostory

Nejdříve musíme importovat potřebné jmenné prostory pro práci s Aspose.Words pro .NET. Na začátek souboru C# přidejte následující řádky:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Nastavení adresáře dokumentů

Než začnete pracovat s dokumentem Wordu, musíte zadat adresář, kam bude dokument uložen. To je nezbytné pro pozdější uložení.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k adresáři dokumentů.

## Krok 2: Inicializace dokumentu a nástroje DocumentBuilder

Dalším krokem je inicializace nového `Document` a `DocumentBuilder`Ten/Ta/To `DocumentBuilder` je pomocná třída, která nám umožňuje konstruovat obsah dokumentu.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložení grafu do dokumentu

Nyní vložme do dokumentu graf pomocí `DocumentBuilder`V tomto tutoriálu použijeme jako příklad spojnicový graf.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Zde vložíme spojnicový graf se specifickou šířkou a výškou a nastavíme název grafu.

## Krok 4: Vymazání výchozí série a přidání nové série

Ve výchozím nastavení bude graf obsahovat několik předgenerovaných řad. Musíme je vymazat a přidat vlastní řady s konkrétními datovými body.

```csharp
// Smazat výchozí generovanou sérii.
chart.Series.Clear();

// Přidejte novou řadu s vlastními datovými body.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Krok 5: Povolení popisků dat

Abychom v grafu zobrazili popisky dat, musíme je pro naši řadu povolit.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Krok 6: Formátování popisků dat

Jádrem tohoto tutoriálu je formátování popisků dat. Na každý popisek dat můžeme jednotlivě použít různé formáty čísel.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Formát měny
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Formát data
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Procentní formát
```

Formát datového popisku můžete navíc propojit se zdrojovou buňkou. Po propojení `NumberFormat` bude resetováno na obecné a zděděno ze zdrojové buňky.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Krok 7: Uložte dokument

Nakonec uložte dokument do zadaného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Tím se dokument uloží pod zadaným názvem a zajistí se zachování grafu s formátovanými popisky dat.

## Závěr

Formátování popisků dat v grafu pomocí Aspose.Words pro .NET může výrazně zlepšit čitelnost a profesionalitu vašich dokumentů Word. Dodržováním tohoto podrobného návodu byste nyní měli být schopni vytvořit graf, přidat datové řady a formátovat popisky dat podle svých potřeb. Aspose.Words pro .NET je výkonný nástroj, který umožňuje rozsáhlé přizpůsobení a automatizaci dokumentů Word, což z něj činí neocenitelný přínos pro vývojáře .NET.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro programovou tvorbu, manipulaci a konverzi dokumentů Wordu pomocí C#.

### Mohu formátovat jiné typy grafů pomocí Aspose.Words pro .NET?
Ano, Aspose.Words pro .NET podporuje různé typy grafů, včetně sloupcových, koláčových a dalších.

### Jak získám dočasnou licenci pro Aspose.Words pro .NET?
Můžete získat dočasnou licenci [zde](https://purchase.aspose.com/temporary-license/).

### Je možné propojit popisky dat se zdrojovými buňkami v Excelu?
Ano, můžete propojit popisky dat se zdrojovými buňkami, což umožňuje dědit formát čísla ze zdrojové buňky.

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?
Najdete zde komplexní dokumentaci [zde](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}