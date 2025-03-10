---
title: Vytvořte a přizpůsobte graf pomocí tvaru
linktitle: Vytvořte a přizpůsobte graf pomocí tvaru
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vytvářet a přizpůsobovat grafy v dokumentech aplikace Word pomocí Aspose.Words for .NET pomocí tohoto podrobného průvodce. Ideální pro vizualizaci dat.
weight: 10
url: /cs/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte a přizpůsobte graf pomocí tvaru

## Zavedení

Vytváření a přizpůsobení grafů ve vašich dokumentech je v dnešním světě založeném na datech klíčovou dovedností. Grafy mohou pomoci vizualizovat data, díky čemuž jsou složité informace lépe stravitelné. Aspose.Words for .NET je výkonná knihovna, která vám umožňuje programově vytvářet a manipulovat s dokumenty Wordu. V tomto tutoriálu vás provedeme procesem vytváření a přizpůsobení spojnicového grafu pomocí Aspose.Words for .NET. Na konci této příručky budete schopni snadno vytvářet profesionálně vypadající grafy.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte následující:

-  Aspose.Words for .NET Library: Můžete si ji stáhnout[zde](https://releases.aspose.com/words/net/).
- Visual Studio: Jakákoli verze, která podporuje .NET.
- Základní znalost C#: Pochopení základů C# vám pomůže postupovat společně s výukovým programem.

## Importovat jmenné prostory

Chcete-li začít, musíte importovat potřebné jmenné prostory. Tento krok je nezbytný, protože vám umožňuje používat třídy a metody poskytované Aspose.Words pro .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Vytvořte nový dokument

Nejprve musíte vytvořit nový dokument aplikace Word. Tento dokument bude sloužit jako plátno pro váš graf.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložte graf

 Dále do dokumentu vložíte spojnicový graf. The`DocumentBuilder.InsertChart` k tomuto účelu se používá metoda.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## Krok 3: Přizpůsobte nadpis grafu

Přizpůsobení názvu grafu může pomoci poskytnout kontext pro zobrazovaná data. Pomocí následujícího kódu můžete zobrazit název a nastavit jeho text:

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// Upozorňujeme, že pokud je jako text nadpisu zadána hodnota null nebo prázdná, zobrazí se automaticky vygenerovaný název.
```

## Krok 4: Upravte pozici legendy

Legenda pomáhá identifikovat různé datové řady v grafu. Jeho polohu a nastavení překrytí můžete upravit takto:

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## Krok 5: Uložte dokument

Nakonec je potřeba dokument uložit. Tento krok zajistí, že všechny vaše změny budou zapsány do souboru.

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## Závěr

V tomto tutoriálu jsme probrali, jak vytvořit a upravit spojnicový graf v dokumentu aplikace Word pomocí Aspose.Words for .NET. Podle podrobného průvodce nyní můžete vytvářet vizuálně přitažlivé grafy, které efektivně sdělují vaše data. Aspose.Words for .NET nabízí širokou škálu možností přizpůsobení, které vám umožní přizpůsobit grafy vašim konkrétním potřebám.

## FAQ

### Mohu použít Aspose.Words pro .NET k vytvoření jiných typů grafů?

 Ano, Aspose.Words for .NET podporuje různé typy grafů, včetně sloupcových grafů, koláčových grafů a dalších. Můžete prozkoumat dokumentaci[zde](https://reference.aspose.com/words/net/) pro více podrobností.

### Jak mohu vyzkoušet Aspose.Words for .NET před nákupem?

 Můžete si stáhnout bezplatnou zkušební verzi z[zde](https://releases.aspose.com/). To vám umožní otestovat knihovnu a její funkce před nákupem.

### Existuje způsob, jak získat podporu, pokud narazím na problémy?

 Absolutně. K podpoře můžete přistupovat prostřednictvím komunitních fór Aspose[zde](https://forum.aspose.com/c/words/8)Komunita a zaměstnanci Aspose jsou velmi pohotoví.

### Jak si koupím licenci pro Aspose.Words pro .NET?

 Licenci si můžete zakoupit přímo z webu Aspose[zde](https://purchase.aspose.com/buy). Existují různé možnosti licencování, které vyhovují různým potřebám.

### Co když potřebuji dočasnou licenci pro krátkodobý projekt?

 Aspose nabízí dočasné licence, o které můžete požádat[zde](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
