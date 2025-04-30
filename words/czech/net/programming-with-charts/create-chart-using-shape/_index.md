---
"description": "Naučte se, jak vytvářet a upravovat grafy v dokumentech Wordu pomocí Aspose.Words pro .NET v tomto podrobném návodu. Ideální pro vizualizaci dat."
"linktitle": "Vytvořte a upravte graf pomocí tvaru"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vytvořte a upravte graf pomocí tvaru"
"url": "/cs/net/programming-with-charts/create-chart-using-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte a upravte graf pomocí tvaru

## Zavedení

Vytváření a úprava grafů v dokumentech je v dnešním světě založeném na datech klíčovou dovedností. Grafy mohou pomoci vizualizovat data a usnadnit tak stravitelnost složitých informací. Aspose.Words for .NET je výkonná knihovna, která umožňuje programově vytvářet a manipulovat s dokumenty Wordu. V tomto tutoriálu vás provedeme procesem vytváření a úpravy spojnicového grafu pomocí Aspose.Words for .NET. Po čtení tohoto průvodce budete schopni snadno vytvářet profesionálně vypadající grafy.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte následující:

- Knihovna Aspose.Words pro .NET: Můžete si ji stáhnout [zde](https://releases.aspose.com/words/net/).
- Visual Studio: Jakákoli verze, která podporuje .NET.
- Základní znalost C#: Pochopení základů C# vám pomůže s plněním úkolů v tutoriálu.

## Importovat jmenné prostory

Chcete-li začít, je třeba importovat potřebné jmenné prostory. Tento krok je nezbytný, protože vám umožní používat třídy a metody poskytované Aspose.Words pro .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Vytvořte nový dokument

Nejprve si musíte vytvořit nový dokument Wordu. Tento dokument bude sloužit jako plátno pro váš graf.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložení grafu

Dále do dokumentu vložíte spojnicový graf. `DocumentBuilder.InsertChart` K tomuto účelu se používá metoda.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## Krok 3: Úprava názvu grafu

Úprava názvu grafu může pomoci poskytnout kontext pro zobrazená data. Název a jeho text můžete zobrazit a nastavit pomocí následujícího kódu:

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// Upozorňujeme, že pokud je jako text názvu zadána hodnota null nebo prázdná hodnota, zobrazí se automaticky vygenerovaný název.
```

## Krok 4: Úprava polohy legendy

Legenda pomáhá identifikovat různé datové řady v grafu. Její umístění a nastavení překrytí můžete přizpůsobit takto:

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## Krok 5: Uložte dokument

Nakonec je třeba dokument uložit. Tímto krokem zajistíte, že se všechny vaše změny zapíší do souboru.

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## Závěr

V tomto tutoriálu jsme se popsali, jak vytvořit a upravit spojnicový graf v dokumentu Word pomocí Aspose.Words pro .NET. Dodržováním podrobných pokynů nyní můžete vytvářet vizuálně poutavé grafy, které efektivně sdělují vaše data. Aspose.Words pro .NET nabízí širokou škálu možností přizpůsobení, které vám umožní přizpůsobit grafy vašim specifickým potřebám.

## Často kladené otázky

### Mohu použít Aspose.Words pro .NET k vytváření jiných typů grafů?

Ano, Aspose.Words pro .NET podporuje různé typy grafů, včetně sloupcových grafů, koláčových grafů a dalších. Můžete si prohlédnout dokumentaci. [zde](https://reference.aspose.com/words/net/) pro více informací.

### Jak si mohu vyzkoušet Aspose.Words pro .NET před zakoupením?

Zkušební verzi zdarma si můžete stáhnout z [zde](https://releases.aspose.com/)To vám umožní vyzkoušet si knihovnu a její funkce před provedením nákupu.

### Existuje způsob, jak získat podporu, pokud narazím na problémy?

Rozhodně. Podporu můžete získat prostřednictvím komunitních fór Aspose. [zde](https://forum.aspose.com/c/words/8)Komunita a zaměstnanci Aspose jsou velmi vstřícní.

### Jak si mohu koupit licenci pro Aspose.Words pro .NET?

Licenci si můžete zakoupit přímo na webových stránkách Aspose. [zde](https://purchase.aspose.com/buy)Existují různé možnosti licencování, které vyhovují různým potřebám.

### Co když potřebuji dočasnou licenci pro krátkodobý projekt?

Aspose nabízí dočasné licence, o které si můžete požádat [zde](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}